---
title: "Help! Robot Arena 2: Design and Destroy"
date: 2011-04-25
forum: Wine
---

### Post by RCROX2013 on 2011-04-25
Please help! I have tried running this under wine, but I have a problem. The game itself runs and boots up fine under wine, but the in game cursor does not move when I move the mouse over it. Like, say I have it set up in a virtual desktop. The mouse will move outside the desktop, but inside, where the game is, the in game cursor does not move. Please help, I have tried everything I know, and I am stuck! Thank you in advance. Oh, and running it outside of the virtual desktop doesn't change anything, the cursor still does not move. :(

---

### Post by Perfect Storm on 2011-04-25
Moved to UF wine forum.

---

### Post by Butthead on 2011-04-26
Um, probably a dumb question, but you did fart around with the Wine preferences settings, right? :confused:

I seem to remember a setting for getting the mouse to work in a game window there. 

Found under the "Emulator" Linux Main menu choice (I believe?). :confused:

(Sorry, I had to do a Linux re-format a few days ago, and haven't gotten around to re-installing Wine yet). :(

---

### Post by c_wolff on 2011-11-16
Hi, found a way to run Robot Arena 2 in ubuntu 11.04:

-Install VirtualBox version 4.x
-install XP as guest
-install Guest Additions (virtualbox menu -> Devices -> Install Guest Additions). Do this in guest XP safe mode. Enable 3D acceleration
-reboot guest XP in normal mode
(EDIT)-install directx 8.1 or 9. I've installed directx 9 with no problem.
-install robot arena 2 (skip directx 8.1 install)

To avoid mouse too sensitive in game, Disable Mouse Integration through menu Machine->Disable Mouse Integration

-run the game

Obs: In VirtualBox, the HOST key usually is RIGHT CTRL

Robot Arena 2 will not stretch to the host screen resolution. To do so you must rescale your host resolution to 800x600, for an example. Guest will follow your host screen resolution

Hope it helps

---

