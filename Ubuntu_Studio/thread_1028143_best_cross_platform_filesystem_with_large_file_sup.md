---
title: "best cross platform filesystem with large file support?"
date: 2009-01-02
forum: Ubuntu Studio
---

### Post by dodonpalex on 2009-01-02
I'm going to use an external usb drive for media files with the main task of editing in cinelerra. Since the media is going to be quite large (4GB+) I need to use a filesystem with large file support.

Here is the thing though: I would like to plug the external drive into a windows/osx machine for additional editing if the need arises.

For my usage FAT32 wont do because of the file size limitation. It seems as if my only option for keeping it usable with a windows system would be to use NTFS but the last I read of it the support in Linux was kinda iffy and I have no clue how well it works with OSX. Any tips for other solutions when it comes to the filesystem?

---

### Post by kidders on 2009-01-03
Hi there,

HFS+ may be the one to go for. OS X and Linux support it natively, and there are third party libraries available for Windows.

---

### Post by kayosiii on 2009-01-03
Ext2 is the best option I have found....

NTFS is well supported by Windows and Linux but and there are Mac Drivers (using fuse) - but are incredibly slow on mac.

HFS+ is supported well on Mac and Linux (need to apt-get extra component) - windows drivers are available but cost quite a bit of money.

EXT2/EXT3 - is well supported by Linux - there are third party drivers for EXT2 for both Windows and Mac - Ext3 filesystems generally can be mounted as EXT2.

---

### Post by TechZilla on 2010-12-18
I know this thread is a bit dated, but running into this problem again and again.  Yes NTFS-3G is great but the performance of FUSE is just not the same as Kernel.

is use ext4 for linux system
and ext2 for archiving files.  ext3 support on other OS is not perfect and a native ext2 partition works better with the current driver situation.  plus i dont see the nessecity of journaling on an archive? system partition defently.  just my 2 cents

---

### Post by wkulecz on 2010-12-20
I've a Viewsonic VMP-70 media player box, and use a USB 2TB NTFS formated drive with it.  I have no issues moving media files back and forth from Windows7 (where I create most of them) to my archive on Ubuntu via the USB drive.  Or going the other way when I rip a DVD on Ubuntu to place on the VMP-70 player.

So far for me the NTFS support in Ubuntu has been 100% perfect.

---

