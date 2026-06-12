---
title: "WoW install error"
date: 2009-11-17
forum: Wine
---

### Post by charlton2142 on 2009-11-17
Hello I have been pulling my hair out trying to install WoW under wine. I have tried to download it via the installer but the accept  EULA button will not activate when I reach the bottom. I think this is due to an error that I get while installing the InstallWoW.exe. When I get part way through downloading said installer a box pops up which just says "install" in the title box with a big red "X" there is no error message so i'm not sure what's  up with that. I also went out and bought the WoW dvd and I copied all the files over after making them all unhidden and that jazz but when I try to run that installer I get an error message stating that the Installer was unable to start up. and that the installer data could not be found. if the problem persists, please contact Blizzard support. 

it should probably be noted that I think im running the latest verion of wine (but im not sure how to confim this and Im using 9.04 Jaunty. 

thanks

---

### Post by Alatar1 on 2009-11-17
I'm not the most experienced with ubuntu myself, but i sure know WoW...
I don't think there is a need to copy the files off the DVD, the downloader should work just fine.

And to check your wine version... Applications > Wine > configure Wine then click on the "About" tab, should say what version it is in there. 

If the EULA "accept" button does not work it is likely its your version of wine, the same thing happened to me before, I just updated wine fully and it worked. and the big red X happened to me just recently on my last wow installation, it just happened, i closed it and the installation still went fine.

---

### Post by beastrace91 on 2009-11-17
I recall that EULA issue popping up in an old version of Wine confirm you are running the latest version by running ```
wine --version
``` in your terminal of choice.

If you are not running the latest (1.1.33 as of my posting this) upgrade to the latest by following the instructions [here](http://www.winehq.org/download/deb).

Regards,
~Jeff

---

### Post by Alatar1 on 2009-11-17
Beastrace, you rock dude. thanks for helping so much! I appreciate you finding those instructions... I'm beggining to think there should be a sticky or something in this forum covering wow, this is the 4th thread on WoW issues i've seen today...

---

### Post by beastrace91 on 2009-11-17
> **Alatar1 said:**
> there should be a sticky or something

There are two stickies [here](http://ubuntuforums.org/showthread.php?t=885111) and [here](http://ubuntuforums.org/showthread.php?t=871535). That pretty much cover everything I've suggested in all of said WoW threads that have popped up today... ;) Its a shame people don't read them... Ahh well builds my post count at any rate :P

Cheers,
~Jeff

---

### Post by protiss on 2010-03-25
worked great for me.  Quick description of what I had to do.

update wine per the previous explanation,

sudo mount -o remount,unhide /dev/sr0 (this is linked to media/cdrom already)

This is the weird step - for some reason I was still grayed out when running directly from /media/cdrom...

went to /home/user/.wine/dosdevices/d:   ---also a link to /dev/sr0.  might not be "d:" for you, make sure to check it.

Invoked SU (yeah, weird right?)

wine Installer.exe

This was done on a fresh 9.10 install, haven't played with any permissions or links or anything yet.

---

