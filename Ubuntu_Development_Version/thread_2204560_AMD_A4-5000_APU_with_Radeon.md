---
title: "AMD A4-5000 APU with Radeon"
date: 2014-02-09
forum: Ubuntu Development Version
---

### Post by open2reason on 2014-02-09
I have just tried the latest 14.04 daily and am happy to report that it looks good using my graphics processor of AMD A4-5000 APU with Radeon.


[ATTACH=CONFIG]250206[/ATTACH]
[ATTACH=CONFIG]250203[/ATTACH]
[ATTACH=CONFIG]250204[/ATTACH]
[ATTACH=CONFIG]250205[/ATTACH] 

Kudos to all developers, am looking forward to the next LTS.

---

### Post by ping-wu on 2014-02-09
Thanks for the report.  I am thinking about getting a new AMD (A10) machine (laptop).

---

### Post by su:bhatta on 2014-02-10
> **open2reason said:**
> I have just tried the latest 14.04 daily and am happy to report that it looks good using my graphics processor of AMD A4-5000 APU with Radeon.
.

Didn't you have to use 'nomodeset' ? I have had to use 'nomodeset' with my A4 from 12.04 installs.

Currently running Kubuntu 14.04 Alpha, with kernel 3.13.0-7, where I did not have to use 'nomodeset' for the first time ! :)

---

### Post by open2reason on 2014-02-10
I started from the latest 12.4.04 lts and found that 'nomodeset" was not required. I booted into an agile and what seemed to me a fully functioning desktop. 
The first image in my post shows the desktop on which you can spy a 14.04lts install icon but the Detail screen displays a 13.10 title,  which, I expect will be changed by the time 14.04lts goes live:D

---

### Post by su:bhatta on 2014-02-10
Oh, Ok.
I never did a fresh install of 12.04.4. So maybe thats the reason.

---

### Post by open2reason on 2014-02-11
bhatta, 
In my case a clean 12.04.04 install on an Acer Aspire XC-105 followed by booting via usb with the latest 14.04 daily and then selecting the normal NON UEFI boot option on offer.

The first display was the blue / white Unetbootin screen which then changed resolution to a smaller text.
This was replaced by the purple Ubuntu boot screen complete with winking read and white progress dots.
The screen then turned black / blank and stayed like this for what seemed quite a while but then the cursor appeared to be swiftly followed by a functioning 14.04 desktop.

Hope this helps.

---

### Post by su:bhatta on 2014-02-11
open2reason,
Thanks for the details. I have also installed a daily build of Kubuntu 14.04, and had no problems in getting a live screen, and did not have to use nomodeset.
I had heard the Linux Kernel from 3.12.x was more friendly towards the AMD hardware. 

That has been my experience too, as the Kubuntu booted to 3.13.0-7 kernel I did not have to use 'nomodeset' to get a live session . Previously, when I had booted up Ubuntu12.04, 13.04 &.13.10 I have had to use 'nomodeset' in every install.
So, yes, I am quite liking my experience with the newer kernels. :)

Also, this trick to enable radeon dynamic power management from webupd8 actually does wonders to my 13.10 Ubuntu Studio install :[http://www.webupd8.org/2014/01/how-to-enable-amd-radeon-dynamic-power.html](http://www.webupd8.org/2014/01/how-to-enable-amd-radeon-dynamic-power.html)

---

