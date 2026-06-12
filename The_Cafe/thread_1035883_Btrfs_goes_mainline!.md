---
title: "Btrfs goes mainline!"
date: 2009-01-10
forum: The Cafe
---

### Post by sirdilznik on 2009-01-10
[http://www.phoronix.com/scan.php?page=news_item&px=Njk4Mw](http://www.phoronix.com/scan.php?page=news_item&px=Njk4Mw)

Great news.  Btrfs will be available in the mainline 2.6.29 kernel.  Once Jaunty comes out I'm thinking of giving this bad boy a try.  Obviously I won't be putting root or my home partition on it, but I may create a small separate partition to experiment with it.  It will probably take quite some time before this has been stabilized and tested thoroughly enough to be a default filesystem in any distro, but I still consider this a major step for this exciting file system.

---

### Post by Changturkey on 2009-01-10
> **sirdilznik said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=Njk4Mw](http://www.phoronix.com/scan.php?page=news_item&px=Njk4Mw)

Great news.  Btrfs will be available in the mainline 2.6.29 kernel.  Once Jaunty comes out I'm thinking of giving this bad boy a try.  Obviously I won't be putting root or my home partition on it, but I may create a small separate partition to experiment with it.  It will probably take quite some time before this has been stabilized and tested thoroughly enough to be a default filesystem in any distro, but I still consider this a major step for this exciting file system.

Fedora will probably have it for 12 :) (just a guess).

---

### Post by BGFG on 2009-01-10
Already!? my stint in ext4 may be a short one. If it happens at all.... Great News!

---

### Post by Slug71 on 2009-01-10
> **BGFG said:**
> Already!? my stint in ext4 may be a short one. If it happens at all.... Great News!

Im using Ext4 with Jaunty right now. Its in the installer as of a couple days ago.

I dont think we'll see Btrfs in the installer until at least 9.10KK but i could be wrong.

---

### Post by toupeiro on 2009-01-10
Are you kidding?  I'm not afraid to use it as my root FS.  Oracle is the primary sponsor of BTRFS.  If they are going to trust this FS to commercialize it in their "unbreakable linux" distribution, or trust it to run OracleRAC, I think I can trust it at home.

---

### Post by BGFG on 2009-01-10
Where does this then leave ext4 ? Since the ext4 devs themselves have described ext4 as an interim to btrfs. With a stable btrfs on tthe horizon.....

---

### Post by Tatty on 2009-01-10
I dont think this means that btrfs is anywhere near stable.

Ext4 support has been part of the linux kernel for years, listed as ext4dev, this just makes it easier for the developers to work on.

I suspect its going to be a long time before btrfs is considered stable enough for general use, which is why ext4 will be its stop-gap.

---

### Post by ghindo on 2009-01-10
What are the advantages of Btrfs, again?

---

### Post by Slug71 on 2009-01-10
> **Tatty said:**
> I dont think this means that btrfs is anywhere near stable.

Ext4 support has been part of the linux kernel for years, listed as ext4dev, this just makes it easier for the developers to work on.

I suspect its going to be a long time before btrfs is considered stable enough for general use, which is why ext4 will be its stop-gap.

Yep, its only entering the Kernel for Dev. purposes and NOT for general use yet. Probably another year for that.
There are still many features being worked on and some not even implemented yet.

So Ext4 will be around for a little while yet but wont get the life that Ext2/3 has had.

---

### Post by Slug71 on 2009-01-10
> **ghindo said:**
> What are the advantages of Btrfs, again?

C/P from Wiki:

> Btrfs is still in heavy development and many basic features are still missing. It includes, or has plans for:[9]

    * Space-efficient packing of small files and indexed directories
    * Dynamic inode allocation (no maximum number of files set at file system creation time)
    * Writable snapshots and snapshots of snapshots
    * Subvolumes (separate internal filesystem roots)
    * Object-level mirroring and striping
    * Checksums on data and metadata (for strong integrity assurance)
    * Compression
    * Copy-on-write logging for all data and metadata
    * Strong integration with device mapper for multiple device support, with several built in RAID algorithms
    * Online filesystem check and very fast offline filesystem check
    * Efficient incremental backup and file system mirroring
    * A filesystem can be upgraded from ext3fs to Btrfs
    * Solid-state drive (SSD) optimized mode (activated through mount option)
    * Online defragmentation

Although Btrfs has no native feature that would make it a distributed or networked filesystem by itself, Oracle is also implementing CRFS (Coherent Remote File System), a network filesystem protocol specifically designed and optimized for networked storage on Btrfs.

---

### Post by BGFG on 2009-01-10
I'm looking forward to either of their defrag utils and faster file access.

---

### Post by gnomeuser on 2009-01-10
> **Changturkey said:**
> Fedora will probably have it for 12 :) (just a guess).

Surely you are kidding, it will be in F11.. No kidding. Looking at the buildsystem we now have the required userspace tools, it is being build in the kernel. I would not at all be surprised if it was in F11.

I suspect it will be available the same way we had with ext4, optionally activated with big fat warnings and blinking lights. One reason to do this is that Red Hat employs a number of people who work on btrfs and this gives them a platform where they can easily test it.

---

### Post by sirdilznik on 2009-01-10
I can almost guarantee that this will be marked as "experimental" in 2.6.29 and for several releases to come.  That being said, it's still a big step and will only accelerate the stabilization and testing process.

---

