---
title: "Help me remove a software raid partition"
date: 2006-08-19
forum: Server Platforms
---

### Post by ethridgt on 2006-08-19
I have three drives.  One 80 GB drive and two 250 GB drives.  I had my root and swap partition on the 80 GB drive and I ran raid 1 on the two 250 GB drives.

So I've failed both drives (using mdadm) and removed them from md0.  I manually stopped mdadm and mounted one of the drives.  I put my data on it to backup and then I reinstalled ubuntu server.  I reformatted swap, the 80 GB drive and the other 250 GB drive.  The install went fine.  However, when rebooting, I saw a message that md0 was started with one drive.  I'm stumped by this.

What I want is:

80 GB drive:
/
swap

250 GB drive 1:
/vol1

250 GB drive 2:
/vol2

If I manually stop md0 using mdadm after restarting, I can manually mount drive 2 to /vol2.  If I don't stop md0, then drive 2 complains about being in use. Can somebody tell how to remove all traces of the old software raid?

-- tale

---

### Post by tonym on 2006-08-21
When you want to take a partition out of the array use mdadm --zero-superblock after removing it.

Also,  check in cfdisk that the partition type isn't 'fd'.  if it is change it.

---

