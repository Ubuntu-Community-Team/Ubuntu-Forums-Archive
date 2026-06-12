---
title: "Rebuilding SoftRAID1"
date: 2008-05-29
forum: Server Platforms
---

### Post by Titan8990 on 2008-05-29
I have two drives that are mirrored via software RAID on a Ubuntu server.

I have been doing a lot of fault testing and have not been happy with the results.

If I pull one drive the system does not boot. 

If replace one drive with a fresh one the system does not boot. The replacement drive was the same size but not of the same firmware. Not sure if that was the issue or not but I plan to test this by wiping one of my RAID drives and trying to reinsert it with hope that it will rebuild.

If one drive completely dies how am I going to rebuild my array? 

Is there a way to force it to boot with only a single drive?

I have tried booting in to recovery mode and no luck with that either.

All suggestions/input are appreciated as always.

---

### Post by SpaceTeddy on 2008-05-29
software raids are not nearly as easy to manage as hardware ones are. For example, if you plug a new drive in, you need to partition it first with a proper raid partition and then tell mdadm to sync with the other drive. As far as i know, it does not work out of the box like hardware raids do. 

As for the booting issue - make sure you install grub to ALL drives, not just the boot one. for example, i have 4 drives in my server, where the first 10 Gbyte is a raid-1 on all four drives holding the linux, and the left over 4X490 Gbyte is a raid-5. I also made very sure that i can boot from ANY of the four drives by installing grub on all of them. 

hope it helps :)

---

### Post by Titan8990 on 2008-05-29
Because it is a mirror I would assume that grub would install on both drives since they should be identical. Grub loads but when Ubuntu is loading it stops at the part when it is checking SATA devices. This is really a guess because the last thing that it does before it halts is check the DVD drive.

> For example, if you plug a new drive in, you need to partition it first with a proper raid partition and then tell mdadm to sync with the other drive.

How will I sync them if I can't boot into the only OS that recognize the drives as a RAID set? Can I do it from the live Ubuntu CD and it will be recognized in my actual installed OS?

Thanks for your input.

---

### Post by quelx on 2008-05-29
Are you using **mdadm** to manage the drives or a driver from the hardware vendor?

I've used mdadm with much success and despite the slight performance hit, it does well enough for quick and dirty (and cheap) arrays.

Here is a howto for using GRUB on mdadm arrays (so they both boot)

[https://help.ubuntu.com/community/Installation/RAID1](https://help.ubuntu.com/community/Installation/RAID1)

---

### Post by Titan8990 on 2008-05-29
I set it up during the OS installation which I believe uses mdadm because I can view the RAID details via a mdadm command.

I saw that article when I was researching but I thought it was dated. Will give it a shot tomorrow and let you know

---

### Post by quelx on 2008-05-29
The page itself is dated but the information isn't.  The bottom **Hoary Update** section should suffice.  The only extra step is installing **grub** on both drives, not the md device or just one...
```
$ sudo grub
grub> device (hd0) /dev/sda
grub> root (hd0,0)
grub> setup (hd0)
grub> device (hd0) /dev/sdb
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```

of course if a drive fails you should be able to boot the second, once you get a replacement **grub** will need to be installed on the new drive, but that shouldn't be too much of a problem even on a live system.

---

### Post by Titan8990 on 2008-05-30
I am still going to give it a try but like I said earlier, grub boots, the OS does not.

---

