# Node Package Verify Action

A custom GitHub Action to verify Node.js packages by running lint and unit tests using npm, yarn, or pnpm package managers.

## Inputs

| Input             | Description                                 | Default |
| ----------------- | ------------------------------------------- | ------- |
| `package-manager` | Package manager to use (npm, yarn, or pnpm) | `npm`   |
| `node-version`    | Node.js version to use (must be >= 18.0.0)  | `lts/*` |

## Example Usage

```yml
name: Lint & Unit Test
on:
  push:
    branches: [main]
  pull_request:
    branches: [dev]
jobs:
  check:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        node: [18]
    steps:
      - name: Node Package Verify Action
        uses: vbilltran68-devops/node-pkg-verify-action@v1
        with:
          node-version: ${{ matrix.node-version }}
          package-manager: 'pnpm'
```
