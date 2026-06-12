---
title: "Simple Scan - Not Working"
date: 2012-11-20
forum: Ubuntu Development Version
---

### Post by VinDSL on 2012-11-20
Guess this says it all...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-20-nov-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-20-nov-2012-1.png")[/INDENT]


Simple Scan worked last week in Ubu 13.04, but evidently recent updates killed it.

Works fine in Ubu 10.10 -- same machine, same hardware.

Anybody else having issues with Simple Scan in RR?!?!?

---

### Post by lonniehenry on 2012-11-20
Just checked mine and it worked fine.  HP Photosmart d110 connected wirelessly.

---

### Post by ronacc on 2012-11-20
did you try xsane ?

---

### Post by VinDSL on 2012-11-20
> **ronacc said:**
> did you try xsane ?
Just installed/tried xsane.  No dice.

[QUOTE=xsane]

scanning for devices

no devices available[/QUOTE]

Must be a USB issue.  OS sees it, but apps don't recognize it...

---

### Post by ronacc on 2012-11-20
or perhaps a driver issue , I'll see if rr finds my brother mfc 7860 .

---

### Post by lindsay7 on 2012-11-20
sometimes an update will revert you HPLIP version back to one that does not work with your printer.  See this for more info,


[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

---

### Post by VinDSL on 2012-11-20
> **lindsay7 said:**
> sometimes an update will revert you HPLIP version back to one that does not work with your printer.  See this for more info,


[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)
I'm using a stand-alone, flatbed, HP scanner.  Does it use printer drivers :confused:

**EDIT**

Just answered my own question.  LoL!  :D
[QUOTE=From your link]HP Linux Imaging and Printing
Print, **[COLOR="Red"]Scan[/COLOR]** and Fax Drivers for Linux[/QUOTE]

I'll check that out.  Thanks!


For giggles, I installed Liquorix 3.6.0-7
```
vindsl@Zuul:~$ uname -sr
Linux 3.6.0-7.dmz.1-liquorix-686

```
Same thing, so it isn't a Linux 3.7-rc6 issue...

---

### Post by VinDSL on 2012-11-20
Commit log shows (my current) HPLIP package was last updated on "Sun Oct 14 16:20:39 2012", so...

I *think* it's okay.  ;)

---

### Post by ventrical on 2012-11-20
Worked ok with my HP-C4180.

---

### Post by ventrical on 2012-11-20
It's really slow at 1200dpi .. but I think that is the scanner itself.

---

### Post by ronacc on 2012-11-20
I installed the cups and scan drivers for my brother MFC7860dw  and it scans ok with both xsane and simple scan . just for grins try running simple-scan with sudo , unless I add a couple of lines to lib/udev/rules.d/40-libsane.rules  I have to scan as root .

---

### Post by ventrical on 2012-11-21
Ok.. my Canon MP520 works a lot faster but Image Viewer will not load hi -res jpgs (nor do I think that simple-scan is saving them correctly.)

Linux dale-desktop 3.7.0-030700rc4-generic #201211041435 SMP Sun Nov 4 19:43:27 UTC 2012 i686 i686 i686 GNU/Linux

---

### Post by ventrical on 2012-11-21
I tried Shotwell and that brought up the hi-res image but when I went to  magnify it it crashed into oblivion. The dark fader screen came first ( I call it the ghost of metacity). Then, when I went to open ff from minimized on Unity Panel it brought up a mirror image of the desktop!!

 Sorry .. did not get a screen shot. Just plain weird! :)

---

### Post by ventrical on 2012-11-21
Tried to load it with Gimp .. crashed into oblivion. Time for reboot !

---

### Post by VinDSL on 2012-11-21
> **ronacc said:**
> [...] just for grins try running simple-scan with sudo [...]
Tried that yesterday.  Same thing.  No soap...

Looking around at the various packages -- the ones responsible for scanning et al. -- all of them are from Quantal.

Hopefully, when the Raring versions hit the repos, this situation will pan out.

In the meantime, Ubu 10.10 is always on tap, and everything works as expected in it...  ;)

---

