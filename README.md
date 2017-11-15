# FAtiMA-DST
Use [FAtiMA-Toolkit](https://github.com/GAIPS-INESC-ID/FAtiMA-Toolkit) to create agents for [Don't Starve Together](http://store.steampowered.com/app/322330/Dont_Starve_Together/).

This repository aims to provide an integration of FAtiMA-Toolkit with Don't Starve Together (DST), allowing anybody to create agents for DST.

**Notes**:
- Throughout this read me I'll reference game files which are available to whomever owns a copy of the game. I'll always assume as a base directory the **scripts** folder. This folder can be found in *[DST install dir]/data/scripts*.
- Although not a prerequisite, some knowledge of the game will be helpful.
- DST modding is encouraged and completely accepted by the game developers, however, there is no documentation whatsoever. Luckily, every line of code is available in the game directory. I recommend the use of an editor that supports the *Search in files* functionality. You won't need to make any mod for the game, but you'll eventually need to search the game files to understand the actions and how everything works. Check the Understanding the Actions section.

### Creating an agent

This integration has two components: **FAtiMA-Server** and **FAtiMA-DST**. The first is a C# console application that will run FAtiMA, and the latter is a mod for DST that will control the character. You can think of **FAtiMA-Server** has the brains of the agents and **FAtiMA-DST** has the body.

1. Write a Role Play Character file using the FAtiMA Authoring Tools.
2. Get the **FAtiMA-DST** mod from the workshop.
3. Launch **FAtiMA-Server** console application.
4. Launch a game with the **FAtiMA-DST** mod enabled.

### Actions

The following table presents a list of actions that agents can perform. This list has been curated from the complete list of available actions in DST (these actions were taken from the **actions.lua** script).

For a complete list of actions available in the game check [this](https://gist.github.com/hineios/2160d86d2c3ebd6aa594f4a00d041ca6).

|Actions|Params|Restrictions|Description|
|:---:|:---:|:---:|:---|
|ACTIVATE|`{target: GUID}`|target: *activatable*|Interact with some game elements. Useful to investigate *dirtpiles*|
|ADDFUEL|`{target: GUID, invobject: GUID}`|target: *fuel*, invobject: *fueled*|Add fuel to fueled entities (campfire, firesupressor)|
|ATTACK|`{target: GUID}`||Attack other entities.|
|BAIT|`{target: GUID, invobject: GUID}`|target: *trap*|Put bait on traps|
|BUILD|`{recipe:, pos: ,rotation: ,skin: }`|||
|CASTSPELL|`{target: GUID}`||Use staves. Equiped Hand slot must have the *spellcaster* component|
|CATCH|`{}`||Needs to be reviewed|
|CHECKTRAP|`{target: GUID}`|target: *trap*|Harvest trap|
|CHOP|`{target: GUID, invobject: GUID}`|target: *workable*, invobject: can work target |Chop trees|
|COMBINESTACK|`{target: GUID, invobject: GUID}`|target: *stackable*, invobject: same *prefab* as target|Combines invobject into target if it is the same prefab and target is not full|
|COOK|`{target: GUID, invobject: GUID}`|target: *cooker*, invobject: must be ||
|CREATE|`{}`||Needs to be reviewed|
|DEPLOY|`{invobject: GUID, pos: (x, y, z)}`|invobject: *deployable*, pos: valid position|Place ground tile, walls, fences, and gates|
|DIG|`{target: GUID, invobject: GUID}`|target: *workable*, invobject: can work target|Dig grass, twigs, rabbit holes, graves, and others from the ground|
|DROP|`{invobject: GUID, pos: (x, y, z)}`|invobject: must be in inventory, pos: valid position|Drop held item to a spot in the ground|
|DRY|`{target: GUID}`|target: *dryer*, invobject: |Dry meat at racks|
|EAT|`{target: GUID}`|target: *edible*|Eat food|
|EQUIP|`{}`|||
|EXTINGUISH|`{}`||extinguish using object|
|FEED|`{}`|||
|FEEDPLAYER|`{}`|||
|FERTILIZE|`{}`|||
|FILL|`{}`||fill mosquito sack|
|FISH|`{}`|||
|GIVE|`{}`|||
|GIVEALLTOPLAYER|`{}`|||
|GIVETOPLAYER|`{}`|||
|HAMMER|`{target: GUID, invobject: GUID}`|target: *workable*, invobject: can work target|Hammer down built structures|
|HARVEST|`{}`||harvest crops|
|HEAL|`{}`|||
|JUMPIN|`{}`|||
|LIGHT|`{}`|||
|LOOKAT|`{}`|||
|MANUALEXTINGUISH|`{}`|||
|MINE|`{target: GUID, invobject: GUID}`|target: *workable*, invobject: can work target|Mine rocks, sinkholes, glassiers, and **rock with gold**|
|MOUNT|`{}`|||
|MURDER|`{}`|||
|NET|`{}`|||
|PICK|`{}`||pick grass|
|PICKUP|`{}`||pick up backpack|
|PLANT|`{}`|||
|REEL|`{}`|||
|RESETMINE|`{}`|||
|RUMMAGE|`{}`||open container|
|SADDLE|`{}`||saddle rideable|
|SEW|`{}`|||
|SHAVE|`{}`|||
|SLEEPIN|`{}`|||
|SMOTHER|`{}`|||
|STORE|`{}`|||
|TAKEITEM|`{}`||take brid from cage|
|TERRAFORM|`{}`|||
|TURNOFF|`{}`|||
|TURNON|`{}`|||
|UNEQUIP|`{}`|||
|UNPIN|`{}`|||
|UNSADDLE|`{}`|||
|UPGRADE|`{}`|||
|USEITEM|`{}`||hats|
|WALKTO|`{}`|||


### Understanding the Actions

