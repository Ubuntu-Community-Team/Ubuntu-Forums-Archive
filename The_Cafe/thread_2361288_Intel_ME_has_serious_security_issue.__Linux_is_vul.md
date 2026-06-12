---
title: "Intel ME has serious security issue.  Linux is vulnerable.  Update BIOS/Firmware"
date: 2017-05-14
forum: The Cafe
---

### Post by MechaMechanism on 2017-05-14
[https://security-center.intel.com/advisory.aspx?intelid=INTEL-SA-00075&languageid=en-fr](https://security-center.intel.com/advisory.aspx?intelid=INTEL-SA-00075&languageid=en-fr)

[http://www.kb.cert.org/vuls/id/491375](http://www.kb.cert.org/vuls/id/491375)

Any OS is affected.  This is why it's a good idea to have a copy of Windows around to flash the BIOS as some PC's/laptops are hard to flash without Windows if not impossible.  I'm very concerned about my System76 Wild Dog Pro.

I'll file a report with System76 and see what they say about their motherboards.

I've already updated the BIOS/Firmware in my Dell XPS 15 9560 using Windows 10, which by the way is an excellent OS.  For now I'm just using Kubuntu on a thumb drive which is lucky as I would have had no way to update the BIOS that I know of, although someone around here might know.  The Dell XPS update is version 1.3.3.

---

### Post by ian-weisser on 2017-05-14
Since intel has provided full documentation instructing users how to identify if their hardware is vulnerable, why bother asking S76 to do it for you?

---

### Post by MechaMechanism on 2017-05-14
> **ian-weisser said:**
> Since Intel has provided full documentation instructing users how to identify if their hardware is vulnerable, why bother asking S76 to do it for you?

Could you post a howto.  The Intel link is not very clear.  I thought about lshw, but since me is not used in Linux is my understanding the lshw tool does not report versioning info.  Otherwise I have no way of knowing what me version I'm using, so I thought I'd ask System76 as they would be the ultimate authority and would be the ones to provide an BIOS file compatible with Ubuntu.

---

### Post by mastablasta on 2017-05-15
> **MechaMechanism said:**
> 
Any OS is affected.  This is why it's a good idea to have a copy of Windows around to flash the BIOS as some PC's/laptops are hard to flash without Windows if not impossible.  I'm very concerned about my System76 Wild Dog Pro.

occasionally you can get away with using FreeDOS.

---

### Post by lammert-nijhof on 2017-05-17
I did use freedos in one occasion for my 9 years old Dell Inspiron 1521. My HP dc8580, same age, had an update function in the bios itself.

---

