---
title: "EVE Online How-To"
date: 2011-03-19
forum: Wine
---

### Post by mg.mattgonterman on 2011-03-19
I haven't really found a good post that informs an individual on how to install EVE Online under Ubuntu, so I figured I would post my own how-to.  Just about everything works perfect, except the fact that I do not have sound and if I alt-tab out, EVE freezes.  Here it goes...

1. Download the EVE Online Client (using a fresh copy of EVE offline installer as of 03/19/2011)

2. Install WINE. (Using version 1.2.2-0ubuntu2-maverick2)
2a. Open a Terminal and type "sudo apt-get install wine".
2b. Don't add the quotes of course.  Accept the license at your own will.

Becaues the EULA requires Arial, you will need to do the following:
3. Download the Arial True Type Font.
3a. Source: [http://www.4shared.com/get/h6VD3TRz/arial.html](http://www.4shared.com/get/h6VD3TRz/arial.html)
3b. Copy or move the arial.ttf file to the WINE folder.
3ba. Navigate to your home folder.
3bb. Click EDIT, then PREFERENCES.  Check "Show hidden and backup files".  Close the window.
3bc. Go to .wine/drive_c/windows/Fonts and put the font file in there.
3bd. Close the explorer.  Undo the changed in step 3bb if you like.

4. Open your download directory and edit install EVE under WINE.
4a. Permissions Tab: Check the box next to "Allow executing file as a program".  Click close once complete.
4b. Right-click the installer and "Open with Wine...".

--The installer should begin to run.  Follow the steps and use common sense when installing.

Once the install is complete, run it.  Works for me with the nVidia proprietary drivers.

---

### Post by draconastar on 2011-05-07
Thanks for your post!  

After running into a few bumps with the install (the downloader constantly wanted to repair the file and then couldn't find the C++ package it needed to do so), I managed to get EVE installed to it's most up-to-date patch.  However, whenever I run EVE, I can start it, get it loaded and login, but then as soon as I do, the music freezes a couple of seconds later, and then seconds after that the entire program freezes, forcing me to kill the process every time.  I have no idea what's causing it!  I'm currently running Wine 1.2.2 in Ubuntu 11.04.  

Any ideas?

---

### Post by speedkreature on 2011-05-13
What audio chipset do you have? Graphics card?
 
My setup is as follows:
Lenovo T510
* Intel i7 620M
* nVidia NVS 3100M
* Conexant 20585 SmartAudio HD
* 8GB RAM
* Ubuntu 11.04 64-bit
 
I did the following:
 
Add wine repository...
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```
 
Install wine 1.2.x...
```
sudo apt-get update && sudo apt-get -y install wine
```
 
With that, wine and winetricks (and a few other bits and pieces) should be installed.
 
Now, install VC2005, VC2008, and the MS core fonts...
```
wintricks vcrun2005
winetricks vcrun 2008
winetricks corefonts
```
 
Some of the posts I've seen recommend installing the gecko backend. You can do this with winetricks as well.
```
winetricks gecko
```
 
 
Having done all of that, I have no problems installing or starting the game. Playing is a bit laggy and my sound starts to chop after character selection, but the game is stable. For me it doesn't make any difference in performance if I'm using Nouveau drivers or the proprietary binary drivers and stability is worse for me with the proprietary drivers (not to mention I lose 3D support on the desktop with the proprietary drivers, a known bug for the T-series).
 
I hope this helps someone. If anyone knows the solution to any of the issues posted to this thread so far, please contribute. I'll be happy to post the end result to the EVE formus so someone can update the Linux install wiki.

---

### Post by leozar100 on 2011-05-13
if you have ubuntu 11.04 try entering the following into terminal it's a lot easier:
```
winetricks eve
```
this will download the latest build of eve online and install it into the correct directories. I have not launched it yet because it's 3.7 GB to download.

---

### Post by adf on 2011-05-21
I did 'winetricks eve' in 11.04. EVE started very nicely and then tried to update. It looks like the eve patch under wine expects eve to be in .wine/drive_c/Program Files, when the actual program is installed .local/share/wineprefixes/eve by winetricks. As a consequence I am having difficulty patching EVE. How do you patch eve with the official updates after having installed with winetricks?

---

### Post by Rikeshar on 2011-05-23
I'm having some trouble with the sound on EVE. I'm using PlayOnLinux and Ubuntu 11.04. I have renamed the Jukebox folder, so that's not a problem. What happens is that intermittently my EVE client will lose all sound. Everything else on the computer has sound, just not EVE. Often I have to reboot the whole computer just to get it back. I'm using the ALSA drivers. I've tried OSS but I get no sound at all. Any ideas?

---

### Post by Celliman on 2011-06-18
Hi,

if you want to upgrade Eve just download the patch and install it manually in the bottle.
You need to create a symlink.  
   
    "ln -s /home/yourhome/.local/share/wineprefixes/eve/drive_c/Programme/EveDirectory  /home/yourhome/.wine/drive_c/Program Files/yourEveDirectory."

After that it is possible to upgrade Eve. Just choose the right directory if it is requested.

---

### Post by sohlside on 2011-07-11
> **Celliman said:**
> if you want to upgrade Eve just download the patch and install it manually in the bottle.

What does "in the bottle" mean?

---

### Post by buzzinh on 2013-01-14
wine...bottle

---

