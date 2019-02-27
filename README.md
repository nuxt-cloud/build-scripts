# Build Scripts

Build scripts to build a language specific project and package it to a production ready compressed `app.tgz` artifact.

To use the artifact one have to extract package in a clean directory and call `./start` script.

**NOTE:** These scripts are designed to smoothly run on linux environments.

## Builders

### Node.js

- Source: [scripts/build-node](./scripts/build-node)
- Cache directort: `.cache`

Builder for any Node.js project. Supports both yarn and npm.

#### Yarn Specific

- `.yarnclean` file is auto generated to remove things like `.md` files from final `app.tgz`
- `.cache/yarn` is also created to cache all yarn fetched packages for future reuse

#### Build Steps

- Prepare cache and cleanup node_modules
- Install all dependencies (including `devDependencies`)
- Run `build` script in `scripts` section of `package.json`
- Clean up node_modules
- Install only `dependencies` (excluding `devDependencies`)
- Create `start` script that runs `start` script in `scripts` section of `package.json`

# License

MIT
