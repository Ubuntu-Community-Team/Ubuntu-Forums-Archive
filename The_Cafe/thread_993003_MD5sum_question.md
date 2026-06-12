---
title: "MD5sum question"
date: 2008-11-25
forum: The Cafe
---

### Post by Dr Small on 2008-11-25
If I rip the Ubuntu 8.10 CD (from Shipit) to my computer, the MD5sum of the ISO should be identical to the one off the website, correct?

Because the website one is:
```
24ea1163ea6c9f5dae77de8c49ee7c03 *ubuntu-8.10-desktop-i386.iso
```

While mine, that I ripped, is:
```
0385697292f0f5f7e41da74bc6c1c744  ubuntu-8.10-i386.iso
```

To rip it, I merely ran:
```
dd if=/dev/cdrom of=ubuntu-8.10-i386.iso
```

---

### Post by ice60 on 2008-11-25
i'm not surprised it's not the same, the checksum was taken before it was burned, it only takes one bit to change for the whole checksum to be different.

---

### Post by wieman01 on 2008-11-25
But there is an issue with the image (after burning). You might not notice it but ideally the hashes ought to match up. I rarely pay attention to hashes though.

---

### Post by Dr Small on 2008-11-25
Ok. Well, I burned them anyways. There may have been a problem with the burn from Shipit, but I didn't notice any. So I just burnt them to disc and they still work like the original and I am happy.

---

### Post by wieman01 on 2008-11-25
Exactly. You might not even need the data/packages that reside in the section that is damaged, so there is a pretty good chance the CD will make you happy after all. :-)

---

### Post by Dragonbite on 2008-11-25
I've gotten a bad disk from ShipIt, so it does happen.

On the other hand, there is the "Check CD for errors" option on the main menu which if I understand it correctly basically runs / checks the md5sum on the CD. So this would do it for you even after it has been burned.

---

### Post by ice60 on 2008-11-25
do you all think it's possible to take the md5 for a livecd iso, then burn it, and rip it, using dd, and get the same checksum again? i bet none of you can do it! i don't think it's been damaged.

---

### Post by Dr Small on 2008-11-25
> **ice60 said:**
> do you all think it's possible to take the md5 for a livecd iso, then burn it, and rip it, using dd, and get the same checksum again? i bet none of you can do it! i don't think it's been damaged.
I don't think it is possible, because the burn speed and rip speed can ruin things, or just miss one bit, and ruin the entire hash.

---

### Post by Moustacha on 2008-11-25
I burnt the 8.10 CD this morning, and the CD write program said there was an error. I ran md5sum on the iso and the CD (md5sum /dev/cdrom) and they were both the same. Rather odd.

---

### Post by maybeway36 on 2008-11-25
Try checking the sums from md5sum.txt on the CD:
```
mount /dev/cdrom
cd /media/cdrom
md5sum -c md5sum.txt
```

---

### Post by x0as on 2008-11-25
> **ice60 said:**
> do you all think it's possible to take the md5 for a livecd iso, then burn it, and rip it, using dd, and get the same checksum again? i bet none of you can do it! i don't think it's been damaged.

You would have lost that bet.

```

gamma:~ x0as$ dd if=/dev/disk2s0 of=Desktop/ubun.iso bs=2k
357905+0 records in
357905+0 records out
732989440 bytes transferred in 272.113997 secs (2693685 bytes/sec)
gamma:~ x0as$ md5 Desktop/ubun.iso Downloads/ubuntu-8.10-desktop-amd64.iso 
MD5 (Desktop/ubun.iso) = f9cdb7e9ad85263dde17f8fc81a6305b
MD5 (Downloads/ubuntu-8.10-desktop-amd64.iso) = f9cdb7e9ad85263dde17f8fc81a6305b
```

---

### Post by wieman01 on 2008-11-26
> **ice60 said:**
> do you all think it's possible to take the md5 for a livecd iso, then burn it, and rip it, using dd, and get the same checksum again? i bet none of you can do it! i don't think it's been damaged.
In all likelihood, you would win the bet...

---

### Post by Liviu-Theodor on 2008-11-26
One more thing: you could burn first on a re-writable cd. If it doesn't work, just erase it. If it works, you could burn on a regular cd.

---

### Post by Dragonbite on 2008-11-26
> **Liviu-Theodor said:**
> One more thing: you could burn first on a re-writable cd. If it doesn't work, just erase it. If it works, you could burn on a regular cd.

I'm more inclined to use USB sticks to make bootable and install from there.  The advantage is to be able to run entire DVDs or CDs depending on the distribution.

Haven't gotten it to work foolproof yet, but did manage to use it once on a system that doesn't have a CD-rom (laptop with a plug-in CD dock which the CD drive died on me.. want to replace it with a DVD anyway but until then my 8 GB drive works!)

---

### Post by Polygon on 2008-11-26
the iso and the finalized dvd will have different hashes most likely

as long as the downloaded ISO has a correct hash, it should be fine

since ubuntu gets installed as an iso, if the hash is wrong then its a VERY bad thing. Use torrents or something

---

