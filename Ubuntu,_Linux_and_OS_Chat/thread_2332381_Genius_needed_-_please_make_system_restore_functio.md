---
title: "Genius needed - please make system restore function"
date: 2016-07-31
forum: Ubuntu, Linux and OS Chat
---

### Post by Jan_Johansson on 2016-07-31
Hi, as the title says, I(and probably many others) would very much like a system restore function that could be added to GRUB menu, so that in case an update or other things went wrong, then the system could be up and running again in no time and ones personal files were safe. All the backup programs that work from inside Ubuntu are no good if you cannot get to the desktop or the prompt.

Personally I'm using Peach OSI which is built upon Xubuntu 14.04 LTS and later will be updated to 16.04 LTS - I took the jump and are only using linux now and no more windows, only a few programs I were using before don't have linux alternatives and I use them on my other laptop.

Hope someone can make this happen:)

With kind regards

JBJ

EDIT: I normally use Redo backup [http://redobackup.org/](http://redobackup.org/)   to backup my system, it uses partclone for the procedures. Note: it cannot be used to restore to smaller drives than the one it were backuped from, unless a small tweak is used:

A way to restore Redo backup to smaller HDD

Example:
1 - Source disk: 500GB
2 - Dest disk: 320GB

NOTE: this do not work with HDD's smaller than 160GB, because of block size limitations.



Workaround: 

Edit the image file: xxxxxxxx.size - it's a normal .txt file and the x's in the name is the date(unless changed by you). 

When opened with a text editor you see only numbers, this is the actual size of the backup which adds up to the size of the whole HDD - Eventhough you only backed up 1 or 2 partitions and the used data is smaller than the actual partition. 

This is why an image cannot be restored to smaller disk! 

Change the numbers to reflect on the size of your backup + the amount of GB you want your partition to be -  Example: if your backup is 16GB and you like your total partition size to be 120GB, then change the numbers to 104GB. Take in mind that a normal installation don't take up so much space even when programs has been added, so if you like to keep free space for other partitions then consider carefully how much space you use for this!

After you have saved the .size file, reboot with Redo backup and chose Restore.

When finished restoring, reboot to Redo and use Gparted to check the partition for errors.

When totally finished, reboot into your OS.

---

### Post by kansasnoob on 2016-07-31
I was told a few years ago that btrfs would bring with it a sort of auto-clone that would allow restoring to a previous state, but development of btrfs seems to be slow and sporadic, so don't hold your breath.

---

### Post by oldos2er on 2016-07-31
> **Jan_Johansson said:**
>  All the backup programs that work from inside Ubuntu are no good if you cannot get to the desktop or the prompt.

You can boot to a prompt via recovery mode and run rsync, for example. If you're using a GUI backup program (you don't say) I can see how that would be a problem.

---

### Post by Geoffrey_Arndt on 2016-07-31
One major issue is . . you're not running Ubuntu and any updates to Ubuntu may not be supported or work on Peach OSI (who knows what modifications the developer(s) have made already)?     I especially don't see the advantage of using many non-official derivatives of Ubuntu.   Mint is one exception, but other _have known stability and update issues_.

But getting back to your main point, there is a way to boot back into Ubuntu now (called a LIVE OS - - DVD and or Flash-Media).   Combine that Clonezilla, and back up programs, (Back-in-Time is excellent) and this problem is largely solved.    A magic restore button on Linux is problematic, because of the variation in Linux and experience level of users.

BTW, the best way to have developers read comments is via other websites such as Launchpad or developer forums/lists.   Most developers don't have time or inclination to read thru user forums.

---

### Post by buzzingrobot on 2016-07-31
Don't bother backing up anything that can be easily restored otherwise.

The best approach for me is not to worry about backing up the "system". Ubuntu, and other Linux distros, can be re-installed quickly. 

Put  /home on a separate partition, on a separate drive if that's available. Back that up.  But, if the system takes a dive, just reinstall and tell the partitioner to mount that partition as /home and not to format it, while mounting and formatting the old /. All your files in /home will remain, while new system is installed.

---

### Post by grahammechanical on 2016-07-31
Last year I experimented with a version of Ubuntu called Snappy Ubuntu Desktop Next. It was not an ISO image but an img file that had to put on a USB stick or a hard drive using the restore image function of the Disks utility.

As well as being Mir + Unity 8 + a Snap packaged OS it had an interesting way of rolling back the OS if an OS update failed.

There were two system partitions - system A and system B. The initial install put the OS in the system A partition and Grub booted Ubuntu from system A partition. The next update to the OS would go in the system B partition and if the update succeeded then Grub would be set to boot Ubuntu from system B but if the update failed Grub would continue to boot from system A.

After that updates to the OS would alternate between System B and system A. And the method worked. The OS file system was read only and all user data went into another partition called writable.

This Ubuntu was built on wily (15.10) code. So it received daily updates to the OS. Sadly, the developers did not continue building images once 15.10 was released. The project did not move on to xenial code. I suppose the concept had been proven to work and so that ended the project.

I can see this kind of Ubuntu being used by OEMs with Ubuntu being pre-installed on laptops and mobile devices. For that to happen Unity 8 has to meet the grade as a proper desktop user interface and all applications will have to be snap packaged. A user of Snappy Ubuntu Desktop Next would never have a broken OS due to an update and the OS would always be up to date without needing to upgrade to a newer release. 

Because of the more complex partitioning layout I find it hard to imagine that this kind of Ubuntu would ever be an ISO installable Ubuntu.

Regards.

---

### Post by Geoffrey_Arndt on 2016-07-31
Really, the practical way to do all this (easy & safe restore) is to use the ChromeOS.   Google has it down to a science, in that you can restore that system easily and since all configs are stored in the "Cloud" . . . it's "so simple even a Cave-Man could do it."

Course, the only down side is you're running ChromeOS versus Linux.

---

### Post by Jan_Johansson on 2016-08-03
> **Geoffrey_Arndt said:**
> One major issue is . . you're not running Ubuntu and any updates to Ubuntu may not be supported or work on Peach OSI (who knows what modifications the developer(s) have made already)?     I especially don't see the advantage of using many non-official derivatives of Ubuntu.   Mint is one exception, but other _have known stability and update issues_.

But getting back to your main point, there is a way to boot back into Ubuntu now (called a LIVE OS - - DVD and or Flash-Media).   Combine that Clonezilla, and back up programs, (Back-in-Time is excellent) and this problem is largely solved.    A magic restore button on Linux is problematic, because of the variation in Linux and experience level of users.

BTW, the best way to have developers read comments is via other websites such as Launchpad or developer forums/lists.   Most developers don't have time or inclination to read thru user forums.

Hi, actually I am running Ubuntu - Xubuntu - and I do recieve updates just like any other user of Ubuntu. Peach OSI is allot more stable than any other version of Xubuntu that I have tried including the official one(7 years of versions tried), and allot more supported as the developer has given a Facebook page where its possible to contact him.

I have made a blog entry review of Peach OSI here, if anyone is interested: [http://jbj-tech-notes.blogspot.dk/2016/06/peach-osi-instead-of-windows.html ]("http://jbj-tech-notes.blogspot.dk/2016/06/peach-osi-instead-of-windows.html")

As my system is setup, I use one partition for Peach OSI and my /home and my personal files are on a second partition and backup on a third partition. 

For the moment I use an USB stick with REDO backup for my back up(it also has Peach OSI on it as liveCD) - but were interested in something a little bit more like Windows System restore function - I hate windows and have done so in all the 29 years I worked with PC's, thats why, when my laptop broke down and I switched to another model, I decided to go ALL-in on Peach OSI.

There is a GRUB entry for recovery and it has helped me after an unfortunate update:

recordfail
    load_video
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  afae36e8-98ba-46bd-bc02-956afeea370b
    else
      search --no-floppy --fs-uuid --set=root afae36e8-98ba-46bd-bc02-956afeea370b
    fi
    echo    'Loading Linux 3.13.0-43-generic ...'
    linux    /boot/vmlinuz-3.13.0-43-generic root=UUID=afae36e8-98ba-46bd-bc02-956afeea370b ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.13.0-43-generic


Its just not enough. So another system restore function would be preferred and in GRUB as this starts before anything else gets loaded.

JBJ

---

### Post by buzzingrobot on 2016-08-03
As I mentioned, I'm not sold on the need for a Windows-like system restore in Linux given the ease and speed of re-installing that system. If you look around, there are simple ways of getting a list of  every .deb installed.  That list can then be used as input to a simple shell script to reinstall those packages. (I know three are docs and examples at Debian's site and I wouldn't be surprised to see them somewhere on Ubuntu's wiki.) Combined with a separate /home partition and, if needed, a backup of edits in /etc, (which you'd want to do if any non-default repos were added) that should restore things.

I suspect it would be possible to automate all this and make it run from the boot, aka Grub, menu, assuming the kernel was still working. The caveat is the Linux is so much more open to user fiddling than Windows and that increases the chances for things to break.

---

### Post by yoshii on 2016-08-03
AV Linux has a "snapshot" function similar to restore or partition restore.  
AV Linux started up again this past March or so (2016).  

You can ask about it here:  [http://bandshed.net/forum/index.php](http://bandshed.net/forum/index.php)

AV Linux is a Debian Linux distro, but it functions so similar to Ubuntu that it's easy to learn and many of the .DEB archives can be installed on either system.  
It's mainly designed for people doing music composing, but you could use it as a base for regular computing if you wanted.

---

### Post by mastablasta on 2016-08-04
> **kansasnoob said:**
> I was told a few years ago that btrfs would bring with it a sort of auto-clone that would allow restoring to a previous state, but development of btrfs seems to be slow and sporadic, so don't hold your breath.

actually OpenSUSE (one of the versions) uses it as default. and it works well. another option is ZFS. i am not sure how well are these on desktops sicne for example ZFS requires RAM and CPU power. so it is often used on server setups, not so much on desktops.

> **buzzingrobot said:**
> 
Put  /home on a separate partition, on a separate drive if that's available. Back that up.  But, if the system takes a dive, just reinstall and tell the partitioner to mount that partition as /home and not to format it, while mounting and formatting the old /. All your files in /home will remain, while new system is installed.

that Works well if you use stock OS. however, if you installed various programs then you would also need to backup those or at least a list of installe dporgrams so you can recover. otherwise reinstall (overwrite the damaged OS) is also possible.

---

### Post by buzzingrobot on 2016-08-04
> **mastablasta said:**
> 
that Works well if you use stock OS. however, if you installed various programs then you would also need to backup those or at least a list of installe dporgrams so you can recover. otherwise reinstall (overwrite the damaged OS) is also possible.

True. And backing up rather than reinstalling is a more useful option for users who do not have good broadband access. The distribution and update methods used by Linux, OS X, and Windows assume everyone has that kind of access, and that's not the case.

E.g., I can download an Ubuntu ISO, burn it, and do a new install, all in about 15 minutes. If someone needs, say, 4 hours to do that, then my advice to "just reinstall" is not useful. 

Building in a automatic *full* backup in Linux or elsewhere means assuming the space to hold that backup exists and will continue to exist. Not a safe assumption.

 You could, at the install, create a hidden partition sized to hold a default reinstall of the OS. Then tweak the bootloader to offer an option to use that image and do the reinstall without formatting /home. I.e., a "recovery" partition like Windows and OS X. (Or, just assume everyone has good broadband and pull the image down.)

Windows "system restore", AFIAK, takes a snapshot of the current configuration state of the system to allow a rollback to that working config if something botches things.

---

### Post by yoshii on 2016-08-04
Windows's system restore isn't as stable as a partition backup though.  I've used it and read about it.

---

### Post by Geoffrey_Arndt on 2016-08-05
For Linux friendly machines (such as System76, Logic Supply, Zareason) it's a trivial matter to do a clean re-install.   On fast broadband and using usbv3-stick, it can be done from A to Z in 15-20 minutes.   The important "stuff" is your data (that is, if yoiu're actually doing productive things on the PC).    The customizations can be tracked in a simple database such as Zim Wiki.   

If well planned, these customizations can be re-implemented in less than an hour (if PPA links, /etc tweaks are saved in Zim).    This is all I need - - I'd rather not mess with additional windows-like restore points at all (along with disk defragging, registry tweaks, malwarebytes, spamNuker, yada yada yada).

---

### Post by Jan_Johansson on 2016-09-28
Guys try not to go OT and I don't want to switch to another distro, I'm happy with the one I have:) I have edited my first post with info about my normal backup method.

JBJ

---

### Post by pauljw on 2016-09-28
This ppa works very well for me on 14.04.  It's been updated to use on 16.04, too.  Follow the instructions for installation.  I keep 5 restore points on my system and it has come in handy a couple of times.

[https://launchpad.net/~nemh/+archive/ubuntu/systemback](https://launchpad.net/~nemh/+archive/ubuntu/systemback)

---

