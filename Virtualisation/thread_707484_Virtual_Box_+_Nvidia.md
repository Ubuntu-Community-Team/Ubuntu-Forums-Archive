---
title: "Virtual Box + Nvidia?"
date: 2008-02-25
forum: Virtualisation
---

### Post by justin whitaker on 2008-02-25
Quick question: I installed Virtual Box on my Hardy install, after setting up the restricted drivers for my Nvidia card. On reboot, I had to go back and reconfigure X, because Virtual Box needs the vanilla kernel. 

So how do I get the official drivers working? Reinstall with the .run file from Nvidia?

I'm not saying I need the eye candy, but it would be nice, seeing that I have the card already. :)

---

### Post by ppietryga on 2008-02-25
When You install new kernel VirtualBox needs to rebuild it's module.
Type:
```

sudo /etc/init.d/vboxdrv setup

```
I think You'll need the kernel headers package installed.

---

### Post by Whiffle on 2008-02-25
I would try doing the nvidia .run again, I've got both virtualbox and nvidia drivers from the .run file working on mine (feisty), without doing anything special.  I don't remember which one I installed first though.

Also, are you sure the nvidia kernel module is loading? ( should be listed w/ lsmod as "nvidia" when you boot the computer)

---

