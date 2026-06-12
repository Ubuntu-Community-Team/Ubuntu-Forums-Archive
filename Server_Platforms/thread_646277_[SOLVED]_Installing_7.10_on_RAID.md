---
title: "[SOLVED] Installing 7.10 on RAID"
date: 2007-12-21
forum: Server Platforms
---

### Post by stickmangumby on 2007-12-21
I've been putting together a file server, with the following in it:

- 3x 160GB SATA HDD
- Gigabyte M68SM-S2 motherboard

The hard drives are currently blank, so I'm free to mess around.

The motherboard has onboard RAID, so I fired up the BIOS and set up a RAID5 array. I then booted up an Ubuntu 7.10 Server CD and tried to install. However, when it gets to the disk partitioning stage, it sees three HDDs, not a single RAID array.

I've been reading the forums for info, and it seems like some mobos with RAID really only have 'software' RAID, in that they have a RAID chip that uses the CPU and main memory, rather than a dedicated processor and memory for RAID. It seems that this is likely to be the case, as it was a cheap mobo, but I can't find confirmation of that anywhere.

So, how do I go about setting up RAID on this system?

---

### Post by jpkotta on 2007-12-21
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I'd just go with software RAID in Linux and not even bother with the FakeRAID.  The real purpose of FakeRAID is to make it easier for Windows to see the RAID array, Linux doesn't really have trouble booting from RAID arrays.  If you go with Linux software RAID, just turn off the FakeRAID.

[https://help.ubuntu.com/community/Installation/LVMOnRaid](https://help.ubuntu.com/community/Installation/LVMOnRaid)
[https://help.ubuntu.com/community/FileServerOnLVMOnRAID1](https://help.ubuntu.com/community/FileServerOnLVMOnRAID1)
[https://help.ubuntu.com/community/Installation/FileServerWithRAID](https://help.ubuntu.com/community/Installation/FileServerWithRAID)

You will want the alternative install CD, because the desktop doesn't have RAID support (not sure about server, it probably works too).  

On my server, I have a small (18GB) drive that holds the rootfs, and my RAID5 array just stores data, so I didn't have to worry about booting from the array.  On my desktop, I boot from a RAID1 and / is on a RAID0.  

On my server I put LVM on top of the RAID array, because it looks like it's easier to add another array if I want.  I tested it; I could add partitions to the LV and grow the fs.

[http://www.tldp.org/HOWTO/LVM-HOWTO/index.html](http://www.tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html](http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html)

I figured out how to use mdadm and LVM from the above howtos.  I glad I learned how to use them rather than just copying commands.

---

### Post by stickmangumby on 2007-12-21
Thanks a lot for the help jpkotta, that was a lot of good links!

---

