---
title: "Alpha 2 ISO file too big"
date: 2012-02-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zeroandone on 2012-02-10
The installation ISO file is too big to fit in a CD, why?

[http://cdimage.ubuntu.com/releases/precise/alpha-2/](http://cdimage.ubuntu.com/releases/precise/alpha-2/)

---

### Post by prusswan on 2012-02-10
It just means there is too much content in Pangolin compared to past editions, and this has been known for quite some time.

---

### Post by zeroandone on 2012-02-10
Then how do you install Alpha 2 from scratch?

---

### Post by andrek on 2012-02-10
Use a dvd-r / dvd-rw disc or an usb stick.

---

### Post by zeroandone on 2012-02-10
The CD image file is actually only about 6MB bigger than a standard CD capacity, I wish the developer could have squeezed the size a bit more.

---

### Post by prusswan on 2012-02-10
There's also the possibilty of upgrading from a previous edition, but that's purely academic

---

### Post by xyzzyman on 2012-02-10
> **zeroandone said:**
> The CD image file is actually only about 6MB bigger than a standard CD capacity, I wish the developer could have squeezed the size a bit more.

Alpha 2 wasn't a special build, it was just a milestone snapshot of where the daily was on that day. The file size issue is noted: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/).

Optimizations aren't done until much later in the development process as any done now will just be undone the very next day probably.

---

### Post by OGpmpdog on 2012-02-10
> **andrek said:**
> Use a dvd-r / dvd-rw disc or an usb stick.

+1, CD Medium is still used for burning??:D

I was reluctant to use USB stick for installing Ubuntu - now, I can't ever go back to DVD-R medium:P

---

### Post by oldfred on 2012-02-10
I used to use USB and do occassionly, but now use hard drive to install to another drive or to a 16GB flash drive (not the other way around).

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

may need this for some 
insmod iso9660

---

### Post by jerrylamos on 2012-02-10
> **zeroandone said:**
> Then how do you install Alpha 2 from scratch?

Running development level unstable software will lead you into learning a good bit of linux.

Starting with your question,

First you'll need at least two partitions on the hard drive plus swap.  I usually have 4 or more.  I use gparted.  Probably have to do a:

sudo apt-get install gparted

Warning, gparted is very powerful, better have all your data backed up.

Install something stable example Lucid Lynx LTS 10.04.3, or if you prefer unity, oneiric ocelot 11.10

Create a folder to put the precise pangolin .iso in, for example I do
sudo mkdir /boot/iso

Move the .iso into it.  Better not have more than one copy of the .iso on the partition. 

sudo chmod 666 /boot/iso/precise-desktop-i386.iso

You might want to install zsync for updating the .iso.  I put an exec in the same folder, create with leafpad or gedit.  I named mine zsyn  

```
#!/bin/bash
sudo zsync [http://cdimage.ubuntu.com/lubuntu/daily-live/current/precise-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/lubuntu/daily-live/current/precise-desktop-i386.iso.zsync)
echo "checksums match?"
read temp
sudo chmod 666 *.iso
exit 0

sudo chmod 777 zsyn
```

Run that for .iso updates.  The http:// is set for lubuntu, change the http for ubuntu or xubutu or whatever you want.

Next do a 
sudo gedit /etc/40_custom

and add the following as edited for your setup.  Do not change the lines that are already there.

```
menuentry "Pangolin ISO sda1" {
set isofile="/boot/iso/precise-desktop-i386.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
```

Then do 
sudo update-grub

and reboot.  You should get a grub menu choice "Pangolin ISO sda1" or whatever you called it.

That boots the .iso directly with no CD, no DVD, no USB, and .iso file size limit is set by your partition size (I tend to use 10 GB.)

Now if this all works, the live precise pangolin comes up and runs, you can do an install.

First open a terminal then do df

You should get a bunch of lines including, in part,

/dev/sda1          ....  isofile

or whatever /dev the isofile turns up as.  Issue:

sudo umount -r -l /dev/sda1

whatever your device is.

You can then with your live do an install onto the hard drive, having made the partition ahead of time with gparted.  Choose the "Something Else" option and make sure you've selected the right partition....

I've done this procedure several times of late.  I've got a netbook, a notebook. and a tower I use for testing.  Much faster to boot the .iso from the hard drive than write a CD or DVD or USB then boot from the slower medium.  Now when I do get a .iso I like, I will make a copy of it. 

Good learning & good luck,

Jerry

---

### Post by effenberg0x0 on 2012-02-10
I think this was mentioned a couple times here, but it's important to reinforce that controlling the ISO size of an unfinished product is really hard and the extra work wouldn't pay off. As Ubuntu PP reaches the end of it's development cycle, the work to make it fit a desired ISO size will be done. Right now it's just not important.

Regards,
Effenberg

---

### Post by SemiExpert on 2012-02-10
I thought it was a matter of policy that the former "CD Image" of 12.04 was going to substantially exceed the capacity of a CD disc?

---

### Post by effenberg0x0 on 2012-02-10
I have downloaded OpenSUSE 4.7GB DVD today so, I am in the group of people that don't care about more or less 50MB. 

It has been said that the ISO would grow but would not exceed 750MB (can't find the thread). But I wouldn't sign my name under it. 

Anyway, right now, in the development phase, it can easily get to be much larger than that and no one will waste a minute trying to make it smaller. It wouldn't make sense to waste time on it.

Regards,
Effenberg

---

### Post by SemiExpert on 2012-02-10
> **effenberg0x0 said:**
>  

It has been said that the ISO would grow but would not exceed 750MB (can't find the thread). But I wouldn't sign my name under it. 



 Actually, that's kind of the issue and it hasn't been clarified recently.

---

### Post by cariboo on 2012-02-10
I don't know about other parts of the world, but where I live in Western Canada, it's almost impossible to find burnable cd-roms at a reasonable price if at all. a 100 DVD-R spindle sells around here for $10-$12, whereas if you can find them, the same size cd-rom spindle runs $25-$35.

---

### Post by uRock on 2012-02-10
> **cariboo907 said:**
> I don't know about other parts of the world, but where I live in Western Canada, it's almost impossible to find burnable cd-roms at a reasonable price if at all. a 100 DVD-R spindle sells around here for $10-$12, whereas if you can find them, the same size cd-rom spindle runs $25-$35.

I am jealous. Still the other way around here.

Isn't the ISO normally oversized around this time in the release cycle?

---

### Post by cariboo on 2012-02-10
> **uRock said:**
> I am jealous. Still the other way around here.

Isn't the ISO normally oversized around this time in the release cycle?

Yes, but that doesn't stop people from complaining. :)

---

### Post by jerrylamos on 2012-02-10
> **cariboo907 said:**
> Yes, but that doesn't stop people from complaining. :)

In particular this subject and solutions have been covered in a number of threads in this forum.  Some people prefer to post first before looking.

As in my post #10 of this thread, you don't need a CD or a DVD or a USB stick to boot and install from a ubuntu .iso file.  I did that on this one here, actually a left over laptop 2.5" hard drive in a 10$ case plugged in to the USB port.  I've a couple notebooks that won't run a USB hard drive so I just carve out a test partition on the hard drive.

I've installed media-less precise pangolin on two  notebooks as well, living a little dangerously because of the Windoze...7 on the hard drive.  I hardly run Windoze but my wife does because of proprietary web software which does not run on linux.

Yes it requires a bit of linux & ubuntu work, but in development cycle of unstable ubuntu release expect to learn a lot from perusing the posts and trying and crashing.

Come release time we'll see what ubuntu development decides to do.  

There's always a possibility a minimum CD plus internet download of the rest.

Jerry

---

### Post by cariboo on 2012-02-10
> **jerrylamos said:**
> 
There's always a possibility a minimum CD plus internet download of the rest.

Jerry

That option has been available since at least Hardy. This [page]("https://help.ubuntu.com/community/Installation/MinimalCD") lists the available mini.iso's

---

### Post by philinux on 2012-02-11
> **SemiExpert said:**
> Actually, that's kind of the issue and it hasn't been clarified recently.

Fairly recently. [http://ubuntuforums.org/showpost.php?p=11431984&postcount=11](http://ubuntuforums.org/showpost.php?p=11431984&postcount=11)

---

### Post by dino99 on 2012-02-11
the mini.iso way:

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/mini.iso)

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/mini.iso)

select 32 (first link) or 64 bits (lastest link) mini image installation: very small sized image :)

---

### Post by dcstar on 2012-02-13
> **cariboo907 said:**
> Yes, but that doesn't stop people from complaining. :)

Almost a good way of preventing people that should not be using **Alpha software** from inappropriately installing it.

Is it time for anyone downloading Alpha releases to "sign" something saying they will not use it for anything but functionality and bug testing?

---

### Post by Gregory Lee on 2012-02-13
I tried putting the alpha 2 ISO on two different USB sticks, but I couldn't get my computer to boot from either one.  Then I burned the ISO file to a DVD+R, and after a few false starts, that worked to install 12.04.

I'm not saying USB won't work -- just that it didn't work for me.

I don't really know why it's important to have multiple partitions for installation, but I was not able to create more than one partition aside from swap during installation.  After 12.04 was installed, I adjusted the partitioning with the GParted that was on the live system I had from rebooting from the DVD with the alpha 2 ISO image.

---

### Post by andrek on 2012-02-13
Well "putting" as "copying" the .iso file onto an usb stick will never work - you need to use a special tool to do that. If you want to do that on Windows - use [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) . Ubuntu has such tool included - usb-creator (Startup Disc Creator).

---

### Post by Zaaark on 2012-02-13
Wha-whaat? Is someone still using CD/DVD disks and drives? Huh... I haven't had any cd-drives in my PC's for like half a decade..

---

### Post by Gregory Lee on 2012-02-13
> **andrek said:**
> Well "putting" as "copying" the .iso file onto an usb stick will never work - you need to use a special tool to do that. If you want to do that on Windows - use [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) ..
I used the pendrive program which was recommended in the Ubuntu documentation.

---

### Post by IanW on 2012-02-13
> **andrek said:**
> Well "putting" as "copying" the .iso file onto an usb stick will never work - you need to use a special tool to do that. If you want to do that on Windows - use [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) . Ubuntu has such tool included - usb-creator (Startup Disc Creator).

Actually, you _can_ "copy" the .iso file directly to a properly formatted USB stick.
Oneiric & Precise builds are  hybrid .iso images specifically designed to do exactly this.

See [this thread]("http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid") for details.

---

### Post by kevpan815 on 2012-02-13
> **zeroandone said:**
> The installation ISO file is too big to fit in a CD, why?

[http://cdimage.ubuntu.com/releases/precise/alpha-2/](http://cdimage.ubuntu.com/releases/precise/alpha-2/)

As Cariboo907 recently stated Alpha 1 and Alpha 2 will sometimes be Over Sized, not to mention the fact that the new limit is 750 MB's, so as a result you will need to use either a DVD, A USB Flash Drive, or a Virtual Machine to test Ubuntu 12.04. I am currently using Virtual Box on my 2010 Apple Mac Mini running Mac OS X Lion Server Edition 10.7.3 as the host.

P.S. Virtual Box is a free download @ [http://www.virtualbox.com/](http://www.virtualbox.com/)

---

### Post by jerrylamos on 2012-02-13
> **kevpan815 said:**
> As Cariboo907 recently stated Alpha 1 and Alpha 2 will sometimes be Over Sized, not to mention the fact that the new limit is 750 MB's, so as a result you will need to use either a DVD, A USB Flash Drive, or a Virtual Machine to test Ubuntu 12.04. I am currently using Virtual Box on my 2010 Apple Mac Mini running Mac OS X Lion Server Edition 10.7.3 as the host.

P.S. Virtual Box is a free download @ [http://www.virtualbox.com/](http://www.virtualbox.com/)

I just download the .iso onto the hard drive and boot it directly.as described in my post #10 in this forum.  No CD, DVD, USB, or virtual machine required.

Just downloaded the pangolin mini.iso on my IBM Thinkpad T40, booted it directly from the hard disk, installed, and booted.  Now I don't recommend mini because of the "do it yourself" selection of packages...

I think there's something called "tasksel" but I don't know what it is.

Jerry



Jerry

---

### Post by cariboo on 2012-02-13
@jerrylamos, have a look [here]("https://help.ubuntu.com/community/Tasksel") for more info on tasksel.

---

### Post by jerrylamos on 2012-02-14
> **cariboo907 said:**
> @jerrylamos, have a look [here]("https://help.ubuntu.com/community/Tasksel") for more info on tasksel.
I guess I did that without realizing.  There was a window as in the community writeup, I chose print server samba server lubuntu desktop.

The lubuntu works, haven't tried the others. Since then I've added firefox, leafpad, synaptic.  Why synaptic?? I don't know how to ask apt-get for the names of packages, while synaptic does give a brief description and a list.

There's very little in system tools and accessories.  I'll try to add as I need to.

precise pangolin  mini iso install was slow loading packages over the internet but certainly gets around the too big - the file is 24.1 MB and would fit on a diskette even.

Jerry

---

### Post by kurt18947 on 2012-02-14
> **Zaaark said:**
> Wha-whaat? Is someone still using CD/DVD disks and drives? Huh... I haven't had any cd-drives in my PC's for like half a decade..
Some do.  For example, I like see what other distros are up to.  Which is cheaper, 6 DVDs or 6 USB sticks?  No need to have an internal DVD drive, a USB DVD drive works just fine.  Another issue with bootable USB sticks is that not all BIOSs will recognize them.  I have a fairly new MoBo (Award modular BIOS) that will not boot from a USB stick unless that stick is formatted FAT32 with Windows, formatting with Gparted or the disk utility in Ubuntu will not work.  This is true of factory formats as well.  I have a decade old Thinkpad that will boot just fine from a CD/DVD, no way from a bootable USB. So yeah, optical drives still have a place.  They're slower, there's no way to enable persistence but sometimes they're the best choice.

---

### Post by nm_geo on 2012-02-14
> **IanW said:**
> Actually, you _can_ "copy" the .iso file directly to a properly formatted USB stick.
Oneiric & Precise builds are hybrid .iso images specifically designed to do exactly this.
 
See [this thread]("http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid") for details.
 
+1 
 
And the dd method does work I have used it since Oneiric works on Live and Alternate 32bit and 64bit.  I recently started using it to make the mini.iso .. Fast and slick bootable USB.

---

