# ADR-001: Inventory per store

## Status

Accepted

## Context

Products can exist in multiple stores, and each store can have different stock levels and minimum stock requirements.

Storing the store directly in the product table would couple the product catalog to a specific location and duplicate product information.

## Decision

The product catalog will remain independent from stores.

Inventory will be modeled using a separate entity that relates:

- Product
- Store
- Current stock
- Reserved stock
- Minimum stock

Each product-store combination must be unique.

## Consequences

### Positive

- Products remain a global catalog.
- Stock can vary by store.
- The system supports multiple stores.
- Inventory transfers can be added later.
- Minimum stock can be configured per location.

### Negative

- Inventory queries require an additional relationship.
- Product creation and inventory assignment become separate operations.
