---
title: "LTSP - Changes to &quot;lts.conf&quot; file are having no effect"
date: 2008-09-05
forum: Server Platforms
---

### Post by marcopolo24124 on 2008-09-05
Hello All,

This is my first post, so please bear with me. My issue is this:

I've installed and configured a LTSP Server for my network. I've used "ltsp-build-client" without any problems. My thin clients boot just fine. I would, however, like to customize the way my clients boot on different computers (different screen resolutions, sound vs no sound, etc.).

From what I've read, this can be done by editing the "lts.conf" file. I also understand that this file is located in a couple of places, both are supposed to work but the one located outside of the chroot is preferred.

-The one located in the chroot (/opt/ltsp/i386/etc/lts.conf).

-The other located outside of the chroot (/var/lib/tftpboot/ltsp/i386/lts.conf).

I have edited both of these files - setting up a [default] section as well as trying a [MAC address] specific section with no affect to the thin clients (I did do a "sudo ltsp-update-image" when I edited the "/opt/ltsp/i386/etc/lts.conf" file).

**My question is:**

Are there any known issues with the "lts.conf" file in Hardy or is the file supposed to located somewhere else?

Any help would be greatly appreciated. I'm beating my head against the wall trying to figure this out.

Thanks...

---

### Post by Vince-0 on 2008-09-08
Hi!

I've experienced similar problems with the lts.conf:

There was no /opt/ltsp/i386/etc/lts.conf on my 8.04 alternate server, I created it, thought it would be there by default?

There is a /var/lib/tftboot/ltsp/i386/lts.conf file!

Both of these have ONLY this in those lts.conf files:

[Default]
X_MODE_0=1440x900

However, there are 3 or 4 out of 30 thin-clients which boot at a very low screen resolution, all the others all look good at a very high res on 19" wide LCDs by default. I've tried swapping thin-clients with the same results. It seems neither of the lts.conf's X_MODE_0 are being applied, even after updating the ltsp client images. Strange that only a few will boot with a very low screen res?

I've found a similar post:
[http://ubuntuforums.org/showthread.php?t=850836&highlight=ltsp](http://ubuntuforums.org/showthread.php?t=850836&highlight=ltsp)

But no definite reason for the cause of this. :confused:

I will continue to test with this, and post my findings.

Any insight would be greatly appreciated!

---

### Post by Vince-0 on 2008-09-10
*Update:*

I swopped the LCD on a thin client with a low resolution to an LCD with a high resolution and rebooted the client - and it seems the screen determines the resolution - the low res client now had a high res with the LCD from the high res client, the opposite is true for the other.

How is that even possible?:lolflag:

I've also checked all file paths and updated images as well as checked the permissions for the lts.conf file but still no luck.

I will continue to investigate tomorrow and post my findings!

---

### Post by marcopolo24124 on 2008-09-10
Thanks for the reply. I have still had no luck with the lts.conf file... in either place. I'll keep you posted.

---

### Post by jc2it on 2008-11-07
Try different settings for the resolution. If you look at the Thin client logs (on the thin client not the server) you should see an error when it trys to apply the screen resolution. The older monitors just are not capable of displaying that high resolution, so it defaults back to the lowest available. 

As for the other problem I would check the lts.conf syntax. I think it is pretty easy to break it. Or at least that has been my experience. There are some references that should help. 
The contents of:
```
/opt/ltsp/i386/usr/share/doc/ltsp-client-core/examples
```
There are two files here that should help.

lts.conf docs:
[http://wiki.ltsp.org/twiki/bin/view/Ltsp/LtsConf](http://wiki.ltsp.org/twiki/bin/view/Ltsp/LtsConf)

---

### Post by freerkkalsbeek on 2008-12-23
Hi,
I had some issues with getting lts.conf changes to have effect.
The syntax is fairly easy, but a few things are very important.

First of all. Having sections in the file.
Start your file with the [Default] section.

Then every setting must be indented. Either with 2 or more spaces or a tab.

If not indented, the file will not be parsed correctly and your changes will have no effect.

Working example:

```
[Default]
  NBD_SWAP=true
  X_VIDEO_RAM=32768
```

Furthermore I found out that in Mythbuntu the init scripts for ltsp-client-core and ltsp-client-setup are not running in the default runlevels.
For instance in rc3.d they are not started. This will mean that a number of options in lts.conf will have no effect, only the options parsed by mythbuntu-diskless-client are parsed.

Good luck,
Freerk

---

### Post by marcopolo24124 on 2008-12-26
Thanks, I've give that a try...

---

