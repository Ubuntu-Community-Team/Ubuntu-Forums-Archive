---
title: "mplayer... have to prime the pump"
date: 2014-09-23
forum: Ubuntu Studio
---

### Post by mashaffer on 2014-09-23
I am setting up a Ubuntu Studio system for a friend and have run into something I don't quite understand. After reboot (and probably fresh login haven't checked) if I try to play and audio file like a .wma file with any number of players that use mplayer it fails to run the file usually giving a message that mplayer is not running. However if I just once run mplayer in a terminal window with no arguments it prints out its help and exits and after that the players all work fine until the next reboot. (Note: Banshee seems to be unaffected and runs fine from the get go.)

Is there some sort of environment setup or domething that I need to do to get it to work properly?

mike

---

### Post by mashaffer on 2014-09-25
Sort of a head scratcher. On a lark I added a final line to  the profile to execute mplayer with no args. At first I thought it worked but sometimes it works fine after reboot other times the first attempt fails but killing the window and double clicking on the wma file again makes it work. Odd that it is not consistent.

mike

---

