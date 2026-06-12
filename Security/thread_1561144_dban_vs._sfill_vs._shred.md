---
title: "dban vs. sfill vs. shred"
date: 2010-08-25
forum: Security
---

### Post by allaboutsam on 2010-08-25
I've noticed an enormous difference in the speed of Darik's Boot & Nuke, sfill, and shred, even when using similar(ish) settings:

dban w/ 3x pseudorandom overwrite: 120 Gb drive in ~5 hours = 24 Gb/hr (72 GB/hr if you count all three overwrites)

shred -u --iterations=1 (1x pseudorandom overwrite): 4 Gb file in ~15 minutes (not clocked) = ~16 Gb/hr

sudo sfill -l -l (i.e., single pseudorandom overwrite): 60 Gb free space in 36 hours = ~1.7 GB/hr

Does anyone have any idea why sfill is so *&#*#&! slow compared to dban or shred???

N.B. All three tests were done on the same physical drive (2.5", 5400rpm, 3.0G SATA), on the same computer, and shred and sfill were both run from the same installation of Ubuntu 10.04.1.

allaboutsam

---

### Post by rookcifer on 2010-08-25
If you want a faster method, try the following:

```
dd if=/dev/random bs=1k count=1 | openssl enc -kfile /dev/fd/0 -in /dev/zero -aes-128-cbc > /dev/sdx
```

You can make the output be either a drive or a file on a drive.  You can test it by changing "/dev/sdx" to something like "test_file."  In my tests this method seems faster than most others.

---

### Post by allaboutsam on 2010-08-26
Very interesting...

I just observed that if you use that on a file, it does not stop at the end of the file. I assume that it continues until it has overwritten all free space on the drive--correct? What happens when the drive is full?

If you use it on a device, does it wipe everything on the device or just the free space?

Thanks!

allaboutsam

---

