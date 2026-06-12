---
title: "latest kernel update problems"
date: 2012-08-10
forum: Server Platforms
---

### Post by MakOwner on 2012-08-10
I'm running 10.04LTS on some older hardware.
I noticed there was an update pending this morning so I did an apt-get update, rebooted and all I get now is the grub > prompt.

I tried running the 10.04 LTS mini CD to get to rescue mode, but the installer never completes loading - I assume it's been pulled or is no longer accessible.

So, I have thrashed server, and I'm scheduled to get on a plane to go overseas in 5 hours.

I have pulled the boot drive and it appears to be clean, it's just grub that appears to be hosed from the update.

Can anyone tell me how to boot strap from grub so I an get the kernel running and get grub fixed?  

This hardware has a CD drive only, and I have been using the minimal image install, and becasue this thing only has 10/100 NICs, it usually takes hours to install, even when the net install image was available.

My best bet for gettting this up before I leave is to get grub fixed on the original drive...

---

### Post by Bachstelze on 2012-08-10
What I would do first is simply try to reinstall GRUB on the drive and see if something goes wrong. Basically mount the drive on another Linux system (preferably another Ubuntu 10.04, or at least another Debian/Ubuntu with the same GRUB version):

```
sudo mount /dev/rootpartition /somewhere
```

If you have a separate /boot partition, mount it as well:

```
sudo mount /dev/bootpartition /somewhere/boot
```

And do

```
sudo grub-install --boot-directory=/somewhere/boot /dev/drive
```

---

### Post by MakOwner on 2012-08-10
> **Bachstelze said:**
> What I would do first is simply try to reinstall GRUB on the drive and see if something goes wrong. Basically mount the drive on another Linux system (preferably another Ubuntu 10.04, or at least another Debian/Ubuntu with the same GRUB version):

```
sudo mount /dev/rootpartition /somewhere
```

If you have a separate /boot partition, mount it as well:

```
sudo mount /dev/bootpartition /somewhere/boot
```

And do

```
sudo grub-install --boot-directory=/somewhere/boot /dev/drive
```

You mean --root-directory instead of --boot-directory?

---

### Post by MakOwner on 2012-08-10
> **MakOwner said:**
> You mean --root-directory instead of --boot-directory?

No joy :(

It's been a while since I was burned by an update from canonical, but I guess it was just about time again. :/

---

