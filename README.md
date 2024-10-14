# Filtering workspace packages does not work correctly

When filtering for dependencies / dependency workspace packages, dependencies
linked with a relative file path are not included.

## Example

- `pnpm m list --depth=-1` correctly lists all projects

- `pnpm --filter @pnpm-filter-bug/main-project list` correctly lists both
  dependencies

- `pnpm --filter @pnpm-filter-bug/main-project^... list --depth=-1` only lists
  the dependency referenced with `"workspace:^"` but omits the dependency with
  the relative path link.

- Using the alternative version:
  - `mv main-project/package.json main-project/package.json.orig`
  - `mv main-project/package.json.alt main-project/package.json`
  shows both dependencies with `pnpm --filter
  @pnpm-filter-bug/main-project^... list --depth=-1`
  
