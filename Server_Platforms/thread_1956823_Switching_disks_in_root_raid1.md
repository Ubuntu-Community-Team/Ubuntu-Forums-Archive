---
title: "Switching disks in root raid1"
date: 2012-04-11
forum: Server Platforms
---

### Post by davidmaxwaterman on 2012-04-11
I'm attempting to replace two disks in my root fs's raid1.
To start with, I attached the new disks and added them to the raid1.
So now it is a raid1 with 4 disks, but when I remove the original two drives, the system won't boot.
Clearly I need to do something more to make the disks bootable.

Anyone?

---

### Post by rubylaser on 2012-04-11
Did you setup grub on the new disks?

```
grub-install /dev/sdc
grub-install /dev/sdd
```

^ assuming those are the correct disks. And, are the disks in the correct order (first) in your BIOS?

---

### Post by davidmaxwaterman on 2012-04-12
> **rubylaser said:**
> Did you setup grub on the new disks?

```
grub-install /dev/sdc
grub-install /dev/sdd
```

^ assuming those are the correct disks. And, are the disks in the correct order (first) in your BIOS?


No, I didn't do that :)

I've removed all irrelevant disks, temporarily, to prevent any mistakes on that front.

This sounds like a plan :

1) grub-install on the new disks
2) mdadm --remove the old ones
3) shutdown
4) move the disks to the ports the old ones were on
5) boot

It'll happen later today, I think.

Max.

---

