---
title: "Lord of the Rings Online free version won't run"
date: 2010-10-16
forum: Wine
---

### Post by Gannin on 2010-10-16
I'm using Wine 1.3.5 on Ubuntu 10.04.

When I try to launch the new free version of LotRO, it crashes.

What I've done so far:

I used winetricks to download and install vcrun2008.

I was able to download and install Lord of the Rings Online by using the lotrostandard installer.

I downloaded and installed the Windows version of the PyLotRO launcher, the version you install into your wine prefix and use with wine.

I successfully patched LotRO to the latest version

What doesn't work:

If I select a server, any server, and try to log in, the resolution of the screen changes and the screen goes black for a second, then I'm returned to the desktop, with no error messages or anything.  It just simply doesn't start.  The PyLotRO window is still in the background saying "Finished", so you click on its exit button and wine closes.

Any thoughts?

---

### Post by slave-zeo on 2010-10-17
I had to stop using the windows/wine version of pyLOTRO because it stopped working for me. I use the native version now and it works as it should. I can say the free version of LOTRO works as it's running in the background right now. 

What graphics card you got? That might have something to do with your problem.

---

### Post by burg1n on 2010-10-17
I had a lot of problems installing and running LotRO, I explained how I fixed all of the problems here:

[http://ubuntuforums.org/showthread.php?t=1597792&highlight=lotro](http://ubuntuforums.org/showthread.php?t=1597792&highlight=lotro)

---

### Post by ajackson on 2010-10-17
> **Gannin said:**
> If I select a server, any server, and try to log in, the resolution of the screen changes and the screen goes black for a second, then I'm returned to the desktop, with no error messages or anything.  It just simply doesn't start.  The PyLotRO window is still in the background saying "Finished", so you click on its exit button and wine closes.
You might need to use winetricks to install the directx9 libraries (d3dx9 I think is the winetricks option).

---

### Post by Gannin on 2010-10-17
Thanks for the replies, I appreciate it :).

In order to get the game to start, I had to go into the wine control panel and change the sound from Alsa to OSS.  Then the game started and the sound during the game worked, but the sound during the movies didn't.  To fix that I had to change the sound from OSS to esound, now the sound works fine in the game and movies both.

---

### Post by McBipolar on 2010-10-17
I too am having an issue with LotRO, but don't want to start a new thread. I'm running Ubuntu Mint 9 and have followed the instructions found here: [http://lorebook.lotro.com/wiki/LOTRO_under_Linux_and_Mac_OS/X](http://lorebook.lotro.com/wiki/LOTRO_under_Linux_and_Mac_OS/X)

I'm running wine1.3. The main difference between my situation and every other guide I've read is that I have the DVD and have installed it on Windows 7 in VirtualBox. I updated the files until I can get to the login screen. Then I copied that directory to my ".wine-lotro" directory and used PyLotro accordingly. 

I'm finally able to patch it, but after I log in, I the following error: 

"Can't open the data files. Check that they exist and that you have permission to write to them. The program will now exist [201]."

And for those wondering, after I copied the folder from VirtualBox using a shared folder, I DID change the owner of the folders (and files within) to me.

---

### Post by ajackson on 2010-10-17
> **McBipolar said:**
> I'm running wine1.3. The main difference between my situation and every other guide I've read is that I have the DVD and have installed it on Windows 7 in VirtualBox. I updated the files until I can get to the login screen. Then I copied that directory to my ".wine-lotro" directory and used PyLotro accordingly. 

I'm finally able to patch it, but after I log in, I the following error: 

"Can't open the data files. Check that they exist and that you have permission to write to them. The program will now exist [201]."

And for those wondering, after I copied the folder from VirtualBox using a shared folder, I DID change the owner of the folders (and files within) to me.
Are they read-only? Also because of the way you installed the game you might need to instal the Visual C++ 2005 runtime as well.

Which DVD did you use, was it Shadows over Angmar or Mines of Moria?

---

### Post by McBipolar on 2010-10-17
I used the DVD Shadows of Angmar. I did run the update within Virtualbox and brought it up to the login screen before I copied the folder over. And yes, I have already installed vc2005 and vc2005sp1.

---

### Post by McBipolar on 2010-10-17
I got things working, but from downloading the files from the Lotro site on Windows 7 in Virtualbox and copying them to Mint. Followed the instructions, and everything works as expected, with the exception being unable to set my windowed mode properly. But I can live with that. All told, it looks like I only wasted $10 for the Shadows of Angmar DVD. Oh well.

---

### Post by Gannin on 2010-10-17
> **McBipolar said:**
> I got things working, but from downloading the files from the Lotro site on Windows 7 in Virtualbox and copying them to Mint. Followed the instructions, and everything works as expected, with the exception being unable to set my windowed mode properly. But I can live with that. All told, it looks like I only wasted $10 for the Shadows of Angmar DVD. Oh well.

You might be able to get around the window issue by going to the Graphics tab on the wine control panel and creating a virtual desktop, then have the game run in full-screen mode within that virtual desktop.  The game will think it's running in full-screen when you're actually getting the window that you want.

---

### Post by ajackson on 2010-10-17
> **McBipolar said:**
> All told, it looks like I only wasted $10 for the Shadows of Angmar DVD. Oh well.

I don't know they make good coasters to put your cup on and fly quite well as frisbees, I'm more amazed you managed to find a SoA DVD :)

---

### Post by burg1n on 2010-10-18
do you use CCSM? I was having CCSM problems and my windowed mode wasn't working until my CCSM problems were resolved, specifically, a problem with the compositor i was using (metacity)

Also, I'm not sure why exactly but every guide I've looked at said do NOT use the cd/dvd and to just download the client from the website.

But all of the guides I've seen are also very outdated

---

