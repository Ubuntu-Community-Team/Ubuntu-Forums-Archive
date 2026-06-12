---
title: "Starcraft 2 graphics issues"
date: 2010-08-14
forum: Wine
---

### Post by wolfmanjack on 2010-08-14
Hi everyone.

I'm trying to run SC2 through wine 1.2, which basically works. I simply copied the install over from the windows partition and tried running it after modifying the winecfg and running winetricks as described in the Wine APPDB entry. However it seems like there are some issues with the 3d-driver, that I'm not quite able to figure out right now (see screenshots)
[[IMG]http://img823.imageshack.us/img823/3705/sc22m.th.png[/IMG]](http://img823.imageshack.us/i/sc22m.png/)[[IMG]http://img217.imageshack.us/img217/6286/sc2b.th.png[/IMG]](http://img217.imageshack.us/i/sc2b.png/)

Judging from the menues I guess everything animated (unlike static graphics) is not displayed or displayed incorrectly.

Right now I'm running 10.04 with the open source xserver-xorg-video-ati and xserver-xorg-video-radeon driver packages for my ATI Radeon 1900 series graphics card. Installing the fglrx driver from the repositories simply resulted in no more 3d acceleration (without checking for any further modification to the xorg.conf) and the proprietary driver provided by AMD's installer script says it won't run on 10.04 (Catalyst 9.3).

Does this basically mean I'm screwed, since AMD/ATI stopped giving driver support for my graphics card (current Catalyst is something like 9.8 iirc), or is there some other way I just haven't thought about yet?

Any help appreciated :)

---

### Post by cogadh on 2010-08-14
If ATI dropped support in the current driver, then your best bet is to probably get the old ATI driver from before they dropped support, if that is still offered for download.

---

### Post by wolfmanjack on 2010-08-15
Did some read-up. The old(er) Catalyst version only supports X-Server versions <1.6, so they won't install and even if they did, they wouldn't work. 

Apparently, there's really nothing I can do (apart from getting a newer graphics card):
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

Too bad ;)

---

### Post by beastrace91 on 2010-08-16
> **wolfmanjack said:**
> Did some read-up. The old(er) Catalyst version only supports X-Server versions <1.6, so they won't install and even if they did, they wouldn't work. 

Apparently, there's really nothing I can do (apart from getting a newer graphics card):
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

Too bad ;)

Yep. And next time do yourself a favor and buy nVidia. Only way to go for gaming under Linux.

~Jeff

---

