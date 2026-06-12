---
title: "Install fails on ProLiant ML330 G3 SCSI"
date: 2009-12-16
forum: Server Platforms
---

### Post by EMCAS on 2009-12-16
Hello,

I recently was able to get a ProLiant ML330 G3 from work, looking to install Ubuntu Server on it and use it as a home and experiments server. 
Unfortuneatly I'm unable to install Ubuntu Server on it. I can boot the cd, select language etc., but when I press the install button it loads some stuff and it reacts to nothing except for the power button. A few moments after that my health LED (weird HP server thingy) turns red. I've tried to install 9.04 and 9.10 server edition, both producing the same error. I've exited GUI and tried installing it with various boot parameters but it just won't work. I think it has something to do with the SCSI adapter that's in my server, but I don't know for sure.
Has anyone had any experience with installing Ubuntu Server on a ML330 G3?
If anyone could help me out, it would be greatly appreciated.

Thanks!

---

### Post by chipper_farley on 2009-12-16
I Googled that machine and it looks like it's an older machine, with maybe a P3 in it.  If that's the case, it's possible that some of the hardware may no longer be supported.  I don't know if that's the case for sure but I experienced something similar with an older Dell server that I just couldn't get anything to install on.  It turned out after tons of researching that in my case the controller in the server had had a big update to the driver since the time I had gotten the machine and the old driver (which I needed) was no longer in the linux kernel, just the new one was.  You might have something similar going on.  I was able to go back and get some older distributions and finally found that Fedora Core 1 (yes 1!) worked.  If it were me, I'd try the current version of Debian and, if it doesn't work, go back a few versions and see what happens.  I believe Debian leaves old versions out there for download.  If you find one that does work, you can probably figure out which release of Ubuntu used that version and (if you can still download it) try that version.

Not sure if this helps but good luck!

---

### Post by bloem on 2010-02-12
Just had the same problem today when I foolishly upgraded the BIOS firmware. It was at 4.06 06/23/2004 and according to the HP support website a later one had a critical bug fix. I installed the latest one (4.09) and from then on grub would start, but no menu, just an endlessly blinking cursor.

Before the upgrade I installed Ubuntu Server 9.10 and have had it running for weeks without problems.

Finally downgraded to 4.08, as that is the earliest one HP still offer on bootable CD, and it started working again ([on CD 7.40-b]("ftp://ftp.hp.com/pub/products/servers/supportsoftware/ZIP/firmware_maintenance-7.40-b.zip")).

My server also has a scsi card, no ide drives, just a single scsi hd.

One whole day wasted just to get my server booting again.

I hope somebody else will not fall into the same trap...

---

### Post by Thalandor on 2010-05-19
Thanks for the link. I ran into the same trouble.

---

