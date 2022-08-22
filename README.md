# renovate-config

[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg)](https://github.com/prettier/prettier)
[![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)

Ridedott's base config for Renovate[bot].

## Getting Started

The project has no runtime and acts as a shareable base config. It can only be
used by other projects implementing Renovate[bot].

### Prerequisites

Minimal requirements to set up the project:

- [Node.js](https://nodejs.org/en) v10, installation instructions can be found
  on the official website, a recommended installation option is to use
  [Node Version Manager](https://github.com/creationix/nvm#readme). It can be
  installed in a
  [few commands](https://nodejs.org/en/download/package-manager/#nvm).
- A package manager like [Yarn](https://yarnpkg.com) or
  [npm](https://www.npmjs.com). All instructions in the documentation will
  follow the npm syntax.
- Optionally a [Git](https://git-scm.com) client.

### Installing

Start by cloning the repository:

```bash
git clone git@github.com:ridedott/renovate-config.git
```

In case you don't have a git client, you can get the latest version directly by
using
[this link](https://github.com/ridedott/renovate-config/archive/master.zip) and
extracting the downloaded archive.

Go the the right directory and install dependencies:

```bash
cd renovate-config
npm install
```

That's it! You can now go to the next step.

## Tests

This repository does not contain any source code, just the configuration, so no
tests are present.

### Formatting

This project uses [Prettier](https://prettier.io) to automate formatting. All
supported files are being reformatted in a precommit hook. You can also use one
of the two scripts to validate and optionally fix all of the files:

```bash
npm run format
npm run format:fix
```

## Publishing

Publishing is handled in an automated way and must not be performed manually.

Each commit to the master branch is automatically deployed to the NPM registry
with a version specified in `package.json`. All other commits are published as
pre-releases.

## Usage

Add a Renovate configuration to your project and use
`"extends": ["local>ridedott/renovate-config"]` to include the options defined
as defaults in the **./default.json** configuration:

```json
{
  "extends": ["local>ridedott/renovate-config"],
  "packageRules": [
    {
      "enabled": false,
      "packageNames": ["@types/node"],
      "updateTypes": ["major"]
    }
  ]
}
```

The default configuration is currently set to:

```json
{
  "automergeSchedule": ["after 9am and before 4pm every weekday"],
  "commitMessageAction": "update",
  "postUpdateOptions": ["npmDedupe"],
  "rangeStrategy": "bump",
  "rebaseStalePrs": true,
  "recreateClosed": true
}
```

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md).

## Built with

### Automation

- [Google Cloud Build](https://cloud.google.com/cloud-build/)

## Versioning

This project adheres to [Semantic Versioning](http://semver.org) v2.
