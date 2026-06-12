---
title: "what file system for external hard drives used in cross-platform environments?"
date: 2007-09-13
forum: The Cafe
---

### Post by xiota on 2007-09-13
What file systems do you use on your external hard drives when cross-platform compatibility is a concern?

Please describe how you cope with the limitations of the file systems when working on different platforms.

FAT32 has file size limits.  There are no full-featured fsck-like tools in GNU/Linux for NTFS.  Windows does not natively support ext-n.  Etc.

Users of HFS+, please describe your experiences.  All of my experiences with that file system resulted in data loss (probably due to improper unmounting on OSX; some new Mac users find dragging hard drives with lots of their important data to the trash highly unintuitive).

---

### Post by igknighted on 2007-09-13
FAT32/VFAT corrupts too easily.  Since there is no journal, unplugging your removable drive without properly unmounting can lead to data corruption (and lets be honest, we all do this).  Also, I store all my linux iso's on my external (and that includes DVD images too large for FAT32's 4gb file size limit).

Ext3 is probably the best file system of the bunch, however it is really only a viable option if you plan on using this drive on just a select group of windows machines.  If you have access to these machines to ensure that the proper file system drivers are installed, its a great option.  Otherwise, you might end up somewhere without that driver and no way to access your drive.

NTFS is a pretty god file system (though not as good as ext3 IMHO).  It does seem to fragment worse than ext3.  If you need guaranteed ability to read your drive without drivers, this is the way to go.  If you use other linux machines that you do not have control of (like at a university comp lab lets say) then you might not have write abality unless they have installed the proper drivers.

There is no perfect solution.  Maybe the answer is to pick primarily ntfs (at least linux can read it no matter what), but make a little ext3 partition for the occaision when you are at a linux box that cannot write to ntfs, then merge the files later.

---

### Post by nowshining on 2007-09-13
igknighted nicely said. :)

---

### Post by arbulus on 2007-09-13
I think it depends on how you are going to use the drive.  Is it going to be plugged into a central machine and accessed by Samba/NFS?  Or is it going to be unplugged and plugged directly into different machines with different platforms?

If it is going to be shared from a central location, i would use ext3.  There's no real reason not to. Especially if it's going to be plugged into a Linux box. Samba can share the drive with no problems to Windows and Mac. Plus it's journaled and you don't really have to worry about fragmentation. 

If you are going to be just plugging it back and forth directly into different machines, I really don't know what would be best.  Macs cannot read ext3, but as far as I know, everyone can read NTFS and FAT32 pretty well, though I really wouldn't use FAT32 because of it's lack of journaling and it's fragmentation problems. I think Macs need a third party driver to be able to write to NTFS, though. So I really don't know on that one.

As for the unmount thing on the Mac:  you can just drag the icon to the trash to unmount the volume, or you can right click/Ctrl+click on the volume and hit "Eject."  I actually have several Macs and I've never had a problem with HFS+.  It seems like a pretty sound filesystem and doesn't take up much space on the disk.  That's one difference between it and ext3.  I notice that when I plug an empty drive in and format it ext3, a 500 GB drive will only have 475 GB available. HFS+ would leave somewhere between 490 and 495 GB available.  It actually really bothers me that I loose 25 GB to the filesystem itself.

---

### Post by devilmyarse on 2007-09-13
NTFS writing is possible in Mac but it's major PITA (and very archaic. Mounting and unmounting is done in terminal) You have to unmount the drive once you've plugged it in. (or if it's on a boot camp partition for windows it's auto mounted at startup) and then remount it for ntfs write, and then it's highly advised to unmount and then remount as read only! 

The only time i ever use this method is if i need to transfer a dvd9 iso to windows (so i can mount rather than burn)

[macFUSE](http://code.google.com/p/macfuse/) once it has been installed and configured properly can enable ntfs-write functionality

Obviously with mac it's a synch to automate the unmount-remount-unmount process. But still quite annoying.

---

### Post by LowSky on 2007-09-13
I was think of formatting my next external Hard drive in ext3, but make a really small partion on it that is NTFS or FAT32 with the windows ext3 driver on it... this way I get to use it anywhere

---

### Post by xiota on 2007-09-13
The theoretical maximum free space on a "500GB" drive using 1024 as a base is about 465GB.  If Macs report 490+ GB available, they are probably calculating based on 1000 rather than 1024.  If I were trying to be clever, I would base file system calculations on 1000 for native file systems and 1024 for others.  I wouldn't be surprised if Apple were doing that with HFS+ to make its filesystem look better.  MS probably doesn't do it with NTFS because Windows doesn't normally support non-MS file systems.

I guess FAT32 is far from dying, even though ntfs-3g is coming along nicely and MS may be trying to kill off FAT with its new exFAT.  Even the name of the new filesystem is indicative of divorce.  I'm more bothered by the 4GB file size limit than lack of journaling.

I'm somewhat surprised that ext2 seems dead.  I wonder how many people are using their ext3 partitions with one of the ext2 IFS drivers for Windows. I've had an ext2 IFS driver corrupt an ext3 partition, so I don't feel safe using that combination anymore.

I forgot about accessing files over a network, even though I do it often.  Since relatively few people marked ext3, this method of access is probably not that common or also "forgotten" among those who have thus far responded to the poll.

I'm also interested in how people feel about being tied to particular platforms for file system maintenance.  How does the annoyance of having to find a Windows system to check an NTFS partition affect people's choices?  Do similar limitations with HFS+ reduce the use of that file system as well?

---

### Post by brandonjp on 2007-09-16
been using two drives - one NTFS and one ext3 - I've had so many more problems with the NTFS drive, even in Windows --  but from Windows I've had GREAT luck reading/writing to the ext3 drive using the ext2 IFS driver at [www.fs-driver.org](www.fs-driver.org) - that driver has really made the difference to where ext3 is my main cross-plat drive

---

### Post by brandonjp on 2007-09-16
> **LowSky said:**
> I was think of formatting my next external Hard drive in ext3, but make a really small partion on it that is NTFS or FAT32 with the windows ext3 driver on it... this way I get to use it anywhere
great idea, by the way!
--bp

---

### Post by Biochem on 2007-09-16
> **LowSky said:**
> I was think of formatting my next external Hard drive in ext3, but make a really small partion on it that is NTFS or FAT32 with the windows ext3 driver on it... this way I get to use it anywhere

That is a good idea until you stumble upon a computer where you don't have admin privilege, like Universities comp lab)

For roaming external NTFS is probably the most "universal" as in you will probably always be able to find windows somewhere.

---

### Post by lisati on 2007-09-16
I have NTFS on my external drives because (a) I use them mainly with Windows, and (b) FAT32 can't handle some of the larger video files on my systems

---

### Post by angryfirelord on 2007-09-16
If you want a filesystem that you can use on any machine with any OS without installing anything, you'll have to stick with ye olde' FAT32.

---

### Post by Dimitriid on 2007-09-16
Make it ext3 but have grub/lilo and puppy loaded on it, in the event you need to access your files on a windows only machine ( also takes care of most "no admin access" environments: almost none of them password lock the BIOS ).

---

### Post by brandonjp on 2007-09-17
sounds like we need a standalone "portable" version of a ext drive viewer - i remember one i used to use like that for HFS+ external drives - HFS Explorer or something

---

