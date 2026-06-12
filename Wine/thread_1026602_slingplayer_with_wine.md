---
title: "slingplayer with wine?"
date: 2008-12-31
forum: Wine
---

### Post by djrakun on 2008-12-31
Hi all,

I followed the steps in this howto to install slingplayer v2.0 on Intrepid Ibex

[http://cyberpunkcafe.com/page.php?74](http://cyberpunkcafe.com/page.php?74)

I complete every step in the howto without error, but the slingplayer installshield dies partially through it with a .NET framework 2.0 error after it starts installing files.  ( uncaught exception)

When running the installsheild again I do not get the same .NET framework error again ( d'oh! I never write down an error the first time I see it.  terrible habit).  

Second run through the error that i see is on step - copying firmware files, and the error is 1603 Fatal error during installation - consult windows installer help ( msi.chm) or msdn for more information.

MSDN says the common causes for this are

You may receive this error message if any one of the following conditions is true:

    * The folder that you are trying to install the Windows Installer package to is encrypted.
    * The drive that contains the folder that you are trying to install the Windows Installer package to is accessed as a substitute drive.
    * The SYSTEM account does not have Full Control permissions on the folder that you are trying to install the Windows Installer package to. You notice the error message because the Windows Installer service uses the SYSTEM account to install software.


So I wonder if the install directory is locked to the installshield.  I am not using sudo on the exe ( doesn't work anyway because the .wine directory is owned by wine).  Could this be a side effect of the encrypted home drive feature in Intrepid:confused:

---

### Post by djrakun on 2008-12-31
changing the path to the root of my home directory (z:/slingplayer) produced the same result.  Don't know if that proves anything, but at least eliminates a suggestion

---

### Post by djrakun on 2008-12-31
ok, i figured it out.  I think the new slingplayer requires two more dlls to be added.  both can be downloaded from 

[http://www.dll-files.com](http://www.dll-files.com)

first you need the winhttp.dll file.  I had to register this one just like the instructions say for the other dlls  ( like quartz.dll).  I also added it to the wine config libraries tab as "native" only ( dont know if this is required)

the second dll that i had to drop in the system32 directory was gdiplus.dll  This one would not register but it doesnt seem that it was necessary.  I also did not add it to the libraries tab in wine config ( i only pasted it in)

once i did that i started SlingPlayer.exe from the command line and voila! i got the annoying advertisement and i'm setting up the slingbox now.  yay!:KS

---

### Post by djrakun on 2008-12-31
ugh, not out of the woods yet.  Slingplayer starts up nicely, however I am trying to watch a slingbox away from my LAN, so I have to log in.  The Sling Accounts login box is completely white and never shows the login/password dialogue.  I think this might be a graphics configuration problem right now because it appears that the popup window itself is the problem.  I doubt i'm missing a dll for the 'sling login box'.

---

### Post by halucinations on 2009-01-03
I have slingplayer 2.0 running in virtualbox.  I have TinyXP rev9 installed as the OS.  Now i have 1.5GB of RAM to use so I set the base memory anywhere from 450MB to 512MB, I am still playing with the settings to see if there is a difference when running slingplayer.  For video I had it set at 100MB of 128MB Avail but I am slowly decreasing it to see where that minimum is.

Hope this helps...

---

### Post by RMOP on 2009-02-05
Did you ever get Slingplayer running?

---

### Post by djrakun on 2009-02-05
the virtualbox suggestion will work, because really you are just running it on xp. I never did get the GUI properly displaying in the initial dialogue boxes using wine.

---

### Post by RMOP on 2009-02-06
Well, I took the plunge and (on the second try) got SlingPlayer working nicely under Wine. And on an eeePC, no less. I must say, I was surprised.

---

### Post by djrakun on 2009-02-06
i am also.  if you have time, can you put together a 'how-to'?  do you recall any special configuration steps?  what ver of wine?  what ver of ubuntu?

---

### Post by 3L33T on 2009-04-14
> **djrakun said:**
> i am also.  if you have time, can you put together a 'how-to'?  do you recall any special configuration steps?  what ver of wine?  what ver of ubuntu?


I followed install steps found both on winehq and cyberpunkcafe but just could not get slingplayer to install successfully.  I either get the DLL error at the end of install (see bug 13371 in winehq) and "unable to load localized resource, please reinstall product" error.  This is using both the slingplayer-1.5UK.exe and slingplayer-1.5.0.325-US.exe install files.  I finally tried Andy's script [HERE]("http://www.slingcommunity.com/group/discussion/26840/Slingplayer-Linux-Install-Script-1.0xb/?page=8") and it just worked like a charm!!!

My setup:

Slingplayer 1.5.1.335
Wine 1.1.19
Ubuntu 8.10 Intrepid Ibex

---

