---
title: "StarCraft Battle.net on Ubuntu"
date: 2008-12-22
forum: Wine
---

### Post by Inxi on 2008-12-22
The game works as long as the CD is in, LAN works, UDP works, campaign works, whatever. The game runs fine both fullscreen and windowed (through Wine's emulated desktop). But, if I go to Battle.net, any Gateway, Battle.net tells me it *can't recognize my version*. I am stuck here (the game freezes)... The window looks like this: [http://appdb.winehq.org/appimage.php?iId=8358](http://appdb.winehq.org/appimage.php?iId=8358)
Sometimes there's no text. Sometimes there is.

I don't want to hear any "it doesn't work/not supported by wine" because it does and is, and you can go to this page for proof: [http://appdb.winehq.org/appimage.php?iId=12011](http://appdb.winehq.org/appimage.php?iId=12011)
If they did it, I can too. If it's truly impossible, I want to know why. Maybe it only works in older versions, I don't know. I want an older version then, I just don't know how to do it.

I want to run StarCraft Battle.net on Ubuntu, e.g., the **multiplayer**. I have a legal version of StarCraft Brood War 1.16 with a working CD-key. Please note that I am on a dual-boot, and I do have a Windows side, and, yes, I can just install StarCraft there and play it with no problems, but I have a desire to kill myself (e.g., figure out how Wine and Ubuntu work). Besides, I hate switching to Windows. I have an ATI video card with a stupid proprietary driver but I doubt this is the issue here. My processor is i386 or whatever.

I decided to restart the thread since my issues are more related to StarCraft than anything else, and not all guides say I need to run it as root.

I found a LOT of guides, including some on this forum, but many of them offer all sorts of random advice and are for older versions of Ubuntu, it seems. I really don't want to break my system. I read these:
[http://ubuntuforums.org/showthread.php?t=572122](http://ubuntuforums.org/showthread.php?t=572122)
[http://www.linuxquestions.org/questions/linux-games-33/has-anyone-got-starcraft-bwbattle.net-working-619471/](http://www.linuxquestions.org/questions/linux-games-33/has-anyone-got-starcraft-bwbattle.net-working-619471/)
[http://www.xanga.com/Susiekins/572913682/linux-and-starcraft-battlenet.html](http://www.xanga.com/Susiekins/572913682/linux-and-starcraft-battlenet.html)
If you have something to say about what they propose (bad advice, weird advice), do it. Because I'm clueless and my computer is a guinea pig.

This is what I had done so far:
Installed StarCraft and StarCraft: Brood War from CD's using Wine to the virtual C:\Program Files\StarCraft folder. I've reinstalled the game 6 times now.
Patched it to 1.16 with the Blizzard Brood War 1.16 patch exe (which was ran through Wine).
At this point, SC works fine if I both run the actual StarCraft.exe through Wine, or if I make a launcher with the following command:
env WINEPREFIX="/home/inxi/.wine" wine "C:/Program Files/Starcraft/StarCraft"

In addition to that, I have done the following:
- installed msttcorefonts.
- deleted these fonts:
/usr/share/wine/fonts/sserife.fon
/usr/share/fonts/truetype/ttf-arabeyes/ae_AlBattar.ttf
/usr/share/fonts/truetype/ttf-devanagari-fonts/samanati.ttf
- went to "wine regedit", and added the following string in HKEY_CURRENT_USER\Software\Wine\Direct3D\
string DirectDrawRenderer value "gdi" 
(before I did all above, the battle.net screen was black and had white text "Create Account" and "... Password")
- installed ipx
- modified /etc/ipx.conf by adding IPX_NETNUM 00000 with nano and ran /etc/init.d/ipx start before running StarCraft like I was told to with some other guide. Didn't help.
>>> 
I am sure I have done that incorrectly. The guy said add IPX_NETNUM 00000 to the file. He didn't say where. So I put it at the end. Then after "sudo /etc/init.d/ipx start" the system told me they get an error at line 15. So I found the IPX_NETNUM 0 that was in there already and replaced it with 00000. I'm pretty sure that's not what the guy had in mind. So any advice here is welcome.
>>>
- I tried to run StarCraft as root, but was not able to (the program asks for password, accepts it, and does not run). I described my issues with running as root in this thread: [http://ubuntuforums.org/showthread.php?t=1018328](http://ubuntuforums.org/showthread.php?t=1018328)
Nobody knows what it is so I'm thinking it's a bug within my system.
Adding "gksu" in front of my uTorrent command doesn't cause any issues. o.O

- I tried to downgrade to an older version of Wine, but was not able to do so because when I downloaded an older package(9.45), it told me it had a disagreement with something and did not permit me to install the package... I was downloading [http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine-dev_0.9.45~winehq0~ubuntu~7.04-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine-dev_0.9.45~winehq0~ubuntu~7.04-1_i386.deb)
Error: Dependency is not satisfiable: wine
Perhaps it's impossible to downgrade so far?

So, is anyone here playing StarCraft Brood War Battle.net on Intrepid Ibex? :)

---

### Post by Pobega on 2008-12-24
The trick is simple; in *winecfg*, under the graphics tab, make sure that you have "Allow the window manager to control the windows" UNCHECKED. For some reason when this is checked StarCraft reports version 0.0.0.0 to Bnet.

---

