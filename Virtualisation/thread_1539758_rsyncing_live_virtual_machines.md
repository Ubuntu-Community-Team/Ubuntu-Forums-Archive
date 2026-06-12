---
title: "rsyncing live virtual machines"
date: 2010-07-26
forum: Virtualisation
---

### Post by pytheas22 on 2010-07-26
I have a virtualization environment based on libvirt and KVM, hosting about a dozen virtual machines.  The virtual disks are all in qcow, qcow2 or raw format, and range in size from 4 to 100 gigabytes.  The guests use ext3, ext4 or NTFS file systems, and the file systems that hold the virtual disks are ext3.

I'm trying to come up with a good backup solution.  The simplest approach seems to be to rsync the virtual disk images from the host machine to remote media while the virtual machines are up and running.  My concern, however, is that rsyncing a disk image while its machine is live and constantly writing data to disk seems inherently risky, because it will be impossible to get a "perfect" copy of the image.

On the other hand, I've done a lot of testing and have never had a case where a disk image backed up in this way from a running machine fails to boot or complains about file system corruption, so in practice it seems to work well.

I'm wondering, therefore, if anyone has experience doing this sort of thing in an environment similar to mine, or could offer other advice on how risky this is, either in principle or in practice.

I'd also be happy to hear any other recommendations on backup solutions for KVM-based virtual machines.  The CentOS wiki has a nice [outline]("http://wiki.centos.org/HowTos/BackupKVMGuest") that uses LVM snapshots, but unfortunately the physical disks that are hosting my virtual disk images are not LVM'd, and it would be difficult to reformat them that way because of the downtime involved.

---

### Post by TheFu on 2010-07-27
I don't use KVM. We use Xen for about 15 VMs, all Linux.  

I started out using rsync, like you, but we always shutdown the VMs to ensure consistent backups.  A backup that can't be used is just random bits, after all. Rsync became slower and slower.

If you have active, open DBMS files, you risk corruption with your backup method. Further, you are probably missing incremental backups which can be highly useful AND efficient.  If you were to perform an SQL dump to file just before performing the rsync, then you could reasonably assure that if the DBMS were corrupted, then you'd have a very recent static file ready for import that would not be corrupted. Just a thought. For other open files ... perhaps a Java session or state file that is being serialized during the rsync, you are taking your chances and have been lucky .... so far.

How do we do it? We use rdiff-backup:
a) shutdown the VMs in turn.
b) mount each virtual disk at the hostOS level - mount 
c) use rdiff-backup to perform incremental backups to another server. If a VM is 20GB, then 30 days of backups is 22GB or so. The most recent backup is a mirror.
d) startup each VM
e) Next VM

This entire process takes about 2 minutes per VM, 30 days of backups add about 10% to the total backup size.  I had issues with rsync of large files - backups were taking over 2 hrs to complete. Now they are just a few minutes per VM and the other VMs are still working.

The mount command from my script is:
   $MOUNT -t ext3 -o loop,rw "$TOP_DIR/domains/$DOMU/disk.img" "/mnt/in/$DOMU"

rdiff-backup needs RW access for some reason, even though the backup is on a different server.

rsync is great for what it does, but it isn't suitable for production backups - no incremental backups.

---

### Post by pytheas22 on 2010-07-28
Thanks for your reply.  I am increasingly thinking that I've just been lucky using rsync on the disk images.  I also notice that fsck sometimes has to recover the journal, which seems like a sure sign that the images are not getting copied cleanly.

How do you mount your disk images on the host?  I know I can do it as loopback devices using losetup, but that doesn't work with qcow images.  I can also use kvm-nbd to mount them as network block devices, which works for both qcow and raw images, but kvm-nbd seems to be buggy on Ubuntu so I'm hesitant to rely on it.  If you know of any other approaches, I'd be interested in looking into them.

Another thought is to have my script pause the virtual machines before copying their disks, then resume them.  This would at least allow rsync to work on a static, unchanging file.  It's probably not completely safe since the machines will still essentially be turned on, but it seems better than rsyncing an image while it's being written to.  I'd like to avoid turning the machines off completely each night when we do backups, because of the risk that they wouldn't start up again for whatever odd reason.

Maybe I'm being ignorant, but are there any major differences between rdiff-backup and rsync, other than rdiff-backup's incremental-snapshot feature?  In terms of bandwidth and disk-write efficiency, they should both be similar, since they both only copy the parts of files that have changed, right?

---

### Post by TheFu on 2010-07-28
> **pytheas22 said:**
> How do you mount your disk images on the host?

I included the actual mount command above. I use Xen with full img files, not KVM or QEMU stuff. I'm fairly certain you can run raw img files with KVM - I've done it.

> Maybe I'm being ignorant, but are there any major differences between rdiff-backup and rsync, other than rdiff-backup's incremental-snapshot feature?  In terms of bandwidth and disk-write efficiency, they should both be similar, since they both only copy the parts of files that have changed, right?

YES, the differences are huge! It is like comparing a PERL 15 line HTTP server to Apache. rsync is a copy between source and target. It is very efficient, but there's only 1 copy available when you're done.  

rdiff-backup has too many improvements over rsync to mention when you want to backup things.  I explained the performance improvements that we saw between rdiff-backup and rsync already.  The ability to have incremental machine backups speaks for itself. I can't imagine calling something a backup solution without incremental backups and different recovery points being available. Suppose you get hacked on Tuesday, but don't notice it until Friday. With rsync, you have no way to see anything but the latest backup for comparison which will match.  With rdiff-backup, you can ask for differences between current and any day that you took a backup. Very useful. There are too many other reasons why rdiff-backup is superior for system backups than rsync to list. You need to do some research. You will thank me later.

Don't misunderstand, rsync ROCKS, for specific purposes for which it was designed.

Don't expect to cleanly backup open files using any method. The time it breaks will be the time you need it to work.

---

### Post by pytheas22 on 2010-07-28
> I included the actual mount command above. I use Xen with full img files, not KVM or QEMU stuff. I'm fairly certain you can run raw img files with KVM - I've done it.

Ah, didn't see the -o loop.  You certainly can use img files with KVM, although most of ours are compressed, and those can't be mounted as loopback devices.

Thanks for the further information on rdiff-backup.  Our approach for backups had always been to keep seven days' worth of rsyncs so we do have increments, but that's way less efficient than rdiff-backup.  I'll probably give it serious consideration and, if it seems to work well, go with it instead of rsync.

---

### Post by TheFu on 2010-07-29
> **pytheas22 said:**
> Our approach for backups had always been to keep seven days' worth of rsyncs so we do have increments, but that's way less efficient than rdiff-backup.  I'll probably give it serious consideration and, if it seems to work well, go with it instead of rsync.

You might want to check out "duplicity" [http://duplicity.nongnu.org/](http://duplicity.nongnu.org/) as well.  It didn't do what I needed, but it may provide options that you or someone else may need.

---

### Post by pytheas22 on 2010-07-30
Ah, that looks nice, thanks.  Encryption of the backups is another concern in order to prevent unauthorized access to the data they hold, so if duplicity can encrypt the archives automatically, that's great.

---

