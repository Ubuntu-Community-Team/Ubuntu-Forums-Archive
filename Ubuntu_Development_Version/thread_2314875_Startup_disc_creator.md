---
title: "Startup disc creator"
date: 2016-02-24
forum: Ubuntu Development Version
---

### Post by mc4man on 2016-02-24
While the new method never fails it seems to create a disk that becomes difficult to format back to a plain storage device. Disks has issues, gparted also inc. totally mis reading the size. 
Maybe there is a trick to simply format the device back to let's say fat32, if so I've not found
Some various images attached, first gparted is after attempting to format in Disks, 2nd gparted is on a fresh disc never opened in Disks

---

### Post by sudodus on 2016-02-24
1. Use [mkusb's wipe menu](https://help.ubuntu.com/community/mkusb/wipe)

2. Use ***gparted***. Often it works if you start in gparted to create a ***fresh partition table***. Sometimes it helps to start by wiping the first megabyte (which is part of the recipe of mkusb/wipe).

3. You may also need to ***unplug and replug*** the pendrive for it to be recognized by the kernel.

---

### Post by sammiev on 2016-02-24
> **sudodus said:**
> 1. Use [mkusb's wipe menu](https://help.ubuntu.com/community/mkusb/wipe)

2. Use ***gparted***. Often it works if you start in gparted to create a ***fresh partition table***. Sometimes it helps to start by wiping the first megabyte (which is part of the recipe of mkusb/wipe).

3. You may also need to ***unplug and replug*** the pendrive for it to be recognized by the kernel.

+1 I was getting the same results and wiping the first megabyte with mkusb worked for me.

I followed it up by formating it Fat32.

---

### Post by mc4man on 2016-02-24
Yeah, using gparted to  make a fresh partition table is what I've been doing, (stumbled across the first time this came up.
I guess my concerns are  - 
sdc does not document how users can format the usb drive once finished with
Disks seems incapable of doing this or if it can not even remotely obvious. However Disks is the default & only partitioning app supplied.

---

### Post by sudodus on 2016-02-24
In standard Ubuntu Xenial live, the SDC (usb-creator-gtk), Disks (gnome-disks) and gparted are provided.

Different flavours come with different tools, but I think all Ubuntu flavours have gparted in the live session (but not in the installed system).

But you should also remember, that you need not worry about the previous content of the pendrive, if you intend to flash a new iso file into it. That process (by dd, mkusb, Disks and now also SDC) will overwrite it anyway. It is only if you want to use the pendrive in another way, that you need reformatting.

I agree that it should be mentioned in the standard documents, but there are wiki/help pages already, for example

[mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive)

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

[Win32DiskImager/iso2usb/FormatHelp](https://wiki.ubuntu.com/Win32DiskImager/iso2usb/FormatHelp)

---

### Post by ELD on 2016-02-25
This has actually been an issue for quite some time (long before 16.04, possibly even 15.04). I was wondering why all my USB drives had issues with wrong sizes, not mounting etc. All of them had been made as boot disks using that tool.

So, I can confirm it's still an issue in the current version in 16.04.

I think it needs to be made into a bigger issue, as people can end up thinking their USB drives are broken (as I have done, ended up buying more at a total waste of money!).

---

### Post by mc4man on 2016-02-25
I did file a bug as there should be some mention/directions or what not as to how to deal with seeing as though Disks will  bork on formatting these drives & there is nothing provided to actually make the drive useful as a storage device post install.
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1549603](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1549603)

---

### Post by sudodus on 2016-02-25
You still say 'there is nothing'. But there *is* something, but not enough, for example the links to the Ubuntu wiki/help pages shown in post #5.

Where do you want this ***information***? Via a button on the Startup Disk Creator's window?

Maybe it would be better to have a ***tool*** via that button, (integrated in the Ubuntu Startup Disk Creator like it is in mkusb).

---

### Post by mc4man on 2016-02-25
> **sudodus said:**
> You still say 'there is nothing'. But there *is* something, but not enough, for example the links to the Ubuntu wiki/help pages shown in post #5.

Where do you want this ***information***? Via a button on the Startup Disk Creator's window?

Maybe it would be better to have a ***tool*** via that button, (integrated in the Ubuntu Startup Disk Creator like it is in mkusb).

I would  like this info/a warning in the package description for sdc & in the sdc dialog prior to creating the disk.
Best would be to provide a means in sdc to format the device if Disks can't be improved to do the job. ( though that's unlikely, at least for 16.04

Slightly off-topic maybe gparted should be in default install though it's package description is somewhat deficient as doesn't show in Dash with some common terms like 'format'  & 'disk'

---

### Post by MikeMecanic on 2016-02-25
First, SDC was not working before and now it works.  SDC is a dedicated ISO maker made for Ubuntu and is the most user friendly app that I ever seen.  There is no choice to deal with because it makes only one thing: Build an ISO image of any Ubuntu flavors.  Once the ISO image have been created you must keep it in case (for n reasons) you need to do a fresh install.   

_It's Disk that needs correction now._  For Gparted, it is in all Ubuntu Installers.  Every time I do a fresh install, I always pass by *Try Ubuntu* and search Gparted in Dash to delete Ubuntu partitions.  That way, I always do a fresh install on an empty hard drive disk.

Cheers,

---

### Post by mc4man on 2016-02-25
Well gparted in a live session isn't going to help format the drive that's running the live session.
As far as Disks, Gnome goes to some lengths to minimize options & capabilities of it's apps,the older gnome-disk-utility *may* have been able to handle.

---

### Post by sudodus on 2016-02-26
> **mc4man said:**
> I would  like this info/a warning in the package description for sdc & in the sdc dialog prior to creating the disk.
Best would be to provide a means in sdc to format the device if Disks can't be improved to do the job. ( though that's unlikely, at least for 16.04

Slightly off-topic maybe gparted should be in default install though it's package description is somewhat deficient as doesn't show in Dash with some common terms like 'format'  & 'disk'

There could be a *button* 'Restore a USB drive for data storage' and behind that button there could be information and a tool (in a second window).

> **MikeMecanic said:**
> First, SDC was not working before and now it works.  SDC is a dedicated ISO maker made for Ubuntu and is the most user friendly app that I ever seen.  There is no choice to deal with because it makes only one thing: Build an ISO image of any Ubuntu flavors.  Once the ISO image have been created you must keep it in case (for n reasons) you need to do a fresh install.   

_It's Disk that needs correction now._  For Gparted, it is in all Ubuntu Installers.  Every time I do a fresh install, I always pass by *Try Ubuntu* and search Gparted in Dash to delete Ubuntu partitions.  That way, I always do a fresh install on an empty hard drive disk.

Cheers,

I agree, that it is good that the new SDC is very simple and *works* :-)

An extra button might be OK - would not make it much more complicated. An alternative is to have another very simple tool to  'Restore a USB drive for data storage'.

I don't agree that you must keep the iso image in a USB pendrive. I consider pendrives to be *temporary* devices. I keep the iso files in my main computer's data partition (which is backed up separately), and I flash the image from an iso file into a pendrive, when i need it.

> **mc4man said:**
> Well gparted in a live session isn't going to help format the drive that's running the live session.
As far as Disks, Gnome goes to some lengths to minimize options & capabilities of it's apps,the older gnome-disk-utility *may* have been able to handle.

I think it will be hard to make the gnome developers add this feature to *Disks*. It is already available in *mkusb* (so I know how to do it) and I think it would be easier to get it into the *SDC* :-)

We can also make a *simple dedicated tool* for it - that would be easiest. But then there would be a huge problem - to get that dedicated tool accepted into a repository :-(

---

### Post by sudodus on 2016-02-26
Maybe something like the **function mk_msdos** of following script might be added to the Ubuntu Startup Disk Creator, SDC, to be 'started from a button'. The function written in bash could be translated to python if it would be integrated better that way, and the echo statements should be replaced or removed.

***Edit:*** Version 1.0 replaced by version 1.1, and a third screenshot is added. Please try this new shellscript :-)

```

#! /bin/bash

#-----------------------------------------------------------------------------
#
## Copyright 2016 Nio Wiklund
#
# GPLv3: GNU GPL version 3
# <http://gnu.org/licenses/gpl.html>.
#
# This is free software: you are free to change and redistribute it.
# There is NO WARRANTY, to the extent permitted by law.

# date        editor   comment
# 20160226    sudodus  created from mk_mkdos in mkusb
# 20160227    sudodus  accepting only mass storage devices as target
# 20160227    sudodus  version 1.1

version=1.1

inversvid="\0033[7m"
resetvid="\0033[0m"
redtext="\0033[31;47m"

#######################################################################
#######################################################################

function mk_msdos {

# make an MSDOS partition table and a FAT32 file system

target="$1"
label1="$2"

label1="${label1:0:11}"
label1="${label1^^}"
#echo "Label (name) for the FAT32 partition: $label1"

echo "Trying to unmount partitions if mounted on the target device"
umount "$target"*
df | grep "$target"
if [ $? -eq 0 ]
then
 echo "mk_msdos: could not unmount a partition on the target device"
 exit
fi
echo "------------------------------------------------------------"
dd if=/dev/zero of="$target" bs=1024 count=1024 2>&1
parted -s "$target" mklabel msdos
sleep 0.5
parted -s "$target" mkpart primary 1048576b 100%
sleep 0.5
parted -s "$target" set 1 boot on  # set boot flag on partition 1
sleep 0.5
mkfs.vfat -v -F 32 -n "$label1" "${target}1"
if [ $? -eq 0 ]
then
 success=true
else
 success=false
fi
sleep 0.5
sync
if $success
then
 /bin/echo -e "$inversvid created MSDOS partition table and FAT file system $resetvid"
else
 /bin/echo -e "$inversvid mk_msdos: could not create MSDOS partition table and FAT file system $resetvid"
fi
}

########################################################################
########################################################################
#
# main program
#
########################################################################
########################################################################

# print version on demand

if [ "$1" == "-v" ]
then
 echo "$0 version $version"
 exit
fi 

# identify usb devices

usb_dev=$(ls -l /dev/disk/by-id|grep usb|grep -v 'part.*->' \
|sed -e 's/.*usb-/usb-/' -e 's#../..#/dev#' -e 's/^/ /' -e 's/$/ /'|sort -k3)

# usage text

leng=${#1}
leng1=$((leng - 1))
trunk=${1:0:leng1}

if [ "$(whoami)" != "root" ] || [ $# -gt 2 ] || ! test -b "$1" || test -b "$trunk" || [ "$1" == "-h" ]
then
 echo "Restore a USB install device to a device with MSDOS partition table
and FAT32 partition (to store and transfer files)"
 echo "Usage:"
 echo "sudo $0 <mass storage device> [label]  # max 11 characters in label"
 echo "Example:"
 echo "sudo $0 /dev/sdx usb-123"
 echo "Help:"
 echo "$0 -h"
 echo "Version:"
 echo "$0 -v"
 /bin/echo -e "${inversvid}${usb_dev}${resetvid}"
 exit
fi

# checkpoint

/bin/echo -en "$redtext$inversvid Warning! $resetvid$redtext
This shellsript is only a $inversvid demo $resetvid$redtext for a function to be built into a program,
that is selecting the target device in a safe way to avoid overwriting     
valuable data by mistake. This simple script is not really safe.           
$inversvid Use it very carefully and only for testing! $resetvid$redtext [press Enter to continue] $resetvid"
read -n1 tmp
lsblk -o NAME,MODEL,FSTYPE,LABEL,MOUNTPOINT,SIZE,NAME

/bin/echo -e "${inversvid}${usb_dev}${resetvid}"
echo ''
echo "$usb_dev"|grep -m1 "$1" > /dev/null
if [ $? -ne 0 ]
then
 /bin/echo -en "$redtext Not a USB device. Do you really want to overwrite $inversvid ${1} $resetvid$redtext ? (y/N)$resetvid "
 read ans
 if [ "$ans" != "y" ]
 then
  exit
 fi
fi

/bin/echo -e "$inversvid Final checkpoint $resetvid"
/bin/echo -en "Do you want to restore $inversvid ${1} $resetvid to a FAT32 partition? (y/N) "
read ans
if [ "$ans" == "y" ]
then
# do it
 mk_msdos "$1" "$2"
# check it
 parted -s "$target" print
fi

```

The attached screenshots illustrate what it looked like, when I used it. I do not expect that you will like the interface - but ***I would like to know if you think it is doing what it should do***. When it is 'good enough for us' I can ask the people in charge of the SDC to adopt it or do something similar :-)

---

### Post by mc4man on 2016-02-26
This is what I get from script - 
> Warning! 
This shellsript is only a  demo  for a function to be built into a program,
that is selecting the target device in a safe way to avoid overwriting     
valuable data by mistake. This simple script is not really safe.           
 Use it very carefully and only for testing! 
NAME   MODEL            FSTYPE  LABEL                    MOUNTPOINT          SIZE NAME
sda    LITEONIT LSS-24L                                                     22.4G sda
sdb    Crucial_CT500MX2                                                    465.8G sdb
&#9500;&#9472;sdb1                  vfat                             /boot/efi           200M &#9500;&#9472;sdb1
&#9500;&#9472;sdb2                  ext4                             /                 150.9G &#9500;&#9472;sdb2
&#9500;&#9472;sdb3                  ext4                                                93.1G &#9500;&#9472;sdb3
&#9492;&#9472;sdb4                  ntfs    media                    /media/doug/media  55.9G &#9492;&#9472;sdb4
sdc    MONSTER DIGITAL  iso9660 Ubuntu 14.04.4 LTS amd64                    14.9G sdc
&#9500;&#9472;sdc1                  iso9660 Ubuntu 14.04.4 LTS amd64                       1G &#9500;&#9472;sdc1
&#9492;&#9472;sdc2                  vfat    Ubuntu 14.04.4 LTS amd64                     2.2M &#9492;&#9472;sdc2
sr0    DVD-RAM UJ8DB                                                        1024M sr0
 Final checkpoint 
Do you want to restore  /dev/sdc1  to a FAT32 partition? (y/N) y
Trying to unmount partitions if mounted on the target device
umount: /dev/sdc1: not mounted
------------------------------------------------------------
1024+0 records in
1024+0 records out
1048576 bytes (1.0 MB, 1.0 MiB) copied, 0.956693 s, 1.1 MB/s
Error: Partition(s) 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64 on /dev/sdc1 have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use.  As a result, the old partition(s) will remain in use.  You should reboot now before making further changes.
Error: Partition(s) 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64 on /dev/sdc1 have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use.  As a result, the old partition(s) will remain in use.  You should reboot now before making further changes.
Error: Partition(s) 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64 on /dev/sdc1 have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use.  As a result, the old partition(s) will remain in use.  You should reboot now before making further changes.
mkfs.fat 3.0.28 (2015-05-16)
/dev/sdc11: No such file or directory
 created MSDOS partition table and FAT file system 
Model: Unknown (unknown)
Disk /dev/sdc1: 1074MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1074MB  1073MB  primary               boot

> sudo blkid
[sudo] password for doug: 
/dev/sdb1: UUID="E0DA-0C61" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="f6a0b209-b862-40fb-b065-01aff5e1555d"
/dev/sdb2: UUID="20dcab9e-a4f9-41c1-967c-4e5ff2bec646" TYPE="ext4" PARTUUID="e36425fb-4fa3-4852-8423-01952d97ccb7"
/dev/sdb3: UUID="ebbeb1c2-8431-4ab7-ac2f-99caf3e9a893" TYPE="ext4" PARTUUID="bea53c19-94b0-4ac6-b4e5-a7107c9e136d"
/dev/sdb4: LABEL="media" UUID="6F77440D3428E11F" TYPE="ntfs" PARTUUID="12a8a557-85dd-40b9-adbb-21b73e461bb3"
/dev/sda: PTUUID="74f02dea" PTTYPE="dos"
/dev/sdc1: PARTUUID="5a7359c1-01"



---

### Post by MikeMecanic on 2016-02-26
Sudodus gets my vote for President! +2 and forward to SDC team.

---

### Post by sudodus on 2016-02-26
@ mc4man,

Let me guess that you ran the script with a partition as target instead of a whole mass storage device, /dev/sdc1 instead of /dev/sdc. Otherwise I don't understand how you could manage to get that result. Anyway, good catch :-)

This is a bug in the 'main script' - but such things should not happen when the function mk_msdos is called from the SDC. It should point to the whole mass storage device, selected by the main user interface. Anyway, I should remove that bug ...

@  MikeMecanic,

I think we need to make this script more robust before we forward it to the SDC team.

[hr][/hr]
***Edit:*** Done - version 1.1 uploaded to post #13.

---

### Post by mc4man on 2016-02-26
> **sudodus said:**
> @ mc4man,

Let me guess that you ran the script with a partition as target instead of a whole mass storage device, /dev/sdc1 instead of /dev/sdc. Otherwise I don't understand how you could manage to get that result. Anyway, good catch :-)

This is a bug in the 'main script' - but such things should not happen when the function mk_msdos is called from the SDC. It should point to the whole mass storage device, selected by the main user interface. Anyway, I should remove that bug ...

@  MikeMecanic,

I'm think we need to make this script more robust before we forward it to the SDC team.
Yeah, I was telling myself to just use sdc but checking history see I did use sdc1...
(In any event the device was able to be formatted in Disks after using the wrong target.

---

### Post by sudodus on 2016-02-27
I have replaced ***restore-pendrive*** version 1.0 with version 1.1, and a third screenshot is added in post #13.

Please try this new shellscript :-)

Can it do what it should do? Is it ready for the the SDC team yet?

---

### Post by coldraven on 2016-02-27
> **mc4man said:**
> While the new method never fails it seems to create a disk that becomes difficult to format back to a plain storage device. Disks has issues, gparted also inc. totally mis reading the size. 
Maybe there is a trick to simply format the device back to let's say fat32, if so I've not found
Some various images attached, first gparted is after attempting to format in Disks, 2nd gparted is on a fresh disc never opened in Disks
Yesterday I tried to blank a working Ubuntu 15.10 64 bit install USB stick and make it into a Xubuntu 14.04 32 bit installer. After trying all the usual methods I still have had no success :(
You can add this gparted error message to yours above

---

### Post by sudodus on 2016-02-27
> **coldraven said:**
> Yesterday I tried to blank a working Ubuntu 15.10 64 bit install USB stick and make it into a Xubuntu 14.04 32 bit installer. After trying all the usual methods I still have had no success :(
You can add this gparted error message to yours above

1. To solve your current problem, you can use an option from the [mkusb wipe menu](https://help.ubuntu.com/community/mkusb/wipe)!

2. Please add your error message (as an attached file) to a new comment in the [Launchpad bug report](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1549603)

3. To help improve the Ubuntu Startup Disk Creator, please fetch the script from post #13 and ***test*** if it solves your problem :-)

---

### Post by mc4man on 2016-02-27
> **sudodus said:**
> I have replaced ***restore-pendrive*** version 1.0 with version 1.1, and a third screenshot is added in post #13.

Please try this new shellscript :-)

Can it do what it should do? Is it ready for the the SDC team yet?
Worked out just fine.

---

### Post by QDR06VV9 on 2016-02-27
@sudodus Agree with mc4man Works just fine!! Unless you had some thing more specific for me to do??
> $ /home/me/mk_msdos.sh -v
/home/me/mk_msdos.sh version 1.1

< dev/zero pv -n -s 13259218944 | dd bs=4096 of='/dev/sdh
That was a bit of time since I last did that...zeroed out a total of 16Gigs SanDisk Corp. Cruzer
Going to play some more with it today..
Regards

---

### Post by sudodus on 2016-02-27
Why did you wipe the whole device (overwrite with zeros)? Was it getting slow? Or was there some problem after the formatting with mk_msdos.sh?

---

### Post by QDR06VV9 on 2016-02-27
Because I could:D and yes it needed it, It was time..and the last time i tried the wipe disk it had saved the front portion of the drive..
But it did do what I had intended it do..The Verbose(Text) comes in handy also.

---

### Post by sudodus on 2016-02-27
Thank you :-)

We are four people that have tested this little script now. It works for us and I think it is ready for the SDC team.

---

### Post by QDR06VV9 on 2016-02-27
+1 
I Hope they take this opportunity to add to it..
Kind Regards

---

### Post by ventrical on 2016-02-27
@sudodus

see here.. [http://ubuntuforums.org/showthread.php?t=1958073&page=35&p=13447230#post13447230](http://ubuntuforums.org/showthread.php?t=1958073&page=35&p=13447230#post13447230)

---

### Post by ventrical on 2016-02-27
> **sudodus said:**
> Thank you :-)

We are four people that have tested this little script now. It works for us and I think it is ready for the SDC team.

It works just fine from mkusb 10.5.1

---

### Post by sudodus on 2016-02-27
I sent the following mail. Let us hope that Marc Deslauriers will be able to help us with this task. (He was revamping the SDC for Xenial, so he knows the code very well.)

> 
To: Marc Deslauriers, Nicholas Skaggs
Cc: "Ubuntu Quality Mailing List
From: Nio (sudodus)
Subject: Robust and user friendly SDC should also be able to restore USB drive
 for data storage
Date: Sun, 28 Feb 2016 01:08:10 +0100

Hi Marc and Nicholas,

We are discussing the new version of the Ubuntu Startup Disk Creator,
SDC, in the following thread at the Ubuntu Forums and the bug report
#1549603 at Launchpad

[http://ubuntuforums.org/showthread.php?t=2314875](http://ubuntuforums.org/showthread.php?t=2314875)

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1549603](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1549603)

We are happy that there is a robust and user friendly SDC program. So
why do we want more?

mc4man started the discussion because he is concerned that it is more
difficult to restore pendrives that have been used as cloned boot drives
(with iso9660 file systems) back to standard drives for storage and
transfer of files. And it is not straightforward to find out how to do
it. He wanted information directly available at the SDC.

There is information at the Ubuntu wiki and help pages, but not directly
available from the SDC or Disks or Gparted (or other tools available in
the Ubuntu family flavours except mkusb, which is only available via PPA).

During the discussion I suggested that it would be a good alternative to
supply a tool to do it, to repartition and reformat the pendrive. We
think the best method would be to build that tool into the SDC, and to
access it via a button in the main window. The button can have the text
'Restore a USB drive for data storage', and the target, the USB drive is
simply selected by the same box as is selectíng the target when flashing
the content of the iso file. It would be possible (but not necessary) to
let the user select a label.

So I took the bash script function mk_msdos from mkusb:

- modified it for this purpose
- wrapped it into a main program to make a verbose command line demo
program, 'restore-pendrive'

The intention was to let some people test it. Four people have tested
this demo program, and it does what we expect it should do.

*Now it is your turn to test it*

If you think that it does what it should do, we can figure out how to
use it. And I am prepared to help with what I can do.

- One alternative is to use the function mk_msdos with a minimal main
program around it (not the verbose demo program we have now), and to
call it via a system call from the SDC.

- Another and maybe better alternative is to build it into the SDC. I
guess it means that it should be translated to python, and the echo
command lines should be removed or replaced.

- Of course it is still an alternative to provide information via that
button (or another button), but if the tool is there, we need no
detailed information.

-----
$ md5sum restore-pendrive
78f8727194210ab633eaff1b4fd1f5a7  restore-pendrive
-----

Grab the attached file and run it in a bash shell :-) See the
screenshots at the following link (post #13)

[http://ubuntuforums.org/showthread.php?t=2314875&p=13446485#post13446485](http://ubuntuforums.org/showthread.php?t=2314875&p=13446485#post13446485)

Best regards
Nio

--------------
Content-Type: text/plain; charset=UTF-8;
 name="restore-pendrive"
Content-Transfer-Encoding: 7bit
Content-Disposition: attachment;
 filename="restore-pendrive"


---

### Post by sudodus on 2016-02-27
> **ventrical said:**
> It works just fine from mkusb 10.5.1

Yes, but those responsible for Ubuntu in general and the Startup Disk Creator in particular do not want mkusb. It does not comply to their standards for programs. I think they listed seven issues with it. Some of the issues are impossible to fix without re-writing the whole program.

Instead this is the way to do it - to enter the most important features into the SDC ;-)

---

### Post by sudodus on 2016-03-16
Marc Deslauriers and Nicholas Skaggs have not replied to the mail I sent more than two weeks ago (Feb 28). Nicholas will move to a new job (still at Canonical). Maybe Marc will have more time after the release of 16.04 LTS.

-o-

There is a lot of instructions that promote

```
dd if=distro.iso of=/dev/sdx
```

at the web pages of several major linux distros. And I seldom see any warning or hint how to restore the pendrive to a data storage drive with an MSDOS partition table and FAT32 file system.

I think many of us (in this forum for the developing release) think it is easy to use gparted or some other tool. So I think we have to use other channels too in order to create opinion and make something happen.

@ *mc4man*,

Can you specify in detail what ***you*** want,please!

Maybe you can give an example.

---

### Post by kansasnoob on 2016-03-16
> **sudodus said:**
> Marc Deslauriers and Nicholas Skaggs have not replied to the mail I sent more than two weeks ago (Feb 28). Nicholas will move to a new job (still at Canonical). Maybe Marc will have more time after the release of 16.04 LTS.

-o-

There is a lot of instructions that promote

```
dd if=distro.iso of=/dev/sdx
```

at the web pages of several major linux distros. And I seldom see any warning or hint how to restore the pendrive to a data storage drive with an MSDOS partition table and FAT32 file system.

I think many of us (in this forum for the developing release) think it is easy to use gparted or some other tool. So I think we have to use other channels too in order to create opinion and make something happen.

@ *mc4man*,

Can you specify in detail what ***you*** want,please!

Maybe you can give an example.

I've generally found that Gparted can't deal with flash drives where a live USB has been created using dd. To further complicate things I've not found a 100% consistent method of making the drive usable again but usually one or the other of these commands works:

```
dd if=/dev/zero of=/dev/sd# bs=1M

dd if=/dev/zero of=/dev/hdX

dd if=/dev/random of=/dev/hdX

dd if=/dev/urandom of=/dev/hdX
```

And given dd's reputation as "disk destroyer" or "data destroyer" it's just not a wise procedure to be recommended for non-technical users. I've even made mistakes in spite of being fully aware of the dangers :redface:

---

### Post by sudodus on 2016-03-16
Hi kansasnoob,

I have already built your method into [mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe). It is usually enough to wipe the first Mibibyte, with a safety belt ;-)

But it might also work to create a new partition table with gparted (not only try to create a new partition in the current partition table).

Edit: This should be possible to build into the Startup Disk Creator (usb-creator-gtk)

---

### Post by sudodus on 2016-03-16
I was adviced to file the following bug:

[https://bugs.launchpad.net/ubuntu-website-content/+bug/1558139](https://bugs.launchpad.net/ubuntu-website-content/+bug/1558139):

'***Please update** [www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)*'

If you think it would help, please mark 'affects me too' :-)

You are also welcome to write comments.

---

### Post by ventrical on 2016-03-17
> **sudodus said:**
> Marc Deslauriers and Nicholas Skaggs have not replied to the mail I sent more than two weeks ago (Feb 28). Nicholas will move to a new job (still at Canonical). Maybe Marc will have more time after the release of 16.04 LTS.



Sorry to hear this Sudodus. Perhaps I can try and e-mail Marc.

Regards..

:edit:   I e-mailed Marc at his ubuntu adress and cited your post and asked him to have a look at it. If I hear any thing I'll get back.

[http://ubuntuforums.org/showthread.php?t=2314875&page=3&p=13447253#post13447253](http://ubuntuforums.org/showthread.php?t=2314875&page=3&p=13447253#post13447253)

Regards..

---

### Post by ventrical on 2016-03-17
Pretty well end of story:

> 
Hi,
 
On 2016-03-17 12:30 PM, Dale Beaudoin wrote:
> Hi Marc,
> 
>  I am Dale Beaudoin, aka, Ventrical at [www.ubuntuforums.org]("http://www.ubuntuforums.org"). I am team captain
> of Ubuntu Development Version Testing formerly known as U+1. There is a
> discussion on some current problems with SDC for xenial xerus.
> 
> Could you please check this link out and get back to me.
> 
> [http://ubuntuforums.org/showthread.php?t=2314875&page=4&p=13456164#post13456164](http://ubuntuforums.org/showthread.php?t=2314875&page=4&p=13456164#post13456164)
> 
> [http://ubuntuforums.org/showthread.php?t=2314875&page=3&p=13447253#post13447253](http://ubuntuforums.org/showthread.php?t=2314875&page=3&p=13447253#post13447253)
> 
 
gnome-disk-utility is the appropriate tool to format a USB stick. Please file a
bug against gnome-disk-utility if it can't successfully re-format a USB stick
that has an Ubuntu image written to it.
 
Marc.



regards..

---

### Post by ventrical on 2016-03-17
> **kansasnoob said:**
> I've generally found that Gparted can't deal with flash drives where a live USB has been created using dd. To further complicate things I've not found a 100% consistent method of making the drive usable again but usually one or the other of these commands works:

And given dd's reputation as "disk destroyer" or "data destroyer" it's just not a wise procedure to be recommended for non-technical users. I've even made mistakes in spite of being fully aware of the dangers :redface:

There is always back-stepping and up-stepping involved that can bork a system. Ver. 3 USB vs MoBo with ver 2.0 or 1.1/Ver. 2.0 USB on Ver 3.0 MoBo etc..  although they are all advertised to be backward-forward compatible there is always the chance of something going wrong. It's a "keep it simple - play it safe" approach and that's why I do not think they will do any enhancement to SDC.

regards..

---

### Post by PaulW2U on 2016-03-17
> **ventrical said:**
> Pretty well end of story:
Which leaves me somewhat confused.

I can see why the Ubuntu developers did not want Unetbootin or mkusb as the default tool for creating live images as these applications have not adopted the current "look and feel" of Ubuntu. They may well be very reliable but recently I have had no problems using SDC which is also my preferred application.

Is Marc Deslauriers now saying that despite recent work on the SDC]it has now been decided that Disks (gnome-disks-utility) is what we should all be using?

If so then why is SDC still available in the Xenial repositories? :confused:

**Edit**: I took a long time post. ventrical may well have (partly) answered by question.

---

### Post by ventrical on 2016-03-17
> **sudodus said:**
> I was adviced to file the following bug:

[https://bugs.launchpad.net/ubuntu-website-content/+bug/1558139](https://bugs.launchpad.net/ubuntu-website-content/+bug/1558139):

'***Please update** [www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu")*'

If you think it would help, please mark 'affects me too' :-)

You are also welcome to write comments.

These outdated wikis are systemic. Thousands of them. I even tried to update/upgrade/edit some of them and there are just too many.

regards..

---

### Post by ventrical on 2016-03-17
> **PaulW2U said:**
> Which leaves me somewhat confused.

I can see why the Ubuntu developers did not want Unetbootin or mkusb as the default tool for creating live images as these applications have not adopted the current "look and feel" of Ubuntu. They may well be very reliable but recently I have had no problems using SDC which is also my preferred application.

Is Marc Deslauriers now saying that despite recent work on the SDC]it has now been decided that Disks (gnome-disks-utility) is what we should all be using?

If so then why is SDC still available in the Xenial repositories? :confused:

**Edit**: I took a long time post. ventrical may well have (partly) answered by question.


Yes . it is what it is. I just forwarded sudodus' msgs to marc, asked him to take a look and he replied as he did. (as which I posted here).

There has always been problems with persistence USB drives and swapping them in and out of different boxes. Also they are much too slow and IMO I think devs just do not have the time. I rarely ever use them because of this reason.

regards..

---

### Post by PaulW2U on 2016-03-17
> **ventrical said:**
> Yes . it is what it is. I just forwarded sudodus' msgs to marc, asked him to take a look and he replied as he did. (as which I posted here).
I think subscribing and commenting on bug report [https://bugs.launchpad.net/ubuntu-website-content/+bug/1558139](https://bugs.launchpad.net/ubuntu-website-content/+bug/1558139) is very relevant now. Thank you sudodus for creating the bug report. A new user to any Linux distribution not only wants but needs something that works 100% of the time otherwise they'll just move on to something that does work.

While users such as ourselves can and will use whatever means we know of to create bootable Ubuntu ISO images new or less informed users will be looking for an application that works **every** time. Marc's email leaves some doubt about which application that might be.

---

### Post by sudodus on 2016-03-17
Well, *ventrical* and *PaulW2U*,

I think Marc is saying that their preferred tool to ***format*** a USB stick is Disks alias gnome-disks.

> gnome-disk-utility is the appropriate tool to format a USB stick. Please file a
bug against gnome-disk-utility if it can't successfully re-format a USB stick
that has an Ubuntu image written to it.

I think he and the other Canonical guys still prefer the SDC to create an Ubuntu Startup Disk ;-)

And I think that the new SDC is both robust and easy to use, so I'm happy because it is a great improvement.

Since there will not be any extra button in the SDC, I think more people will come to our Ubuntu Forums. They will need our help to format pendrives (restore them to storage drives)  :-P

And I think mkusb is the best tool for that task ;-)

---

### Post by ventrical on 2016-03-17
> **sudodus said:**
> Well, *ventrical* and *PaulW2U*,

I think Marc is saying that their preferred tool to ***format*** a USB stick is Disks alias gnome-disks.



I think he and the other Canonical guys still prefer the SDC to create an Ubuntu Startup Disk ;-)

And I think that the new SDC is both robust and easy to use, so I'm happy because it is a great improvement.

Since there will not be any extra button in the SDC, I think more people will come to our Ubuntu Forums. They will need our help to format pendrives (restore them to storage drives)  :-P

And I think mkusb is the best tool for that task ;-)

+1  ;)

---

### Post by mc4man on 2016-03-17
> gnome-disk-utility is the appropriate tool to format a USB stick. Please file a
bug against gnome-disk-utility if it can't successfully re-format a USB stick
that has an Ubuntu image written to it.

Marc.
That's wrong, (Mark D). The new SDC was created knowing that gnome-disks couldn't deal with  or the new SDC was created & uploaded without really testing.
Before putting something new in that will create a significant issue that issue should be resolved.
(- I would suspect that Windows default disk management tool would likewise have problems, is that a bug in Windows?

---

### Post by PaulW2U on 2016-03-17
> **sudodus said:**
> I think Marc is saying that their preferred tool to ***format*** a USB stick is Disks alias gnome-disks.
> **sudodus said:**
> I think he and the other Canonical guys still prefer the SDC to create an Ubuntu Startup Disk ;-)
On rereading everything I think you're right. Two applications might be needed by some (new) users to create a bootable or  installable image on a USB stick. ](*,)

---

### Post by sudodus on 2016-03-17
No formatting is necessary when you clone an iso file. So only one tool is needed for that task, but another tool is needed to restore it to storage device.

Edit: And mc4man is right, when he is concerned that several people might think that their pendrive cannot be restored, so there should be an easily available tool or at least information available, where a beginner might have a fair chance to find it.

---

### Post by sudodus on 2016-03-17
I addressed this issue April 30th 2012 (in the tutorial thread about mkusb), as you can see in [this link](http://ubuntuforums.org/showthread.php?t=1958073&p=11890356#post11890356)

---

### Post by ventrical on 2016-03-17
> **mc4man said:**
> That's wrong, (Mark D). The new SDC was created knowing that gnome-disks couldn't deal with  or the new SDC was created & uploaded without really testing.
Before putting something new in that will create a significant issue that issue should be resolved.
(- I would suspect that Windows default disk management tool would likewise have problems, is that a bug in Windows?

Hi mac4man,sudodus

Here is e-mail.

"just google marc deslauriers and send e-mail to the ubuntu dot com adress."

Regards..

---

### Post by sudodus on 2016-03-17
I think we should remove the explicit mail address to save Marc from spam ;-)

---

### Post by ventrical on 2016-03-17
> **sudodus said:**
> I think we should remove the explicit mail address to save Marc from spam ;-)

Spam? Its on google for goodness sake;)

Umm I thought we are transparent here. No?

Perhaps you should e-mail him and invite him directly to the forum because there would be more clarity in that rather than me acting as a proxy.

Regards..

---

### Post by sudodus on 2016-03-17
I was thinking about bots scanning our forums for mail addresses and collecting them for spammers.

Thanks for making it harder for bots :-)

---

### Post by ventrical on 2016-03-17
> **sudodus said:**
> OK, if that address is official, an extra link to it won't make any difference. (I was thinking about bots scanning our forums for mail addresses and collecting them for spammers.)

edited out

thanks for pointers;)

regards..

---

### Post by sudodus on 2016-03-17
> **ventrical said:**
> Spam? Its on google for goodness sake;)

Umm I thought we are transparent here. No?

Perhaps you should e-mail him and invite him directly to the forum because there would be more clarity in that rather than me acting as a proxy.

Regards..

You are the original poster of this thread, ***mc4man***. I suggest that you invite Marc :-)

---

### Post by ventrical on 2016-03-17
> **sudodus said:**
> You are the original poster of this thread, ***mc4man***. I suggest that you invite Marc :-)

But you were the first to e-mail him at another link (which seems not to be working)? So perhaps we can find resolution if you personally e-mailed him your original e-mail to his ubuntu dot com adress and see what happens.

[http://ubuntuforums.org/showthread.php?t=2314875&page=3&p=13447253#post13447253](http://ubuntuforums.org/showthread.php?t=2314875&page=3&p=13447253#post13447253)

Regards..

---

### Post by sudodus on 2016-03-17
mc4man has the ball. If he passes it to me, fine.

---

### Post by ventrical on 2016-03-17
Well... if I get three nominations I'll take up the issue once again with him. Part of new UDV testing admin is to act as liason between ubuntuforums and developers.

 So give me three +1s and I'll do it for mac4man and for the the group:)

regards..

---

### Post by mc4man on 2016-03-17
Anybody can email someone they have an address to ....

I subscribed both devs who commited to SDC 0.3.0 back in early Dec. to the bug report, they can respond or not, up to them.

@sudodus - 
So is the current SDC incapable of setting a volume label to disks it creates?

---

### Post by ventrical on 2016-03-17
> **mc4man said:**
> Anybody can email someone they have an address to ....

I subscribed both devs who commited to SDC 0.3.0 back in early Dec. to the bug report, they can respond or not, up to them.

@sudodus - 
So is the current SDC incapable of setting a volume label to disks it creates?

alright ...

 I forwarded the following  link to marc D.

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1549603](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1549603)

regards..

---

### Post by ventrical on 2016-03-17
> **ventrical said:**
> Well... if I get three nominations I'll take up the issue once again with him. Part of new UDV testing admin is to act as liason between ubuntuforums and developers.

 So give me three +1s and I'll do it for mac4man and for the the group:)

regards..

:) 
 thanks for the votes of confidence :)

regards..

---

### Post by ventrical on 2016-03-17
> **mc4man said:**
> Anybody can email someone they have an address to ....

I subscribed both devs who commited to SDC 0.3.0 back in early Dec. to the bug report, they can respond or not, up to them.

@sudodus - 
So is the current SDC incapable of setting a volume label to disks it creates?

marc has added a reply to your bug. He wants to fix it and is willing to let others help him. 

 regards

---

### Post by QDR06VV9 on 2016-03-17
> **ventrical said:**
> Well... if I get three nominations I'll take up the issue once again with him. Part of new UDV testing admin is to act as liason between ubuntuforums and developers.

 So give me three +1s and I'll do it for mac4man and for the the group

regards..
Here you go then 3x+1's
:)

---

### Post by sammiev on 2016-03-17
> **runrickus said:**
> Here you go then 3x+1's
:)

Here you go then 3x+2's :)

---

### Post by sudodus on 2016-03-18
> **mc4man said:**
> Anybody can email someone they have an address to ....

I subscribed both devs who commited to SDC 0.3.0 back in early Dec. to the bug report, they can respond or not, up to them.

@sudodus - 
So is the current SDC incapable of setting a volume label to disks it creates?

Able or unable? I think the SDC clones, that is, copies each byte from the iso file to the pendrive. It does not edit anything. It would be possible to do that, but I don't think it does now. Just like the other cloning tools, it 'only' clones. I think this is good, it makes the SDC robust.

---

### Post by sudodus on 2016-03-18
> **ventrical said:**
> marc has added a reply to your bug. He wants to fix it and is willing to let others help him. 

 regards

Thanks *ventrical*, for making this happen :-)

---

### Post by ventrical on 2016-03-18
@runrickus, sammiev

Thanks you guys ;)

Regards..

---

### Post by ventrical on 2016-03-18
> **sudodus said:**
> Thanks *ventrical*, for making this happen :-)

Your welcome.
Obviously some of the mailing lists have become redundant or seconded to the point where the devs just don't read them any more. Also, some of the launchpad slices have to be brought directly to the developer. It's not like they are deliberately ignoring anyone.  It's good to see some action taken on mac4mans bug report. He has helped me a lot over the years.

regards..

---

### Post by ventrical on 2016-03-18
Just doing a back-step experiment.

I downloaded ubuntu (unity) current on a ubuntu 10.10 box and installed a persistive drive to 4GB USB and although it took a little time, it completed successfully and I am using that persistive install now.

And look how it formatted the USB.

regards..

---

### Post by mc4man on 2016-03-18
> **sudodus said:**
> Able or unable? I think the SDC clones, that is, copies each byte from the iso file to the pendrive. It does not edit anything. It would be possible to do that, but I don't think it does now. Just like the other cloning tools, it 'only' clones. I think this is good, it makes the SDC robust.
It would seem that if SDC could set a specific volume label, (not a user option),  then only those drives would eligible to be formated (from a gtk button that's only active under that circumstance.

---

### Post by sudodus on 2016-03-18
> **ventrical said:**
> Just doing a back-step experiment.

I downloaded ubuntu (unity) current on a ubuntu 10.10 box and installed a persistive drive to 4GB USB and although it took a little time, it completed successfully and I am using that persistive install now.

And look how it formatted the USB.

regards..

Have you checked if the SDC version of 10.10 works

- with 32-bit and 64-bit versions of all current Ubuntu versions?

- in UEFI as well as in BIOS mode? (With a 64-bit version the target should boot also in UEFI mode.)

It must also work ***between*** versions, architectures and boot modes (running in one of them, installing another one).

I think this mixture (and changes in the internal structure of the iso files between versions) made it hard to keep the old SDC working.

---

### Post by sudodus on 2016-03-18
> **mc4man said:**
> It would seem that if SDC could set a specific volume label, (not a user option),  then only those drives would eligible to be formated (from a gtk button that's only active under that circumstance.

Yes it would, but then we start introducing complication, and potential causes to failure with future versions of Ubuntu.

---

### Post by vasa1 on 2016-03-18
> **mc4man said:**
> I did file a bug ...
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1549603](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1549603)
The bug pointed to another [bug, #1558139]("https://bugs.launchpad.net/ubuntu-website-content/+bug/1558139"), which in turn pointed to [How to create a bootable USB stick on Ubuntu]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu"). On this page, point #4 is this:> Click 'Other' to choose the downloaded ISO file.Is there an illustration missing? The image between #3 and #4 doesn't show any clickable button (or element) titled 'Other'.

---

### Post by sudodus on 2016-03-18
I think they refer to the screenshot at/after paragraph #6: 'Other...'

---

### Post by sudodus on 2016-03-18
You can see screenshots of the old and new SDC versions at the following link

[Creating a bootable Ubuntu USB flash drive from Ubuntu](https://help.ubuntu.com/community/Installation/FromUSBStick#Install_and_run_Startup_Disk_Creator_alias_usb-creator)

Scroll a little for the screenshot of the new version. The main difference is that the part about persistence is removed.

---

### Post by ventrical on 2016-03-18
> **sudodus said:**
> Have you checked if the SDC version of 10.10 works

- with 32-bit and 64-bit versions of all current Ubuntu versions?

- in UEFI as well as in BIOS mode? (With a 64-bit version the target should boot also in UEFI mode.)

It must also work ***between*** versions, architectures and boot modes (running in one of them, installing another one).

I think this mixture (and changes in the internal structure of the iso files between versions) made it hard to keep the old SDC working.

Just the 64-bit ubuntu xenial version. Yes.. it does boot in UEFI. Of course I will have to do more testing time permitting.  But I left this here to illustrate a point to marc d. that perhaps he may be able to draw some reference point to commit a fix for current SDC.

regards..

---

### Post by sudodus on 2016-03-18
I see and agree, that it is good to step back to a point where things were working well.

What happened after that point? Was something introduced, that can be removed to make things work again? But I am afraid that things are more complicated now with UEFI and several version upgrades of syslinux.

---

### Post by ventrical on 2016-03-18
> **sudodus said:**
> I see and agree, that it is good to step back to a point where things were working well.

What happened after that point? Was something introduced, that can be removed to make things work again? But I am afraid that things are more complicated now with UEFI and several version upgrades of syslinux.

That's exactly it. It is a house keeping issue that got neglected somewhere along the way. It is also a resource issue.  Bigger projects drew more attention and smaller ones got left behind ie; ccsm and the maintenance done on them was sparse.  We have been told now since utopic that gnome-disks is the best way to create bootable USB drives. It was mostly a preference to have persistent drives and , as marc tells me, it is a huge job to put a button in current SDC with this option, even to call for format.

So we have to "shake the bushes" so to speak.

  I recall how so often people tell me that developers DO NOT visit ubuntuforums. I also notice obsolete wikis and mailing list and bug reports falling off the edge of launchpad. So sometimes we have to take it directly to the source if we want to get something done. The current setup is wanting. The QA program is isolated in many ways but I will not critisize what that group is doing. I have to assume that they are doing their best to tackle bugs. It goes back to resources. 

Then there is group participation. When Sam Spillsbury was responsible for  compiz fixes he often said that he would like some others to help him fix compiz but that they needed some experience in vertex programming and after that it sort of all went silent.  However .. if we all work together I believe that we can fix a lot of bugs. Perhaps we have to try different channels to contact the principles responsible for any specific app or group of apps. 

Now that I think of it I wonder if LXD containers or some mini virtual machine for apps could pull an earlier version program from a ppa repo to work in a current development release but then, if it was too large a program it would be silly. So it is just common sense and the nature of programming to look for the most efficient method as opposed to the most preferred one.

regards..

---

### Post by ventrical on 2016-03-18
> **sudodus said:**
> I see and agree, that it is good to step back to a point where things were working well.

What happened after that point? Was something introduced, that can be removed to make things work again? But I am afraid that things are more complicated now with UEFI and several version upgrades of syslinux.

Well.. here is the answer to that question from the current engineer responsible for that.

[URL="https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1549603/comments/18"]https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1549603/comments/18


[/URL]

---

### Post by ventrical on 2016-03-18
> **sudodus said:**
> Have you checked if the SDC version of 10.10 works

- with 32-bit and 64-bit versions of all current Ubuntu versions?

- in UEFI as well as in BIOS mode? (With a 64-bit version the target should boot also in UEFI mode.)

It must also work ***between*** versions, architectures and boot modes (running in one of them, installing another one).

I think this mixture (and changes in the internal structure of the iso files between versions) made it hard to keep the old SDC working.

Update:

1. It will not boot correctly on non-UEFI BIOS mode systems. Perhaps I'll check for 'upstart' option.
2. It does not retain persistence.  So marc is correct in his launchpad post (as are you). It could take a lot of work to fix it entirley. The newer .ISO structures have been different from past ones.

edit: Yes .. the older SDC method is useless on newer .ISOs

Regards..

---

### Post by sudodus on 2016-03-18
I'm looking forward to Marc doing what he promises in the bug report [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1549603](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1549603) comments #15-16 :-P

---

### Post by ventrical on 2016-03-18
> **sudodus said:**
> I'm looking forward to Marc doing what he promises in the bug report [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1549603](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1549603) comments #15-16 :-P

Thats about the best we can do:) Look forward ! :)

regards..

---

### Post by sudodus on 2016-03-18
We can also remind him well in time before the release of 16.04.1 LTS :-)

---

### Post by ventrical on 2016-03-18
Of course. It may take time. They still haven't fixed the 'babysitting' bug from Trusty. That being that if you leave a persistent session of SDC  while the bootloader is being installed and you do not enter PASSWORD in time it will fail. It is the worse piece of programming I have ever seen... that goes back to house keeping .. and I have a lot of my own .. some even growing legs and ready to jump out of the sink  ;)

regards..

---

### Post by ventrical on 2016-03-18
> **ventrical said:**
> That's exactly it. It is a house keeping issue that got neglected somewhere along the way. It is also a resource issue.  Bigger projects drew more attention and smaller ones got left behind ie; ccsm and the maintenance done on them was sparse. 

So we have to "shake the bushes" so to speak.
It goes back to resources. 

Then there is group participation. When Sam Spillsbury was responsible for  compiz fixes he often said that he would like some others to help him fix compiz but that they needed some experience in vertex programming and after that it sort of all went silent.

regards..

Just want to correct this blather. A major update to all components of compiz just in.

sorry for off topic..
regards..

---

### Post by ventrical on 2016-03-30
..any news on whether there has been some progress with mac4man's bug report ?

regards..

---

### Post by sudodus on 2016-03-30
I have not seen anything yet.

---

### Post by mc4man on 2016-03-30
It seems that Disk's   'Disk image Writer'  ends up with the same issue when used to create a live usb (UEFI). After creating one  then Disks can't do anything with the drive as far as formating.

---

### Post by sudodus on 2016-03-30
Disks clones the iso file, so there will be the same content in the pendrive as when it is made with the SDC, mkusb and dd. And yes, it is also the same problem. 

"A tool should be able to restore what it has tampered with, or at least link to another tool to do it"

It seems we have to wait for a solution within the Ubuntu standard tools. They don't want my solution ;-)

---

### Post by mc4man on 2016-03-30
> **sudodus said:**
> Disks clones the iso file, so there will be the same content in the pendrive as when it is made with the SDC, mkusb and dd. And yes, it is also the same problem. 

"A tool should be able to restore what it has tampered with, or at least link to another tool to do it"


From that viewpoint, which seems reasonable to me, an upstream Gnome bug on Disks seems appropriate.

---

### Post by sudodus on 2016-03-30
Maybe it would solve the problem faster, maybe not.

I think one problem is that Marc Deslauriers et. al. do not like ***mount*** and other tools that need superuser privileges. He wants to use something like

```
/usr/bin/udisks --mount /dev/sdb1
```

and if I have understood correctly, there is a bug, that he intends to squash in order for this to start working in ***gnome-disks*** also when the drive contains the partition table and file system of a cloned iso file.

---

### Post by ventrical on 2016-04-08
Bunch of updates on gnome-disk-utility and usb-creator-common/gtk.

---

### Post by sudodus on 2016-04-08
Thanks for the heads up. I will look for changes :-)

---

### Post by ventrical on 2016-04-08
udisk2 upgraded in ubuntu unity!.

Marc D. -from launchpad quote..

"As soon as I have some free time, I'll try and isolate the race that is preventing udisks2 from working correctly."

regards..

---

### Post by mc4man on 2016-04-08
> **ventrical said:**
> Bunch of updates on gnome-disk-utility and usb-creator-common/gtk.
Don't see that at all.

---

### Post by ventrical on 2016-04-08
> **mc4man said:**
> Don't see that at all.

I got it on a Mate install but Unity only upgraded  udisk2.. so I don't know what's going on.

---

### Post by ventrical on 2016-04-08
xubuntu will also only upgrade udisks2. 

 I have 4 separate installs of ubuntu (unity) on 4 separate drives and only one upgraded udisks2. My other install of Mate on a separate system niether installed usb-creator-* packages nor udisks2.

```

 ubuntu-ui-toolkit-theme ubuntu-wallpapers ubuntu-wallpapers-utopic ubuntu-wallpapers-vivid
  ubuntu-wallpapers-wily udev udisks2 unity-schemas unity-services uno-libs3 update-manager
  update-manager-core update-notifier update-notifier-common ure util-linux uuid-runtime
  vdpau-va-driver vim-common vim-tiny xbrlapi xdiagnose xfwm4 xserver-common xserver-xorg-core
  xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-intel xserver-xorg-video-radeon
  xubuntu-docs
281 upgraded, 7 newly installed, 1 to remove and 1 not upgraded.
Need to get 334 MB of archives.
After this operation, 33.2 MB disk space will be freed.
Do you want to continue? [Y/n] 

```

---

### Post by mc4man on 2016-04-08
> **ventrical said:**
> xubuntu will also only upgrade udisks2. 

 I have 4 separate installs of ubuntu (unity) on 4 separate drives and only one upgraded udisks2. My other install of Mate on a separate system niether installed usb-creator-* packages nor udisks2.

udisks2 was recently updated though likely nothing to do with this threads  issue - 
> udisks2 (2.1.7-1ubuntu1) xenial; urgency=medium

  * debian/patches/reread_parttable.patch: Reread partition table before
    wiping new partitions we just created. This helps ensure we got the device
    nodes we need from udev (and thus avoids gnome-disks crashing so much, for
    instance, when creating partitions). ([LP: #1460602]("https://bugs.launchpad.net/ubuntu/+source/udisks2/+bug/1460602"))

 -- Mathieu Trudel-Lapierre <mathieu-tl@ubuntu.com>  Fri, 01 Apr 2016 15:02:31 -0400


usb-creator-gtk was last updated on  Fri, 22 Jan 2016  & gnome-disk-utility on Mon, 26 Oct 2015

---

### Post by sudodus on 2016-04-08
I think gnome-disks uses udisks2 under the hood.

With a USB drive, that was made into a boot drive with usb-creator-gtk 0.3.2, try if you can restore the partition table to MSDOS with a FAT32 file system, which is suitable for storing files :-)

---

### Post by ventrical on 2016-04-08
> **mc4man said:**
> udisks2 was recently updated though likely nothing to do with this threads  issue - 


usb-creator-gtk was last updated on  Fri, 22 Jan 2016  & gnome-disk-utility on Mon, 26 Oct 2015

Thanks mac4man.

 I have no idea why that would update in my most recent Mate install. I apt-get, dist-upgraded a few days ago.

---

### Post by ventrical on 2016-04-08
> **sudodus said:**
> I think gnome-disks uses udisks2 under the hood.

With a USB drive, that was made into a boot drive with usb-creator-gtk 0.3.2, try if you can restore the partition table to MSDOS with a FAT32 file system, which is suitable for storing files :-)

Yep .. will try this. maybe  what mac talked about is a percursor to getting the rest of the bug squashed.

---

### Post by ventrical on 2016-04-08
> **sudodus said:**
> I think gnome-disks uses udisks2 under the hood.

With a USB drive, that was made into a boot drive with usb-creator-gtk 0.3.2, try if you can restore the partition table to MSDOS with a FAT32 file system, which is suitable for storing files :-)

ehehehe...

Actually it is very disappointing ... 

.. so the tool/app that we use as an ark to install ubuntu software is basically performing like malware atm.. at least in the sense  that a USB device cannot be restored to workable FAT32.

---

### Post by sudodus on 2016-04-08
Unfortunately they want to do it the hard way - instead of adopting tools that work. They need some kind of feedback now, so that they don't settle down thinking that things work.

---

### Post by ventrical on 2016-04-08
Actually my last message seems to be an f/p because I can move/copy files to the USB drive.

---

### Post by ventrical on 2016-04-08
> **sudodus said:**
> Unfortunately they want to do it the hard way - instead of adopting tools that work. They need some kind of feedback now, so that they don't settle down thinking that things work.

I did send that screenshot to Marc and I aksed him if there will be further work done before release day.

regards..

---

### Post by sudodus on 2016-04-08
> **ventrical said:**
> I did send that screenshot to Marc and I aksed him if there will be further work done before release day.

regards..

:-)

---

### Post by mc4man on 2016-04-08
> **ventrical said:**
> I did send that screenshot to Marc and I aksed him if there will be further work done before release day.

regards..
I'm confused as to what that screenshot is showing. The main issue is that Disks cannot format a Sdc created boot drive at all. What you've shown is something else.

---

### Post by sudodus on 2016-04-08
I tried, and managed stepwise, I thought, but then gnome-disks crashed and I was prompted to file a bug report, #1568135, 'gnome-disks failed when trying to restore a boot drive to a storage drive'.

[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1568135](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1568135)

I wrote that it is related to bug #1549603, usb-creator-gtk.

This was in a ***live session*** of the current daily iso file of Lubuntu Xenial i386, so there is no cruft from any previous versions.

---

### Post by ventrical on 2016-04-08
mac, sudodus,

 marc D has replied and asked me to file a bug. I might need some help with this.

Please take a look at the bug I filed and content.

[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1568139](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1568139)

---

### Post by ventrical on 2016-04-08
> **mc4man said:**
> I'm confused as to what that screenshot is showing. The main issue is that Disks cannot format a Sdc created boot drive at all. What you've shown is something else.

But it did just that!

And I will re-test it again.

---

### Post by ventrical on 2016-04-08
> **sudodus said:**
> I tried, and managed stepwise, I thought, but then gnome-disks crashed and I was prompted to file a bug report, #1568135, 'gnome-disks failed when trying to restore a boot drive to a storage drive'.

[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1568135](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1568135)

I wrote that it is related to bug #1549603, usb-creator-gtk.

This was in a ***live session*** of the current daily iso file of Lubuntu Xenial i386, so there is no cruft from any previous versions.

Ok... my best guesstimate as to what is happening is that the 'udisks-error-quark' is an f/p after  udisks2 is upgraded. But, after re-boot you can repeat the process and  the error will not report. However .. I think that the bug happens with each instance after a USB drive is created with  new xenial ISO... and then it will happen again. To test this I will try  again.

---

### Post by ventrical on 2016-04-08
I think there is a serious security bug because as I am using SDC once again it has failed to ask  for authentication. err That could be because I had used 'disks' in this current session but it usually never fails to ask for password.

---

### Post by ventrical on 2016-04-08
> **sudodus said:**
> I tried, and managed stepwise, I thought, but then gnome-disks crashed and I was prompted to file a bug report, #1568135, 'gnome-disks failed when trying to restore a boot drive to a storage drive'.

[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1568135](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1568135)

I wrote that it is related to bug #1549603, usb-creator-gtk.

This was in a ***live session*** of the current daily iso file of Lubuntu Xenial i386, so there is no cruft from any previous versions.

Got it !!!

  The error comes up when you try to copy a file to the pressumably re-formated FAT32 partiton.

---

### Post by ventrical on 2016-04-08
> **mc4man said:**
> I'm confused as to what that screenshot is showing. The main issue is that Disks cannot format a Sdc created boot drive at all. What you've shown is something else.

What is happening here is that it will appear that the USB  is formatted to FAT32 ... and then when you try to copy a file to the newly formated/created partiton the  udisk-error-quark will pop up. However ..  normal files can be copied to the USB disk that has been formatted. So I think the udisk-quark flag is an false positive.

---

### Post by sudodus on 2016-04-08
Gnome-disks can write a partition table. But it fails to create the FAT32 file system. gparted and mkusb can do it, so yes, gnome-disks is buggy.

I agree that one problem is that it tries to do things without explicit superuser permissions (fiddling with pkexec?)

---

### Post by ventrical on 2016-04-08
> **sudodus said:**
> Gnome-disks can write a partition table. But it fails to create the FAT32 file system. gparted and mkusb can do it, so yes, gnome-disks is buggy.

I agree that one problem is that it tries to do things without explicit superuser permissions (fiddling with pkexec?)

Haven't touched it. This is scary stuff. Started happening after udisks2 upgrade .. but it could be deeper than that.

---

### Post by ventrical on 2016-04-08
> **sudodus said:**
> Gnome-disks can write a partition table. But it fails to create the FAT32 file system.


ok.. understood about FAT32 file system.

---

### Post by sudodus on 2016-04-08
I did not mean that you are fiddling with pkexec. I meant that Marc D. and his colleagues do :-P

---

### Post by mc4man on 2016-04-08
> **sudodus said:**
> Gnome-disks can write a partition table. But it fails to create the FAT32 file system. gparted and mkusb can do it, so yes, gnome-disks is buggy.

I agree that one problem is that it tries to do things without explicit superuser permissions (fiddling with pkexec?)
What option is that?
Here I see 2 options, delete & format.. Neither of those can do anything.

---

### Post by sudodus on 2016-04-08
I edit the partition table (create an MSDOS or GUID partiiton table) at the top. I edit a partition and try to edit its file system below the graph of the 'volumes'. See the attachment.

---

### Post by ventrical on 2016-04-08
> **sudodus said:**
> I did not mean that you are fiddling with pkexec. I meant that Marc D. and his colleagues do :-P

ahhha hahaha :) 

interesting...;)

uh .. but there was this authentication  ghost bug .. that if  you left  the authentication window unattended it would fail the install and I am not sure if they had fixed that bug . Some of these bugs are like cockroaches. They carry these little pods with them and when you squash them they release the pod (eggs) with  several brood in tow.;)

---

### Post by ventrical on 2016-04-08
> **mc4man said:**
> What option is that?
Here I see 2 options, delete & format.. Neither of those can do anything.

A reminder of exactly why we are here in this forum.

---

### Post by mc4man on 2016-04-08
> **sudodus said:**
> I edit the partition table (create an MSDOS or GUID partiiton table) at the top. I edit a partition and try to edit its file system below the graph of the 'volumes'. See the attachment.
Here's there is nothing at the top as far as edit (scr.3), there is below,  though it, (the input box & drop down appear 'blank', I've got to scroll way down. 
scr. 1

And as far as a Sdc created one,  - you'd try this on both partitions?
scr.2 highlight on Efi part.

---

### Post by sudodus on 2016-04-08
Yes the 'Format Disk' option that you see in attachment #3 (in post #121).

I have tried with Lubuntu i386 - it looks slightly different from yours, I guess you have an amd64 system.

---

### Post by mc4man on 2016-04-08
> **sudodus said:**
> Yes the 'Format Disk' option that you see in attachment #3 (in post #121).

I have tried with Lubuntu i386 - it looks slightly different from yours, I guess you have an amd64 system.

Ok, I was able to turn that drive back to FAT with Disks, no errors or crashes, no problems writing to. But the method is too obscure to be considered for general use.

---

### Post by mc4man on 2016-04-08
So here it is bottom to top, ie.
In bottom highlight each of the 2 partitions in turn > click on that config icon > edit partition > click on drop down > scroll down & pick one of the Windows FAT32, here used 0x0b. Then back to top > hamburger menu > Format Disk.. > 
If Mbr/Dos is picked it ends up unallocated anyway so picked "No Partitioning" > when done >  then picked (FAT) & all is ok

Edit: So I don't think the specific picks above matter, it just the process which is - 
1. Change both partitions
2. Format the disk
3. Format (partition) the disk

---

### Post by ventrical on 2016-04-08
I think the general trend is towards sufficiency and not much detail in the GUI when it comes to functionality. One would think that , since  these methods are how we install and distribute ubuntu to other machines, that there would be more traditional ubuntu  guides, buttons and whistles to help us get along. 

From a programming perspective when considering efficiency, some might consider these apps masterpieces.

regards..

---

### Post by sudodus on 2016-04-13
Second workaround: gnome-disks works if ***wiping the whole device*** (in the format menu) before creating the partition and file system. But this is very slow.

It should be enough to wipe the first megabyte (actually mibibyte 1024x1024 bytes) which takes less than 1 second compared to 6-16 minutes to wipe the whole device in typical 4 GB pendrives. Wiping the whole device is also causing unnecessary wear of the flash hardware.

It is possible to do it stepwise. First the partition is created and in the next step the file system.

The tools are there but the internal work flow is buggy. Average users will give up long before they have explored all the alternatives.

-o-

Third workaround: It works with ***root privileges***, but I guess this is not what the developers want ;-)

```
sudo -H gnome-disks
```

First 'Format disk' to create a new partition table, then 'Create partition in unallocated place' at the plus sign.

This works for me in the current Lubuntu Xenial i386 daily iso file.

---

### Post by sudodus on 2016-04-16
I discovered another bug in gnome-disks, which is intended for restoring drives to mass storage devices.

It is straight-forward to install from a compressed image file from [http://phillw.net/isos/linux-tools/uefi-n-bios/](http://phillw.net/isos/linux-tools/uefi-n-bios/) with mkusb or mkusb-nox. I tried in Lubuntu Xenial daily to restore disk image with gnome-disks but it considered the size to be 3.5 GB, when it was 12 GB, so the image was truncated, Bug #1571255

See this link: [gnome-disks truncates a huge image when restoring to a drive from xz-compressed image file](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1571255)

Please mark 'affects me too' if it does :-P

-o-

***Edit: ***This bug affects Lubuntu Xenial i386 but not amd64.

---

### Post by jerrylamos on 2016-04-16
> **MikeMecanic said:**
> .  ...Every time I do a fresh install, I always pass by *Try Ubuntu* and search Gparted in Dash to delete Ubuntu partitions.  That way, I always do a fresh install on an empty hard drive disk.

Cheers,

I've been on Ubuntu running (or trying to) development starting with Dapper Drake.

Typically I may have on the hard/ssd disk at least 4 partitions, two to alternate test iso's, one that works i.e. 14.04, and an archive with saved files ...
Therefore I use the format in the install process since I'm installing on a partition and don't want to clobber the other three.

Lately the native hard/ssd drive has Windows 10 on it so I can help my wife who uses commercial software not available on linux.

All my testing is done booting a USB SSD drive runs just fine thanks.  This is on a desktop, a 15" laptop, and a 13" laptop all three with the same setup.

And yes I install gparted as part of my setup exec.  BTW I do an install every few weeks looking for bugs and manual updates most days.

---

### Post by mc4man on 2016-04-25
Have also noticed if unity8 (mediasource.service) is installed then boot usb's can be an issue formatting as the service is busy on them.
Eventually it either releases or can be worked thru, & unity8 currently is worthless anyway

---

