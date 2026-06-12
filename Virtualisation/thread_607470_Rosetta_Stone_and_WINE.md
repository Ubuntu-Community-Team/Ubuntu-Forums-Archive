---
title: "Rosetta Stone and WINE"
date: 2007-11-09
forum: Virtualisation
---

### Post by employeeno5 on 2007-11-09
I've trolled previous threads and haven't found any addressing this issue yet (at least as far as I understand my problem) so please hear me out.
Also, I hope this is the appropriate forum for WINE issues. Forgive me if it's not.

So, I'm using Gutsy 7.10 and am attempting to get the Rosetta Stone working for my for my girlfriend. She has Rosetta Stone version 2.1.5.2A

I installed wine. I then used wine to install the Rosetta Stone from it's installation CD. It appeared to install the program without any hiccups or problems.
Now, when I put in the language CD and go to run the program I get a splash screen and then nothing. You can hear that once starting the program that it does access the CD while the splash screen goes up, but it quickly loses interest and nothing more happens.
No error messages or anything. It's like all it wants to run is the splash screen and then it's happy to quietly turn itself off.

I'm fairly new to Linux. I know that there may be nothing to be done to get this program to work, but as I'm pretty new I just wanted to check in see if I was missing something obvious or if anyone had any ideas or solutions. 

Many thanks for any thoughts on the issue.

---

### Post by hardyn on 2007-11-09
there are no promises that anything will work with wine, but alot does.  any low level hardware calls (copy protection) will most likely fail with wine.  I am no expert in either rosetta or wine, but it might be a better use of time to dual boot ubuntu, or virtualize windows XP

---

### Post by MrFSL on 2007-11-09
When diagnosing ANY WINE issue (or any Linux issue for that matter) It always help to run the application from the terminal and post the output.

Example:```
wine /path/to/program.exe
```

---

### Post by employeeno5 on 2007-11-09
Ah yes, thanks. I plumb forgot to check out my terminal out-put.
Here we go.

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:process:IsWow64Process (0xffffffff 0x34efac) stub!
fixme:advapi:QueryServiceObjectSecurity 0x124988 4 0x1249c0 0 0x34ef30 - semi-stubXlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:process:IsWow64Process (0xffffffff 0x34efac) stub!
fixme:advapi:QueryServiceObjectSecurity 0x124988 4 0x1249c0 0 0x34ef30 - semi-stub
fixme:advapi:QueryServiceObjectSecurity 0x124988 4 0x1249c0 28 0x34ef30 - semi-stub
fixme:advapi:SetEntriesInAclA 1 0x34eec0 0x1249d4 0x34ef2c
fixme:advapi:SetServiceObjectSecurity 0x124988 4 0x34eeac
fixme:process:IsWow64Process (0xffffffff 0x34f66c) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34e734) stub!.
fixme:advapi:QueryServiceObjectSecurity 0x124988 4 0x1249c0 28 0x34ef30 - semi-stub
fixme:advapi:SetEntriesInAclA 1 0x34eec0 0x1249d4 0x34ef2c
fixme:advapi:SetServiceObjectSecurity 0x124988 4 0x34eeac
fixme:process:IsWow64Process (0xffffffff 0x34f66c) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f618) stub!
fixme:process:IsWow64Process (0xffffffff 0x34e734) stub!
```

As for the previous reply I got:

Yes, I thought that may well be the case. I do have a dual boot of Windows on my Dell and it runs fine in it of course. I'm mainly testing to see if I can get it running in Linux because I rebuilt an old iBook very cheaply out of spare and used parts as a Christmas present for my girlfriend.

She doesn't use a computer for anything but web browsing and email. Anything except for her Rosetta Stone. I've been hoping to install a Linux distro. on it instead of buying Panther or Tiger and having them run rather slow on the older equipment when she's not doing anything that requires much power.

I'd love to install Ubuntu or Xubuntu on it, but she won't want something without her Rosetta Stone. It's not a huge deal; Rosetta Stone will run fine in OS X 10.3 and up and she could care less what operating system she's using. She'll be thrilled just to have her own computer in her lap while I'm working and that it's small and "cute" (She loves that Apple Glacier color. She got her iPod and DS Lite that way and wants a computer that color too.)

I really hope I can make this work, but like I said, there's always OS X.

---

### Post by hardyn on 2007-11-09
the first few error messages are regarding video, perhaps you need an accelerated video driver for rosetta?

---

### Post by employeeno5 on 2007-11-09
huh. I don't know. I'm thinking it may have to do with quicktime. On my first installation of Rosetta Stone it also installed automatically an ancient version of quicktime which doesn't appear to run. I'm trying to re-install quicktime in wine or try a new version... I don't know yet, we'll see.
If it does require a video driver I don't know what. I've got a driver installed for my ATI accelerated graphics that works great with everything else..

---

### Post by gubemton on 2007-11-09
I am having similar problems.
Actually, all of the video part works fine (I mean that i don't receive any error messages about video), so my terminal output looks much like that which you have.

The problem is that when the program loads, it can't find any of the "Language data."  I've browsed around a little bit in the directory to which i mounted the iso image of the dvd, and it seems to be composed of pdf's and other directories arranged by chapter, in which directories are semi-text files (they display as some text with some mixed up, non-ascii characters) and also the mp3 files that it plays as part of the program (it shows you a four pictures, and then plays a sound file that says a word in chinese, and then the user is supposed to click on the correct picture, the one that the word describes, etc.).

Anyway, does anybody have any ideas to fix such a problem, where the Rosetta Stone program does not know where to find the files it needs?  It is too bad that it doesn't tell me where it looks, even.

Here is what I get at the terminal:
```
me@sea:/media/iso$ wine autorun.exe
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,0,3): stub!
fixme:win:SetLayeredWindowAttributes (0x10030,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,20,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,40,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,60,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,80,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,100,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,120,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,140,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,160,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,180,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,200,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,220,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,240,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,255,3): stub!
fixme:win:SetLayeredWindowAttributes (0x10030,0x00000000,80,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,235,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,215,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,195,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,175,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,155,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,135,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,115,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,95,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,75,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,55,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,35,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,15,3): stub!
fixme:win:SetLayeredWindowAttributes (0x1002c,0x00000000,0,3): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,255,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,235,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,215,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,195,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,175,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,155,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,135,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,115,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,95,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,75,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,55,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,35,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,15,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002e,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,20,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,40,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,60,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,80,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,100,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,120,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,140,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,160,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,180,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,200,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,220,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,240,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,255,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002e,0x00000000,80,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,235,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,215,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,195,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,175,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,155,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,135,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,115,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,95,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,75,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,55,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,35,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,15,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20030,0x00000000,0,2): stub!


```

---

### Post by siciliancasanova on 2007-11-24
I just installed Rosetta Stone no problems on WINE in 7.10

Although my files came from .torrent and not the cd rom so my languages weren't on a disk I just copied them into the file system.

---

### Post by firebrother15 on 2007-11-29
Hey Employeeno5. I'm still trying to get it running as well, but I might be able to solve your problem. I'm actually running Fedora 8 instead of Ubuntu so it may be completely different, but here-goes anyway.

All I had to do to get it working was uncheck the "allow windows manager to control windows" box on the graphics tab of winecfg. After that Rosetta Stone started just fine, including the old quicktime version. I'm still having trouble getting it to recognize the language disc, but that's another problem altogether...

---

### Post by employeeno5 on 2007-11-29
Thanks for the tip.
I'll try that out and see if it makes any difference.

---

### Post by Xanderfoxx on 2007-11-30
> **siciliancasanova said:**
> I just installed Rosetta Stone no problems on WINE in 7.10

Although my files came from .torrent and not the cd rom so my languages weren't on a disk I just copied them into the file system.

How did you manage this?

What website/source? I did not know Rosetta has Linux binaries. If I did, I wouldn't hesitate in switching to Ubuntu GNU/Linux.

I would appreciate your feedback.:lolflag:

Thanks.

---

### Post by Xanderfoxx on 2007-11-30
[COLOR=Black][FONT=Lucida Sans Unicode][SIZE=3]I attempted to install:

[/SIZE][/FONT][/COLOR][INDENT][COLOR=Black][FONT=Lucida Sans Unicode][SIZE=3]Rosetta Stone Demo CD-ROM Version 2 - Home Series,[/SIZE][/FONT][/COLOR]
[/INDENT][COLOR=Black][FONT=Lucida Sans Unicode][SIZE=3]and I got this feedback:

[/SIZE][/FONT][/COLOR]```

alex@alex-laptop:~$ cd /media/cdrom0
alex@alex-laptop:/media/cdrom0$ wine setup.exe
cwd: C:\windows\temp\I1196443250\Windows
cmd: "C:\windows\temp\I1196443250\Windows\resource\jre\bin\javaw.exe" -Xms16777216 -Xmx50331648 -classpath "C:\windows\temp\I1196443250\InstallerData\IAClasses.zip;C:\windows\temp\I1196443250\Windows\resource\jdglue.zip;C:\windows\temp\I1196443250\InstallerData\Execute.zip;C:\windows\temp\I1196443250\Windows\InstallerData\Execute.zip;C:\windows\temp\I1196443250\InstallerData\Resource1.zip;C:\windows\temp\I1196443250\Windows\InstallerData\Resource1.zip;C:\windows\temp\I1196443250\InstallerData;C:\windows\temp\I1196443250\Windows\InstallerData;" com.zerog.lax.LAX "C:/windows/temp/I1196443250/Windows/Setup.lax" "C:/windows/temp/lax56eb.tmp" 
fixme:msvcrt:MSVCRT__sopen : pmode 0x01b6 ignored
Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.NoClassDefFoundError
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Unknown Source)
        at java.awt.Toolkit$2.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Unknown Source)
        at sun.awt.GlobalCursorManager$CursorEvent.<init>(Unknown Source)
        at sun.awt.GlobalCursorManager.<clinit>(Unknown Source)
        at java.awt.Cursor.initIDs(Native Method)
        at java.awt.Cursor.<clinit>(Unknown Source)
        at java.awt.Window.<init>(Unknown Source)
        at java.awt.Frame.<init>(Unknown Source)
        at java.awt.Frame.<init>(Unknown Source)
        at com.zerog.ia.installer.LifeCycleManager.f(DashoA8113)
        at com.zerog.ia.installer.LifeCycleManager.g(DashoA8113)
        at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
        at com.zerog.ia.installer.Main.main(DashoA8113)
        at java.lang.reflect.Method.invoke(Native Method)
        at com.zerog.lax.LAX.launch(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)
err:heap:HEAP_ValidateInUseArena Heap 0x110000: in-use arena 0x127c80 next block has PREV_FREE flag
alex@alex-laptop:/media/cdrom0$ 


```

[COLOR=Black][SIZE=3][FONT=Lucida Sans Unicode]If you need more information, please feel free to ask.

Thank you in advance.
[/FONT][/SIZE][/COLOR]

---

### Post by NotoriousMOK on 2007-12-16
> **firebrother15 said:**
> All I had to do to get it working was uncheck the "allow windows manager to control windows" box on the graphics tab of winecfg.

This worked good for me -- thanks!

(Gutsy on a Toshiba Tecra M3)

---

### Post by thenava on 2007-12-21
I got it to run by doing the following:

run winecfg and go to the drives tab.
hit 'Add', and create a new drive, D or whatever
set the path to /media/cdrom0

That should settle the no language source error.

If you are using an iso, mount it to /media/cdrom0:
sudo mount filename.iso /media/cdrom -t iso9660 -o loop

Hope it works.

---

### Post by Nexusx6 on 2008-01-12
I also need help in Rosetta Stone. Despite a gold raiting on just about every version in the AppDB I always crash :frown:

It installs perfectly, and runs just fine, but when I get to the screen where you get to choose which language to load it will either:
a)Crash with "A Fatal Error has occured" instantly if I already have the language mounted
b)Crash with the same error if I load the language after the program starts.

I tried a few versions of the application (2.0.6.1A, 2.0.8.1A) and mutlipul versions fo the language pack, all failing ; ;

Here's my Wine readout when run from the console:
```
$ wine TheRosettaStone.exe 
fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\system32\\tmpF9C82.FOT","C:\\windows\\temp\\AAX8c9b.tmp",(null)): stub
fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\system32\\tmp3BC82.FOT","C:\\windows\\temp\\AAX8cb1.tmp",(null)): stub
fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\system32\\tmpCCC82.FOT","C:\\windows\\temp\\AAX8cc8.tmp",(null)): stub
fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\system32\\tmp5EC82.FOT","C:\\windows\\temp\\AAX8ce1.tmp",(null)): stub
fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\system32\\tmp9FC82.FOT","C:\\windows\\temp\\AAX8cf5.tmp",(null)): stub
fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\system32\\tmp41D82.FOT","C:\\windows\\temp\\AAX8d11.tmp",(null)): stub
fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\system32\\tmpB2D82.FOT","C:\\windows\\temp\\AAX8d27.tmp",(null)): stub
fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\system32\\tmpA5D82.FOT","C:\\windows\\temp\\AAX8d58.tmp",(null)): stub
fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\system32\\tmp97D82.FOT","C:\\windows\\temp\\AAX8d74.tmp",(null)): stub
fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\system32\\tmpD8D82.FOT","C:\\windows\\temp\\AAX8d8a.tmp",(null)): stub
fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\system32\\tmp2AD82.FOT","C:\\windows\\temp\\AAX8d9d.tmp",(null)): stub
fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\system32\\tmpFCD82.FOT","C:\\windows\\temp\\AAX8dc9.tmp",(null)): stub
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:font:get_nearest_charset returning DEFAULT_CHARSET face->fs.fsCsb[0] = 00000000 file = /home/fox/.wine/dosdevices/c:/windows/fonts/vgaoem.fon
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:font:get_nearest_charset returning DEFAULT_CHARSET face->fs.fsCsb[0] = 00000000 file = /home/fox/.wine/dosdevices/c:/windows/fonts/vgaoem.fon
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
wine: Call from 0x73c21895 to unimplemented function GDI32.dll.NamedEscape, aborting

```

I would really appreciate any help

---

### Post by fjgaude on 2008-01-12
It would surely work, run correctly if you used VMware Server or VirtualBox, instead of wine.

---

### Post by theZoid on 2008-01-12
> **fjgaude said:**
> It would surely work, run correctly if you used VMware Server or VirtualBox, instead of wine.

Yes, that is another option for sure.  I run some proprietary tax programs (professional vertical market) in an XP virtual machine and they run perfectly....actually, everything does so far.  and fast.

---

### Post by dcperkins on 2008-01-14
this thread is extremely helpfull. thanks !

---

### Post by FrankVdb on 2008-01-16
Yes, installing Rosetta in a virtual Windows machine is the best you can do under Ubuntu. It merely requires a relatively new system because Windows will run on top of Linux, requiring some resources.

Personally I'm satisfied with my VirtualBox Windows install. Windows starts in a mere seven seconds. I leave the dictionaries that I use regularly (I'm an interpreter) open. When I open Windows, everything is ready to use.

---

### Post by wohlgejm on 2008-04-16
Originally Posted by firebrother15
All I had to do to get it working was uncheck the "allow windows manager to control windows" box on the graphics tab of winecfg.

Hey everyone, I'm brand new to linux, just got my Thinkpad R61 in the mail a week ago and figured I give dual booting with Vista a try.  I have to say I'm impressed with Ubuntu, I haven't booted into Vista once.  Well now back to the topic at hand... I did exactly as firebrother15 did in the WINE configuration and installed Rosetta Stone Version 3 with Russian levels 1,2,3 and the program runs quite smoothly!

---

### Post by ToneDispenser on 2008-04-26
I also had a problem with "Rosetta Stone". It wouldn't find my language disc. You can find the solution to this at [Wine's Appdb in this comment]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2497#Comment-21518"). I converted my language CD with the script in the comment and mounted the resulting image.

Works fine now :)

---

### Post by mrojas73 on 2008-04-26
I have used rossetta stone in the past on wine with 0 issues.

---

### Post by mhedges48 on 2008-04-29
Hello,
I just purchased Japanese levels 1-3, Rosetta Stone ver. 3. I am using  Gutsy Gibbon and cannot get it to run.
I try to install using WINE and receive this error: "the wizard was interrupted before Rosetta Stone V3 could be completely installed."
However, the program is at least partially installed, as I have the folder in .wine/Program Files. When I try and run the RosettaStoneVersion3.exe, I get this error: 
"Fatal Application Error: 2120".

I have tried the suggestions in this forum with no success.

Any help in getting this program running is greatly appreciated.

best
Matt

---

### Post by Chonnawonga on 2008-06-24
I'm having the same problem as mhedges48: "The wizard was interrupted..."

Here is any and all terminal output I'm getting:

```
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:advapi:LookupAccountNameW (null) L"brad" (nil) 0x7f22f7fc (nil) 0x7f22f800 0x7f22f7f4 - stub
fixme:advapi:LookupAccountNameW (null) L"brad" 0x7f021118 0x7f22f7fc 0x7f01fac8 0x7f22f800 0x7f22f7f4 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 1 ignored L"Upgrade" table values
err:ole:CoGetClassObject class {88d96a05-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d96a05-f192-11d4-a65f-0040963251e5} could be created for context 0x1
err:ole:CoGetClassObject class {88d969c0-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d969c0-f192-11d4-a65f-0040963251e5} could be created for context 0x1
fixme:msxml:DllCanUnloadNow 
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 2 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 4 ignored L"CreateFolder" table values
err:ole:CoGetClassObject class {88d96a05-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d96a05-f192-11d4-a65f-0040963251e5} could be created for context 0x1
err:ole:CoGetClassObject class {88d969c0-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d969c0-f192-11d4-a65f-0040963251e5} could be created for context 0x1
fixme:msxml:domdoc_createNode unhandled node type 2
fixme:msxml:DllCanUnloadNow 
err:msi:custom_get_thread_return Invalid Return Code -2302
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603
```

Any help would be very much appreciated!

---

### Post by Chonnawonga on 2008-06-24
Scratch that: I found the solution here: [http://ubuntuforums.org/showthread.php?t=736405]("http://ubuntuforums.org/showthread.php?t=736405")

Works well for me!

---

### Post by mac-duff on 2008-10-18
Hello,
do we have so far a resolution for the error:
Fatal Application Error: 2120

???
Get also this strange error

cu


Edit:
Updated to the last version, no error anymore :)

---

### Post by ollifl on 2009-11-29
Works pretty good in Karmic Koala eventhough I had some problems installing.

- Rosetta v.3.2
- installed Spanish SA version
       -had to install language pack 2 first, 3 and language pack 1 last. I don't know why but it worked.

---

### Post by Trinity1976 on 2009-12-01
I have been trying all day to install Rosetta Stone v 3 from CD-ROM. These are my experiences so far.

I installed Wine and when I right click on the 'setup.exe' and choose 'Open with Wine Windows Program Loader', it launches set-up, so far so good. I go through the wizard, click the install button and the program looks like it's installing, gets to the end of the Status bar then comes up with the following message:

"Rosetta Stone Version 3 setup wizard ended prematurely because of an error"

After a bit of research I followed the suggestion on this forum to install msxml4 using Winetricks. That seemed to make things worse, as now the setup wizard doesn't even get as far as it did. The Status bar doesn't even move and after a while the wizard just disappears.

I also tried Wine-doors and that gives the same problem. I asked tried playonlinux, which gets me a bit further down the installation process but only as far as the message "Rosetta Stone Version 3 setup wizard ended prematurely because of an error".

Bearing in mind that I have no idea what I'm doing I'm just following other people's suggestions without really knowing what they do, can anyone suggest anything else?

---

### Post by Trinity1976 on 2009-12-06
Trying to install from a terminal I get the following output. Any ideas?

> fixme:system:SetProcessDPIAware stub!
fixme:advapi:CheckTokenMembership ((nil) 0x132af0 0x35fd0c) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x132af0 0x35fd0c) stub!
err:msi:copy_package_to_temp failed to copy package L"RosettaStoneVersion3.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"RosettaStoneVersion3.msi"

Never mind. I tried a different version of Rosetta and it worked.

---

### Post by amirhomayoun on 2009-12-07
> **Trinity1976 said:**
> I have been trying all day to install Rosetta Stone v 3 from CD-ROM. These are my experiences so far.

I installed Wine and when I right click on the 'setup.exe' and choose 'Open with Wine Windows Program Loader', it launches set-up, so far so good. I go through the wizard, click the install button and the program looks like it's installing, gets to the end of the Status bar then comes up with the following message:

"Rosetta Stone Version 3 setup wizard ended prematurely because of an error"

After a bit of research I followed the suggestion on this forum to install msxml4 using Winetricks. That seemed to make things worse, as now the setup wizard doesn't even get as far as it did. The Status bar doesn't even move and after a while the wizard just disappears.

I also tried Wine-doors and that gives the same problem. I asked tried playonlinux, which gets me a bit further down the installation process but only as far as the message "Rosetta Stone Version 3 setup wizard ended prematurely because of an error".

Bearing in mind that I have no idea what I'm doing I'm just following other people's suggestions without really knowing what they do, can anyone suggest anything else?

I'm having the same problem with Rosetta Stone 3.4.5, Wine 1.0.1 and Ubuntu 9.10.

Based on what I found out the problem is coming from the fact that Rosetta Stone is trying to add itself to the Windows Firewall exception list. In Wine there is no such a thing as firewall. RS also tries to restart the (non-existent) firewall. I tried to change wine's config to different versions of Windows (95, 98, 2000, ...) but non worked.
In windows you can resolve the issue by turning on the firewall in Services.MSC.

Right now I can't think of anything but changing the version of the setup we are using.

PS) Take a look here:

```
http://old.nabble.com/Firewall-exception-list-td18749192.html
```

My problem solved too! The latest version of Wine did the job. Wine v1.1.31.

---

### Post by Trinity1976 on 2009-12-08
Hi,

I know this may be an odd question but:. When Wine installs Rosetta Stone I know it puts the files in the Program Files folder in the virtual C drive, but when you add a language pack, where do the files go? I can't seem to find a file structure that matches the one I had in Windows,

Trin

---

### Post by amirhomayoun on 2009-12-09
> **Trinity1976 said:**
> Hi,

I know this may be an odd question but:. When Wine installs Rosetta Stone I know it puts the files in the Program Files folder in the virtual C drive, but when you add a language pack, where do the files go? I can't seem to find a file structure that matches the one I had in Windows,

Trin

It asks you where you want to keep the files.You can give it any address. I think the default address is somewhere in home folder.

---

### Post by motuspork on 2010-06-01
Sorry to bring back an old thread, but I'm new to Ubuntu (installed v10.04), and I can't seem to get Rosetta working either.  Install works great with Wine, but I'm getting the error that there are no language packs found.  Was there a definitive fix for this?

---

### Post by TheFu on 2010-06-01
> **motuspork said:**
> Sorry to bring back an old thread, but I'm new to Ubuntu (installed v10.04), and I can't seem to get Rosetta working either.  Install works great with Wine, but I'm getting the error that there are no language packs found.  Was there a definitive fix for this?

[http://appdb.winehq.org/appview.php?appId=1867](http://appdb.winehq.org/appview.php?appId=1867) may be helpful. winehq.org is where I'd look.  The last time I looked at Rosetta, it was using very unusual copy protection methods that required direct and specific access of the DVD media by the OS. That may have changed. I don't know.

---

### Post by Punkristo on 2010-08-07
> **motuspork said:**
> Sorry to bring back an old thread, but I'm new to Ubuntu (installed v10.04), and I can't seem to get Rosetta working either.  Install works great with Wine, but I'm getting the error that there are no language packs found.  Was there a definitive fix for this?

Im getting the same error also. Any fix for this?

---

### Post by jeffery6803 on 2011-01-04
hello  i`ve gotten rosetta stone to completely work for me under wine this was on a brand new install of wine  then built the dependecies for wine ran  winecfg  installed rosetta install completed successfully but when i ran rosetta stone was getting a blank gray screen i solved the gray screen by setting wines windows version to windows 2000 tested everything works great no crashes  full mic support one other thing is that this version is  3.4 and was downloaded as a torrent  where i had to change the .exe to a cracked version should work but as this not  being the original exe can not assure it will

---

### Post by jeffery6803 on 2011-01-04
remember you have to add your cd drive to wine with winecfg  if you`ve already done that and are still getting the no cd drive then i  can`t help if  not run winecfg click add enter the path to your cd drive once youve done that click advanced towards the bottom and under type select cdrom drive  i use acetoneiso to mount the images it`s easier or you   can mount them manually your self if you use acetone iso the virtual drive will be located in your home folder  /home/yourname/virtual-devices/1 or if you have more than one drive mounted in acetoneiso 2,3,4,5 etc

---

### Post by jalirious on 2011-04-30
Hi, some of the comments were very helpful, but could be more complete. 

Here is a 'howto' for installing language packs.
This is for 'Spain1.iso' (or whatever) images, for me taken as a torrent.

Rosetta stone installed = yes.

>winecfg
click Drives, click add, select D (for example) set path as /media/cdrom0
click apply
click close
sudo mkdir /media/cdrom0
sudo mount /pathto/Spain1.iso /media/cdrom0 -t iso9660 -o loop
Run Rosetta stone under wine, install language pack
when finished
sudo umount -a

repeat as necessary.

---

### Post by Georgia boy on 2011-05-07
I have a question. Has anyone tried this one instead of Roseta Stone? 

[http://www.livemocha.com/](http://www.livemocha.com/)

Wonder if it's any good or not?

---

### Post by zidane13 on 2011-05-17
Nvm

---

### Post by Amish_Gramish on 2011-05-25
> **Georgia boy said:**
> I have a question. Has anyone tried this one instead of Roseta Stone? 

[http://www.livemocha.com/](http://www.livemocha.com/)

Wonder if it's any good or not?

Live Mocha is decent, and great for the price of free, but whenever you upload your audio to the system, their compression methods always make you sound horrible, and there are often glitches and mistakes that end up making it so you don't learn as well.

I'd say use it in combination with Rosetta Stone, but it's too annoying to use it by itself.

---

### Post by DonJuan4076 on 2011-08-09
Ok so I just read through this thread and it seems like no one has solved the language pack problem, is this correct?


My problem is similar to others I used Wine to launch Rosetta Stone but Rosetta Stone will not recognize my language CD when running Ubuntu 11.04, everything works great on Windows. I have tried everything from ripping the CD and making an .iso to copying the files into the Rosetta Stone folder, no luck.

So my question is... 

Did anyone ever solve Rosetta Stone the language pack problem on Ubuntu?

---

### Post by omelette on 2011-08-09
Funny this thread should pop up.  I have been using RS for a while now, but with VirtualBox.  I had a go installing it with Wine but failed miserably way back.  One or two pages into the thread and armed with new-found knowledge I thought I'd give it another bash.  All the 'solutions' offered didn't work for me though.  Although it installed perfectly the first time, this time it kept terminating prematurely.  I had no alternative but to consign the entire '.wine' folder to the trash and start from scratch - which I've done literally dozens of times since first using Wine, it's biggest problem imo.  It was also the first time I had played seriously with Wine's Drives tab so I guess I have learned a little and got further than I managed before.  Actually I thought I had it cracked, it finds the language packs and displays them, but when I then click on an individual lesson, bang, up comes an error saying it cannot find the lesson in question.  Weird!  This is only with a mounted ISO file - which works perfectly with RS/VirtualBox - it does not detect the physical language CD-ROM in the drive at all (which also works fine with RS/VB) which is even stranger.

Hard to believe RS earned a Gold Wine-compatibility award given the number problems highlighted in this thread alone...

---

### Post by omelette on 2011-08-10
Well, I found a solution but it's not at all pretty.  First off, there's a bug in the auto-mount application (double-clicking the ISO image) on my setup which just adds to the overall confusion - I'm running this on Fedora 14 - it mounts the ISO seemingly OK, displaying all folders found on the root directory of the language disk - except when you check their contents, they're all empty!  This ISO was created from the original RS language disk, and I tried both Nero -> nrg2iso and Brasero, so it's unlikely the problem lies with the ISO.  If Ubuntu's auto-mount isn't broken like this then you're sitting pretty.  It is presumed that you have already installed RS and the Apple plugin successfully.

Note that the order you do the following is critical.

1.  Mount your language disk ISO by double-clicking it, or right-click and select 'mount'.  Note that this first step is seemingly mandatory - although using the 'mount' command itself from the terminal works perfectly, mounting all language folders and their contents, RS still does not detect them, it will only detect the 'broken' mount on my setup.
2. This displays the mounted disk on the desktop but also creates a folder in a hidden directory in the users root directory named '.gvfs' - unhide this by checking "Show hidden filed" in the Nautilus 'View' tab and create a link to it. Inside this folder is another folder containing all of the mounted language folders.  This is the folder we are interested in.
3.  Open Wine Configuration and from the Drives tab, create or edit an existing drive and browse to the languages folder mentioned in point 2. Expand the 'Show Advanced' options here and change 'Type' to "CD-ROM".
4.  Fire up RS.  On my system it unfailingly detects the language folders, but clicking on any individual lesson results in an error telling you the lesson could not be found - not surprising since if you check the folders manually you will find that they are all empty!
5.  Here's where things turn ugly.  With RS still running (critical) you must now either close and re-mount the ISO with 'mount' - see an earlier post in this thread on how to do that - or open it with another application.  I have tried each and they both work.  I used AcetoneISO2 as it was already installed. Now from Wine Configuration's Drives tab, Browse to this mounted language disk folder.  If you use AcetoneISO2 it is in a folder called 'virtual-drives' in the users root-directory, usually a folder named '1' if AcetoneISO2 has not mounted any other images.  Ensure the 'Type' of Drive is still "CD_ROM".  Now simply hit the Wine Configuration 'Apply' tab.  Presto, RS now has access to the language files and works perfectly.

Until you close RS that is, restart and you have to repeat this nonsense as RS fails to find the correctly-mounted ISO!  But as I said already, if Ubuntu correctly mounts the ISO to begin with, you should be fine.  Not for me alas...

Another complication I experience is that I like to have an online dictionary open as I go through each lesson, but thanks to the shitty way RS is programmed, it can't be minimised when run.  It even follows you around if you switch to another virtual desktop!  One solution is to click the 'Emulate a virtual Desktop' option found on the Graphics tab of Wine Configuration.  You can now minimise it and should be a good solution if your auto-mount works properly, but due to the messing I have to do above, it not really viable...

Hence, I will be sticking with VirtualBox.

---

