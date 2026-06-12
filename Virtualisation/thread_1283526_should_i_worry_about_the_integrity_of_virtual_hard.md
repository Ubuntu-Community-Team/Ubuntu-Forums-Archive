---
title: "should i worry about the integrity of virtual hard disks"
date: 2009-10-05
forum: Virtualisation
---

### Post by washable mist on 2009-10-05
hey guys

i am looking to replace my current file server with something newer, i am looking to replace the current pentium 4 2.4ghz,512mb system with a newer 2.8ghz dual core with 4gb of ram.

i currently use a windows OS but i was thinking of using ubuntu with either a linux or windows file server inside a VM. i will also want to use a second VM for a Hoast for local counter strike games.

but because i will be storing lots of data (nearly 1TB) on the drive, so i was wondering about how people think the virtual hard disk will cope with this?

---

### Post by smc18 on 2009-10-07
Im curious to what anyone else says too.  I've read that you wouldn't normally virtualize a file server.

I have physical Ubuntu Server running on a either a 2.4 or 2.8 GHz P4 with 1GB of RAM and I'm more than happy with it. It's using mdadm for my RAID 1, and running Samba as my File Server.

I JUST setup a xenserver hypervisor with some vms running on it and I don't feel comfortable enough to know the proper ways to manage it. Hence why I'm learning :)

---

### Post by maxxjr on 2009-10-08
> **washable mist said:**
> hey guys

i am looking to replace my current file server with something newer, i am looking to replace the current pentium 4 2.4ghz,512mb system with a newer 2.8ghz dual core with 4gb of ram.

i currently use a windows OS but i was thinking of using ubuntu with either a linux or windows file server inside a VM. i will also want to use a second VM for a Hoast for local counter strike games.

but because i will be storing lots of data (nearly 1TB) on the drive, so i was wondering about how people think the virtual hard disk will cope with this?

Just to note it, I use my Host OS as file server for both Guest OS and real PC's on the network.  This way, I can keep the virtual machines smaller since all they need is space for OS and applications.  Performance will be better for file serving from the Host OS, if this is a consideration for you.  When I do backups on the Host OS, I backup both the shared files and the VM files.

Also, have you tried your game on a VM yet?  I have no experience with the game you are looking at, but if it is at all graphics intensive, you will have significant performance constraints running it in a VM.

---

### Post by __p1n__ on 2009-10-08
A physical volume is just like raw disk except that it has some metadata at the beginning.  You can format any logical volumes inside the volume group based on the thing with any filesystem that you like.

A big benefit to LVM though is that you can implement raid 1 with it across partitions and/or physical drives and that will improve integrity.

On the last machine that I built for myself I used 2 1-TB drives in a physical RAID-1 configuration.  The netbsd/xen dom0 uses the first physical partition on the mirrored disk set and the second partition is configured as a physical volume that hosts the the volume group and LVM's.  Each domU is based upon an LVM image within that vg.  I'm not using any redundancy at the LVM level because physical mirroring is happening transparently under it all.

---

### Post by dcstar on 2009-10-10
> **smc18 said:**
> Im curious to what anyone else says too.  I've read that you wouldn't normally virtualize a file server.


Virtual drives use the underlying host resources and will add extra overhead to any file I/O, so you **may** not want to use a fileserver VM for performance reasons, but nothing else.

I actually put my VM drives on separate high-performance Linux filesystems more suited to the large file sizes that VMs have. Reiserfs works better than EXT3 in my experience, and people have used XFS as well.

---

