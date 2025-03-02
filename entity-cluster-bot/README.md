# Entity Cluster Bot

## Description

This agent detects whether two or more accounts are likely controlled by the same entity through simple heuristics. The purpose of this bot is for downstream consumption, for example, to propagate alerts across multiple accounts.

It operates under the assumption that bi-directional exchange of tokens/ ETH for newer accounts is likely controlled by the same entity. Contracts created by an address are also considered part of the same entity.

The bot generates a graph and identifies and reports on the connected components.

A entity is created if this condition is observed accounts with less than MAX_NONCE transactions within a ENTITY_CLUSTER_WINDOW_IN_DAYS timeframe. Entities will age out within MAX_AGE_IN_DAYS.

## Supported Chains

- All Forta Supported Chains

## Alerts

- ENTITY-CLUSTER
  - Fired when a new entity with more than one address is detected
  - Severity is always set to "info"
  - Type is always set to "info"
  - Metadata will contain a unique entity identifier along with all the addresses that are currently associated with the entity.

## Test Data

Ronin Bridge exploiter

npm run tx 0x431136dd361557abe34fe4685a278654e9e1bc7547a40719b348c096c5092d2b,0x5dfb733a9522f72e4dff5d6cb635135ee599cf3c19f2b9e4a8c91fba7e7aeb45

creates entity with 0x098b716b8aaf21512996dc57eb0615e2383e2f96 and 0xe708f17240732bbfa1baa8513f66b665fbc7ce10