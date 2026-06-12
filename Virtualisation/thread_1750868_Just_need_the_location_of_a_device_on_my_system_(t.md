---
title: "Just need the location of a device on my system (the path)"
date: 2011-05-06
forum: Virtualisation
---

### Post by ClientAlive on 2011-05-06
Running Ubuntu 10.04 in Oracle VM Virtual Box.

I'm working on installing the guest additions and am asked to first "change directories" (cd) to a certain location but I'm not exactly sure where that is. The instruction reads thus:

> 
Change to the directory where your CD-ROM drive is mounted and execute as root:
sh ./VBoxLinuxAdditions.run


If anyone can give me the path for this I would sure appreciate it.

Thank you.
:)

---

### Post by ClientAlive on 2011-05-06
I think I found it. Thanks anyway folks. Sorry for the bother.

Found my answer here:  [http://superuser.com/questions/261643/cant-install-guest-additions-using-virtualbox-ubuntu-guest-os-win7-host-os](http://superuser.com/questions/261643/cant-install-guest-additions-using-virtualbox-ubuntu-guest-os-win7-host-os)

```
cd /media
```

:D

---

