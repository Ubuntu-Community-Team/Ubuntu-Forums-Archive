---
title: "need to install small XP, but have ubuntu using the entire disk"
date: 2013-11-23
forum: Windows
---

### Post by squakie on 2013-11-23
I'm not sure, but I think the answer on this might be no.

I've completed a couple of Raspberry Pi media centers only to find I messed up a few the old VHS scans and need to rescan them.  I never was able to make the USB video capture devices (I tried 3) work in Ubuntu, but at that point I still had a small XP install in dual boot.  After I thought I was finished, I reinstalled Ubuntu, using the entire disk.

So, I need a small XP install again.  I have an apparently broken DVD/RW at the moment, so I can't proceed anyway, but I wanted to "get my ducks in a row" first.

I *thought* there was something about XP needing to be the first partition on the disk - but I could be very wrong there.  I also have no clue if it's even possible to shrink a ext3 partition to make room for a small XP installation.  I know about the MBR getting messed up and how to correct that, so that part is minor.  I just don't know about the NTFS partition placement and an ext3 partition can be shrunk.

Any ideas would be appreciated!

---

### Post by monkeybrain20122 on 2013-11-23
Found this

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) Scroll down and there are ways to install Windows after Ubuntu.

---

### Post by squakie on 2013-11-23
Thanks for the link!  Unfortunately, there is no mention there of resizing a linux partition to make room for Windows, nor any mention of whether or not the Windows partition needs to be first on the disk (this may have been an old requirement).

---

### Post by Impavidus on 2013-11-23
I never tried it, but I think it should be OK to shrink the ext3 partition. I don't think Win XP must be the first partition, but I read it must be a primary partition before the extended partition.

---

### Post by Bucky Ball on 2013-11-23
*Thread moved to **Other OS/Distro Support**.*

---

### Post by squakie on 2013-11-23
> **Impavidus said:**
> I never tried it, but I think it should be OK to shrink the ext3 partition. I don't think Win XP must be the first partition, but I read it must be a primary partition before the extended partition.

Yep - I think you're right about the primary partition thing - and guess what - yep I already have extended partitions on the driver ;(

Oh well - it was worth a shot!

Thainks everyone for the info!

---

