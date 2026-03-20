# HârnWorld Adventure: The Bloody Raven
[![Version (latest)](https://img.shields.io/github/v/release/toastygm/hm-adv-br)](https://github.com/toastygm/hm-adv-br/releases/latest)
[![Forge Installs](https://img.shields.io/badge/dynamic/json?label=Forge%20Installs&query=package.installs&suffix=%25&url=https%3A%2F%2Fforge-vtt.com%2Fapi%2Fbazaar%2Fpackage%2Fhm-adv-br&colorB=4aa94a)](https://forge-vtt.com/bazaar#package=hm-adv-br)
[![GitHub downloads (latest)](https://img.shields.io/badge/dynamic/json?label=Downloads@latest&query=assets[?(@.name.includes('zip'))].download_count&url=https://api.github.com/repos/toastygm/hm-adv-br/releases/latest&color=green)](https://github.com/toastygm/hm-adv-br/releases/latest)

This module provides the adventure "The Bloody Raven", a mini-adventure for the
[HârnWorld](https://columbiagames.com/harnworld/) fantasy setting. However, this
adventure could be located in any fantasy setting or location with minimal adaptations.

Although designed for use with the [HârnMaster](https://foundryvtt.com/packages/hm3)
system, this module is mostly system-agnostic, with the exception of Actors.
Detailed descriptions of the actors has been provided in journal entries to facilitate
conversion to other game systems.

On a wilderness section of road or trail, the characters discover an abandoned Khuzdul
(Dwarven) outpost.

# Credits

This module is made possible by the hard work of HârnWorld fans, and is provided at no
cost. This work is an adaptation of the adventure [The Bloody Raven](https://www.lythia.com/adventures/bloody-raven/) available at
the HârnWorld fan site [Lythia.com](https://www.lythia.com/).

**Writer:** Kerry Mould

**Contributor:** Andy Gibson

**Original Maps:** Thomas Shook

**Adapted to Foundry VTT:** Tom Rodriguez

This module is "[Fanon](https://www.lythia.com/about/publishing-fan-written-material/)", a derivative work of copyrighted material by Columbia Games Inc. and N. Robin Crossby.

# Development

Requires Node.js >= 24.

## Project structure

- `assets/packs/<name>/unique/` — source JSON files for each compendium pack
- `assets/templates/module.template.json` — module manifest template (version/URLs are injected at build time from `package.json`)
- `scripts/init.js` — ScenePacker integration
- `utils/` — build scripts

## Common tasks

```sh
npm install                  # install dependencies (first time / after pulling)
npm run deploy:qa            # build and deploy to local QA Foundry instance
npm run deploy:release       # build and create build/dist/module.zip
npm run release              # create GitHub release (needs GITHUB_TOKEN)
npm run clean                # remove build/
```

## Making content changes

Edit the JSON files in `assets/packs/<name>/unique/`. These are the source of truth — LevelDB packs are compiled from them at build time.

## Deploying locally for testing

Set environment variables for your Foundry data paths (in `.env.local` or your shell):

```
FOUNDRYVTT_DEV_DATA=/path/to/foundry/dev
FOUNDRYVTT_QA_DATA=/path/to/foundry/qa
FOUNDRYVTT_PROD_DATA=/path/to/foundry/prod
```

Then `npm run deploy:qa` (or `:dev` / `:prod`) will build and rsync to that instance.

## Releasing

1. Bump the version in `package.json`
2. Commit and push to `main`
3. `npm run deploy:release` — builds and creates `build/dist/module.zip`
4. `export GITHUB_TOKEN=$(gh auth token)` (or set in `.env.local`)
5. `npm run release` — creates a GitHub release with `module.zip` and `module.json` attached

