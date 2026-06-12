---
title: "Can someone make a video?"
date: 2010-04-20
forum: Wine
---

### Post by Confusedlol on 2010-04-20
Showing how to do this? Because i have absolutely NO idea what this is talking about...All i'm reading is gibberish.


Make sure you have the following packages installed before you start:
1# aptitude install libgl1-mesa-dev x11proto-gl-dev libasound2-dev
At least these were the packages I had to install in Hardy to get Wine to compile with OpenGL and ALSA support (crucial if you want to get the game to run at all and with sound as well).
Grab the latest Wine source (1.1.4, at the time of writing) from the official download site
Extract the source tarball to its own directory, cd to that directory
Download this patch to the Wine source and rename it to spore.patch
cd into the wine-x.x.x subfolder with the actual source
Apply the patch by issuing the following command:
$ patch -p1 < ../spore.patch
If the patching was successful, compile and install Wine with the following command:
$ tools/wineinstall
Make yourself a sandwich and some coffee, because the compiling may take a while depending on how fast your CPU is (it took roughly 20 minutes on my 2.5 GHz Core 2 Duo). When Wine asked me if I wanted to install the compiled version to my system, I answered “yes” and consequently had to enter my root password before the installation stage. If you do not want to install the patched version permanently, answer “no”.
Install Spore with the installer from the CD and cancel the DirectX install popup. The install should finish normally. If Wine hangs a bit, leave it to do its thing for a few minutes.
Crack Spore’s stupid DRM (see disclaimer up top!).
Start the game with the provided Wine launcher or by going to the game’s Sporebin directory and typing $ wine SporeApp.exe in the terminal. Enjoy!

---

### Post by hikaricore on 2010-04-20
Seems to be pretty clear to me.
Follow the directions you pasted.

But first I would check the appdb to see if this patch is even needed anymore.
Before you drive yourself insane with your own inability to follow instructions.

---

### Post by Confusedlol on 2010-04-20
Instructions? I know that much that they're instructions but it doesn't show how to do what it's asking me to do...What's a appdb?

---

### Post by 3rdalbum on 2010-04-20
Firstly, don't use old instructions with new versions of Ubuntu. "Hardy" is Ubuntu 8.04, the current version of Ubuntu is 9.10 (18 months newer).

Secondly, there is a program called Play On Linux that can automatically set up Wine for you to play certain games that are on its supported list. Spore is on the supported list (you might need to use a cracked version, that is, one that has the DRM copy prevention removed from it).

If you're using Ubuntu 9.10 or higher, then Play On Linux is in the repositories already.

---

### Post by 3rdalbum on 2010-04-20
> **Confusedlol said:**
> Instructions? I know that much that they're instructions but it doesn't show how to do what it's asking me to do...What's a appdb?

AppDB is this: [http://appdb.winehq.org/](http://appdb.winehq.org/)

Click on Browse Apps to start.

But try Play On Linux first.

---

### Post by Confusedlol on 2010-04-20
Alright thanks :). How do i figure out which Ubuntu i have? If i'm not mistaken i have 8.04, it's what came with the computer. Is there like a disc or something i need for 9+?

---

### Post by Confusedlol on 2010-04-20
Well i tried to install it =\. It said Archive not supported, or something like that.

---

### Post by Confusedlol on 2010-04-21
Any ideas?

---

