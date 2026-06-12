---
title: "Windows OS Home Folders &amp; Linux OS Home Folders"
date: 2015-03-23
forum: Windows
---

### Post by sai7 on 2015-03-23
How come Linux OS can access Windows OS home folders, but Windows OS can not access Linux OS home folders? I know that Linux OS home folders are encrypted, but isn't that the same way with Windows OS home folders?

---

### Post by deadflowr on 2015-03-23
Encryption of a folder is something entirely different than why Linux system can read Windows Files but not vice versus.
The reason is simple, Linux can read the Window Partition file system type NTFS, where as Windows cannot read the Linux Partition file system type EXT4, as well as several of the other linux file system types.
If Microsoft ever decided to add support to Windows to be able to read and access Linux file system types, then you could.

Right now, I guess, there are 3rd party tools you can use on Windows to see and read, and write(?) linux files while on Windows.
But they are not important enough for me to use or remember what they are called.

---

### Post by yancek on 2015-03-23
Developers for Linux want people to be able to read/write to windows filesystems so they have written the software to enable it.
Microsoft does not want people who use their software to be able to read/write Linux fiflesystems so they don't write software to enable it.  They certainly could.  It's a business decision, no money in it for microsoft and that's the bottom line.

---

### Post by sai7 on 2015-03-24
> **deadflowr said:**
> Encryption of a folder is something entirely different than why Linux system can read Windows Files but not vice versus.
The reason is simple, Linux can read the Window Partition file system type NTFS, where as Windows cannot read the Linux Partition file system type EXT4, as well as several of the other linux file system types.
If Microsoft ever decided to add support to Windows to be able to read and access Linux file system types, then you could.

Right now, I guess, there are 3rd party tools you can use on Windows to see and read, and write(?) linux files while on Windows.
But they are not important enough for me to use or remember what they are called.

Oh, I see. Well, the reason why I thought it might have been an encryption problem is because I'm using one of those 3rd party programs (Ext2Fsd Project) and I can access all of my Linux folders except my admin account. It had 2 files in it.

Access-Your-Private-Data.desktop
README

When I opened up README, this is what it says.

"THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private"

The problem is, I think it was unmounted because it's an encrypted folder. Otherwise, I would be able to view it like every other folder.

> **yancek said:**
> Developers for Linux want people to be able to  read/write to windows filesystems so they have written the software to  enable it.
Microsoft does not want people who use their software to be able to  read/write Linux fiflesystems so they don't write software to enable it.   They certainly could.  It's a business decision, no money in it for  microsoft and that's the bottom line.

I see, I guess that much as well. Microsoft doesn't want to give anything out if they don't get money for it. I believe that's how they also started out as a big company too. They never gave their ideas to the Linux community until late last year. They finally started letting Linux users use their .NET framework. I also bet that the .NET framework that they're letting people use is probably a small branch off the actual .NET framework and not the complete set. Probably a re-creation of it. Wouldn't know because I don't use .NET framework.

---

### Post by bcschmerker on 2015-03-24
The problem is not the encryption, but basic filesystem compatibility.  From my experience dealing with a corrupted Registry on the Asus® CM1630 in 2014, I found that Microsoft Corporation supports only the legacy FAT filesystems (inherited from MS-Disk Operating Systems 1.0 through 7.2 and non-NT Windows, including FAT32 introduced for Windows 95), New Technology File System (developed for Windows® NT), and ISO disc images natively in Windows® 6.x; don't know whether otherwise (e.g., the High Performance File System originally developed for IBM® Operating System/2) exists in Windows Server 2003 and newer.

---

### Post by deadflowr on 2015-03-24
Well, ecryptfs has/uses a kernel module, from what I can assertain.
So it makes sense it won't open in Windows, with or without a 3rd party tool to read the linux file system.

I do not know how Windows implements encryption so can't comment on that.

---

