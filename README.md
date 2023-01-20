# PNPM `deploy` invalid aliased dependency prune reproduction repo

When running `pnpm deploy --prod` pnpm prunes aliased dependencies, which are also specified in `devDependencies`. See [`packages/app/package.json`](./packages/app/package.json).

## Reproduction steps

1) Install deps `pnpm install`
2) Run `pnpm deploy -F app app-prod --prod`
3) Run `ls app-prod/node_modules` (prints `aliased-is-odd is-callable`)

Additionally you may run `pnpm deploy -F app app-dev` and then `ls app-prod/node_modules` to see `aliased-is-odd aliased-lodash is-callable lodash`.
