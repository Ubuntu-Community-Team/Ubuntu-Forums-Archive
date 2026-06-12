---
title: "Question on Xmir and 13.10"
date: 2013-09-06
forum: Ubuntu Development Version
---

### Post by wgarcia on 2013-09-06
I've just upgraded one of my systems to 13.10. Is it going go be running Unity on Xmir just with the upgrade, and how do I check it?

---

### Post by Alan F on 2013-09-06
You need to specifically install Mir.

See here for details ....

[https://wiki.ubuntu.com/Mir/Installing](https://wiki.ubuntu.com/Mir/Installing)

---

### Post by wgarcia on 2013-09-06
Thanks, everything is very clear in the link that you provide.

---

### Post by grahammechanical on 2013-09-06
At some point between now and the release date of 13.10 there will be available ISO images that install xmir as the server by default instead of Xserver but only if we are running the Nouveau open source video driver. If we install third party software during installation then we will automatically get a proprietary video driver. We are waiting proprietary video driver that run with xmir. Will these proprietary video drivers be availbale by the end of October? Or will we have to wait until the release of 14.04?

So, depending on whether you installed a proprietary video driver or not, you may already be running xmir. This is one of the commands I used to test if xmir is loaded.

```
 grep -i LoadModule /var/log/Xorg.0.log
```

And I see this

> [    19.203] (II) LoadModule: "xmir"

If you do not get a response from some of those commands, then xmir is not loaded.

Regards.

---

### Post by jerrylamos on 2013-09-06
Good luck.  Saucy + mir on this notebook Acer Aspire 5253 Radeon 6310 with or without external monitor the only way saucy with mir will run is in recovery mode, reduced resolution, sluggish, bugs filed.
On my netbook with Intel Atom, saucy + mir displays the external screen with the smaller built in screen picture overlaid - two launchers, etc.  
Oh, yes, drivers are whatever came with the Ubuntu .iso.
I hope to keep up with mir ppa changes...

BTW, recent saucy running very well, nice, until the mir install.

---

### Post by wgarcia on 2013-09-07
I have tried Mir now and here on a Dell Latitude E6410 Unity runs well on Xmir. No performance loss noticed compared to running it on plain X. The only problem I found so far is that an application that runs on Java (pdfstudio) does not open (bug filed, [https://bugs.launchpad.net/ubuntu/+source/unity-system-compositor/+bug/1221817](https://bugs.launchpad.net/ubuntu/+source/unity-system-compositor/+bug/1221817)). I haven't tried an external monitor though.

---

