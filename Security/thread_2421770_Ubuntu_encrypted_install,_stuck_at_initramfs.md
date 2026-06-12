---
title: "Ubuntu encrypted install, stuck at initramfs"
date: 2019-06-26
forum: Security
---

### Post by allusernamestaken on 2019-06-26
Never seen this, google has failed me so I'm here. Booting from a USB I can mount the drive and everything is there, just can't boot normally. Screenshot [https://i.redd.it/wsvi4nobk7631.jpg](https://i.redd.it/wsvi4nobk7631.jpg)

[IMG]https://i.redd.it/wsvi4nobk7631.jpg[/IMG]

---

### Post by TheFu on 2019-06-27
Looks like some sort of RAID is involved. If you aren't doing RAID, then could one of the disks be marked as RAID member from prior use? If so, those flags need to be removed using the RAID tool.

If not, then we need more detailed data. Inside your 'live boot environment', please install boot-repair, but DO NOT let it repair anything.  Run the get/gather info task and post the URL back here.

---

### Post by allusernamestaken on 2019-06-27
No raid, it's a single drive laptop, hence why I used the full disc encryption, just in case someone steals it. It had been working normally for months before this happened after an update.

I'll try it in a few.

---

### Post by TheFu on 2019-06-27
I'm running 16.04.6 with LVM + LUKS encryption and patch weekly on Saturday mornings.  Not seeing this issue here.

Best to always say the release version being used.

---

### Post by allusernamestaken on 2019-06-27
How would I go about seeing why it would be looking for a raid array?

---

### Post by Rubi1200 on 2019-06-28
Can you boot a previous kernel from GRUB advanced menu?

As TheFu asked, which version are you on?

Output from this might also help:

```
journalctl -b
```

---

### Post by TheFu on 2019-06-28
I've asked for information. boot-info and the OS version.
None has been provided.  Kinda can't help. Good luck.

---

### Post by chrispeddler on 2019-06-30
Maybe an Ubuntu update can help solve the issue. Have you done that?

---

### Post by allusernamestaken on 2019-07-11
Can't update if I can't boot the system, can I? Or is there a way to do so from a live install without wiping out the in place install?

---

### Post by CharlesA on 2019-07-12
Hi,

I ran into something similar to this a long time ago. I don't recall how I got it fixed, but I think it involved having to force the cryptsetup modules to load in initramfs

Boot into the live environment and chroot to your encrypted install. See here: [https://feeding.cloud.geek.nz/posts/recovering-from-unbootable-ubuntu-encrypted-lvm-root-partition/](https://feeding.cloud.geek.nz/posts/recovering-from-unbootable-ubuntu-encrypted-lvm-root-partition/)

You can also try running this command from the chroot'd install and see if you get any results:
```
sudo update-initramfs -v -u -k all | grep crypt | grep -v crypto
```

You should get something like this:
```
Adding config /etc/initramfs-tools/conf.d/cryptroot
Calling hook cryptroot
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
/usr/share/initramfs-tools/scripts/local-top/ORDER ignored: not executable
/usr/share/initramfs-tools/scripts/local-bottom/ORDER ignored: not executable
/usr/share/initramfs-tools/scripts/local-block/ORDER ignored: not executable
/usr/share/initramfs-tools/scripts/init-top/ORDER ignored: not executable
/usr/share/initramfs-tools/scripts/init-bottom/ORDER ignored: not executable
/usr/share/initramfs-tools/scripts/local-premount/ORDER ignored: not executable
Adding module /lib/modules/4.15.18-17-pve/kernel/drivers/md/dm-crypt.ko
Adding binary /sbin/cryptsetup
Adding library-link /lib/x86_64-linux-gnu/libcryptsetup.so.4
Adding library /lib/x86_64-linux-gnu/libcryptsetup.so.4.7.0
Adding library-link /lib/x86_64-linux-gnu/libgcrypt.so.20
Adding library /lib/x86_64-linux-gnu/libgcrypt.so.20.1.6
Adding binary /lib/cryptsetup/askpass
Calling hook cryptroot-unlock
Calling hook cryptpassdev
Calling hook cryptkeyctl
Calling hook cryptgnupg
Adding config /etc/initramfs-tools/conf.d/cryptroot
Calling hook cryptroot
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
/usr/share/initramfs-tools/scripts/local-top/ORDER ignored: not executable
/usr/share/initramfs-tools/scripts/local-bottom/ORDER ignored: not executable
/usr/share/initramfs-tools/scripts/local-block/ORDER ignored: not executable
/usr/share/initramfs-tools/scripts/init-top/ORDER ignored: not executable
/usr/share/initramfs-tools/scripts/init-bottom/ORDER ignored: not executable
/usr/share/initramfs-tools/scripts/local-premount/ORDER ignored: not executable
Adding module /lib/modules/4.15.18-15-pve/kernel/drivers/md/dm-crypt.ko
Adding binary /sbin/cryptsetup
Adding library-link /lib/x86_64-linux-gnu/libcryptsetup.so.4
Adding library /lib/x86_64-linux-gnu/libcryptsetup.so.4.7.0
Adding library-link /lib/x86_64-linux-gnu/libgcrypt.so.20
Adding library /lib/x86_64-linux-gnu/libgcrypt.so.20.1.6
Adding binary /lib/cryptsetup/askpass
Calling hook cryptroot-unlock
Calling hook cryptpassdev
Calling hook cryptkeyctl
Calling hook cryptgnupg
Adding config /etc/initramfs-tools/conf.d/cryptroot
Calling hook cryptroot
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
/usr/share/initramfs-tools/scripts/local-top/ORDER ignored: not executable
/usr/share/initramfs-tools/scripts/local-bottom/ORDER ignored: not executable
/usr/share/initramfs-tools/scripts/local-block/ORDER ignored: not executable
/usr/share/initramfs-tools/scripts/init-top/ORDER ignored: not executable
/usr/share/initramfs-tools/scripts/init-bottom/ORDER ignored: not executable
/usr/share/initramfs-tools/scripts/local-premount/ORDER ignored: not executable
Adding module /lib/modules/4.15.18-14-pve/kernel/drivers/md/dm-crypt.ko
Adding binary /sbin/cryptsetup
Adding library-link /lib/x86_64-linux-gnu/libcryptsetup.so.4
Adding library /lib/x86_64-linux-gnu/libcryptsetup.so.4.7.0
Adding library-link /lib/x86_64-linux-gnu/libgcrypt.so.20
Adding library /lib/x86_64-linux-gnu/libgcrypt.so.20.1.6
Adding binary /lib/cryptsetup/askpass
Calling hook cryptroot-unlock
Calling hook cryptpassdev
Calling hook cryptkeyctl
Calling hook cryptgnupg

```

---

