---
title: "VMWare + WinXPPro killing my harddrive"
date: 2008-07-08
forum: Virtualisation
---

### Post by chadjohnson on 2008-07-08
Whenever I have Windows XP Pro loaded in VMWare Server, my harddrive is constantly being accessed. The VM's memory usage is well under 100MB, and it has 512MB to work with. This doesn't happen with System Rescue CD (i.e. the Linux live CD) booted.

I have the host settings set to "Allow some virtual memory to be swapped." I tried "Fit all virtual machine memory into reserved host RAM," and my harddrive is STILL constantly being accessed. I also have it not creating snapshots in the background.

The host machine has 2GB RAM and a 6000+ (3GHz) processor.

What the heck is going on?

---

### Post by fjgaude on 2008-07-08
VMware could be defragging the partition (consolidating disks) used for Appliances, that you specified when you created a VM or more.

---

### Post by chadjohnson on 2008-07-08
That could be possible. Where would I check the settings for this?

*EDIT* Ah, nevermind. Why do I always post before I search myself? Found it. I'll defragment manually and see what happens.

---

### Post by chadjohnson on 2008-07-08
Thanks, but no cigar. It's still accessing the harddrive frequently after defragmentation.

---

### Post by fjgaude on 2008-07-08
Okay, the only thing I would suggest is to take a snapshot under the LM menu and notice what happens with the drive activity.

Is the drive you are talking about the same drive that the host OS is on?

---

### Post by chadjohnson on 2008-07-09
Ah, that could be one factor in the activity increase: it's running two operating systems at once. The vm disk image is on the same physical drive as the host OS, but it's on a separate partition.

Snapshotting did make the drive activity go up quite a lot.

---

### Post by fjgaude on 2008-07-09
Now, revert to the Snapshot and see how that is.

How many people are using your system at once?

---

