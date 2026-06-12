---
title: "Howto: Mustek 1248 UB USB Scanner Install / Setup"
date: 2007-02-03
forum: Tutorials
---

### Post by danpre on 2007-02-03
This HOWTO was created the same way as great howto for [MUSTEK 1200 UB Plus]("http://ubuntuforums.org/showthread.php?t=154429&highlight=mustek") by [williamts99]("http://ubuntuforums.org/member.php?u=69004")

An easy, cut and paste way to get The Mustek 1248 UB USB Scanner working in Ubuntu Breezy and Dapper.

Open the Terminal(Applications>Accessories>Terminal), copy and paste the following one at a time.

To get to the proper directory:

```
cd /usr/share/sane/gt68xx
```

To download the driver firmware file sbfw.usb from the [SANE gt68xx-backend site:]("http://www.meier-geinitz.de/sane/gt68xx-backend/")

```
sudo wget http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/SBSfw.usb
```

That's all there is to it, enjoy!!

If you are a KDE user I would suggest to install Kooka - as an "easy to use open source GNU/Linux scan program"

---

### Post by endesign on 2008-11-20
Thanks Danpre!

This worked for me on Ubuntu 8.10 also.

---

### Post by trukker on 2009-03-10
Crap color output..... is there some way to fix this?

---

### Post by devonmiles on 2009-04-23
Hi all,

I just got the same scanner, and it acts in a strange way using Sane. I scanned the paper 5 times (w the same settings) and got the result that can be seen on the picture. Of course, the paper was not moved. As you probably can see, the upper part of the image is stretched, however, never the same way. I tried the scanner on a Vindoz machine and it seemed to work properly there.
And yes, I followed this howto, and I'm running an 8.04 system.

Any suggestions?


Hah, got it!
When I removed the additional ca. 1 meter long USB cable section from between the scanners own cable and the computer, it just worked perfectly. Surprising, hm?
Conclusion is that you must be satisfied with the length of scanners own cable.

---

### Post by norman@littletank.org on 2009-05-16
The scanner is set up and working and I am using the USB lead that came with the scanner. The lead is plugged directly into the computer running Ubuntu 8.10. The colour of scanned images is very poor and I see that I am not on my own. Has anyone any ideas on how to get the colour correct, please?

---

### Post by motorcity909 on 2009-09-16
Thank you, thank you, thank you!  I've only been Ubuntu'd for about 2 months but scanning was something I had to revert to XP to do but this fix has got my cheapo flatbed scanner working in Ubuntu 9.04 and I couldn't be happier with it!

Thanks!

:P

---

### Post by dhirendra1 on 2010-05-14
Just tried it on Lucid.  Worked like a charm.  Thanx.

---

### Post by dreama on 2011-05-27
Thanks,

This works on Natty (11.04), too.

---

### Post by silviucc on 2012-04-29
This also works on Ubuntu 12.04 64bit.

You will certainly notice that **/usr/share/sane/gt68xx/** is not there. Panic!! :P No problem, just create it:
> 
sudo mkdir /usr/share/sane
sudo mkdir /usr/share/sane/gt68xx/


Then just copy the firmware file in that newly created dir. Your scanner should work.

---

### Post by forsubhi on 2012-06-07
thank you [danpre]("http://ubuntuforums.org/member.php?u=2272")

it is worked on kubuntu 12.04

---

