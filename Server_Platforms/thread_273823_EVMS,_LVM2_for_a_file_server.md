---
title: "EVMS, LVM2 for a file server"
date: 2006-10-08
forum: Server Platforms
---

### Post by deviantintegral on 2006-10-08
I am looking into the possibility of setting up a storage system for use by around 200-300 users (and growing!). I have experience with setting up all file systems to work under Gentoo with evms. I mainly want some kind of volume management so drives can be added or removed from a RAID 5 setup.

From what I understand, Ubuntu only supports LVM during installation, and that to use EVMS I have to install first and *not* use evms on the root partition. What are the differences between an LVM and an EVMS setup - will I lose anything by going with the LVM setup during install? Or is there a way to set up EVMS the way I want?

Thanks,
--Andrew

---

### Post by jaddison on 2007-05-30
I too would be interested in a response to this... I know it's been some time since this was originally posted, but I find myself very interested in learning more about EVMS.  I have read the user guide on sourceforge, but I would like to hear some practical, anecdotal situations depicting its use.

Any takers on this?

Thanks,
J

---

### Post by deviantintegral on 2007-05-30
Well, how things have progressed since I posted this topic!

After having major issues with Gentoo kernels, I transitioned my EVMS system to Ubuntu 6.10. Including the root partition! I did it by:


[LIST][*]Booting up with the regular Live CD installer[*]Using apt-get to install evms[*]Mounting the existing volumes, or for most people use evmsn or evms-gui to create them[*]Install a base system using 'debootstrap', pointed at Ubuntu repositories[*]chroot to the new system, install evms in the chroot and configure as needed
[/LIST]

This worked **great** for a few months, but I'm currently in the process of converting my system to straight LVM. Why?

[LIST][*]The evms scripts in the initramfs image sometimes conflicted with lvm and mdraid, making the system unbootable until I manually disabled the scripts[*]The evms GUI often wouldn't let me do simple operations that should have been possible and were documented elsewhere as possible. Namely, expanding a RAID5 set (my original reason for evms) would cause the system to run out of RAM (1 gig, expanding array by a 250 gig drive)[*]Last week, after a normal shutdown, evms decided that my mdraid superblocks were corrupted somehow. On manual inspection, they are fine, and if I mount everything manually using mdraid and lvm or the resuce mode, it works fine, and all my data is intact.[*]In general, it seems as if the "evms community" is pretty dead. LVM has much more documentation, and now that mdraid can expand a RAID5 set, I don't have a use for evms.
[/LIST]

I think the biggest kicker for me was when I was trying to determine why my RAID5 expand was consuming so much memory. Figuring I could just buy more RAM, I spent quite a few hours on google, forums, and IRC trying to get an answer as to how much RAM is required. The best I got was "RAID5 expands use a lot of memory". Bleh.

I'm hoping my experiences with LVM are much better. The server is currently backing up files to new drives, so I'll be able to post soon about the differences.

---

### Post by Brazen on 2007-05-30
evms is just a bunch of tools for working with volumes and file systems.  It can work with LVM for the volumes and Ext3, XFS, etc for the file systems.  It's just a frontend.  Even your Gentoo box should be using LVM for the underlying volume structure.  EVMS just sorta of blurs the line between working directly with partitions and volumes.

Maybe this snip from wikipedia explains it better:
> For a while, both LVM and EVMS were competing for inclusion in the mainline kernel. EVMS had more features and better userland tools, but the internals of LVM were more attractive to kernel developers, so in the end LVM won the battle for inclusion. In response, the EVMS team decided to concentrate on porting the EVMS userland tools to work with the LVM kernelspace. [http://lwn.net/Articles/14816/](http://lwn.net/Articles/14816/)

Personally, I never cared for it.  I prefer working directly with the LVM and file system tools.

---

### Post by jaddison on 2007-05-30
Interesting feedback, guys.

I was hoping that EVMS is the enterprise solution I was looking for, but it's looking like that might not be the case.  I am sure that I'll have more questions on this topic.

I haven't given up on EVMS yet, however.  I'll keep asking for feedback from others - maybe we'll all learn something new about EVMS!

**On that note, Ubuntu community, any EVMS experiences to share?**

Thanks,

---

