---
title: "Booting Ubuntu Server 8.10 from RAID1 (with GRUB)"
date: 2008-11-29
forum: Server Platforms
---

### Post by Muunsyr on 2008-11-29
Hi All,

This is my first post, although I have been lurking for some time.

I have been using Ubuntu for some time now, and have been very happy with it. I have just got some new hardware for a basic server (samba and squeezecenter for my Logitech Squeezebox). Which brings me to this post - this is the first time I have ever set up soft RAID with ubuntu (or any linux for that matter).

I have just successfully installed Server 8.10 (i386) with RAID 1 on two 750GB drives. After scrounging the net for guides I noticed several people mentioning setting up grub on both drives (in case it is the grub drive that fails). Is this still needed to be done manually with 8.10?

Your help will be greatly appreciated.

-Muunsyr

---

### Post by Philio on 2008-11-29
It wouldn't do any harm to do this yourself.

```
sudo grub-install /dev/sda
sudo grub-install /dev/sdb
```

(Use appropriate disks)

No idea if the installer does this automatically, but I would guess not.

---

### Post by andguent on 2008-11-29
I would agree with Philio above. The installer probably only installs grub once.

Installing grub on the second drive is not a bad idea, but keep in mind it may or may not work when needed. The good news is that if either drive is still good, grub can be recovered and rebuilt with the help of some good documentation and most any linux boot disk. Getting the second drive to boot properly is really only needed if you expect that no trained technicians can reach the server for a while after it goes down. 

WARNING: I'm suggesting something here that shouldn't break your setup, but could cause problems. To be mean, you can test by shutting the server off, disconnecting the primary drive, and starting it back up. Does it boot? That is one possible situation you may encounter.

The long and short of it that Linux software RAID is possibly one of the easiest RAID setups to recover from when a drive fails. Don't expect complete and total recovery on first reboot, but your data should be safe. Hotswap hardware RAID is better, but it usually only is available in high end servers.

If you haven't done so already, make sure you setup mdadm.conf and outbound email so your server can email you if it encounters a drive problem. Google is your friend (and I don't remember the steps off the top of my head).

---

