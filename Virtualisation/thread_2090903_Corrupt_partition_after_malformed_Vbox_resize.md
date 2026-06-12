---
title: "Corrupt partition after malformed Vbox resize"
date: 2012-12-03
forum: Virtualisation
---

### Post by worldsayshi on 2012-12-03
I'm a great big fool and I deserve the pain I've brought upon myself. 

I was a bit stressed. Though, "Well a vbox resize ought to work, I can't take all safety measures every time. Don't think just do it already;  So :" > VBoxManage modyfihd --resize <it was kb's here wasn't it ?> <hit Enter>. 1%..100%. "Ah that went swell." NOPE!

So I got this:
```

error: no such partition.
grub rescue>
```
running 'ls' and 'ls <drivename>' will yield the same responses. So the vdi max size has been set to an outrageous value and that has somehow messed with the partition as well.

(Foolishly I have two weeks worth of non versioned thesis code on the vm)

I've followed most of the guides I have been able to find out there. Some have produced what looks like at least partial solutions.

What I've tried:
1. Using clonezilla I think I managed to extract the partition from the "oversized" vdi image.
2. I created a new vb image, created a partition on it and tried loading the clonezilla image onto it. It seemed to produce some error message after 50%. But it was a bit unclear if it succeeded or failed. I pressed on. Doing the same thing again seemed pointless.
2b. Booting the partition still gave the same grub error.
3. I tried using **boot-repair** on the partition to no avail. Boot-repair report success but the grub response is the same.
4. I used testdisk - it seems like it found something. There is now a smaller partition on this vdi copy, but it's still non-bootable with grub error message "error file not found". Testdisk left 3 mb unused space just before the partition lying around. :confused: And then several gb at the end (my margin when creating the new vdi).

I feel like I'm mostly waving around in the dark here. What do you think I should try next? I hope I'm making sense with this. :mad:

What I have:
A. The original "oversized" vdi
B. A clonezilla resurection image of the corrupted partition.
C. A testdisk analyzed vdi with a smaller partition bearing a closer resemblence to the original partition, but still non-bootable.

---

