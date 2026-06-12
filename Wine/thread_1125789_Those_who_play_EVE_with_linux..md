---
title: "Those who play EVE with linux."
date: 2009-04-14
forum: Wine
---

### Post by Zummy on 2009-04-14
Do you crash randomly? I am able to boot into the game (using WINE) and everything works fine, graphcis are amazing, no text problems, nothing.  However my EVE have a tendency to crash every now and then.  Does or did that effect you at all? Howd you fix it?

---

### Post by Mokoma on 2009-04-14
ummmm, what graphics card are you using? did you install directx or are you using the native wine versions? did you set any direct3d registery keys?

---

### Post by Zummy on 2009-04-14
I'm using a nVidia 8800 GT Ultra.  For the Direct X, I didn't go out of my way after installing Wine, so I probably haven't put in any registry keys or updated my Direct X (To my knowledge) How would I check?

---

### Post by Mokoma on 2009-04-14
most people will tell you not to install the official directx, but ive got to say it has never had any bad effects for me, it has only helped. as for registery keys look at this site.

[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

---

### Post by Zummy on 2009-04-14
No i havent set any Registry Keys, do you recommend me to?  Also I will download the official Direct X and see where that leads me.

---

### Post by wolfyking2 on 2009-04-14
if your going to install directx, install it through winetricks, under dx9 (I think the name is right, not sure) and there you go!  If you don't know what winetricks is, just google it ;)

---

### Post by jprophet420 on 2009-04-25
at first i tried a program recommended on the eve website called 'play on linux'. you can install dx on it, it didn't work. the splash screen loaded and that was it. so i tried it with wine 1.01 and winetricks to install dx, and the same thing happened, made it to the splash screen and thats it. 

Does anyone else have the game running currently in 9.04? to the OP, did you install dx before or after the crashes? what version of wine? thanks.

---

### Post by AthlonMDK on 2009-04-26
Hi

Got the same issue, tried playing in windowed mode, helped for me. Seems to be a gpu driver issue.

---

### Post by jprophet420 on 2009-04-26
how do you set it to run in windowed mode if you cant launch it? in wine or do i have to launch it with command line? thanks.

NM, it does not fix the problem. ran it in windowed mode and same thing.

---

### Post by Namtabmai on 2009-04-26
It's been months since I've played Eve but I found the only way I could get it to run was in a wine virtual desktop.
In winecfg you can set applications to run as a virtual desktop and also set the size, I just set the size to the same as my physical display size.

---

### Post by jprophet420 on 2009-04-27
yeah, thats what i did, i should have been more specific. It just hangs at the splash screen when run on virtual desktop set to the same size as the desktop (and several other sizes for that matter). Is there any way i could get it to launch in safe mode perhaps?

i found this interesting...
[http://bugs.winehq.org/show_bug.cgi?id=16173](http://bugs.winehq.org/show_bug.cgi?id=16173)
but held no solution for me, however i posed it in the hopes it would help someone.

I have tried wine 1.01, 1.18 1.19 and 1.20

---

### Post by jprophet420 on 2009-04-28
> 1.) Get wine-1.1.17 source and the appropriate patch from this thread:
[http://bugs.winehq.org/show_bug.cgi?id=17437](http://bugs.winehq.org/show_bug.cgi?id=17437)

2.) Extract wine:
tar xvfj wine-1.1.17.bz2

3.) Copy patch to wine-1.1.17 directory and patch there:
patch -p1 < apocrypha.shaders.1.1.17.patch

4.) Compile and install wine (compile as user and install as root)
./configure
make depend
make
make install
[http://www.eveonline.com/ingameboard.asp?a=topic&threadID=1017452](http://www.eveonline.com/ingameboard.asp?a=topic&threadID=1017452)

---

