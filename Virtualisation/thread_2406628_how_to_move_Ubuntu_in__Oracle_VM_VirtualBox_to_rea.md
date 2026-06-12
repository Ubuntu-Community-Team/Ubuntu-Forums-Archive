---
title: "how to move Ubuntu in  Oracle VM VirtualBox to real instalation?"
date: 2018-11-23
forum: Virtualisation
---

### Post by nicolas400 on 2018-11-23
Hi, I have an installation of Ubuntu running in an Oracle VM VirtualBox.
I installed some features that I want to try, successfully!,  But now I want to move that installation to a "real" installation, on my hard disk.
I tried first making an image of the disk, but I can't create the image if the disk is mounted.

Is there any way to accomplish this?

Best Regards

---

### Post by howefield on 2018-11-23
Thread moved to the "*Virtualisation*" forum.

---

### Post by yancek on 2018-11-23
It is possible but it appears from your post that you are trying to do it from the Ubuntu installed in Virtual Box.  I don't believe that will work.  In years past, there was software which could be used on an installed system of Ubuntu to create an iso image which would retain all settings.  Remastersys, Systemback, PinGuy Builder.  I don't think (know) that any will work with the latest Ubuntu.  You might do an online search, I haven't found anything indicating they will work.

Do you have an iso file of another Linux system on the host system?  What is the host system?  Which OS do you use to boot the host (which bootloader)?

I used a GParted iso to do this and copied the installed system in VBox to a flash drive which did boot/work.  You would need another Linux system as an iso on the host system and would need to access it in VBox by first selecting by highlighting Ubuntu in VBox and going to Settings/Storage to select the iso file.  If you have multiple systems in VBox, this might complicate things.  I just used a dd command to copy the entire system to the flash drive from VBox.  You could then use a variation of a dd command to do this but what you would use would depend upon what you have installed on the host and whether you have one drive or multiple drives.

---

### Post by oldfred on 2018-11-23
I do not know virtual installs.

You may have same issue as any other attempt to move an install of duplicate or different UUIDs and manually having to edit those. And if gpt it also has GUIDs that must match primary & backup partition tables.

But I do believe in doing a new fresh install anytime you want to move Ubuntu. Then you restore from your normal backup. That becomes a good test that your backup procedures are complete and if you still have old install, you can go back an get anything you missed.

Most of your configuration & data is in /home, but if a server configuration you may have data, web or other applications that may be in / folders, but you are backing those up anyway.
I also export list of installed apps as part of my backup, to make it easy to reinstall everything.

---

