# NPM Version

This is a composite action that creates a PR to bump and NPM package version. Use this action is deisgned to be used with [skonves/npm-publish](https://github.com/skonves/npm-publish).

## Usage

The following workflow can be manually dispatched to open a PR that bumps the package version.

```yaml
# .github/workflows/version.yml
name: version

on:
  workflow_dispatch:
    inputs:
      newversion:
        description: "npm version [<newversion> | major | minor | patch | premajor | preminor | prepatch | prerelease | from-git]"
        required: true
      preid:
        description: 'The "prerelease identifier" to use as a prefix for the "prerelease" part of a semver.'
        required: false

jobs:
  npm-version:
    runs-on: ubuntu-latest
    steps:
      - uses: skonves/npm-version
        with:
          newversion: ${{ inputs.newversion }}
          preid: ${{ inputs.preid }}
```

## More info

The following article on Medium describes the design philosophy behind this action: [Publishing NPM packages without a local environment](https://medium.com/@stevekonves/publishing-npm-packages-without-a-local-environment-b392f40d1817).
