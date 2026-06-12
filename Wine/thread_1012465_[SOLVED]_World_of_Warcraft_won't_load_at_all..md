---
title: "[SOLVED] World of Warcraft won't load at all."
date: 2008-12-15
forum: Wine
---

### Post by slammed87d21 on 2008-12-15
For some reason, trying to load installer.exe on the install DVD, nothing happens and my DVD drive goes nuts. I did what the Wiki said, but it doesn't seem to work. Any suggestions?

---

### Post by slammed87d21 on 2008-12-15
A little more info on what's happening, when I try to run the installer it says Cannot find installer file I think. slows my comp down really bad.

---

### Post by Sandlst on 2008-12-15
Could you please give a link to the wiki you are following?  One thing you might want to try is to copy the contents of the dvd to a folder in your hard drive, then try running the installer from there.  Several years ago, this was required to install WoW, although I thought this was no longer necessary.  I have a copy of WoW on an external HD, I don't even remember the last time I had to install it.

---

### Post by slammed87d21 on 2008-12-15
[http://ubuntuforums.org/showthread.php?t=579378&highlight=World+Warcraft]("http://ubuntuforums.org/showthread.php?t=579378&highlight=World+Warcraft")

I tried that one and the link in it.I also tried copying the disc to my drive.

---

### Post by Sandlst on 2008-12-15
So I'm guessing the step that you are stuck on is this one: > **Sammi said:**
> 4. Open a terminal and do these commands inside to start the installation:
```
cd /<path-to-directory>/
wine Installer.exe
```*Replace <path-to-directory/> with the right path to the directory where you copied all the files.*
The terminal should print out an error message of some kind, could you please post exactly what it says?

---

### Post by slammed87d21 on 2008-12-15
heres what it said:

bash: cd: /File: No such file or directory

I put the folder on my desktop. what path would that be?

---

### Post by Sandlst on 2008-12-16
Ah, the path would be ```
cd ~/Desktop/FOLDERNAME
```where FOLDERNAME is the name of the folder you made on the desktop.

~ is just a shortcut for /home/USER by the way.

---

### Post by slammed87d21 on 2008-12-16
Ok, got it right this time. Here's what it said:

slammed87d21@slammed87d21-laptop:~$ cd ~/Desktop/WoW
slammed87d21@slammed87d21-laptop:~/Desktop/WoW$ wine Installer.exe
slammed87d21@slammed87d21-laptop:~/Desktop/WoW$ 

Wine opened a window that said this also:

Installer

No installer data could be found. If this problem persists, please contact Blizzard Technical Support.


Am I doing something wrong?


Right after I posted this, this came up in Terminal:

slammed87d21@slammed87d21-laptop:~/Desktop/WoW$ fixme:richedit:IRichEditOle_fnGetClientSite stub 0x14d32a8
fixme:ole:OleCreateStaticFromData (not shown), stub!

---

### Post by Sandlst on 2008-12-16
No, you are doing it correctly.
> **slammed87d21 said:**
> 

Right after I posted this, this came up in Terminal:

slammed87d21@slammed87d21-laptop:~/Desktop/WoW$ fixme:richedit:IRichEditOle_fnGetClientSite stub 0x14d32a8
fixme:ole:OleCreateStaticFromData (not shown), stub!

lines starting with "fixme:" are not actual error messages, they are notes to the developers that certain functions are not complete.  I would guess from the error message that there was some problem copying the dvd over; you can try copying the dvd contents again, but I would also try running the installation straight from the dvd first to possibly save time.  The path should be ```
cd /cdrom
``` and then run the installer as usual: ```
wine Installer.exe
```

---

### Post by slammed87d21 on 2008-12-16
Still says the same. Can't find installer data.

---

### Post by Sandlst on 2008-12-16
After some searching around, this seems to be a problem relating to the dvds themselves.  This seems to work for some people though: > ok heres what I did:

Inorder to mount the DVD with all the hidden files shown, I had to first unmount it. In a terminal type

Code:
sudo umount /media/cdrom0/
sudo mount /media/cdrom0/ -o unhide



now you should get a window opening up on your desktop showing you all the hidden files on the DVD
If doing that shows additional files on the cd that were not there before, copy those new files/folders over to the original folder you created on your desktop.  If this fails too, you could always go to the WoW community site and download the game client after logging in here: [https://www.worldofwarcraft.com/account/](https://www.worldofwarcraft.com/account/)

This method works with wine for sure although it will take forever to download the entire thing.  Alternatively, if you have access to a windows computer, you can install WoW onto that and then simply copy the World of Warcraft folder onto your ubuntu machine.  

Unfortunately there does not seem to be a simple quick fix for the problem you are having.

**EDIT**
There is one more way to possibly fix this, but it involves a lot of annoying complicated stuff, so I would rather not post it unless the above first command did not work as it *should* do the same thing.

---

### Post by slammed87d21 on 2008-12-17
Coudn't get it to work, so I just installed XP to dual-boot. Runs fine in XP. Thanks anyway.

---

### Post by cebe11 on 2009-01-03
@ sandlist ( or anyone for that matter!)
> **EDIT**
There is one more way to possibly fix this, but it involves a lot of annoying complicated stuff, so I would rather not post it unless the above first command did not work as it should do the same thing.


Could you give more details?
I've been trying to get the installer to work properly but keep getting these exact errors ( can't find installer data).

I umounted and remounted the DVD (Cdrom0), copied all the files ( including the hidden files)into a directory (~/wow1) and I keep getting this same error (can't find installer data).

I've also tried to run the installer.exe file right from the dvd using wine but get the exact same results.

I'm using fiesty with wine 1.0 installed.  I made no patches to wine, but got it from repositories as explained in the guide here [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Xtreme it on 2009-03-31
Any follow up in this issue?
Just bought WoW assuming I would play it in Ubuntu and I'm stuck at installation with the same issues described above.

I have a WoW in a DVD and Wine 1.1.18 installed from WineHQ. Currently running Ubuntu 8.04.

---

### Post by Sandlst on 2009-04-01
Even though I posted in this thread previously, I cannot seem to find the "other method" I was talking about back then, although I seem to remember it basically doing the same thing as another suggestion in this thread.  I would check out this page if I wanted to install WoW again (I still run from a usb drive): [http://www.wowwiki.com/Troubleshooting_Wine](http://www.wowwiki.com/Troubleshooting_Wine)
It seems to have some good info.

EDIT:  It seems there is another active thread with this issue, so read it if you have not already ([http://ubuntuforums.org/showthread.php?t=980629](http://ubuntuforums.org/showthread.php?t=980629))

---

