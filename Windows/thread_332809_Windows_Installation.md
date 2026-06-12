---
title: "Windows Installation"
date: 2007-01-06
forum: Windows
---

### Post by Xyem on 2007-01-06
OK ladies and gentlemen, here is my story.

I recently acquired a USB 2.5" HDD enclosure. I proceeded to steal my ( 6GB ) harddrive from my laptop ( Kitty ) and put it in the enclosure. After deleting the Linux partitions from it and formatted it as FAT32 in the Windows disk management thing, I was away.

A problem first surfaced when I plugged in into Windows XP ( on Panther ). I could not transfer a 170MB file to the USB drive. It would claim that the file could not be found and it would be ejected. Fudge. After that it makes the "bong" noise to indicate new hardware has been found and shortly after the lower one to denote it has been ejected, without even mounting any partitions. *sigh* I booted into Ubuntu 6.06 and I had some issues where Ubuntu could not mount it or create the nodes in '/dev'. After unplugging and replugging it in a few times, it saw it and made sdb and I tried to repartition it in Gparted. It didn't like that and came up with some errors. God damn it.

I eventually plugged the drive in via IDE on Dragon and formatted it there, all was fine. I then put it back in its enclosure and copied a 256MB file ( created with 'dd' ) to it. Here it worked fine. So after a bit more messing, still unable to copy the other files in Windows, I decide to try Windows 2000. And here we get to the reason for my post.

During the Windows installation, it claims all the existing partitions are unformatted or damaged. There is some unallocated space so I go ahead and create a 30GB partition there. It says "the partition is larger than 2048MB so FAT32 will be used". I am fine with this so I say ok. I get to the formatting screen. To my horror in the corner it says "formatting 120000MB". There is only one partition on Panther that large and that is my main partition with XP on it! So despite the fact I *definately* ( I even rebooted and did it again ) chose the new partition, it tried to format my existing C: drive! Luckily I pressed reboot quick enough to prevent it from doing anything, otherwise, my girlfriend would have been very unhappy ( she has all her things on Panther ).

Windows 2000 has lost a lot of points due to this. Is it so hard to install to the partition I tell you too? Grr

And why is it so hard to get a USB drive to work properly? :(

---

### Post by smoker on 2007-01-06
can i ask how you are powering the 2.5 drive, i don't think you'll be able to power it effectively from the usb connector, so try an external power source if you can.

not sure what you mean by 'windows xp (on panther)' could you elaborate? also 'IDE on Dragon'?

with your windows install, i believe any partitions windows can't read, it will say is damaged or unformatted. you may find it easier to install if you create a fat32 or ntfs partition before trying the install, you can do this with 'gparted boot disk' i believe, available from sourceforge.net

best of luck

---

### Post by FurryNemesis on 2007-01-06
I think that's what he's called his partitions. Am I right?

Anyway, try the Ultimate Boot CD for repartitioning. [http://www.ultimatebootcd.com](http://www.ultimatebootcd.com)

---

### Post by Xyem on 2007-01-06
> not sure what you mean by 'windows xp (on panther)' could you elaborate? also 'IDE on Dragon'?

Oh sorry, I have 9 computers and they all are named ( Panther, Dragon, Mouse, Kitty, Rhino, Hippo, Moth, Snail and Worm )

> with your windows install, i believe any partitions windows can't read, it will say is damaged or unformatted. you may find it easier to install if you create a fat32 or ntfs partition before trying the install

I created a FAT32 partition before I tried the second time in PartitionMagic and it said **that** was unformatted or damaged. So I am very confused. I think it *may* be because Windows 2000 cannot read that far into the disc ( 137GB limit and the partition starts from 120GB and is 30GB large so it ends at 150GB ).

In other news, regarding the USB drive. It works perfectly fine in Windows 2000 ( on Dragon ). I can copy files over to it perfectly with no problems at all. I have a theory that my Windows XP installation ( on Panther ) is borked. It does some rather strange things, for example, I cannot play DVDs in it, copying large files to my USB drive fails, harddrive "fails" ( Windows freezes and then on reboot it claims that the drive is unbootable, a power cycle solves it ) and just this evening it changed to a black screen and would not respond at all. I think I may reinstall XP ( trust me, I would rather not.. I hate Windows but my gaming and hardware ( SLI in Panther ) require it. :( )

Any thoughts on this are appreciated.

---

### Post by smoker on 2007-01-06
might be worthwhile downloading and running diagnostics from your hard drive manufacturers website, at least this will assure you it is not a hard drive fault if nothing else.

i think there are such utilities on the boot disk suggested by furrynemisis above, though you may find out for sure at the link supplied.

---

### Post by Xyem on 2007-01-06
I don't think it is an issue with the drive itself as it works fine under Linux and Windows 2000 ( at least on Dragon ). fsck.vfat didn't return any errors when I ran it earlier.

I think if it is anything, it is an issue with Panther herself, as I seem to only be having issues on her. For example, as I said before when XP recognises it and then ejects it, it seems to only mount them again if I plug it into a different USB port. Under Ubuntu I have to unplug it and plug it back in about 3 or 4 times before it gets nodes created in '/dev' which makes me think it is not a Windows specific issue.

I shall find out the manufacturer of the drive and see if they do have any diagnostic software, in case it comes up with something.
On another note, which may be of use, I download a tool for Windows called "SwissKnife" which is a partition manager. Initially, if I selected my USB drive, it would cause it to crash. The solution was to delete the existing partition in disk management..

EDIT:
Actually, I just had a thought. Before the drive was formatted to become my USB drive ( it was originally in my laptop, Kitty ), Xubuntu was installed on it. GRUB would have been installed to the MBR. Is it possible, at all, that the Linux bootloader being present in the MBR is causing this strange behaviour on Panther? Though it works fine on Dragon ( in both Windows 2000 and Ubuntu ) so maybe this is not that case. It seems to be hard to isolate the core problem. Which really has nothing to do with the title of this thread so perhaps I should ask this thread to be renamed?

---

### Post by smoker on 2007-01-06
it may be a possibility - just as with the right app, some data can be recovered from a reformatted drive, - that a trace of the previous mbr, ie, grub, before format, could be causing confusion.

with manufacturers diagnostics, there is also usually an option of overwriting a drive with zeros, or something akin to a 'low level format', and this should presumably destroy any traces of previous data on the drive.

there is also an app called 'boot n' nuke' which will destroy any remnants of data on a drive, available here: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by Xyem on 2007-01-06
> can i ask how you are powering the 2.5 drive, i don't think you'll be able to power it effectively from the usb connector, so try an external power source if you can.

Sorry, I missed answering this question. The cable comes out of the enclosure and ends in two USB connectors where the second one is for additional power ( if required ). I get the same problem if I have both or just one plugged in.

> with manufacturers diagnostics, there is also usually an option of overwriting a drive with zeros, or something akin to a 'low level format', and this should presumably destroy any traces of previous data on the drive.

Would 'dd if=/dev/zero of=/dev/sdX' not do the same thing? ( Obviously done in Linux, heh )

---

### Post by smoker on 2007-01-06
> The cable comes out of the enclosure and ends in two USB connectors where the second one is for additional power ( if required ). I get the same problem if I have both or just one plugged in.

drives can be pretty demanding of power, especially when first spinning up to speed. i've made extensions before to power drives straight from the powersupply (ran the extension out a pci blanking plate at the back of the computer. has your enclosure got a power connector though?

> Would 'dd if=/dev/zero of=/dev/sdX' not do the same thing? ( Obviously done in Linux, heh )

i've never actually used this command, the reason i prefer manufacturer diagnostics is basically because they are designed to work specifically for their product, so therefore, presumably, should be better at the task required. but i am sure, though this is my way, there are many other effective options available.

---

### Post by Xyem on 2007-01-06
> has your enclosure got a power connector though?

Nope, just that single USB cable.

I just downloaded [dd for Windows]("http://www.chrysocome.net/dd") and basically ran the command I posted earlier. It ran fine except for one problem which it emitted at the end. This is the command and output..
> dd bs=1M --size --progress if=/dev/zero of=\\?\Device\Harddisk3\DR9
> rawwrite dd for windows version 0.4beta5.
Written by John Newbigin <jn@it.swin.edu.au>
This program is covered by the GPL.  See copying.txt for details
6,007,291,904Error writing file: 1117 The request could not be performed because of an I/O device error
6,007,291,904
5730+0 records in
5729+0 records out

Strangely enough, the drive has not been "zeroed".. I can still access it fine!

---

### Post by smoker on 2007-01-06
hi, Xyem,

i noticed that this is a beta, are you sure it will do in windows what it can in linux?

---

### Post by Xyem on 2007-01-07
From what it "allows" me to do, I would have thought so. I am thinking it failed because the drive was mounted at J: and I don't know how to unmount it without it being lost completely ( I don't know how Windows mounts drives and partitions and such ). I will be booting into Ubuntu later and doing it properly in an OS where *I* have the power ;)

---

