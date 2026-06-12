---
title: "Enabling CPU security (NX)"
date: 2010-05-12
forum: System76 Support
---

### Post by akwala on 2010-05-12
On my Serval, model "serp4", running Lucid...
```
$ /usr/bin/check-bios-nx --verbose
This CPU is family 6, model 23, and has NX capabilities but is unable to
use these protective features because the BIOS is configured to disable
the capability.  Please enable this in your BIOS.  For more details, see:
https://wiki.ubuntu.com/Security/CPUFeatures
```...I followed the instructions for Ubuntu 10.04 here: [https://wiki.ubuntu.com/Security/CPUFeatures](https://wiki.ubuntu.com/Security/CPUFeatures)

Looking at the BIOS settings, it wasn't apparent where/how I could enable NX. Can anyone help?

---

### Post by thomasaaron on 2010-05-13
The BIOS manufacturers did not enable that option, and they did not create a way for the user to toggle it.

I don't know if it is because the motherboard itself doesn't support it, or because, like the wiki says...
> 
Many BIOS manufacturers disable the features in a conservative attempt to help legacy operating systems that may perform strangely when these features are available. 

---

### Post by JPtja on 2010-06-11
Hello,

I have this problem here aswell, but I can't set up my NX-compatibilities..

What can I do now?

---

### Post by narcisgarcia on 2010-12-26
I have the "check-bios-nx" message in a lot of computers, and because of lacking BIOS option to enable NX feature, now I remove the warning message:

```
sudo rm /etc/update-motd.d/20-cpu-checker
```

---

### Post by narcisgarcia on 2010-12-26
I see the "check-bios-nx" message in a lot of computers, and because of lacking BIOS option to enable NX feature, now I remove the warning message:

```
sudo rm /etc/update-motd.d/20-cpu-checker
```

---

### Post by vestelle on 2011-05-10
Hi to all, 

I have just installed the Ubuntu server 10.04.2 and I receive the same NX capability alert every time I connect to my server. After reading the link [https://wiki.ubuntu.com/Security/CPUFeatures](https://wiki.ubuntu.com/Security/CPUFeatures), I checked my BIOS and it seems this option is already activated. My CPU is 64bits although I'm using the 32bits SO, and I'm using the 2.6.32-28-generic-pae, so I wouldn't expect this alert to appear. 

I'm just considering removing this alert as proposed in previous posts, but before doing it, I would like to know if this capability is actually used or not in my system...

Thanks to all!

---

