---
title: "Problem with LVM"
date: 2005-05-24
forum: Server Platforms
---

### Post by dierre on 2005-05-24
Hello...

thanks to ubuntu I have discovered what LVM is (it just made me curious seeing it in the init script) and I am playing a little around with it.

I have created my PVs, created a LV, added the formers to the latter... everything went fine.

But I'm having troubles trying to move a PV out of a LV... this is what I get:
```

root@luisa:~ # pvmove /dev/sda1
  mirror: Required device-mapper target(s) not detected in your kernel
```

I googled a little around and it seems to be a kernel problem...
Anybody has made it work with ubuntu? I'm using ubuntu 5.04 and kernel  2.6.10-5-386

Thanks in advance,
Francesco

---

### Post by tonym on 2005-05-27
You have to install the dm-mirror kernel module.  I have used pvmove a number of times,  sometimes it works quite happily, sometimes it corrupts things quite nicely.  By choice if I had space I would create a new lv and copy files across.

Regards

Tony.

---

