---
title: "Migrating LUKS partitions between devices"
date: 2013-08-29
forum: Security
---

### Post by CallMeDave on 2013-08-29
Well, I've been tackling this for a while and now I officially accept that I just don't know enough to make this work on my own.  So here's my problem:

I have a bootable USB drive with Ubuntu Desktop on it, and created it during the initial installation (using the alternative install ISO) to use a LUKS encrypted partition.  It has worked great, and I have no complaints.

Lately, though, I've decided I wanted to move up to a stronger key - 512 instead of 256.  I thought that the easiest way to do this would be to use fdisk to create the same partition structure on a brand new USB drive, use cryptsetup to create the encrypted partition, then simply copy all the files off the original USB drive to the respective counter-parts on the new USB drive.

I updated /etc/fstab and /etc/crypttab to point to the new UUIDs, then ran update-initramfs -u and update-grub so it would boot the device with the correct target UUIDs.

But no.  My "this should be simple" assumption was way, way off.  It isn't working.

GRUB works just fine.  When I choose the OS from the menu, the Ubuntu splash screen loads, so I believe it is seeing the boot partition (/dev/sda1) just fine.  However, unlike the original USB drive, it doesn't prompt me for a password.  Actually, it simply does nothing before eventually dropping to initramfs.

I'm interpreting this behavior as meaning that the problem is the encrypted partition simply cannot be found.  However, I have nothing to base this on other than what I've mentioned above.

Thank you, everyone.

---

### Post by TheFu on 2013-08-29
* Backup the files to unencrypted storage.
* Create a new install with or without encryption as you like.
* Restore the backup files to the new install.

When I have encrypted stuff, I'm religious about backups.  **Got backup religion?**

---

### Post by CallMeDave on 2013-08-29
Yes I have backups of important files, however there are also various programs and configurations that I'd like to retain.  Despite the time it has taken, struggling to get this to work, it would still take longer - and even be more frustrating - attempting to reinstate all this from scratch.

So the original question about a full system copy from the original USB drive to the second USB drive, and tweaking it to boot properly, remains.

---

### Post by TheFu on 2013-08-29
> **CallMeDave said:**
> Yes I have backups of important files, however there are also various programs and configurations that I'd like to retain.  Despite the time it has taken, struggling to get this to work, it would still take longer - and even be more frustrating - attempting to reinstate all this from scratch.

So the original question about a full system copy from the original USB drive to the second USB drive, and tweaking it to boot properly, remains.

There is a huge difference between 
* "backups of important files"
and
* system backups with settings, lists of packages, important files, 
* full system backups.

Time to get backup religion. My signature has links for that. These days with linux, it really is pretty easy to migrate systems around with just a tiny bit of effort to understand backups, restores, and booting. It is just a little too complex to put in a reply, hence the links.

BTW, I do not do full system backups. I backup settings, data, configuration, and lists of installed packages only. For me, it means I need to install a fresh OS **before** restoring the data, settings, followed by the packages in the list ... it reduces all backups by about 2G-4G in size, since the core OS and anything installed using normal repositories are easily restored.  

These commands are the key:
```
$ dpkg --get-selections
$ dpkg --set-selections
```
to saving a list of installed packages, then adding them back into APT for later restoration.  Data and setting backups are handled by any normal backup tool - tar, rsync, back-in-time, dejaDup, duplicity, duplicati, rdiff-backup, rbackup, rsnapshot, ... there must be over 100+ options.  If you are running a DBMS, be certain to either export that data or shutdown the DBMS to avoid data corruption.

Sadly for non-technical people, this is not an automatic process and I don't know of any tool that will do it as efficiently.

For the non-tech people, using a disk-cloning tool is probably the best option: ** Clonezilla or Partimage** - even those tools need some manual tweaks for UUIDs and network devices if the OS is recovered to a new system.

Anyway, for this problem, split it up into the encryption aspect and the backup/restore aspect is how I'd attack it. Whenever encryption is used, having excellent backups that can be restored is mandatory.  > Backup Religion can save you, it can.  my best Yoda voice. ;)

---

