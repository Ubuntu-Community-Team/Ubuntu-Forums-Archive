---
title: "Trouble installing Ubuntu server on older computer"
date: 2014-12-11
forum: Server Platforms
---

### Post by max60 on 2014-12-11
I've been trying to get ubuntu server on an older computer, I don't know how old exactly, but at least five years old. When I download the newest version and create a startup disk with startup disk creator on Ubuntu desktop, I get errors about being unable to mount the drive. When I mount the iso and copy the files over to the usb there are a bunch of errors about not being able to copy file links on FAT32, so I switch the file system to NTFS, and then I get errors with syslinux that it can only work on FAT32 systems. I've also tried creating startup disks with an actual dvd, but then the computer wont boot due to not recognizing any operating system.

I could probably figure this out with a few more hours of troubleshooting, but in truth, this has become a waste of my time. Can anyone tell me what I'm doing wrong and how to fix it?

---

### Post by bobthebaritone on 2014-12-12
Hi Max60,
You should be ok with making a boot USB FAT 32.
There is the following note in the 14.10 release notes for Ubuntu server:

[LIST]
[*]Due to changes in syslinux, it is not currently possible to use usb-creator from 14.04 and earlier releases to write USB images for 14.10; we believe that it is also not possible to use usb-creator from a 14.10 system to write USB images for earlier releases. For now the workaround is to use a matching release of Ubuntu to write the images, but we intend to issue updates soon to work around this incompatibility. [1325801]("https://bugs.launchpad.net/bugs/1325801")
NOTE: you should also do a checksum compare with downloaded images. Have you done this with your ISO?

Cheers,

Bob



[/LIST]

---

### Post by sudodus on 2014-12-12
Particularly for servers, I'd recommend the long time support (LTS) versions, that are supported for 5 years. The other versions are only supported for 9 months.

I suggest that you try both of Ubuntu Server 12.04 LTS and 14.04 LTS. In an old computer the older version (12.04 LTS) might be better, but there might be some new feature in 14.04 LTS that you want or need.

This link gives more information about booting from USB

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by max60 on 2014-12-12
I'm not using 14.1 as of right now, from what I gather you're trying to say I cannot create a 14.1 disk on a 14.04 desktop?

However, I did try 12.04 as sudodus said and it worked, but when I check the disk for defects on the installer it says;

"The ./install/netboot/ubuntu-installer/i386/pxelinux.cfg/default file failed the MD5 checksum verification. Your CD-ROM or this file may have been corrupted"

I looked around and apparently this is a common thing due to the file not existing, however I thought it may be relevant as I cannot seem to partition the disks. When the installer goes to the step to partition disks the only options are "Write edits to drive", "Undo partition edits" or login to iSCSI to edit the partitions". I may be paraphrasing, I can't remember the exact wording. I have no idea how to use iSCSI. My computer doesn't have an ip address, and when I put 'ip addr show' into the command line it doens't really give me any information. So my drive has no partition for root and I have no idea how to create one. Any ideas?

---

### Post by max60 on 2014-12-12
update: I seem to be able to get past the unusual partition editor by manually unmounting /dev/sda1 and mounting it to root instead of cdrom. The only problem with this is I cannot copy files to cdrom after I do that.

---

### Post by sudodus on 2014-12-13
> **max60 said:**
> I'm not using 14.1 as of right now, from what I gather you're trying to say I cannot create a 14.1 disk on a 14.04 desktop?

You can but not easily with the Startup disk creator because of that bug. But there are also other reasons to try the two LTS versions first.
> 
However, I did try 12.04 as sudodus said and it worked, but when I check the disk for defects on the installer it says;

"The ./install/netboot/ubuntu-installer/i386/pxelinux.cfg/default file failed the MD5 checksum verification. Your CD-ROM or this file may have been corrupted"

I'm not sure if there is a bug or if you *should* get a correct result from the md5sum checksum test. What about the md5sum of the iso file?

Example (do it for the particular file, that *you* downloaded)

```
md5sum ubuntu-12.04.4-server-amd64.iso
e83adb9af4ec0a039e6a5c6e145a34de  ubuntu-12.04.4-server-amd64.iso
```

How does it check with the corresponding value at

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
> 
I looked around and apparently this is a common thing due to the file not existing, however I thought it may be relevant as I cannot seem to partition the disks. When the installer goes to the step to partition disks the only options are "Write edits to drive", "Undo partition edits" or login to iSCSI to edit the partitions". I may be paraphrasing, I can't remember the exact wording. I have no idea how to use iSCSI. My computer doesn't have an ip address, and when I put 'ip addr show' into the command line it doens't really give me any information. So my drive has no partition for root and I have no idea how to create one. Any ideas?

If you have an Ubuntu desktop iso file, or some other linux iso file, you can make a CD/DVD/USB boot drive, boot the computer and run ***gparted***, which is a good tool with an intuitive graphical user interface. That way it will be easier to create the partitions you want, and then you can reboot with the Ubuntu Server install drive and 'simply' select those partitions with the installer (instead of creating them).

The instructions for testing might help you do the steps necessary to install. The following list is copied and pasted from

[http://iso.qa.ubuntu.com/qatracker/milestones/318/builds/73675/testcases/1337/results](http://iso.qa.ubuntu.com/qatracker/milestones/318/builds/73675/testcases/1337/results)

> 
Scope of this test is to verify that the system is installed and you can login into it.

Proceed in your native language if you wish. Instructions will remain in English

Boot up the image
Choose the desired language
Select "Install Ubuntu Server"
Choose the language
Select your location
Configure locales
At configure keyboard page, select NO
Select the country of the keyboard
Select the keyboard layout
Select hostname ubuntu as default
Insert the name for the new user
Insert the name for the account
Choose a password
Reinsert the password
At encrypt request select NO
Verify or setup the timezone
At partitioning select "Guided - Use entire disk" [COLOR=#0000ff]- Here you might be able to select "Manual partitioning"[/COLOR]
Select disk to partition
At "Write changes to disks", verify that everything is right and select YES
At "http proxy" request, leave it blank and press enter
At managing upgrades select "No automatic updates"
At Software selection, press "Enter"
Select to install Grub in the master boot record
Remove the installation media (CDROM or USB key)

Wait that the system reboot
   The system reboot, the login prompt appear and you can login into it 


I'm not sure about the partitioning options, I usually start from the Ubuntu **mini.iso**, where there is a [COLOR=#0000ff]"Manual partitioning"[/COLOR] option

---

### Post by sudodus on 2014-12-13
> **max60 said:**
> update: I seem to be able to get past the unusual partition editor by manually unmounting /dev/sda1 and mounting it to root instead of cdrom. The only problem with this is I cannot copy files to cdrom after I do that.

Do the partitioning with ***gparted***, which is described in my previous post. It is easier.

---

