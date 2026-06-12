---
title: "disable lvm full disk encryption..."
date: 2013-04-18
forum: Security
---

### Post by moostapha on 2013-04-18
In short, I'm not satisfied with the disk performance using LVM's full disk encryption on 12.10. Running a Samsung 840 Pro in a modern Thinkpad, I'm getting <6MB/s and under 1500 IOPS. 

That's unacceptable. 

Without reinstalling from scratch, is there a good way to disbale the LVM encryption and try the hardware encryption my SSD offers? Or do I just need to bite the bullet, wipe, and reinstall? 

Yes, if I'd been thinking, I would have just used the hardware option to begin with. But suffice it to say that I wasn't thinking when I did the install. I'd actually forgotten that my SSD had that feature.

---

### Post by Cheesemill on 2013-04-18
If you want to disable LVM encryption then yes, you have to reinstall.

However there may be another issue at work here, the dm-crypt overhead shouldn't really be any more than 5% or 10% if you are using a modern CPU.
On my laptop with encrypted LVM I get >100MB/s for read and write.

---

### Post by KaosuX on 2013-04-18
> **moostapha said:**
> In short, I'm not satisfied with the disk performance using LVM's full disk encryption on 12.10. Running a Samsung 840 Pro in a modern Thinkpad, I'm getting

Please review the advice I gave in the following thread: [http://ubuntuforums.org/showthread.php?t=2132516](http://ubuntuforums.org/showthread.php?t=2132516). Once you have mounted the encrypted device, it would be easy to create an image of the non-encrypted contents and then reload it back on a freshly formatted drive to save yourself some time. However, if you already have good recent backups and don't mind setting your system back up for your specific hardware and needs then the advice from the poster above me would also be a quick and easy route to achieve your overall goal. 

If you're not comfortable working with LVM's and such in general, then you might actually save time just reinstalling Ubuntu from scratch and using your most recent backup to save your personal files.

---

### Post by moostapha on 2013-04-18
I think a fresh install might be the best idea. I don't actually need LVM on this machine (single-disk laptop) and everything important is in my dropbox anyway. AFAIK, the only advantage of LVM in my situation is being able to create snapshots, which I haven't seriously looked into yet. It might not be all that important given the redundancy I already have. But, it could be nice. I abuse snapshos for VMs like mad. 

The biggest hinderance would be writting a post-install script to fetch & install everything I need and do some configurations (mostly replacing stuff in /usr/bin with scripts to call them correctly), plus waiting about 10 hours for my Dropbox to re-sync before I can do anything else. 

If it's just a weird setup issue, I'm open to looking into it. Here's what I'm getting from ioping: 

"HACKINTOSH" is a desktop (accessed over ssh) with a Mercury Accelcior in an x8 slot. "LAPTOP" is a Thinkpad x230 running ubuntu with an 840 Pro (I think...whatever the current 7ish mm samsung pro-series SSD is). 

[@HACKINTOSH:~]$ ioping -c 4 .
4096 bytes from . (hfs /dev/disk0s2): request=1 time=0.0 ms
4096 bytes from . (hfs /dev/disk0s2): request=2 time=0.0 ms
4096 bytes from . (hfs /dev/disk0s2): request=3 time=0.0 ms
4096 bytes from . (hfs /dev/disk0s2): request=4 time=0.0 ms

--- . (hfs /dev/disk0s2) ioping statistics ---
4 requests completed in 3003.2 ms, 81633 iops, 318.9 mb/s
min/avg/max/mdev = 0.0/0.0/0.0/0.0 ms


[@LAPTOP:~]$ ioping -c 4 .
4096 bytes from . (ext4 /dev/mapper/ubuntu-root): request=1 time=0.4 ms
4096 bytes from . (ext4 /dev/mapper/ubuntu-root): request=2 time=0.8 ms
4096 bytes from . (ext4 /dev/mapper/ubuntu-root): request=3 time=0.7 ms
4096 bytes from . (ext4 /dev/mapper/ubuntu-root): request=4 time=0.8 ms

--- . (ext4 /dev/mapper/ubuntu-root) ioping statistics ---
4 requests completed in 3003.3 ms, 1500 iops, 5.9 mb/s
min/avg/max/mdev = 0.4/0.7/0.8/0.2 ms

The results from the hackintosh are actually a bit slower than I'm used to. I wonder what it's up to.

---

