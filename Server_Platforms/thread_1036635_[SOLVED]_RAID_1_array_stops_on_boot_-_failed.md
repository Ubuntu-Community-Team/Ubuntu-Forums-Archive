---
title: "[SOLVED] RAID 1 array stops on boot - failed?"
date: 2009-01-11
forum: Server Platforms
---

### Post by Mattventura on 2009-01-11
When my server boots (without the "splash" and "quiet" boot options) I get errors such as md: md0 stopped, and then get dropped to a BusyBox shell. Nothing I can do with mdadm seems to work, and anything related to reassembling the array seems to give an "md: md0 stopped." error. mdadm --assemble --scan gives this:

```
mdadm: CREATE user root not found
mdadm: CREATE group disk not found
[  867.963387] md: md0 stopped.
mdadm: no devices found for /dev/md0
```

/etc/mdadm/mdadm.conf looks like (comments stripped):

```
DEVICE partitions
CREATE owner=root group=disk mode=0660 auto=yes
HOMEHOST <system>
MAILADDR root
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=71262188:8fa629ba:a5bce8ef:f436f2c6
```

What is interesting is that the array actually contains 3 devices. The third device was put into the array as an active device, a power failure occurred, and the system now refuses to boot. Does anyone know how to fix this without losing data?

---

### Post by Mattventura on 2009-01-11
Solved -- did "mdadm --assemble --force /dev/md0 /dev/sda2 /dev/sdb4 /dev/sdc3" (sda2,etc are the raid partitions)

---

### Post by Mattventura on 2009-01-11
OK, now it is doing it again when I reboot. How do I fix the raid superblocks to stop this?

Update: in the initramfs shell, mdadm.conf says I have 2 devices in my array, but mdadm --examine --scan says I have 3 (the correct number)

Fixed: resync array and use --update=super-minor

---

