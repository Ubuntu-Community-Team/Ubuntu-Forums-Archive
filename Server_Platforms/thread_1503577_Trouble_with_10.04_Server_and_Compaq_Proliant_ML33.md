---
title: "Trouble with 10.04 Server and Compaq Proliant ML330 G2 w/ATA RAID"
date: 2010-06-07
forum: Server Platforms
---

### Post by sha.goyjo on 2010-06-07
Hey there. I'm having a great deal of time getting Lucid Server up and running on my Compaq Proliant ML330 G2. I've put a thread up in installing and upgrading, but people there don't seem to have any ideas about my problem. Since I figured there would be a higher concentration of server users here, somebody might be able to help.
,
I've got a Proliant ML330 G2, 2 1.4 GHz PIV's
A dvd and CD drive on IDE1 (I'll explain why in a moment
A 65 gb hdd on IDE2
and four 40gb hdd's on hardware ide raid.

I've tried everything, but I can't get the sucker to boot. Installing to the raid array doesn't work. Some array setups won't partition, and others aren't even recognized as arrays. I've tried disabling the raid array and installing to the IDE hdd (my original intention) but I just get bad system disk errors.

It would be exceptionally helpful if anyone has one of these boxes, or has worked on one, but I'm willing to take advice from any direction at this point. Thanks.

---

### Post by CharlesA on 2010-06-07
Which drive is it installing GRUB on?

Can you boot off a livecd and post the output of this:

```
sudo fdisk -l
```

---

### Post by sha.goyjo on 2010-06-07
I've tried every option with grub, incl putting it on the mbr of the drive I want to boot from and the superblock. Only boot option I haven't tried yet is lilo.

I'll do the fdisk output after I get off of work tonight.

---

### Post by sha.goyjo on 2010-06-09
Sorry this took so long. I had to take my Fiancee to the airport to go on her peace corps TOD, and I've been in fairly constand mournful depression since.

Please keep in mind that this output is from my hand written notes.

```

255 heads 634 sectors/track 7476 cylinders
units = cylinder of 16065x512 = 822520 bytes
Disk Identifier = 0x00016832
device           boot         start        end        type
/dev/sda1         *            1            32         linux
partition does not end on cylinder boundary
/dev/sda2                      6870         7477       linux swap/solaris
/dev/sda3                      32           6870       linux
partition tables are not in disk order

```

Please keep in mind that this is not the first paritioning scheme I've tried. This time I was trying to create a small partition for booting to see if the system was used to having a special /boot partition to boot from. Idk, it was just a thought. If anyone has an idea I'd love to hear it.

---

