---
title: "Ext4 is completed and for kernel 2.6.28, so says Linus."
date: 2008-11-14
forum: The Cafe
---

### Post by YaroMan86 on 2008-11-14
After such a long wait it seems that ext4 is finally been completed. I wonder if we'll get an option to install on ext4 in the next Ubuntu release because of this.

My link: [http://www.linux-magazine.com/online/news/kernel_ext_4_filesystem_moves_beyond_developer_status]("http://www.linux-magazine.com/online/news/kernel_ext_4_filesystem_moves_beyond_developer_status")

---

### Post by mssever on 2008-11-14
> **YaroMan86 said:**
> After such a long wait it seems that ext4 is finally been completed. I wonder if we'll get an option to install on ext4 in the next Ubuntu release because of this.

My link: [http://www.linux-magazine.com/online/news/kernel_ext_4_filesystem_moves_beyond_developer_status]("http://www.linux-magazine.com/online/news/kernel_ext_4_filesystem_moves_beyond_developer_status")

What's the difference between ext3 and ext4? If ext4 does get included in Jaunty, I presume it won't yet be the default. After all, filesystems need to be thoroughly debugged before becoming the default. Of course, making it an option will expand the cadre of testers.

---

### Post by samjh on 2008-11-14
Ext4: [http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)
Comparisons: [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

[quote=mssever]After all, filesystems need to be thoroughly debugged before becoming the default.[/quote]Absolutely essential.

---

### Post by Erunno on 2008-11-14
Ext4 is being regarded as an intermediate solution until btrfs become stable and to offer an upgrade path to a slightly more modern filesystem for installations which still run on ext3. Since ext4 doesn't really introduce anything new which hasn't been available for years in other filesystems (especially XFS) I'm ambivalent about this milestone.

---

### Post by bash on 2008-11-14
> **Erunno said:**
> Ext4 is being regarded as an intermediate solution until btrfs become stable and to offer an upgrade path to a slightly more modern filesystem for installations which still run on ext3. Since ext4 doesn't really introduce anything new which hasn't been available for years in other filesystems (especially XFS) I'm ambivalent about this milestone.

You have a link to a source for that? AFAIK a lot of Kernel devs are curious and interested about Btrfs, but so far I haven't read anywhere that it is set to become the next default filesystem (after ext4).

---

### Post by Changturkey on 2008-11-14
Now for GRUB2.

---

### Post by Erunno on 2008-11-14
> **bash said:**
> You have a link to a source for that?

Sure. [1][2]

I can't connect to the second site currently though, maybe it will come up again later. The mail was written by Theodore Ts'o of ext4 fame himself. Here's the gist of the mail:

> At the end of the that workshop, there was unaminous agreement (including from yours truly) that (a) Linux needed a next generation filesystem to be competitive, (b) Chris Mason's btrfs (with some changes/enhancements discussed during the workshop) was the best long-term solution for NGFS, and (c) because creating a new enterprise filesystem always takes longer than people expect, and even then, it takes a while for enterprise users to trust a new filesystem for their most critical data, ext4 in the next generation of filesystems was needed as the bridge to the NGFS.

[1] [http://www.heise.de/open/Kernel-Log-Dateisystem-Ext4-verlaesst-Entwicklungsphase-ein-Zwischenstopp-auf-dem-Weg-zu-btrfs--/news/meldung/117415]("http://www.heise.de/open/Kernel-Log-Dateisystem-Ext4-verlaesst-Entwicklungsphase-ein-Zwischenstopp-auf-dem-Weg-zu-btrfs--/news/meldung/117415") (German)
[2] [http://thread.gmane.org/gmane.linux.file-systems/26246/focus=26492]("http://thread.gmane.org/gmane.linux.file-systems/26246/focus=26492")

---

### Post by bash on 2008-11-14
> **Erunno said:**
> Sure. [1][2]

I can't connect to the second site currently though, maybe it will come up again later. The mail was written by Theodore Ts'o of ext4 fame himself. Here's the gist of the mail:



[1] [http://www.heise.de/open/Kernel-Log-Dateisystem-Ext4-verlaesst-Entwicklungsphase-ein-Zwischenstopp-auf-dem-Weg-zu-btrfs--/news/meldung/117415]("http://www.heise.de/open/Kernel-Log-Dateisystem-Ext4-verlaesst-Entwicklungsphase-ein-Zwischenstopp-auf-dem-Weg-zu-btrfs--/news/meldung/117415") (German)
[2] [http://thread.gmane.org/gmane.linux.file-systems/26246/focus=26492]("http://thread.gmane.org/gmane.linux.file-systems/26246/focus=26492")

Cool. Thanks for the links. Didn't know that. I should read the Heise Kernel log more often, but I keep forgetting it. Good to hear that they are in favor of including something like btrfs as default in the long run. I'm all in favor of that. Just thought that weren't such plans yet.

---

### Post by Grant A. on 2008-11-14
> **Erunno said:**
> Since ext4 doesn't really introduce anything new which hasn't been available for years in other filesystems (especially XFS) I'm ambivalent about this milestone.

XFS can't be shrunk.

---

### Post by Polygon on 2008-11-14
and xfs can't be used in the linux kernel without using FUSE so...we are kinda out of luck for the moment.

---

### Post by Erunno on 2008-11-14
> **Polygon said:**
> and xfs can't be used in the linux kernel without using FUSE so...we are kinda out of luck for the moment.

You're confusing XFS with ZFS.

---

### Post by Polygon on 2008-11-14
yeah, my bad. silly filesystems that are just <letter>FS.

---

### Post by ericesque on 2008-11-14
ext4 looks pretty lack luster for the desktop user.

I am in no way hindered by ext3's 32000 subdirectory limit.
Nor have I ever desired to create a single 2TB file-- although
I can see some crazy media hoarders wanting to backup and
possibly hitting that one... but if they just stopped stealing,
their FS wouldn't cause them grief!

---

### Post by ghindo on 2008-11-14
Hasn't there been the option to install Ubuntu with Ext4 for a while now?

---

### Post by Polygon on 2008-11-14
> **ericesque said:**
> ext4 looks pretty lack luster for the desktop user.

I am in no way hindered by ext3's 32000 subdirectory limit.
Nor have I ever desired to create a single 2TB file-- although
I can see some crazy media hoarders wanting to backup and
possibly hitting that one... but if they just stopped stealing,
their FS wouldn't cause them grief!

supposedly the drive check every 30 mounts is a lot faster with ext4 cause of some cool technical reason, which is good for the average user so they don't have to wait as long

---

### Post by SunnyRabbiera on 2008-11-14
Well I kind of look forward to ext4.
ext3 has done me a great service since I started using linux and I like to see if ext4 can pick up where it left off.

---

### Post by perlluver on 2008-11-14
Wasn't a Defragmenter supposed to be added to ext4, or in the ext4 tools.  Thought I read that somewhere.

---

### Post by david_lynch on 2008-11-15
> **Polygon said:**
> and xfs can't be used in the linux kernel without using FUSE so...we are kinda out of luck for the moment.
Huh? xfs was ported from SGI years ago. No fuse needed, ever....

---

### Post by SunnyRabbiera on 2008-11-15
> **perlluver said:**
> Wasn't a Defragmenter supposed to be added to ext4, or in the ext4 tools.  Thought I read that somewhere.

yes there will be a online defragmentaion tool

---

### Post by kevin11951 on 2008-11-15
> **SunnyRabbiera said:**
> yes there will be a online defragmentaion tool

your joking right? 2 things that scare me:

1.  Online!? As in a program running on the Internet that can access my hdd like that?!

2.  Why do we need a defragmentor?

---

### Post by mevem on 2008-11-15
> **kevin11951 said:**
> 1.  Online!? As in a program running on the Internet that can access my hdd like that?!No, it means the filesystem can be online/mounted/up and running while defragmenting.

> **kevin11951 said:**
> 2.  Why do we need a defragmentor?Every filesystem gets fragmented, only not as much as FAT or earlier NTFS-versions. This is a problem, at least on storage devices with relatively slow random access.

---

### Post by insane_alien on 2008-11-15
> **kevin11951 said:**
> your joking right? 2 things that scare me:

1.  Online!? As in a program running on the Internet that can access my hdd like that?!

not refferring to internet access(although in theory you could set up an SSH connection and tell your computer to defragment your drive while you are away. just means that the filesystem can be in use and still be defragmented. an offline defragmenter would require the filesystem to be unmounted before any defragmentation could take place.

> 
2.  Why do we need a defragmentor?

it would be foolish and idiotic to claim that filesystems never get fragmented. while linux file systems are generally very very good at keeping a low level of fragmentation, once you get up past 85-90% usage fragmentation can become a serious issue.

ext4 has features which make you less likely to need to defragment but it will also include a defragmenter for those extreme cases where you do.

---

### Post by JNelson on 2008-11-15
Ext3 can get fragmented even with 1/3 of the drive in use. Read this

[http://www.heise-online.co.uk/open/Tuning-the-Linux-file-system-Ext3--/features/110398/3](http://www.heise-online.co.uk/open/Tuning-the-Linux-file-system-Ext3--/features/110398/3)

> The battle against fragmentation also interferes with another optimising strategy: The locality of data and metadata which block groups try to achieve. Since Ext3 tries to store the files within one directory within the same block group, fragmentation can occur even though a lot of contiguous free space may still be available on the disk. The claim that Ext3 only starts to fragment when the file system is filled up to 80 or 90 percent is not always true. Depending on usage patterns, a file system which still has ample space available may still get fragmented.

---

