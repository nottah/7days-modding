# Nottah's 7 Days to Die Modlets

**Compatibility: These modlets are designed for the 7 Days to Die 3.x branch and have been tested and confirmed working through v3.2 (b10).**

Five XML modlets by **Nottah**, each available in its own folder under `Mods/`. Install whichever ones you want. The descriptions below are based on the folders' `ModInfo.xml` and `Config/*.xml` files.

| Modlet folder | Version | What it does | Multiplayer installation |
| --- | --- | --- | --- |
| `Nottah_AutoReloadCrossbows` | 1.0.2 | Starts the normal reload after firing an iron or compound crossbow. | Server and every client |
| `Nottah_BandageDuctTape` | 1.0.0 | Adds a duct tape recipe using a regular bandage and glue. | Server; marked `ServerSideOnly` |
| `Nottah_CraftableNightVision` | 1.0.0 | Adds a workbench recipe for the vanilla Night Vision Goggles helmet modification. | Server; marked `ServerSideOnly` |
| `Nottah_DualAttributeMods` | 1.0.0 | Allows the five vanilla attribute helmet mods in chest armor as well. | Server; marked `ServerSideOnly` |
| `Nottah_MixerClay` | 1.1.0 | Adds cement mixer recipes for clay soil using crushed sand and water. | Server; marked `ServerSideOnly` |

## Mod descriptions

### Auto Reload Crossbows

Sets `Action0/AutoReload` to `true` for the Iron Crossbow (`gunBowT1IronCrossbow`) and Compound Crossbow (`gunBowT3CompoundCrossbow`). This automatically begins the normal reload after a shot. The patch does not change reload speed, ammunition capacity, or damage.

Its `ModInfo.xml` explicitly instructs installation on the server and every client.

### Bandages to Duct Tape

Adds an alternate recipe producing **1 duct tape** (`resourceDuctTape`) from:

- 1 glue (`resourceGlue`)
- 1 regular bandage (`medicalBandage`)

The recipe uses the `packMuleCrafting` tag and specifies no workstation or explicit crafting time. It is appended to the recipe list, leaving existing recipes in place.

### Craftable Night Vision

Adds a **workbench** recipe producing **1 vanilla Night Vision Goggles helmet modification** (`modArmorNightVision`) from:

- 1 armor parts (`armorParts`)
- 20 electrical parts (`resourceElectricParts`)
- 2 headlights (`resourceHeadlight`)
- 1 motion sensor (`motionsensor`)
- 10 scrap polymers (`resourceScrapPolymers`)

The recipe sets `craft_time="120"` (a base time of 120 seconds) and uses the `workbenchCrafting` tag. It adds a way to craft the existing modification without changing the item itself. No unlock requirement is specified in the added recipe.

### Dual Attribute Mods

Sets the allowed installation tags to `armorHead,armorChest` for these vanilla attribute modifications:

- Perception (`modArmorPerception`)
- Strength (`modArmorStrength`)
- Fortitude (`modArmorFortitude`)
- Agility (`modArmorAgility`)
- Intellect (`modArmorIntellect`)

This allows an attribute mod in chest armor while retaining helmet compatibility. As described in the metadata, the intent is to support hybrid builds with one attribute mod in each armor piece. The XML only changes installation tags; it does not change attribute bonuses, slot counts, or stacking restrictions.

### Mixer Clay

Adds two **cement mixer** recipes, each producing **150 clay soil** (`resourceClayLump`):

| Ingredients | Output | Base crafting time |
| --- | --- | --- |
| 10 crushed sand (`resourceCrushedSand`) + 1 clean/boiled water (`drinkJarBoiledWater`) | 150 clay soil | 30 seconds |
| 10 crushed sand (`resourceCrushedSand`) + 1 murky water (`drinkJarRiverWater`) | 150 clay soil | 30 seconds |

Both recipes set `craft_time="30"`, require `cementMixer`, and use the `cementMixerCrafting` tag. They are added alongside existing recipes.

## Installation

1. Close the game, or stop the dedicated server.
2. Download or clone this repository.
3. Copy the desired `Nottah_*` folders from this repository's `Mods/` folder into the game's or dedicated server's `Mods` directory. Create that directory if necessary. For a local Steam installation, use **Manage → Browse local files** to locate the game installation directory.
4. Check that each mod's `ModInfo.xml` is directly inside its own folder, as shown below. Copy the individual modlet folders, avoiding an extra repository folder or a nested `Mods/Mods/` directory.
5. For multiplayer, install **Auto Reload Crossbows on the server and every client**. The other four modlets declare `ServerSideOnly="true"` in their metadata and are intended for server installation. For single-player, install the selected modlets locally.
6. Restart the game or server to load the mods.

Example installed layout:

```text
7 Days To Die/
└── Mods/
    ├── Nottah_AutoReloadCrossbows/
    │   ├── ModInfo.xml
    │   └── Config/
    │       └── items.xml
    └── Nottah_MixerClay/
        ├── ModInfo.xml
        └── Config/
            └── recipes.xml
```

To uninstall a modlet, close the game or stop the server, remove its folder from the installed `Mods` directory, and restart.

## Compatibility

The versions listed above are **modlet versions**. Game compatibility is stated at the top of this README. Compatibility with other mods has not been verified here. Crafting times are the values declared in the recipes and may be affected by game modifiers.

## Credits and AI assistance

- **Nottah** — Mod author and maintainer; responsible for design decisions,
  in-game testing, and releases.
- **OpenAI Codex (AI coding assistant)** — Assisted with reviewing the XML
  modlets, writing repository documentation, and preparing repository updates.

AI assistance is disclosed for transparency. Nottah reviews and approves
changes and maintains responsibility for the project.
