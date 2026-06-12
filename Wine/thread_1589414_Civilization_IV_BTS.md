---
title: "Civilization IV BTS"
date: 2010-10-06
forum: Wine
---

### Post by VietCanada on 2010-10-06
Here's my success story. Perhaps others will share by adding theirs?

With an Intel onboard Video card on an Asus P5KPL-AM Motherboard I had beautiful graphics, much, much superior to my Win 7 install but the game was too slow to play. I searched high and low, tried everything but could not increase the frame rate. I reinstalled Wine and Civ more often in the past few months than 10 years of reinstalling various versions of virus infected, comically inept MS OSs.

:KSLast weekend I installed an Asus EN9500GT (Nvidia) card with 1 gig ddr2 video memory, 800 mhz, MS DirectX 10 and OpenGL 2.0 support and increased my ram from 3gb to 4gb.

I went to **[http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu)** for the Nvidia driver. Actually I copied and pasted the above line into my software sources. I also allowed for experimental stuff to be searched for and added to my update choices.

I had no sound in the game until I opened **Configure Wine** from the **Applications** drop down menu and changed the audio from Alsa to OSS. Emulation. 16 bit, 48000 sample rate. In the game audio options I chose **use system configuration **and my own music file.

I used **winetricks** to install MSxml3 and d3dx9 first. I installed the games using the install button on the **Uninstall Wine Software** window and searching for the Autoplay or install exe's on the discs.  I deleted msxml3 ddl from the warlords and bts files after using **Browse C: Drive** to find the game folder. I am using the latest available versions of Ubuntu and Wine.

The graphics are perhaps a bit better than Win 7 but the speed of the game is the same now.

I uninstalled Win 7 and now have only Ubuntu on my machine. I have an Intel dual core E5200 and onboard sound card.

I hope this helps somebody.

:(OTOH I can't get Civ V working at all but perhaps it's because I have no intention of installing Steam. Thats Sid's choice not mine. Sid can feel free to install Steam  on his machine and love it all he wants but he has no business subsequently insisting that I do the same. I want Civ V. If I wanted Steam I'd already have it. Give your head a shake Sid.

Many months after finally taking the Linux plunge I can now enjoy my computing experience without taking out the MS mortgage and submitting to unseen, unwanted, self interested and greed based authoritarianism. I feel I've entered the modern age where I truly own my computer. I built it and I decide what software goes on it and what I do with it. Freedom. Nice try Bill. How's that Netscape thing working out BTW?

---

### Post by VietCanada on 2011-12-01
I still have the same hardware. Ubuntu 10.10 (64 bit) everything updated. Wine 1.3.33.
Medibunu, x-org.

I don't play online. I do play it often on my LG 42" at 1080 resolution.

To keep CIV BTS running well I have found it best to completely uninstall wine then reinstall it whenever Wine is updated or my kernel is updated. I should say I do this if I have any problems with the game after they update. But I seem to do it often.

I uninstall it with these commands-

[B]sudo apt-get remove --purge wine1.3
rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm[/B]

Then I open Synaptic search for Wine and completely remove anything that shows up.

I reinstall wine through the terminal-

[B]sudo apt-get  update
[/B]**sudo apt-get  install wine1.3**

Next I reinstall CIV BTS. I patch each game (3 disks) as I install them with every available patch.

I also install Blue Marble and The Bat Mod.

Next I open Winetricks and add corefonts and d3dx9_36 set to native.

Everything runs, I have sound but my victory movies freeze after they begin. The music continues though and I am able to view all the after game stuff. The movie problem did not go away after the latest purge and reinstall.

Hope this helps someone.

Maybe someone can help me with my victory movies!

:popcorn:

---

