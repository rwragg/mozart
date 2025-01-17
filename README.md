# mozart

A simple mapper script for Mozart MUD that's hosted at the University I work at.
You can connect to Mozart @ mozartmud.net:4500
This is a tintin++ script (https://tintin.sourceforge.io) and has some specific set paths for file access. Beware!

The script is based of a forum post on the tintin++ boards from 2013.
https://tintin.sourceforge.io/forum/viewtopic.php?f=6&t=1961

# Warning
This script has some hardcoded paths set, as my MUD folder is ~/mud/ - which you need to change
if you want to use this yourself. You also need to start tt++ with the file argument, as it depends
on the creation of some dotfiles for data storage.

# Disclaimer
This script runs shell commands in tintin++. This means that I do a bunch of sed/awk/cat in order to format
text output from the mapper and identify code. If you are not comfortable with this, you can turn off the
identify part of the script by commenting out the #READ lines for the identy and mapper module (#NOP comments out).
Of course, this removes the whole point of the script, but that's your choice obviously.

I am not liable for any magic shenanigans that occur on your system, sorry.

# Usage
$ tt++ main.tin
This loads the main script that reads in other necessary files. Ensure you start it this way for the
mapper to work correctly. Note that the main.tin file ONLY reads in the other modules.

## General

login - autologs into Mozart

setup - initalizes the splits, the screen regions, the chat windows and lots of background stuff

ALT+1 - toggles gossip chat pane

ALT+2 - toggles tells chat pane

ALT+3 - toggles group chat pane

setbuff {SpellName} - adds a spell and toggles it on/off to the auto-recast list. See the $spell variable for possible spells you can add to the buff list. (If you add a spell not in $spell, you break the printbuffs call.

recast - manually triggers the automatic cast of the first non-applied spell in the buff list. This should be going via #TICKERs, but they may not fire correctly.


## Map stuff!

mapoff - turns the mapping off and sets rooms to static which means you can move in the map but no
no new data is being written. Also alters the prompt to let you know the mapper is turned off.

mapon - turns the mapper on. Any movement into a new room will pull the roomname, description and terrain
and then set those values in the map file. It will also use the zone name that you set manually. The room
is also colorized according to the $zcol variable. You can set this with "setcol <aaa>" where aaa = rgb values in letters. ie, red = <faa>, blue = <aaf>

zone - sets the zone we want to write to the current rooms we enter.

nozone - sets zone name to NotYetSet so you can easily come back to rooms you dont know the correct area for.

save - writes the map to file and also saves the player position (room vnum in map).

logout - when in an inn, it calls the save alias and then rents a room.

symbol - sets a 1-3 character note in the current room on the map. Dont go above 3, it will skew the map.

note - sets a note for the current room. ie, note Boss room.

listnote - displays a list of room with notes that match your search.

findroom - tries to match the room name, and calculate a path that is shown on the map.

walk - travels along the path one room per 'walk' command.

undo - performs an undo on the latest room creation/movement. Does NOT undo room information (names) from
what I can tell so far.

More information can be read from the script itself, it's fairly self explanatory.
