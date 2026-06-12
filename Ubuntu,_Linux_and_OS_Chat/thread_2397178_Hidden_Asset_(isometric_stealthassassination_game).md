---
title: "Hidden Asset (isometric stealth/assassination game) public alpha demo testing"
date: 2018-07-26
forum: Ubuntu, Linux and OS Chat
---

### Post by Christian Knudsen on 2018-07-26
Haven't posted about my game Hidden Asset here for a while. Version 0.6.2 of the alpha demo is now available for download and testing. Use the download links below.

This version includes some significant changes to the core gameplay. In this development video, I go over some of these changes: [https://youtu.be/ZOEwVGntIQ0](https://youtu.be/ZOEwVGntIQ0)


-- Download links --

North America:
[Windows 7 or later (128 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetwindows)
[Linux 32-bit (126 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetlinux32)
[Linux 64-bit (126 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetlinux64)
[Mac OS X 10.5 or later (156 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetmacosx)

Europe:
[Windows 7 or later (128 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetwindowseu)
[Linux 32-bit (126 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetlinux32eu)
[Linux 64-bit (126 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetlinux64eu)
[Mac OS X 10.5 or later (156 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetmacosxeu)


-- Debug information --
 
For the Windows and Linux versions, there are two executables: a **normal** version and a **debug** version. The debug version may run a bit slower on older computers, so if you’re not getting a steady 40 FPS (hit F1 to toggle FPS on/off), you may want to use the normal version. But if you can use the debug version, please do so as this will provide valuable information in case of a crash:

– On Windows, the debug information will pop up in a window during a crash.
– On Linux, the debug information will be outputted to the terminal, so please run the game from the terminal (navigate to the game directory and run it with ./hiddenassetdebug).
– Please take a screenshot of the debug information and paste it here or send it to me directly in an email, while also letting me know where you were in the game/what you were doing just before the crash.

(Note that on Linux, you may have to set the run permission of the executable with ‘chmod -x hiddenasset’ to allow you to run it, as the permission is sometimes lost when compressing the game files.)

 
-- Feedback --

When you’re done with the game, please send me the **stats.txt** file that on Windows and Linux will be located in the game directory and on Mac OS X will be in your ‘~/Library/Application Support/Hidden Asset’ directory. You can either email it to [email]contact@laserbrainstudios.com[/email] or write a post on the forums (as a guest, if you don’t feel like signing up) with a link to where I can download it. The stats.txt file contains information about time used in the game, when certain parts were reached, who you killed, how often and where you were killed, etc. No personal information or system information is gathered!

Also, please share any thoughts or comments about the game! Were certain parts too hard or too easy? Was the game fun? Too much or too little tutorial information?
 

-- Linux dependencies --
 
If you don’t already have SDL2, SDL2_mixer and SDL2_image installed on your system, they can be installed with the following commands in the terminal (given that they’re in your distribution’s repositories):

sudo apt-get install libsdl2-2.0
sudo apt-get install libsdl2-mixer-2.0
sudo apt-get install libsdl2-image-2.0

(Note that on Linux, you may have to set the run permission of the executable with ‘chmod -x hiddenasset’ to allow you to run it, as the permission is sometimes lost when compressing the game files.)

 
-- Screenshots --

[[img]https://s3-us-west-2.amazonaws.com/hiddenasset/screenshot05thumb.png[/img]](https://s3-us-west-2.amazonaws.com/hiddenasset/screenshot05.png)

[[img]https://s3-us-west-2.amazonaws.com/hiddenasset/screenshot06thumb.png[/img]](https://s3-us-west-2.amazonaws.com/hiddenasset/screenshot06.png)

[[img]https://s3-us-west-2.amazonaws.com/hiddenasset/screenshot07thumb.png[/img]](https://s3-us-west-2.amazonaws.com/hiddenasset/screenshot07.png)

[[img]https://s3-us-west-2.amazonaws.com/hiddenasset/screenshot04thumb.png[/img]](https://s3-us-west-2.amazonaws.com/hiddenasset/screenshot04.png)

[[img]https://s3-us-west-2.amazonaws.com/hiddenasset/screenshot01thumb.png[/img]](https://s3-us-west-2.amazonaws.com/hiddenasset/screenshot01.png)

[[img]https://s3-us-west-2.amazonaws.com/hiddenasset/screenshot02thumb.png[/img]](https://s3-us-west-2.amazonaws.com/hiddenasset/screenshot02.png)

[[img]https://s3-us-west-2.amazonaws.com/hiddenasset/screenshot03thumb.png[/img]](https://s3-us-west-2.amazonaws.com/hiddenasset/screenshot03.png)

---

### Post by toyson on 2018-07-30
Good, the game just keeps getting better and better

---

### Post by Christian Knudsen on 2018-07-31
Glad you like it! :D

---

### Post by Christian Knudsen on 2018-08-01
Hidden Asset v0.6.2.1 released!

This is a minor update that primarily fixes a potential crash when loading a game.


-- Download links --

North America:
[Windows 7 or later (128 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetwindows)
[Linux 32-bit (126 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetlinux32)
[Linux 64-bit (126 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetlinux64)
[Mac OS X 10.5 or later (156 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetmacosx)

Europe:
[Windows 7 or later (128 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetwindowseu)
[Linux 32-bit (126 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetlinux32eu)
[Linux 64-bit (126 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetlinux64eu)
[Mac OS X 10.5 or later (156 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetmacosxeu)

---

### Post by oldrocker99 on 2018-08-02
Thanks (as usual) for the timely update!

---

### Post by Christian Knudsen on 2018-08-14
Version 0.6.2.2 of the Hidden Asset alpha demo is now available for download and testing. Use the download links below. Savegames from previous versions won’t work in this new version.

Changelog:
– Fixed: Bug that would sometimes stop the player while automatically following an NPC.
– Fixed: Fast forward sometimes affecting cutscene playback speed.
– Fixed: Damage text on damage dealt by a thrown object including the word ‘CRITICAL!’.
– Added: Game now pauses when minimized.
– Changed: Doors unlocked with a keycard or keycode only need to be unlocked when entering.
– Changed: NPC rushing to help another NPC fight the player will react to seeing a corpse.
– Changed: Tech Eden owner will not walk out of the back room if the player is behind the counter.
– Changed: NPC that heard you will stand still and listen for a shorter time.
– Changed: Guard at Hensley International reacts to dishwasher turning on even if currently reacting to hearing the player.


-- Download links --

North America:
[Windows 7 or later (128 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetwindows)
[Linux 32-bit (126 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetlinux32)
[Linux 64-bit (126 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetlinux64)
[Mac OS X 10.5 or later (156 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetmacosx)

Europe:
[Windows 7 or later (128 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetwindowseu)
[Linux 32-bit (126 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetlinux32eu)
[Linux 64-bit (126 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetlinux64eu)
[Mac OS X 10.5 or later (156 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetmacosxeu)

---

### Post by Christian Knudsen on 2019-04-08
Version 0.6.3 of the Hidden Asset alpha demo is now available for download and testing. Use the download links below. Savegames from previous versions won’t work in this new version.

In this video, I talk about the long-requested features that have been added and briefly touch upon the upcoming Kickstarter crowdfunding campaign:

[https://www.youtube.com/watch?v=eXQoyn5cHGY](https://www.youtube.com/watch?v=eXQoyn5cHGY)

Changelog:
- Fixed: X-ray circle glitching out when player outside of view and entering view.
- Fixed: Potential elevator congestion issue.
- Fixed: Hensley International receptionist sometimes ending up standing inside the reception counter under specific circumstances.
- Fixed: Potential crashes when creating the selection border.
- Fixed: Selection border for doors with keycards/keypads being drawn offset if UI is not scaled to 100%.
- Fixed: NPC that had spotted you and is aiming weapon in your direction because you ducked to hide will now shoot immediately when you pop back up.
- Fixed: Moving cars leaving behind invisible walls.
- Added: Tutorial info about rotating the map.
- Added: Sound and visual effect when rotating the map.
- Added: If you scroll far off the map, text will tell you what button to press to center on player character.
- Added: Player's path shown (with option to only show it when in Tactical View).
- Added: Objects in front of player have transparency for 'x-ray' effect.
- Added: When dragging a device, an information box will tell you how to use it.
- Added: You can now also double-click on an item in a container/drawer to take it.
- Added: When left-clicking on a character or object you're right next to, the game will let you know (in case you're left-clicking in an attempt to interact with it instead of right-clicking).
- Added: Extra restrictions to try and keep panicking NPCs from cowering/hiding against a door.
- Changed: Larger 'x-ray' radius.
- Changed: Left-clicking on a selected object will make you walk up to the object, not to the non-highlighted selected tile 'behind' the object.
- Changed: Left-clicking on a door will always make you go to the tile on the other side of the door.
- Changed: Right-clicking while carrying corpse will make you walk to the selected tile and drop corpse there.
- Changed: If you click to shoot an NPC while moving but don't have a ranged weapon equipped, you won't stop moving.
- Changed: Interface hand icons (where you equip a weapon) are more distinct.
- Changed: "Above & Beyond Entrance Keys" instead of just "Above & Beyond Keys" to make it clear they can't be used to unlock a door inside the building.


-- Download links --

North America:
[Windows 7 or later (128 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetwindows)
[Linux 32-bit (126 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetlinux32)
[Linux 64-bit (126 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetlinux64)
[Mac OS X 10.5 or later (156 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetmacosx)

Europe:
[Windows 7 or later (128 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetwindowseu)
[Linux 32-bit (126 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetlinux32eu)
[Linux 64-bit (126 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetlinux64eu)
[Mac OS X 10.5 or later (156 MB)](http://www.laserbrainstudios.com/download.php?name=hiddenassetmacosxeu)

---

### Post by Christian Knudsen on 2019-04-16
[center][SIZE=5][color=green]**KICKSTARTER ANNOUNCEMENT**[/color][/SIZE]

**The Hidden Asset crowdfunding campaign will launch on Kickstarter on April 23rd at 11:00 am CDT / 4:00 pm GMT.**

[https://www.youtube.com/watch?v=TgLnk8x-gao](https://www.youtube.com/watch?v=TgLnk8x-gao)[/center]

---

### Post by oldrocker99 on 2019-04-16
I'm waiting...

---

### Post by Christian Knudsen on 2019-04-23
The wait is over...

[center][SIZE=6][color=green][HIDDEN ASSET IS LIVE ON KICKSTARTER!](https://www.kickstarter.com/projects/2034635017/hidden-asset-isometric-stealth-and-assassination-v)[/color][/SIZE]

[https://youtu.be/05LmKfH89ak](https://youtu.be/05LmKfH89ak)

[https://www.kickstarter.com/projects/2034635017/hidden-asset-isometric-stealth-and-assassination-v](https://www.kickstarter.com/projects/2034635017/hidden-asset-isometric-stealth-and-assassination-v)[/center]

---

### Post by Frogs Hair on 2019-04-23
Not a support request moved to *UL&OS Chat*.

---

