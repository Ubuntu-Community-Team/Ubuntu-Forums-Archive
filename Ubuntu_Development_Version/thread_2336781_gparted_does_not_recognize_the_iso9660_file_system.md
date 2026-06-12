---
title: "gparted does not recognize the iso9660 file system in cloned Ubuntu USB boot drives"
date: 2016-09-11
forum: Ubuntu Development Version
---

### Post by sudodus on 2016-09-11
I created the bug report [#1622313, "gparted does not recognize the iso9660 file system in cloned Ubuntu USB boot drives"](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/1622313) from Xenial daily 'looking at' its own iso file as cloned, running a live system from the ***current daily Lubuntu Xenial desktop i386*** iso file.

Please mark 'affects me too', if it affects you and help add some heat to the bug report :-P It would be valuable to check in other versions of Ubuntu, particularly in Trusty alias 14.04.x LTS, because many people will install fresh Xenial systems from old Trusty systems.

I think many of us have seen this bug in gparted, but we have not reacted until now. A user at the Lubuntu mailing lists starting complaining about it, and put the blame on the new ***Ubuntu Startup Disk Creator*** alias ***usb-creator-gtk*** version 0.3.2 and 0.3.3 in Xenial.

But the Ubuntu Startup Disk Creator is only cloning the iso files, and they are hybrid iso files, made to boot from both DVD and USB drives. So the bug is in gparted, that cannot see the iso9660 file system, when in a USB pendrive.

After some additional testing, I found that the bug is worse in the 64-bit 16.04.1 LTS, and much worse in the 64-bit 14.04.1 LTS, as illlustrated by the following screenshots. This behaviour will really confuse new users of Ubuntu and the Ubuntu flavours.

-o-

Edit: The uploader has changed. Previously it was possible to upload big pictures, and the resolution (pixel) was decreased automatically to keep them within whatever was allowed. Now there is hard limit at 1024x768. So I cropped the pictures to keep the important information, and after that decreased the resolution to so that the width was 1024 pixel. Then I managed to upload the screenshots. Here they are :-)

---

### Post by oldfred on 2016-09-11
If you delete the backup gpt table does gparted then work?
This is from the dd/hybrid DVD/flash drive image? That only overwrites the beginning of drive.

Seen many issues where Windows converts a gpt drive to MBR with a BIOS install and leaves backup gpt table. All partition tools then fail and fixparts seems to be the only tool that works to remove backup gpt table.
When both MBR & gpt are seen, it parted/gparted partition tools do not know what you want and assume you want to erase & start over. gdisk seems to work, not sure about new fdisk in 16.04. Older fdisk did not work with gpt at all.

---

### Post by sudodus on 2016-09-11
I checked the pendrive with ***xxd***, and there is no GPT backup table at the end, nothing but 'zeros'. So this bug is provoked by the structure, that comes from the iso file, not by any cruft behind the region used by the iso 9660 file system.

---

### Post by mc4man on 2016-09-11
> **sudodus said:**
> 

-o-

Edit: The uploader has changed. Previously it was possible to upload big pictures, and the resolution (pixel) was decreased automatically to keep them within whatever was allowed. Now there is hard limit at 1024x768. 
I don't think there is a hard limit, just inconsistent performance from forum, I've had tiny pics rejected. So for instance attached here is  uploaded as 1628x912

---

### Post by sudodus on 2016-09-11
Hi mc4man,

I see. Maybe there was a bug at that particular instance, that made up the limit.

The reason I wrote 1024x768 was because I was told by the error message when I tried with a screendump file from a typical wide-screen laptop. And it worked after a reduced the width to exactly 1024 pixel.

-o-

By the way, what do you think of the main subject of this thread, that gparted does not recognize [the partition table and] iso 9660 file system of USB drives?

---

### Post by mc4man on 2016-09-11
> **sudodus said:**
> Hi mc4man,

I see. Maybe there was a bug at that particular instance, that made up the limit.

The reason I wrote 1024x768 was because I was told by the error message when I tried with a screendump file from a typical wide-screen laptop. And it worked after a reduced the width to exactly 1024 pixel.

-o-

By the way, what do you think of the main subject of this thread, that gparted does not recognize [the partition table and] iso 9660 file system of USB drives?i'll have to try one of those sdc creations later when I return home, been using unetbootin since 16.04.

(- That forum error message is generic catch-all.  I've gotten it when trying to attach a .txt & .gz files...

---

### Post by mc4man on 2016-09-12
So tried setting a sdc disk back to a usb storage device again.
Don't see where anything has changed. 

gparted certainly has issues, maybe they'll fix upstream though with some persistence & correct choices it can currently do the job.
(- plus even if fixed it may never be upgraded in 16.04

disks remain totally incapable of doing anything with these devices.
No info is provided to the user on how to return to a storage device.
sdc & disks are on the default install, gparted isn't so  Ubuntu continues to be  deficient here

---

### Post by mc4man on 2016-09-12
What's semi interesting is in 14.04 i use gnome-disk-utility 3.0.2-2ubuntu8 (the older one
It has no problems creating a FAT32 usb device from a sdc device (simply pick "Format Drive" button & format to master boot record, then create partition of choice

---

### Post by sudodus on 2016-09-12
> **mc4man said:**
> So tried setting a sdc disk back to a usb storage device again.
Don't see where anything has changed. 

The only things changed from version 0.3.2 to 0.3.3 of the SDC are that the option **--version** and **man usb-creator-gtk** give the correct information about the version. It helps, but I know it is not enough to make you happy ;-)
> 
gparted certainly has issues, maybe they'll fix upstream though with some persistence & correct choices it can currently do the job.
(- plus even if fixed it may never be upgraded in 16.04

Yes I hope so, the bug is pushed upstream by Alberto Salvia-Novella :-)
> 
disks remain totally incapable of doing anything with these devices.
No info is provided to the user on how to return to a storage device.
sdc & disks are on the default install, gparted isn't so  Ubuntu continues to be  deficient here

mkusb (if you want a GUI) and mkusb-nox (if you want it simple) can do it easily. I can inform about this method at some more places at the Ubuntu help wiki, sub-pages of [https://help.ubuntu.com/community](https://help.ubuntu.com/community).

We can create some opinion and 'heat', but really only hope that [your bug report #1549603](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1549603) will get some attention by the developers. I certainly agree, that new users should find a way to restore a USB pendrive from a cloned boot drive to a standard storage drive. A good place ***to show how to do it, or better provide a way to do it***, is in the SDC, another place is Disks (gnome-disks), as we have already discussed even with some developers. But it is not even in the instructions how to make a USB boot drive at [download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu).

And by the way, gparted is available the live session (it comes with the iso file).

---

### Post by sudodus on 2016-09-12
> **mc4man said:**
> What's semi interesting is in 14.04 i use gnome-disk-utility 3.0.2-2ubuntu8 (the older one
It has no problems creating a FAT32 usb device from a sdc device (simply pick "Format Drive" button & format to master boot record, then create partition of choice

Interesting :-)

---

### Post by sudodus on 2016-09-12
After Prerequisites come the main tasks, and after that come Postrequisites ;-)

I added this paragraph to an Ubuntu help wiki page that is used by many people: [FromUSBStick#Postrequisites - restore the USB drive](https://help.ubuntu.com/community/Installation/FromUSBStick#Postrequisites_-_restore_the_USB_stick).

And I added an internal link from [FromUSBStick#Known_Issues](https://help.ubuntu.com/community/Installation/FromUSBStick#Known_Issues)

*Edit:* And this link, a new post in a tutorial thread: [Restore a USB boot drive](https://ubuntuforums.org/showthread.php?t=2196858&p=13543602#post13543602)

---

### Post by ventrical on 2016-09-12
> **sudodus said:**
> 

Edit: The uploader has changed. Previously it was possible to upload big pictures, and the resolution (pixel) was decreased automatically to keep them within whatever was allowed. Now there is hard limit at 1024x768. So I cropped the pictures to keep the important information, and after that decreased the resolution to so that the width was 1024 pixel. Then I managed to upload the screenshots. Here they are :-)

Thanks .. I thought there was something wrong with my browser.


Edit:

This is a problem with the forums. it is intermittent.  I will open thread in appropiate area.

Regards..

---

### Post by T2uiYKb7 on 2016-09-22
> **sudodus said:**
> I created the bug report [#1622313, "gparted does not recognize the iso9660 file system in cloned Ubuntu USB boot drives"]("https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/1622313") from Xenial daily 'looking at' its own iso file as cloned, running a live system from the ***current daily Lubuntu Xenial desktop i386*** iso file.

Please mark 'affects me too', if it affects you and help add some heat to the bug report :-P It would be valuable to check in other versions of Ubuntu, particularly in Trusty alias 14.04.x LTS, because many people will install fresh Xenial systems from old Trusty systems.

I think many of us have seen this bug in gparted, but we have not reacted until now. A user at the Lubuntu mailing lists starting complaining about it, and put the blame on the new ***Ubuntu Startup Disk Creator*** alias ***usb-creator-gtk*** version 0.3.2 and 0.3.3 in Xenial.

But the Ubuntu Startup Disk Creator is only cloning the iso files, and they are hybrid iso files, made to boot from both DVD and USB drives. So the bug is in gparted, that cannot see the iso9660 file system, when in a USB pendrive.

After some additional testing, I found that the bug is worse in the 64-bit 16.04.1 LTS, and much worse in the 64-bit 14.04.1 LTS, as illlustrated by the following screenshots. This behaviour will really confuse new users of Ubuntu and the Ubuntu flavours.

-o-

Edit: The uploader has changed. Previously it was possible to upload big pictures, and the resolution (pixel) was decreased automatically to keep them within whatever was allowed. Now there is hard limit at 1024x768. So I cropped the pictures to keep the important information, and after that decreased the resolution to so that the width was 1024 pixel. Then I managed to upload the screenshots. Here they are :-)

So glad you reported this I don't know why I didn't. It annoys the heck out of me but I never stopped and thought why it happened. I thought somehow dd'n or cp'n an ISO or IMG to sdx somehow "broke" the partition table but[COLOR=#008000] is it just that it turns it into iso9660?[/COLOR]

---

### Post by sudodus on 2016-09-23
Yes, or should we say, it copies everything including the partition table from the iso or img file to the drive.

If there is an iso9660 file system, gparted will have problems, If there are other file systems, for example ext4, FAT32 or NTFS, gparted will be happy.

---

### Post by T2uiYKb7 on 2016-09-23
True thanks that makes so much more sense. I think this a common misconception. It scared the heck out of me when Gparted threw multiple serious errors at me, a bad partition table on a local drive would be **disastrous.** 

I think it's also a reason DD gets a bad name , people calling in "Disk Destroyer" not in jest and claiming it breaks there USBs. It would be great if all partition programs recognized iso9660 (and other optical disk partition tables/file formats if there are any) and didn't get scared to death by error messages.

---

### Post by sudodus on 2016-09-24
This might be a reason, but there are other and really serious reasons, why ***dd*** is nicknamed 'disk destroyer'. It is very powerful, but also dangerous, because it asks no questions. It does what you tell it to do directly. So if you tell it to wipe your family pictures ... and this can be a minor typing error away! This is the main reason why I created [mkusb](https://help.ubuntu.com/community/mkusb) in order to 'wrap a safety belt around dd'.

---

### Post by sudodus on 2016-10-08
There is activity in an upstream bug report. See this link: [https://bugzilla.gnome.org/show_bug.cgi?id=771244](https://bugzilla.gnome.org/show_bug.cgi?id=771244), where I posted the following comment.

> **Intro**

It is great that you are improving gparted :-)

I am developing and testing software at the user's level (including script-based software like 'my' mkusb). Unfortunately I am not advanced enough to compile gparted from the source code, but if you can provide a package for a major distro, I can install and test it, for example a deb package for debian and ubuntu. That way can will get help from me with extensive testing.

**Background**

What Alberto and I want is a fix so that gparted can recognize typical *isohybrid* partition tables with the 'iso9660' file system and the special structure, that makes such iso files possible to clone to bootable CD/DVD disks as well as to bootable USB pendrives and flash cards. Maybe we should also make it recognize 'udf' file systems with the same or similar isohybrid partition tables.

This kind of cloning (for example with dd or better with a tool, that wraps a 'safety belt' around the process) is the recommended method to create USB boot drives for many linux distros.

gparted is a very good tool, but this bug makes people give up with their pendrives. Too many people think that the cloning process caused a damage, so that their pendrive will not work, and/or will not be possible to restore to standard mass storage devices with an MSDOS partition table and a FAT32 file system.

**Test with mini.iso files (and other iso files of major linux distros)**

So please test with some typical USB pendrives made by cloning iso files. When gparted does not complain, but sees the file system, the end users feel confident with their pendrive.

If you cannot send me a compiled package, I suggest that you test the new version of gparted with some of the Debian or Ubuntu 'mini.iso' files (32-bit and 64-bit), which are small so quick to clone to a USB pendrive, as well as iso files of other major linux distrod (for example Arch, Fedora, Mageia, Manjaro, openSUSE). Many full size iso files (1-1.5) GB take a minute to clone to a fast USB pendrive. A slow pendrive may have a write speed of 5 MB/s, so it would need 3-6 minutes.

**Comparison with lsblk**

This is how lsblk sees a USB boot drive made from a Debian mini.iso file.

```
$ sudo lsblk -f /dev/sdd
NAME   FSTYPE  LABEL    UUID                                 MOUNTPOINT
sdd    iso9660 ISOIMAGE 2016-09-13-22-21-51-00               
&#9500;&#9472;sdd1 iso9660 ISOIMAGE 2016-09-13-22-21-51-00               
&#9492;&#9472;sdd2 vfat    Firmware C000-DAC4
                           
$ sudo lsblk -m /dev/sdd
NAME    SIZE OWNER GROUP MODE
sdd    29,8G root  disk  brw-rw----
&#9500;&#9472;sdd1   22M root  disk  brw-rw----
&#9492;&#9472;sdd2    6M root  disk  brw-rw----
```

gparted version 0.25.0 is not happy with it and dumps the following text (to a terminal window)

```
======================
libparted : 3.2
======================
Invalid partition table - recursive partition on /dev/sdd.
Invalid partition table - recursive partition on /dev/sdd.
```

and the corresponding complaint and lack of output for the file system in gparted's GUI.

---

**Report the bug upstream?**

If the main bug or missing feature to recognize the isohybrid partition table structure, maybe we should create a bug report against libparted.

Or you should use the same method as lsblk (and/or blkid) for gparted to recognize these kinds of partition tables and file systems.

---

