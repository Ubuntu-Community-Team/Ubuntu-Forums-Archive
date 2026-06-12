---
title: "Feeling relieved about upgrade from ext3 to ext4"
date: 2016-08-01
forum: The Cafe
---

### Post by yoshii on 2016-08-01
I recently found out that some wikipedia info about ext4 disadvantages was out of date and that it is in modern times probably a good choice over ext3 in most cases.  
Anyways, this is relevant because I had formatted my digital audio workstation partition as ext3, which is still a great invention, but if i understand the documentation, is slightly less safe unless the "barrier" parameter is set manually (it's off by default).  

Anyways, ext4 has some performance advantages and I had to learn how to convert from ext3 to ext4 and it turned out to be pretty easy, so I'm happy.  

I had one snafu, i tried performing one of the necessary commands from an old LiveCD, and it said something or other was missing from Canonical.  But I was able to run checkdisk from within gParted and everything got maintained and I didn't lose any data nor have any issues after bootup.  

So now I can expect my workstation to be just a little bit faster even though it was already fast enough to get pretty good projects done.  
I can probably push things just a little bit more if I get adventurous.  

Long story short, I am relieved at the ease of doing a major filesystem change and impressed with the sophistication of the software.

---

### Post by Bucky Ball on 2016-08-01
Congratulations. My only question is: how? Did you backup your data and simply recreate the partition as an EXT4 then copy the data back or some other way?

---

### Post by yoshii on 2016-08-02
The technique you are talking about is the preferred way to do it, but I don't have the right tools (backup drive, backup software, backup knowledge/experience) to do that, so I just did the less efficient way.  

First step was to edit my /etc/fstab to have ext4 instead of ext3 for the system hard drive partition (the only drive in use).  This wasn't a problem since the version of Xubuntu I am using is already mounting ext3 drives via some kind of ext4 mechanism.  I know this because I have the boot splash screen disabled in grub so I can see all of the boot messages as they happen.  

Anyways, after that, I followed the instructions for activating ext4 functions:  [https://help.ubuntu.com/community/ConvertFilesystemToExt4?action=fullsearch&value=linkto%3A%22ConvertFilesystemToExt4%22&context=180](https://help.ubuntu.com/community/ConvertFilesystemToExt4?action=fullsearch&value=linkto%3A%22ConvertFilesystemToExt4%22&context=180)  ...Oh, and I think I added an ext4 command to my grub config in case the kernel needed it.  I found that out from the ext4 website.  It looks like this ( /etc/default/grub ):

```

GRUB_CMDLINE_LINUX_DEFAULT="rootfstype=ext4"

```

The failing part was the command to re-install grub2, but I'm not even sure if that's necessary since the instructions are also for some really really old Ubuntu systems.  
Anyways, instead I ran checkdisk via gParted from the LiveCD which was already running.  It showed me that the partition was, yes, set to ext4.  And instead of having fsck run at boot time, I let gParted check it.  Then I rebooted and did sudo update-grub, and rebooted.  

Since ext4 is backwards compatible with ext3, the changes affect new saves and new writes not the old data.  That's why they recommend doing a full format and retransferring backed up files into ext4 to get fresh metadata and a defragmented copy.  But even without doing that, ext4 has some technical advantages, especially for large file handling, which I won't go into.

---

