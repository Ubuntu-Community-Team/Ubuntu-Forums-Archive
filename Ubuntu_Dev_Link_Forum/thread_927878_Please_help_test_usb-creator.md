---
title: "Please help test usb-creator"
date: 2008-09-23
forum: Ubuntu Dev Link Forum
---

### Post by castrojo on 2008-09-23
Evan has asked for a call for testing for usb-creator. The mail hasn't hit the archive yet so I am posting it here:

With beta freeze quickly approaching, I have been trying to iron out
the remaining issues in usb-creator, but there have been very few bug
reports to date.  If you have a USB stick that you're not using for
important work and have a few moments, I would greatly appreciate it
if you installed the usb-creator package (currently at 0.1.4) and
tested it with an Ubuntu or Kubuntu Desktop CD or ISO file.

Again, I'd like to stress that you should only run this on a disk that
you have or do not need backups of.

Please file any bugs on the source package
([http://launchpad.net/ubuntu/+source/usb-creator/+filebug](http://launchpad.net/ubuntu/+source/usb-creator/+filebug))

---

### Post by Ubuntiac on 2008-09-23
I'm not seeing the package...

Do you need to be using Intrepid for this? Ironically I'm not on Intrepid yet as my laptop has no CD drive, making it hard to install the fresh ISO's.

Catch 22.:roll:

---

### Post by FRnunurs on 2008-09-23
Hi whiprush,

Thanks for the job, this will perfectly fits our needs : We are currently trying to make an Ubuntu-based USB distro for all students of our campus (not only computing/IT students).
If the package is stable enough, I hope to be one of the first to adapt it :-). In any case, count on us to provide you support and feedback on it.

I'll start to test it ASAP.

kind regards.

FRnunurs / B.V
student , member of UTC-LUG
UTC, IT School - France

---

### Post by phoenix3051 on 2008-09-24
Where can I find this package? I'm running Ibex and Hardy but haven't managed to find it yet, is there a PPA?

Regards,
P.

---

### Post by FRnunurs on 2008-09-25
> **phoenix3051 said:**
> Where can I find this package? I'm running Ibex and Hardy but haven't managed to find it yet, is there a PPA?

Regards,
P.

You need to register in launchpad ( [http://launchpad.net/ubuntu/](http://launchpad.net/ubuntu/) )

Usb-creator topic is here : [http://launchpad.net/ubuntu/+source/usb-creator/+filebug](http://launchpad.net/ubuntu/+source/usb-creator/+filebug) (check 1st post)

Once logged on the site, you can get release & sources in the "overview" section.

;)

---

### Post by castrojo on 2008-09-25
The package in Intrepid is "usb-creator"

---

### Post by MentalNotes on 2008-09-27
Works well for me. I used usb-creator to put Hardy on to my 4GB Corsair Flash Voyager. I'm posting using it now.

---

### Post by evan d on 2008-09-28
I've built usb-creator 0.1.7 for Hardy in my PPA for those of you who are not running Intrepid yet:

[http://launchpadlibrarian.net/18023045/usb-creator_0.1.7%7Eppa1_all.deb](http://launchpadlibrarian.net/18023045/usb-creator_0.1.7%7Eppa1_all.deb)

Please remember that usb-creator is still beta software and therefore you should back up your USB disk before using it with this application.

Again, please post any issues you find in new bug reports ([http://launchpad.net/ubuntu/+source/usb-creator/+filebug](http://launchpad.net/ubuntu/+source/usb-creator/+filebug)).  It's quite hard to track multiple issues in single bug reports, so please break them up into multiple reports.

Thanks, your help in testing is much appreciated.

---

### Post by olskar on 2008-09-29
Tried it and it worked perfectly, an icon would be nice ;)

---

### Post by hype on 2008-09-30
Just tried out usb-creator on a 8Go usb stick: works nice.

I just have a few questions, concerning persistence.

Is it possible to create a persistent usb key using usb-creator?
For me, thez live usb worked nicely; i just created a user (with admin rights), installed a few apps, but after reboot, that user was deleted.

How to have the usb stick boot to a gdm login window that asks for a login/password?


And besides usb-creator, what would happen if booting from a Desktop live cd and installing ubuntu on the usb stick, straight from the installer ?

---

### Post by C.S.Cameron on 2008-09-30
I still can't understand the need for such an application when it so easy to install to Flash the same as to HDD.

---

### Post by evan d on 2008-09-30
> **hype said:**
> Is it possible to create a persistent usb key using usb-creator?
For me, thez live usb worked nicely; i just created a user (with admin rights), installed a few apps, but after reboot, that user was deleted.

Was this using usb-creator 0.1.7?  Persistence support is broken in casper, but you should end up at an initramfs prompt rather than the full desktop.

> **hype said:**
> How to have the usb stick boot to a gdm login window that asks for a login/password?

Why would you want to do this?  It's currently not possible on the live CD (which we're eventually renaming to "test drive", as the former is confusing when talking about USB drives).

> **hype said:**
> And besides usb-creator, what would happen if booting from a Desktop live cd and installing ubuntu on the usb stick, straight from the installer ?

That will work by the 8.10 release.  It requires some outstanding changes to partman and grub in order to work without modification of the installed system post-install.

---

### Post by evan d on 2008-09-30
> **C.S.Cameron said:**
> I still can't understand the need for such an application when it so easy to install to Flash the same as to HDD.

I think you may be confused on the intention of this application.  It does not replace ubiquity, the desktop CD installer, but rather writes a modified copy of the desktop CD to a USB disk and optionally enables persistence support.

---

### Post by C.S.Cameron on 2008-09-30
I'm often mistaken for being a little confused.
My point is that I built my current stick installing from the Live CD to the Flash drive the same as I would to internal HDD.
(My computer BIOS sees flash as just another HDD).
The Flash drive has:
A FAT32 partition visible to windows,
ext2 home partition,
ext3 O/S partition,
swap space for booting into low ram computers.
It can open in gnome or xfce sessions.
Switchconf allows it to boot:
Using Nvidia restricted drivers on a dual monitor,
Using Nvidia drivers on a HDTV,
Without restricted drivers on an ATI laptop, but with touchpad drivers etc working.
Using the basic xorg.conf for generic computers,
And using a boot CD for computer with BIOS that won't boot Flash.
Not to mention it runs wine, tvtime, Sketchup, Avast and has all the plugins for Movie Player.
I fully agree that Ubuntu should have an install to USB option.
I just think it should produce a fully featured flash drive.
Have ordered a new 4G and will give usb-creator a try when it arrives, but don't expect an easy sell.

---

### Post by evan d on 2008-09-30
> **C.S.Cameron said:**
> I'm often mistaken for being a little confused.
My point is that I built my current stick installing from the Live CD to the Flash drive the same as I would to internal HDD.
(My computer BIOS sees flash as just another HDD).

Right, and as mentioned that's not the design goal of usb-creator, so there is no overlap.

> **C.S.Cameron said:**
> The Flash drive has:
A FAT32 partition visible to windows,
ext2 home partition,
ext3 O/S partition,
swap space for booting into low ram computers.

For what it's worth, usb-creator uses a single vfat partition, which is perfectly readable in Windows (though the actual Ubuntu filesystem is packed in a squashfs, which is not).  usb-creator will happily co-exist with any other files you have on this partition.

> **C.S.Cameron said:**
> Switchconf allows it to boot:
Using Nvidia restricted drivers on a dual monitor,
Using Nvidia drivers on a HDTV,
Without restricted drivers on an ATI laptop, but with touchpad drivers etc working.
Using the basic xorg.conf for generic computers,

Our ability to add the nvidia driver to the CD or a tool such as this is governed by the decisions that nvidia's legal department makes.  Our hands are tied.

> **C.S.Cameron said:**
> And using a boot CD for computer with BIOS that won't boot Flash.

As said before, we're talking about two different overall use cases, but the usb-creator specification doesn't concern itself with BIOSes that cannot boot USB mass storage devices as one of the use cases is a computer without a CDROM drive.  In which case I have yet to see such a system with a BIOS that does not boot from USB mass storage.

The CD-based images will still be available for users with such BIOSes, however.

For the curious, the other use cases are computers without CD burners and and wanting a faster installation medium[1].

1: [https://wiki.ubuntu.com/USBInstallationImages](https://wiki.ubuntu.com/USBInstallationImages)

> **C.S.Cameron said:**
> 
Not to mention it runs wine, tvtime, Sketchup, Avast and has all the plugins for Movie Player.


This is more of a statement for the CD and DVD images themselves, as usb-creator does not concern itself with the packages on the image.

> **C.S.Cameron said:**
> 
I fully agree that Ubuntu should have an install to USB option.
I just think it should produce a fully featured flash drive.
Have ordered a new 4G and will give usb-creator a try when it arrives, but don't expect an easy sell.

Which again is not what we're talking about here.  As you said yourself, Ubuntu already has an install to USB option, ubiquity.  Your USB mass storage device is similar enough to a hard drive that the desktop installer can write to it with very little consideration.

I don't think you're the use case for this.  You clearly want a highly customized image, and that's great, but it's not something usb-creator is setting out to provide.

---

### Post by C.S.Cameron on 2008-10-01
Evan: You are wrong about one thing, I will be a user.
This is much better than the Live CD.
Downloaded and installed usb-creator on my thumbdrive using above link.
Process was smooth with no problems.
From there tried installing Xubuntu 8.04.1 on a 2G flash that had EEE-Xubuntu on it.
usb-creator said there was enough space.
Formatting was instantaneous, Install seemed to go ok and was very quick.
When booting, ended up at busybox with (initramfs).
Then tried an Ubuntu 8.04.1 disk.
usb-creator said there was enough space.
When booting, ended up at busybox with (initramfs).
Tried Ubuntu-EEE, same thing, but this was the closest I've gotten to installing it on flash
My last attempt was with Xubuntu 8.10 A6, (Intrepid).
First from CD and then directly from an iso on the desktop.
Both worked like a charm on the 2G flash. System Monitor says there is still 1.2G available.
It only took 2 minutes to install from the iso, not the 45 minutes I am use to.
I was a little worried about installing from a flash to a flash but usb-creator picked the correct drives.
I think I can vouch for usb-creator being fool proof.
The thing I like most is that it eliminates the need for a CD drive when installing Ubuntu.
I am still a little confused about this persistence thing but give usb-creator a 9 out of 10 anyway.

---

### Post by msktje on 2008-10-02
Hello, I have a question about that persistent ability. 
Is it so that when you boot the stick and you install extra packages,
the next time you boot the stick the packages are still installed?
Is this feature already implemented or wil it be in time for intrepid or
wil it be for 9.04?
greetz FW

---

### Post by Ubuntiac on 2008-10-08
For everyone not getting the advantage of this...

**[CENTER]It's not about installing TO a usb key, its about installing FROM a usb key to your hard drive.[/CENTER]**

I have no CD drive on my laptop therefore I CAN'T use a live CD. This let's me replace the live cd with a "live usb key" and *finally*  have an easy way to do a fresh install.

Evan, it works *perfectly* for me and is an absolute {$PREFERRED_DEITY} send. Thankyou!!!

---

### Post by Ubuntiac on 2008-10-08
Uh oh...

I just found out that [this bug]("https://bugs.launchpad.net/ubuntu-express/+bug/157153") is alive and well with Intrepid. Fortunately the simple fix is there, too.

In short, computers installing (*)ubuntu from a USB key become unable to automount usb keys after installing. This may or may not be limited to laptops without CD drives.

If you've used usb-creator to install from usb, I'd encourage you to share whether usb automount works for you or not and whether you have a cd/dvd drive on the bug report.

To be fair, I understand this is a bug with Ubuntu / the kernel, but I have a feeling that because of the ease of installing from usb that usb-creator is bringing that we're about to see a whole lot more people hitting this bug.:confused:

---

### Post by C.S.Cameron on 2008-10-09
I used a flash drive built using usb-creator to install Xubuntu 8.10 Beta on a second flash drive, full install, not CD image.
Booting gave error message, no such drive.
Menu.lst had root listed as (1,2).
After changing root to (0,2) the drive boots.
During updates I am asked to modify menu.lst.
If I say yes, it is changed back to (1,2).

Automount seems to work fine when I am running this drive.

My only problem is that the latest usb-creator from launchpad no longer seem to work for me.
Booting all I get is grub _ with a blinking curses.
I've tried it a dozen times with different distro's, different computers, etc.

Oop's, forget that last statement, I installed Usb-creator just a few minutes ago booting from a 8.10 Beta Live CD.
It seems to be working fine again.

---

### Post by High Roller on 2008-10-10
> **evan d said:**
> Persistence support is broken in casper, but you should end up at an initramfs prompt rather than the full desktop.

I'm using the Ibex daily build and I get full desktop but no persistence support.  It seems it's acting like a LiveCD.

---

### Post by sipickles on 2008-10-10
> **evan d said:**
> I think you may be confused on the intention of this application.  It does not replace ubiquity, the desktop CD installer, but rather writes a modified copy of the desktop CD to a USB disk and optionally enables persistence support.

So, this does not provide an installation *from* USB *to* Hard Drive?

I need to install Intrepid Server onto a WAFER-MARK Pc (No CD, but with a HD).

I am going to attempt to use USB-Creator to do this -the USB drive replacing the LiveCD. Am I barking mad?

Thanks

Si

---

### Post by Ubuntiac on 2008-10-10
> So, this does not provide an installation from USB to Hard Drive?

It absolutely *does* allow you to install from usb to a hard drive.

I'm posting this from my laptop (which has no cd drive) running Intrepid. I used usb-creator to put the cd iso on my usb key and install onto the hard drive from there. I am now happily running Intrepid without any usb key.

Hope this clears the issue up! :popcorn:

---

### Post by sipickles on 2008-10-10
Alas, with Intrepid Server ISO, the USB-Creator succeeds but the boot fails with

Insert proper boot device

Told! :(

---

### Post by evan d on 2008-10-10
> **msktje said:**
> Hello, I have a question about that persistent ability. 
Is it so that when you boot the stick and you install extra packages,
the next time you boot the stick the packages are still installed?
Is this feature already implemented or wil it be in time for intrepid or
wil it be for 9.04?
greetz FW

Yes.  But persistence is currently broken, though it will be fixed before release.  See:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/274076](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/274076)

---

### Post by evan d on 2008-10-10
> **Ubuntiac said:**
> Uh oh...

I just found out that [this bug]("https://bugs.launchpad.net/ubuntu-express/+bug/157153") is alive and well with Intrepid.

It's on my radar and will be fixed by release.

---

### Post by evan d on 2008-10-10
> **C.S.Cameron said:**
> I used a flash drive built using usb-creator to install Xubuntu 8.10 Beta on a second flash drive, full install, not CD image.
Booting gave error message, no such drive.
Menu.lst had root listed as (1,2).
After changing root to (0,2) the drive boots.
During updates I am asked to modify menu.lst.
If I say yes, it is changed back to (1,2).

The drive order changes after you install.  This is solved by adding UUID support to GRUB, which was done by Colin King earlier in the cycle, and updating update-grub to handle the new uuid command that came as a result of that, which I'm going to commit to the archive tonight.

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/281100](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/281100)

> **C.S.Cameron said:**
> My only problem is that the latest usb-creator from launchpad no longer seem to work for me.
Booting all I get is grub _ with a blinking curses.
I've tried it a dozen times with different distro's, different computers, etc.

The bootloader defaults to (hd0), which happens to be your usb drive when you're installing from it.  This has been on my radar for some time now and I'm in the process of writing a patch to make it default to something more reasonable.

---

### Post by evan d on 2008-10-10
> **sipickles said:**
> Alas, with Intrepid Server ISO, the USB-Creator succeeds but the boot fails with

Insert proper boot device

Told! :(

debian-installer based CD (Alternate CD, Server CD) support is on the way.

[https://bugs.launchpad.net/ubuntu/intrepid/+source/usb-creator/+bug/234185](https://bugs.launchpad.net/ubuntu/intrepid/+source/usb-creator/+bug/234185)

---

### Post by Sand Lee on 2008-10-11
usb-creator worked just fine for me **except** for one thing:
It doesn't enable the LBA flag by default - this does not let my flash drive boot. [Bug Report.]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/277903")

---

### Post by Ubuntiac on 2008-10-11
> **evan d said:**
> It's on my radar and will be fixed by release.

All hail Evan! Long may your offspring walk the Earth, and your code command it's technology.

May the Ubuntu be with you. :biggrin:

---

### Post by vijaym on 2008-10-15
Have been trying this software without luck

using hardy on PC

have reported as bug
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/283874](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/283874)

any assistance

ta

---

### Post by High Roller on 2008-10-16
Now testing on a daily build with persistence enabled.  Works like a charm now that casper is fixed.

---

### Post by Rinnan on 2008-10-21
Well, I've run into a little problem with it -- if you insert a USB stick which has already gotten another usb-creator created installation on it, it will try to install it on one of the partitions (sdb1) instead of the drive.  It won't offer to reformat.  And of course, if it's a 2GB stick such as mine was, it won't be able to fit a new installation on the partition anyway.  So, it would be better if the offer to format a stick is always there, or, if it detects a previous installation it offers to overwrite it.  This happened when I tried to install a newer Ubuntu over an older Ubuntu on the same stick. Finally I had to "dd if=/dev/zero of=/dev/sdb bs=1M" for a few seconds so that it overwrote important stuff.  After that, the now unpartitioned stick worked perfectly.

On an unrelated note, I've found that a different one of my USB sticks, a Cruzer, even though it is big enough, will absolutely not boot on any machine.  It seems to install perfectly.  Is this some kind of problem with the stick?  The Kingston works just fine.

EDIT:  note to everyone:  Don't try the "dd if=/dev/zero of=/dev/sdb bs=1M" command above unless you already know exactly what it does.  It's a dangerous command, perhaps even more dangerous than the "rm -rf /" boogeyman you read about aound here.  Side note:  just blanking the first 512 byte block on the stick seemed to have no effect, oddly, so I went for the violent approach above.

---

### Post by C.S.Cameron on 2008-10-22
U-C is working ok for me installing to a 2G Kingston Traveler.
Could only get Error 17 installing to 4G Kingston Traveler.

Grabbed a second 4G Kingston to try U-C on it.
I had been using this drive for Live CD persistence.
It has two ext3 partitions on it, casper-rw and home-rw.

To my surprise on booting the 2G Kingston I found that it was using persistence from the second 4G.
 
This might be of use if a person wants a separate home drive or to expand storage space.

Applications installed only to the 2G do not work when the 4G is plugged in.
Applications installed when the 4G is plugged in are saved only to it.

---

### Post by High Roller on 2008-10-26
Tried usb-creator on the latest daily - 10/25/08.
Can no longer boot in persistent mode.  I get a whole bunch of errors that seem to indicate that it can't find the persistent file system.

I'll see if I can somehow get those errors captured in a log.  But for now I can't seem to do that as I can't get anything to boot :)

Last readable error message:
> The GDM user 'gdm' does not exist.  Please correct GDM configuration and restart GDM.

---

### Post by JoWilly on 2008-10-30
This tool doesn't work (using a fresh "release" 8.10 install).

It always hangs at "Starting up". Clicking on cancel opens a windows with a "Quit" button. Clicking on Quit does nothing. The only way to close the Quit window is to kill it.

The same goes for the main window. The only way to close it is to kill it.

The terminal output shows that it hangs after the 8th line ("Persitence size") and does nothing thereafter.

This is on a Sony Vaio laptop, using the 32bit 8.10 release, a 2 Gb usb key, and feeding it the 32bit iso and I have also tried the 64bit iso.

---

### Post by JoWilly on 2008-10-31
Ok, I have now tried to get this to work on another system (desktop core2duo 3ghz, 4Gb ram, freshly installed 8.10 x64).

On this x64 system I get exactly the same problem as with the 32bit laptop. USB disk creator hangs at "starting up" without doing anything.

This tool, as shipped with the final release ubuntu 8.10 (and now fully updated as of October 31st in the morning) just does not work.

---

### Post by DaddyX3 on 2008-10-31
I've been scratching my head on this one for 2-days now, just can't seem to get this thing to work for me. 
I think a little more in depth article on what the setup requirements are for this utility is in order. For example, 
* What format does your USB stick have to be(fat16, fat32, ntfs, ext2, ext3)?
* What flags need to be enabled for the install to work correctly and boot as it is supposed to? 
* Does the above mentioned formats effect which flags should be enabled? 
* Systems with different BIOS have different nominclatures for booting from USB .... do you use USB HDD, USB floppy, USB cdrom ?? I know this may sound like a silly question - but it is important. 
* What does it mean if you get a 'grub error 17'? Are you trying to boot in the right fashion? If not then what are some tips for getting a correct boot? 
* Which 'usb-creator' version is the latest and which one has the fixed casper??? How would I know if I have been scratching my head for the last couple days on a piece of software that actually works!?
Thanks in advance guys/ girls

---

### Post by DaddyX3 on 2008-10-31
I've been scratching my head on this one for 2-days now, just can't seem to get this thing to work for me. 
I think a little more in depth article on what the setup requirements are for this utility is in order. For example, 
* What format does your USB stick have to be(fat16, fat32, ntfs, ext2, ext3)?
* What flags need to be enabled for the install to work correctly and boot as it is supposed to? 
* Does the above mentioned formats effect which flags should be enabled? 
* Systems with different BIOS have different nominclatures for booting from USB .... do you use USB HDD, USB floppy, USB cdrom ?? I know this may sound like a silly question - but it is important. 
* What does it mean if you get a 'grub error 17'? Are you trying to boot in the right fashion? If not then what are some tips for getting a correct boot? 
* Which 'usb-creator' version is the latest and which one has the fixed casper??? How would I know if I have been scratching my head for the last couple days on a piece of software that actually works!?
Thanks in advance guys/ girls

---

### Post by Odisej on 2008-10-31
I've used it for installing Ubuntu Ibex RC on my EeePC. Worked like a charm. Only needed to insert the usb key and select the ISO image rest was done automatically. Was able to install Ubuntu without any problems.
:popcorn:

---

### Post by coyotle on 2008-10-31
> **JoWilly said:**
> This tool doesn't work (using a fresh "release" 8.10 install).

It always hangs at "Starting up". Clicking on cancel opens a windows with a "Quit" button. Clicking on Quit does nothing. The only way to close the Quit window is to kill it.

The same goes for the main window. The only way to close it is to kill it.

The terminal output shows that it hangs after the 8th line ("Persitence size") and does nothing thereafter.

This is on a Sony Vaio laptop, using the 32bit 8.10 release, a 2 Gb usb key, and feeding it the 32bit iso and I have also tried the 64bit iso.

Yes, I have the same problem!

Log:
$ usb-creator 

-- Starting up at 22:09:49 --
[22:09:49] got a disc: MACOSXBOOT
[22:09:49] new device:
{'capacity': dbus.UInt64(2011168768L), 'uuid': '4031-97D0', 'label': '', 'free': 2007224320L, 'fstype': 'vfat', 'device': '/dev/sdb', 'mountpoint': '/media/disk', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_4031_97D0'}
[22:09:49] adding: /dev/sdb
[22:10:05] mounting /home/coyote/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/ISO/ubuntu-8.10-desktop-i386.iso
[22:10:05] updating dest_status as part of update_row_state
[22:10:18] Installing...
[22:10:18] Source CD: /home/coyote/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/ISO/ubuntu-8.10-desktop-i386.iso
[22:10:18] Destination disk: /dev/sdb
[22:10:18] Persistence size: 128 MB

and nothing more...

---

### Post by zorkerz on 2008-10-31
This worked fine for me with a newer 64 bit intrepid iso (older beta's did not work). I just put in my usb already formatted to fat32 and let it fly. It even keeps all the information that is already on the usb. Though I will say it wold be nice if all the ubuntu files went into a single folder to remove clutter so that i can easily find my files already on there.

---

### Post by fodogen on 2008-10-31
> **coyotle said:**
> Yes, I have the same problem!

Log:
$ usb-creator 

-- Starting up at 22:09:49 --
[22:09:49] got a disc: MACOSXBOOT
[22:09:49] new device:
{'capacity': dbus.UInt64(2011168768L), 'uuid': '4031-97D0', 'label': '', 'free': 2007224320L, 'fstype': 'vfat', 'device': '/dev/sdb', 'mountpoint': '/media/disk', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_4031_97D0'}
[22:09:49] adding: /dev/sdb
[22:10:05] mounting /home/coyote/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/ISO/ubuntu-8.10-desktop-i386.iso
[22:10:05] updating dest_status as part of update_row_state
[22:10:18] Installing...
[22:10:18] Source CD: /home/coyote/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/ISO/ubuntu-8.10-desktop-i386.iso
[22:10:18] Destination disk: /dev/sdb
[22:10:18] Persistence size: 128 MB

and nothing more...
I had the same symptoms as you but found the problem(for me at least).
It crashes around row 450 in /usr/share/pyshared/usbcreator/backend.py if the thumbdrive does not have a valid partion. The partition must be numbered and not like my drive was(/dev/sdb) otherwise num will be empty. It looks like the code is supposed to write an error message if this occurs but it doesn't happen.
What I did was to reformat the drive with gparted so that I got a valid fat32 partition on it. Then the drive worked like a charm. :)

---

### Post by The Penguin on 2008-11-02
Now that ubuntu 8.10 Intrepid Ibex has been released, I tried the usb-creator and it seemed  to create the bootable usb disk properly until I tried to boot off it. I get an "Invalid or damaged bootable partition" error message when booting from the usb drive.

christopher@R2-D2:~$ usb-creator 

-- Starting up at 08:20:08 --
[08:20:08] new device:
{'capacity': dbus.UInt64(8002797568L), 'uuid': '4761-0C85', 'label': 'FLASHDRIVE', 'free': 5129895936L, 'fstype': 'vfat', 'device': '/dev/sdb1', 'mountpoint': '/media/FLASHDRIVE', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_4761_0C85'}
[08:20:08] adding: /dev/sdb1
[08:20:21] possibly adding: /org/freedesktop/Hal/devices/volume_label_Ubuntu_8_10_i386
[08:20:21] got a disc: Ubuntu 8.10 i386
[08:20:22] updating dest_status as part of update_row_state
[08:20:22] updating dest_status as part of update_row_state
[08:20:22] prop modified
[08:20:22] device_udi: /org/freedesktop/Hal/devices/volume_label_Ubuntu_8_10_i386
[08:20:22] num_changes: 3
[08:20:22] change: volume.mount_point
[08:20:22] change: volume.is_mounted_read_only
[08:20:22] change: volume.is_mounted
[08:20:37] Installing...
[08:20:37] Source CD: /org/freedesktop/Hal/devices/volume_label_Ubuntu_8_10_i386
[08:20:37] Destination disk: /dev/sdb1
[08:20:37] Persistence size: 2052 MB
[08:20:37] Marking partition 1 as active.
[08:20:37] installing the bootloader to /dev/sdb1.
[08:20:40] ['/usr/share/usb-creator/install.py', '-s', u'/media/cdrom1/.', '-t', '/media/FLASHDRIVE', '-p', '2052']
[08:25:50] Install command exited with code: 0

---

### Post by Drew_[SCED] on 2008-11-03
I tried installing Xubuntu on a Sandisk Cruzer micro 2.0 GB, and the laptop (Toshiba Satellite M115) was unable to boot from it.  It caused the BIOS to act very slowly, and when it tried to boot from the USB drive, it just stalled and skipped over to the HDD.

Things I might have done wrong:
[LIST]
[*][s]Gotten a bad image - torrented from isoHunt[/s]
[*]Not used a Live CD, but rather just selected the image from my desktop
[*]Left the computer after it had stalled for a couple minutes, so couldn't read error messages (if any)
[/LIST]

Things I know I had right:
[LIST]
[*]Had enough space
[*]BIOS supported USB boot
[*]Had BIOS boot from USB before HDD
[/LIST]

I'm trying again, downloading a fresh image from Ubuntu (still bittorrent) and may try a Live CD first as well.

This may be a matter of my error, but I sure don't think it is.  (I'll update if it works.)

Update: tried it with an Ubuntu image, and had the same issue.  Also, it seems that when I plug the drive in when the computer is running Windows, there is no autorun to show the regular menu that appears for CDs.

---

### Post by Handssolow on 2008-11-03
A bit off the point I know but I eventually got 8.10 beta persistent on an 8Gb USB memory stick by using advice I found here-

[http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

I'm not sure now if I used the manual approach or the automatic method, probably automatic. I had to make sure first that I removed any partitions on the memory stick with fdisk before starting the install. Now I've updated/upgraded 8.10, configured for wifi, changed to UK English etc I'm thinking about how I back up the memory stick's OS onto my Desktop PC then to DVD to simplify the creation of a copy. I want Ubuntu on a memory stick because I dont want to install Ubuntu to my Acer Aspire One's hd and risk altering XP and I want to use Ubuntu for websurfing when I'm unsure of security. I would like to set up some login/password at bootup, instead the USB OS behaves just like a live CD (but with persistence). I might have a go with usb-creator after I've bought another memory stick.

---

### Post by phlancelot on 2008-11-04
Hi, I'm not totally sure if this fits into the right discussion but I'm having some problems with the USB-creator tool in 8.10

I ran the tool with no problems from the live CD using my empty 2G flash stick. All seemed to be going well.

My problem comes when I try to boot using the thing. In two different computers I am unable to get the thing to boot, I have changed the BIOS settings and all but all I get is a black screen as it tries to boot that says 

GRUB _               that last underscore is a flashing cursor.... this screen just hangs for eternity.

On both the comptuers I have Hardy installed to the main hard drives, could it be interfering with the master boot record/grub/etc ? 

Thanks for your help.

---

### Post by C.S.Cameron on 2008-11-04
Re
Things I know I had right:

    * Had enough space
    * BIOS supported USB boot
    * Had BIOS boot from USB before HDD

In BIOS I need to select the flash drive as first HDD and not boot from USB first.

---

### Post by Drew_[SCED] on 2008-11-05
> **C.S.Cameron said:**
> Re
Things I know I had right:

    * Had enough space
    * BIOS supported USB boot
    * Had BIOS boot from USB before HDD

In BIOS I need to select the flash drive as first HDD and not boot from USB first.

You say toe-may-toe, I say toe-mah-toe.

---

### Post by Drew_[SCED] on 2008-11-05
> **fodogen said:**
> I had the same symptoms as you but found the problem(for me at least).
It crashes around row 450 in /usr/share/pyshared/usbcreator/backend.py if the thumbdrive does not have a valid partion. The partition must be numbered and not like my drive was(/dev/sdb) otherwise num will be empty. It looks like the code is supposed to write an error message if this occurs but it doesn't happen.
What I did was to reformat the drive with gparted so that I got a valid fat32 partition on it. Then the drive worked like a charm. :)

How do I use (or where do I get) gparted?

I should rephrase that; I know what gparted is, it's the GNOME Partition Manager that Ubuntu uses for installation - but I don't know how to access it on this computer, nor do I know how to use it on my flash drive.  Is it the mkfs command?  If so, I've done that to my flash drive, and it doesn't work.

---

### Post by Handssolow on 2008-11-05
Sorry if this is off topic again but there are several things which need sorting out with my USB persistant 8.10 (beta then updated). Essentially mine's working like a live CD which I can update but it's not like a normal install. There's no Grub and therefore no recovery mode. Some of the updates throw up an error message because there's apparently no  /var/cache/debconf/passwords.dat file. The install icon is always on the desktop. The sources list isn't optimal for this USB based system. It keeps expecting to access a cdrom but that was on my desktop not now my stick's plugged into my AcerA0 netbook, so the sources list probably needs changing. There's a home folder but it's Ubuntu's not mine by name. There's no password system except if I activate the Login Window, but it's not the same in the terminal where no password is necessary.

Would any other USB creation methods be any different?

Like a live CD I can move the memory stick and boot my desktop from the memory stick where it recognises and apparently functions with the different hardware. It's all rather neat and I'm very impressive to be able to boot my XP netbook with Ubuntu on a USB stick.

---

### Post by C.S.Cameron on 2008-11-05
If you want a password you can create a new account in Users and Groups.
If you want a Full install, you can use your persistent USB (or Live CD), to install to a flash drive using the same method as to HDD, this uses a bit more disk space.
You can also create casper and home partitions on your U-C stick.

Garted, (Gnome Partition Editor), can be found in Applications, Add/Remove.

---

### Post by Drew_[SCED] on 2008-11-05
Update: using a Live CD ALSO does not work, though Pendrivelinux seems to believe it should.

I guess there's something wrong with my drive where it won't support OS booting.  Oh well.

---

### Post by C.S.Cameron on 2008-11-06
After dozens of installs with usb-creator, (some worked many did not), I am starting to think this has something to do with the formatting of the flash drive.
For example:
Had U-C install working on 2G Kingston.
Used EEE PC support DVD to make EEE recovery disk, (this formatted the drive).
Then reformatted flash drive to FAT32, (using gparted CD).
Installed 8.10 from CD using U-C.
Got "Error 17", (not "grub error 17").
Deleted files and used Unibootin to install 8.10, (this worked).
Deleted files and used U-C to install 8.10, (this worked).
Reformatted with gparted then installed using U-C and it still worked.
Have also tried this on 4G Kingston with same results, (even with full 4G partition).

---

### Post by caljohnsmith on 2008-11-06
> **C.S.Cameron said:**
> After dozens of installs with usb-creator, (some worked many did not), I am starting to think this has something to do with the formatting of the flash drive.
For example:
Had U-C install working on 2G Kingston.
Used EEE PC support DVD to make EEE recovery disk, (this formatted the drive).
Then reformatted flash drive to FAT32, (using gparted CD).
Installed 8.10 from CD using U-C.
Got "Error 17", (not "grub error 17").
Deleted files and used Unibootin to install 8.10, (this worked).
Deleted files and used U-C to install 8.10, (this worked).
Reformatted with gparted then installed using U-C and it still worked.
Have also tried this on 4G Kingston with same results, (even with full 4G partition).
Just one small comment; I know with UNetBootin, it has to use FAT16 rather than FAT32 because syslinux only supports FAT16 partitions. I would assume it is the same with the Intrepid USB-Creator, since it also uses syslinux. Maybe if you instead formatted your partition to FAT16 that would solve your problem?

---

### Post by C.S.Cameron on 2008-11-06
Unetbootin has been working for me using FAT32 formatting.

---

### Post by caljohnsmith on 2008-11-06
> **C.S.Cameron said:**
> Unetbootin has been working for me using FAT32 formatting.
I guess I would have to read more how UNetBootin works, because I googled it and you're right, according to [this UNetBootin Wiki page]("http://unetbootin.wiki.sourceforge.net/guide"), UNetBootin uses FAT32. But from the "syslinux" man page:
>    Booting from a FAT partition on a hard disk SYSLINUX can boot from a FAT12 or FAT16 filesystem partition on a  hard disk  ([COLOR="Blue"]FAT32,  introduced  in  Windows 95 OSR-2, is not supported, however.[/COLOR]) 
So like I said, I guess I will have to read more how UNetBootin works if I don't want to make any more ignorant comments. :)

---

### Post by candtalan on 2008-11-06
I have found a problem today and I have a short thread at 

[http://ubuntuforums.org/showthread.php?t=972860](http://ubuntuforums.org/showthread.php?t=972860)
"8.10 USB stick booting problems - wierd"

U-C is certainly not working for me, I am using a checked ok live cd to run the process, because I do not have 8.10 installed yet.

I have tried two machines, and two usb sticks (each 1GB), also gparted  to pre format fat 16 and also unetbootin. 
Unetbootin worked ok! However it required me to initially format to fat32, which it then accepted.

I notice that U-C seems to format to fat16, at least when I examine the usb stick with gparted, it shows as fat16.

I have not yet tried to pre format to fat32 and *then* use U-C
tia


Success here! Update:
I pre formatted the 1GB usb stick to fat32 using gparted, then booted the pc with a checked ok live CD ubuntu 8.10, then I used usb creator as soon as the live cd system was running, using the pre formatted fat32 usb stick.

The USB stick was created ok and it works as a normal usb boot ok!!

I have been trying for ages to get this to work with very variable mostly failed boot results! When i looked, it was fat16, so I thought it must need to be this, but it was probably just that the stick was fat16 originally.

I now notice that the U-C does not seem to format the usb stick? If it did then I did not notice it. Anyway, I am now going to try another similar stick again preformatting with fat32.

---

### Post by sedawk on 2008-11-07
Hello!

I upgraded to 8.10 (from 8.04 with latest updates) and
usb-creators hangs at "Starting Up" like described by others above.

Output when starting usb-creator from command line:

[15:22:58] adding: /dev/sdb1
[15:23:08] mounting /home/_user_/Desktop/ubuntu-8.10-desktop-i386.iso
[15:23:08] updating dest_status as part of update_row_state
[15:23:14] Installing...
[15:23:14] Source CD: /home/_user_/Desktop/ubuntu-8.10-desktop-i386.iso
[15:23:14] Destination disk: /dev/sdb1
[15:23:14] Persistence size: 128 MB
[15:23:14] Marking partition 1 as active.
[15:23:14] installing the bootloader to /dev/sdb1.
[15:23:14] Forcing shutdown of the install process.

? "Forcing shutdown" ?

---

### Post by Vadi on 2008-11-08
Fails to work for me. Just sits at "Starting up" forever.

---

### Post by Zerocool3001 on 2008-11-09
I've actually had a few separate problems with usb creator. I'll post them in launchpad. Email me if you want more details or to try some things.

---

### Post by marktebbutt on 2008-11-10
Sadly, everything seemed to work ok for me - until I tried to boot from the USB stick. I then just got the following message - invalid or damaged bootable partition.
Any advice would be appreciated.

---

### Post by Flimm on 2008-11-10
I have been affected by this bug:
[usb-creator produces flash drive that won't boot on my system: could not find kernel image](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/290154)
Do you think we've provided enough information for this bug report to be marked as triaged?

---

### Post by C.S.Cameron on 2008-11-12
My last install has been working great for a week now.
Got Virtual Box running XP running AutotCAD and SketchUp
(a little slowly at times).

---

### Post by ingo on 2008-11-24
I've used usb-creator on a home cooked Kubuntu-8.10 iso and it worked a treat! Cheers to the dev(s).  How did you get the bootstrap working? Pendrive and the like NEVER worked for me, so I'm delighted that usb-creator appears to deliver on its promises!

---

### Post by lmonast on 2008-11-30
I've tried to install intrepid on a Ideapad S10. I've used to kingston pen drive (2 gb and 8 gb) formated fat 32 formatted. Everything runs smooth until I try to boot the S10 with the pen drive. I press F12, choose the pen-drive, but then it says "pen drive without operational system".
I've tried both pen-drives on a thinkpad t61 and the resultas were similar. What am I doing wrong?
Thank you,
Leo

---

### Post by caljohnsmith on 2008-11-30
> **lmonast said:**
> I've tried to install intrepid on a Ideapad S10. I've used to kingston pen drive (2 gb and 8 gb) formated fat 32 formatted. Everything runs smooth until I try to boot the S10 with the pen drive. I press F12, choose the pen-drive, but then it says "pen drive without operational system".
I've tried both pen-drives on a thinkpad t61 and the resultas were similar. What am I doing wrong?
Thank you,
Leo
A "pen drive without operational system" error might be the result of having a BIOS that will not boot a drive which doesn't have one of its partitions marked as bootable. You can check that by opening a terminal (Applications > Accessories > Terminal), and do:
```
sudo fdisk -lu
```
And look to see if any of the partitions on your pen drive have an asterisk * in the boot category. If not, that might be your problem. How about posting the output of the fdisk command above so I can help you check. :)

---

### Post by lmonast on 2008-12-01
> **caljohnsmith said:**
> A "pen drive without operational system" error might be the result of having a BIOS that will not boot a drive which doesn't have one of its partitions marked as bootable. You can check that by opening a terminal (Applications > Accessories > Terminal), and do:
```
sudo fdisk -lu
```
And look to see if any of the partitions on your pen drive have an asterisk * in the boot category. If not, that might be your problem. How about posting the output of the fdisk command above so I can help you check. :)

Many thanks!Any other suggestion?
I've got this:


> Disk /dev/sdb: 8036 MB, 8036286464 bytes
18 heads, 58 sectors/track, 15034 cylinders, total 15695872 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2200    15695871     7846836    b  W95 FAT32

---

### Post by caljohnsmith on 2008-12-01
OK, how about doing:
```
sudo dd if=/dev/sdb count=100 | gzip -c > ~/Desktop/sdb.MBR.gz
```
That will create a really small "sdb.MBR.gz" file on your desktop; please attach that to your next post so I can take a look at your USB drive's MBR (Master Boot Record). You can attach it by clicking the "paper clip" icon at the top of the Ubuntu forum message box in your browser. Also, which program did you use to format your USB drive?

---

### Post by lmonast on 2008-12-01
Here it goes. The pen drive was not mounted.
I formated the pen drive using windows vista (sorry for that :-) ). Should I've used gparted?

---

### Post by caljohnsmith on 2008-12-01
lmonast, that definitely clears things up quite a bit; you don't seem to have any valid boot code in the MBR of your sdb USB drive that I can tell, and it's only 53 bytes in length. In fact, that error message you are getting is coming from an error code in the sdb MBR. Also, I notice your USB drive geometry is a little different since you used Vista to format it, so I think you would be better off using a Linux tool to format it; I think theoretically it shouldn't make any difference, but better to play it as safe as possible. I would try reformatting the drive with Ubuntu's gparted (System > Admin > Partition Editor), and then reinstalling. How about giving that a try and letting me know what happens.

---

### Post by lmonast on 2008-12-01
Thank you very much. I've formated the disk with ubuntu but it did not work.
Then I used unerbootin and it works perfectly. Again, thanks...
[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

---

### Post by castrojo on 2008-12-08
Hi guys, Evan has been busy lately and will get back to answering your questions as soon as possible.

---

### Post by halgar on 2008-12-11
I can report the following error as above with 8.10: "Invalid or damaged bootable partition" 

This has been duplicated by building and testing on a T60 and T61 Thinkpad.

Each time I use gparted to delete the USB partition.  Then I let the usb-creator format it.  ALso, I select to use 2 of the 8 gig as storage.

BIOS has USB boot enabled.  USB is chosen via the F12 boot list.

fdisk shows the partition as bootable:
/dev/sdb1  *    1   988   7936078+  c  W95  FAT32  (LBA)

There was a site that thought this was due to the lba flag not being on, but I find that it is always set to on by usb-creator.

I have not tried unerbootin, but would prefer to keep the process as simple and Ubuntu as possible as I am documenting it for others.

thanks for any ideas,
halgar

---

### Post by evan d on 2008-12-15
First, apologies for not replying sooner.  As Jorge has kindly mentioned on my behalf, it's been a busy few weeks.

Can anyone that was having issues please try 0.1.11, as found in my PPA:
[https://launchpad.net/~evand/+archive](https://launchpad.net/~evand/+archive)

This, among other things, always writes the syslinux bootloader code to your MBR, rather than just the first partition of the disk, so it should solve the booting issues for some users.

Please do report back if it has or has not solved your problems, I'm very interested in resolving all of them.

Thanks!

---

### Post by evan d on 2008-12-15
I should also note that always showing the format button is planned.  I'll post a link to the full specification with 9.04 plans once I have it updated from our discussions at the Ubuntu Developer Summit that just concluded this past week.

---

### Post by Chikitulfo on 2009-04-06
Hi, 
I had some problems with the usb-creator from 8.10, but with the one in launchpad it worked flawlessly!!

---

### Post by wirechief on 2009-04-16
I have been following another bug report that should be known here too.
Bug 276822] Re: busybox with (initramfs) / boot: / kernel not found
Since about April 10th 2009 it didn't matter if i used netbootin-linux-319
or usb-creator ii  usb-creator 0.1.15  it would fail and drop me to a 
busybox with initramfs  [https://bugs.launchpad.net/bugs/276822](https://bugs.launchpad.net/bugs/276822) provides
more details but the last test i made was to add rootdelay=90 on the grub
boot line and that while making it longer to boot it made it up to the desktop. Something in the coding for the persistence is not using enough time for the usb stick to get setup and its failing.

---

### Post by bedge on 2011-01-04
I'd like to ask if there's any plan to work on the console version of this as defined in this spec:
[https://wiki.ubuntu.com/Specs/LucidUsbCreatorConsole/](https://wiki.ubuntu.com/Specs/LucidUsbCreatorConsole/)

Thanks.

---

### Post by Treken on 2011-09-05
64 bit version would be nice

---

