---
title: "Encrypting disks over 1TB not possible?"
date: 2009-04-06
forum: Server Platforms
---

### Post by serrano on 2009-04-06
Hello.
I recently installed a 1,5 TB Seagate disk and did a clean install of 8.10 x64 Server version. At installation i chose to set up the disk as LVM with encryption. All went well (except GRUB didnt want to play with MBR for some reason, LILO did) but upon checking disk space after the installation it only reported that the disk vas ~950 GB large.

After reinstallation from scratch again i chose just to set up the disk with normal partitions, upon completion all 1,5 TB was found (1.3x something usable). Also, GRUB didnt complain this time.

Is it a known problem (feature) that LVM/Encryption wont recognize disks over 1TB or am i totally lost?

---

### Post by Cybie257 on 2009-04-06
I've used EncFS and TrueCrypt with partitions over 1TB. In fact, at home, 1.2TB, and work, 4.3TB.

The problem you might come across is that it will only report 1000MB/1TB for anything bigger than, but that just seems to be a reporting problem as I have used over 2.5TB of storage on the 4.3TB EncFS volume. 

The thing I like about TrueCrypt is the ability to read it cross-platform, especially if you choose NTFS as the filesystem since windows doesn't read Ext3/4 partitions, Ext2 sometimes when the addons work. :)

-Cybie

EDIT: If you need to boot into an Encrypted disk, Truecrypt does have an option that not only allows you to boot into an encrypted drive, but also to "hide" the drive/partition until the passphrase is entered upon boot. 

[http://www.truecrypt.org/docs/?s=hidden-operating-system](http://www.truecrypt.org/docs/?s=hidden-operating-system)

---

### Post by serrano on 2009-04-06
So it's just a reporting issue?
What happens when the disk fills up all the reported space and data crosses over?

Will it just report a negative number och something?

---

### Post by Cybie257 on 2009-04-06
My assumption (as I have yet to get down below 1TB free, is that it will then begin reporting the proper Free Bytes.

I'm currenty at work now looking at the server, both remote and on-site. The remote server is reporting is showing the proper bytes free (after some updates), while the on-site server, connected via SSHFS, is reporting 0 bytes used and 1000GB/1TB free. 

I have read something within the forums on this and if I can located the thread, I will post it in here for you. 

-Cybie

---

### Post by Cybie257 on 2009-04-06
Here some information about LVM end encryption regarding 1.5TB Drives that I have found so far. 

some snippets:

> The original report (concerning the 1.5 TB disk) hits an internal
limit which is in place to avoid overflow.  Recipes in general use MB
units, and then 1000000000 (1000 TB) is a big enough maximum for the
"unlimited" partition.  But partman-auto-lvm users kB units instead,
and then the supposedly unlimited maximum size drops to 1 TB,
effectively capping the size of the root LV, and all the rest gets
used as swap, because the code avoids leaving unused physical extents
in the VG. 

> This is not the original problem (that's that the maximum automatic LV size is 1 TB in the current calculation scheme).

> 
If it isn't acceptable for Lenny, then maybe a warning should be added
that LVM (crypto) automatic partitioning does not work over 1 TB.  And
the k -> K one character change in computing the free space could be
discussed separately.  And possibly using 100%FREE instead of vg_info.

I pulled this information from the following link:

   [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=511442](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=511442)


As for what I was referring to, this is what I found as to why the server reports ok, but the onsite doesn't (using SSHFS) - Just an FYI

 In Nautilus, all folders are reported as having 1TB (1000.0 GB) free. Nice but not at the same time...

> This is normal. The underlying SFTP-protocol doesn't support reporting free space properly. 

from : 
   [http://apps.sourceforge.net/mediawiki/fuse/index.php?title=SshfsFaq](http://apps.sourceforge.net/mediawiki/fuse/index.php?title=SshfsFaq)

-Cybie

PS. May not be the exact answer(s) your are looking for but at least something to go on. Hope this helps. :)

---

