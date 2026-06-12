---
title: "Is my WINE configured to root?"
date: 2013-07-16
forum: Security
---

### Post by Tom_ZeCat on 2013-07-16
I'm using WINE 1.6-rc4, which I downloaded and installed.  The one in the repository (1.4something) was not running Treepad Business well and so I wanted to try a later WINE to see if it would run better, which it did.  

On the security page ([http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)) it recommends that you don't run WINE under root.  I just ran the install package in the terminal and didn't change it.  I think WINE might be set to run in root.  When I go to Wine ==> Configure Wine ==> Drives, I see this: 
> C: ../drive_c
H: /media/WRITING
I: /media/WRITING
K: /media/H
Z: /

Does that drive Z mean I'm indeed configured to root?  I don't run much in WINE.  Treepad Business is the only thing I run regularly so far.  I also installed WordStar for Windows 2.0, a Windows 3.1 program.  To my amazement, this almost 20 year-old program ran flawlessly. I've also installed Ultralingua 5.03, a German/English dictionary.  It runs okay, but later versions 6.0 and 7.1 don't :(.

Even though I don't run much in WINE, I want it to be secure.  Though I'll always check for a Linux-based solultion first I may very well install other Windows programs.

---

### Post by monkeybrain2012 on 2013-07-16
I think there are rare occasions where one may need wine to run software installed in /usr/bin or /usr/local/bin etc even though these are not installed with Wine (lnms-vst?), so you need WIne to be able to access those places, but this is not the same as running it as root, it is like, you install vlc in /usr/bin but you don't run it as root, even though you need sudo to change things in /usr/bin.  I don't use such software so I just change the z drive to map to /home/username

---

### Post by lah7 on 2013-07-31
Don't worry about the Z: Drive in Wine being assigned to "/" -- It's there so you can access the file system much like Linux does.

Wine runs at user level, so if you was to purposely run a malicious windows program, it couldn't delete Linux's system folders on the Z: drive **but** it could potentially erase the folders you can write to, such as your home folder [COLOR=#0000cd]/home/username/[/COLOR] -- that is if you was to be using Wine for testing dangerous programs...

I believe the Z: Drive is there so Wine can communicate between the Windows and Linux world, such as trying to execute[COLOR=#0000cd] "wine /home/username/someapp.exe"[/COLOR] would translate to "[COLOR=#0000cd]Z:\home\username\someapp.exe" [/COLOR]-- I think it's safe to remove if you wish, but if there's errors, Z: not pointing to "/" could be the problem.
The C: Drive can only access the sub-folders of [COLOR=#0000cd]/home/username/.wine/drive_c/[/COLOR] and that is all. Once you have your app installed, you should be alright with removing the Z: if you wanted to.

Unless you specifically ran Wine as the superuser via **sudo** or **root**, then that's when you risk your entire file system and that's strongly not recommended.

---

