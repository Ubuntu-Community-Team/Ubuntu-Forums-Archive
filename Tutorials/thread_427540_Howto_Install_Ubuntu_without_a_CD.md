---
title: "Howto: Install Ubuntu without a CD"
date: 2007-04-29
forum: Tutorials
---

### Post by tuxcantfly on 2007-04-29
[COLOR="Red"]_***UNetbootin NOW HAS ITS OWN WEBSITE AND GUIDE AT [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)***_[/COLOR]

UNetbootin allows for installation of various Linux distributions to a real partition (so it's no different from a standard Ubuntu install), and uses a standard netboot installation, so internet access is needed. The main advantage of UNetbootin over Wubi and similar projects is that it creates a standard GNU/Linux install without needing a CD, and supports a variety of distributions.

Note that if you have a USB drive handy, and your computer can boot from USB, [this](http://ubuntuforums.org/showthread.php?t=811397) guide (which instead creates a liveUSB drive to boot and install from) will likely work better.

Downloads at [http://sourceforge.net/project/showfiles.php?group_id=222386](http://sourceforge.net/project/showfiles.php?group_id=222386)

**Note that this guide is now somewhat outdated; I am still updating it; please see the website at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) for more up-to-date instructions**

**Supported Distributions and Versions**

UNetbootin allows for the installation of:

Ubuntu (and official derivatives) 7.10, 7.04, 6.10, 6.06 LTS, and upcoming 8.04 LTS
Fedora 8, 7, and Rawhide
openSUSE 10.3, 10.2, and Factory
PCLinuxOS 2008
CentOS 5.1
Debian Stable/Etch, Testing/Lenny, and Unstable/Sid
ArchLinux 2007.08
FreeBSD 7.0 and 6.3
NetBSD 4.0
Frugalware Linux Stable, Testing, and Current
Foresight Linux 1.4.2
Damn Small Linux 4.2.4
VectorLinux 5.9
Mandriva 2008.0 and 2007.1
Slackware 12.0 

Post a request for any others that support installation over FTP, and supply links to the requested distribution's PXE/netboot initrd image, or FTP-install CD.

**Purpose**

This is meant for people who want to install Ubuntu but don't have a CD-R to burn, lack a CD writer, or they want to install on a computer that doesn't have a CD-ROM drive, like an ultra-portable laptop.

**What it does**

UNetbootin uses an Windows-based or Linux-based installer to install a small modification to the Windows or Linux bootloader (grldr and boot.ini for NT-based systems, grub.exe and config.sys for Win9x, or grub for Linux), uses the bootloader to boot the netboot initrd and kernel, then uses that to download and install the desired distro (Ubuntu, Mandriva, Fedora, OpenSuse, Slackware, Debian, and Arch Linux) are currently supported) directly from the internet, no CD required. After Ubuntu is installed, the modification to the bootloader is then undone, 
[B]
Requirements/Dependencies[/B]

Linux or Microsoft Windows 95-Vista
A broadband internet connection (dial-up will take way too long to download)
3GB or more of spare hard drive space to install Ubuntu in

**Installation Instructions**

Before installing, remember to back up all your data, in case you do something wrong in the partitioning stage of the installer.

1. Download the appropriate file for the distro version you want to install; if using Windows, use the exe files, if using an Ubuntu or a Debian-based distro, use the deb files, if using Fedora or an RPM-based distro, use the rpm files, if using if using another Linux distribution, use the sh (self extracting) files:
[http://sourceforge.net/project/showfiles.php?group_id=222386](http://sourceforge.net/project/showfiles.php?group_id=222386)

2. Run the file, and click "OK" to reboot

3. Select "UNetbootin" from the menu list

4. Answer the questions asked by the installer, and wait while it downloads and installs 650 MB of packages.

**IMPORTANT NOTE TO USERS INSTALLING UBUNTU: If you're installing *Ubuntu, make sure to mark one or more desktop environment (Ubuntu, Xubuntu, Kubuntu, etc) using the space button when asked by the installer, so that it's marked with an asterisk (*), or else you'll be left with a commandline-only environment.**

5. Reboot, and enjoy your new Ubuntu, Fedora, openSUSE, Mandriva, Slackware, Arch Linux, or Debian system

**Removal Instructions**

1. To undo the changes to the Windows bootloader, simply boot Windows, and the uninstaller should begin. Press "OK", and it will undo the changes, or uninstall manually from "Add/Remove Applications". If you used Linux, and used the .deb/.rpm packages, uninstall the "unetbootin" package, or if you used the .sh version, use the command:
```
sudo unetbootin-uninst
```
2. To remove Ubuntu itself, see this guide: [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

**Running UNetbootin from a liveCD or using it to make a bootable USB net-install drive**

The .sh (shell script) version for GNU/Linux can operate in 3 different ways; installmode=tohost operates like the rpm/deb packages, chainloading off the existing grub install, installmode=nohost can be used off a liveCD/liveUSB when there is no existing OS installed, while installmode=usbdrive can be used to make a bootable net-install USB drive. Syntax and options are as follows:

If you are running this script from a host, hard-drive Linux install, and want the GRUB bootloader installed in /boot to be used, enter:

```
./unetbootin-fedora8rev49.sh installmode=tohost
```


Otherwise, if you are running this script from a liveCD or other live, non-hard drive media, or the installmode=tohost option fails, or you want to specify your target partition (targetpartition=/dev/sda1) or (optionally) the bootloader (bootloader=grub or bootloader=lilo), enter, in addition to the targetpartition and formatpartition options:

```
./unetbootin-fedora8rev49.sh installmode=nohost targetpartition=/dev/sda1 formatpartition=yes
```


Otherwise, if you want to install to a USB drive, enter, in addition to the targetpartition and formatpartition options:

```
./unetbootin-fedora8rev49.sh installmode=usbdrive targetpartition=/dev/sda1 formatpartition=yes
```

**Using UNetbootin If You Don't Have an OS Installed**

If you have a liveCD/liveUSB, boot it and use the UNetbootin .sh version as described above in the section for the "installmode=nohost" option, then reboot and the installer will start from the hard drive.

Alternatively, if the machine can boot off a USB drive, and you have access to another machine that can run Linux from a liveCD or hard drive, then make a bootable net-install USB drive using the UNetbootin .sh version as described above in the section for the "installmode=usbdrive" option, then boot the install-USB drive on the target machine and the installer will start.

If all else fails, or if you only have access to floppies, then first, download the [Debian minimal-install floppies](ftp://ftp.debian.org/debian/dists/testing/main/installer-i386/current/images/floppy). Then, install Debian. Once installed, download the UNetbootin deb package using wget $unetbootin.deb, install it using dpkg -i $unetbootin.deb, then once done, reboot, and select UNetbootin in the GRUB menu.

[B]
More Resources[/B]

A Fedora and CentOS specific guide is available at [http://ubuntuforums.org/showthread.php?t=543257](http://ubuntuforums.org/showthread.php?t=543257) and [http://forums.fedoraforum.org/showthread.php?p=859216](http://forums.fedoraforum.org/showthread.php?p=859216). A Fedora and Ubuntu guide is also available at [http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora_p4](http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora_p4)

A Mandriva specific guide is available at [http://forum.mandriva.com/viewtopic.php?p=371030](http://forum.mandriva.com/viewtopic.php?p=371030) and [http://ubuntuforums.org/showthread.php?p=3411772](http://ubuntuforums.org/showthread.php?p=3411772)

An OpenSuse specific guide is available at [http://opensuse.us/phpBB2/viewtopic.php?p=14851](http://opensuse.us/phpBB2/viewtopic.php?p=14851) [http://www.suseforums.net/index.php?showtopic=39081](http://www.suseforums.net/index.php?showtopic=39081) and [http://ubuntuforums.org/showthread.php?p=3411879](http://ubuntuforums.org/showthread.php?p=3411879)

An Arch Linux specific guide is available at [http://ubuntuforums.org/showthread.php?t=556230](http://ubuntuforums.org/showthread.php?t=556230) and [http://bbs.archlinux.org/viewtopic.php?pid=283021](http://bbs.archlinux.org/viewtopic.php?pid=283021)

A Vector Linux specific guide is available at [http://ubuntuforums.org/showthread.php?p=4062492](http://ubuntuforums.org/showthread.php?p=4062492)

A Slackware specific guide is available at [http://ubuntuforums.org/showthread.php?p=3720797](http://ubuntuforums.org/showthread.php?p=3720797) and [http://slackwarehelp.org/viewtopic.php?p=6427](http://slackwarehelp.org/viewtopic.php?p=6427)

**Notes For Vista Users**

Vista has its own partition manager, which can be started with the command:

```
diskmgmt.msc
```

It can be used to shrink the NTFS partition to make space for Ubuntu's partition, and may work better than Ubuntu's partitioner. Details on using the graphical tool are at [http://www.pro-networks.org/forum/viewstory.php?t=78111](http://www.pro-networks.org/forum/viewstory.php?t=78111) and [http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/](http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/)

Should the graphical tool not work, you can also use diskpart, a commandline tool:

```
diskpart
```

Details at [http://www.mydigitallife.info/2007/09/26/using-diskpartexe-as-disk-management-alternative-in-windows-vista-2000-2003-and-xp/](http://www.mydigitallife.info/2007/09/26/using-diskpartexe-as-disk-management-alternative-in-windows-vista-2000-2003-and-xp/) and [http://vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work/](http://vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work/)

**Installing Other Distributions Using UNetbootin**

Since UNetbootin allows for the usage of unmodified netboot kernel and initrds, it is possible to install any distribution that provides one, such as in the form of a mini-FTP-install iso. If installing another distribution on a one-time usage basis (for packaging and mass distribution, see the section below), first install another distribution using UNetbootin, download the netboot version of the desired distribution (generally available on the FTP server), extract the initrd and kernel files, and replace (on Windows) C:\unetbootin\ubnkern and C:\unetbootin\ubuninit, or (on Linux) /boot/ubnkern and /boot/ubninit with the netboot kernel and initrd files, respectively, then reboot and the installer for the desired distribution should start.

**Packaging UNetbootin for Other Distributions**

Thanks to UNetbootin's portable architecture, it is easy to add support for other distributions. If you would like to create UNetbootin packages for other distributions, first make sure you have installed the "bzr", "alien", "fakeroot", and "wine" utilities, which are installable through your package manager, then check out the source with the command:

```
bzr checkout http://bazaar.launchpad.net/~gezakovacs/unetbootin/devel-new
```

Then add the name of the distribution, referred to here as {distroname}, into the file "targetdistros" in the checked-out source, add the netboot initrd and kernel, with the naming scheme "ubninit-{distroname}" and "ubnkern-{distroname}" into the "initkern" folder, then cd to the source directory, and run the command:

```
./build
```

Then, the "exe", "deb", "rpm", and "sh" packages for distribution will be created in the "dist" directory. More info is available in the readme file in the source folder.

**License/Source Code**

This is licensed under the GNU GPL. Source code is available at the launchpad page at [https://launchpad.net/unetbootin](https://launchpad.net/unetbootin)

**Credits**

This guide was written from scratch by me. The installer was created using NSIS [http://nsis.sourceforge.net/Main_Page](http://nsis.sourceforge.net/Main_Page) the bootloader came from grub4dos [http://grub4dos.sourceforge.net/](http://grub4dos.sourceforge.net/) and the netboot initrd/kernel came from Ubuntu.

**Known Issues**

If you encounter errors on reboot such as "Error 17" or "File not found" at the grub screen, try defragmenting your hard drive and running "chkdsk /r"

If you encounter errors following the bootup and during the operation of the debian-installer, consult the netboot initrd, debian-installer, and ubuntu installation howtos and documentation

If you encounter errors in Ubuntu, consult the general ubuntu documentation and the forums

If you encounter errors in the Windows portion of the installer, post a question here

Use this guide at your own risk.

---

### Post by tuxcantfly on 2007-04-30
Ignore this, I'm subscribing to this thread...

---

### Post by nonlinear on 2007-05-06
wow, so glad i found this, this is exactly what i need right now!  having problems burning error-free discs, and used teh regular WUBI but want a 'real' install....  i think this feature should be incorporated into the next release

has anyone tried this?  how did it go?  is it possible to put a pre-existing ubuntu iso in the directory and bypass the download stage?

---

### Post by tuxcantfly on 2007-05-06
> is it possible to put a pre-existing ubuntu iso in the directory and bypass the download stage?

No, it's a netboot installer, so you can't use an iso; you'll have to download while installing

> i think this feature should be incorporated into the next release

We'll have it incorporated eventually, though using a different method (install from alternate iso instead of netboot) but probably not in the next release, as we're still working out issues with the loopmounted installation.

> has anyone tried this? how did it go?

It works the same way as the standard netboot install does, only without any cds needed, so if netboot works, this will work fine too. After install, you'll just have a plain ubuntu install.

---

### Post by chochem on 2007-05-12
I used this to successfully install Feisty. I know I ought to have thought of it myself but I think a mention of "have your IP-address-gateway-dns-server-info at the ready" should be included in the howto. That being said the installation went like a charm once I had rebooted and collected the needed info. 

The Windows bit is perfect: you run it (takes two seconds) and don't have to do anything part from OK'ing a reboot. Once you're done and boot into Windows again, you're presented with an uninstaller which works just as elegantly simply. As for the actuall installation process, it's pretty much the same as using the text-based alternate install cd. As long as that doesn't frighten you, I'll definitely recommend this. 

One slight annoyance was that the installation process was halted halfway through to ask what desktop was required (ubuntu/kubuntu/xubuntu/etc.) I would have prefered to see this at the start with the other installation choices so that the installer could be left on its own for the some 30 minutes the process took.

---

### Post by Mr|C on 2007-05-19
Can this be used to install 7.04 on an external Hard drive?

---

### Post by tuxcantfly on 2007-05-19
> Can this be used to install 7.04 on an external Hard drive?

Yes, it mimics the standard ubuntu behavior, so it should be able to, just follow the way you would install with a standard ubuntu install.

---

### Post by Mr|C on 2007-05-19
Thanks for the fast reply. I'll let you know how it goes :)

---

### Post by Mr|C on 2007-05-19
Ok, I'm worried :P It's installed everything to my C:/ drive, when I want it to go to my Z:/ drive (The letter of the USB external). Is this okay?

---

### Post by tuxcantfly on 2007-05-19
> Ok, I'm worried :P It's installed everything to my C:/ drive, when I want it to go to my Z:/ drive (The letter of the USB external). Is this okay?

No, that's not ok, installing to a usb drive is a bit tricky, you might have better luck if you follow instructions here: 
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)
[http://frontier05.blogspot.com/2006/01/installing-ubuntu-to-external-usb.html](http://frontier05.blogspot.com/2006/01/installing-ubuntu-to-external-usb.html)

---

### Post by Lucho77 on 2007-05-21
> **chochem said:**
> I used this to successfully install Feisty. I know I ought to have thought of it myself but I think a mention of "have your IP-address-gateway-dns-server-info at the ready" should be included in the howto. That being said the installation went like a charm once I had rebooted and collected the needed info. 

The Windows bit is perfect: you run it (takes two seconds) and don't have to do anything part from OK'ing a reboot. Once you're done and boot into Windows again, you're presented with an uninstaller which works just as elegantly simply. As for the actuall installation process, it's pretty much the same as using the text-based alternate install cd. As long as that doesn't frighten you, I'll definitely recommend this. 

One slight annoyance was that the installation process was halted halfway through to ask what desktop was required (ubuntu/kubuntu/xubuntu/etc.) I would have prefered to see this at the start with the other installation choices so that the installer could be left on its own for the some 30 minutes the process took.

It does not work for me, I am trying to install Ubuntu in a 'Dell Inspiron 5000 laptop' with Win98SE 0n it, No CD-Rom, 64 MB RAM, it has 2 partitions Win98SE uses 2 GB and the other is a 7 GB for now as logical partition, all it does is bounce back to windows asking if want to unistall 'Wubi-7.04-netboot'.
Please advice. Thanks.

---

### Post by tuxcantfly on 2007-05-21
> It does not work for me, I am trying to install Ubuntu in a 'Dell Inspiron 5000 laptop' with Win98SE 0n it, No CD-Rom, 64 MB RAM, it has 2 partitions Win98SE uses 2 GB and the other is a 7 GB for now as logical partition, all it does is bounce back to windows asking if want to unistall 'Wubi-7.04-netboot'.
Please advice. Thanks.

Hmm... is there a C:\grub or C:\grldr or C:\menu.lst file? In C:\config.sys, do you see anything saying "grub", "ubuntu", or "grldr"? I never tested this on Win9x, so I don't think I can really help you, unless it's an issue with the timeout, have you checked C:\config.sys and have the timeout set to 10 or more?

Anyhow, this wubi-netboot method is kinda becoming obsolete, you might want to just use the standard Wubi (or Lubi, [http://ubuntuforums.org/showthread.php?t=442597](http://ubuntuforums.org/showthread.php?t=442597) if you're using linux) to install,we've already incorporated most of this version's features into that, see  [http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html) for the site and [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234) for the forums

---

### Post by Lucho77 on 2007-05-21
Thanks 'tuxcantfly', if this is obsolete i will go for the 'standard wubi' option, I will let you know how this goes, I'll see you in the newer thread. Thanks again.

---

### Post by Robert98374 on 2007-05-23
Just subscribing to the post this looks awesome :-)

---

### Post by ksglp on 2007-06-11
hiya, i'm stuck here;

2. Click "OK" to reboot

3. Select "Ubuntu" from the menu list

when i click OK to reboot, it reboots back to Windows like it always did, with an uninstall programme popping up,

select Ubuntu from what menu list?
where is this menu?

cheers for any help,

Jordan

---

### Post by tuxcantfly on 2007-06-11
whoops, seems like your timeout is set to 0. Open C:\boot.ini, and find the line which says "timeout 0" or "timeout somenumber", and replace whatever that number is with 30, then it should show up.

PS, which windows version are you using?
PS, you might want to check out Wubi (for windows users) or Lubi (for linux users), as they have most of the functionality of this already, and it might work better for you, the only advantage this one has left over Wubi/Lubi is that it installs to a real partition, rather than a loopmounted partition. Wubi is at [http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html) and Lubi is at [http://ubuntuforums.org/showthread.php?t=441918](http://ubuntuforums.org/showthread.php?t=441918)

---

### Post by ksglp on 2007-06-12
OK, still having problems, all i want is to have a go of Ubuntu!

Had a look for that boot file in C:/ - there is a file called boot but it seems to contain absolutely nothing and is 0kb in size, so no timeout to replace with 30

downloaded wubi installer, got all the way to the end eventually where it asked me to reboot, i did so, straight back into Windows (2000 i think)

does anyone know what the problem is here?

all help is very much appreciated

---

### Post by tuxcantfly on 2007-06-12
> Had a look for that boot file in C:/ - there is a file called boot but it seems to contain absolutely nothing and is 0kb in size, so no timeout to replace with 30

Seems like your boot.ini isn't stored on C:\, did you check D:\ or the other drives for a boot.ini file? Find a boot.ini file (make sure you have hidden and system files showing) that looks something like this:

```
[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
```

and if the timeout says 0, replace it with 30, and at the end put in this line:

```
C:\grldr="Ubuntu"
```

Also make sure that grldr is in C:\; if not, find it from another drive and copy it to C:\grldr

---

### Post by ksglp on 2007-06-12
there is a file on C:/ called boot.ini, but it is empty, could i just copy and paste that code in?

D:/ is the CD drive

grldr is stored in C:/

---

### Post by tuxcantfly on 2007-06-14
> there is a file on C:/ called boot.ini, but it is empty, could i just copy and paste that code in?

D:/ is the CD drive

grldr is stored in C:/

That sounds rather strange... are you using a pristine install of Windows 2000, or has the installation been upgraded from other versions? Well anyhow, since the boot.ini file is empty, pasting in the lines shouldn't do any harm, though if that's the case, it probably won't fix the issue either, though there shouldn't be much harm in trying... Are you sure you're using windows 2000, not ME or some other non-NT windows? Is there a C:\config.sys file? Try editing that one if it exists...

---

### Post by ksglp on 2007-06-14
might be ME actually, certainly acts like it has ME anyway!

there is a config.sys file, it says


 [menu] 
 menucolor=15,0 
 menuitem=windows,Windows 
 menuitem=grub,Ubuntu 
 menudefault=windows,30 
 [grub] 
 device=grub.exe 
 [windows] 
  
 [menu] 
 menucolor=15,0 
 menuitem=windows,Windows 
 menuitem=grub,Ubuntu 
 menudefault=windows,30 
 [grub] 
 device=grub.exe 
 [windows] 
 
don't know why it repeats itself, but it does
what should I edit it to?

sorry for all the hassle,
 i do really want to try this OS, but i know none of the intricacies of system files and stuff like that so your guidance really is appreciated

---

### Post by maty dews on 2007-06-14
hi would i be able to use this method to install feisty on a partion on my harddrive, without suffering the bug with ati cards? because at the moment it hangs before even getting onto the live cd, so woundering if this would be a viable option?

i tryed running wubi to run it off a virtual hard drive but i seemed to have similar issues their

any help would be great

---

### Post by Ozdemon on 2007-06-26
I have an old Gateway solo 9300 laptop.  It was choking on xp, so I thought I would switch to Ubuntu.  I used this method and all went well until the installation phase hung at 6%.  After waiting 1.5 hrs with no change, I shut down.  Now I have nothing as the HDD was wiped - I'm not complaining as I was aware of the risk.

However I would appreciate any help.  The laptop has a dead cd drive, but workable floppy and usb ports and I have an eternal usb/firewire cd drive.  The bios will not boot from a usb device and no bios update is available.  

So, I was thinking what I need to do is make a boot floppy of some sort that will enable the laptop to see the external usb cd drive and install Ubuntu from there.

I looked at the guide to using smart boot manager  [https://help.ubuntu.com/community/SmartBootManagerHowto]("https://help.ubuntu.com/community/SmartBootManagerHowto") , but I could not work it out.  I don't even know which OS I should be using because I don't have an OS anymore (or do I?).

So in short, is there any flavor of floppy that will enable me to see the external usb cd drive and install Ubuntu?

---

### Post by tuxcantfly on 2007-06-26
> So in short, is there any flavor of floppy that will enable me to see the external usb cd drive and install Ubuntu?

I'm not aware of any floppies that can boot from external usb cd drives (SBM can't), so what I'd do is install a minimal debian system using netboot floppies, then subsequently apt-get yourself an ubuntu installation...

Guide on installing debian using netboot floppies:
[http://linux.simple.be/debian/floppy](http://linux.simple.be/debian/floppy)

Detailed procedures on creating floppies from image files (since you can't boot your computer, you'll have to do the floppy creation process on another computer):
[http://www.debian.org/releases/stable/i386/ch04s03.html.en](http://www.debian.org/releases/stable/i386/ch04s03.html.en)

Then, after you're done installing a minimal debian system, to turn it into an ubuntu system, this should do the job (enter these in the terminal of the minimal debian install):

```
su root
echo \
"
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted multiverse universe
deb http://security.ubuntu.com/ubuntu feisty-security main restricted multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted multiverse universe
" > /etc/apt/sources.list
apt-get update
apt-get dist-upgrade
apt-get install ubuntu-desktop
```

Then reboot and you should have an ubuntu install, though note that I've never tested this procedure myself, so I can't guarantee that it'll work...

---

### Post by Ozdemon on 2007-06-26
> **tuxcantfly said:**
> I'm not aware of any floppies that can boot from external usb cd drives (SBM can't), so what I'd do is install a minimal debian system using netboot floppies, then subsequently apt-get yourself an ubuntu installation...

...

Wow, thanks for the quick reply.  :D
The floppy drive is internal - the cd drive is external usb.  I will get on to your suggestion right now.  Many thanks.

---

### Post by Ozdemon on 2007-06-27
I tried to install over Debian.

What happened was:
(1) I must have missed something, because I ended up doing a full install of Debian;

(2) On putting in the cmd apt-get update, it failed because of something to do with no public key;

(3) I pressed on and entered apt-get dist-upgrade. This downloaded the about 490 mb and then started extracting and replacing

(4) I entered apt-get install ubuntu-desktop and the installation started - but I got an error code (1)

(5) I restared, but Debian gave me lots of warning messages about things not working.  However I did get to the desktop, but Debian is not looking to healthy.

I am loath to give up - so I am glad to try any more suggestions.

**UPDATE**
My hard drive failed during a re-install, so I have to give up on that laptop (it's now in the bin).  However, I am now keen to install Ubuntu, so I will buy a 2nd hand laptop that DOES have a bootable cd drive.

Anyway, thanks for the help.

---

### Post by zach12 on 2007-06-28
cool i'm installing ubuntu on a new laptop (don't have cd )it older but new to me i'll use this

---

### Post by zach12 on 2007-06-30
hello
i'm installing ubuntu on a laptop useing this howto
when i try to get a mirror archive of ubuntu from us.archive.ubuntu.com(i'm in the usa)
i get a error message here it is
Quote:
bad mirror archive the specifed mirror archive is not avaiable try a different mirror archive

---

### Post by tuxcantfly on 2007-06-30
> bad mirror archive the specifed mirror archive is not avaiable try a different mirror archive

Seems like it doesn't manage to detect your internet connection, make sure it's connected (and if you're using wireless, try using ethernet, that might work), otherwise, you'll have to use either Wubi [http://wubi-installer.org/](http://wubi-installer.org/) (if you have Windows installed) or Lubi [http://ubuntuforums.org/showthread.php?t=441918](http://ubuntuforums.org/showthread.php?t=441918) (if you have Linux installed) since only those can do an offline install; they install to loopmounted partitions rather than a real partition, but you can transfer them to real partitions (making a real ubuntu install) using LVPM [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

---

### Post by zach12 on 2007-06-30
ok i have not used the wifi on windows 
i will config the wifi on windows

---

### Post by tuxcantfly on 2007-06-30
> ok i have not used the wifi on windows
i will config the wifi on windows

I doubt that will fix your problem; Ubuntu isn't affected by the Windows wifi configuration, you likely have a wifi chipset that isn't supported by default in Ubuntu; you should use an ethernet cable instead of wifi for the install, and configure the wifi in Ubuntu (you'll probably need ndiswrapper) later, once Ubuntu is installed.

---

### Post by ksglp on 2007-07-05
> **ksglp said:**
> might be ME actually, certainly acts like it has ME anyway!

there is a config.sys file, it says


 [menu] 
 menucolor=15,0 
 menuitem=windows,Windows 
 menuitem=grub,Ubuntu 
 menudefault=windows,30 
 [grub] 
 device=grub.exe 
 [windows] 
  
 [menu] 
 menucolor=15,0 
 menuitem=windows,Windows 
 menuitem=grub,Ubuntu 
 menudefault=windows,30 
 [grub] 
 device=grub.exe 
 [windows] 
 
don't know why it repeats itself, but it does
what should I edit it to?

sorry for all the hassle,
 i do really want to try this OS, but i know none of the intricacies of system files and stuff like that so your guidance really is appreciated

anyone know?

---

### Post by tuxcantfly on 2007-07-05
> anyone know?

Sorry, I don't know anything about winME (the guy who did the win9x bootloader portion of Wubi, Hello1024, has disappeared from the forums), I'd just use a normal cd-based installation, or if you have a floppy, you could also do this:

1. Download the Super Grub Disk from here: [http://forjamari.linex.org/frs/download.php/554/super_grub_disk_english_floppy_0.9590.img](http://forjamari.linex.org/frs/download.php/554/super_grub_disk_english_floppy_0.9590.img)

2. Use this guide to put it on a floppy: [http://www.pamarsystems.com/raw.html](http://www.pamarsystems.com/raw.html)

3. Boot the Super Grub Disk floppy (it should just boot if you keep it in the computer, but you might have to change the startup order in your bios to boot from floppy first), press "c" to go to a command-line at the GRUB boot prompt, and enter these commands:
```

root (hd0,0)
configfile /menu.lst
```

Hope that helps... If it doesn't, try entering these commands on the GRUB boot prompt:

```
find --set-root /wubi
kernel /wubi/linux
initrd /wubi/initrd.gz
```

---

### Post by jazzgossen on 2007-07-11
This sounds good... but what if I don't have Windows installed on the computer? I have a computer with an empty HDD, and Slax Linux on a bootable USB stick. Do you know how to netboot from this setup?

---

### Post by tuxcantfly on 2007-07-11
> This sounds good... but what if I don't have Windows installed on the computer? I have a computer with an empty HDD, and Slax Linux on a bootable USB stick. Do you know how to netboot from this setup?

Extract the initrd and kernel using p7zip-full (7z x Wubi-netboot-7.04.exe), then place those files into the /boot folder of your Slax Linux USB install, then add to /boot/grub/menu.lst in the Slax USB install:

```
title Ubuntu
kernel /boot/linux
initrd /boot/initrd.gz
boot
```

Substitute the names of the kernel and initrd for the real ones, and remeber to set your timeout to greater than 0, then boot the Slax install, select Ubuntu when the grub menu shows up, and it should start up the netboot.

---

### Post by pieisgood4589 on 2007-07-11
is there any way to switch to ubuntu completely with this wubu and delete Windows XP? PLEASE! I WOULD LOVE THAT!

---

### Post by tuxcantfly on 2007-07-12
> is there any way to switch to ubuntu completely with this wubu and delete Windows XP? PLEASE! I WOULD LOVE THAT!

[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

---

### Post by tuxcantfly on 2007-07-31
> is there any way to switch to ubuntu completely with this wubu and delete Windows XP? PLEASE! I WOULD LOVE THAT!

This version allows you to install to a dedicated partition and delete WinXP, but if you already installed using Wubi, just use LVPM (previous post) to transfer it over to a dedicated partition

---

### Post by tuxcantfly on 2007-07-31
Downloads have moved to sourceforge, at [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=240555](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=240555)

---

### Post by tuxcantfly on 2007-08-06
I've renamed the project and program to UNetbootin, in order to avoid naming confusion with Ubuntu and Wubi. I'm currently setting up a more elegant site on the Sourceforge page.

---

### Post by tuxcantfly on 2007-08-07
UNetbootin now has its own site and guide at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by tuxcantfly on 2007-08-08
I've finished my latest release (revision 21) of UNetbootin, and it's ready to download via sourceforge.

New features:

In addition to Ubuntu 6.06, 6.10, and 7.04, Debian Sid and Debian Etch are now supported for installation, just download the appropriate files to install

In addition to Windows, you can now also install using Linux. If using a debian-based distro (like Ubuntu) just install the deb package, and if using another distro, use the self-extracting sh file.

Everything is now handled automatically by the build script, so adding support for another distro is trivial work; just add the distro's name into a line in the build script and place the distro's initrd and kernel in a directory, and everything else is automatically handled, down to the building of the 3 installer versions (sh, deb, and exe). Just contact me through the details on my launchpad page or pm me if you want to have any distro added; just provide links to the latest netboot initrd and kernel (or archive containing the two) and I'll build it in to UNetbootin so that .

---

### Post by Zwendel on 2007-08-09
Hi, I tried UNetbootin to solve a "refuces to boot from CD" problem, worked like a charm.

Only prob I had, after the basic install it asks you what else do you want? So I mark LAMP and Ubuntu desktop, installation starts and after reboot the Ubuntu desktop works just fine, but I don't find any trace of the LAMP stuff. After a quick peek at the Synaptix it seems it didn't get installed, php, apache etc are not marked there.

What did I do wrong? Can I still get the LAMP or do I go about it manually installing the webserver components I need? (the laptop functions as a local development/test sever)

Cheers and anyway thanks for UNetbootin!

---

### Post by Hojer on 2007-08-13
Hi, I gather from previous post that I was supposed to get the question what to install, for instance Ubuntu desktop. I did not.

I did choose Xubuntu along the way, the install finished and the computer rebooted. I then came to a command line where I was promted to log on, which worked fine.

But... how do I start the desktop? :| I'm a total noob, so anything but a Windows-like desktop is way over my head. Please advise.

BR
Hojer

---

### Post by RaverDK on 2007-08-13
Have just read this hole tread, and i must say that its a pretty cool pice of software... for sure a think to remember when running out of CD's ;-)

Nice that you keep soo good support throu this forum, keep up the good work mate... 

boom

---

### Post by JJM02351 on 2007-08-19
Are you able to also install Xubuntu with this tool?

---

### Post by Zwendel on 2007-08-20
> **JJM02351 said:**
> Are you able to also install Xubuntu with this tool?

Yes you are. First you install the basics and then the rest of the options is presented to you to choose from. Among those is the Xubuntu desktop.
Cheers

---

### Post by Apt403 on 2007-08-22
How long should the partition portion of the install take to complete? I'm using the minimiun partition size, about 41gb, on a 250gb drive. It's been sitting at 0% for about 10 minutes now...

Edit: NVM, I got some kind of error, and I exited the installer. CHKDSK just finished doing its thing.

I think I'll wait o install Ubuntu until I can get down to Best Buy and buy some blank CD-RWs...

---

### Post by tuxcantfly on 2007-08-23
I've added support for Ubuntu 7.10 in UNetbootin, it's available for download from the usual page at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

Note that since Ubuntu 7.10 is still undergoing development, it shouldn't be used on production machines, unless you're doing development or want the bleeding-edge

---

### Post by tuxcantfly on 2007-08-23
I've added support for Debian Lenny in UNetbootin, it's available for download from the usual page at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by tuxcantfly on 2007-09-04
I've added support for Fedora 7, it's available for download at the usual spot at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

---

### Post by tuxcantfly on 2007-09-04
I've just added RPM packages for Fedora, Suse, and Redhat users, download at the usual spot at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

---

### Post by tuxcantfly on 2007-09-04
I posted a guide for installing Fedora 7 using UNetbootin at [http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540) (ubuntuforums) and [http://forums.fedoraforum.org/showthread.php?goto=newpost&t=165622](http://forums.fedoraforum.org/showthread.php?goto=newpost&t=165622) (fedoraforums)

---

### Post by neo_timmy on 2007-09-05
hey tuxcantfly can u pls build fedora 7 uNetbootin with ntfs read only driver. my image is on the ntfs drive & it doesnt recognize it. or can u pls tell me how can i make it recogznie it. i tried using the ntfs driver available on rpm.livn.org. wasnt able to successfully add to modules.cgz

cheers

---

### Post by tuxcantfly on 2007-09-05
> **neo_timmy said:**
> hey tuxcantfly can u pls build fedora 7 uNetbootin with ntfs read only driver. my image is on the ntfs drive & it doesnt recognize it. or can u pls tell me how can i make it recogznie it. i tried using the ntfs driver available on rpm.livn.org. wasnt able to successfully add to modules.cgz

cheers

The default Fedora netboot initrd doesn't support NTFS, and I'd rather not try modifying it too much or it'll break and become unmaintainable (I'd have to modify the initrd every time Fedora is updated). For now, what I'd do is boot the Ubuntu or Debian UNetbootin version, and allow it to proceed until it reaches the "partitioning" section, and there, shrink your NTFS partition and make a new (FAT32) partition, allow it to create the new partition, and before it actually starts installing, just reboot, and move the iso file over to the fat32 partition, and reboot back into the Fedora installer, that way you can get Fedora to recognize and install using the iso file. If all else fails, you can just tell it to fetch it from HTTP or FTP, though that'll probably take quite a while.

---

### Post by Nephus on 2007-09-06
Well, everything was going great with the install, but now I'm stuck at a screen that says something to the effect of

6%
Please Wait...

for the last hour.

I'm a little timid about trying to restart this thing if it's stuck (I have no CD drive on this laptop, so I don't wanna kill my windows install by accident)  but it doesn't seem to be going anywhere at this point.

Any suggestions?


edit: nevermind.  As is true with anything from computers to cars, the moment you try to get it fixed, it stops doing it.  I just checked on it and it was at 67% doing something now.

---

### Post by tuxcantfly on 2007-09-06
> **Nephus said:**
> Well, everything was going great with the install, but now I'm stuck at a screen that says something to the effect of

6%
Please Wait...

for the last hour.

I'm a little timid about trying to restart this thing if it's stuck (I have no CD drive on this laptop, so I don't wanna kill my windows install by accident)  but it doesn't seem to be going anywhere at this point.

Any suggestions?

Give it time. For some reason, while caching the files (downloading from the web), the counter remains at 6%. If you're on a DSL connection, it will stay there at 6% for around 2 hours, since it's downloading 700MB of files off the internet.

---

### Post by cheapgadget1 on 2007-09-11
I used UNetbootin to install xubuntu fiesty fawn on my computer last night and the install said it completed and then needed to reboot to start the system.  I did this but the reboot gets to the starting up screen just like my Ubuntu install from Live CD that I have on another computer and then after a long pause it fires into a long string of text (i.e. starting networking   [OK]).  It stops after Loading local boot scripts  [ok].  If I hit enter at this point it take me to a text log in which it accepts and then puts me at a command prompt.  

I am a total noob to Linux and command line for that matter.  I have been using Ubuntu on another machine and really like it.  I wanted to load Xubuntu on this older machine to use an an internet tablet/email machine but I am totally stuck.  

I have tried commands that other post suggested such as startx and sudo dpgk-reconfigure xserver-xorg to no avail.  I need help and it need to be very basic as I am new to this.  If this is a repeat of another post I am sorry I searched for an answer on my own last night for nearly 3 hours. Thanks in advance for any help.

---

### Post by tuxcantfly on 2007-09-11
> **cheapgadget1 said:**
> I used UNetbootin to install xubuntu fiesty fawn on my computer last night and the install said it completed and then needed to reboot to start the system.  I did this but the reboot gets to the starting up screen just like my Ubuntu install from Live CD that I have on another computer and then after a long pause it fires into a long string of text (i.e. starting networking   [OK]).  It stops after Loading local boot scripts  [ok].  If I hit enter at this point it take me to a text log in which it accepts and then puts me at a command prompt.  

I am a total noob to Linux and command line for that matter.  I have been using Ubuntu on another machine and really like it.  I wanted to load Xubuntu on this older machine to use an an internet tablet/email machine but I am totally stuck.  

I have tried commands that other post suggested such as startx and sudo dpgk-reconfigure xserver-xorg to no avail.  I need help and it need to be very basic as I am new to this.  If this is a repeat of another post I am sorry I searched for an answer on my own last night for nearly 3 hours. Thanks in advance for any help.

Hmm strange, that isn't supposed to happen, for some reason every time it was reported it was when users were running xubuntu, I'll look into it... I have a hunch that for some reason the xubuntu-desktop packages weren't downloaded and installed...

Anyhow, for now, try doing this:

```

sudo apt-get update
sudo apt-get install xubuntu-desktop
sudo killall gdm
sudo gdm
```

see if it works then

---

### Post by cheapgadget1 on 2007-09-11
> **tuxcantfly said:**
> Hmm strange, that isn't supposed to happen, for some reason every time it was reported it was when users were running xubuntu, I'll look into it... I have a hunch that for some reason the xubuntu-desktop packages weren't downloaded and installed...

Anyhow, for now, try doing this:

```

sudo apt-get update
sudo apt-get install xubuntu-desktop
sudo killall gdm
sudo gdm
```

see if it works then

Thanks tuxcantfly,
I will try that when I get back in front of the computer.  If it is at all helpful, I am having this problem on an HP Omnibook XE3, it has a 1Ghz Celeron Processor, and a 20G HDD, running 196 M Ram.  Thanks again I will post the results as soon as I have them.

---

### Post by tuxcantfly on 2007-09-11
I've updated the UNetbootin Ubuntu 7.10 (Gutsy) builds to be in line with the new kernel that's being used by default, you can download the new builds at [https://sourceforge.net/project/showfiles.php?group_id=198821](https://sourceforge.net/project/showfiles.php?group_id=198821)

---

### Post by cheapgadget1 on 2007-09-11
> **tuxcantfly said:**
> Hmm strange, that isn't supposed to happen, for some reason every time it was reported it was when users were running xubuntu, I'll look into it... I have a hunch that for some reason the xubuntu-desktop packages weren't downloaded and installed...

Anyhow, for now, try doing this:

```

sudo apt-get update
sudo apt-get install xubuntu-desktop
sudo killall gdm
sudo gdm
```

see if it works then

Hello tuxcantfly,
I entered the code you suggested and it worked almost.  It now launches into xubnuntu successfully, however, the splash screen and desktop at stuck in a 320x200 pixel resolution and I can't change it via the gui and as stated earlier.  I have no idea how to make these changes via command line.  I am nearly certain this is a problem of my own making while I was messing with the xserver per other posts.  I am guessing it has something to do with the driver settings or something.  Again your help is greatly appreciated.
Cheers,
cheapgadget1

---

### Post by tuxcantfly on 2007-09-12
> **cheapgadget1 said:**
> Hello tuxcantfly,
I entered the code you suggested and it worked almost.  It now launches into xubnuntu successfully, however, the splash screen and desktop at stuck in a 320x200 pixel resolution and I can't change it via the gui and as stated earlier.  I have no idea how to make these changes via command line.  I am nearly certain this is a problem of my own making while I was messing with the xserver per other posts.  I am guessing it has something to do with the driver settings or something.  Again your help is greatly appreciated.
Cheers,
cheapgadget1

You'll need to install the graphics drivers for your card.

If you're using an ATI card:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

If you're using an Nvidia card:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by cheapgadget1 on 2007-09-12
This laptop has a build in intel 830MG controller.  Can you point me to the thread for that driver set.  Thank you for your patience with this noob.

Cheers

---

### Post by tuxcantfly on 2007-09-12
> **cheapgadget1 said:**
> This laptop has a build in intel 830MG controller.  Can you point me to the thread for that driver set.  Thank you for your patience with this noob.

Cheers

See here:

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

The "Install newer modesetting Intel video driver" section is probably what you need. If that doen't fix the issue, try [https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver) and if that doesn't work either just seach the forums for "915resolution", there are a variety of different guides here for different configurations.

---

### Post by aristhankful on 2007-09-20
To the author(s) of Win/GnuLinux binary,

I just wanted to thank you (all) for contributing to the GNU community.  The uNetbootin utility proved really useful to me as I had to install a copy of Ubuntu on my Thinkpad X40, which doesn't have a CD/DVD-rom.

Many thanks for your efforts people. You made my life a heck of a lot easier with this last install.

Peace.

---

### Post by tuxcantfly on 2007-09-21
> **aristhankful said:**
> To the author(s) of Win/GnuLinux binary,

I just wanted to thank you (all) for contributing to the GNU community.  The uNetbootin utility proved really useful to me as I had to install a copy of Ubuntu on my Thinkpad X40, which doesn't have a CD/DVD-rom.

Many thanks for your efforts people. You made my life a heck of a lot easier with this last install.

Peace.

Thanks. Anyhow, I've added support for Arch Linux in the latest build, download it at the usual spot at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821) I posted the archlinux-specific guide at [http://ubuntuforums.org/showthread.php?p=3401421](http://ubuntuforums.org/showthread.php?p=3401421) and [http://bbs.archlinux.org/viewtopic.php?pid=283021](http://bbs.archlinux.org/viewtopic.php?pid=283021)

---

### Post by Ramthebuffs on 2007-09-21
I had the same issue with a freeze in the boot section while booting.  I'm pretty sure I selected to use ubuntu desktop.  I hit enter after selecting it in the install.  However, it immediately advanced rather than filling the [*] like I thought it would so maybe I did it wrong.  Anyway, rightnow I'm either installing or reinstalling ubuntu desktop.

btw, I'm doing the 7.04 install.

---

### Post by tuxcantfly on 2007-09-21
> **Ramthebuffs said:**
> I had the same issue with a freeze in the boot section while booting.  I'm pretty sure I selected to use ubuntu desktop.  I hit enter after selecting it in the install.  However, it immediately advanced rather than filling the [*] like I thought it would so maybe I did it wrong.  Anyway, rightnow I'm either installing or reinstalling ubuntu desktop.

btw, I'm doing the 7.04 install.

When choosing desktops, you have highlight and to use the <space> button to mark Ubuntu, Xubuntu, Kubuntu, and/or the other desktops, and you can only press <enter> AFTER it has been marked with the *. Simply highlighting and pressing <enter> will not select the package, and will only install a minimalist, command-line-only system. I've updated the first post accordingly since there seems to be plenty of confusion over this.

---

### Post by tuxcantfly on 2007-09-22
I've added support for installing Mandriva 2007 using UNetbootin, download at the usual spot at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

A guide to installing Mandriva with UNetbootin is at [http://forum.mandriva.com/viewtopic.php?p=371030](http://forum.mandriva.com/viewtopic.php?p=371030) and [http://ubuntuforums.org/showthread.php?p=3411772](http://ubuntuforums.org/showthread.php?p=3411772)

---

### Post by tuxcantfly on 2007-09-23
I've added support for installing OpenSuse 10.2 using UNetbootin, usual download spot at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

OpenSuse specific guide at [http://www.suseforums.net/index.php?showtopic=39081](http://www.suseforums.net/index.php?showtopic=39081) and [http://ubuntuforums.org/showthread.php?p=3411879](http://ubuntuforums.org/showthread.php?p=3411879)

---

### Post by tuxcantfly on 2007-09-23
I've added some screenshots to the guide, see [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) also I've used UNetbootin to allow for using Parted Magic to boot, so that it can be used as a full-fledged partitioning application, with all o fGParted's functions, if you only have Windows; simply download the exe version of Partition Manager at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821) if you're using Linux, though, use the deb, rpm, or sh packages.

---

### Post by tuxcantfly on 2007-09-24
Just updated the Ubuntu 7.10 (Gutsy) builds, get it while it's fresh! Download at usual spot at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

---

### Post by Kobalt on 2007-09-24
Glorious tool ! Very very usefull... 
Bravo. ;)

---

### Post by tuxcantfly on 2007-09-24
As some have noticed, Arch Linux's FTP is undergoing a transition in repos, thus breaking FTP installation. For now, use this workaround to fix it, if you're installing Arch Linux using UNetbootin (essentially, download the arch iso first and have the installer use that instead of FTP): [http://bbs.archlinux.org/viewtopic.php?pid=284090#p284090](http://bbs.archlinux.org/viewtopic.php?pid=284090#p284090)

---

### Post by tuxcantfly on 2007-09-28
Since the new Ubuntu 7.10 beta has just come out, complete with a different kernel and initrd (thus breaking UNetbootin), I've updated the UNetbootin 7.10 packages with the latest kernel and initrd so that it now installs properly; hopefully, with the kernel freeze coming up soon, there shouldn't be any more updates to the Gutsy kernel that'll break UNetbootin. Usual download spot at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

---

### Post by gradedcheese on 2007-09-30
Hey, thanks for the pointer to UNetbootin.  With its help, Ubuntu 7.10 is happily installing on my [Fit-PC]("http://www.fit-pc.com/") :)

---

### Post by nooby on 2007-09-30
> "have your IP-address-gateway-dns-server-info at the ready"
Seems this is still missing from the text on how to? 
I know my IP but have no clue on the gateway or dns? Does my windows have that one stored somewhere? 

For us who are new to Linux it would help to have a short text on how much each partition needs. Or have I failed to find that part? 

Should one defrag windows xp first so the partitioning is safer?

---

### Post by tuxcantfly on 2007-10-01
> **nooby said:**
> Seems this is still missing from the text on how to? 
I know my IP but have no clue on the gateway or dns? Does my windows have that one stored somewhere? 

For us who are new to Linux it would help to have a short text on how much each partition needs. Or have I failed to find that part? 

Should one defrag windows xp first so the partitioning is safer?

Don't worry about the IP/dns/gateway stuff, just accept the defaults, they'll work fine (I presume you're using a plain DSL/Cable connection, with a dynamic address; if you're running on a static address, you can usually get the details by navigating your web browser to [http://192.168.0.1](http://192.168.0.1) )

As for the partitioning, just let it do the automatic partitioning (make sure to select the option that says "resize partition" not "delete partitions" so that your windows install doesn't get wiped out), that'll work fine, but if you need details for some more elaborate partitioning schemes, see [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Defragging might be helpful, though it's usually not necessary, though you may want to do it just as a precaution.

---

### Post by nooby on 2007-10-02
Thanks for such detailed answer. Much appreciated. [http://192.168.0.1/](http://192.168.0.1/) timed out in both Firefox and IE. I'm on windows xp sp2. 

But the LAN gave maybe what I need. I'm on fiber LAN connection to a Switch? in basement. ISP or is it a server? It take care of hundreds of users. Each of us have 100/10 meg. So no DSL LAN WAN something. 

So maybe the status box give my info? 

I test it when the freeze kernel is available? I prefer to use UNetbooin cause that would allow me to delete it without having as much knowledge about MBR and such maybe if I want to test PCLOS later. Being as new as I am to Linux one don't want to lock oneself to just one Distro. 

No offense towards all good programmers supporting Ubuntu. I started with Ubuntu cause I trusted that work.

---

### Post by tuxcantfly on 2007-10-03
> **nooby said:**
> Thanks for such detailed answer. Much appreciated. [http://192.168.0.1/](http://192.168.0.1/) timed out in both Firefox and IE. I'm on windows xp sp2. 

But the LAN gave maybe what I need. I'm on fiber LAN connection to a Switch? in basement. ISP or is it a server? It take care of hundreds of users. Each of us have 100/10 meg. So no DSL LAN WAN something. 

So maybe the status box give my info? 

I test it when the freeze kernel is available? I prefer to use UNetbooin cause that would allow me to delete it without having as much knowledge about MBR and such maybe if I want to test PCLOS later. Being as new as I am to Linux one don't want to lock oneself to just one Distro. 

No offense towards all good programmers supporting Ubuntu. I started with Ubuntu cause I trusted that work.

Not exactly sure about that network connection, since it's a static address, you might be able to get a few details from your Windows install (Control Panel -> Network -> Properties?). I believe the comand "ipconfig" in windows also might give you some info. In the worst-case scenario, just wait until Oct 18 and download and burn the Ubuntu 7.10 CD and install from there.

As for the kernel freeze, it will be Oct 4 (details at [https://wiki.ubuntu.com/GutsyReleaseSchedule](https://wiki.ubuntu.com/GutsyReleaseSchedule) ) , but given that the kernel doesn't appear to have been updated since Sept 24, I doubt it will be changing from now to the official Ubuntu 7.10 release on Oct 18. Besides, even if it does change, you can just update the kernel after installing using the update manager, so no need to worry about that; so far, the primary issue with UNetbootin and the changing kernel has been that it can't fetch the install files from the Ubuntu servers after the Ubuntu kernel has changed and before I've updated the kernel in UNetbootin because it's still relying on an outdated version that's no longer on the servers, so in the unlikely case that the Ubuntu kernel happens to get updated right before the kernel freeze, UNetbootin will simply refuse to install and come out with an error along the lines of "was unable to fetch kernel modules" right before starting the actual install and no harm will be done.

As for switching to another distro like PCLinuxOS or deleting Ubuntu, you needn't worry about the MBR; the GRUB installed by PCLinuxOS will simply overwrite that of Ubuntu, and you can overwrite your Ubuntu partition with one for PCLinuxOS. Should you ever screw up the MBR and make your system unbootable, just boot from the Super Grub Disk at [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) and that'll fix all your bootloader problems, and should you ever want to just remove GRUB in all its entirely and go back to just Windows, just boot a Windows XP recovery disk, press "R", then when you get to the recovery console, enter "fixmbr".

---

### Post by nooby on 2007-10-03
Thanks for all effort you put into this. Much appreciated. As a noob it is safer for me to wait until Gutsy is on UNetbootin. I have the LiveCD with 6.06 to play with and learn basic things so I am prepared when Gutsy or next after that one has fixed the Kernel thing about Shutdown.

I tested the Ubuntu Live CD distro version 6.06 and that one shut down correctly. Surprising. But I must have done somthing wrong cause I failed to log in to the forum. Gave wrong password so now I am back on laptop with windows so I know the psw. 

LiveCD are two noisy for me. I should learn to use the USB memory pin instead or do a Frugal install maybe. So much to learn. I tested an old Knoppix I had kept. Much less noisy due to then spinning less fast. From 2004 so they didn't try to spin as fast as the modern DVD are able to. But knoppix had a GUI me not used to and the LAN didn't activate automatically which Ubuntu did.

---

### Post by tuxcantfly on 2007-10-03
> **nooby said:**
> when Gutsy or next after that one has fixed the Kernel thing about Shutdown.

That's very strange, you're having shutdown issues? Is it an actual error you're having, after you've installed Ubuntu, or was it simply something you had heard about? What version of Ubuntu did you install (7.04 or 7.10), and what method did you use (LiveCD, Alternate CD, UNetbootin, or Wubi)? Are there any error messages, or does it just hang? Perhaps you misunderstood what I meant by kernel freeze; it's not a freeze as in a crash, rather simply a date in the development cycle of Ubuntu 7.10, and it doesn't prevent users from installing or using Ubuntu 7.10 using UNetbootin; the version available for download at [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=243411](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=243411) works fine.

---

### Post by nooby on 2007-10-03
I used WUBI and it it's Fiesty Fawn7.04 as I remember and not 7.1 from the official site for it. The install was fast and great and worked like a charm. Until I unfortunately did an update. At first I didn't want to do the update cause from Win XP I know that updates could create problems of incompatibility. 

So I postponed the prompt to update for a day or two. During these hours I had no problem with shut down at all. But after the update I have every time. 

It looks as if all is going well but the hardware doesn't shut down. Only the Ubuntu does. No error message. 

I tried to look in Bios to make the ACPI compatible but being a noob it is not easy to know what they talk about there. 

I use that computer now but using win xp sp2. 

It is an Aopen XC Cube Mini with intel chipset 915. Small like a box for shoes. Very quite and with lots of features. 
Just two years old. As I remember the model name is like MDZ915-M or very similar name. 

It has a SATA HDD 160GB 512MB DDR2 1600GHertz processor. 

win xp shuts it down every time for two years now, haven't missed one time so no problem with hardware. 

thanks for caring about my problem. 

Wouldn't UNetbootin solve it? 

When I use an old Ubuntu Edgy 6.06 version Live CD and that one could shut down the hardware. As I remember. Not motivated to try again cause the DVD Rom didn't like the CD it wobbled too much. Could self destruct maybe. I tested a live Knoppix CD also and that one spinned quietly compared to Ubuntu. 

I've read about "frugal" installation and maybe that could make a live Cd more quite? 

As you realize I am so much noob on all this computer stuff that it is a miracle I get anything going. 

I read on the net using google that the shutdown incompatibility has gone on for years now in the Kernel. Even latest tribe of Gutsy seems to still have it. So maybe it is futile for me to wait for it. I have to find a Linux that use another kernel not having the incompatibility? 

Others who have searched for a solution seems to have given up to find it or they have forgotten to tell us that they now have a solution. 

I have to read more about the kernel. Is it true that all Linux use the incompatible version? Could there be old distros that are compatible. 

Could one borrow a module from that old one and repair the newest one for us having this problem. 

I don't want to give up on using Linux. Sooner or later that is the sole OS that will be available. Have not heard of anything else coming. 

Best regards

Nooby

PS I go to bed now, has to go up early next morning. It is 22.40 PM here locally

---

### Post by tuxcantfly on 2007-10-03
> **nooby said:**
> I used WUBI and it it's Fiesty Fawn7.04 as I remember and not 7.1 from the official site for it. The install was fast and great and worked like a charm. Until I unfortunately did an update. At first I didn't want to do the update cause from Win XP I know that updates could create problems of incompatibility. 

So I postponed the prompt to update for a day or two. During these hours I had no problem with shut down at all. But after the update I have every time. 

It looks as if all is going well but the hardware doesn't shut down. Only the Ubuntu does. No error message. 

I tried to look in Bios to make the ACPI compatible but being a noob it is not easy to know what they talk about there. 

I use that computer now but using win xp sp2. 

It is an Aopen XC Cube Mini with intel chipset 915. Small like a box for shoes. Very quite and with lots of features. 
Just two years old. As I remember the model name is like MDZ915-M or very similar name. 

It has a SATA HDD 160GB 512MB DDR2 1600GHertz processor. 

win xp shuts it down every time for two years now, haven't missed one time so no problem with hardware. 

thanks for caring about my problem. 

Wouldn't UNetbootin solve it? 

When I use an old Ubuntu Edgy 6.06 version Live CD and that one could shut down the hardware. As I remember. Not motivated to try again cause the DVD Rom didn't like the CD it wobbled too much. Could self destruct maybe. I tested a live Knoppix CD also and that one spinned quietly compared to Ubuntu. 

I've read about "frugal" installation and maybe that could make a live Cd more quite? 

As you realize I am so much noob on all this computer stuff that it is a miracle I get anything going. 

I read on the net using google that the shutdown incompatibility has gone on for years now in the Kernel. Even latest tribe of Gutsy seems to still have it. So maybe it is futile for me to wait for it. I have to find a Linux that use another kernel not having the incompatibility? 

Others who have searched for a solution seems to have given up to find it or they have forgotten to tell us that they now have a solution. 

I have to read more about the kernel. Is it true that all Linux use the incompatible version? Could there be old distros that are compatible. 

Could one borrow a module from that old one and repair the newest one for us having this problem. 

I don't want to give up on using Linux. Sooner or later that is the sole OS that will be available. Have not heard of anything else coming. 

Best regards

Nooby

PS I go to bed now, has to go up early next morning. It is 22.40 PM here locally

Oh sorry, didn't occur to me that your shutdown issues came from a Wubi-generated install; that changes the context of the issue entirely. Anyhow, Wubi and UNetbootin are different projects (though I also happen to be a developer of Wubi as well); the website for UNetbootin is at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) while Wubi's is at [http://wubi.sourceforge.net/](http://wubi.sourceforge.net/) I believe you may be confusing the two (this is the UNetbootin forum thread not the Wubi one); Wubi installs Ubuntu into a file, while UNetbootin installs a standard, full-fledged Ubuntu install to a partition like Ubuntu normally would, only it does it without a CD.

The shutdown error you had with Wubi was likely due because it installs to a file not a partition, and the patches it uses don't cope too well with upgrades and updates(which explains why shutdown stopped working after the update). That error is Wubi-specific, and doesn't occur on standard Ubuntu installs like those installed by the Ubuntu CD or UNetbootin; the accounts of shutdown errors you were reading about on google were likely very rare cases (probably due to some obscure hardware); a standard Ubuntu install using the CD or UNetbootin won't have any such shutdown errors, since it worked fine for you with the Ubuntu 6.06 CD, so it isn't a hardware issue nor an Ubuntu issue, it's a Wubi-specific issue. Of course if I read that wrong, and if you did try a standard (CD or UNetbootin, not Wubi) install of Ubuntu, and the shutdown doesn't work, then that would be an Ubuntu bug, but I think it's much more likely, based on that account, that shutdown will work fine if you install using the CD or UNetbootin, and that the shutdown issue you had was a Wubi-speicific issue.

---

### Post by nooby on 2007-10-04
Ooops I've done it again, being in wrong forum. I apology 
:(

I guess the reason I am in the wrong forum is due to me liking the concept of unetbootin very much so I searched for threads to see if that bug occur in such set up too. I must have forgotten me in wrong forum. 

the reason me still have not tried out unetbootin is that I wait for the official release of gutsy and I am still unsure of if I need to defrag first before using unetbootin. 

I also must learn more about the following. 

When I have used ubuntu 7,1 for a while and want to test other distros. 

Is it easy for a noob like me to delete the U and install anothrr distro?

---

### Post by tuxcantfly on 2007-10-04
> **nooby said:**
> Ooops I've done it again, being in wrong forum. I apology 
:(

I guess the reason I am in the wrong forum is due to me liking the concept of unetbootin very much so I searched for threads to see if that bug occur in such set up too. I must have forgotten me in wrong forum. 

the reason me still have not tried out unetbootin is that I wait for the official release of gutsy and I am still unsure of if I need to defrag first before using unetbootin. 

I also must learn more about the following. 

When I have used ubuntu 7,1 for a while and want to test other distros. 

Is it easy for a noob like me to delete the U and install anothrr distro?

Defragging is not necessary, though if your hard drive is almost full (70% disk usage or above) it may be helpful.

As for deleting Ubuntu and installing another distro, just go into "Manual Partitioning" in the installer of the other distribution, and tell it to format the ext3 partition (on which Ubuntu is installed), that'll delete Ubuntu and overwrite it with the new distro.

---

### Post by nooby on 2007-10-04
Yes the HDD is 160GB so it could have both Win XP and a Linux partition no problem I guess. Plenty of space. 

But I don't want to use the DVD burner to deal with iso so a unetbootin would be ideal. 

So thanks for your work on that one. I maybe give unetbotin gutsy a chance then in November 2007. 

If I remember correctly. The shutdown error will go away when I have a real install and not a wubi install?

---

### Post by tuxcantfly on 2007-10-05
I see that HowtoForge has posted a nice tutorial of installing Ubuntu or Fedora using UNetbootin at [http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora](http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora) so you might want to check it out if you need more details.

---

### Post by nooby on 2007-10-05
Yes that one was really good. Thanks. I do plan to use unetbootin, I would be really surprised me wouldn't within a month or so.

---

### Post by fkoehn on 2007-10-06
HELP!

;)

My 7.10 install failed when the linux-generic kernel couldn't be installed.

On the following reboot, I only see a "J" on the upper left corner on the screen.

What do I need to do to get into the bootloader again??

Any help appreciated,
Frank.

---

### Post by nooby on 2007-10-06
Could this one help? 
[http://rescuecd.sourceforge.net/]("http://rescuecd.sourceforge.net/")
 Timo's rescue CD?

the username is "root".The standard password is "rescue"

I am too new but I plan to build that one. Seems very good to have around in case something happens.

EDIT
Sorry I wanted to refer to what tuxcantfly advised 


the Super Grub Disk is what you're looking for? [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by tuxcantfly on 2007-10-06
Rather annoyingly, it appears that some last-minute, post-kernel-freeze change made it into Gutsy's kernel (thus breaking installations using UNetbootin 7.10, I presume that was the issue that fkoehn had), I've uploaded a new build with the newer kernel.

Also, I've added a version of UNetbootin that can install OpenSuse 10.3 (happens to be a pretty fine distro, anyone who hasn't tried it yet really should)

Also, Windows Vista support happens to be a quite highly-requested feature; I can't exactly build in support right now (don't have access to a Vista machine for testing), but the general procedure for getting it working is documented nicely at [http://www.msfn.org/board/Multiboot_Vista_XP_OSes_Grub4Dos_Me_t95537.html](http://www.msfn.org/board/Multiboot_Vista_XP_OSes_Grub4Dos_Me_t95537.html) for anybody interested in using UNetbootin on Windows Vista.

PS @fkoehn: Maybe the Super Grub Disk is what you're looking for? [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by zivley on 2007-10-07
The program seems great, to install Linux aside of Windows, even from within Windows, great idea, but what if I want to fully replace the Windows? I don't care for it, can I just chose to "Use the entire disk" at the partitioner stage?
Did someone try that option?
I'll go for it and report later...
Say goodbye Windows!

---

### Post by zivley on 2007-10-07
Well, I guess it didn't go well, but I think it has nothing to do with the fact I partitioned the whole disk, it all went well till I've got to the stage "Select and install software", after selecting what I wanted (Ubuntu Desktop) it started running, and hung at 6%, I let it go for almost 2 hours now and it's still stuck there, from time to time I hear the PC Speaker makes strange beeps, as if I were pressing some keyboard keys, you know what I mean?
In the meantime I've burned the ISO of the official Ubuntu 7.10 beta, so I guess I'll restart and install from it.
Do you have any ideas about what could be go wrong?

---

### Post by zivley on 2007-10-07
> **tuxcantfly said:**
> Give it time. For some reason, while caching the files (downloading from the web), the counter remains at 6%. If you're on a DSL connection, it will stay there at 6% for around 2 hours, since it's downloading 700MB of files off the internet.

Sorry about my post, after I sent the message, I've been digging in this same thread and found this quoted post, as an answer to someone that has the same problem than me, so I think I'll let it go for a few more hours, I don't mind, I'm going home soon, and I'll leave it like this, if tomorrow I see the same situation, then I'll restart and install from CD.
It's still weird why those pc speaker beeps occur...

---

### Post by tuxcantfly on 2007-10-08
Archlinux 2007.08 has been released, and it now actually has a working ftp install, which means a new build of UNetbootin for Arch... See the usual spot at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821) for downloads (exe, sh, deb, and rpm formats)

---

### Post by zivley on 2007-10-08
Ok, just wanted to say that everythng is fine now, I came this morning to work and the computer finished the installation, and it was only waiting for me to continue with reboot.
After the reboot everything came up great, no windows anymore, that's what I've chosen to do.
Thanks to tuxcantfly for the great program!

---

### Post by Kobalt on 2007-10-09
Installing a 64bits system with UNetbootin would be great... Is that scheduled by any chance?

---

### Post by guyver on 2007-10-09
I have two questions concerning this.

1.  Can it be used to install Xubuntu?  I don't see that as an option, so I have to ask.

2.  After installation, is there a way I can permanently remove the Windows stuff?  

I'm dealing with a laptop with 128MB of RAM and the internal CD drive does not work.  The BIOS does not support booting from the USB.  My only options at this point are a floppy install (if there was such a thing in the Ubuntu world) or something through the ethernet (but I'm a newb trying to leave the Windows world... instructions are not always straightforward).

---

### Post by Kobalt on 2007-10-09
Yes, you can install Xubuntu using UNetbootin: once you have installed it, it will prompt you to chose between Ubuntu, Kubuntu or Xubuntu. Chose what you like...

To completely remove Windows you should [check this out]("https://help.ubuntu.com/community/HowToRemoveWindows").

---

### Post by guyver on 2007-10-09
Very much appreciated.  Only problem now is the link you provided HIGHLY recommends not to use the information on it, but there's no information yet to remove Windows... or did I miss something?

---

### Post by tuxcantfly on 2007-10-09
> **Kobalt said:**
> Installing a 64bits system with UNetbootin would be great... Is that scheduled by any chance?

uploading 64-bit builds at the moment, will be up in a few hours (pesky DSL connections can only go so fast...)

---

### Post by tuxcantfly on 2007-10-09
Mandriva 2008 was recently released, so I've published a new UNetbootin build that can install it.. see the usual download spot at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821) and instructions are at the unetbootin site at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by tuxcantfly on 2007-10-09
I've updated the UNetbootin Ubuntu 7.10 (gutsy) development builds, since there has been yet another last-minute change in the kernel.

---

### Post by tuxcantfly on 2007-10-10
> **Kobalt said:**
> Installing a 64bits system with UNetbootin would be great... Is that scheduled by any chance?

Check the download page... I've finished uploading the 64-bit builds, you should now be able to install them. Since the packages are all marked as "noarch/all", you don't need to necessarily install 32-bit from a 32-bit OS, or 64-bit from a 64-bit OS; you can install 64-bit if your processor is capable of it (amd64 or intel core2 and above), even if you're running a 32-bit Windows or Linux install.

---

### Post by Kobalt on 2007-10-10
Thank you so much tuxcantfly, I'll test this out tonight when I come home.

I'll let you know.

Cheerio ! ;)

---

### Post by nooby on 2007-10-10
Thanks indeed Tux that you provide such many distros to be available through unetbootin. 

Is it difficult to do the same for PCLinuxOS? Or isn't that one a good distro. It is one of the most popular at the distrowatch so I want to test it without having to burn an iso. 

Are they maybe different?

---

### Post by tuxcantfly on 2007-10-10
> **nooby said:**
> Thanks indeed Tux that you provide such many distros to be available through unetbootin. 

Is it difficult to do the same for PCLinuxOS? Or isn't that one a good distro. It is one of the most popular at the distrowatch so I want to test it without having to burn an iso. 

Are they maybe different?

I've been searching around for PCLinuxOS netboot initrd / mini FTP install files, but I can't find any, just iso files. If you know where they can be found (usually they're on a "netboot" or "media" directory on the ftp server), point me to them and I'll gladly add pclinuxos builds. Same goes for other distros, if you want to have builds for those available as well, just post the link to the netboot initrd and kernel, or the ftp mini-install iso files on the ftp servers and I'll make builds as soon as I can.

---

### Post by GreatSlovakia on 2007-10-10
Before I am going to try out I wondered wether this would make it possible to bypass the restriction on my school-laptop, which makes it always to boot from the hard drive (and the bios is of course pass protected). Yet the second problem would be still then that I only have wlan, and I don't expect this to work with wlan... am I correct?

---

### Post by Kobalt on 2007-10-10
As far as I know it's not possible yet to perform a netinstall of a Linux distro from a wifi connection...

---

### Post by tuxcantfly on 2007-10-10
> **GreatSlovakia said:**
> Before I am going to try out I wondered wether this would make it possible to bypass the restriction on my school-laptop, which makes it always to boot from the hard drive (and the bios is of course pass protected). Yet the second problem would be still then that I only have wlan, and I don't expect this to work with wlan... am I correct?

For question 1: Yes, assuming you have admin privs, you won't have to do any tinkering with the BIOS settings to get it to boot. (and of course make sure you aren't violating any school policies by circumventing their security systems)

For question 2: Probably won't work on wlan, though you could also pre-download the packages to your hard drive and use those by selecting "Hard Drive" as the installation source. (note that that'll only work on the Fedora, openSUSE, Mandriva, and Archlinux installers, not the Ubuntu one). If you have a CD though, and just want to boot that, you can boot from the CD through GRUB, by adding this to the menu.lst:

```
title Boot CD
cdrom --init
map --hook
chainloader (cd0)
boot
```

More details at [http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Using_ATAPI_CDROM_in_GRUB_for_DOS](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Using_ATAPI_CDROM_in_GRUB_for_DOS)

---

### Post by tommytabib on 2007-10-10
Hello,

I have the mandriva one 2008 kde iso downloaded and i want to use unetbootin to install it. I select 'hard disk' installation method and direct it to the right directory of the iso but it says its not there (when i know it is).

Heres what im typing under directory "/home/xxx/downloads/" and it didnt work, so i tried "/home/xxx/downloads/mandriva-one-2008-kde-i586.iso" but that didnt work either.

Is it because this only works with mandriva free and not with mandriva one?
And do the iso files have to be extracted or can they just be as an iso?

Thanks

---

### Post by tuxcantfly on 2007-10-10
> **tommytabib said:**
> Hello,

I have the mandriva one 2008 kde iso downloaded and i want to use unetbootin to install it. I select 'hard disk' installation method and direct it to the right directory of the iso but it says its not there (when i know it is).

Heres what im typing under directory "/home/xxx/downloads/" and it didnt work, so i tried "/home/xxx/downloads/mandriva-one-2008-kde-i586.iso" but that didnt work either.

Is it because this only works with mandriva free and not with mandriva one?
And do the iso files have to be extracted or can they just be as an iso?

Thanks

Yes, you can use only the mandriva free, not the mandriva one; you need actual packages, not the liveCD disk image like mandriva one provides. The packages must also be extracted from the iso (or separately downloaded from the ftp mirror).

---

### Post by guyver on 2007-10-11
> **tuxcantfly said:**
> I'm not aware of any floppies that can boot from external usb cd drives (SBM can't), so what I'd do is install a minimal debian system using netboot floppies, then subsequently apt-get yourself an ubuntu installation...

Guide on installing debian using netboot floppies:
[http://linux.simple.be/debian/floppy](http://linux.simple.be/debian/floppy)

Detailed procedures on creating floppies from image files (since you can't boot your computer, you'll have to do the floppy creation process on another computer):
[http://www.debian.org/releases/stable/i386/ch04s03.html.en](http://www.debian.org/releases/stable/i386/ch04s03.html.en)

Then, after you're done installing a minimal debian system, to turn it into an ubuntu system, this should do the job (enter these in the terminal of the minimal debian install):

```
su root
echo \
"
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted multiverse universe
deb http://security.ubuntu.com/ubuntu feisty-security main restricted multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted multiverse universe
" > /etc/apt/sources.list
apt-get update
apt-get dist-upgrade
apt-get install ubuntu-desktop
```

Then reboot and you should have an ubuntu install, though note that I've never tested this procedure myself, so I can't guarantee that it'll work...


If I change the path locations to say archive.xubuntu.com will this work?  I would like to install Xubuntu instead.  Preferably I would rather do the Gutsy Xubuntu, but I can settle for Feisty now.  Thanks in Advance.

---

### Post by tuxcantfly on 2007-10-11
> **guyver said:**
> If I change the path locations to say archive.xubuntu.com will this work?  I would like to install Xubuntu instead.  Preferably I would rather do the Gutsy Xubuntu, but I can settle for Feisty now.  Thanks in Advance.

keep the repository lines the same, just change the "feisty" to "gutsy", and change the apt-get command to "xubuntu-desktop" instead of "ubuntu-desktop"

---

### Post by Donkor on 2007-10-14
Just wondering, are there any plans to allow an option that isn't as automated?  I'd like to select the packages I install instead of having seemingly everything installed.  Things like OO, Firefox, etc I don't need and just take up hd space.  

Other than that, it's great.  I used it twice on two laptops with feisty and I'm going to try it with gutsy now.

Edit: Looks like Gutsy's installer has it now, though not as customizable as I'd hoped.  It still installs openoffice, games, firefox, thunderbird, pidgin, etc which I didn't select.

---

### Post by tuxcantfly on 2007-10-14
> **Donkor said:**
> Just wondering, are there any plans to allow an option that isn't as automated?  I'd like to select the packages I install instead of having seemingly everything installed.  Things like OO, Firefox, etc I don't need and just take up hd space.  

Other than that, it's great.  I used it twice on two laptops with feisty and I'm going to try it with gutsy now.

Edit: Looks like Gutsy's installer has it now, though not as customizable as I'd hoped.  It still installs openoffice, games, firefox, thunderbird, pidgin, etc which I didn't select.

Ubuntu's official netboot installers don't provide package-by-package customizability (so I can't add those features without diverging from the official netboot installer, which I'd rather not do for maintainability reasons). If you want to have a greater degree of control on your install process, try the Fedora or openSUSE versions of UNetbootin (which provide individual package-selection options in the official netboot installers), or if you absolutely must use Ubuntu, just select the base system install option, and use apt-get to install the packages you need.

---

### Post by reisyboy on 2007-10-16
Hi well i have a small question, i want this i really do i want to install ubuntu on a PC with no Floppy or CD Rom  or bootable usb so this is great.... but what i really want is this in a very small install package, that i can leave on the HD in another partition. That can do just this, incase the OS i am going to put on breaks or dies or i want to change it. Then i could boot to the loader an select UNetbootin an do another install... is there anything like this? a micro-distro that has UNetbootin or another such tool that can either fetch the install from the net an let me install, or boot an extracted ISO like UNetbootin can that is designed to be left on the HD in a little partition on its own do it can be booted to do recoverys etc?

---

### Post by tuxcantfly on 2007-10-16
> **reisyboy said:**
> Hi well i have a small question, i want this i really do i want to install ubuntu on a PC with no Floppy or CD Rom  or bootable usb so this is great.... but what i really want is this in a very small install package, that i can leave on the HD in another partition. That can do just this, incase the OS i am going to put on breaks or dies or i want to change it. Then i could boot to the loader an select UNetbootin an do another install... is there anything like this? a micro-distro that has UNetbootin or another such tool that can either fetch the install from the net an let me install, or boot an extracted ISO like UNetbootin can that is designed to be left on the HD in a little partition on its own do it can be booted to do recoverys etc?

Not exactly sure about what you mean by "very small install package", UNetbootin at ~10 MB should comfortably fit on even a small hard drive. What you could do is just install the UNetbootin loader to the hard drive, don't remove it after Ubuntu has been installed and should Ubuntu break, just select the UNetbootin option. Should your bootloader also break, just use the Super Grub Disk [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) and that'll let you start up UNetbootin through the Windows bootloader.

---

### Post by reisyboy on 2007-10-16
Ahh so i can install the bootloader app and run keep it should i need to recover the system and then remove all other OS's an install a nice Ubuntu on the remainder of the disk, that right???

What i meant was just that i wanted an to keep UNetbootin on the pc. I was under the impression it NEEDED to have an OS installed, but from your reply i understand that the it can just reside on the disk, on its own.

BTW i presume when installing Ubuntu i can choose to keep the original bootloader??? or do i have to use a specific string on it to keep it?

---

### Post by tuxcantfly on 2007-10-16
I've updated the PartedMagic Partition Manager package to version 1.8, usual download spot at [https://sourceforge.net/project/showfiles.php?group_id=198821](https://sourceforge.net/project/showfiles.php?group_id=198821)

---

### Post by tuxcantfly on 2007-10-16
> **reisyboy said:**
> Ahh so i can install the bootloader app and run keep it should i need to recover the system and then remove all other OS's an install a nice Ubuntu on the remainder of the disk, that right???

What i meant was just that i wanted an to keep UNetbootin on the pc. I was under the impression it NEEDED to have an OS installed, but from your reply i understand that the it can just reside on the disk, on its own.

It needs to reside on a disk, and thus it needs to be on some kind of partition. Whether or not that partition has an operating system installed on it doesn't matter; so long as you have a bootloader installed that can load it (GRUB or GRLDR), and the file is on a partition, it'll work fine. But you'll need a bootloader to boot UNetbootin, whether you have an OS installed or not (GRUB installed on the MBR will probably work best).

> BTW i presume when installing Ubuntu i can choose to keep the original bootloader??? or do i have to use a specific string on it to keep it?

Towards the end of the installation, you'll be asked whether or not to install GRUB to the MBR. If you select no, the original bootloader will be kept, but you'll need to find out some kind of way to get Ubuntu boot without GRUB, using whatever other bootloader you want to use. I'd just install GRUB, and if you need to boot another OS like Windows, GRUB will just allow you to "chainload" the other bootloader, so you can still use your original bootloader but also have GRUB installed to the MBR.

---

### Post by Luca.es on 2007-10-17
Any ETA on the Vista support?

I would create a dynamic partition with free disk space in vista and then tell ubuntu to use that new partition. Is that possible?

Thanks.

---

### Post by tuxcantfly on 2007-10-17
> **Luca.es said:**
> Any ETA on the Vista support?

I would create a dynamic partition with free disk space in vista and then tell ubuntu to use that new partition. Is that possible?

Thanks.

I don't have access to any computer that capable of running Windows Vista, therefore no ETA yet because I can't test it under Vista. Supposedly, GRLDR can work under Vista using the instructions [http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Booting_GRUB_for_DOS_via_the_Windows_Vista_boot_manager](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Booting_GRUB_for_DOS_via_the_Windows_Vista_boot_manager) but I haven't tried them. If they do work please post exactly what you have to do to get it working under Vista (other than the commands), I might be able to add support that way without needing access to Vista.

---

### Post by tuxcantfly on 2007-10-17
> **Luca.es said:**
> I would create a dynamic partition with free disk space in vista and then tell ubuntu to use that new partition. Is that possible?

Thanks.

Yes, certainly is possible; that was the exact technique I was considering using (once I have access Windows Vista, that is). The partition-shrinking bit can be done via the Windows Vista drive-management API, and thus can be used on all the UNetbootin versions, though the automatically-partition-and-use-new-partition bit will need a separate implementation on each distro (kickstart on Fedora, preseed on Ubuntu, etc.) so that'll probably take longer to do since it has to be redone on each version.

---

### Post by tuxcantfly on 2007-10-20
Note that the default US mirror for Ubuntu (us.archive.ubuntu.com) and various others happen to be VERY congested at the moment (7.10 release is probably the culprit), so UNetbootin may fail or go very slowly when attempting to use those mirrors. For now, use other mirrors, such as the South Africa mirror (za.archive.ubuntu.com) which appears to be going fast, or if that too fails, use the main Ubuntu mirror by going into the "manual" mirror selection mode, (archive.ubuntu.com)

---

### Post by guyver on 2007-10-21
> **tuxcantfly said:**
> keep the repository lines the same, just change the "feisty" to "gutsy", and change the apt-get command to "xubuntu-desktop" instead of "ubuntu-desktop"

I have gotten errors concerning the security and backport within the sources.list file.  I entered all deb lines continuously from the command prompt up to the creation of the file since I wasn't sure if I could do a carriage return on each line you listed for the echo command.  When I noticed the errors as a result of using the apt-get update command, I edited the sources.ist file so that each deb command was on its own line and I removed the backslash I though you accidentally omitted for the security.

I get the following errors:

> W:  GPG error:  [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-**security** Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W:  GPG error:  [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-**updates** Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W:  GPG error:  [http://security.ubuntu.com](http://security.ubuntu.com) **gutsy** Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W:  GPG error:  [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-**backports** Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W:  You may want to run apt-get update to correct these problems

I did rerun apt-get update but this did nothing.

---

### Post by tuxcantfly on 2007-10-21
> **guyver said:**
> I have gotten errors concerning the security and backport within the sources.list file.  I entered all deb lines continuously from the command prompt up to the creation of the file since I wasn't sure if I could do a carriage return on each line you listed for the echo command.  When I noticed the errors as a result of using the apt-get update command, I edited the sources.ist file so that each deb command was on its own line and I removed the backslash I though you accidentally omitted for the security.

I get the following errors:

W:  GPG error:  [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-**security** Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W:  GPG error:  [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-**updates** Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W:  GPG error:  [http://security.ubuntu.com](http://security.ubuntu.com) **gutsy** Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W:  GPG error:  [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-**backports** Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W:  You may want to run apt-get update to correct these problems

I did rerun apt-get update but this did nothing.

You need to import Ubuntu's GPG key, more info at [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt) (the key you want is 40976EAF437D05B5)

However, I've just found this guide, it may actually work better than the approach I described: [https://help.ubuntu.com/community/Installation/WithFloppies](https://help.ubuntu.com/community/Installation/WithFloppies)

---

### Post by guyver on 2007-10-21
If I use this other guide, I am not sure what I need to do to ensure I install Xubuntu instead of Ubuntu.

I try to use the following command and get a "server returned error 404:  HTTP/1/1 404 Not Found": ** wget [http://mirrors.kernel.org/ubuntu/debootstrap_1.0.3build1_all.deb](http://mirrors.kernel.org/ubuntu/debootstrap_1.0.3build1_all.deb)**

---

### Post by guyver on 2007-10-21
I realized I needed to double check the path and this is what I needed to use for the server I chose:  [http://mirrors.kernel.org/ubuntu/pool/main/d/debootstrap/](http://mirrors.kernel.org/ubuntu/pool/main/d/debootstrap/)  However, I am currently stuck at where the instructions say to:  "base-config new"  I get a command not found error.


I am also still uncertain how I go about installing Xubuntu instead of Ubuntu with this approach.  The tutorial seems a bit dated since it's referring to Hoary and also assumes the user only wishes to install Ubuntu.

---

### Post by guyver on 2007-10-21
> **tuxcantfly said:**
> You need to import Ubuntu's GPG key, more info at [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt) (the key you want is 40976EAF437D05B5)

However, I've just found this guide, it may actually work better than the approach I described: [https://help.ubuntu.com/community/Installation/WithFloppies](https://help.ubuntu.com/community/Installation/WithFloppies)

Okay, I decided to ditch the other tutorial and retry your approach again and get a private requesting key.

I first create the sources.list file as per your instructions.

I then enter:  "**gpg --keyserver pgpkeys.mit.edu --recv-key 40976EAF437D05B5**"

The only negative comment I see after executing this command was "**gpg: can't open `/gnupg/options.skel` : No such file or directory**"

I am then provided an 8-digit hex private requesting key.

I then type:  "**gpg --edit-key [email]ftpmaster@ubuntu.com[/email]**" and then type "**fpr**" at the shell prompt.

I assume fpr somehow validates my key.  I then type "**quit**" to exit back to the main command prompt.

I then type:  "**gpg -a --export** *_[8-digit requesting key]_* **| apt-key add -**"  (had to remove sudo since I got a bash error saying command not found)

I then resumed your original walk through tutorial:

apt-get update
apt-get dist-upgrade

I then get an error:  "Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?"

I reran apt-get update and dist-upgrade and was taken to a menu where I selected my key map and something to do with cron (which I took the default value).

After a while, the result of running "apt-get dist-upgrade" produced the following error:

"Preconfiguring packages ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
          LANGUAGE = (unset),
          LC_ALL = (unset),
          LANG = "en_US.UTF-8"
     are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
dpkg: regarding .../dpkg_1.14.5ubuntu16_i386.deb containing dpkg:
 package uses Breaks; not supported in this dpkg
[B]dpkg: error processing /var/cache/apt/archives/dpkg_1.14.5ubuntu16_i386.deb (--unpack):
 unsupported depedency problem - not installing dpkg
Errors were encountered while processing:
 /var/cache/apt/archives/dpkg_1.14.5ubuntu16_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]"

Hoping that this is not a catastrophic error, I went on to type:

apt-get install ubuntu-desktop

This produced similar errors and does not actually install Xubuntu although it looks like it downloaded almost everything.

---

### Post by tuxcantfly on 2007-10-21
> **guyver said:**
> Okay, I decided to ditch the other tutorial and retry your approach again and get a private requesting key.

I first create the sources.list file as per your instructions.

I then enter:  "**gpg --keyserver pgpkeys.mit.edu --recv-key 40976EAF437D05B5**"

The only negative comment I see after executing this command was "**gpg: can't open `/gnupg/options.skel` : No such file or directory**"

I am then provided an 8-digit hex private requesting key.

I then type:  "**gpg --edit-key [email]ftpmaster@ubuntu.com[/email]**" and then type "**fpr**" at the shell prompt.

I assume fpr somehow validates my key.  I then type "**quit**" to exit back to the main command prompt.

I then type:  "**gpg -a --export** *_[8-digit requesting key]_* **| apt-key add -**"  (had to remove sudo since I got a bash error saying command not found)

I then resumed your original walk through tutorial:

apt-get update
apt-get dist-upgrade

I then get an error:  "Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?"

I reran apt-get update and dist-upgrade and was taken to a menu where I selected my key map and something to do with cron (which I took the default value).

After a while, the result of running "apt-get dist-upgrade" produced the following error:

"Preconfiguring packages ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
          LANGUAGE = (unset),
          LC_ALL = (unset),
          LANG = "en_US.UTF-8"
     are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
dpkg: regarding .../dpkg_1.14.5ubuntu16_i386.deb containing dpkg:
 package uses Breaks; not supported in this dpkg
[B]dpkg: error processing /var/cache/apt/archives/dpkg_1.14.5ubuntu16_i386.deb (--unpack):
 unsupported depedency problem - not installing dpkg
Errors were encountered while processing:
 /var/cache/apt/archives/dpkg_1.14.5ubuntu16_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]"

Hoping that this is not a catastrophic error, I went on to type:

apt-get install ubuntu-desktop

This produced similar errors and does not actually install Xubuntu although it looks like it downloaded almost everything.

For the dpkg installation error, perhaps you want to update your dpkg to a newer version from Debian [http://packages.debian.org/dpkg](http://packages.debian.org/dpkg) and first install the "etch" version, then the "lenny" version, then that'll let you smoothly upgrade to Ubuntu's version afterwards.

As for the installation of xubuntu, use this command:

```
sudo apt-get install xubuntu-desktop
```

---

### Post by guyver on 2007-10-21
Sorry for the confusion.

I didn't know how to install Xubuntu for that other link you provided that covered a floppy install.  That was what I didn't know how to do... unless you mean the same command works for either.  In my previous post I said "apt-get install ubuntu-desktop", but I really meant "apt-get install xubuntu-desktop"... I did a copy paste and forgot to edit that part.

As for the dkpg installation, do I add both dkpg paths from the link you provided in the sources.list in order to install them?

Sorry, I'm a newb.

---

### Post by guyver on 2007-10-21
Well, I didn't get far... decided to start over again... this time doing the install via this walk through:  [https://help.ubuntu.com/community/Installation/WithFloppies](https://help.ubuntu.com/community/Installation/WithFloppies)

The part where I am stuck is when I type: "base-config new"

The system responds with "bash: base-config: command not found"

What do I have to do?

---

### Post by tuxcantfly on 2007-10-22
> **guyver said:**
> Sorry for the confusion.

I didn't know how to install Xubuntu for that other link you provided that covered a floppy install.  That was what I didn't know how to do... unless you mean the same command works for either.  In my previous post I said "apt-get install ubuntu-desktop", but I really meant "apt-get install xubuntu-desktop"... I did a copy paste and forgot to edit that part.

As for the dkpg installation, do I add both dkpg paths from the link you provided in the sources.list in order to install them?

Sorry, I'm a newb.

You separately download the dpkg .deb packages and install them with the command:

```
sudo dpkg -i ./dpkg-something.deb
```

Install the debian etch version first, once that's installed, upgrade to the lenny version, then after that, it should work when you attempt to upgrade to the ubuntu gutsy version of dpkg

I think you should follow my original instructions, that guide I linked to looks excessively complicated and I'm not sure whether it even works on newer versions.

---

### Post by guyver on 2007-10-22
> **tuxcantfly said:**
> You separately download the dpkg .deb packages and install them with the command:

```
sudo dpkg -i ./dpkg-something.deb
```

Install the debian etch version first, once that's installed, upgrade to the lenny version, then after that, it should work when you attempt to upgrade to the ubuntu gutsy version of dpkg

I think you should follow my original instructions, that guide I linked to looks excessively complicated and I'm not sure whether it even works on newer versions.

Sorry for this stupid question, but do I do this before or after I do the "apt-get update"?



I really appreciate your time and patience on this.  This is what I think the whole procedure has evolved into (I'm not 100% certain on the dpkg lines)

 

Create sources.list file:

```
1.  **su root**
2.  **echo \**
3.  **"**
4.  **deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted multiverse universe**
5.  **deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security main restricted multiverse universe**
6.  **deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted multiverse universe**
7.  **deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted multiverse universe**
8.  **" > /etc/apt/sources.list**
```

Import Ubuntu GPG key [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

```
1.  **gpg --keyserver pgpkeys.mit.edu --recv-key 40976EAF437D05B5**
2.  **gpg --edit-key [email]ftpmaster@ubuntu.com[/email]**
3.  **fpr**
4.  **quit**
5.  **gpg -a --export *[COLOR="Red"][8-digit requesting key][/COLOR]* | apt-key add -**
```

Update dpkg ( I've had bad luck with sudo for the Floppy Install) [http://packages.debian.org/dpkg](http://packages.debian.org/dpkg)

```
Install Debian Etch Version:
1.**  wget http://http.us.debian.org/debian/pool/main/d/dpkg/dpkg_1.13.25_i386.deb**
2.  **sudo dpkg -i ./dpkg_1.13.25_i386.deb**

Upgrade to Debian Lenny Version:
3.  **wget http://http.us.debian.org/debian/pool/main/d/dpkg/dpkg_1.14.7_i386.deb**
4.  **sudo dpkg -i ./dpkg_1.14.7_i386.deb** 
```

Get Updates & Install

```
1.  **apt-get update**
2.  **apt-get dist-upgrade**
3.  **apt-get install xubuntu-desktop**
```

One thing I also forgot to ask is should I install GRUB when prompted near the end of my Debian Minimal Install?  Also just for clarification, when asked to select the type of install (i.e. desktop, laptop, server, etc.), do I deselect everything and  contintue in order to do the minimal installation you had intended?

---

### Post by luluone on 2007-10-22
Hello,

First, thank you for that forum.

I have a question
I install package UNetbootin-ubuntu710rev48 on Ubuntu Feisty but I have an error 17.
I try to defrag.

I think it come from menu.lst

There is my menu.lst

> 
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=66498ba1-cacf-4348-bb70-9282602684d8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=66498ba1-cacf-4348-bb70-9282602684d8 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professionnel
root		(hd0,0)
savedefault
makeactive
chainloader	+1


title UNetbootin-ubuntu710rev48
root (hd0,1)
configfile /boot/grub/menu-ubn.lst




In the unetbootin section what must be the root (hdx,x)?
(Grub is on the MBR of hd0,0).
Excuse me for my english
Thank you for your help

---

### Post by asbjornu on 2007-10-22
I ran the Ubuntu 7.10 Windows installer in Windows 98 and the Windows-part of the installation seemed to go fine, but then it asks me to boot and when I do, it's like nothing happened. Grub doesn't start, I just boot directly into Windows and then UNetboot is uninstalled. Doing it again yields the exact same result.

It seems as if UNetboot isn't able to write to the bootloader for some reason, even though I don't get any error messages. Can I debug this somehow (with a switch to unetbootin-ubuntu710rev48.exe or something)? Any help is highly appreciated! :)

Oh and I didn't think of it before, but I really want Xubuntu instead of Ubuntu, since I'm installing on a rather old laptop.

---

### Post by tuxcantfly on 2007-10-22
> **guyver said:**
> Sorry for this stupid question, but do I do this before or after I do the "apt-get update"?



I really appreciate your time and patience on this.  This is what I think the whole procedure has evolved into (I'm not 100% certain on the dpkg lines)

 

Create sources.list file:

```
1.  **su root**
2.  **echo \**
3.  **"**
4.  **deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted multiverse universe**
5.  **deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security main restricted multiverse universe**
6.  **deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted multiverse universe**
7.  **deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted multiverse universe**
8.  **" > /etc/apt/sources.list**
```

Import Ubuntu GPG key [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

```
1.  **gpg --keyserver pgpkeys.mit.edu --recv-key 40976EAF437D05B5**
2.  **gpg --edit-key [email]ftpmaster@ubuntu.com[/email]**
3.  **fpr**
4.  **quit**
5.  **gpg -a --export *[COLOR="Red"][8-digit requesting key][/COLOR]* | apt-key add -**
```

Update dpkg ( I've had bad luck with sudo for the Floppy Install) [http://packages.debian.org/dpkg](http://packages.debian.org/dpkg)

```
Install Debian Etch Version:
1.**  wget http://http.us.debian.org/debian/pool/main/d/dpkg/dpkg_1.13.25_i386.deb**
2.  **sudo dpkg -i ./dpkg_1.13.25_i386.deb**

Upgrade to Debian Lenny Version:
3.  **wget http://http.us.debian.org/debian/pool/main/d/dpkg/dpkg_1.14.7_i386.deb**
4.  **sudo dpkg -i ./dpkg_1.14.7_i386.deb** 
```

Get Updates & Install

```
1.  **apt-get update**
2.  **apt-get dist-upgrade**
3.  **apt-get install xubuntu-desktop**
```

One thing I also forgot to ask is should I install GRUB when prompted near the end of my Debian Minimal Install?  Also just for clarification, when asked to select the type of install (i.e. desktop, laptop, server, etc.), do I deselect everything and  contintue in order to do the minimal installation you had intended?

Yes, install GRUB

Deselect everything, it'll all be installed with the xubuntu-desktop package

As for sudo not working, perhaps try using "su" instead

---

### Post by tuxcantfly on 2007-10-22
> **luluone said:**
> Hello,

First, thank you for that forum.

I have a question
I install package UNetbootin-ubuntu710rev48 on Ubuntu Feisty but I have an error 17.
I try to defrag.

I think it come from menu.lst

There is my menu.lst



In the unetbootin section what must be the root (hdx,x)?
(Grub is on the MBR of hd0,0).
Excuse me for my english
Thank you for your help

Your menu.lst indicates that (hd2,1) is where your /boot is (apparently you have a separate /boot, my partition detection scheme wasn't designed to handle that), try changing the last entry to (hd2,1)

---

### Post by tuxcantfly on 2007-10-22
> **asbjornu said:**
> I ran the Ubuntu 7.10 Windows installer in Windows 98 and the Windows-part of the installation seemed to go fine, but then it asks me to boot and when I do, it's like nothing happened. Grub doesn't start, I just boot directly into Windows and then UNetboot is uninstalled. Doing it again yields the exact same result.

It seems as if UNetboot isn't able to write to the bootloader for some reason, even though I don't get any error messages. Can I debug this somehow (with a switch to unetbootin-ubuntu710rev48.exe or something)? Any help is highly appreciated! :)

Oh and I didn't think of it before, but I really want Xubuntu instead of Ubuntu, since I'm installing on a rather old laptop.

Strange, haven't tested it too much on Win9x, that might be the issue... anyhow mind posting your C:\config.sys? Does it have anything along the lines of "Ubuntu" or "grub" written in it? It should look like described in [http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Starting_GRUB_for_DOS_from_DOS](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Starting_GRUB_for_DOS_from_DOS)

---

### Post by guyver on 2007-10-22
> **tuxcantfly said:**
> Yes, install GRUB

As for sudo not working, perhaps try using "su" instead

One typo I had was what I thought was a lower case "I" for the installation of the dpkg.  It turns out it was a lower case "L".

sudo definitely does not work.  However when I do a su, the system says:

> Unknown id: dpkg

---

### Post by tuxcantfly on 2007-10-22
> **guyver said:**
> One typo I had was what I thought was a lower case "I" for the installation of the dpkg.  It turns out it was a lower case "L".

sudo definitely does not work.  However when I do a su, the system says:

```
su root
```

that'll ask for root password, give it
then afterwards, enter:

```
dpkg -i ...
```

and that'll run the commands after that as root

---

### Post by guyver on 2007-10-22
> **tuxcantfly said:**
> ```
su root
```

that'll ask for root password, give it
then afterwards, enter:

```
dpkg -i ...
```

and that'll run the commands after that as root

Okay, that did the trick.  But now when I try to install the Lenny dpkg, I get the following error:

> dpkg: regarding ./dpkg_1.14.7_i386.deb containing dpkg, predependency problem: dpkg pre-depends on libc6 (>= 2.6.1-1)

libc6 is installed, but is version 2.3.6.ds1-13etch2.

dpkg: error processing ./dpkg_1.14.7_i386.deb (--install):
pre-dependency problem - not installing dpkg

Errors were encountered while processing:
./dpkg_1.14.7_i386.deb

Is the Lenny dpkg imperative?

---

### Post by tuxcantfly on 2007-10-22
> **guyver said:**
> Okay, that did the trick.  But now when I try to install the Lenny dpkg, I get the following error:



Is the Lenny dpkg imperative?

Ayay, seems like you're going to have to do a full dist-upgrade to lenny before you can upgrade to gutsy... see here: [http://www.pendrivelinux.com/2007/10/06/how-to-upgrade-from-etch-to-lenny/](http://www.pendrivelinux.com/2007/10/06/how-to-upgrade-from-etch-to-lenny/) and here: [http://forums.debian.net/viewtopic.php?t=19237&highlight=lenny](http://forums.debian.net/viewtopic.php?t=19237&highlight=lenny)

---

### Post by tuxcantfly on 2007-10-22
> **guyver said:**
> Okay, that did the trick.  But now when I try to install the Lenny dpkg, I get the following error:



Is the Lenny dpkg imperative?

Also, the lenny floppy images on the debian ftp site can be found here: [ftp://ftp.debian.org/debian/dists/testing/main/installer-i386/current/images/floppy](ftp://ftp.debian.org/debian/dists/testing/main/installer-i386/current/images/floppy)

Might be easier just to start from those

---

### Post by guyver on 2007-10-22
> **tuxcantfly said:**
> Ayay, seems like you're going to have to do a full dist-upgrade to lenny before you can upgrade to gutsy... see here: [http://www.pendrivelinux.com/2007/10/06/how-to-upgrade-from-etch-to-lenny/](http://www.pendrivelinux.com/2007/10/06/how-to-upgrade-from-etch-to-lenny/) and here: [http://forums.debian.net/viewtopic.php?t=19237&highlight=lenny](http://forums.debian.net/viewtopic.php?t=19237&highlight=lenny)

Do I also add the deb-src lines in the 2nd link you provided before the ubuntu lines within the sources.list file?

---

### Post by guyver on 2007-10-22
I went ahead with the apt-get update (using all 4 Lenny lines in example of 2nd link) and got the following error:

> Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occured while processing mgetty (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_gutsy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

This is what I put at the beginning of my sources.list file:

> deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) lenny main
deb-src [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) lenny main

deb [http://security.debian.org/](http://security.debian.org/) lenny/updates main contrib
deb-src [http://security.debian.org/](http://security.debian.org/) lenny/updates main contrib 

If I opt to do a Feisty Xubuntu, can I avoid the Lenny dpkg?

---

### Post by tuxcantfly on 2007-10-22
> **guyver said:**
> I went ahead with the apt-get update (using all 4 Lenny lines in example of 2nd link) and got the following error:



This is what I put at the beginning of my sources.list file:

Ouch, that doesn't sound good... I think you should start again using the lenny floppies at [ftp://ftp.debian.org/debian/dists/testing/main/installer-i386/current/images/floppy](ftp://ftp.debian.org/debian/dists/testing/main/installer-i386/current/images/floppy) that'll probably save you some time and frustration; you'll be able to upgrade directly to Gutsy that way

As for the rest, I'm not sure; I haven't tried the Debian-to-Ubuntu-by-dist-upgrade conversion approach since Debian Sarge -> Ubuntu 5.10 so things are likely quite different now

---

### Post by guyver on 2007-10-22
> **tuxcantfly said:**
> Ouch, that doesn't sound good... I think you should start again using the lenny floppies at [ftp://ftp.debian.org/debian/dists/testing/main/installer-i386/current/images/floppy](ftp://ftp.debian.org/debian/dists/testing/main/installer-i386/current/images/floppy) that'll probably save you some time and frustration; you'll be able to upgrade directly to Gutsy that way

As for the rest, I'm not sure; I haven't tried the Debian-to-Ubuntu-by-dist-upgrade conversion approach since Debian Sarge -> Ubuntu 5.10 so things are likely quite different now

If I use the Lenny disks, do I need to add those comments concerning Lenny in my sources.list file?  And do I need to get the dpkgs for that mattter?

---

### Post by tuxcantfly on 2007-10-22
> **guyver said:**
> If I use the Lenny disks, do I need to add those comments concerning Lenny in my sources.list file?  And do I need to get the dpkgs for that mattter?

No, you should be able to just upgrade directly to Gutsy, however, can't quite guarantee it'll work perfectly (haven't tried this procedure in years).

---

### Post by guyver on 2007-10-22
> **tuxcantfly said:**
> No, you should be able to just upgrade directly to Gutsy, however, can't quite guarantee it'll work perfectly (haven't tried this procedure in years).

Ah, so I can skip the getting a key as well?  I'm on it now... crossing my fingers.  If this fails, I guess this old notebook will have to be a Debian box.  

For the life of me, it seems there are A LOT of people asking for this feature to be able to do a floppy install and it seems to fall on deaf ears with Canonical.  How hard could it be for them to make a Ubuntu version of Debian's floppy install?

---

### Post by tuxcantfly on 2007-10-22
> **guyver said:**
> Ah, so I can skip the getting a key as well?  I'm on it now... crossing my fingers.  If this fails, I guess this old notebook will have to be a Debian box.  

For the life of me, it seems there are A LOT of people asking for this feature to be able to do a floppy install and it seems to fall on deaf ears with Canonical.  How hard could it be for them to make a Ubuntu version of Debian's floppy install?

for 1: yes you will need the Ubuntu gpg key, and you'll need to add the ubuntu lines to the /etc/apt/sources.list and the other instructions I described in my original post, however you won't need to deal with the rest of the madness

for 2: ubuntu's kernel doesn't fit on a floppy drive (it's 1.7 MB as of Gutsy), I believe that's why

---

### Post by tuxcantfly on 2007-10-22
> **guyver said:**
> Ah, so I can skip the getting a key as well?  I'm on it now... crossing my fingers.  If this fails, I guess this old notebook will have to be a Debian box.  

For the life of me, it seems there are A LOT of people asking for this feature to be able to do a floppy install and it seems to fall on deaf ears with Canonical.  How hard could it be for them to make a Ubuntu version of Debian's floppy install?

Come to think of it, can't believe I haven't realized it, you have a working debian system now, you can just use UNetbootin (the deb package) to install Ubuntu Gutsy. Just download with wget, and do the usual dpkg -i, reboot, and select "UNetbootin". Don't bother with the dist-upgrade approach I mentioned, UNetbootin will do the job way better.

---

### Post by guyver on 2007-10-22
> **tuxcantfly said:**
> Come to think of it, can't believe I haven't realized it, you have a working debian system now, you can just use UNetbootin (the deb package) to install Ubuntu Gutsy. Just download with wget, and do the usual dpkg -i, reboot, and select "UNetbootin". Don't bother with the dist-upgrade approach I mentioned, UNetbootin will do the job way better.

Ah, so immediately after doing the minimal install, I should use this UNetbootin to install Xubuntu?  I clicked on your signature block dealing with UNetbootin but it seems the link there assumes I already have a GUI linux to run from... did I miss something?  The SourceForge link I think is dead.

But you're saying this other approach requires my installing Etch and Lenny?

---

### Post by tuxcantfly on 2007-10-22
> **guyver said:**
> Ah, so immediately after doing the minimal install, I should use this UNetbootin to install Xubuntu?  I clicked on your signature block dealing with UNetbootin but it seems the link there assumes I already have a GUI linux to run from... did I miss something?  The SourceForge link I think is dead.

Sourceforge link is dead? Whoa that's not good, it's supposed to be at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821) exactly where is it linking from?

Anyhow all you need is dpkg, GRUB, and internet access. No need for a fancy GUI environment. Download the deb using wget, using dpkg -i to install, then reboot.

> But you're saying this other approach requires my installing Etch and Lenny?

You need to have something installed beforehand, to boot off of in the first place. Installing Debian just happens to be the easiest approach if you have no OS on your hard drive in the first place, anything else (Windows, Linux) will do.

---

### Post by guyver on 2007-10-22
> **tuxcantfly said:**
> Sourceforge link is dead? Whoa that's not good, it's supposed to be at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821) exactly where is it linking from?

Anyhow all you need is dpkg, GRUB, and internet access. No need for a fancy GUI environment. Download the deb using wget, using dpkg -i to install, then reboot.



You need to have something installed beforehand, to boot off of in the first place. Installing Debian just happens to be the easiest approach if you have no OS on your hard drive in the first place, anything else (Windows, Linux) will do.

Sorry, I meant the tutorial link found in your signature block's link appears to be dead.

I'm sort of confused.  When you say dpkg, you are referring to Etch and Lenny, right?

I also do not know what you mean by "the deb".

I was thinking I just redo a minimal install and go straight to UnetBootin... I just don't know how I go about getting this onto the old laptop I'm trying to use as a linux box... and yes I would be using the laptop entirely for Linux so there's no worry about data loss.

---

### Post by tuxcantfly on 2007-10-22
> **guyver said:**
> Sorry, I meant the tutorial link found in your signature block's link appears to be dead.

I'm sort of confused.  When you say dpkg, you are referring to Etch and Lenny, right?

I also do not know what you mean by "the deb".

I was thinking I just redo a minimal install and go straight to UnetBootin... I just don't know how I go about getting this onto the old laptop I'm trying to use as a linux box... and yes I would be using the laptop entirely for Linux so there's no worry about data loss.

"The deb" refers to this file (ends in .deb): [http://downloads.sourceforge.net/lubi/unetbootin_ubuntu710rev48_all.deb?modtime=1192914068&big_mirror=0](http://downloads.sourceforge.net/lubi/unetbootin_ubuntu710rev48_all.deb?modtime=1192914068&big_mirror=0)

When I say dpkg I mean boot your Debian install (whichever one you have, doesn't really matter), and after downloading the file I linked to 

```
wget http://downloads.sourceforge.net/lubi/unetbootin_ubuntu710rev48_all.deb

```
Then install the package:

```
su root
dpkg -i ./unetbootin_ubuntu710rev48_all.deb
```

Then reboot, select UNetbootin in the grub menu, after that it's just standard Ubuntu install process

PS is my sig link still dead? Seems to work fine for me...

---

### Post by guyver on 2007-10-22
> **tuxcantfly said:**
> "The deb" refers to this file (ends in .deb): [http://downloads.sourceforge.net/lubi/unetbootin_ubuntu710rev48_all.deb?modtime=1192914068&big_mirror=0](http://downloads.sourceforge.net/lubi/unetbootin_ubuntu710rev48_all.deb?modtime=1192914068&big_mirror=0)

When I say dpkg I mean boot your Debian install (whichever one you have, doesn't really matter), and after downloading the file I linked to 

```
wget http://downloads.sourceforge.net/lubi/unetbootin_ubuntu710rev48_all.deb

```
Then install the package:

```
su root
dpkg -i ./unetbootin_ubuntu710rev48_all.deb
```

Then reboot, select UNetbootin in the grub menu, after that it's just standard Ubuntu install process

PS is my sig link still dead? Seems to work fine for me...

I'm redoing the Debian installation just for good luck.  How do I get UNetbootin to install Xubuntu instead of Ubuntu?

---

### Post by tuxcantfly on 2007-10-22
> **guyver said:**
> I'm redoing the Debian installation just for good luck.  How do I get UNetbootin to install Xubuntu instead of Ubuntu?

Part of the install process, it'll ask you. Was already described nicely in this thread a few pages ago, go check if you need more details. (I think I really need to reorganize this thread...)

---

### Post by asbjornu on 2007-10-23
> **tuxcantfly said:**
> Strange, haven't tested it too much on Win9x, that might be the issue... anyhow mind posting your C:\config.sys? Does it have anything along the lines of "Ubuntu" or "grub" written in it? It should look like described in [http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Starting_GRUB_for_DOS_from_DOS](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Starting_GRUB_for_DOS_from_DOS)
I'm not on my computer to check for this right now, but I'll do ASAP and report back. If UNetbootin isn't able to fix config.sys, I'll just hack it myself according to the nice explanation in that Grub4DOS tutorial you linked to. Thanks!

> **tuxcantfly said:**
> (I think I really need to reorganize this thread...)
Don't you think UNetbootin deserves its own forum? Much easier to organize different discussions when they can evolve in their own threads. The information overload and activity in this thread surely demands that UNetbootin gets its own forum, no?

---

### Post by nooby on 2007-10-23
> (I think I really need to reorganize this thread...)

Tux that is a good idea. I love this thread. 

I failed using the Live CD for Ubuntu 6.06 to install that distro. it could not use the free space cause it has an unmoveable file in it. 

Are the resizing tool in UNetbootin able to move the windows unmoveable file? I don't know its name and have no clue on how to find out its name either. 

Could it be the swapfile. It looks very big in the defrag program. 

I've decided to dedicate an old computer compac HP D230MT as my learning tool. It has unfortunate only 250megabyte memory so maybe a bit less than what is best. 
The hardisk now is owned by Win XP pro but I have 27Giga free space but many unmoveable files in it so I need some kind of prog that could move unmoveable files. 

Would you advice against using UNetbootin with such low on memory? 

I maybe could use memory from another compac computer if the physical size is same. Both are HP/ Compac som hopefully their holders for memory are same. 

I need to make olace for the three partions for  linux. 

I have a Live CD for Ubuntu 6.06 so maybe that one have the resizing tool I need. It failed cause the unmoveable was an obstacle? 

Or is that one built in into UNetbootin?

---

### Post by tuxcantfly on 2007-10-23
> I failed using the Live CD for Ubuntu 6.06 to install that distro. it could not use the free space cause it has an unmoveable file in it. 

Are the resizing tool in UNetbootin able to move the windows unmoveable file? I don't know its name and have no clue on how to find out its name either. 

Could it be the swapfile. It looks very big in the defrag program. 

Probably, that's pagefile.sys (the swapfile). See here on how to get rid of it (you can re-enable it later): [http://www.raymond.cc/blog/archives/2007/10/17/is-it-safe-to-delete-hiberfilsys-and-pagefilesys/](http://www.raymond.cc/blog/archives/2007/10/17/is-it-safe-to-delete-hiberfilsys-and-pagefilesys/)

Also remember to defrag your hard drive if you haven't done so already, that helps on the resizing bit.

> I've decided to dedicate an old computer compac HP D230MT as my learning tool. It has unfortunate only 250megabyte memory so maybe a bit less than what is best. 
The hardisk now is owned by Win XP pro but I have 27Giga free space but many unmoveable files in it so I need some kind of prog that could move unmoveable files. 

Would you advice against using UNetbootin with such low on memory? 

Yep UNetbootin will work fine on low-ram computers (it uses the text-based interface, so it doesn't need as much RAM as much as the liveCD does)

> Or is that one built in into UNetbootin?

You'll be able to partition it during the installation phase. I also have the UNetbootin installer for Parted Magic on the download page (under the name Partition Manager), that'll also let you manage your partitons using GParted. Granted, if 6.06 didn't work, that probably won't work either, but doesn't hurt to try (maybe the newer version fixed some of the issues).

---

### Post by nooby on 2007-10-24
Thanks for tip on these but it doesn't seem to be them. I did as they say there in the link but still have an enormous big one up in the space I want to place 7.04 or 7.1 in. 

Could it be the swap file. Is that one safe to take away? I tried to find it but failed. 

could it be a restore point that have saved a kind of mirror of windows? 

**How do I find what the name of the file is?**

---

### Post by tuxcantfly on 2007-10-24
> **nooby said:**
> Thanks for tip on these but it doesn't seem to be them. I did as they say there in the link but still have an enormous big one up in the space I want to place 7.04 or 7.1 in. 

Could it be the swap file. Is that one safe to take away? I tried to find it but failed. 

could it be a restore point that have saved a kind of mirror of windows? 

**How do I find what the name of the file is?**

Doesn't it show it in the disk defragmenter? It can't be swap, then; that's pagefile.sys (which was described in the guide I linked to)

---

### Post by nooby on 2007-10-24
Yes the trick was to say it should be 2 meg and then to no pagefile at all which is 2 meg and then to reboot so now I will try unetbootin. I am writing on that computer now. 28 gig free I will try to tell unetbootin to use 20 gig for linux. But I ahve no knowledge on how to do that. But I try. 

should I use 7.04 first or go directly to 7.1 ?

---

### Post by tuxcantfly on 2007-10-24
> **nooby said:**
> Yes the trick was to say it should be 2 meg and then to no file which is 2 meg and then to reboot so now I will try unetbootin. I am writing on that computer now. 28 gig free I will try to tell unetbootin to use 20 gig for linux. But I ahve no knowledge on how to do that. But I try. 

should I use 7.04 first or go directly to 7.1 ?

Go straight to 7.10. As for the partitioning bit, just let it do automatic partitioning; it'll have an option to use the free space (or you can also select the manual partitioning approach). More info at [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by nooby on 2007-10-24
I try 7.1 then but I forgot to ask an important question. 

I need to give linux important numbers that have to do with DNS and such. For a noob a newbie that is totally beyond me. 

I have no clue on such figures. 

I remember it came up in another thread but don't remember now. 

Could be in wubi forum. I asked about it there?  Do you have a clue on dns?

Search found it but none answered it. 

"have your IP-address-gateway-dns-server-info ready"

how do I find out such?

I've found two of them now in the LAN box but the third?

---

### Post by tuxcantfly on 2007-10-24
> **nooby said:**
> I try 7.1 then but I forgot to ask an important question. 

I need to give linux important numbers that have to do with DNS and such. For a noob a newbie that is totally beyond me. 

I have no clue on such figures. 

I remember it came up in another thread but don't remember now. 

Could be in wubi forum. I asked about it there?  Do you have a clue on dns?

DNS? It asks you for it? Don't you have a plain DSL or Cable connection? Are you using wireless? Maybe try using wired internet for now. Other than that, if you're on a static connection that doesn't automatically configure your DNS and all, you'll need to check your ISP's manual and such for DNS info; it's different for everyone.

---

### Post by nooby on 2007-10-24
Now I get it. It was easy if one had been told to be fast on the trigger. One should go one down and hit enter. If one doen't do this within a second of that screen it goes to directly to windows. 

My keyboard was not detected properly so now I ahve a keyboard totally wrong chars on it. Hope I could change that later. 
It was impossible to undo the unfortunate error by going back. It ignored such attempts. 

my Old text

I have dowloaded the unetbooin exe file and have rebooted it to install now.

Now it ask the trick question if I want to uninstall the unetbootin. 

it seems to go in a loop. 

It says that in order to install it need to reboot. 
Ok I do that and then it asks if I really want to uninstall the installer. 

What to do? If I answer No then it just don't do anything. 
If I answer yes it says it has done a successful Uninstall. 

but the menu never come up. 

Could my pagefil be too small then. I have two meg in it nowwhat should it make it for unetbootin to work?

---

### Post by nooby on 2007-10-24
The prog says that it fail to resize and then it says it is too small. 

But I have 28 gig of free space now that the page file is moved out of the white space to the right. 

so what could it be? 

When I try to do the Manual partitioning it shows options I don't get what it means.

It looks as if it want to take away the whole windows so I need more info on how to partition.

---

### Post by nooby on 2007-10-24
Tux,
 I've read up on partitioning now in both windows and ubuntu. 

Those who write those instructions have no clue on what a nooby is. 

They are not detailed enough to be understood by the average user like me. 

My neighbor see me as a computer guru and I fail to get it. 

I want to use the UNetbootin program. 

What now. How could I safely use the manul partition tool. 

What to answer when it asks? It doesn't indicate where it will put the partition. the whole area is win NYFS the left area on the hdd some 11giga is used by windows xp. so there is 27 gigaunleft  left to the right. I want to put linux on some 20 giga there and use the 7 giga over as windows ntfs while linux should have ext3 I guess. 

How do I do it? 

Now how do I tell the partition tool to use say 20 giga to the right so windows get 7 giga of free space and Linux the 20 giga to the right and those 20 giga shoudl have three partiotions on them. Home, Swap, and the free space. 

One need a step for step instruction. 

The guided is not to be trusted. I read numerous of users who wiped out all the windows files.

---

### Post by nooby on 2007-10-24
qtparted on the live 6.06 CD failed to resize too. 

So I need to find out while resizing fails. some say one should delete a windows prog that protect the hdd from being partitioned. the Guardian program something?

Even geeks seems to be skeptical. Look here what one of them says: 

> Using GParted to Resize Your Windows Vista Partition

One of the more advanced options for resizing your Windows Vista partition is to use the GParted Live CD, a bootable linux CD that takes you straight into GParted, the great linux utility for managing partitions. The problem is that if you resize your boot/system partition, you will be completely unable to boot without repairing windows.

First make sure that you have a bootable Windows Vista installation DVD, as you will be unable to use your computer if you don't.

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/")

If even such persons says it is difficult then one wonder how noobs should do it. Yes I know when it works it just works. 

But this is first time for me and it failed to resize the ntfs hdd so I don't know what to do now. 

should I install wubi and see if the shotdown error rise in that older computer too or maybe older computers don't have it?

---

### Post by nooby on 2007-10-24
I felt so disappointed that I failed to make partitions so I dowloaded wubi instead so I at least hav something to learn linux on. 

if I am lucky it allow me to shutdown on this computer cause the more modern one had the acpi or dsdt error? 

I write in linux wubi now. and will test the shutdown and get back and tell result.

Edit

yes linux wubi worked on that computer despite it told of 4 different problems with 
failed to set xfer  mod err_mask=0x4 and 0x40 and I had to restart it three times. 

Now I only need a step for step instruction on how to find out why the resize and partitioning failed.

---

### Post by asbjornu on 2007-10-25
> **asbjornu said:**
> I'm not on my computer to check for this right now, but I'll do ASAP and report back. If UNetbootin isn't able to fix config.sys, I'll just hack it myself according to the nice explanation in that Grub4DOS tutorial you linked to.
I managed to take a look at this yesterday and indeed the grub stuff was missing from config.sys. I added the following lines to my config.sys file after installation (but before pressing the "Reboot" button):
```

device=grub.exe
install=grub.exe
shell=grub.exe
```
And then rebooted. After the boot, Grub started just fine and now I have Xubuntu 7.10 on my laptop. In other words, it worked great! Thanks for making this fantastic application! I know I will have much use for in the future as well, so please continue improving it. :)

---

### Post by dweissma on 2007-10-25
Is it possible to install Ubuntu over a wireless Internet connection? My old laptop has a wireless PC Card but no ethernet port to connect to my cable modem. Thanks

---

### Post by tuxcantfly on 2007-10-27
> **dweissma said:**
> Is it possible to install Ubuntu over a wireless Internet connection? My old laptop has a wireless PC Card but no ethernet port to connect to my cable modem. Thanks

Unfortunately, no; Ubuntu doesn't provide the option to install using pre-downloaded packages. However, the UNetbootin Fedora version does; you may want to try that instead; see [http://docs.fedoraproject.org/install-guide/f7/en_US/sn-installing-from-harddrive.html](http://docs.fedoraproject.org/install-guide/f7/en_US/sn-installing-from-harddrive.html)

---

### Post by tuxcantfly on 2007-10-28
I've finally managed to get my hands on the new Vista bootloader system in the form of the Windows Server 2008 Release Candidate Evaluation Edition (which theoretically works the same), so I've managed to get UNetbootin working on Vista.

I've uploaded the new Vista-compatible builds of UNetbootin for Ubuntu 7.10, download it at the usual spot at [https://sourceforge.net/project/showfiles.php?group_id=198821](https://sourceforge.net/project/showfiles.php?group_id=198821)

I'll have the rest uploaded soon (pesky dsl connection is a bit slow), if it works for any of you or doesn't on Vista please just make a short post confirming it.

Oh and if any of you are wondering why the revsion numbers have gone back to 1, it's because bzr choked out on me while I was committing, and I ended up with an utterly broken branch, so I had to transfer my code to a new location at [https://code.edge.launchpad.net/~gezakovacs/unetbootin/devel-new](https://code.edge.launchpad.net/~gezakovacs/unetbootin/devel-new) . The 100 is just so that it appears first in the download section.

---

### Post by tuxcantfly on 2007-10-28
I've also updated the Mandriva 2008, OpenSuse 10.3, Fedora 7, and PartedMagic Partition Manager packages to work on Vista as well.

Fedora 8 is coming out in 12 days, I'll have the UNetbootin Fedora 8 packages available soon.

---

### Post by GZBurtchell on 2007-10-28
> **tuxcantfly said:**
> I've also updated the Mandriva 2008, OpenSuse 10.3, Fedora 7, and PartedMagic Partition Manager packages to work on Vista as well.

Fedora 8 is coming out in 12 days, I'll have the UNetbootin Fedora 8 packages available soon.



Will UNetbootin work for installing Ubuntu Studio 7.10?

---

### Post by tuxcantfly on 2007-10-28
> **GZBurtchell said:**
> Will UNetbootin work for installing Ubuntu Studio 7.10?

Yes, you can select between the various *buntus (ubuntu,kubuntu,xubuntu,gobuntu,studio,server) in a dialog that appears after the "installing base system" phase is done.

---

### Post by GZBurtchell on 2007-10-29
> **tuxcantfly said:**
> Yes, you can select between the various *buntus (ubuntu,kubuntu,xubuntu,gobuntu,studio,server) in a dialog that appears after the "installing base system" phase is done.

Well, I got as far as "Select And Install Software", selected Ubuntu Studio Desktop, the next window came up, the indicator bar sat at 6% for a bit then shot up to 85% and then this message came up:

Select And Install Software
Installation Step Failed
The Failing Step Is:
Select And Install Software

I thought it might be a mirror that was too congested so I tried a couple of different ones but got the same message. I aborted out of it rather than let it continue until I know what the problem is and how to corect it.

---

### Post by tuxcantfly on 2007-10-29
> **GZBurtchell said:**
> Well, I got as far as "Select And Install Software", selected Ubuntu Studio Desktop, the next window came up, the indicator bar sat at 6% for a bit then shot up to 85% and then this message came up:

Select And Install Software
Installation Step Failed
The Failing Step Is:
Select And Install Software

I thought it might be a mirror that was too congested so I tried a couple of different ones but got the same message. I aborted out of it rather than let it continue until I know what the problem is and how to corect it.

Do you get the same error when you just select "Ubuntu", or is it just an ubuntustudio-specific error? Also, did you actually select the entry (using space) so that a star appears next to it before pressing enter? (Simply going over it and pressing enter without selecting with space isn't going to mark it for installation)

Also, on another note, I've found a minor bug with UNetbootin on Vista; the install folder c:\unetbootin isn't properly removed after uninstallation. I've uploaded a new build for Ubuntu 7.10 to fix that, users of the other builds can just remove the folder manually after uninstallation if it remains residual after uninstall.

---

### Post by tuxcantfly on 2007-10-29
Also, note for any users using Windows Vista or Server 2008:

Vista has its own partition manager, which can be started with the command:

```
diskmgmt.msc
```

It can be used to shrink the NTFS partition to make space for Ubuntu's partition, and may work better than Ubuntu's partitioner. Details on using the graphical tool are at [http://www.pro-networks.org/forum/viewstory.php?t=78111](http://www.pro-networks.org/forum/viewstory.php?t=78111) and [http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/](http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/)

Should the graphical tool not work, you can also use diskpart, a commandline tool:

```
diskpart
```

Details at [http://www.mydigitallife.info/2007/09/26/using-diskpartexe-as-disk-management-alternative-in-windows-vista-2000-2003-and-xp/](http://www.mydigitallife.info/2007/09/26/using-diskpartexe-as-disk-management-alternative-in-windows-vista-2000-2003-and-xp/) and [http://vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work/](http://vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work/)

I've added this info to the main website and first post

---

### Post by GZBurtchell on 2007-10-29
> **tuxcantfly said:**
> Do you get the same error when you just select "Ubuntu", or is it just an ubuntustudio-specific error? Also, did you actually select the entry (using space) so that a star appears next to it before pressing enter? (Simply going over it and pressing enter without selecting with space isn't going to mark it for installation)

Also, on another note, I've found a minor bug with UNetbootin on Vista; the install folder c:\unetbootin isn't properly removed after uninstallation. I've uploaded a new build for Ubuntu 7.10 to fix that, users of the other builds can just remove the folder manually after uninstallation if it remains residual after uninstall.


I'm using the Linux version of UNetbootin and happily running with Grub. I already have Gutsy installed, (dual boot with WinXP), so I didn't think to try that or a different version, other than the Ubuntu Studio that I wanted to install.  I definately selected the Ubuntu Studio Desktop entry, and properly selected it with the star in the box next to it. I checked the partition it was to be installed on and the folders are there though most being empty or incomplete.

My internet connection was working fine. I'm thinking I had the unfortunate luck of catching a bad day on the mirrors. Though I did try four different ones with the same results. I'll give it another shot tonight and see what happens.

---

### Post by GZBurtchell on 2007-10-29
I found the problem.

Note: You MUST have a floppy drive plugged in and enabled.

Gutsy did the same thing. It had a fit and wouldn't install until I plugged the darn thing back in. I used the floppy drive perhaps 3 times in as many years. Pretty useless so I pulled it out, stuck it in a drawer, and disabled the FD controller in the bios. And to think, I still have a 5.25" drive and floppies hanging around, as well as a true dinosaur 8" drive from my first computer - for nostalgia. :-) 

After I plugged the floppy drive back in and enabled the controller the installer ran fine.

---

### Post by asbjornu on 2007-10-30
[Can we please get a separate UNetbootin forum please? :)]

I'm thinking of buying a new harddrive to my old Compaq Armada M300 and don't have any way to boot onto anything from the computer. What I'm thinking is to buy a USB jacket to the new harddrive and load UNetbootin onto it from another computer somehow.

Can someone please explain to me how I should make the new harddrive bootable and set up with UNetbootin before I plug it into the laptop and install Linux on it there?

I'm thinking this might work (please correct me if I'm wrong):

1. Attach the clean, new laptop harddrive to another Windows-based computer (I have Cygwin and can install Linux if that helps).
2. Format the laptop drive with the "/s" option to put Windows boot files on it so it can boot.
3. Download UNetbootin and put it on the laptop harddrive.
4. Detach the laptop harddrive and plug it into the laptop.
5. Boot the laptop up on the new harddrive and install Linux from UNetbootin.

What I'm not really confident about is step 2. I'm not sure Windows allows me to format a harddrive as a system bootable drive, since it isn't a floppy. Is there a way to format a random drive as bootable (e.g. fill the boot sector with something bootable) from Cygwin or Linux? If there is, what is the procedure? How can I modify the steps above to make such a solution work?

Thanks!

---

### Post by tuxcantfly on 2007-10-30
> **asbjornu said:**
> [Can we please get a separate UNetbootin forum please? :)]

Just made a request to ubuntu-geek (this forum's admin), expect one soon...

> I'm thinking of buying a new harddrive to my old Compaq Armada M300 and don't have any way to boot onto anything from the computer. What I'm thinking is to buy a USB jacket to the new harddrive and load UNetbootin onto it from another computer somehow.

Can someone please explain to me how I should make the new harddrive bootable and set up with UNetbootin before I plug it into the laptop and install Linux on it there?

Easier approach, I think, would be to just install GRUB and a minimal Linux distro onto it (floppy-install of Debian or something), then you can install the UNetbootin Linux package and that'll do the job.

FYI, to install GRUB to the MBR of a drive, you use the command grub-install, some details are at [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm) Once you have GRUB installed you can just place the initrd and kernel files onto /boot and update the menu.lst to load them (or UNetbootin can automatically do it for you as well if you copy over a base system and boot that and install the UNetbootin package).

On another note, I've updated the Arch, OpenSuse, Fedora, and Mandriva builds (rev7) to fix the vista-uninstallation bug in the earlier version (rev1) (Ubuntu builds have already been updated)

---

### Post by asbjornu on 2007-11-01
> **tuxcantfly said:**
> Just made a request to ubuntu-geek (this forum's admin), expect one soon...
Great!

> **tuxcantfly said:**
> Easier approach, I think, would be to just install GRUB and a minimal Linux distro onto it (floppy-install of Debian or something), then you can install the UNetbootin Linux package and that'll do the job.
Okay, thanks for the reply. I'll try this out as soon as my new harddrive arrives. The [floppy install](http://linux.simple.be/debian/floppy) I found requires actual floppy disks to be used, though. I can of course fill four floppies with the given disk images, but what I'd like is to have the install on the laptop harddrive. I'm not sure how to achieve that.

> **tuxcantfly said:**
> FYI, to install GRUB to the MBR of a drive, you use the command grub-install, some details are at [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm) Once you have GRUB installed you can just place the initrd and kernel files onto /boot and update the menu.lst to load them (or UNetbootin can automatically do it for you as well if you copy over a base system and boot that and install the UNetbootin package).
This sounds like a way to go, but since I'm completely braindead when it comes to Linux, I don't really know where to start. Could you please point me in the right direction?

---

### Post by Schiavonske1013 on 2007-11-02
hi, just wonderin, is there a way to add the noapic option when booting into the installer, because it wont start without using the noapic option

---

### Post by tuxcantfly on 2007-11-02
> **Schiavonske1013 said:**
> hi, just wonderin, is there a way to add the noapic option when booting into the installer, because it wont start without using the noapic option

Either select the UNetbootin option and mash ESC button immediately afterwards until you see the grub menu, then you can edit the kernel line using 'e' and boot with 'b', or you can also edit the C:\menu.lst file and add noapic to the end of the kernel line of the UNetbootin entry towards the end

---

### Post by ajskhan on 2007-11-03
> **tuxcantfly said:**
> Either select the UNetbootin option and mash ESC button immediately afterwards until you see the grub menu, then you can edit the kernel line using 'e' and boot with 'b', or you can also edit the C:\menu.lst file and add noapic to the end of the kernel line of the UNetbootin entry towards the end

So I downloaded it, rebooted and it is stuck at:


[IMG]http://i172.photobucket.com/albums/w8/ajskhan/3160660298_ORIG.jpg?t=1194128591[/IMG]

Please help, thanks...

---

### Post by tuxcantfly on 2007-11-04
> **ajskhan said:**
> So I downloaded it, rebooted and it is stuck at:

Please help, thanks...

Looks like some kind of hardware incompatibility. Some options that might help (see my previous post) are noapic, noacpi, nolapic, acpi=off, maybe do a google search for your hardware (some motherboads need some more obscure options to work), if none of those work, perhaps try installing Fedora or openSUSE instead (see the website at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) I have instructions for each), they might detect work better with your hardware, perhaps try the desktop/liveCD version of Ubuntu as well (though I doubt that will work if the netboot installer hangs), otherwise, if none of those work, chances are, your hardware isn't compatible with Linux, perhaps try the new opensolaris preview release, pc-bsd, desktopbsd, or freebsd if you still want a unix-like system, otherwise, you're out of luck

---

### Post by hums07 on 2007-11-05
I downloaded Unetbootin for Gutsy, installed it, reboot my computer but it failed to find GRLDR saying: 
> Try (HD0,0): NTFS5:2
Try (HD0,1): NTFS5 No grldr
Try (HD0,2): ....

It then asked for reboot. Rebooting to windows and deny uninstall, I can see the GRLDR in the C:.
Boot.ini entry is correct.
I have tried wubi before and can successfully install on D:, but I want a real install so gave Unetbootin a shot. I cannot use LVPM because HD space is limited, C: is 12 GB and D: is 6 GB. Strangely, I cannot install wubi on C: eventhough I have freed 7.2 GB of HD space.

In short, I seems it was Unetbootin problem that I encountered (because Wubi can do).

---

### Post by tuxcantfly on 2007-11-05
> **hums07 said:**
> I downloaded Unetbootin for Gutsy, installed it, reboot my computer but it failed to find GRLDR saying: 

It then asked for reboot. Rebooting to windows and deny uninstall, I can see the GRLDR in the C:.
Boot.ini entry is correct.
I have tried wubi before and can successfully install on D:, but I want a real install so gave Unetbootin a shot. I cannot use LVPM because HD space is limited, C: is 12 GB and D: is 6 GB. Strangely, I cannot install wubi on C: eventhough I have freed 7.2 GB of HD space.

In short, I seems it was Unetbootin problem that I encountered (because Wubi can do).

After installing UNetbootin but prior to rebooting, copy the files grldr.mbr, grldr, and menu.lst from C:\ to D:\ and whatever other partitions you might have, and try rebooting and select the UNetbootin option as usual; it should work then

---

### Post by tuxcantfly on 2007-11-06
I've added UNetbootin packages for installing Slackware 12.0, download at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821) I've posted instructions at [http://ubuntuforums.org/showthread.php?p=3720797](http://ubuntuforums.org/showthread.php?p=3720797) and [http://slackwarehelp.org/viewtopic.php?p=6427](http://slackwarehelp.org/viewtopic.php?p=6427)

On another note, Fedora 8 is coming out in 2 days, I'll get UNetbootin Fedora 8 No-CD install builds out as soon as possible after it's released...

---

### Post by tuxcantfly on 2007-11-08
Fedora 8 has been released, so I've accordingly added UNetbootin builds to allow for no-CD Fedora installs. You can download the Fedora 8 version at [https://sourceforge.net/project/showfiles.php?group_id=198821&package_id=251761](https://sourceforge.net/project/showfiles.php?group_id=198821&package_id=251761)

If installing Fedora, select "FTP" as the installation source, and for the server, specify:

    **download.fedora.redhat.com**

and for the folder, if using the standard (32-bit) version, specify:

    **pub/fedora/linux/releases/8/Fedora/i386/os**

or if using the 64-bit version, specify:

    **pub/fedora/linux/releases/8/Fedora/x86_64/os**

---

### Post by adolan21 on 2007-11-10
I have Vista and I've tried the mandriva 08 installer but all it does is boot back to Windows.

I have a few questions:

What files do I need before the install, and what to do with them?
What commands do I need to add to my boot file?

Thanks.

---

### Post by tuxcantfly on 2007-11-10
> **adolan21 said:**
> I have Vista and I've tried the mandriva 08 installer but all it does is boot back to Windows.

I have a few questions:

What files do I need before the install, and what to do with them?
What commands do I need to add to my boot file?

Thanks.

Very strange... Anyhow, when you open the Command Prompt in Administrator mode, and enter "bcdedit", does the last entry say "UNetbootin"? If not, apparently it didn't edit the Windows Vista bcd config properly, that would probably be the issue...

Anyhow, to add the entry manually, use the following commands (make sure you run the commmand prompt as administrator):

```
bcdedit /create /d "UNetbootin" /application bootsector
```

Now it'll tell you some long id string, substitute that into wherever I have "someid" in the next few lines (but keep the {brackets} around the id string)

```
bcdedit /set {someid} device boot
bcdedit /set {someid} path \grldr.mbr
bcdedit /displayorder {someid} /addlast
```

Then see if it works afterwards...

EDIT: Perhaps your timeout is set to 0. If that's the case, do this:

```
bcedit /timeout 30
```

That'll set timeout to 30 seconds.

PS What edition of Vista is this? Also, did you upgrade or is this some fresh install? Also did you do any weird system config hacks on it? Also is the timeout set above 0 in bcdedit?

---

### Post by tuxcantfly on 2007-11-10
> **adolan21 said:**
> I have Vista and I've tried the mandriva 08 installer but all it does is boot back to Windows.

I have a few questions:

What files do I need before the install, and what to do with them?
What commands do I need to add to my boot file?

Thanks.

Ok, did some testing, I believe I've pinpointed the problem to the 0 sec timeout issue, so I've uploaded some new builds (ubuntu 7.10, fedora 8, opensuse 10.3, mandriva 2008.0, and slackware 12.0) that now set timeout to 30 sec upon installation. Just remove the old version, download the new one, install, and it should work.

---

### Post by adolan21 on 2007-11-10
Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=D:
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
resumeobject            {bba1c506-1be2-11dc-9377-9b8ba96c3213}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 30

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Microsoft Windows Vista
locale                  en-US
inherit                 {bootloadersettings}
osdevice                partition=C:
systemroot              \Windows
resumeobject            {bba1c506-1be2-11dc-9377-9b8ba96c3213}
nx                      OptIn


That's what it says even after I loaded the new one and it still didn't work:( am I missing some files that I didn't download?  Is there anything I have to have before I use the installer?  I am using Windows Vista Home Premium, and to my knowledge I haven't done any config changes.

---

### Post by tuxcantfly on 2007-11-10
> **adolan21 said:**
> Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=D:
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
resumeobject            {bba1c506-1be2-11dc-9377-9b8ba96c3213}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 30

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Microsoft Windows Vista
locale                  en-US
inherit                 {bootloadersettings}
osdevice                partition=C:
systemroot              \Windows
resumeobject            {bba1c506-1be2-11dc-9377-9b8ba96c3213}
nx                      OptIn


That's what it says even after I loaded the new one and it still didn't work:( am I missing some files that I didn't download?  Is there anything I have to have before I use the installer?  I am using Windows Vista Home Premium, and to my knowledge I haven't done any config changes.

Timeout is set to 30, just like the new version of the installer automatically sets it, so it isn't the 0 sec timeout issue then; however it appears a UNetbootin entry wasn't created for some reason...

I'm not sure if you've already done this, but try opening a command prompt with administrator privileges (right-click, run as administrator), and enter the following commands, line by line, and post the output of each:

```
bcdedit /create /d "UNetbootin" /application bootsector
```

Now it'll tell you some long id string, substitute that into wherever I have "someid" in the next few lines (but keep the {brackets} around the id string)

```
bcdedit /set {someid} device boot
bcdedit /set {someid} path \grldr.mbr
bcdedit /displayorder {someid} /addlast
```

Also, which of the following files/directories exist/are missing in the C:\directory after installation? grldr, grldr.mbr, bootmgr, boot, boot.ini, unetbootin

EDIT: Wait, seems like for some reason you have your boot manager installed on D:\ not C:\, perhaps try copying the files/folders C:\grldr, grldr.mbr, bootmgr, and unetbootin to D:\, uninstall UNetbootin but keep the files in D:\ there, then try running the installer again.

---

### Post by adolan21 on 2007-11-10
That did the trick thanks a lot for your help!! Now I just have to configure my internet settings in order to download it from the ftp

---

### Post by adolan21 on 2007-11-11
I'm having a hard time configuring my internet, I see that I can install it from my harddrive but i am unsure of which one to download.  I see that you wrote not the live CD, but the other file is 4gb, is this the correct file?

This is for Mandriva 2008.

---

### Post by tuxcantfly on 2007-11-11
> **adolan21 said:**
> I'm having a hard time configuring my internet, I see that I can install it from my harddrive but i am unsure of which one to download.  I see that you wrote not the live CD, but the other file is 4gb, is this the correct file?

This is for Mandriva 2008.

Any of the Mandriva 2008.0 "Free" versions will do; just not the "Mandriva One" (LiveCD) version. The "Free" versions are available for download at [ftp://ftp.free.fr/mirrors/ftp.mandriva.com/MandrivaLinux/official/iso/2008.0](ftp://ftp.free.fr/mirrors/ftp.mandriva.com/MandrivaLinux/official/iso/2008.0)

If you don't want to download the whole 4GB DVD version, just use the 700MB "free mini" version.

---

### Post by Jake2500 on 2007-11-11
Hi everyone
I am having trouble with unetbootin.
after i selected the option "UNetbootin-ubuntu710rev10"  on the boot menu it says that grldr.mbr is either missing or currupt. i have checked it exists and reinstalled many times usin difrent versions but always the same error.

bcdedit shows the following:
Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=S:
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
displayorder            {current}
                        {7264b27f-906c-11dc-af56-00016c1a5135}
toolsdisplayorder       {memdiag}
timeout                 30

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Microsoft Windows Vista
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {572bcd55-ffa7-11d9-aae0-0007e994107d}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {0edb023f-72f9-11db-ab67-ee8972af9baa}
nx                      OptIn

Real-mode Boot Sector
---------------------
identifier              {7264b27f-906c-11dc-af56-00016c1a5135}
device                  boot
path                    \grldr.mbr
description             UNetbootin-ubuntu710rev10

---

### Post by tuxcantfly on 2007-11-11
> **Jake2500 said:**
> Hi everyone
I am having trouble with unetbootin.
after i selected the option "UNetbootin-ubuntu710rev10"  on the boot menu it says that grldr.mbr is either missing or currupt. i have checked it exists and reinstalled many times usin difrent versions but always the same error.

bcdedit shows the following:
Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=S:
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
displayorder            {current}
                        {7264b27f-906c-11dc-af56-00016c1a5135}
toolsdisplayorder       {memdiag}
timeout                 30

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Microsoft Windows Vista
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {572bcd55-ffa7-11d9-aae0-0007e994107d}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {0edb023f-72f9-11db-ab67-ee8972af9baa}
nx                      OptIn

Real-mode Boot Sector
---------------------
identifier              {7264b27f-906c-11dc-af56-00016c1a5135}
device                  boot
path                    \grldr.mbr
description             UNetbootin-ubuntu710rev10

Windows bootmgr installed on partition S:\? That certainly seems like some obscure, strange partition configuration... Anyhow try copying the files C:\grldr, grldr.mbr, and menu.lst to every other partition you have before rebooting (including S:\), see if it works then.

---

### Post by adolan21 on 2007-11-12
I ended up doing a Wubi install of Xubuntu, but I am having some problems connecting my wireless card.  I have a broad com 4311 which does state, from their website, to have a linux driver.  I am very new to linux, I have the linux driver download it, but how do I install it?  Can someone be nice enough to go through it step by step and not be so technical with the terminology.  I know the terminal and having to type commands, I just don't know what to type.

---

### Post by tuxcantfly on 2007-11-12
> **adolan21 said:**
> I ended up doing a Wubi install of Xubuntu, but I am having some problems connecting my wireless card.  I have a broad com 4311 which does state, from their website, to have a linux driver.  I am very new to linux, I have the linux driver download it, but how do I install it?  Can someone be nice enough to go through it step by step and not be so technical with the terminology.  I know the terminal and having to type commands, I just don't know what to type.

See [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty) and if that doesn't solve your problem, see the wireless networking subforum at [http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136) and re-ask your question there; this is a UNetbootin-specific thread not a general hardware help forum.

---

### Post by Jake2500 on 2007-11-12
hi guys
thanks for the tip moving the files to S: worked

btw the boot stuff is on S: so if windows decided for some reason to explode or something the recovery software, which is on another partition, would still boot (it requires the windows boot loader)

---

### Post by tuxcantfly on 2007-11-12
> **Jake2500 said:**
> hi guys
thanks for the tip moving the files to S: worked

btw the boot stuff is on S: so if windows decidede for some reason to explode or something the recovery software, which is on another partition, would still boot (it requires the windows boot loader)

Only the installer requires the Windows bootloader (and those changes are undone after your next reboot into Windows). Ubuntu itself (and other distros) uses GRUB, installed to the MBR, so there's no dependency on the Windows bootloader other than for the install process. So no changes to the Windows bootloader are made or needed after the install; everything is reverted back to its original state.

---

### Post by Elotero on 2007-11-12
Would this method create an automatic dual boot? I was going to burn a copy of Ubuntu Studio and create a partition for my brothers laptop to dual boot but if I understand right, this method is just lke a cd? So when i am installing i will get the prompt for partitioning/ offereing me the option to dual boot?

---

### Post by ido370 on 2007-11-12
i just downloaded the installer for archlinux (i386, where's the i686?), but after installing packages and configuring the system and network, i did not install a bootloader, since i thought the LUBI installer would take care of that after the installation, so after i finished everything i rebooted bu i only get the vista bootloader with two unetbootin-archlinuxrev7 entries and they both start the archlinux installer again. what am i doing wrong?

---

### Post by Grimly Fiendish on 2007-11-12
Hi All,

I know this error has appeared previously in this thread (and others) but I think my situation might be different...

I'm trying to use UNetbootin (and have also have Wubi) to install Xubuntu on an old Dell Latitude (CPi 300) with a clapped-out CD drive. 
The laptop is running Windows 2000 Professional on a single partitioned 12Gb HD.

UNetbootin runs/installs perfectly, adds relevant line to BOOT.INI etc but when I reboot I get the following...

[FONT="Courier New"]Try hd(0,0): NTSF5: 1
Try hd(0,1): invalid or null
Try hd(0,2): invalid or null
Try hd(0,3): invalid or null
Cannot find GRLDR in all devices. Press Ctrl+Alt+Del to restart.[/FONT]

Now I know there are no other partitions on the HD (only one C: partition) and from experimenting with an attached floppy that GRLDR seems to expect to find grldr, menu.lst etc on the other (non-existent) partitions.

When I run partinfw.exe (from Terabyte Unlimited) it gives the following information...

[FONT="Courier New"]PARTINFW 1.10
Copyright (c) 1996-2006 TeraByte, Inc.  All rights reserved.

Run date: 11/12/2007 18:59

====================================================================
           MBR Partition Information (HD0 - 0xE03BDF2E)
                         (CHS: 1023/254/63)
+====+====+=============+====+=============+===========+===========+
| 0: | 80 |    0   1  1 |  7 | 1023 254 63 |        63 |  23567292 |
| 1: |  0 |    0   0  0 |  0 |    0   0  0 |         0 |         0 |
| 2: |  0 |    0   0  0 |  0 |    0   0  0 |         0 |         0 |
| 3: |  0 |    0   0  0 |  0 |    0   0  0 |         0 |         0 |
+====+====+=============+====+=============+===========+===========+
                           BOOT SECTOR INFORMATION
-------------------------------------------------------------------------------
File System ID: 0x7   LBA: 63  Total Sectors: 23567292   ID: 0x1
                          Jump: EB 52 90
                      OEM Name: NTFS    
                 Bytes Per Sec: 512
                 Sec Per Clust: 8
                   Res Sectors: 0
                        Zero 1: 0x0
                        Zero 2: 0x0
                          NA 1: 0x0
                         Media: 0xF8
                        Zero 3: 0x0
                 Sec Per Track: 63
                         Heads: 255
                   Hidden Secs: 63
                          NA 2: 0x0
                          NA 3: 0x800080
                 Total Sectors: 0x01679BBB
                       MFT LCN: 0x04
                  MFT Mirr LCN: 0x0CAF80
                 Clust Per FRS: 0x1
              Clust Per IBlock: 0x1
                     Volume SN: 0xF1AB01FB5ECD8E9
                      Checksum: 0x0
                     Boot Flag: 0xAA55
-------------------------------------------------------------------------------
[/FONT]

This seems to imply that there are four partitions in the MBR, my C: partition and three 'phantom' partitions.

Do you think this is the root of my problems?

Is there a way to sort out the MBR so GRLDR see only one partition?

Am I completely on the wrong track?

Any help would be extremely appreciated as this is cracking me up and I really want Xubuntu on the laptop.

Thanks in advance

---

### Post by tuxcantfly on 2007-11-12
> **ido370 said:**
> i just downloaded the installer for archlinux (i386, where's the i686?), but after installing packages and configuring the system and network, i did not install a bootloader, since i thought the LUBI installer would take care of that after the installation, so after i finished everything i rebooted bu i only get the vista bootloader with two unetbootin-archlinuxrev7 entries and they both start the archlinux installer again. what am i doing wrong?

You'll need to install a bootloader. The bootloader used by UNetbootin is only used on a temporary basis, to launch the installer (and is removed on the next reboot); you'll need GRUB to actually boot the Linux distro.

> Would this method create an automatic dual boot? I was going to burn a copy of Ubuntu Studio and create a partition for my brothers laptop to dual boot but if I understand right, this method is just lke a cd? So when i am installing i will get the prompt for partitioning/ offereing me the option to dual boot?

Yes, the partitioner will pop up and you can set up a dual-boot.

---

### Post by tuxcantfly on 2007-11-12
> **Grimly Fiendish said:**
> Hi All,

I know this error has appeared previously in this thread (and others) but I think my situation might be different...

I'm trying to use UNetbootin (and have also have Wubi) to install Xubuntu on an old Dell Latitude (CPi 300) with a clapped-out CD drive. 
The laptop is running Windows 2000 Professional on a single partitioned 12Gb HD.

UNetbootin runs/installs perfectly, adds relevant line to BOOT.INI etc but when I reboot I get the following...

[FONT="Courier New"]Try hd(0,0): NTSF5: 1
Try hd(0,1): invalid or null
Try hd(0,2): invalid or null
Try hd(0,3): invalid or null
Cannot find GRLDR in all devices. Press Ctrl+Alt+Del to restart.[/FONT]

Now I know there are no other partitions on the HD (only one C: partition) and from experimenting with an attached floppy that GRLDR seems to expect to find grldr, menu.lst etc on the other (non-existent) partitions.

When I run partinfw.exe (from Terabyte Unlimited) it gives the following information...

[FONT="Courier New"]PARTINFW 1.10
Copyright (c) 1996-2006 TeraByte, Inc.  All rights reserved.

Run date: 11/12/2007 18:59

====================================================================
           MBR Partition Information (HD0 - 0xE03BDF2E)
                         (CHS: 1023/254/63)
+====+====+=============+====+=============+===========+===========+
| 0: | 80 |    0   1  1 |  7 | 1023 254 63 |        63 |  23567292 |
| 1: |  0 |    0   0  0 |  0 |    0   0  0 |         0 |         0 |
| 2: |  0 |    0   0  0 |  0 |    0   0  0 |         0 |         0 |
| 3: |  0 |    0   0  0 |  0 |    0   0  0 |         0 |         0 |
+====+====+=============+====+=============+===========+===========+
                           BOOT SECTOR INFORMATION
-------------------------------------------------------------------------------
File System ID: 0x7   LBA: 63  Total Sectors: 23567292   ID: 0x1
                          Jump: EB 52 90
                      OEM Name: NTFS    
                 Bytes Per Sec: 512
                 Sec Per Clust: 8
                   Res Sectors: 0
                        Zero 1: 0x0
                        Zero 2: 0x0
                          NA 1: 0x0
                         Media: 0xF8
                        Zero 3: 0x0
                 Sec Per Track: 63
                         Heads: 255
                   Hidden Secs: 63
                          NA 2: 0x0
                          NA 3: 0x800080
                 Total Sectors: 0x01679BBB
                       MFT LCN: 0x04
                  MFT Mirr LCN: 0x0CAF80
                 Clust Per FRS: 0x1
              Clust Per IBlock: 0x1
                     Volume SN: 0xF1AB01FB5ECD8E9
                      Checksum: 0x0
                     Boot Flag: 0xAA55
-------------------------------------------------------------------------------
[/FONT]

This seems to imply that there are four partitions in the MBR, my C: partition and three 'phantom' partitions.

Do you think this is the root of my problems?

Is there a way to sort out the MBR so GRLDR see only one partition?

Am I completely on the wrong track?

Any help would be extremely appreciated as this is cracking me up and I really want Xubuntu on the laptop.

Thanks in advance

I would open Windows' disk manager (diskmgmt.msc); that should let you see the 3 other strange volumes, and just delete them if there's nothing important in them. Perhaps also create a FAT32 partition in the freed space and copy over C:\grldr, grldr.mbr, and menu.lst following UNetbootin installation but prior to reboot; that might also help.

Also, maybe try a "chkdsk /r" to fix anything wrong on your partitions, and defragment your disks.

---

### Post by Grimly Fiendish on 2007-11-12
> **tuxcantfly said:**
> I would open Windows' disk manager (diskmgmt.msc); that should let you see the 3 other strange volumes, and just delete them if there's nothing important in them. Perhaps also create a FAT32 partition in the freed space and copy over C:\grldr, grldr.mbr, and menu.lst following UNetbootin installation but prior to reboot; that might also help.

Also, maybe try a "chkdsk /r" to fix anything wrong on your partitions, and defragment your disks.

Thank you so much for the speedy reply!

The thing is though, that these 'phantom' partitions don't show up in DOS/Explorer or the disk manager MSC - all these seem to think there's just one big contiguous C: partition.

It's only GRLDR (and partinfw.exe) that seems to think there's 4 partitions - the first primary/logical partition (hd0,0) and hd0,1, hd0,2 and hd0,3.

I think it might be a dodgy MBR, would you concur or do you think I'm on the wrong track?

btw, I'm curently running CHKDSK and defragging the drive...

Again, thanks for your help...

---

### Post by Grimly Fiendish on 2007-11-12
> **Grimly Fiendish said:**
> Thank you so much for the speedy reply!

The thing is though, that these 'phantom' partitions don't show up in DOS/Explorer or the disk manager MSC - all these seem to think there's just one big contiguous C: partition.

It's only GRLDR (and partinfw.exe) that seems to think there's 4 partitions - the first primary/logical partition (hd0,0) and hd0,1, hd0,2 and hd0,3.

I think it might be a dodgy MBR, would you concur or do you think I'm on the wrong track?

btw, I'm curently running CHKDSK and defragging the drive...

Again, thanks for your help...

Here's what I eventually did...

As per your advice, I created a small FAT32 partition (20 Mb!) and copied grldr, grldr.mbr and menu.lst to it.

But, crucially, I also copied the \unetbootin directory to the FAT32 partition.

On the next boot, grldr/grub/whatever it's called sprang into life and, as I type, the Ubuntu download/installation is progressing...

Hopefully, all will go well...

Either way, I'll post my experience...

Cheers

---

### Post by Grimly Fiendish on 2007-11-12
> **Grimly Fiendish said:**
> Here's what I eventually did...

As per your advice, I created a small FAT32 partition (20 Mb!) and copied grldr, grldr.mbr and menu.lst to it.

But, crucially, I also copied the \unetbootin directory to the FAT32 partition.

On the next boot, grldr/grub/whatever it's called sprang into life and, as I type, the Ubuntu download/installation is progressing...

Hopefully, all will go well...

Either way, I'll post my experience...

Cheers

Ok, after baby-sitting the installation for hours and all appeared to be going well...

Until, at the end, got this error saying didn't know where to install GRUB - No options semed to be acceptable or workable so selected 'finish installation'.

Laptop now bricked - 'Cannot find OS' or something and no way (as yet, anyway) of booting into machine.

I'm not complaining (I knew the risks) but, Jeez, this whole *ix stuff has a long way to go (someday, I'm sure it will get there).

I speak as a developer of long standing (MS/SQL Server/Oracle) so I'm not technically inept but this has been a dispiriting experience.

Anyway, anyone got any ideas as to how I might be able to resusicate apparently dead laptop (bearing in mind CD is kaput)?

Thanks

---

### Post by tuxcantfly on 2007-11-12
> **Grimly Fiendish said:**
> Ok, after baby-sitting the installation for hours and all appeared to be going well...

Until, at the end, got this error saying didn't know where to install GRUB - No options semed to be acceptable or workable so selected 'finish installation'.

Laptop now bricked - 'Cannot find OS' or something and no way (as yet, anyway) of booting into machine.

I'm not complaining (I knew the risks) but, Jeez, this whole *ix stuff has a long way to go (someday, I'm sure it will get there).

I speak as a developer of long standing (MS/SQL Server/Oracle) so I'm not technically inept but this has been a dispiriting experience.

Anyway, anyone got any ideas as to how I might be able to resusicate apparently dead laptop (bearing in mind CD is kaput)?

Thanks

Whoa, that doesn't sound good, seems like the GRUB configuration is screwed up (I suspect it has something to do with the awkward partition layout confusing GRUB), anyhow just re-install GRUB using the Super Grub Disk; see [http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download) for downloads; use either the floppy version or the USB flash drive version (you'll need access to another computer to write the image to a floppy or flash drive), then just change the boot order to boot from floppy/USB drive, then use the "repair GRUB" option on the Super Grub Disk (details at [http://supergrub.forjamari.linex.org/?section=documentation](http://supergrub.forjamari.linex.org/?section=documentation) ) and it should work then

---

### Post by Grimly Fiendish on 2007-11-13
> **tuxcantfly said:**
> Whoa, that doesn't sound good, seems like the GRUB configuration is screwed up (I suspect it has something to do with the awkward partition layout confusing GRUB), anyhow just re-install GRUB using the Super Grub Disk; see [http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download) for downloads; use either the floppy version or the USB flash drive version (you'll need access to another computer to write the image to a floppy or flash drive), then just change the boot order to boot from floppy/USB drive, then use the "repair GRUB" option on the Super Grub Disk (details at [http://supergrub.forjamari.linex.org/?section=documentation](http://supergrub.forjamari.linex.org/?section=documentation) ) and it should work then

Thanks (again!) for all your help, Tux...

I'll give the above a shot when I get home.

Here's hoping...

---

### Post by cacycleworks on 2007-11-21
Box is a P-4 HP e-PC that will not boot from CR-ROM and it doesn't have a floppy drive. Basically, a P4 laptop in a tiny desktop case. I tried all the stuff with loaders, smb this, and all that. Nope. Tried the USB boot that I *have* had work on some Dells we have. Nope. Ended up bricking it with "No OS" like above. 

But I banged on the enter key and it gave me a clue:
```
Client MAC ADDR: 00 04 23 14 0C 7E GUID: AC388561-F52C-11D5-AD37-44DEC94FC43E
PXE-E53 : No boot filename received

PXE-M05 : Exiting Intel PXE ROM

```

Turns out, it's ethernet card supports PXE. I had zero experience before this...

New to install ubuntu box is mentioned above. The "PXE host" from which all commands below I just coped is a Dell C521 AMD Athlon on the same simple "home network" running kubuntu gutsy amd64. Network is hanging off of one of the high speed 4 port wireless routers (with DHCP running on it!). My net is 192.168.2.x, with netmask 255.255.255.0. I formerly made the wireless router assign DHCP from 192.168.2.100 to 192.168.2.120. And I have some static IP's hanging out in the 192.168.2.40~192.168.2.59 range, so you see I set the DHCP range away from potential conflicts. Router is on 192.168.2.1

#  [http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install)
# Awesome reference, I didn't need much of it. but it did tell me about:
```
 /etc/default/tftpd-hpa: RUN_DAEMON="yes"
```

# 
# The 2 refs that really got me solved:
# [http://mywheel.net/blog/index.php/ubuntu-network-install/](http://mywheel.net/blog/index.php/ubuntu-network-install/)
# [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch16_:_Telnet,_TFTP,_and_xinetd#Configuring_The_TFTP_Server](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch16_:_Telnet,_TFTP,_and_xinetd#Configuring_The_TFTP_Server)
# 
# 
# actual commands that worked copied from my terminal with explanations behind # and output shown too:
# -------------------------------------------------------

$ wget [http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.10/release/xubuntu-7.10-alternate-i386.iso](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.10/release/xubuntu-7.10-alternate-i386.iso)

~# apt-get install tftpd-hpa dhcp3-server
[COLOR="DarkSlateGray"]Setting up dhcp3-server (3.0.5-3ubuntu4) ...
Generating /etc/default/dhcp3-server...
 * Starting DHCP server dhcpd3                                                         [fail]
invoke-rc.d: initscript dhcp3-server, action "start" failed.

[/COLOR]~# cd /var/lib/tftpboot
/var/lib/tftpboot# mkdir ubuntu
/var/lib/tftpboot# cp /home/chris/xubuntu-7.10-alternate-i386.iso .
/var/lib/tftpboot# mount -o loop /var/lib/tftpboot/xubuntu-7.10-alternate-i386.iso /var/lib/tftpboot/ubuntu
/var/lib/tftpboot# cd /var/www
/var/www# ln -s /var/lib/tftpboot/ubuntu/
/var/www# ls
[COLOR="DarkSlateGray"]apache2-default  ubuntu
[/COLOR]
/var/www# vi /etc/dhcp3/dhcpd.conf
# edited to make only the lines shown below uncommented...
/etc# cat dhcp3/dhcpd.conf
ddns-update-style none;

default-lease-time 600;
max-lease-time 7200;

# from [http://mywheel.net/blog/index.php/ubuntu-network-install/](http://mywheel.net/blog/index.php/ubuntu-network-install/)
ping-check = 1;
filename = "ubuntu/install/netboot/pxelinux.0";
subnet 192.168.2.0
netmask 255.255.255.0 {
range 192.168.2.20 192.168.2.24;
}



/var/www# /etc/init.d/dhcp3-server restart
[COLOR="DarkSlateGray"] * Stopping DHCP server dhcpd3                                                         [fail]
 * Starting DHCP server dhcpd3                                                         [ OK ]
[/COLOR]
# tried starting the computer and it dhcp'd but did a PXE-E32: TFTP open timeout.

/var/www# cd ../log
/var/log# tail syslog
[COLOR="DarkSlateGray"]Nov 20 21:34:13 cu1 dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov 20 21:34:13 cu1 dhcpd: Internet Systems Consortium DHCP Server V3.0.5
Nov 20 21:34:13 cu1 dhcpd: Copyright 2004-2006 Internet Systems Consortium.
Nov 20 21:34:13 cu1 dhcpd: All rights reserved.
Nov 20 21:34:13 cu1 dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov 20 21:34:13 cu1 dhcpd: Wrote 0 leases to leases file.
Nov 20 21:35:33 cu1 dhcpd: DHCPDISCOVER from 00:04:23:14:0c:7e via eth0
Nov 20 21:35:34 cu1 dhcpd: DHCPOFFER on 192.168.2.24 to 00:04:23:14:0c:7e via eth0
Nov 20 21:35:35 cu1 dhcpd: DHCPREQUEST for 192.168.2.24 (192.168.2.50) from 00:04:23:14:0c:7e via eth0
Nov 20 21:35:35 cu1 dhcpd: DHCPACK on 192.168.2.24 to 00:04:23:14:0c:7e via eth0[/COLOR]

#  OK- so dhcp is working ... maybe there is a conf for tftp...?

/var/log# apt-get install tftp-hpa
/var/log# cd /etc/
/etc# find . -name "*tftp*"
[COLOR="DarkSlateGray"]./rc4.d/S20tftpd-hpa
./default/tftpd-hpa
./rc1.d/K20tftpd-hpa
./rc3.d/S20tftpd-hpa
./init.d/tftpd-hpa
./rc2.d/S20tftpd-hpa
./rc5.d/S20tftpd-hpa
/etc# cd default/
[/COLOR]/etc/default# vi tftpd-hpa

/etc# cat default/tftpd-hpa
#... changed "no" to "yes"
RUN_DAEMON="yes"
OPTIONS="-l -s /var/lib/tftpboot"
/etc#



/etc/default# cd /var/lib/tftpboot/
/var/lib/tftpboot# ls
[COLOR="DarkSlateGray"]ubuntu  xubuntu-7.10-alternate-i386.iso[/COLOR]

/etc/default# /etc/init.d/tftpd-hpa start
[COLOR="DarkSlateGray"]Starting HPA's tftpd: in.tftpd.[/COLOR]
/etc/default# netstat -a | grep tftp
[COLOR="DarkSlateGray"]udp        0      0 *:tftp                  *:*[/COLOR]

# Did reboot and it immediately started into the installer!! But then
# it tried to configure network off of my temporary dhcp server, so I
# had to select <Go Back> a bunch of times until I go the retry Auto Network
# configure option...

/etc/default# /etc/init.d/dhcp3-server stop
[COLOR="DarkSlateGray"] * Stopping DHCP server dhcpd3                                                         [ OK ][/COLOR]

# and now the installer configured via normal dhcp server and all started
# well.
# 
# if you get the freeze after the task select stage of the install, go away
# and come back in an hour. Seems that's what it might take.
# [https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/62986](https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/62986)
# 
# Now to make it so this "server" doesn't start serving dhcp and tftp 
# at reboot by removing the init.d start up scripts. I didn't apt-get remove
# because I assumed it wouldn't work and I'd need to do it again...

/etc# find . -name "*S*dhcp*"
[COLOR="DarkSlateGray"]./rc4.d/S40dhcp3-server
./rc3.d/S40dhcp3-server
./rc2.d/S40dhcp3-server
./rc5.d/S40dhcp3-server[/COLOR]

[B][COLOR="Red"]# Find is a powerful command TEST it in a safe place as
# a plain user before experimenting!! Notice I checked the 
# output above before executing the xargs rm below![/COLOR][/B]

/etc# find . -name "*S*dhcp*" -print0 | xargs -0 rm
/etc# find . -name "*S*dhcp*"

# double check what is left...

/etc# find . -name "*dhcp*"
[COLOR="DarkSlateGray"]./dhcp3
./dhcp3/dhcpd.conf
./default/dhcp3-server
./rc1.d/K40dhcp3-server
./init.d/dhcp3-server
./acpi/suspend.d/65-dhcpd-stop.sh
./acpi/resume.d/69-dhcpd-start.sh
[/COLOR]

# missed one... let's remove it now.

/etc# rm acpi/resume.d/69-dhcpd-start.sh
/etc# 

# repeat for tftp, as I do not need that service...

/etc# find . -name "*tftp*"
[COLOR="DarkSlateGray"]./rc4.d/S20tftpd-hpa
./default/tftpd-hpa
./rc1.d/K20tftpd-hpa
./rc3.d/S20tftpd-hpa
./init.d/tftpd-hpa
./rc2.d/S20tftpd-hpa
./rc5.d/S20tftpd-hpa[/COLOR]
/etc# find . -name "*S*tftp*"  -print0 | xargs -0 rm
/etc# find . -name "*S*tftp*"

# verify:

/etc# find . -name "*tftp*"
[COLOR="DarkSlateGray"]./default/tftpd-hpa
./rc1.d/K20tftpd-hpa
./init.d/tftpd-hpa
[/COLOR]/etc#

# Now that it worked and my little box is finally booting and installing:
# Find the ISO mounted and unmount it

/etc# mount
[COLOR="DarkSlateGray"]. (other mounts omitted)
.
/var/lib/tftpboot/xubuntu-7.10-alternate-i386.iso on /var/lib/tftpboot/ubuntu type iso9660 (rw,loop=/dev/loop0)[/COLOR]
/etc# umount /var/lib/tftpboot/ubuntu

# so now if I need to do this again, I just start up dhcpd and tftpd and then mount the ISO
# again.  

:)

---

### Post by cacycleworks on 2007-11-21
oh, yeah, the e-pc was running windows 2000, which seemed particularly resistant to my efforts of installing a boot loader. I tried grub4dos and some other one, too, that claimed to be able to boot to HD then load CD. It couldn't install over grub. :P All that muckering about took twice as long as the PXE install did tonight. Of course, it didn't help having to boot to win2k all those times!!

:)

---

### Post by zivley on 2007-11-21
> **cacycleworks said:**
> # Now to make it so this "server" doesn't start serving dhcp and tftp 
# at reboot by removing the init.d start up scripts. I didn't apt-get remove
# because I assumed it wouldn't work and I'd need to do it again...

/etc# find . -name "*S*dhcp*"
[COLOR="DarkSlateGray"]./rc4.d/S40dhcp3-server
./rc3.d/S40dhcp3-server
./rc2.d/S40dhcp3-server
./rc5.d/S40dhcp3-server[/COLOR]

[B][COLOR="Red"]# Find is a powerful command TEST it in a safe place as
# a plain user before experimenting!! Notice I checked the 
# output above before executing the xargs rm below![/COLOR][/B]

/etc# find . -name "*S*dhcp*" -print0 | xargs -0 rm
/etc# find . -name "*S*dhcp*"

# double check what is left...

/etc# find . -name "*dhcp*"
[COLOR="DarkSlateGray"]./dhcp3
./dhcp3/dhcpd.conf
./default/dhcp3-server
./rc1.d/K40dhcp3-server
./init.d/dhcp3-server
./acpi/suspend.d/65-dhcpd-stop.sh
./acpi/resume.d/69-dhcpd-start.sh
[/COLOR]

# missed one... let's remove it now.

/etc# rm acpi/resume.d/69-dhcpd-start.sh
/etc# 

# repeat for tftp, as I do not need that service...

/etc# find . -name "*tftp*"
[COLOR="DarkSlateGray"]./rc4.d/S20tftpd-hpa
./default/tftpd-hpa
./rc1.d/K20tftpd-hpa
./rc3.d/S20tftpd-hpa
./init.d/tftpd-hpa
./rc2.d/S20tftpd-hpa
./rc5.d/S20tftpd-hpa[/COLOR]
/etc# find . -name "*S*tftp*"  -print0 | xargs -0 rm
/etc# find . -name "*S*tftp*"

# verify:

/etc# find . -name "*tftp*"
[COLOR="DarkSlateGray"]./default/tftpd-hpa
./rc1.d/K20tftpd-hpa
./init.d/tftpd-hpa
[/COLOR]/etc#




Nice guide indeed! A life saver.
Let me just tell you there's an easier way to remove init scripts.
All you need is to get into /etc/init.d/ and see what is the exact name of the service you want to disable at boot.
Then you use update-rc.d program (it adds or remove init scripts to the different run levels)
For example, to remove the dhcp server you need something like this:
```

update-rc.d dhcp3-server remove

```

Simple, isn't it?
Read the update-rc.d help for more options on how to use
Cheers,
Ziv

---

### Post by cacycleworks on 2007-11-21
> **zivley said:**
> Nice guide indeed! A life saver.

Then you use update-rc.d program (it adds or remove init scripts to the different run levels)
For example, to remove the dhcp server you need something like this:
```

update-rc.d dhcp3-server remove

```
Cheers,
Ziv

Thanks!! That is so added to my "useful_cli.txt" file! (and to my copy of the how-to)

---

### Post by the bogs on 2007-11-22
i have an old Toshiba Portege laptop with W98 on it. no option to boot from cd or usb in bios.

I have tried using unetbootin as described.

Problem is that i do not even get the boot up screen and the pc boots straight into w98. What can i do?

---

### Post by Grimly Fiendish on 2007-11-22
> **tuxcantfly said:**
> Whoa, that doesn't sound good, seems like the GRUB configuration is screwed up (I suspect it has something to do with the awkward partition layout confusing GRUB), anyhow just re-install GRUB using the Super Grub Disk; see [http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download) for downloads; use either the floppy version or the USB flash drive version (you'll need access to another computer to write the image to a floppy or flash drive), then just change the boot order to boot from floppy/USB drive, then use the "repair GRUB" option on the Super Grub Disk (details at [http://supergrub.forjamari.linex.org/?section=documentation](http://supergrub.forjamari.linex.org/?section=documentation) ) and it should work then

Ok, here's what eventually worked for me...

Bear in mind that my starting position was a laptop with unreliable CD drive, working floppy drive and a network connection.

I downloaded the Debian install floppies images from here... [http://ftp.nl.debian.org/debian/dists/etch/main/installer-i386/current/images/floppy/](http://ftp.nl.debian.org/debian/dists/etch/main/installer-i386/current/images/floppy/)

I downloaded boot.img, root.img, net-drivers-1.img and net-drivers-2.img and wrote these images to floppy using rawwritewin.exe (easily available online).

The floppy based installation recognised my (rather esoteric PCMCIA) network card and I was easily able to complete a network/internet based full Debian installation.

I then downloaded and installed the relevant UNetbootin package (Xubuntu under Debian) and rebooted.

UNetbootin worked perfectly! 

I was able to perform the network/internet install of Xununtu - Mission accomplished!

One caveat, if you're in Ireland don't use the Irish mirror use a UK mirror for the install.

Great work by tuxcantfly...

---

### Post by tuxcantfly on 2007-12-03
I've added UNetbootin builds for the newly-released CentOS 5.1

Downloads are available at the usual spot at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

If installing CentOS, select "FTP" as the installation source, and for the server, specify:

    ```
mirrors.kernel.org
```

and for the folder, if using the standard (32-bit) version, specify:

    ```
centos/5.1/os/i386
```

or if using the 64-bit version, specify:

    ```
centos/5.1/os/x86_64
```

There is also a screenshot-based guide at [http://bashcurescancer.com/rhel-50-centos-ftp-install-gui-mode.html](http://bashcurescancer.com/rhel-50-centos-ftp-install-gui-mode.html)

In case you haven't heard of CentOS, it's basically a free, rebranded version of Red Hat Enterprise Linux. Though it isn't quite cutting-edge, CentOS 5.1 is fully compatible with RHEL 5 Update 1, and it's also extremely stable.

---

### Post by quypham007 on 2007-12-16
Thanks for adding CentOS 5.1 in!!!!  Ubuntu based Linux may be known well here, CentOS rules the SMB and Corporate sectors I work in because it IS Red Hat MINUS the logos.  Same exact RPMS, built from same RPMS, etc - just logos changed.  It is very nice also.  I basically use it because it IS what pays the bills - Microsoft and Red Hat contract work I do pays the bills :)

Tuxcantfly - excellent work and options you have provided the community with your useful tool.  Any possibility is having a freedos version or even DOS (for machines with no OS) - I know "noone" may be using DOS/FreeDOS anymore, but what if someone does not want to install Debian (due to the longer more elaboarate install process) just so they can install UNETBOOTIN.  With DOS based install - it just format /s on the C: drive.  And then just copy a DOS/FreeDOS version of UNETBOOTIN over the C: drive and execute, reboot, and voila (so much faster than Debian install)...to your chosen Liunux distro ready for installation...just an idea.  Better yet, an option to install/execute from a Linux based LiveCD - that would be even better.  Thanks again!

---

### Post by tuxcantfly on 2007-12-17
> **quypham007 said:**
> Thanks for adding CentOS 5.1 in!!!!  Ubuntu based Linux may be known well here, CentOS rules the SMB and Corporate sectors I work in because it IS Red Hat MINUS the logos.  Same exact RPMS, built from same RPMS, etc - just logos changed.  It is very nice also.  I basically use it because it IS what pays the bills - Microsoft and Red Hat contract work I do pays the bills :)

Tuxcantfly - excellent work and options you have provided the community with your useful tool.  Any possibility is having a freedos version or even DOS (for machines with no OS) - I know "noone" may be using DOS/FreeDOS anymore, but what if someone does not want to install Debian (due to the longer more elaboarate install process) just so they can install UNETBOOTIN.  With DOS based install - it just format /s on the C: drive.  And then just copy a DOS/FreeDOS version of UNETBOOTIN over the C: drive and execute, reboot, and voila (so much faster than Debian install)...to your chosen Liunux distro ready for installation...just an idea.  Better yet, an option to install/execute from a Linux based LiveCD - that would be even better.  Thanks again!

Sorry, don't have access to DOS at the moment (nor do I know anything about its bootloader), but if all you want to do is initiate a Linux install starting from DOS, try loadlin.exe (it lets you load the LILO bootloader, which in turn can load the kernel and initrd for the netboot kernel and initrd for installation), or if you prefer GRUB over LILO, supposedly "grub.exe" from the GRUB4DOS package can do the same thing; just copy over the menu.lst, kernel, and initrd from UNetbootin, and load them with grub.exe from DOS.

---

### Post by zivley on 2007-12-18
Hey tuxcanfly, yesterday I sucessfully installed CentOS with your program.
I only had a little problem with the grub, I installed it on an old RedHat and it complained about not finding the root on the hardisk (hd01-1) or something like that, I edited the grub command to be right for the PC, it was (hd1,1) and then it booted to the unetbootin, and again complained about the same problem, so I fixed again the grub command and then all started well and I completed the installation sucessfully.
I think you need to check that one.
But anyway, a minor problem, I managed to overcome, your piece of software is awesome, it saves me the distro download time and the CD burning, and also very useful for computers with no CD.
Thanks a lot!

---

### Post by Ayrs on 2007-12-18
I just tried installing Ubuntu using this method I think everything went like it was suppose to, however, whenever I launch Ubuntu there is no GUI and it's all DOS Prompt style.   Sorry I'm a newb to Linux so I'm sure there is something wrong on my part.  Help would be appreciated!  Thanks.

---

### Post by tuxcantfly on 2007-12-18
> **zivley said:**
> Hey tuxcanfly, yesterday I sucessfully installed CentOS with your program.
I only had a little problem with the grub, I installed it on an old RedHat and it complained about not finding the root on the hardisk (hd01-1) or something like that, I edited the grub command to be right for the PC, it was (hd1,1) and then it booted to the unetbootin, and again complained about the same problem, so I fixed again the grub command and then all started well and I completed the installation sucessfully.
I think you need to check that one.
But anyway, a minor problem, I managed to overcome, your piece of software is awesome, it saves me the distro download time and the CD burning, and also very useful for computers with no CD.
Thanks a lot!

It probably has to do with changes in the syntax of the "sed" command since the older versions included in old Red Hat releases, so I'm afraid I can't fix it to work on older releases without introducing incompatibility issues with certain newer sed versions, or introducing additional dependencies on something like perl or python to do the stream editing (which will in turn lead to the same problem of some distros having different versions or not bundling the tool at all).

Also, what Redhat version is this (It worked fine when I tested on an old Fedora Core install, which should theoretically be similar to the original Redhat), and are you using a specialized partition layout (are you using a dedicated /boot)? Partition layout might also be contributing to the issue.

> I just tried installing Ubuntu using this method I think everything went like it was suppose to, however, whenever I launch Ubuntu there is no GUI and it's all DOS Prompt style. Sorry I'm a newb to Linux so I'm sure there is something wrong on my part. Help would be appreciated! Thanks.

I think you forgot to mark one of the desktop packages (highlight and press space) when you were installing (they need to show up as marked, with an asterisk next to them, before you press enter). Since you've already installed the system, though, just login and enter the following commands (enter your password when prompted) to download and install the GUI desktop package:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

Then reboot and it should boot into a nice GUI. Replace "ubuntu-desktop" with "xubuntu-desktop" if installing Xubuntu, same procedure with the other Ubuntu variants.

---

### Post by tuxcantfly on 2007-12-24
Happy holidays folks, nothing like cranking out shell scripts and tinkering with MBRs over winter break... anyhow...

I've released a new version of UNetbootin, shell-script (.sh) version, now with 2 oft-requested features:

1. Ability to install from a liveCD or other live-media (liveUSB) install, as well as the ability to specify a target partition and (optionally) grub or lilo as the bootloader (this is the installmode=nohost option)
2. Ability to install to a USB drive in order to create a bootable-USB-netboot installer (this is the installmode=usbdrive option)

As for the original behavior (chainload from the host hard-drive grub installation), that can be accessed through the installmode=tohost option.

Anyhow, here's the syntax and options for running (This example is for Fedora 8, but I've also uploaded the new .sh builds for Ubuntu 7.10, openSUSE 10.3, Debian 4.0, CentOS 5.1, Arch Linux, Mandriva 2008, and Slackware 12.0):

[B]
If you are running this script from a host, hard-drive Linux install, and want the GRUB bootloader installed in /boot to be used, enter:[/B]

```
./unetbootin-fedora8rev49.sh installmode=tohost
```


**Otherwise, if you are running this script from a liveCD or other live, non-hard drive media, or the installmode=tohost option fails, or you want to specify your target partition (targetpartition=/dev/sda1) or (optionally) the bootloader (bootloader=grub or bootloader=lilo), enter, in addition to the targetpartition and formatpartition options:**

```
./unetbootin-fedora8rev49.sh installmode=nohost targetpartition=/dev/sda1 formatpartition=yes
```


**Otherwise, if you want to install to a USB drive, enter, in addition to the targetpartition and formatpartition options:**

```
./unetbootin-fedora8rev49.sh installmode=usbdrive targetpartition=/dev/sda1 formatpartition=yes

```

Ususal download spot at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

---

### Post by tuxcantfly on 2007-12-29
Also, just added a version for booting FreeDOS, for running those pesky DOS-only recovery and bios-flashing tools some OEMs ship on computers.

Usual download location at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

---

### Post by Eric Weir on 2008-01-02
> **tuxcantfly said:**
> It works the same way as the standard netboot install does, only without any cds needed, so if netboot works, this will work fine too. After install, you'll just have a plain ubuntu install.

I think this is what I need/want. I jut have one question: Will I end up with a dual-boot machine, i.e., able to to run either Windows or Ubuntu? 

If so, I'd rather have a pure Ubtuntu machine. Is that possible?

Thanks,

---

### Post by tuxcantfly on 2008-01-02
> **Eric Weir said:**
> I think this is what I need/want. I jut have one question: Will I end up with a dual-boot machine, i.e., able to to run either Windows or Ubuntu?

If so, I'd rather have a pure Ubtuntu machine. Is that possible?

Thanks,

Yes, it's possible to just have a pure Ubuntu machine; if you select the "resize partitions and install Ubuntu in free space" option at the partitioning stage you'll end up with a dual-boot install, and if you select the "erase all partitions" option you'll end up with pure Ubuntu.

---

### Post by Eric Weir on 2008-01-02
> **tuxcantfly said:**
> Yes, it's possible to just have a pure Ubuntu machine; if you select the "resize partitions and install Ubuntu in free space" option at the partitioning stage you'll end up with a dual-boot install, and if you select the "erase all partitions" option you'll end up with pure Ubuntu.

Good, that's what I want.

Another question, that perhaps should be posted under another subject heading. I did not do the install on my first Ubuntu system. I've heard it recommended that you have separate partitions for the operating system and your documents -- or maybe it's your home folder -- especially since the practice of "mounting" renders the partioning transparent as far as the user is concerned. 

I'm assuming, if the above is right, that the patitioning process is pretty straightforward. On a 40 GB hard drive, would a 10/30 GB division be adequate? [Almost all my files are text files. Almost none are graphic.]

One poster to the orginal thread recommended having your "IP address-gateway-dns server info" ready when you start the installation process. I take it the addresses under the Windows installation will be retained in the Unbuntu installation?

Thanks for your prompt response.

Sincerely,

---

### Post by tuxcantfly on 2008-01-02
> **Eric Weir said:**
> Good, that's what I want.

Another question, that perhaps should be posted under another subject heading. I did not do the install on my first Ubuntu system. I've heard it recommended that you have separate partitions for the operating system and your documents -- or maybe it's your home folder -- especially since the practice of "mounting" renders the partioning transparent as far as the user is concerned. 

I'm assuming, if the above is right, that the patitioning process is pretty straightforward. On a 40 GB hard drive, would a 10/30 GB division be adequate? [Almost all my files are text files. Almost none are graphic.]

The way I usually do it is keep 8GB for system (/) and the rest for documents (/home). You won't need any more than 8 unless you're installing multiple desktop environments (full ubuntu system install is just 3.5GB), so 8/32 is how I'd go

> 
One poster to the orginal thread recommended having your "IP address-gateway-dns server info" ready when you start the installation process. I take it the addresses under the Windows installation will be retained in the Unbuntu installation?

Thanks for your prompt response.

Sincerely,

You only need IP address/gateway/dns server info if you're on a static connection. No, they won't be retained from Windows, you'll need to jot down the info if you have a static address and input it when prompted (since the downloading and installing portion occurs while outside of Windows, so the Windows registry/info isn't accessible)

---

### Post by Eric Weir on 2008-01-02
> **tuxcantfly said:**
> ....You won't need any more than 8 unless you're installing multiple desktop environments (full ubuntu system install is just 3.5GB), so 8/32 is how I'd go.

You only need IP address/gateway/dns server info if you're on a static connection....

My IP address dynamic, so it looks like I'm in good shape. I just have to buy the machine!

Thanks again,

---

### Post by Eric Weir on 2008-01-02
> **Eric Weir said:**
> I just have to buy the machine!

Well, I did it. An IBM X40 Ultralight, 1.5 Ghz, 512 MB [for now], 40 GB. According to Thinkwiki, very hospitable to Ubuntu. 

Thanks again,

---

### Post by tuxcantfly on 2008-01-03
Just posted up new builds for the recently-released VectorLinux 5.9, download location at [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=256936](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=256936)

VectorLinux-specific guide located at [http://ubuntuforums.org/showthread.php?p=4062492](http://ubuntuforums.org/showthread.php?p=4062492)

---

### Post by Eric Weir on 2008-01-03
> **tuxcantfly said:**
> Just posted up new builds for the recently-released VectorLinux 5.9, download location at [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=256936](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=256936)


What's VectorLinux? Another distribution? Never heard of it.

---

### Post by tuxcantfly on 2008-01-03
> **Eric Weir said:**
> What's VectorLinux? Another distribution? Never heard of it.

VectorLinux is one of the older, slackware-based distros. Runs nice and fast on older computers. It just doesn't have the corporate backing nor huge user community of the likes of Ubuntu, Fedora, and openSUSE, which is probably why it isn't as popular. More info at website on [http://vectorlinux.com/](http://vectorlinux.com/) (PS that post was a general announcement, not specifically targetted towards anyone)

---

### Post by tuxcantfly on 2008-01-03
(General Announcement)

I've uploaded builds UNetbootin builds for Ubuntu 8.04 [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=256965](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=256965) and openSUSE Factory [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=256968](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=256968)

Ubuntu instructions are the same as before (install, reboot), while openSUSE factory instructions are as follow:

**openSUSE-Factory Instructions**

If installing openSUSE, after rebooting, ignore any error messages and select back if prompted for a CD, then go to the main menu, select the "Start Installation" option, choose "Network" as the source, choose "HTTP" as the protocol, and for the server, specify:

    ```
download.opensuse.org
```

and for the folder, if installing openSUSE Factory, specify:

    ```
distribution/SL-OSS-factory/inst-source/
```

Since both of these are experimental distributions, and thus frequently change, the UNetbootin builds will initiate the download of the latest builds of that distribution's netboot initrd and kernel files from the official mirrors rather than bundling them in. (Which is why the filesize is now down to a couple of kilobytes rather than several megabytes)

---

### Post by cacycleworks on 2008-01-06
> **tuxcantfly said:**
> VectorLinux is one of the older, slackware-based distros. Runs nice and fast on older computers. It just doesn't have the corporate backing nor huge user community of the likes of Ubuntu, Fedora, and openSUSE, which is probably why it isn't as popular. More info at website on [http://vectorlinux.com/](http://vectorlinux.com/) (PS that post was a general announcement, not specifically targetted towards anyone)

I installed it on a modern Sony Vaio laptop with core-duo 1.6 GHz CPU with lots or RAM and a 7200rpm hard drive. (it's a 32 bit cpu, not the newer 64 bit core-duo) From off to work-ready desktop was about 30 seconds. Add another minute for kubuntu on the same machine. Ultimately, I went with xubuntu on it. Slackware is different enough that I'm keeping all one OS -- I have too much actualy work to do without learning another linux at this moment. Definitely impressive, though.

:-) Chris 

btw- thanks a bunch for your work on UNetbootin! Next time I get one of these silly little computers, I'll go your route. I'm half tempted to try out CentOS someday.

---

### Post by bradley1980 on 2008-01-06
Hi tuxcantfly,

Can you to compile UNetbootin for Xubuntu and/or Fluxbuntu. I had trouble installing Xubuntu on my old laptop via live cd. It hanged during partitioning process. Could be I have insufficient ram or something is wrong with my cd-rom. 

Thanks.

Edit : Oops.. Got it. There is a post in here which says that Xubuntu can be install using the  UNetbootin for Ubuntu. Well, is it possible for you to compile the UNetbootin for Fluxbuntu :D

---

### Post by tuxcantfly on 2008-01-06
> **bradley1980 said:**
> Hi tuxcantfly,

Can you to compile UNetbootin for Xubuntu and/or Fluxbuntu. I had trouble installing Xubuntu on my old laptop via live cd. It hanged during partitioning process. Could be I have insufficient ram or something is wrong with my cd-rom. 

Thanks.

Edit : Oops.. Got it. There is a post in here which says that Xubuntu can be install using the  UNetbootin for Ubuntu. Well, is it possible for you to compile the UNetbootin for Fluxbuntu :D

Fluxubuntu, Geubuntu, Ubuntu Lite, Linux Mint, and the other non-official Ubuntu derivatives are all just the Ubuntu base system with a different desktop environment and a few extra packages tacked on. UNetbootin supports only the official Ubuntu versions (Ubuntu, Kubuntu, Xubuntu, Gobuntu, UbuntuStudio, and Ubuntu Server), since the other derivatives don't provide their own PXE/netboot initrd packages.

Attempting to maintain functioning 3rd-party PXE initrds would be extremely difficult, due to the constant changing of the respective distibutions; however, if you or anyone else finds working PXE/netboot initrds for these Ubuntu derivatives you want supported by UNetbootin (same goes for other distros), just post the links here and I'll have the UNetbootin builds ready as soon as possible.

However, you can still get the same outcome of installing fluxubuntu; just use the Ubuntu version to Install the base system (no desktops), then

```
 sudo apt-get install fluxbox
```

You can then proceed to install the other applications using the same approach, and you'll eventually end up with a Fluxubuntu desktop

---

### Post by allllec on 2008-01-07
I tried this just now, however it said it cannot find any network devices (i have a gigabit onboard network card) so clearly i need some kind of driver.

Is there anyway to load a driver ?



Cheers

Alec

---

### Post by tuxcantfly on 2008-01-07
> **allllec said:**
> I tried this just now, however it said it cannot find any network devices (i have a gigabit onboard network card) so clearly i need some kind of driver.

Is there anyway to load a driver ?



Cheers

Alec

What that means is that the ethernet card chipset isn't supported by the distribution you're attempting to install. Loading a driver on boot is (theoretically) possible by locating a functioning driver, compiling it, and modifying the initrd to use it by replacing the existing module in /lib/modules (google up "initrd customization" if interested, there are a few guides), but it's rather difficult and time-consuming, so I wouldn't recommend it unless you're a Linux expert.

I'd suggest trying out Fedora and openSUSE, and seeing if either of them support your network chipset out-of-the box. If you still have no luck there, you can just pre-download the install iso for Fedora/openSUSE while still in Windows to your hard drive (make sure you do the partitioning beforehand though, and download the iso to a different partition than the one you want to install to), and select "hard drive" as the installation source, to be able to install without a CD without needing to be connected to the internet (or alternatively you could just use the standard CD install process). Then again, in both situations after installation, you'll still be faced with the issue of locating, compiling, and installing the driver for the network card.

An easy way to avoid all this, though, is to see if you can salvage a standard PCI ethernet card from an older computer if you have a spare one, and use it on a temporary basis, since they tend to be better compatible with Linux than some newer chipsets.

---

### Post by bradley1980 on 2008-01-07
I encountered the driver issue as well but of a different sort. After the system performed the disk and hardware scan, i got this message:

No disk driver was detected. if you know the name of the driver needed by your disk drive, you can select it from the the list.

Driver needed for your disk drive:

continue with no disk
3w-9xxx
3w-xxxx
53c700
and the list goes on....

I tried to continue with no disk but got a warning message saying that there is no root drive. At the point i had to abort the installation.

Not sure whether my A: drive caused this. Win2k and XP cannot detect my A: drive but WinMe and Win98 can.

Is there a way to solve this problem?

Thanks

---

### Post by tuxcantfly on 2008-01-07
> **bradley1980 said:**
> I encountered the driver issue as well but of a different sort. After the system performed the disk and hardware scan, i got this message:

No disk driver was detected. if you know the name of the driver needed by your disk drive, you can select it from the the list.

Driver needed for your disk drive:

continue with no disk
3w-9xxx
3w-xxxx
53c700
and the list goes on....

I tried to continue with no disk but got a warning message saying that there is no root drive. At the point i had to abort the installation.

Not sure whether my A: drive caused this. Win2k and XP cannot detect my A: drive but WinMe and Win98 can.

Is there a way to solve this problem?

Thanks

I've never encountered that issue nor seen that error; sorry, can't help on that. Best solution, I'd say, is just to try a different distribution and see if it likes your disk better. Use whatever works well with your hardware; most of the major desktop distros (Ubuntu, Fedora, openSUSE) are pretty much the same anyhow from an average desktop user's perspective.

Anyhow, unfortunately, I'm not the right person to ask to solve these driver and hardware-specific issues. That's for upstream (the individual distro teams responsible for the kernel and drivers) to solve; perhaps just file a bug report for whatever distribution you had trouble with (if it's Ubuntu, see Launchpad.net, and remember to mention your hardware of course), they might be able to help you better (and of course, once they've been alerted to the issue, they'll hopefully be able to fix the issue by the next release, so other users of your hardware won't have issues).

Same goes for other general distribution-specific hardware issues. If there's an issue with the UNetbootin loader itself (basically the Windows and GRUB part, before the main installer itself starts), I'd be more than glad to help and will try to fix whatever the bug is, but for general issues on specific hardware, I can't help much since it's not my area of expertise; you'll get much better help with the problem by filing a bug report upstream so the teams working on the individual distros will be able to fix their bugs, and if you must, you can settle for using a different distro in the meantime.

---

### Post by Eric Weir on 2008-01-08
My IBM X40 arrived yesterday. Even though I've been using Ubuntu -- actually, Kubuntu -- pretty much exclusively since September, I almost hate to wipe out the XP install. It includes a full install of MS Office Professional. But I'm going to do it.

One more question -- well, maybe just one more: Instead of giving you an XP CD with this system, IBM has created a hidden partition from which it's possible possible to restore the OS if necessary.

As I said, I'm not looking to create a dual-boot system, but I wonder if it's possible to preserve this hidden partition while doing an Ubuntu-only install.

Thanks in advance,

---

### Post by tuxcantfly on 2008-01-08
> **Eric Weir said:**
> My IBM X40 arrived yesterday. Even though I've been using Ubuntu -- actually, Kubuntu -- pretty much exclusively since September, I almost hate to wipe out the XP install. It includes a full install of MS Office Professional. But I'm going to do it.

One more question -- well, maybe just one more: Instead of giving you an XP CD with this system, IBM has created a hidden partition from which it's possible possible to restore the OS if necessary.

As I said, I'm not looking to create a dual-boot system, but I wonder if it's possible to preserve this hidden partition while doing an Ubuntu-only install.

Thanks in advance,

Yes, but in that case make sure you do NOT use any of the "Guided Partitioning" options. Just use the "manual partitioning" option when you get to the partitioning stage, and delete every partition except the hidden one (it should be labeled as type W95 FAT32 Hidden, hex code 1c or 1d), then create the appropriate filesystem layout for Ubuntu (swap partition, / partition, and optionally a /home partition).

If Ubuntu's partitioner doesn't show the hidden partition, or you can't determine it's corresponding partition number, manually use GParted or fdisk (same procedure, delete all partitions except the hidden one) instead (PartedMagic, on the UNetbootin download page, will allow you to run GParted to do your partitioning without a CD).

---

### Post by Eric Weir on 2008-01-09
> **tuxcantfly said:**
> Yes, but in that case make sure you do NOT use any of the "Guided Partitioning" options. Just use the "manual partitioning" option when you get to the partitioning stage, and delete every partition except the hidden one (it should be labeled as type W95 FAT32 Hidden, hex code 1c or 1d), then create the appropriate filesystem layout for Ubuntu (swap partition, / partition, and optionally a /home partition)....

Thanks. Which raises still another question. [Hopefully these will end someday.] How much should I allow for a swap partition? 

The machine has 512 MB of RAM at this point, but I plan to add another 512 MB. Most of my work is text processing, web browsing, and email. There is little to no graphics processing.

---

### Post by tuxcantfly on 2008-01-09
> **Eric Weir said:**
> Thanks. Which raises still another question. [Hopefully these will end someday.] How much should I allow for a swap partition? 

The machine has 512 MB of RAM at this point, but I plan to add another 512 MB. Most of my work is text processing, web browsing, and email. There is little to no graphics processing.

Swap size should be equivalent or just slightly larger than the amount of RAM, so assuming the 1GB of RAM, you should have around 1024MB, or (slightly larger to allow for hibernation) approx. 1100MB.

PS: if the size of all these individual partitions is really bothering you, you can opt to just go for the LVM (Logical Volume Manager) option (80MB /boot, all the rest as LVM pool, within the LVM pool you can just define a /home, swap, and /, and just resize each when needed); that way you can safely change how much of the LVM pool goes to /, /home, and swap logical volumes on the go (basically the equivalent of resizing partitions), even without unmounting or rebooting, whenever you need more space on an individual logical volume (basically the LVM equivalent of a partition, only it resides within the LVM pool not the physical disk). I'm not sure about how good Ubuntu's support for it is (all I know is there's an option in the partitioner for LVM, never actually tried it), but Fedora 8 uses LVM by default and even provides a nice GUI for managing the volume groups; it worked well in my experience. More info at [http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29](http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29)

---

### Post by Eric Weir on 2008-01-09
> **tuxcantfly said:**
> Swap size should be equivalent or just slightly larger than the amount of RAM, so assuming the 1GB of RAM, you should have around 1024MB, or (slightly larger to allow for hibernation) approx. 1100MB.

Thanks.

> PS: if the size of all these individual partitions is really bothering you, you can opt to just go for the LVM (Logical Volume Manager) option (80MB /boot, all the rest as LVM pool, within the LVM pool you can just define a /home, swap, and /, and just resize each when needed)....No, I can't imagine that the size you suggested -- 8 GB /, 30+ GB /home -- wouldn't be adequate. 

I'm going to take a little time to make sure the machine is uptodate before installing Ubuntu. I understand an update to the BIOS is available, and I'd like to take care of that while I've still got XP. I'm new at this sort of thing, so I'll need to go slowly, make sure I understand instructions, etc.

I'm taking it when I'm ready I'll be able to install any of the Ubuntu flavors, which In my case will be Kubuntu.

Thanks again,

---

### Post by NoNameforMe on 2008-01-10
Hey folks, i've got a very strange problem o.O

Installation with UNetbootin worked perfectly, but i've got a problem to start Ubuntu (7.10)

When I choose Ubuntu in the Grub-boot loader it loads the driver, then stops an it expects Username and Password.

So I type in the Username I choosed while the installation and then I can't type in the password o.o

It looks like the keyboard isn't connect, it doesn't matter which key I press on my keyboard (I've tested all of 'em), it is impossible to type in my password an therefore impossible to start Ubuntu.

But Ctrl+Alt+Del for restart works fine...

What's the problem and do I fix it?

---

### Post by tuxcantfly on 2008-01-10
> **NoNameforMe said:**
> Hey folks, i've got a very strange problem o.O

Installation with UNetbootin worked perfectly, but i've got a problem to start Ubuntu (7.10)

When I choose Ubuntu in the Grub-boot loader it loads the driver, then stops an it expects Username and Password.

So I type in the Username I choosed while the installation and then I can't type in the password o.o

It looks like the keyboard isn't connect, it doesn't matter which key I press on my keyboard (I've tested all of 'em), it is impossible to type in my password an therefore impossible to start Ubuntu.

But Ctrl+Alt+Del for restart works fine...

What's the problem and do I fix it?

Are you attempting to login through the console (no GUI), or through GDM (the GUI login screen)? Correct me if I'm wrong, but from the sound of it, it seems like you forgot to select a desktop environment during installation (from post 1:If you're installing *Ubuntu, make sure to mark one or more desktop environment using the space button when asked by the installer, so that it's marked with an asterisk (*), or else you'll be left with a commandline-only environment.), and are attempting to login from the console. If it's through the console that you're attempting to login, the password is being entered in fine, you just don't see the characters themselves for security reasons. Just enter the password, hit enter, and it'll login fine.

Since you didn't select a desktop environment to install, you're going to have to install one after logging in to be able to use a GUI. Just enter the following commands:
```

sudo apt-get update
sudo apt-get install ubuntu-desktop
```

Then wait as the packages are installed, reboot, and all should work fine.

Since this isn't the first time users have encountered this problem of forgetting to select a desktop environment, I've updated the instructions in the first post and the website to have the instructions appear more noticeable

---

### Post by muginaa on 2008-01-11
For some reason the windows unetbootin installer does not work for my old laptop. It hangs after extracting menu.lst and never reboots. Anyway, I have now managed to install grub and have modified the boot.ini in such a way that I could basically run the installer. The problem is, that I can not find the necessary files,  i.e. ubnkern and ubuninit (?),  that need to be copied  to the c:\unetbootin directory to reboot th elaptop and start the actual installation? Could someone please tell me where to donload them or post them to this forum?

Thanks!

---

### Post by tuxcantfly on 2008-01-11
> **muginaa said:**
> For some reason the windows unetbootin installer does not work for my old laptop. It hangs after extracting menu.lst and never reboots. Anyway, I have now managed to install grub and have modified the boot.ini in such a way that I could basically run the installer. The problem is, that I can not find the necessary files,  i.e. ubnkern and ubuninit (?),  that need to be copied  to the c:\unetbootin directory to reboot th elaptop and start the actual installation? Could someone please tell me where to donload them or post them to this forum?

Thanks!

The files are on the FTP sites of the respective distributions (ftp.ubuntu.com, ftp.debian.org, etc), they're usually in a folder titled "ftp-install", "netboot", or something similar. Alternatively, you can just extract them from the .exe, .rpm, or .deb version using 7-zip [http://7-zip.org/](http://7-zip.org/) (rightclick->extract here)

Also, what version of Windows was this on? And what distro and version were you installing? (I want to see if I can reproduce this bug myself)

---

### Post by muginaa on 2008-01-11
Hello,

thanks, problem solved! The installation starts all right. All I need now is  to find the right vga= option for the display...

The laptop is (soon was) running windows 2000 professional and it's a travel mate 225X

Cheers!

---

### Post by muginaa on 2008-01-11
oops, forgot to say that the installer version was the latest ubuntu (and Vector). Before that I tried with wubi and that failed as well. I had the grub already installed when I started playing with wubi and unetbootin.

---

### Post by NoNameforMe on 2008-01-13
> **tuxcantfly said:**
> Are you attempting to login through the console (no GUI), or through GDM (the GUI login screen)? Correct me if I'm wrong, but from the sound of it, it seems like you forgot to select a desktop environment during installation (from post 1:If you're installing *Ubuntu, make sure to mark one or more desktop environment using the space button when asked by the installer, so that it's marked with an asterisk (*), or else you'll be left with a commandline-only environment.), and are attempting to login from the console. If it's through the console that you're attempting to login, the password is being entered in fine, you just don't see the characters themselves for security reasons. Just enter the password, hit enter, and it'll login fine.

Since you didn't select a desktop environment to install, you're going to have to install one after logging in to be able to use a GUI. Just enter the following commands:
```

sudo apt-get update
sudo apt-get install ubuntu-desktop
```

Then wait as the packages are installed, reboot, and all should work fine.[...]

omg, you're right ](*,)
Didn't noticed that while installation, was quite late and very tired -.-

I also thougt of this possibility that the password isn't shown, but alo noticed that I wrote my Username wrong... *.*

Thx for your help :)

---

### Post by dsigned on 2008-01-14
so...I went through the process, with a few hitches, but i thought it had completed successfully. However, after the computer rebooted, the only screen that would come up was "missing operating system."
Here are the hitches, in case that helps to address the issue:
- I did not have my Web server key, but it said "auto-detected succesfully", so i think that was ok.
- I got an error message when i tried to check too many boxes in the menu that lets you select the desktop. I tried multiple times, and eventually, when i selected only the ubuntu desktop (and nothing else), it went through
- I input 50% for the partition free space. It seemed as though the program would automatically partition the hard drive into a percentage, instead of me having to input a raw figure, but the hard drive is only 37G so if somehow it decided to format the entire drive, i suppose that could be the problem.
- i don't know if i can access the bios
Long story short, i would like to know if this is a fixable glitch, or if i need to
start figuring out how to reload OS's.

---

### Post by christiand88 on 2008-01-14
I am trying this automatically with unetbootin both 32bit and 64bit on my Lenovo X61.
Both times it will not recognize any disk drives. It gives me a list to choose from and none make sense, or work that i've tested. If i click just ignore it, it will goto the next screen to select/edit the partitions and it doesn't detect any media, or partitions at all.

Any clues?
Thanks
Christian

---

### Post by tuxcantfly on 2008-01-15
> **christiand88 said:**
> I am trying this automatically with unetbootin both 32bit and 64bit on my Lenovo X61.
Both times it will not recognize any disk drives. It gives me a list to choose from and none make sense, or work that i've tested. If i click just ignore it, it will goto the next screen to select/edit the partitions and it doesn't detect any media, or partitions at all.

Any clues?
Thanks
Christian

That's a hardware incompatibility between your disks and Ubuntu itself. I'd suggest trying a different distro (Fedora or openSUSE), one of those might work better on your hardware. If neither of those work either, or you absolutely must use Ubuntu, I'd suggest filing a bug for Ubuntu on Launchpad.net, you'll probably get better support there; hopefully the kernel devs responsible for maintaining the drivers themselves will notice, and try to fix your issue (or have it fixed in a later release/update).

> so...I went through the process, with a few hitches, but i thought it had completed successfully. However, after the computer rebooted, the only screen that would come up was "missing operating system."
Here are the hitches, in case that helps to address the issue:
- I did not have my Web server key, but it said "auto-detected succesfully", so i think that was ok.
- I got an error message when i tried to check too many boxes in the menu that lets you select the desktop. I tried multiple times, and eventually, when i selected only the ubuntu desktop (and nothing else), it went through
- I input 50% for the partition free space. It seemed as though the program would automatically partition the hard drive into a percentage, instead of me having to input a raw figure, but the hard drive is only 37G so if somehow it decided to format the entire drive, i suppose that could be the problem.
- i don't know if i can access the bios
Long story short, i would like to know if this is a fixable glitch, or if i need to
start figuring out how to reload OS's. 

Hopefully, the issue you're having is just a bootloader installation problem, not a partitioning issue, which can easily be fixed using the Super Grub Disk [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) just boot it up and it should hopefully be able to get you to boot into an OS and fix your bootloader.

Otherwise, if that doesn't work I'd just boot a Windows disk, go into recovery mode by pressing R, type in "fixmbr", that should remove GRUB altogether, and hopefully you'll be able to boot into Windows after that.

Otherwise, if you can't get either OS booting through either of the methods, the only advice I can offer is to boot up a liveCD/Ubuntu Desktop CD, mount your partitions, and recover whatever data you can, then do a clean re-install.

---

### Post by rodica.balasa on 2008-01-18
here is how i installed on an old computer, using a floppy and netboot:

[http://www.len.ro/work/tools/life-to-an-old-i8000-1/view]("http://www.len.ro/work/tools/life-to-an-old-i8000-1/view")

---

### Post by jnewm on 2008-01-20
Hi,

I just wanted to say thanks so much to everyone who put UNetbootin together!

I'd been using Ubuntu for a couple years and loved it, but couldn't, for the life of me, get Ubuntu to install on my desktop from the Live CD.  (The integrity check kept finding a single file error - whether on the Feisty, Gutsy, or alternative iso).  So, I was seriously on the verge of having to buy a new computer (or at least a new CD drive).  

BUT, UNetbootin worked perfectly!  I only wish I'd known about it before burning 20 CDs and staring at my computer for way too many hours :).

Thanks so much again!
Jesse

---

### Post by Skeptical33 on 2008-01-24
I have a Fedora 2 system that I'm trying to upgrade to Fedora 8 with.

I ran this from within that server:
```
./unetbootin-fedora8rev49.sh installmode=nohost targetpartition=/dev/sda3 formatpartition=yes
```

Next I rebooted, and now all I see is a "grub>" command line.  I don't know what to type from there to get the install working.  Help?

---

### Post by tuxcantfly on 2008-01-24
> **Skeptical33 said:**
> I have a Fedora 2 system that I'm trying to upgrade to Fedora 8 with.

I ran this from within that server:
```
./unetbootin-fedora8rev49.sh installmode=nohost targetpartition=/dev/sda3 formatpartition=yes
```

Next I rebooted, and now all I see is a "grub>" command line.  I don't know what to type from there to get the install working.  Help?

Strange, it should have displayed a menu rather than the grub prompt, seems like the partition didn't get properly unmounted, or something else failed on the grub install process... Anyhow these commands should do the job:

```
root (hd0,2)
kernel /boot/ubnkern
initrd /boot/ubninit
```

or, this might also do the job:

```
root (hd0,2)
configfile /boot/grub/menu.lst
```

If it still doesn't work, try it with different options for the first line, like root (hd0,1) and the like

---

### Post by Skeptical33 on 2008-01-24
> **tuxcantfly said:**
> Strange, it should have displayed a menu rather than the grub prompt, seems like the partition didn't get properly unmounted, or something else failed on the grub install process... Anyhow these commands should do the job:

```
root (hd0,2)
kernel /boot/ubnkern
initrd /boot/ubninit
```

or, this might also do the job:

```
root (hd0,2)
configfile /boot/grub/menu.lst
```

If it still doesn't work, try it with different options for the first line, like root (hd0,1) and the like

Awesome advice! The second command worked! Thank you!

---

### Post by Skeptical33 on 2008-01-25
A new problem.  Once the setup proceeds to the hard drive partitioning area, it's not able to locate any of my hard disks!

I'm running RAID 5 on an Adaptec 2015s SCSI Raid card.

How can I resolve this problem?

---

### Post by tuxcantfly on 2008-01-25
> **Skeptical33 said:**
> A new problem.  Once the setup proceeds to the hard drive partitioning area, it's not able to locate any of my hard disks!

I'm running RAID 5 on an Adaptec 2015s SCSI Raid card.

How can I resolve this problem?

Sorry, can't help on that one; I'm no RAID expert. Once the installer has been loaded (as it seems to now have been), any issue after that is a general Fedora hardware bug, not one related to UNetbootin (all this does it load the installer, after that it's the standard procedure). Since your hardware seems to have worked fine with an older version of Fedora, this sounds like a pretty nasty regression. I'd suggest filing a bug on Fedora's bug tracker, maybe some developers who know more about Fedora's kernel and RAID handling system might be able to help. If you're not specifically tied in to Fedora, you could always try some different distribution (might work better with your hardware, and these days most mainstream distros are practically the same), but that's just about all I can suggest.

---

### Post by Skeptical33 on 2008-01-25
> **tuxcantfly said:**
> Sorry, can't help on that one; I'm no RAID expert. Once the installer has been loaded (as it seems to now have been), any issue after that is a general Fedora hardware bug, not one related to UNetbootin (all this does it load the installer, after that it's the standard procedure). Since your hardware seems to have worked fine with an older version of Fedora, this sounds like a pretty nasty regression. I'd suggest filing a bug on Fedora's bug tracker, maybe some developers who know more about Fedora's kernel and RAID handling system might be able to help. If you're not specifically tied in to Fedora, you could always try some different distribution (might work better with your hardware, and these days most mainstream distros are practically the same), but that's just about all I can suggest.

Say I wanted to switch distros or even versions of Fedora, how can I accomplish this now?  I'm remotely controlling this server via KVM over IP and don't have physical access to the machine.

Can I still boot back to my original Fedora 4.4, since it hasn't been deleted yet?  What command would I type in grub to get it back?

---

### Post by tuxcantfly on 2008-01-25
> **Skeptical33 said:**
> Say I wanted to switch distros or even versions of Fedora, how can I accomplish this now?  I'm remotely controlling this server via KVM over IP and don't have physical access to the machine.

Can I still boot back to my original Fedora 4.4, since it hasn't been deleted yet?  What command would I type in grub to get it back?

The command would depend on what partition the original install was on. If, say, it was on /dev/sda4, then it would be (I'm assuming you're using GRUB not LILO as the Fedora bootloader):

```
root (hd0,3)
configfile /boot/grub/menu.lst
```

The second number is always 1 less than the partition number in the Linux notation (since GRUB numbering starts at 0 not 1).

Or, if you were using a dedicated /boot partition as /dev/sda2, then it would be:

```
root (hd0,1)
configfile /grub/menu.lst
```

Or, this may also work, if the bootloader was installed to the partition itself (in this example /dev/sda6):

```
root (hd0,5)
chainloader +1
```

---

### Post by Skeptical33 on 2008-01-25
Great that worked. Now, how do I erase the UNetbootin thing so that next time I reboot, my old system is back, rather than dropping me to the grub command line?

Also, you mentioned that UNetbootin just gets you to the normal install screen.  However, I do recall that during the first install screen, it should ask you if you have a third-party scsi drivier to load?

---

### Post by tuxcantfly on 2008-01-25
> **Skeptical33 said:**
> Great that worked. Now, how do I erase the UNetbootin thing so that next time I reboot, my old system is back, rather than dropping me to the grub command line?

Also, you mentioned that UNetbootin just gets you to the normal install screen.  However, I do recall that during the first install screen, it should ask you if you have a third-party scsi drivier to load?

Once you boot into fedora, enter the following command (as root):

```
grub-install /dev/sda
```

That should install GRUB back to overwrite the UNetbootin-installed MBR. Otherwise, there's a more sophisticated approach that can be used if that doesn't work, it basically goes along these lines, details at [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html)

```
grub
(grub prompt should now show up)
root (hd0,2)
setup (hd0)
quit
```

As for the third-party scsi driver part, I don't recall ever seeing that even when installing from DVD (though I may just have overlooked it), nor do I see it in the official install docs. Perhaps the feature may have been removed in newer Fedora versions?

(PS did the RPM version not work, or why did you use the shellscript "installmode=nohost formatpartition=yes" installation option? That approach is generally intended for usage from liveCD/liveUSB distros to install on a computer with no functional Linux or Windows install, since it overwrites the MBR and installs its own bootloader)

---

### Post by Skeptical33 on 2008-01-25
> **tuxcantfly said:**
> 
As for the third-party scsi driver part, I don't recall ever seeing that even when installing from DVD (though I may just have overlooked it), nor do I see it in the official install docs. Perhaps the feature may have been removed in newer Fedora versions?
Well it has been a long while so perhaps I've gotten things confused with the Windows 2003 install process?  But as I recall, there was some way to install a third-party SCSI driver.

Anyways, I searched online and found that my Adaptec 2015s runs on I2O (whatever that is).  And from this page, [http://i2o.shadowconnect.com/faq.php#fedora_howto](http://i2o.shadowconnect.com/faq.php#fedora_howto), it seems like it's only supported up to Fedora 4.

> **tuxcantfly said:**
> 
(PS did the RPM version not work, or why did you use the shellscript "installmode=nohost formatpartition=yes" installation option? That approach is generally intended for usage from liveCD/liveUSB distros to install on a computer with no functional Linux or Windows install, since it overwrites the MBR and installs its own bootloader)
I did the first option and rebooted, but nothing seemed to have happened. This is why I went with the second option.  Maybe I did something wrong?
[edit] on second thought, i think I may have missed that new menu option. Wasn't looking closely for it.

---

### Post by Skeptical33 on 2008-01-25
This is really strange, but I was installing Fedora 8 on 2 servers, and after a whole afternoon of downloading, now both of them have this error on a black screen:

```

GRUB Loading stage1.5

GRUB loading, please wait...
Error 15
```

What happened there?

---

### Post by hhuuhhu on 2008-01-25
Hi,
i'm trying to use unetbootin to replace Windows XP totally with Ubuntu 7.10. I'm following tutorial ([http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora](http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora)), but in partitioning step i chose "Guided - use entire disk". Everything went fine until I got an error message during the Base System Installation.

ERROR MESSAGE

"Unable to install initramfs-tools

An error was returned while trying to install the initramfs-tools package onto the target system.

Check /var/log/syslog or see virtual console 4 for details."

PART OF THE SYSLOG in /var/log/syslog

base-installer: info: Using kernel 'linux-generic'
base-installer: info: Setting do_initrd='yes'.
base-installer: info: Setting link_in_boots='no'.
base-installer: info: Available initramfs generator(s): 'initramfs-tools'
apt-install: Unexpected error; skipped processing of: initramfs-tools
base-installer: apt-install or in-target is already running so you cannot run either of
base-installer: them again until the other instance finishes. You may be able to use
base-installer: 'chroot /target ...' instead.
base-installer: error: exiting on error base-installer/kernel/failed-package-install'


So, i have formatted my hard disk and haven't any other OS installed. CD-Rom device doesn't work and unetbootin installer doesn't recommend ending this installation. I'm doing the installation on laptop, so it doesn't have Floppy drive. How can I solve this problem and get Ubuntu installed? I Have used already 3 nights searching for solution, but can't find anything. Would appreciate, if someone could help me.

---

### Post by tuxcantfly on 2008-01-26
> **hhuuhhu said:**
> Hi,
i'm trying to use unetbootin to replace Windows XP totally with Ubuntu 7.10. I'm following tutorial ([http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora](http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora)), but in partitioning step i chose "Guided - use entire disk". Everything went fine until I got an error message during the Base System Installation.

ERROR MESSAGE

"Unable to install initramfs-tools

An error was returned while trying to install the initramfs-tools package onto the target system.

Check /var/log/syslog or see virtual console 4 for details."

PART OF THE SYSLOG in /var/log/syslog

base-installer: info: Using kernel 'linux-generic'
base-installer: info: Setting do_initrd='yes'.
base-installer: info: Setting link_in_boots='no'.
base-installer: info: Available initramfs generator(s): 'initramfs-tools'
apt-install: Unexpected error; skipped processing of: initramfs-tools
base-installer: apt-install or in-target is already running so you cannot run either of
base-installer: them again until the other instance finishes. You may be able to use
base-installer: 'chroot /target ...' instead.
base-installer: error: exiting on error base-installer/kernel/failed-package-install'


So, i have formatted my hard disk and haven't any other OS installed. CD-Rom device doesn't work and unetbootin installer doesn't recommend ending this installation. I'm doing the installation on laptop, so it doesn't have Floppy drive. How can I solve this problem and get Ubuntu installed? I Have used already 3 nights searching for solution, but can't find anything. Would appreciate, if someone could help me.

Ouch, that's one sticky situation, seems like a package (initramfs-tools, used to generate the initrd to boot Ubuntu) got corrupted while downloading and the rest of the installation went downhill from there. When you reboot the machine, you'll probably get the GRUB Error 17 or Error 15 message, since the kernel and initrd haven't been properly installed hasn't yet been installed to the partition and GRUB hasn't been installed, though you can get around this by booting off either a floppy or USB key, if you can boot from either. I'd suggest fetching the Super Grub Disk (floppy or usb drive version) from [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) and see if you can get it to boot anything. If not, I'd fetch the Debian floppy or USB drive install media (it's on ftp.debian.org) and get a minimal Debian environment installed, from there on you should be able to install the UNetbootin deb package for whatever distro you want installed (aka Ubuntu), that'll let you launch the installer again and hopefully everthing will work that time.

Otherwise, if you have no access to any physical boot media (floppy or USB) whatsoever, I'd remove your hard drive from the computer, transfer it temporarilty to another computer that can boot from CD, USB, or Floppy, get an OS installed or repair the bootloader using either the Super Grub Disk, or, if that doesn't work, do a minimal debian install, and put the hard drive back into the original computer once done, and it should be able to boot properly.

Also, on another note, it's generally a much safer and wiser solution to initially dual-boot, then turn it into a single-boot by deleting the partition and expanding the Linux one after it has installed successfully, especially when you can't fall back on a rescue CD, in order to avoid situations like this. Do that next time you attempt to install, just in case something goes wrong again or your connection fails, so that you'll have a working system to fall back on.

---

### Post by tuxcantfly on 2008-01-26
> **Skeptical33 said:**
> This is really strange, but I was installing Fedora 8 on 2 servers, and after a whole afternoon of downloading, now both of them have this error on a black screen:

```

GRUB Loading stage1.5

GRUB loading, please wait...
Error 15
```

What happened there?

Bootloader apparently didn't get installed properly, for some reason (did you get any error messages, or did you just leave it unattended and come back to see the error? In the latter case, perhaps your connection might have failed while in the middle of downloading and installing the kernel/bootloader or the like, causing Fedora to abort the installation). Unless you were booting UNetbootin off a USB stick (and GRUB got installed to the USB drive not the hard drive due to a bug in Fedora's installer, this occurs on Ubuntu due to a bug in d-i, it may also affect Fedora), the issue is either an incompatibility between the version of GRUB installed by Fedora and your hardware (might be the SCSI/SATA/RAID controller; the kernel and GRUB use different code for handling disks so it may be that GRUB was incompatible with it but the kernel was compatible), or perhaps GRUB was installed using the wrong parameters (did you instruct it to install GRUB to the MBR or to a partition? Because if GRUB wasn't installed to the MBR, then the UNetbootin-installed GRUB might still be attempting to load, but since you probably wiped out its partition, it can't find the necessary files).

Hopefully this server isn't a remote Xen guest, because if you have physical access to it, you can probably easily fix all using the Super Grub Disk at [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) (just boot the CD/floppy/USB drive, select the GRUB repair option, and all should work), but if you don't, you're going to have to attempt a remote recovery of the server's bootloader, which I believe may be possible if you can access the virtual server's BIOS itself or otherwise get it to do a PXE network boot off another server on the internet. If that's the case, I'm afriad I can't help, since I don't remotely administer servers, but these links might help (and if they don't, hopefully you can get hold of someone who has physical access to the servers  so that you can do a GRUB recovery on them):

[https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

---

### Post by whitefang5412 on 2008-01-26
Hm. I'm looking into purchasing an ASUS eee pc, but I'm sure as some of you know it does not have a cd-rom drive. I want to install ubuntu on it from this method, just scared something may go wrong and I'm down in the dumps for a while using this ubuntu machine until I can find out a way to get an OS installed on that machine so I can atleast use it. Hm.... Any suggestions?

---

### Post by tuxcantfly on 2008-01-26
> **whitefang5412 said:**
> Hm. I'm looking into purchasing an ASUS eee pc, but I'm sure as some of you know it does not have a cd-rom drive. I want to install ubuntu on it from this method, just scared something may go wrong and I'm down in the dumps for a while using this ubuntu machine until I can find out a way to get an OS installed on that machine so I can atleast use it. Hm.... Any suggestions?

Perhaps this was what you were looking for? [http://wiki.eeeuser.com/ubuntu:eeexubuntu:home](http://wiki.eeeuser.com/ubuntu:eeexubuntu:home) (see the USB installation section). I doubt you'll have any success with UNetbootin, since from what I remember, the eee PC ships with a wifi incompatible with default Ubuntu so there's no way of fetching the packages from the net.

---

### Post by Stevi on 2008-01-27
Hey, I've got some questions before using netbootin. I'd like to install mandriva-linux-2008-spring-free-ophrys-dvd-i586.iso. Is it possible to install this .iso (maybe renaming it to mandriva-linux-2008.0-free-dvd-i586.iso) with the mandriva.deb following these instructions:
[quote="[unetbootin](http://lubi.sourceforge.net/unetbootin.html)

"]_Mandriva Instructions_
If installing Mandriva, first use PartedMagic Partition Manager (download) to create 2 spare partitions: a 4 GB one to store the ISO temporarily for installation, and a larger one to install Mandriva in. Then, download Mandriva Linux "Free" (NOT "One") 2008 to the new 4GB partition. Then install UNetbootin, reboot, and select "Hard Drive" as the installation source, select your 4GB partition and the folder containing the ISO, then proceed with the standard install process.[/quote]
:confused::confused:
I need the beta because from time to time my Laptop freezes with the older kernel (also with ubuntu or other dists).

---

### Post by Skeptical33 on 2008-01-27
> **tuxcantfly said:**
> Bootloader apparently didn't get installed properly, for some reason (did you get any error messages, or did you just leave it unattended and come back to see the error? In the latter case, perhaps your connection might have failed while in the middle of downloading and installing the kernel/bootloader or the like, causing Fedora to abort the installation). Unless you were booting UNetbootin off a USB stick (and GRUB got installed to the USB drive not the hard drive due to a bug in Fedora's installer, this occurs on Ubuntu due to a bug in d-i, it may also affect Fedora), the issue is either an incompatibility between the version of GRUB installed by Fedora and your hardware (might be the SCSI/SATA/RAID controller; the kernel and GRUB use different code for handling disks so it may be that GRUB was incompatible with it but the kernel was compatible), or perhaps GRUB was installed using the wrong parameters (did you instruct it to install GRUB to the MBR or to a partition? Because if GRUB wasn't installed to the MBR, then the UNetbootin-installed GRUB might still be attempting to load, but since you probably wiped out its partition, it can't find the necessary files).

Hopefully this server isn't a remote Xen guest, because if you have physical access to it, you can probably easily fix all using the Super Grub Disk at [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) (just boot the CD/floppy/USB drive, select the GRUB repair option, and all should work), but if you don't, you're going to have to attempt a remote recovery of the server's bootloader, which I believe may be possible if you can access the virtual server's BIOS itself or otherwise get it to do a PXE network boot off another server on the internet. If that's the case, I'm afriad I can't help, since I don't remotely administer servers, but these links might help (and if they don't, hopefully you can get hold of someone who has physical access to the servers  so that you can do a GRUB recovery on them):

[https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

Yes it was unattended so I didn't see any intermediate messages.  The same problem has occurred on 2 separate servers now.  

What's worse is, now the system looks broken.  I try booting off a Fedora 7 LiveCD, and it works fine.  Problem occurs when I click the "install to hard drive" icon on the desk top.  On the second step where I select the language, it just freezes.  It didn't use to do that.  I had Fedora 7 installed using the same CD prior.

I tried re-formatting the hard drives, but still the same error.  Do you have any ideas how to fix this thing?

---

### Post by tuxcantfly on 2008-01-27
> **Stevi said:**
> Hey, I've got some questions before using netbootin. I'd like to install mandriva-linux-2008-spring-free-ophrys-dvd-i586.iso. Is it possible to install this .iso (maybe renaming it to mandriva-linux-2008.0-free-dvd-i586.iso) with the mandriva.deb following these instructions:

:confused::confused:
I need the beta because from time to time my Laptop freezes with the older kernel (also with ubuntu or other dists).

Extract the ophrys iso, locate the kernel and initrd (should be named vmlinuz and initrd.gz and be in the isolinux subdirectory or so), rename them to ubnkern and ubninit, and place them into c:\unetbootin (replace the existing ones), and reboot, that should do the job. If you can't find the initrd and kernel files, try using the ones off the ftp mirrors instead.

---

### Post by tuxcantfly on 2008-01-27
> **Skeptical33 said:**
> Yes it was unattended so I didn't see any intermediate messages.  The same problem has occurred on 2 separate servers now.  

What's worse is, now the system looks broken.  I try booting off a Fedora 7 LiveCD, and it works fine.  Problem occurs when I click the "install to hard drive" icon on the desk top.  On the second step where I select the language, it just freezes.  It didn't use to do that.  I had Fedora 7 installed using the same CD prior.

I tried re-formatting the hard drives, but still the same error.  Do you have any ideas how to fix this thing?

Strange, indeed... Anyhow, if you happen to have a DOS bootdisk handy, try booting that and using the DOS fdisk to create a new DOS disklabel, that'll wipe out the MBR, all partitions, and hopefully Fedora won't hang when attempting to install to the disk. Alternatively, you might try to overwrite the first few sectors of the hard drive (MBR, PBR, etc) using dd with null bytes, then use fdisk to initialize a new DOS disklabel, and see if that does the job.

---

### Post by Skeptical33 on 2008-01-28
> **tuxcantfly said:**
> Strange, indeed... Anyhow, if you happen to have a DOS bootdisk handy, try booting that and using the DOS fdisk to create a new DOS disklabel, that'll wipe out the MBR, all partitions, and hopefully Fedora won't hang when attempting to install to the disk. Alternatively, you might try to overwrite the first few sectors of the hard drive (MBR, PBR, etc) using dd with null bytes, then use fdisk to initialize a new DOS disklabel, and see if that does the job.

I don't have any boot disks. Everything is remote and I can't get my hands on the server.  Hence I used UNetbootin.

Any other ideas on how to kill the MBR?  I don't know how to use dd to erase the first few sectors.

---

### Post by tuxcantfly on 2008-01-28
> **Skeptical33 said:**
> I don't have any boot disks. Everything is remote and I can't get my hands on the server.  Hence I used UNetbootin.

Any other ideas on how to kill the MBR?

However, you said you could boot the Fedora LiveCD then right? Try doing this then (as root):

```
dd if=/dev/zero of=/dev/sda
```

That'll overwrite the disk's contents with zeros (you probably only have to do it for the first few megabytes or so). Then after that enter:

```
fdisk /dev/sda
```

fdisk will spew out errors and ask to initialize a new DOS disk label, enter the command "o" on the fdisk prompt (to create a new DOS disklabel), recreate your partitions, and hopefully it will work after that.

---

### Post by ossguy on 2008-01-29
In order to understand a bit better what can be done with UNetbootin, I'm interested in knowing a bit more about how it works.  From what I can tell, it copies the kernel image and initrd image to the UNetbootin installation directory on the host (Windows or Linux).  When you run UNetbootin from the host, it adds an entry in the bootloader that points to the kernel and initrd images in the UNetbootin installation directory on the host (which is on an NTFS or ext2/3, etc. partition).  On reboot, the kernel and initrd images are loaded into RAM but none of the partitions on the hard drive are mounted.  This way, the installer can blow away the partition containing the kernel and initrd images while its running (since they are loaded into memory and the partitions aren't mounted).  Is this correct?

If so, I would pretty much understand how UNetbootin works.  There's one more thing that I don't quite understand, though.  How does UNetbootin remove itself from the bootloader menu after it's booted?

Thanks for all your work on UNetbootin and related projects.  I think this project will start taking off as more and more machines start shipping without an optical drive (Asus' Eee PC, OLPC's XO, Apple's MacBook Air, etc.).

---

### Post by ossguy on 2008-01-29
It seems to me that UNetbootin and related projects could benefit from moving to mailing lists instead of using forum threads as the primary means of communication.  I find it easier to post to mailing lists since it is easier to send an e-mail than to login to a forum site and post a reply.  Mailing lists also handle different threads of conversation more gracefully since most e-mail clients and archive tools (like pipermail, which most Mailman installs use) can group messages by thread.  This makes it easier to find a topic that has been previously discussed.

I would suggest having Sourceforge host the mailing lists through the Lubi project page.  This has worked well for me in projects that I have hosted.

I'd be happy to discuss this further.  Let me know if you have any comments or questions.

---

### Post by tuxcantfly on 2008-01-29
> **ossguy said:**
> In order to understand a bit better what can be done with UNetbootin, I'm interested in knowing a bit more about how it works.  From what I can tell, it copies the kernel image and initrd image to the UNetbootin installation directory on the host (Windows or Linux).  When you run UNetbootin from the host, it adds an entry in the bootloader that points to the kernel and initrd images in the UNetbootin installation directory on the host (which is on an NTFS or ext2/3, etc. partition).  On reboot, the kernel and initrd images are loaded into RAM but none of the partitions on the hard drive are mounted.  This way, the installer can blow away the partition containing the kernel and initrd images while its running (since they are loaded into memory and the partitions aren't mounted).  Is this correct?

Yes, pretty much correct

> If so, I would pretty much understand how UNetbootin works.  There's one more thing that I don't quite understand, though.  How does UNetbootin remove itself from the bootloader menu after it's booted?

It adds the uninstaller to the Windows autostart; that way it's removed (menu entry along with the files) next time the user boots WIndows. Theoretically, this can also be accomplished by loading a temporary kernel that removes the menu entry then chainloads the main kernel/initrd, but I stick with the Windows uninstaller approach because it's generally safer.

---

### Post by ossguy on 2008-01-29
Because of the large number of distributions that UNetbootin supports and since UNetbootin has separate releases for each distribution that contain that distributions kernel and initrd files (usually), there are a ton of released files to choose from when downloading.  This could turn into quite a headache for the maintainer of UNetbootin as a change to the core of UNetbootin requires all of the packages to be re-made, for example.

I suggest that the core UNetbootin functionality be confined to a single package for each host distribution (so there would be one .deb, one .rpm, one .exe, etc.) that knows how to handle the installation of any target distribution (ie. FreeDOS, Ubuntu, etc.).  This core package would know how to grab the necessary minimal ISO files from the web as needed (when the user selects which distro they want to install) and then take the necessary files from the ISO and stick them on the hard drive.

There could also be an option for the user to specify their own ISO to UNetbootin.  This would allow users to test new distributions that UNetbootin doesn't know about yet.  It may require UNetbootin to include a mechanism to search for the kernel and initrd image and prompt the user if it can't find them in the ISO.

Since I haven't really looked at the code, I'm not sure how feasible this would be, but it seems like the sort of thing that would be good to move toward.

---

### Post by ossguy on 2008-01-29
From what I can tell, UNetbootin has not been tested on the Eee PC or OLPC XO and does not support Mac OS X.  I'm guessing you're probably thinking about these, but in case you aren't, here's a nudge.

The Eee PC might work with the Debian package, but I'm not sure whether the file locations or bootloader configuration are sufficiently similar to most Debian installations to make it work.  I may have access to an Eee PC for testing, but I'm not sure if I'd have a lot of time to test it.

The XO might work with the RPM, but it's less likely because it uses the Sugar interface by default.  You could make a proper activity and use the Sugar interface, but it might be easier just to use a command-line app for starters.  Also, the XO will not boot a standard kernel because it does not have the standard BIOS that most kernels assume.  So one would have to replace the distribution-provided kernel from the minimal ISO with the kernel from the XO.  This isn't too hard, but would require some special casing.  It also means that UNetbootin would have to replace the installed kernel with the XO kernel, which is a little harder to do.  Hopefully the mainline kernel will soon support the OLPC, but for now I don't think it does.  I would be able to do some testing on the XO, but it probably won't be for a month or two.  You could also emulate it yourself if you like ([http://wiki.laptop.org/go/Emulating_the_XO](http://wiki.laptop.org/go/Emulating_the_XO)).

Lastly, it would be nice to have Mac OS X support, especially now that the MacBook Air (sans optical drive) is released.  This is probably a fair bit of work (at least to make it look nice), but perhaps you can find an OS X coder that's interested.  You may want to include the automatic installation of rEFIt ([http://refit.sourceforge.net/](http://refit.sourceforge.net/)) to make things easier on the user.

I hope my comments are useful.  I'd be happy to discuss them in more detail if you have questions.

I'd really like to see more resources behind this project (perhaps in the form of official Canonical support).  I think that would really help with implementing some of these high-priority feature requests.  Any tips on how to push for that would be appreciated.

---

### Post by ossguy on 2008-01-29
> **tuxcantfly said:**
> Perhaps this was what you were looking for? [http://wiki.eeeuser.com/ubuntu:eeexubuntu:home](http://wiki.eeeuser.com/ubuntu:eeexubuntu:home) (see the USB installation section). I doubt you'll have any success with UNetbootin, since from what I remember, the eee PC ships with a wifi incompatible with default Ubuntu so there's no way of fetching the packages from the net.

The wired ethernet should work fine on the Eee PC during installation so I suspect UNetbootin would work.  The wireless can be setup after the installation is completed using the instructions at [https://help.ubuntu.com/community/EeePC](https://help.ubuntu.com/community/EeePC).  Similar methods should work for other distributions.

---

### Post by tuxcantfly on 2008-01-29
> **ossguy said:**
> Because of the large number of distributions that UNetbootin supports and since UNetbootin has separate releases for each distribution that contain that distributions kernel and initrd files (usually), there are a ton of released files to choose from when downloading.  This could turn into quite a headache for the maintainer of UNetbootin as a change to the core of UNetbootin requires all of the packages to be re-made, for example.

I suggest that the core UNetbootin functionality be confined to a single package for each host distribution (so there would be one .deb, one .rpm, one .exe, etc.) that knows how to handle the installation of any target distribution (ie. FreeDOS, Ubuntu, etc.).  This core package would know how to grab the necessary minimal ISO files from the web as needed (when the user selects which distro they want to install) and then take the necessary files from the ISO and stick them on the hard drive.

There could also be an option for the user to specify their own ISO to UNetbootin.  This would allow users to test new distributions that UNetbootin doesn't know about yet.  It may require UNetbootin to include a mechanism to search for the kernel and initrd image and prompt the user if it can't find them in the ISO.

Since I haven't really looked at the code, I'm not sure how feasible this would be, but it seems like the sort of thing that would be good to move toward.

Yes, I've considered the idea before, and while it would work well for the Windows version, it's rather infeasible on Linux, due to the lack of a standard user interface that works basically universally on both platforms, preinstalled without needing excessive dependencies (I'd rather not maintain 2 incompatible codebases), not to mention that the install-and-reboot simplicity wouldn't go as smoothly. As for mailing lists, I tend to avoid them due to the sheer amount of spam they tend to get, and I'd rather not bother with the hassle of managing a mailing list. As for EEE PC and Mac OSX, I don't have the hardware, though that link to the emulator is certainly going to be helpful. Anyhow, thanks for the advice, I'll see if I can get any of those suggestions implemented as soon as I have time (aka spring break), it's finals season here so I must get back to studying.

---

### Post by andreas_m on 2008-02-01
Hi,

everything runs well,except i can't fling off the Linux boot loader,despite the fact I've already uninstall it  when i log in my Windows XP Home.

Any help!!!!

---

### Post by tuxcantfly on 2008-02-01
> **andreas_m said:**
> Hi,

everything runs well,except i can't fling off the Linux boot loader,despite the fact I've already uninstall it  when i log in my Windows XP Home.

Any help!!!!

Edit C:\boot.ini (if you can't see it, make sure to enable the show hidden files option, uncheck the read-only/system properties before editing it), and remove the line that says "C:\ubnldr.mbr=UNetbootin" or so (the last line).

PS could you post the contents of the boot.ini file prior to editing it, so that I can see what might've went wrong with the uninstallation process?

---

### Post by andreas_m on 2008-02-01
> **tuxcantfly said:**
> Edit C:\boot.ini (if you can't see it, make sure to enable the show hidden files option, uncheck the read-only/system properties before editing it), and remove the line that says "C:\ubnldr.mbr=UNetbootin" or so (the last line).

PS could you post the contents of the boot.ini file prior to editing it, so that I can see what might've went wrong with the uninstallation process?

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Windows Server 2003, Enterprise" /noexecute=optout /fastdetect

I don't see anything refering to UNetbootin.Any suggestions???

---

### Post by tuxcantfly on 2008-02-01
> **andreas_m said:**
> [boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Windows Server 2003, Enterprise" /noexecute=optout /fastdetect

I don't see anything refering to UNetbootin.Any suggestions???

What do you refer to by "i can't fling off the Linux boot loader"? Are you trying to remove GRUB itself (so that you can no longer boot into Ubuntu)? If so, boot up a Windows XP recovery cd, go into recovery mode, type in "fixmbr", that'll remove GRUB and leave you booting into only Windows.

---

### Post by andreas_m on 2008-02-01
> **tuxcantfly said:**
> What do you refer to by "i can't fling off the Linux boot loader"? Are you trying to remove GRUB itself (so that you can no longer boot into Ubuntu)? If so, boot up a Windows XP recovery cd, go into recovery mode, type in "fixmbr", that'll remove GRUB and leave you booting into only Windows.

I mean when i reboot then first appears the Linux bootloader and then i choose other OS so windows bootloader appears.
Simply i wish to have one bootloader with three options: Ubuntu,Windows XP,Windows Server 2003.

Is that possible???

---

### Post by tuxcantfly on 2008-02-01
> **andreas_m said:**
> I mean when i reboot then first appears the Linux bootloader and then i choose other OS so windows bootloader appears.
Simply i wish to have one bootloader with three options: Ubuntu,Windows XP,Windows Server 2003.

Is that possible???

NTLDR (the Windows boot manager) can't boot Linux, therefore the only way to get all 3 booted from 1 bootloader is to use GRUB and remove the Windows bootloader options. Therefore, remove that last line in your boot.ini (so that when you attempt to boot Windows XP it goes straight into it), then edit your /boot/grub/menu.lst (as [root](https://help.ubuntu.com/community/RootSudo)) in Ubuntu, and add this line at the end (after the Windows XP line):

```
title Windows 2003
root (hd1,0)
chainloader +1
map (hd0) (hd1)
map (hd1) (hd0)
boot
```

If that doesn't work to get Windows 2003 booted, see [here](http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q10) (or search these forums for "GRUB map disk", "GRUB multiple windows", etc)

---

### Post by jenra on 2008-02-02
I've got an odd problem, I messed up a gutsy installation by uninstalling gnome (no idea how, must have been half-asleep.
My system has an XP partition and a gutsy partition (w/ swap, etc.). I used a program I found online called MBRFIX.exe to get rid of grub (no recovery disks on me at the moment), but now the interesting part: boot.ini does nothing! It reads as follows:
[boot loader]
timeout=15
default=c:\ubnldr.mbr
[operating systems]
c:\ubnldr.mbr="UNetbootin-ubuntu710x64rev99"
But in reality there is a 0 second timeout and it shows two operating systems:
Microsoft Windows XP Professional
Microsft Windows
The second option seems to start up a terminal (edit: windows cmd)  while the first boots up Windows XP normally. Neither entry is in the boot.ini, nor does UNetbootin show up at all. I'm quite confused. How can I get UNetbootin to show up?
Thanks!

---

### Post by hums07 on 2008-02-03
I tried installing Ubuntu but I got error. After choosing "Ubuntu" at the NTLDR boot loader option, I got error messages something like:
```
Try (hd0,0) ...
Try (hd0,1) ...
Try (hd0,2)...

```
Looks like it did not find grub (?). So, instead I installed using Netboot approach from this wiki page: [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows).

We all know that PCLinuxOS has been on the top list of distrowatch.com for some months now, so I wonder if you have a plan to support its installation via UNetbootin.

---

### Post by tuxcantfly on 2008-02-05
> **hums07 said:**
> I tried installing Ubuntu but I got error. After choosing "Ubuntu" at the NTLDR boot loader option, I got error messages something like:
```
Try (hd0,0) ...
Try (hd0,1) ...
Try (hd0,2)...

```
Looks like it did not find grub (?). So, instead I installed using Netboot approach from this wiki page: [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows).

Yes, that's a GRLDR/GRUB4DOS-related boot error. Strange, though, that it worked when you used the manual instructions, as they do essentially the same thing as UNetbootin. Probably, sporadic file fragmentation/corruption was responsible for the issue; a defragmentation and chkdsk /f should fix the issue if you ever encounter it in the future.

> **hums07 said:**
> We all know that PCLinuxOS has been on the top list of distrowatch.com for some months now, so I wonder if you have a plan to support its installation via UNetbootin.

Done. PCLinuxOS builds are at [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=261499](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=261499)
This version works a bit differenly from the previous UNetbootin builds (since PCLinuxOS is a liveCD-only distro), so make sure to read the installation instructions at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) (middle of the page, titled "PCLinuxOS Instructions")

---

### Post by hums07 on 2008-02-05
> **tuxcantfly said:**
> Yes, that's a GRLDR/GRUB4DOS-related boot error. Strange, though, that it worked when you used the manual instructions, as they do essentially the same thing as UNetbootin. Probably, sporadic file fragmentation/corruption was responsible for the issue; a defragmentation and chkdsk /f should fix the issue if you ever encounter it in the future.

This info might be useful to you. When I installed Ubuntu using manual approach I used grub4dos version 0.4.1pre22. I failed when I used version 0.4.3, it gave the same error message as above.

---

### Post by lootje2 on 2008-02-08
I bought a 2nd-hand with 7.10 pre-installed (so not my personal/preferred configs etc). I played with it, like it, but now want a fresh install.

Is UNetbootin a viable option to do this and if so, how to completely remove the first?

Thanks for your time.

Lootje2

---

### Post by tuxcantfly on 2008-02-08
> **lootje2 said:**
> I bought a 2nd-hand with 7.10 pre-installed (so not my personal/preferred configs etc). I played with it, like it, but now want a fresh install.

Is UNetbootin a viable option to do this and if so, how to completely remove the first?

Thanks for your time.

Lootje2

Yes, UNetbootin (use the .deb version since you have Ubuntu already installed) will be able to wipe out your existing install completely if you use the "Use Entire Disk" option when prompted in the partitioning stage. Remember to back up your data first, since everything on that computer will be getting wiped out.

Then again, for safety, you may want to instead resize the existing install and temporarily keep both, until you're sure; you can subsequenly delete your existing Ubuntu install's partition and expand the new install's partition after you've made a new, fresh install. It takes slightly longer, but it's safer since you won't be left with an unbootable computer should your connection fail in the middle of the downloading stage and thereby potentially ruin the entire installation process.

---

### Post by lootje2 on 2008-02-08
Thanks for quick and clear reply.

It's now 01.43, so somewhere tomorrow I will have a go at it.

Thanks again,
Lootje2

---

### Post by johnraff on 2008-02-19
A BIG thankyou to Tuxcantfly for putting this together - it's *exactly* what I had been searching the web for! An install from a Windows 98 partition worked perfectly, just as it said on the tin. :)
I'm now tempted to try out some of the other distros on offer...

One small question: I wanted a minimal command-line install, so I disobeyed the instructions to select a desktop and, as I couldn't see an option for a command-line setup, I just left all the options unchecked. I got my system OK but instead of the 300M or so I was expecting, after "aptitude clean" I still had 750M or so. A bit of searching around came up with some Open Office stuff, English locales for Firefox and Thunderbird, and some of xorg. Removing all that got me down to about 450M...

Is there no way to install a minimal command-line Ubuntu system with unetbootin?

---

### Post by keryil on 2008-02-23
Does anybody know if I can use an internet connection over wireless over VPN for this kind of installation (i.e. a wireless network that has an internet connection over a VPN)?

---

### Post by whoscheesemine on 2008-02-23
Hello all,

I downloaded Unetboot and followed all the directions to a 'T'. When it asked which distro I wanted to go with I chose Xubuntu. I know Xubuntu will work on this computer as I've installed it before. I am currently using a patition with a messed up Ubuntu/Xubuntu/ interface but that's another story I won't get into. This computer has a very slow CD-ROM drive so I figured this Unetboot would be an excllent method. I'm already loving it and thinking its an awesome idea, but I'm having an issue with it that I was hoping someone could share some enlightenment with me on. I went to boot it for the first time after it was finished installing. It did all the checks then it asked me to login in text. Odd, I thought, as I've never had to do that before. So, I logged in with my user and pass and then i was given a quick warning about how ubuntu comes with no license and then.... well that's it. Its just all terminal. Its all command prompt...... What did i do wrong?!:confused::(
[COLOR="Red"][B]
Edit:[/B][/COLOR] I see that there are updates that need to be installed now that I'm back on the working partition. If I did half the installation last night, and the other half this morning, when new updates were to take place after it checked for updates or something, would that cause an issue? Just trying to think of things here! thanks!

[COLOR="Red"]**Edit #2:**[/COLOR] I decided to write down and type everything grub said to see if it would help the situation at all. 

Basically, I turn on the computer, lots of stuff is said but the very last screen says the following:

* Mounting local file systems...             [ok]
* Activating swapfile swap...                  [ok]
$Mounting securityfs on /sys/kernel/security: done     [ok]
Loading APParmor profiles: done
*Checking minimum space in /tmp...   [ok]
*Configuring network interfaces...   [ok]
*Setting up console font and keymap...   [ok]
*Loading ACPI modules   [ok]

*Starting ACPI services   [ok]

*Starting system log daemon...   [ok]

*Starting kernel log daemon   [ok]

Ubuntu 7.10 Shekels tty1

Shekels login *Starting deffered execution scheduler atd   [ok]

*Starting Periodic command scheduler crond   [ok]

*Running local boot scripts (/etc/rc.local)   [ok]

That's where it stops. I've let it sit for a good hour or two and it stays there, but when I press enter it says the following:

Last login: Sat Feb 23 17:25:09 EST 2008 on tty1
Linux Shekels 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/sharedoc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

shekels@Shekels:~$

The last part is a prompt where I can enter terminal commands. I don't know grub that well (if that's what the linux version of DOS is called I'm not sure enlighten me if I'm wrong I'd much rather know what its called then to not know... kind of obsessive like that).

A thought I just had was that when I installed this I chose the username to be shekels just like the other partition. I named it this, because it is the last name of my mother and little brother and it is easy for them to remember. I suppose if the issue is caused by having them both be named shekels I could reinstall it with a different name. Now I could be wrong here, but I thought the SDA1, 2 so forth and so on were each assigned to each partition to seperate them from one another so an issue like having the username on both be the same wouldn't be an issue. Chances are, I'm wicked wrong here, but I like to guess things and have people tell me whether I'm right or not to further my knowledge on such things. 

If anyone can help me out thanks a million.

---

### Post by johnraff on 2008-02-24
Failing a Higher Guru... :)

Anyway, that's the normal (?) Gutsy command-line login it seems.
The "*username* login" bit comes too soon, but if you start typing your username at the point where it stops you can log in normally.

As to why you got a command-line interface, not a desktop, it might be because you didn't select the Xubuntu optiion properly. You have to hit the space bar when the star is by the option you want, before hitting enter to continue with the install.

If you've got the patience, you could try doing the whole install over again...

---

### Post by whoscheesemine on 2008-02-24
I actually have plenty of patience and will try that now, thanks a million. I know that I most deffinitely did not hit spacebar before I hit enter.

EDIT: That's exactly what the problem was. Thanks alot!

---

### Post by tuxcantfly on 2008-02-25
I've released a new version of UNetbootin, now written in proper Qt4 and C++. 

New Features: In addition to being able to load the usual distributions (currently Ubuntu, Fedora, openSUSE, CentOS, and Debian; I'll add in the others later), it can also load any kernel and initrd (with parameters), or floppy/hard drive disk image.

Currently supports only Windows, though I'll have Linux support ready soon (Qt4 should make cross-platform porting easier).

Download at: [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=264540](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=264540)

New interface:

[img]http://sourceforge.net/dbimage.php?id=161201[/img]

---

### Post by RayArdia on 2008-02-28
Used unetbootin-ubuntu710rev113 to attempt dual boot with XP. All seemed to go according to plan until, right at the end of the process it hangs , with flashing cursor, at:-

....
ubuntu login:*starting deferred execution scheduler                    [OK]
*starting periodic command scheduler crond                                   [OK]
*running local boot scripts (/etc /rc, local)                                     [OK]
_

First try the flashing cursor appeared on the left, second try on the right, otherwise no apparent differences in the process. No matter how long I wait, nothing further happened - only option is to reboot by switch on cpu.
I have not uninstalled  unetbootin-ubuntu710rev113 as prompted by screen on restarting windoze, and Win XP works OK. 
The "boot options screen is starting to look jungle-like with lots of entries because of my various attempts to get unetbootin to complete!
What now please, oh wise ones? BTW profile inserts details of a laptop I was having problems with. The above comments apply to running unetbootin on my desktop PC a Time AMD i386 machine with only 256MB Ram and 80GB HDD, 1.15Mhz.

---

### Post by tuxcantfly on 2008-02-28
> **RayArdia said:**
> Used unetbootin-ubuntu710rev113 to attempt dual boot with XP. All seemed to go according to plan until, right at the end of the process it hangs , with flashing cursor, at:-

....
ubuntu login:*starting deferred execution scheduler                    [OK]
*starting periodic command scheduler crond                                   [OK]
*running local boot scripts (/etc /rc, local)                                     [OK]
_

First try the flashing cursor appeared on the left, second try on the right, otherwise no apparent differences in the process. No matter how long I wait, nothing further happened - only option is to reboot by switch on cpu.
I have not uninstalled  unetbootin-ubuntu710rev113 as prompted by screen on restarting windoze, and Win XP works OK. 
The "boot options screen is starting to look jungle-like with lots of entries because of my various attempts to get unetbootin to complete!
What now please, oh wise ones? BTW profile inserts details of a laptop I was having problems with. The above comments apply to running unetbootin on my desktop PC a Time AMD i386 machine with only 256MB Ram and 80GB HDD, 1.15Mhz.

So I presume this is after the ubuntu installation, on the first boot? In that case, it's most likely a graphics card driver incompatibility issue, which usually occurs  when using ATI/AMD cards (though some have had similar issues with nvidia and intel chipsets as well).

As soon as the screen goes blank, press Ctrl-Alt-F2. You should see a login screen; login there, then once logged on, enter the following command:

```
sudo dpkg-reconfigure xserver-xorg
```

You'll be asked a few questions about your monitor and graphics card, accept the defaults, but when asked about the video card driver, select "vesa" from the list instead. Then reboot, and hopefully all should work.

---

### Post by RayArdia on 2008-02-29
> **tuxcantfly said:**
> So I presume this is after the ubuntu installation, on the first boot? In that case, it's most likely a graphics card driver incompatibility issue, which usually occurs  when using ATI/AMD cards (though some have had similar issues with nvidia and intel chipsets as well).

As soon as the screen goes blank, press Ctrl-Alt-F2. You should see a login screen; login there, then once logged on, enter the following command:

```
sudo dpkg-reconfigure xserver-xorg
```

You'll be asked a few questions about your monitor and graphics card, accept the defaults, but when asked about the video card driver, select "vesa" from the list instead. Then reboot, and hopefully all should work.

Thankyou; did that and got:_

Package xserver-xorg is not installed and no info is available. Use dpkg --info (=dpkg-deb --info) to examine archive files and dpkg --content to list
/usr/sbin/dpkg -reconfigure:
xserver-xorg is not installed

By typing various things (in almost total ignorance ) I got assorted help etc screens, but not much that made any sense to the ancient brain! Sorry to be a pain in the ........ but I could use a bit more help!
Ray

---

### Post by rupert on 2008-03-01
when I try to install the deb for hardy it tries to download the kernel images, since I dont have a network card on that laptop it cant get this.
Is there a complete offline package for this or do I have to download them by hand?

---

### Post by cacycleworks on 2008-03-01
> **RayArdia said:**
> 
ubuntu login:*starting deferred execution scheduler                    [OK]
*starting periodic command scheduler crond                                   [OK]
*running local boot scripts (/etc /rc, local)                                     [OK]


Apologies if this is a "dumb answer" ... that appears to be the standard login prompt: and then those messages are "console" messages as those processes were starting.

At this point, you could/should be able to type the username you created followed by the password. If you hit enter a few times, it will lose its mind for a second or 5, and then present the login prompt again.

:)
Chris

---

### Post by rupert on 2008-03-02
OK , after I reaized that Ubuntu cant be installed from an ISO file that is located on a HD i tries to install the latest Fedora Rawhide. I can select the partition where the iso is located and the installer starts, after some seconds it stops and the logs say:

unable to identify CDROM format
VFS: cant find ext2 on dev loop1

and some stuff about selinux taht cant write some stuff because its a read only FS.

can someone help me with this?
I need an install that has the 2.4.24+ Kernel and can be installed from HD, because I dont have a network card and I cant boot from anything, no cdrom no usbstick

thx

---

### Post by tuxcantfly on 2008-03-03
> **rupert said:**
> OK , after I reaized that Ubuntu cant be installed from an ISO file that is located on a HD i tries to install the latest Fedora Rawhide. I can select the partition where the iso is located and the installer starts, after some seconds it stops and the logs say:

unable to identify CDROM format
VFS: cant find ext2 on dev loop1

and some stuff about selinux taht cant write some stuff because its a read only FS.

can someone help me with this?
I need an install that has the 2.4.24+ Kernel and can be installed from HD, because I dont have a network card and I cant boot from anything, no cdrom no usbstick

thx

Fedora Rawhide is in rather early alpha right now, so presumably it won't work at all on certain hardware (apparently won't work on yours). If you really need a cutting-edge distro, either go for openSUSE 11.0 Alpha 2 (seems to work better IMHO) or Fedora 9 Alpha 1 (barely works here, but you may have better luck). Just pre-download the kernel and initrd from the FTP mirrors (they're usually named "linux", "vmlinuz", "bzImage", "initrd.img", "initrd.gz", or the like), download the DVD install image (no need to extract or anything), download the UNetbootin Generic Loader at [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=264540](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=264540) (this'll let you load the custom kernel/initrd), transfer the 4 files (DVD iso, kernel, initrd, and UNetbootin .exe file) to the target computer, run UNetbootin there specify the kernel and initrd paths when prompted, reboot, and see if it works then (standard procedure after that; select "Hard Drive" as installation source, specify partition and directory, etc).

---

### Post by koer9911 on 2008-03-10
I'm on ubuntu 5.10.

I downloaded "unetbootin_ubuntu710rev99_all.deb".

And instlled it using command:
 sudo dpkg -i unetbootin_ubuntu710rev99_all.deb

Installing went fine then i rebooted ,but in GRUB menu 
selecting UNetbootin-ubuntu710rev99.
i got error:15(or21) Selected disk does not exist.

EDIT: Yess.. i got it working and it works perfectly !!!

---

### Post by marxistvegan on 2008-03-11
Odd question I have OSX and VirtualBox with Ubuntu installed, I have a new computer with no CD or DVD or Floppy.  So my question is can I use a Virtual run of Ubuntu on OSX to install ubuntu on the new pc?  Does this also work for MythUbuntu?

---

### Post by tuxcantfly on 2008-03-11
> **marxistvegan said:**
> Odd question I have OSX and VirtualBox with Ubuntu installed, I have a new computer with no CD or DVD or Floppy.  So my question is can I use a Virtual run of Ubuntu on OSX to install ubuntu on the new pc?

Theoretically, yes (not sure about VirtualBox, but I know VMware can target a physical partition), but I'd strongly advise against it, not only because it'll involve plenty of manual tinkering with your partitions and MBR/GPT (a mistyped command or two will wipe out your data and render your computer unbootable), but also because the virtualized hardware is different from the physical one, so even if you manage to get Ubuntu installed to the physical partition from a virtual machine, install a bootloader, and boot Ubuntu, you'll still have to tinker with getting the machine's hardware properly detected and configured. If you happen to have Bootcamp set up (I'm assuming this is an Intel Mac), you can just run the Windows version of UNetbootin from Windows, otherwise, the next best route would probably just be to make a bootable USB drive and install Ubuntu from there.

>  Does this also work for MythUbuntu?

Yes, you can get MythUbuntu installed; just install the standard Ubuntu desktop, and you can install the package "mythbuntu-desktop" afterwards to end up with a Mythbuntu desktop.

---

### Post by anystupidname on 2008-03-13
I'm looking for a clonezilla unetbootin. Has somebody already created one? If not, how hard is it to use an already created ISO to generate my own package? I'm on Ubuntu and have really been liking the partedmagic and other unetbootin packages. Thanks! :)

---

### Post by V4mpire on 2008-03-13
hi i was interested in trying this as i cant use cdrom as ide has died.. but i have 1 main problem and that is alot of distros haven't supported my network card on start of installer i am currently using debian etch but feel like a change... but only reason i came here is because someone was helping me find a way of netinstalling a different distro and i would like to try the newest ubuntu 8.04 but i need to know if this would support my onboard lan card otherwise this is going to pose a problem unless theres a way i can install the network drivers on before install so it will continue and that ubuntu would support the lan card when i have finished install. the network card is 01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169SC Gigabit Ethernet (rev 10)

---

### Post by tuxcantfly on 2008-03-14
> **anystupidname said:**
> I'm looking for a clonezilla unetbootin. Has somebody already created one? If not, how hard is it to use an already created ISO to generate my own package? I'm on Ubuntu and have really been liking the partedmagic and other unetbootin packages. Thanks! :)

Read the sections titled "Installing Other Distributions Using UNetbootin" and "Packaging UNetbootin for Other Distributions" from [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) (the first is simply if you want to load CloneZilla, the second is if you want to make a new UNetbootin package for CloneZilla to redistribute en masse). From the site:

> Installing Other Distributions Using UNetbootin

Download the Generic UNetbootin Loader, and supply it with the appropriate floppy/hard disk image, or kernel and initrd files when prompted (see first screenshot). See your distribution's FTP mirrors, or the contents of the iso file, to find these files. If special booting options and parameters are required for the kernel, check the distribution's boot configuration files (usually after the "kernel" line in either isolinux.cfg, syslinux.cfg, menu.lst, or grub.conf) and supply them on the "Option" line.
Packaging UNetbootin for Other Distributions

Thanks to UNetbootin's portable architecture, it is easy to add support for other distributions. If you would like to create UNetbootin packages for other distributions, first make sure you have installed the "bzr", "alien", "fakeroot", and "wine" utilities, which are installable through your package manager, then check out the source with the command:

    bzr checkout [http://bazaar.launchpad.net/~gezakovacs/unetbootin/devel-new](http://bazaar.launchpad.net/~gezakovacs/unetbootin/devel-new)

Then add the name of the distribution, referred to here as {distroname}, into the file "targetdistros" in the checked-out source, add the netboot initrd and kernel, with the naming scheme "ubninit-{distroname}" and "ubnkern-{distroname}" into the "initkern" folder, then cd to the source directory, and run the command:

    ./build

Then, the ".exe", ".deb", ".rpm", and ".sh" packages for distribution will be created in the "dist" directory. More info is available in the readme file in the source folder.

If you're wondering where the kernel and initrd files can be found, they can generally be found in the "isolinux" or "boot" subdirectories, titled either "kernel" "vmlinuz", "bzImage", and similar names for the kernel file, and "initrd.img", "initrd.gz", or the like for the initrd file.

> hi i was interested in trying this as i cant use cdrom as ide has died.. but i have 1 main problem and that is alot of distros haven't supported my network card on start of installer i am currently using debian etch but feel like a change... but only reason i came here is because someone was helping me find a way of netinstalling a different distro and i would like to try the newest ubuntu 8.04 but i need to know if this would support my onboard lan card otherwise this is going to pose a problem unless theres a way i can install the network drivers on before install so it will continue and that ubuntu would support the lan card when i have finished install. the network card is 01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169SC Gigabit Ethernet (rev 10)

Given the package merge from Debian, the network card will probably be supported, but if you're still unsure, just install the package and reboot; if the netboot installation works, then your card is supported you're good to go, and if it fails, just reboot back, remove the package, and your system will be back to normal.

---

### Post by V4mpire on 2008-03-14
> **tuxcantfly said:**
> Given the package merge from Debian, the network card will probably be supported, but if you're still unsure, just install the package and reboot; if the netboot installation works, then your card is supported you're good to go, and if it fails, just reboot back, remove the package, and your system will be back to normal.

only problem being is i would like to be able to change distro as i have messed debian up abit i dunno if it will boot back up if i reboot but is there anyway i could say get the lan drivers if need be and put them onto a floppy disk and if it doesn't work with my lan card then i could get it to install those drivers to use ?

---

### Post by tuxcantfly on 2008-03-16
@V4mpire: The only change that's occurring is an added entry to menu.lst, so if it's still able to reboot properly now, it will be able to do so after an install attempt (no formatting or other serious modification occurs until well into the netboot-install stage, by which you'll have noticed if your network card works or not).

@all: **ANNOUNCEMENT, NEW VERSION**

The latest version (rev166), available for download from [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=264540](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=264540) now supports the creation of bootable USB drives from Windows (also works in Linux via wine, native Qt4 version will be released as soon as I finish some GRUB-specific tweaks) in addition to support for a few additional distros and misc bugfixes. Please report if it works or not (and any relevant info if you encounter issues).

---

### Post by ugm6hr on 2008-03-16
This is great.

Especially the function to install to USB.  Means I can try out distros without having to write CD coasters.

Also - DSL is on the list (not mentioned in post 1).

---

### Post by BigMike007 on 2008-03-16
Hi,

been following this guide trying to get xbuntu onto an old Armada 4220t - no facility to change boot sequence.. so, all going well with unetbootin method until i get to the partioning screen... loads it up but appears not to be able to pick up hard disk so partition.  I just get two blank lines between "help on partitioning" and "undo changes to partitions".

Tried the detecting disks again but this just tells me about no driver for the "disk drive", which i take to be the fdd.  I then tried selecting "none of the above" from the list of drivers,  and then this tells me I have no detectable partionable disks attached to the computer...but i know there is as it has win98 installed on it (and boots fine into it)... is there something I can do to get it to detect?

Any guidance would be much appreciated...

cheers

---

### Post by BigMike007 on 2008-03-16
Hi,

been following this guide trying to get xbuntu onto an old Armada 4220t - no facility to change boot sequence.. so, all going well with unetbootin method until i get to the partioning screen... loads it up but appears not to be able to pick up hard disk so partition.  I just get two blank lines between "help on partitioning" and "undo changes to partitions".

Tried the detecting disks again but this just tells me about no driver for the "disk drive", which i take to be the fdd.  I then tried selecting "none of the above" from the list of drivers,  and then this tells me I have no detectable partionable disks attached to the computer...but i know there is as it has win98 installed on it (and boots fine into it)... is there something I can do to get it to detect?

Any guidance would be much appreciated...

cheers

---

### Post by tuxcantfly on 2008-03-16
> **BigMike007 said:**
> Hi,

been following this guide trying to get xbuntu onto an old Armada 4220t - no facility to change boot sequence.. so, all going well with unetbootin method until i get to the partioning screen... loads it up but appears not to be able to pick up hard disk so partition.  I just get two blank lines between "help on partitioning" and "undo changes to partitions".

Tried the detecting disks again but this just tells me about no driver for the "disk drive", which i take to be the fdd.  I then tried selecting "none of the above" from the list of drivers,  and then this tells me I have no detectable partionable disks attached to the computer...but i know there is as it has win98 installed on it (and boots fine into it)... is there something I can do to get it to detect?

Any guidance would be much appreciated...

cheers

Ubuntu seems to not support your hard disk/controller, and I'm not aware of any simple way to load a third-party driver during installation, so your best bet would probably be to try a different distro (Fedora, openSUSE, etc) or perhaps a different version of Ubuntu.

---

### Post by setotitan on 2008-03-17
well i really screwed the pooch on this one. up to recently i've been a windows user. i just started working with ubuntu on my desktop however i wanted to be able to carry a notebook around so i could work on it in my spare time. i have this acer travelmate laptop, it has no CD/DVD drives and no floppy. the only thing it has is 3 USB's and a firewire. it already had xp on it so i figured i'd use the UNetbootin installer. well everything was working great, right up until the end... i didn't have it plugged in and my battery died!! i know i know such a rookie mistake, but the DL was taking so long because i was doing it wireless i thought i'd move closer to my router to get better signal strength. i just lost track of time and it died. much to my dismay when i reboot it i get the bios splash screen and then it just goe's to a black screen with a blinking cursor. :( 

the only thing i could think to do is maybe install from a thumb drive. however when i look at the bios it only has the option to boot from a floppy, optical, hard drive, or network. i'm feeling like i'm totally screwed on this. i mean the laptop was about 4 years old but it wasn't trash by any means. and seeing as i've only used windows for the past 13 years all i can think to do is put in the install disc, and there's not even a CD drive for that!  ](*,) i have NO CLUE where to go from here. i wanted gutsy on it but if anyone can help get any OS back on there it would be a miracle! any and all suggestions are welcome.

---

### Post by ugm6hr on 2008-03-17
> **setotitan said:**
> i wanted gutsy on it but if anyone can help get any OS back on there it would be a miracle! any and all suggestions are welcome.

From post 1:
> If all else fails, or if you only have access to floppies, then first, download the Debian minimal-install floppies. Then, install Debian. Once installed, download the UNetbootin deb package using wget $unetbootin.deb, install it using dpkg -i $unetbootin.deb, then once done, reboot, and select UNetbootin in the GRUB menu.

---

### Post by setotitan on 2008-03-17
yeah, yanked the hard drive slapped it into a desktop and installed ubuntu that way. it's back in my laptop and working fine, thanks!

---

### Post by k33bz on 2008-03-21
Hi, I had made a post and someone reffered me to unetbootin, so I checked out the site.  But before I go ahead and do this I need to make sure on a few things.

My problem is this, I am running Fiesty Fawn on my laptop, and want to do a fresh install of Gutsy Gibbon, I have to use restricted drivers, ndiswrapper, and WICD for my laptop. WIFI is the only conection I have, no broadband connections.

So my question is this, If I install Gutsy over Fiesty using unetbootin (no extra partitions) Will it effect my WIFI?

---

### Post by tuxcantfly on 2008-03-24
> **k33bz said:**
> Hi, I had made a post and someone reffered me to unetbootin, so I checked out the site.  But before I go ahead and do this I need to make sure on a few things.

My problem is this, I am running Fiesty Fawn on my laptop, and want to do a fresh install of Gutsy Gibbon, I have to use restricted drivers, ndiswrapper, and WICD for my laptop. WIFI is the only conection I have, no broadband connections.

So my question is this, If I install Gutsy over Fiesty using unetbootin (no extra partitions) Will it effect my WIFI?

If so, I'd suggest doing an HD-Media install, rather than a netboot one; simply go to [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/) and download the files "vmlinuz" and "initrd.gz", specify those as the kernel (vmlinuz) and initrd (initrd.gz) when installing in "Manual" mode with UNetbootin (use the newer Generic version, not the Ubuntu-specific one), and download the 7.10 **alternate** (not desktop/liveCD) iso to the root directory of your partition. Then reboot, hopefully the installer will begin and will detect the iso file, and you should be able to install Ubuntu that way.

Beforehand, of course, remember to save the required drivers to a USB drive or so, so that you can install them after the installation to get internet access.

---

### Post by kknull on 2008-03-29
hi,
I cannot install unetbootin: I have winxp and I have only an E: drive (because there is an ext3 partition before the ntfs one).
How can I resolve?

Thanks.

---

### Post by tuxcantfly on 2008-03-29
> **kknull said:**
> hi,
I cannot install unetbootin: I have winxp and I have only an E: drive (because there is an ext3 partition before the ntfs one).
How can I resolve?

Thanks.

Which version are you using? If it's not the newer, Generic version, use that one (download at [http://unetbootin.sourceforge.net/unetbootin-windows-latest.php](http://unetbootin.sourceforge.net/unetbootin-windows-latest.php) )

---

### Post by cokhavim on 2008-04-03
> **tuxcantfly said:**
> 

ERROR MESSAGE

"Unable to install initramfs-tools

An error was returned while trying to install the initramfs-tools package onto the target system.

Check /var/log/syslog or see virtual console 4 for details."

Ouch, that's one sticky situation, seems like a package (initramfs-tools, used to generate the initrd to boot Ubuntu) got corrupted while downloading and the rest of the installation went downhill from there. When you reboot the machine, you'll probably get the GRUB Error 17 or Error 15 message, since the kernel and initrd haven't been properly installed hasn't yet been installed to the partition and GRUB hasn't been installed, though you can get around this by booting off either a floppy or USB key, if you can boot from either. 

.

How do I access /var/log/syslog or virtual console 4 when running the installer?  I'm having the same issue as this person who posted, but I don't know how to see the log, and I don't want to exit the installer for fear of not being able to boot again (CD player doesn't work).

Also, using the installer, I was able to change mirrors and download the packages again, but the same error message appears about initramfs-tools.

Another thing: I have a separate /boot partition that I did not format during these installation attempts.  Is that what's affecting the initramfs-tools?  I dont' think it is because the previous poster (hhuuhhu) did a clean install using the whole disk.  I dont' want to format the /boot partition just yet unless I know for sure that it really is the problem.  

What should I do?  why is the installer hiccupping at initramfs-tools?

Thanks.

---

### Post by cokhavim on 2008-04-03
Ok, I found out how to access the console and copied the syslog to a usb disk.  I took the plunge and decided to abort the installation and found to my relief that grub still worked and did not erase the installer (I guess that makes sense since I didn't format the /boot partition).  So I started up the installer again, and got the same error about initramfs.

Here's the relevant section from syslog:

```
Apr  3 18:25:24 debootstrap: update-initramfs: deferring update (trigger activated)
Apr  3 18:25:24 debootstrap: 
Apr  3 18:25:24 debootstrap: Setting up ubuntu-minimal (1.79) ...
Apr  3 18:25:24 debootstrap: Processing triggers for libc6 ...
Apr  3 18:25:24 debootstrap: ldconfig deferred processing now taking place
Apr  3 18:25:24 debootstrap: Processing triggers for initramfs-tools ...
Apr  3 18:25:24 debootstrap: update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Apr  3 18:25:24 debootstrap: Cannot find /lib/modules/2.6.22-14-generic
Apr  3 18:25:24 debootstrap: update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Apr  3 18:25:24 debootstrap: dpkg: subprocess post-installation script returned error exit status 1
Apr  3 18:25:25 debootstrap: Setting up initramfs-tools (0.85eubuntu20) ...
Apr  3 18:25:25 debootstrap: update-initramfs: deferring update (trigger activated)
Apr  3 18:25:25 debootstrap: 
```

What's going on?

---

### Post by johnraff on 2008-04-08
> **ossguy said:**
> In order to understand a bit better what can be done with UNetbootin, I'm interested in knowing a bit more about how it works.  ...  On reboot, the kernel and initrd images are loaded into RAM but none of the partitions on the hard drive are mounted.  This way, the installer can blow away the partition containing the kernel and initrd images while its running (since they are loaded into memory and the partitions aren't mounted).  Is this correct?
> **tuxcantfly said:**
> Yes, pretty much correct
How much RAM is needed to do this?

(I've got this old box with 16MB that I'd like to try installing DSL on.)

---

### Post by Doctor Device on 2008-04-09
I have a thinkpad X24 with a damaged CD drive (I can run small live CDs like Puppy and DSL, but installing a full distribution is impossible. last time I tried, it took over 2 hours to get to the partitioner, on a regular ubuntu liveCD). right now I am running Debian Etch 4.0, because it could install over the internet. I stumbled across unetbootin earlier, saw that it supported the distribution I want (Mint), but I have run into a problem.

I installed libqt4 and it's dependencies, tried running unetbootin, no luck.

I installed everything in the repository that referenced libqt4, tried running it again, and I get the following error in the terminal.

> Qt: Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

./Downloads/unetbootin-linux-191: symbol lookup error: 
./Downloads/unetbootin-linux-191: undefined symbol: _ZN9QListData7detach2Ev

the "authentication failed" bit confuses me, because I'm logged in with the root password in the terminal.

in a word: HELP! (bear in mind that I've never been good with command lines, so use small words and lots of diagrams please. #-o)

---

### Post by vferrusola on 2008-04-12
Fresh installation of ubuntu 7.10 .
Install QT4.
Install unetbootin-linux-191 and i have this error:
Qt: Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

./Downloads/unetbootin-linux-191: symbol lookup error:
./Downloads/unetbootin-linux-191: undefined symbol: _ZN9QListData7detach2Ev

I like to install GOS from an ISO file.

May be a problem with the libQT's version?

Any know how to repair this error?

Thanks

---

### Post by madjr on 2008-04-13
Hello,

i would like to try unetbootin

but i need to install Ubuntu hardy on 5 different computers that do not have CD-rom.

it says that it downloads the iso.

does it have to download the same iso 5 times (1 for every install ) ?

or i can specify where the iso is and avoid re-downloading?

i don't have much experience with filesystem and partitions, so a step by step guide would be really appreciated.

thank you very much :KS

---

### Post by tuxcantfly on 2008-04-13
> **madjr said:**
> Hello,

i would like to try unetbootin

but i need to install Ubuntu hardy on 5 different computers that do not have CD-rom.

it says that it downloads the iso.

does it have to download the same iso 5 times (1 for every install ) ?

or i can specify where the iso is and avoid re-downloading?

i don't have much experience with filesystem and partitions, so a step by step guide would be really appreciated.

thank you very much :KS

No, you do not have to re-download the ISO file every time; use the version at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) and pre-download the iso file (the desktop one) the standard way (from the Ubuntu website), then just specify the iso file when you start UNetbootin (see screenshot on homepage). Either that, or simply install to a USB drive, and you can install from the USB drive to each of the computers. As for the installation, see the Ubuntu homepage itself (same process).

@vferrusola: I haven't been able to reproduce that error. What desktop environment are you using (I'm on GNOME here). Also what architecture is this (i386 or amd64; the binary is for i386 and you'll need the compatibility libraries if on amd64)? Also, what command are you using to invoke sudo (sudo, gksudo, kdesu)? Also, what qt version is this (I'm using the version from backports, 4.3.2-0ubuntu3.2)? And do you have all the packages installed (libqt4-gui and libqt4-core)?

---

### Post by tez-a on 2008-04-17
having tried 1 booting from cd "2 using wubi 7.04. 3 wubi 8.04 4 the 610 version of ubuntu as a dual install finally found this post about ubnetinstall so tried that it gives me an option so i pick linux mint. it starts to download and appears to stick but later it asks me to reboot. I choose ubutu and it flicks through the first stage then i get error 13 any ideas

---

### Post by tuxcantfly on 2008-04-18
> **tez-a said:**
> having tried 1 booting from cd "2 using wubi 7.04. 3 wubi 8.04 4 the 610 version of ubuntu as a dual install finally found this post about ubnetinstall so tried that it gives me an option so i pick linux mint. it starts to download and appears to stick but later it asks me to reboot. I choose ubutu and it flicks through the first stage then i get error 13 any ideas

Apparently, the ISO file wasn't downloaded properly; you didn't see any errors because I haven't yet finished the code for error reporting. If you have an unreliable connection, just download the iso file manually from the Linux Mint site, and select it under the Disk Image option when running UNetbootin.

---

### Post by te.ss on 2008-04-19
I have a Vista notebook and downloaded a version for windows-191 to install Hardy Heron on.  When an installation windows, I followed what shown in the screenshot.   When I rebooted, it straightly went into Windows. 

What did I do wrong?  :confused:

Thanks

---

### Post by mothwi on 2008-04-21
Booting Unetbootin from a Flash drive.  It worked great on my laptop.

My old Dell (PII400) is hanging at

[42.357595] RAMDISK: Compressed image found at block 0
[43.947900] RAMDISK: Ran out of compressed data
[43.947990] invalid compressed format (err=1)
[44.011948] VFS: Cannot open root device "<NULL>" or unknown-block(140,1)
[44.012031] Please append a correct "root=" boot option; here are the aviailable partitions:
[44.012114] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(104,1)

I'm perfectly happy to format the entire drive, if I can get to a utility to do so.  CD-ROM's dead.

---

### Post by madjr on 2008-04-22
> **tuxcantfly said:**
> No, you do not have to re-download the ISO file every time; use the version at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) and pre-download the iso file (the desktop one) the standard way (from the Ubuntu website), then just specify the iso file when you start UNetbootin (see screenshot on homepage). Either that, or simply install to a USB drive, and you can install from the USB drive to each of the computers. As for the installation, see the Ubuntu homepage itself (same process).



thanks tuxcantfly :)

i followed your instructions above.

Anyway the partition i have unetbootin and the ubuntu ISO is mounted as **/cdrom**, but using the ubuntu **installer** and when it launches the **partitioner** it un-mounts every partition that is mounted, including the partition **/cdrom**, then the installer just crashes.

Once the installer (ubiquity) crashes it won't launch anymore, so i have to reboot

Can't get installed :(

what should i do? 

thanks! :KS

---

### Post by avmian on 2008-04-23
Thanks tuxcantfly for this tool.

I just have one problem when I create an live USB with your tool. (ubuntu and kubuntu hardy) 
I can not choose the keyboard at boot time. As I have a french keyboard it is a problem.

I tried to change the syslinux.cfg like this:
from:
```
append initrd=/ubninit file=/cdrom/preseed/kubuntu-kde4.seed boot=casper quiet splash --
```
to:
```
append locale=fr_FR bootkbd=fr initrd=/ubninit file=/cdrom/preseed/kubuntu-kde4.seed boot=casper quiet splash --
```

But I still have the US keyboard. For information this method works with a standard syslinux installation.

---

### Post by jorgelamofeta on 2008-04-25
> **tuxcantfly said:**
> No, you do not have to re-download the ISO file every time; use the version at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) and pre-download the iso file (the desktop one) the standard way (from the Ubuntu website), then just specify the iso file when you start UNetbootin (see screenshot on homepage). Either that, or simply install to a USB drive, and you can install from the USB drive to each of the computers. As for the installation, see the Ubuntu homepage itself (same process).

@vferrusola: I haven't been able to reproduce that error. What desktop environment are you using (I'm on GNOME here). Also what architecture is this (i386 or amd64; the binary is for i386 and you'll need the compatibility libraries if on amd64)? Also, what command are you using to invoke sudo (sudo, gksudo, kdesu)? Also, what qt version is this (I'm using the version from backports, 4.3.2-0ubuntu3.2)? And do you have all the packages installed (libqt4-gui and libqt4-core)?

Like vferrusola and Doctor Device,I'm getting the error

```
unetbootin-linux-191: undefined symbol: _ZN9QListData7detach2Ev

``` 
when running unetbootin in Debian. Relevant details:

Linux 2.6.8 w/ Debian Etch running on a ix86
libqt4-core & libqt4-gui (both 4.2.1-2+etch1) installed
unetbootin run as root via su

This is actually an ancient dual boot machine (with a useless cd-rom), with windows me on the other side. One option is to ditch grub, revert to the windows version of the mbr and use the windowized unetbootin. 

Any suggestions?

Yours,
Jorge at the Skunkworks

---

### Post by jorgelamofeta on 2008-04-25
> **tuxcantfly said:**
> No, you do not have to re-download the ISO file every time; use the version at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) and pre-download the iso file (the desktop one) the standard way (from the Ubuntu website), then just specify the iso file when you start UNetbootin (see screenshot on homepage). Either that, or simply install to a USB drive, and you can install from the USB drive to each of the computers. As for the installation, see the Ubuntu homepage itself (same process).

@vferrusola: I haven't been able to reproduce that error. What desktop environment are you using (I'm on GNOME here). Also what architecture is this (i386 or amd64; the binary is for i386 and you'll need the compatibility libraries if on amd64)? Also, what command are you using to invoke sudo (sudo, gksudo, kdesu)? Also, what qt version is this (I'm using the version from backports, 4.3.2-0ubuntu3.2)? And do you have all the packages installed (libqt4-gui and libqt4-core)?

Like vferrusola and Doctor Device,I'm getting the error

```
unetbootin-linux-191: undefined symbol: _ZN9QListData7detach2Ev
``` 

when running unetbootin in Debian. Relevant details:

Linux 2.6.8 w/ Debian Etch running on a ix86
libqt4-core & libqt4-gui (both 4.2.1-2+etch1) installed
unetbootin run as root via su

This is actually an ancient dual boot machine (with a useless cd-rom), with windows me on the other side. One option is to ditch grub, revert to the windows version of the mbr and use the windowized unetbootin. 

Any suggestions?

Yours,
Jorge at the Skunkworks

---

### Post by Brian_M on 2008-04-26
First off, thanks to 'Tuxcantfly' and the rest who put time/effort into this (both the initial project and the follow-up questions).

Now, I'm stuck.  :P  IBM Thinkpad 240, can not boot from USB, CD, or PXE/network (can not, as in it's not allowed in the most current BIOS available).  Can boot from floppy, but I don't have one of those and don't care to incur the expense.  

I like the idea of WUBI and Unetbootin, but both fail...  Unetbootin is my preferred method anyway.  It hangs after the reboot, when trying to find the NIC.  There is no built-in NIC, so I'm forced to use a PCMCIA item (actually have 4 of the little buggers...  leftovers through the years), yet none of them are recognized.  Is there a list of what IS recognized out there somewhere?  I might be able to work a trade or borrow something that'll work for setup as I'm sure what I have will work fine once set up.  Or is there a way to add support for one of the 4 cards that I currently own?

I have no doubt that I could see an installation through to completion if I could just get past the network detection step.

Here are the PCMCIA NICs I have on hand: 1 is a 3com FE575CT-D, one is a 3com 3C589D-TP, one is a Xircom CEM56-100 and the last is a Netgear WAG511 (dual band wireless).

Thanks again,

Brian

---

### Post by crazydruid on 2008-04-27
I tried out UNetbootin on my HP laptop in an attempt to install Vector Linux alongside my default Vista.Sadly,being a newbie,i got totally confused and decided to uninstall UNetbootin. However,after doing so,it still appears as one of the options when i boot up my laptop.I can boot into Vista as per normal with no problems but how do i remove the UNetbootin entry (listed below)at boot up? I've searched for traces of it on my laptop but no joy.

UNetbootin-vector59rev62

Many thanks.
CD

---

### Post by phreakaholic on 2008-04-27
thanks, wanna try it on my own.

---

### Post by crazydruid on 2008-04-27
All sorted now. EasyBCD done the trick and removed the boot entry :)

---

### Post by Chonnawonga on 2008-05-07
Hi,

I'm trying to install Ubuntu on an old Thinkpad T22 with no CD drive. Unetbootin seems to be the perfect tool for this. My problem is that the current install of Windows 2000 seems to ignore the boot options set up in boot.ini and just go straight into normal Windows boot. Here's the boot.ini:

```
[boot loader]
timeout=1500
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect

C:\ubnldr.mbr="UNetbootin"

```

Any ideas about why this might happen?

Thanks!

---

### Post by Chonnawonga on 2008-05-07
Scratch that: the problem is obvious now that I see it here. This extra weird character seems to have thrown the whole thing off:

```

```

What the heck is that, anyway? I didn't even notice it until I saw it on my own post.

Now that I've removed it, the boot.ini is working, and I'm fine from there.

---

### Post by masonchumpia on 2008-05-10
After selecting the UNetbootin entry in Windows Vista Boot Manager, I get the following:

```

File: \ubnldr.mbr
Status: 0xc000000f
Info: The selected entry could not be loaded because the application is missing or corrupt.
```

Does anybody have any insight towards this?

---

### Post by Rydia on 2008-05-12
Hi

I've installed Unetbootin + Damn Small Linux on a Compaq Presario 1277 on top of Windows 98 SE. Unfortunately, during the boot up of UNetBootin, all it does is attack the floppy disk drive instead of booting from the hard disk. GRUB is loaded, it just only wants to attack disk :(

---

### Post by jeyros12 on 2008-05-14
Hi,
I tried to install xubuntu 8.04_x64 on one of my partitions (ntfs for the moment) with unetbootin under windows. First only my C drive appeared as hard disk, my other partitions appeared as usb drives whereas they're not (including the partition I was trying to install xubuntu on). I still continued the process : it downloaded some stuff then ask me for rebooting which I did. At rebooting, no prompt asking me for some ubuntu stuff or whatever, just the normal windows boot without any bootloader stuff like usual...

If it helps, 3 files were on the partition (syslinux.cfg, ubnkern, ubninit).

I'll be glad if you can help!

Tx

---

### Post by DogTired on 2008-05-24
I was unsuccessful at installing Xubuntu 8.04 onto an old laptop that has no CD drive.  It's a Sony VAIO PCG-Z505LS - 744Mhz, 128MB RAM, XP Pro currently installed.  I want a dual-boot installation with Xubuntu installed onto its own 10 GB partition.  The laptop does have network access.

I tried using Unetbootin, and the Xubuntu alternate install i386 ISO file.  The install started out OK, but right after configuring the keyboard layout it insisted on finding a CD-ROM drive.  When it couldn't find the CD drive, the installation would not progress and I had to terminate the install.  So it seems the installation starts off OK by finding the ISO file but then defaults back to trying to load the install from a CD.  Is there a parameter I can change to force the installation to look at the local image file?

I logged onto the Xubuntu IRC channel for some help and was told to open a shell during the install and edit /etc/apt/sources.list to comment out any references to the cd-rom.  When I opened the file, it was empty.  (Or maybe it had not been created by the install yet?)

Is there any way around this problem?  I suppose I could try using the unetbootin menu to install Ubuntu from the net, but on this old clunky laptop I'd much prefer to have Xubuntu.

Thanks for any help you can provide.

_Edit 1_ After trying to add anything to the sources.list file and then saving it - results in an error message stating 'No such file or directory'.  Searching the web, I've run across a couple of posts that say you must edit sources.list "as root".  I'm new to Linux and don't have a clue as to what this means.  Nor can I find any clarification.  Any help?

---

### Post by mendieta on 2008-05-24
Hi

This is a terrific tool. I meant to install kubuntu on my eeepc, in a 4GB SDHC, alongside the default xandros. However, when I run the unetbootin executable (I just downloaded the latest) i get a segmentation fault. Libqt4 is installed ... any ideas ?

Also, wouldn't it be helpful to add a **statically** linked download for Linux ? (I know it's a inefficient, but this would let you bootstrap the install in almost any Linux system

Cheers!

---

### Post by tuxcantfly on 2008-05-24
> **mendieta said:**
> Hi

This is a terrific tool. I meant to install kubuntu on my eeepc, in a 4GB SDHC, alongside the default xandros. However, when I run the unetbootin executable (I just downloaded the latest) i get a segmentation fault. Libqt4 is installed ... any ideas ?

Also, wouldn't it be helpful to add a **statically** linked download for Linux ? (I know it's a inefficient, but this would let you bootstrap the install in almost any Linux system

Cheers!

Xandros contains an outdated Qt4 version, that's probably causing the segfault (since I'm probably using a feature not present in earlier Qt4.x releases). Indeed, statically linking the executable would fix that issue; I'll make sure to make the next release statically linked.

@ DogTired: see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more info on running applications as root. To edit /etc/apt/sources.list as root, use this command:

```
sudo nano /etc/apt/sources.list
```

However, if you just want to install Xubuntu via the net, you can do that with the standard Ubuntu option in UNetbootin (it'll simply ask you which desktop environment to install after you begin the installer, select the one titled "xubuntu-desktop" or "XFCE").

---

### Post by tuxcantfly on 2008-05-24
> **mendieta said:**
> Hi

This is a terrific tool. I meant to install kubuntu on my eeepc, in a 4GB SDHC, alongside the default xandros. However, when I run the unetbootin executable (I just downloaded the latest) i get a segmentation fault. Libqt4 is installed ... any ideas ?

Also, wouldn't it be helpful to add a **statically** linked download for Linux ? (I know it's a inefficient, but this would let you bootstrap the install in almost any Linux system

Cheers!

Try the latest version (201) at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) that version is statically linked, and should hopefully eliminate the segfault issue (assuming that it was caused by an outdated libqt4 version).

---

### Post by mendieta on 2008-05-25
> **tuxcantfly said:**
> Try the latest version (201) at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) that version is statically linked, and should hopefully eliminate the segfault issue (assuming that it was caused by an outdated libqt4 version).

Awsome, I tried it, and the segfault is gone!. but I get a libc error and the program exits gracefully: 

```

/home/user/bin> sudo ./unetbootin-linux-201
./unetbootin-linux-201: /lib/tls/libc.so.6: version `GLIBC_2.4' not found (required by ./unetbootin-linux-201)

```

I'll see if i upgrade glibc ... thanks so much for all your work!

UPDATE: I enabled all the usual repositories for the eee 701 (as per the eeeuser.com), and there are no updates for libc6. There is a a libc6-i686 (version 2.3.6). Installing that didn't help :

```

./unetbootin-linux-201: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by ./unetbootin-linux-201)

```

I still think the static linking is a good think, it just doesn't make it for the eee :-(

Thank you!

---

### Post by Niva on 2008-05-26
Well I just installed Ubuntu 8.04 because the laptop I was given to install on had a failed cd/dvd drive.  It worked, but during the install there was a page where it asked me to select the packages I wanted to install and it was not intuitive how to select or what I needed.  Unfortunately pressing enter selected no packages and all I got was a basic kernel install with a cli interface.

I'm just making it through doing the manual apt-get install mess for desktop and etc.  

Still, very neat package and thanks for all the info here.

---

### Post by HHelsinger on 2008-05-26
I've downloaded the latest Unetbootin, but it won't boot!   Unetbootin itself won't load.  It starts to load, and then stops.  

 I'm running Win98 on an old Toshiba Portege.  I had previously loaded unetbootin 180, to install DSL, but as DSL had problems I deleted it, and unetbootin 180 along with it.  

I would like to use unetbootin to do a manual install of either TinyMe, or Puppy, but first unetbootin itself has to load.

Any ideas?

---

### Post by tuxcantfly on 2008-05-27
> **HHelsinger said:**
> I've downloaded the latest Unetbootin, but it won't boot!   Unetbootin itself won't load.  It starts to load, and then stops.  

 I'm running Win98 on an old Toshiba Portege.  I had previously loaded unetbootin 180, to install DSL, but as DSL had problems I deleted it, and unetbootin 180 along with it.  

I would like to use unetbootin to do a manual install of either TinyMe, or Puppy, but first unetbootin itself has to load.

Any ideas?

What portion exactly are you referring to as "UNetbootin itself"? If the application itself (aka on Windows) isn't starting up, try running it from the command line, see if it generates any output and post it. If it does indeed complete but GRUB4DOS (the bootloader) fails, it usually outputs error messages, write them down and post them.

Anyhow, I haven't tested on Win9x in a while, since I don't have ready access to Win9x, so some portions may be broken (it's probably due to the Unicode support for non-US users I included in UNetbootin, which Win9x doesn't support, since non-US users far outnumber the <1% of the population still using Win9x), but since you said that 180 worked, you can still get the older releases at [http://sourceforge.net/project/showfiles.php?group_id=222386&package_id=268713](http://sourceforge.net/project/showfiles.php?group_id=222386&package_id=268713) and the really old releases at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

And if your old computer happens to support booting from USB, you can always just create a bootable DSL/TinyMe USB drive from another computer and boot it on the computer running Win9x.

If that isn't an option, you can always do the job manually; download [ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/dsl-4.3-initrd.iso](ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/dsl-4.3-initrd.iso) and use 7-zip [http://www.7-zip.org/](http://www.7-zip.org/) to extract out the files "linux24" and "minirt24.gz" and supply those as the "kernel" and "initrd" files to UNetbootin, and under the "options" section type in whatever comes after APPEND in "isolinux.cfg", which is:

```
ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=791 initrd=minirt24.gz nomce noapic quiet BOOT_IMAGE=knoppix
```

---

### Post by cacycleworks on 2008-05-27
> **Niva said:**
> Well I just installed Ubuntu 8.04 because the laptop I was given to install on had a failed cd/dvd drive.  It worked, but during the install there was a page where it asked me to select the packages I wanted to install and it was not intuitive how to select or what I needed.  Unfortunately pressing enter selected no packages and all I got was a basic kernel install with a cli interface.

I'm just making it through doing the manual apt-get install mess for desktop and etc.  

Still, very neat package and thanks for all the info here.

Hi Niva, a command like "sudo apt-get install ubuntu-desktop" will load all the packages. Search these forums and Google for more info on that. I personally install ubuntu via this method --> cli then apt-get install all the goodies. :D

Thanks, 
Chris

---

### Post by mendieta on 2008-05-27
```

/home/user/bin> sudo ./unetbootin-linux-201
./unetbootin-linux-201: /lib/tls/libc.so.6: version `GLIBC_2.4' not found (required by ./unetbootin-linux-201)

```

I am thinking ... would it be possible to also link against glibc statically ? (to remove all dependencies?)

This would make unetbootin (the binary) more widely accesible !

Also, anyone knows of debian etch unetbootin current packages? 

Many thanks!

---

### Post by HHelsinger on 2008-05-28
I took your advice (I always do).  I downloaded an earlier version (180) of unetbootin, and indeed it did start up properly on my win98 Toshiba laptop.  So now I'm stuck further along.   I downloaded the iso of TinyMe - and that is on the desktop.  I told unetbootin to install it -- I reboot, I get a menu with a choice of Windows or Unetbootin, I choose the latter, it cycles through the menu again, I choose unetbootin again, and I get this message:
> (hd0.0)
Filesystem type is fat, partition type 0xc
[linux-bzImage, setup=0x1600,size=0x43f4]

unable to open Dosfile /menu.lst

I assume it is looking for a Grub menu.lst.  should one have been created by unetbootin?

The Toshiba won't boot from USB, nor from CD.  You suggested I could "do the job manually" by extracting "kernel" and "initrd" files from the current iso of dsl -- I assume that suggestion was specific to dsl, and I could use the comparable files (vmlinuz and initrd.gz) from TinyMe?  

Thanks.

---

### Post by tuxcantfly on 2008-05-29
> **HHelsinger said:**
> I took your advice (I always do).  I downloaded an earlier version (180) of unetbootin, and indeed it did start up properly on my win98 Toshiba laptop.  So now I'm stuck further along.   I downloaded the iso of TinyMe - and that is on the desktop.  I told unetbootin to install it -- I reboot, I get a menu with a choice of Windows or Unetbootin, I choose the latter, it cycles through the menu again, I choose unetbootin again, and I get this message:


I assume it is looking for a Grub menu.lst.  should one have been created by unetbootin?

The Toshiba won't boot from USB, nor from CD.  You suggested I could "do the job manually" by extracting "kernel" and "initrd" files from the current iso of dsl -- I assume that suggestion was specific to dsl, and I could use the comparable files (vmlinuz and initrd.gz) from TinyMe?  

Thanks.

Yes, vmlinuz and initrd.gz would work, though you'd need to also extract livecd.sqfs as well to the root directory (C:\). As for the PCLinuxOS kernel boot options, they are (from isolinux.cfg):

```
livecd=livecd initrd=initrd.gz root=/dev/rd/3 acpi=on vga=788 keyb=us splash=silent fstab=rw,noauto
```

---

### Post by pcmanager on 2008-05-29
Hi All.  Im trying to use unetbootin and in a new pclos gnome hd instalation i get the message 7pzip-full not installed when starting unetbootin.  I check synaptics and it shows it installed. After the error message the unetbootin starts and downloads the file i choose but stops after download...  I also tried it on a win xp serpack2 machine.  unetbootin starts. downloads files fast 731 meg 100 percent downlaoded then stops.  No extraction or copy will start?  Thanks for any help you can give me.

---

### Post by tuxcantfly on 2008-05-29
> **pcmanager said:**
> Hi All.  Im trying to use unetbootin and in a new pclos gnome hd instalation i get the message 7pzip-full not installed when starting unetbootin.  I check synaptics and it shows it installed. After the error message the unetbootin starts and downloads the file i choose but stops after download...  I also tried it on a win xp serpack2 machine.  unetbootin starts. downloads files fast 731 meg 100 percent downlaoded then stops.  No extraction or copy will start?  Thanks for any help you can give me.

Try pre-downloading the ISO to your desktop and providing the file to UNetbootin manually (on Windows); do you get the same error? As for "stops", how long did you wait before closing it (it may take a while to extract)? As for the error on PCLinuxOS, try entering the command "7z" on the terminal, the command isn't found right? Are there any other p7zip/7-zip packages in the PCLOS repos, try installing them if there are.

---

### Post by gnrathon on 2008-05-29
is this a "real" install
or a virtual one like Wubi?

---

### Post by tuxcantfly on 2008-05-29
> **gnrathon said:**
> is this a "real" install
or a virtual one like Wubi?

It's a "real" install. From the first sentence of the first post:

> UNetbootin allows for installation of various Linux distributions to a real partition (so it's no different from a standard Ubuntu install)

---

### Post by gnrathon on 2008-05-29
cool thanks
will i  have just attempted to install it
but as soon as i recoot, my computer gives an error screen 
then reboots again

did i do something wrong?

---

### Post by Leefmc on 2008-05-30
I've been skimming pages, but have yet to run into a similar problem. If i do, i'll remove this comment (and post a fix link).



I have a laptop with a broken Cd drive and no ability to boot from USB. So i installed UNetBootin, and downloaded the ISO Torrent from [http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/) for 8.04 x86 Desktop.

I ran UNetBootin with the ISO, and all seemed good. I rebooted, selected the UNetBootin option in the boot menu, went to Ubuntu, played, enjoyed myself, then shut down. I then by accident went into UNetBootin, which apparently reinstalled Ubuntu. Well, more playing took place, then i rebooted. Now at this point, as i was reading the directions i realized i needed to boot into windows, so i went into windows. Note that there were only 2 boot options, UNetBootin, and Windows. No Ubuntu.

Once i got into windows, it asked me to remove UNetBootin, i did so, and all seemed fine and dandy. I rebooted, hoping to get into Ubuntu, but no bootmenu appeared, and instead went straight into windows.

Can anyone explain what is wrong? I'm not familiar with duel-booting, so i can not even confirm it was successful, i know i did not see anything involving "Ubuntu" in my boot.ini, and the timeout is "30".

Infact, here is my entire boot.ini.
```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

```

Anyone know what is wrong?

Thanks,
Lee


*edit*
Also note, that when the installation of Ubuntu took place, i did not get any "steps". That is, the installation from the point i clicked the boot menu item "UNetBootin" to the time Ubuntu was running, i did not click the screen or type anything in. So in otherwords, it did not give me any options for creating a partition. Is this normal?

I would though, like to create a custom partition size.. without destroying my windows install.

---

### Post by pcmanager on 2008-05-30
Hi and thanks for the reply.  I downloaded the pclos iso to my pc, then let unetbootin use that.  I am using a hard drive case with usb connection to the windows pc.  In unetbootin, it only shows drive letter A for usb.  So when the program begins extracting and copy. I now get the error Drive A is open or no media.  Is there a way to fix this.   Thanks.  Oh if i ever get it installed to my usb hard drive. will it become bootable in different pc's or only the one origionally used to write the bootloader to the usb hard drive or is the bootloader written to the windows pc and just points to the hard drive for bootin.

On the linux pc like you said when i type 7z in a terminal i get the bash command not found... pclos synaptics says its installed but not the full version.  what program do i use to install the full version or what brand of linux...

Thanks Tuxcantfly

---

### Post by mendieta on 2008-05-31
Ok, I am trying to install Kubuntu in an eeepc with unetbootin and document it. I had an udev issue: 
```

vol_id not found. This is required for either install mode.
Install the "udev" package or your distribution's equivalent.
```

I solved the problem by symlinking:

```

sudo ln -s  /lib/udev/vol_id /sbin/vol_id
```

Maybe there is a cleaner solution, like making unetbootin search for vol_id in /lib/udev?

Also: the unetbootin program downloads some files to the usb device, but then it shows a button to "reboot now". If I press it, nothing happens. If I exit, grub is not modified (the menu.lst). Any ideas ?

Many thanks!

---

### Post by defenestratos on 2008-05-31
I download the file and make it executable. I double click on it. Nothing happens. Is it because it has no extension? I use 64 bit is that why?

---

### Post by laxinon on 2008-05-31
i`m trying to install Ubunto with Unetbootin.
the program starts but when at stage 2 (extracting) it stopped responding, this happen at the 7th file extract.
i tried to rerun it but nothing.
i suspect that it has something to do with C++ runtime that is not working properly .
the laptop i`m trying to install on has win XP SP2 but has many buges

---

### Post by mendieta on 2008-05-31
> **defenestratos said:**
> I download the file and make it executable. I double click on it. Nothing happens. Is it because it has no extension? I use 64 bit is that why?

Have you tried running it from the command line and see if there is any output to help you understand more?

---

### Post by Leefmc on 2008-05-31
Ok, im all good. Its either missing in the docs, or i just simply mis-understood what UNetBootin actually does. I thought it _installed_ ubuntu, rather than loading a livecd.

Though, something (possibly unetbootin) caused me mass problems, and i ended up whiping my Windows copy. Oh well.

Thanks! :)

---

### Post by mendieta on 2008-05-31
> **mendieta said:**
> 
Also: the unetbootin program downloads some files to the usb device, but then it shows a button to "reboot now". If I press it, nothing happens. If I exit, grub is not modified (the menu.lst). Any ideas ?
Many thanks!

Ok, I looked at the source code, I think I have a clue, hope someone can give me a hand and confirm I am right.

I have two drives:

/dev/sda -> Xandros install on the eeepc internal ssd 
/dev/sdb -> an external sdhc where I want to net-install Kubuntu

I want to modify the existing grub in /dev/sda. I am running unetbootin from Xandros  (/dev/sda1). In this case I should use a **hard drive** install and choose "/" as the target, right ? I was choosing "usb" and /dev/sdb, because that's where I will install Kubuntu. But I guess I was wrong, and the disk/partition where you will install your new OS is chosen after you reboot, during the actual install of the new OS, right? 

Graphically, this is what I was doing:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=72345&d=1212267052[/IMG]

And this is what I should be doing, right?: 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=72349&d=1212267929[/IMG]

Thanks in advance!

---

### Post by tuxcantfly on 2008-06-01
> **mendieta said:**
> Ok, I am trying to install Kubuntu in an eeepc with unetbootin and document it. I had an udev issue: 
```

vol_id not found. This is required for either install mode.
Install the "udev" package or your distribution's equivalent.
```

I solved the problem by symlinking:

```

sudo ln -s  /lib/udev/vol_id /sbin/vol_id
```

Maybe there is a cleaner solution, like making unetbootin search for vol_id in /lib/udev?

Also: the unetbootin program downloads some files to the usb device, but then it shows a button to "reboot now". If I press it, nothing happens. If I exit, grub is not modified (the menu.lst). Any ideas ?

Many thanks!

Something's wrong with your distribution's PATH. For the first issue, vol_id isn't in your path (I don't search for vol_id specifically in any directory, I use "whereis", which searches for binaries in your PATH, to locate it), and I'd rather not start hardcoding directories for every distribution that doesn't have its PATH set right (though I suppose I could try making an exception for eeepc's Xandros). Could you confirm that the command "whereis vol_id" doesn't return the correct path to the binary?

As for the reboot issue, apparently the command "init" isn't in your PATH either, probably the same issue, since I'm using the standard command "init 6" for rebooting.

Since I don't have an eeepc, could you post where the "init" binary for eeepc is, and could you confirm that running the command "init 6" manually as root doesn't reboot the computer (which is what I'm assuming is causing the reboot issue)?

As for the rest, if I recall correctly, Ubuntu wasn't fully compatible with the stock eeepc, so you'll probably also need to do some hacking around with the wireless to get it to net-install.

---

### Post by tuxcantfly on 2008-06-01
> **mendieta said:**
> Ok, I looked at the source code, I think I have a clue, hope someone can give me a hand and confirm I am right.

I have two drives:

/dev/sda -> Xandros install on the eeepc internal ssd 
/dev/sdb -> an external sdhc where I want to net-install Kubuntu

I want to modify the existing grub in /dev/sda. I am running unetbootin from Xandros  (/dev/sda1). In this case I should use a **hard drive** install and choose "/" as the target, right ? I was choosing "usb" and /dev/sdb, because that's where I will install Kubuntu. But I guess I was wrong, and the disk/partition where you will install your new OS is chosen after you reboot, during the actual install of the new OS, right? 

Graphically, this is what I was doing:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=72345&d=1212267052[/IMG]

And this is what I should be doing, right?: 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=72349&d=1212267929[/IMG]

Thanks in advance!

Second option is what you want to do. However, I'm not sure whether it'll work, since I don't think the eeepc uses standard GRUB as a bootloader (but then again, I don't have an eeepc so I may be wrong). Additionally, whatever few guides on installing Ubuntu/Fedora/etc on the eeepc I've seen have all recommended making a liveUSB first on another computer, then booting from it on the eeepc, so I think there's a reason behind that, though if you do indeed succeed without using a USB drive, then that's nice to know.

---

### Post by tuxcantfly on 2008-06-01
> **laxinon said:**
> i`m trying to install Ubunto with Unetbootin.
the program starts but when at stage 2 (extracting) it stopped responding, this happen at the 7th file extract.
i tried to rerun it but nothing.
i suspect that it has something to do with C++ runtime that is not working properly .
the laptop i`m trying to install on has win XP SP2 but has many buges

The 7th file, filesystem.squashfs, is almost 700 MB. It'll take a while to extract, just be patient. If you need to confirm that it's progressing with the extraction process, just go to wherever it says the destination is, and periodically refresh and check the file properties; the file size should gradually be growing towards 700 MB.

---

### Post by tuxcantfly on 2008-06-01
> **defenestratos said:**
> I download the file and make it executable. I double click on it. Nothing happens. Is it because it has no extension? I use 64 bit is that why?

The latest version is statically linked, so technically it should run without any external libraries, but since you're using Ubuntu 64-bit, try installing the package "ia32-libs" (which will give you 32-bit libraries for running 32-bit applications) and try again.

Also try running it from the command line if it doesn't run even with ia32-libs installed.

Also perhaps use the command "chmod +x ./unetbootin-linux-216" prior to running it, in case it wasn't made executable when you tried setting the permissions via the GUI.

---

### Post by mendieta on 2008-06-01
> **tuxcantfly said:**
> Something's wrong with your distribution's PATH. For the first issue, vol_id isn't in your path (I don't search for vol_id specifically in any directory, I use "whereis", which searches for binaries in your PATH, to locate it), and I'd rather not start hardcoding directories for every distribution that doesn't have its PATH set right (though I suppose I could try making an exception for eeepc's Xandros). Could you confirm that the command "whereis vol_id" doesn't return the correct path to the binary?


Correct, it doesn't find it (I also tried this manually during my tests, oddly, it only finds the manpage, I had to look at the deb package to locate the binary). I also have mixed feelings about hardcoding stuff. Tough call.

> 
As for the reboot issue, apparently the command "init" isn't in your PATH either, probably the same issue, since I'm using the standard command "init 6" for rebooting.

Since I don't have an eeepc, could you post where the "init" binary for eeepc is, and could you confirm that running the command "init 6" manually as root doesn't reboot the computer (which is what I'm assuming is causing the reboot issue)?


True, it fails with a timeout on /dev/initctl, I tried this too after looking at your code, I just forgot to report, sorry!

> 
As for the rest, if I recall correctly, Ubuntu wasn't fully compatible with the stock eeepc, so you'll probably also need to do some hacking around with the wireless to get it to net-install.

Well, but the eeepc has a built in ethernet card, I should be fine using the wired connection to my home router (which provides dhcp). 

Many, many thanks!

---

### Post by mendieta on 2008-06-01
> **tuxcantfly said:**
> The latest version is statically linked, so technically it should run without any external libraries.

Yes and no, see my earlier post, it seems to link dynamically against libc6, and require libc6 >=2.4. This means, any distro based on debian etch, including the eeepc's xandro's, will have problems. Oh well!

---

### Post by mendieta on 2008-06-01
> **tuxcantfly said:**
> Second option is what you want to do. However, I'm not sure whether it'll work, since I don't think the eeepc uses standard GRUB as a bootloader (but then again, I don't have an eeepc so I may be wrong). Additionally, whatever few guides on installing Ubuntu/Fedora/etc on the eeepc I've seen have all recommended making a liveUSB first on another computer, then booting from it on the eeepc, so I think there's a reason behind that, though if you do indeed succeed without using a USB drive, then that's nice to know.

I'll give it a shot next weekend, I have a feeling it may work. The grub menu.lst is in /bot/grub ... I don't know, we'll see. If it works, I'll try to post a minihowto here in ubuntuforums. I could provide also a binary (the statically linked official one fails).

Also, have you thought of including, as part of the documentation, install guides for the most typical cases ? (from Linux HD, Linux USB, Windows HD, Windows USB) Each guide would have a series screenshots, I think this would save enormous time in  FAQ. Personally, I got confused on how to install. You could ask people to contribute, you seem to have lots of users :-)

One more thing, a whishlist, wouldn't it be nice, in the future (assuming you have time or someone volunteers), to have an interface that is more like a wizard ?

Thanks for all your work!

---

### Post by defenestratos on 2008-06-03
hugo@hugo-laptop:~/Desktop$ ./unetbootin-linux-216
./unetbootin-linux-216: /lib32/libc.so.6: version `GLIBC_2.4' not found (require d by ./unetbootin-linux-216)
hugo@hugo-laptop:~/Desktop$ 

> **tuxcantfly said:**
> The latest version is statically linked, so technically it should run without any external libraries, but since you're using Ubuntu 64-bit, try installing the package "ia32-libs" (which will give you 32-bit libraries for running 32-bit applications) and try again.

Also try running it from the command line if it doesn't run even with ia32-libs installed.

Also perhaps use the command "chmod +x ./unetbootin-linux-216" prior to running it, in case it wasn't made executable when you tried setting the permissions via the GUI.

---

### Post by mendieta on 2008-06-03
> **defenestratos said:**
> hugo@hugo-laptop:~/Desktop$ ./unetbootin-linux-216
./unetbootin-linux-216: /lib32/libc.so.6: version `GLIBC_2.4' not found (require d by ./unetbootin-linux-216)
hugo@hugo-laptop:~/Desktop$

Yes, that's exactly what I was pointing out above.

---

### Post by gothalo on 2008-06-03
Hi.
I am kinda new to linux so I don't know what Im doing. When i ran UNetbootin i choose Xubuntu, went down to install on my hd and clicked OK or watever. Everything went well until after I rebooted. An error message said that it cannot find grldr in all drives. BTW Ive copied the latest menu.lst and grldr in the root of my drive. What did i do wrong??

---

### Post by Grantham on 2008-06-04
Alright.... So I chose Ubuntu 8.04 (Nonlive)and it downloaded and installed fine, but when I rebooted to select 'UNetBootin' right after the boot up/logo screen, it flashed something, hit 'ESC' to go to menu, and if you don't in the 3 seconds it allows me, it flashes some more then my compute restarts.

What's going on?

---

### Post by mendieta on 2008-06-04
> **tuxcantfly said:**
> I'm not sure whether it'll work, since I don't think the eeepc uses standard GRUB as a bootloader (but then again, I don't have an eeepc so I may be wrong). 

Good news, **It worked!** I got to the installer, but aborted for lack of time, I'll fdo it in the weekend. 

In a nutshell: the eeepc uses unionfs to merge a "factory installation", stored in /dev/sda1, and a "user modified partition", /dev/sda2. Unetbootin installs everything in  /dev/sda2, which is not seen by grub by default. What I did was to edit grub on boot, and edit one entry to make it look exactly like the one written by unetbootin in /dev/sda2/ (except for the root, which needs to be the second partition). That's it. 

:-)

---

### Post by Grantham on 2008-06-04
Okay, I let it sit at the 'Booting UnetBootin' Screen for about 5 minutes, and an error popped up.

find --set-root /unetbtin/ubnkern

ERROR 15: FILE NOT FOUND

Ehh... Any suggestions?

---

### Post by mendieta on 2008-06-04
> **Grantham said:**
> Okay, I let it sit at the 'Booting UnetBootin' Screen for about 5 minutes, and an error popped up.

find --set-root /unetbtin/ubnkern

ERROR 15: FILE NOT FOUND

Ehh... Any suggestions?

It looks like the root partition is misspecified, you could try editing the UnetBootin entry in grub, and specify a different root. No idea why this is happening though, maybe you can specify more details (what type of install you are attempting, etc)

---

### Post by tuxcantfly on 2008-06-04
> **Grantham said:**
> Okay, I let it sit at the 'Booting UnetBootin' Screen for about 5 minutes, and an error popped up.

find --set-root /unetbtin/ubnkern

ERROR 15: FILE NOT FOUND

Ehh... Any suggestions?

I presume the installation type is Hard Disk, and that you're running from Windows, on an NTFS filesystem. It's probably some issue with GRUB4DOS; it sometimes fails on certain, generally somewhat fragmented or otherwise corrupted NTFS filesystems. Try copying the installed folders/files (C:\unetbtin, C:\ubnldr*) to your other partitions if you have any. Otherwise, if your computer can boot from USB, try USB drive installation mode (it's more reliable).

---

### Post by tuxcantfly on 2008-06-04
> **mendieta said:**
> Also, have you thought of including, as part of the documentation, install guides for the most typical cases ? (from Linux HD, Linux USB, Windows HD, Windows USB) Each guide would have a series screenshots, I think this would save enormous time in  FAQ. Personally, I got confused on how to install. You could ask people to contribute, you seem to have lots of users :-)

I actually have a few already, I suppose I'll eventually merge their contents into the FAQ:

LiveUSB (Ubuntu): [http://ubuntuforums.org/showthread.php?t=811397](http://ubuntuforums.org/showthread.php?t=811397)
LiveUSB (PCLinuxOS): [http://www.pclinuxos.com/index.php?option=com_smf&Itemid=58&topic=46097.0](http://www.pclinuxos.com/index.php?option=com_smf&Itemid=58&topic=46097.0)
Hard Disk (PCLinuxOS): [http://www.pclinuxos.com/forum/index.php?topic=40364.0](http://www.pclinuxos.com/forum/index.php?topic=40364.0)

As for the others, I'll get around to them eventually

---

### Post by Grantham on 2008-06-04
I'm trying to install Ubunto 8.04 on a new partition (Labeled 'E'), used the NTFS filesystem.

The only folders at C:\unetbtin was the UNetBootin program, which opened right up into the window. I tried setting it to copy to drive E but that wouldn't allow me to... Probably for the better.

Got the full script of sorts it shows me while trying to install on GRUB:

(hd0,0)
Filesystem type is NTFS
partition type 0x7
[linux bzImage, setup=x1e001 size=0x196f78]

Huh. hd0,0... Shouldn't it be something like (hd0,1), referring to the second partition of the first disk, or am I completely wrong? x]

---

### Post by cautha on 2008-06-06
This may have been covered already, but searching the thread didn't turn up anything, so here goes...

I'm attempting to install Debian testing (i386) on my laptop with UNetbootin; I use wireless exclusively on this box, yet the installer doesn't allow for wireless connectivity at the outset. Predictably, DHCP probing fails, and I'm not able to continue.

Is there any way -- or some other tool -- to get the job done, short of burning a DVD? I already tried downloading the full 4GB iso and using that with UNetbootin, but I'm essentially told to insert the DVD into my optical drive.

Alternatively, is there a distro readily installable with UNetbootin that will optionally connect to a wireless network _before_ an FTP install?

Thanks!

Harry

---

### Post by DogTired on 2008-06-10
Using UNetBootin, I'm trying to install Ubuntu on an old Vaio laptop with no CD-Rom.  Windows XP is installed and it has network connectivity.

For the first installation, I installed over the network.  Everything went fine - I was met with several prompts and it installed on a new partition that the Ubuntu installation created.  I played around with Ubuntu for a while and shut down.  After a reboot into Windows I was prompted to remove UNetBootin, which I did.  Subsequent reboots went directly into Windows, with no boot options.  For whatever reason, it seems that Grub did not install.

I tried installing two more times with the same results.  (Definition of insanity: doing the same thing over and over again and expecting different results.)  I then downloaded ISO's of both Ubuntu & Xubuntu and tried installing them.  Same result.

_Now, subsequent installs only install a virtual copy, with no prompts._  Between each installation I have removed UNetBootin when prompted.  My guess is there must be a configuration file left somewhere on C:, but I cannot find it.

This seems to be the same problem that Leefmc was having (posts #385 #391 in this thread).  I haven't seen any others reporting this problem, nor have I seen a response to Leefmc.  Does anyone know why, when using UNetBootin, Ubuntu automatically installs the virtual version and does not allow for a full install?  Might an earlier version of Ubuntu behave differently?

---

### Post by tuxcantfly on 2008-06-10
> **DogTired said:**
> Using UNetBootin, I'm trying to install Ubuntu on an old Vaio laptop with no CD-Rom.  Windows XP is installed and it has network connectivity.

For the first installation, I installed over the network.  Everything went fine - I was met with several prompts and it installed on a new partition that the Ubuntu installation created.  I played around with Ubuntu for a while and shut down.  After a reboot into Windows I was prompted to remove UNetBootin, which I did.  Subsequent reboots went directly into Windows, with no boot options.  For whatever reason, it seems that Grub did not install.

I tried installing two more times with the same results.  (Definition of insanity: doing the same thing over and over again and expecting different results.)  I then downloaded ISO's of both Ubuntu & Xubuntu and tried installing them.  Same result.

_Now, subsequent installs only install a virtual copy, with no prompts._  Between each installation I have removed UNetBootin when prompted.  My guess is there must be a configuration file left somewhere on C:, but I cannot find it.

This seems to be the same problem that Leefmc was having (posts #385 #391 in this thread).  I haven't seen any others reporting this problem, nor have I seen a response to Leefmc.  Does anyone know why, when using UNetBootin, Ubuntu automatically installs the virtual version and does not allow for a full install?  Might an earlier version of Ubuntu behave differently?

You can't resize the partition you booted in live mode from. To do an actual installation to your hard drive rather than booting in live mode, you will have to do one of the following:

* Use the LiveUSB install mode, and boot from the liveUSB drive to perform the installation: [http://ubuntuforums.org/showthread.php?t=811397](http://ubuntuforums.org/showthread.php?t=811397)
* Resize your partitions, using the "Parted Magic" option, prior to installing the Ubuntu live boot mode: [http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora_p4](http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora_p4)
* Select the "Netboot" version under the distribution version selector: [http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora](http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora)

---

### Post by tuxcantfly on 2008-06-10
> **cautha said:**
> This may have been covered already, but searching the thread didn't turn up anything, so here goes...

I'm attempting to install Debian testing (i386) on my laptop with UNetbootin; I use wireless exclusively on this box, yet the installer doesn't allow for wireless connectivity at the outset. Predictably, DHCP probing fails, and I'm not able to continue.

Is there any way -- or some other tool -- to get the job done, short of burning a DVD? I already tried downloading the full 4GB iso and using that with UNetbootin, but I'm essentially told to insert the DVD into my optical drive.

Alternatively, is there a distro readily installable with UNetbootin that will optionally connect to a wireless network _before_ an FTP install?

Thanks!

Harry



> I'm attempting to install Debian testing (i386) on my laptop with UNetbootin; I use wireless exclusively on this box, yet the installer doesn't allow for wireless connectivity at the outset. Predictably, DHCP probing fails, and I'm not able to continue.

Is there any way -- or some other tool -- to get the job done, short of burning a DVD? I already tried downloading the full 4GB iso and using that with UNetbootin, but I'm essentially told to insert the DVD into my optical drive.

First, use UNetbootin to boot into Parted Magic, and use it to resize your partitions: [http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora_p4](http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora_p4)

Then, use a predownloaded liveCD ISO file to install, this way you don't have to connect to the internet for installation. Ubuntu (desktop/livecd version, not alternate/install) would work fine; Debian-Live at [http://debian-live.alioth.debian.org/](http://debian-live.alioth.debian.org/) should also work (I haven't tried Debian-Live with UNetbootin, but given that it boot mechanism is a modified version of casper, which is essentially the same as Ubuntu's, it should also work).

---

### Post by eddo189 on 2008-06-12
hi.  I am trying to install ubuntu to a second hard drive.  I would like to use Unetbootin to do so.  However, when I tell it to put in on a hard disk, it only lets me select C:\ (my main hard drive), and not H:\ (a second hard drive).

 My end goal is to remove my first hard drive altogether, and tuck it away somewhere for safe keeping, and make the H:\ drive my new primary hard drive.  Is this even possible?  Thanks.

---

### Post by cacycleworks on 2008-06-12
> **eddo189 said:**
> hi.  I am trying to install ubuntu to a second hard drive.  I would like to use Unetbootin to do so.  However, when I tell it to put in on a hard disk, it only lets me select C:\ (my main hard drive), and not H:\ (a second hard drive).

 My end goal is to remove my first hard drive altogether, and tuck it away somewhere for safe keeping, and make the H:\ drive my new primary hard drive.  Is this even possible?  Thanks.

My first thought is to just disconnect the 1st drive now and re-try. Would that work?

---

### Post by eddo189 on 2008-06-12
> **cacycleworks said:**
> My first thought is to just disconnect the 1st drive now and re-try. Would that work?

Well..  Since the second hard drive is blank, and i am trying to do this without a CD, i am kinda doubting that option...

---

### Post by mendieta on 2008-06-13
> **eddo189 said:**
> hi.  I am trying to install ubuntu to a second hard drive.  I would like to use Unetbootin to do so.  However, when I tell it to put in on a hard disk, it only lets me select C:\ (my main hard drive), and not H:\ (a second hard drive).

 My end goal is to remove my first hard drive altogether, and tuck it away somewhere for safe keeping, and make the H:\ drive my new primary hard drive.  Is this even possible?  Thanks.

Yes, this is confusing. I am sure netbootin will keep improving and smooth out these little things. Geza (the author of unetbootin) clarified this same question for me (see a few posts above). When you choose hardrive install, it only shows C:\. This will copy temporary files in C: , to allow you to boot from there, and load the installer of the OS you are installing. Next, the installer will ask you where you want to install. At this point, you'll choose H:

Take this with a grain of salt, I only tried it (and worked like this) in a linux to linux install. But I don't see why this should depend on the host and target OS types.

Please do this with care. Cheers!

---

### Post by DogTired on 2008-06-17
> **tuxcantfly said:**
> You can't resize the partition you booted in live mode from. To do an actual installation to your hard drive rather than booting in live mode, you will have to do one of the following:

* Use the LiveUSB install mode, and boot from the liveUSB drive to perform the installation: [http://ubuntuforums.org/showthread.php?t=811397](http://ubuntuforums.org/showthread.php?t=811397)
* Resize your partitions, using the "Parted Magic" option, prior to installing the Ubuntu live boot mode: [http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora_p4](http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora_p4)
* Select the "Netboot" version under the distribution version selector: [http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora](http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora)


@Tuxcantfly - Thanks to your help I finally got Xubuntu installed on my very old laptop with no CD-Rom and minimal memory (128 MB).  As I became more frustrated, I'm fairly certain that for the last 3 installation attempts I selected the Live network installation.  Your response got me to slow down and make one more attempt.

It was a slow, tedious experience for a newb, but it's installed and updated.  (It's surprising to me that Xubuntu is slower at everything than XP on this machine, but that's not an issue for this forum.)

Anyway, thanks for all your work and for all your help.

---

### Post by quinthar on 2008-06-22
(Sorry if this question has already been answered; this is a huge thread and I might have missed it.)

Is there any way to use UNetbootin to install Ubuntu 8.04 in a completely unattended manner by pre-specifying all installation options upfront?  

I have a dedicated Fedora Core 4 server to which my only access is via SSH.  (I can have an admin do basic console work, but anything fancy -- such as installing a new OS -- costs extra.)  What I'd like to do is:

1) Install a command-line version of UNetbootin.

2) Configure Unetbootin to install Ubuntu 8.04

3) Pre-specify all the command-line options such that it'll completely blow away the entire system (reformat all partitions), install with a particular network config (IP, gateway, netmask, etc), install a particular root password, etc.

4) Reboot

5) Log in a while later using SSH and the new root password and find a clean Ubuntu install.

If something gets screwed up and the system dies that's fine as it doesn't cost anything to have an admin re-image the machine back to it's base (Fedora Core 4) specifications.

Any ideas?  If not with Ubuntu, can this be done for Debian?

Thanks!

-david

----------------------------------------------------------

**Edit**: Ok, it looks like the way I would do this is to pass a boot parameter to the installer specifying a preseed file:

[http://d-i.alioth.debian.org/manual/en.i386/apbs02.html](http://d-i.alioth.debian.org/manual/en.i386/apbs02.html)

So it would appear my questions really are:

1) Can I run unetbootin from the command line on a headless system?  The webpage and screenshots look like it needs a GUI.

2) Can I specify additional boot options when installing a full distribution or disk ISO?  Or do I need to remaster my own ISO?

3) Is there any way to have unetbootin download the ISO straight into RAM after rebooting such that it can blow away all partitions and reformat the entire hard drive?  Or do I need to put some (possibly remastered) ISO into a partition that the preseed file is configured to not destroy?

Thanks!

-david

---

### Post by tuxcantfly on 2008-06-23
> **quinthar said:**
> (Sorry if this question has already been answered; this is a huge thread and I might have missed it.)

Is there any way to use UNetbootin to install Ubuntu 8.04 in a completely unattended manner by pre-specifying all installation options upfront?  

I have a dedicated Fedora Core 4 server to which my only access is via SSH.  (I can have an admin do basic console work, but anything fancy -- such as installing a new OS -- costs extra.)  What I'd like to do is:

1) Install a command-line version of UNetbootin.

2) Configure Unetbootin to install Ubuntu 8.04

3) Pre-specify all the command-line options such that it'll completely blow away the entire system (reformat all partitions), install with a particular network config (IP, gateway, netmask, etc), install a particular root password, etc.

4) Reboot

5) Log in a while later using SSH and the new root password and find a clean Ubuntu install.

If something gets screwed up and the system dies that's fine as it doesn't cost anything to have an admin re-image the machine back to it's base (Fedora Core 4) specifications.

Any ideas?  If not with Ubuntu, can this be done for Debian?

Thanks!

-david

----------------------------------------------------------

**Edit**: Ok, it looks like the way I would do this is to pass a boot parameter to the installer specifying a preseed file:

[http://d-i.alioth.debian.org/manual/en.i386/apbs02.html](http://d-i.alioth.debian.org/manual/en.i386/apbs02.html)

So it would appear my questions really are:

1) Can I run unetbootin from the command line on a headless system?  The webpage and screenshots look like it needs a GUI.

2) Can I specify additional boot options when installing a full distribution or disk ISO?  Or do I need to remaster my own ISO?

3) Is there any way to have unetbootin download the ISO straight into RAM after rebooting such that it can blow away all partitions and reformat the entire hard drive?  Or do I need to put some (possibly remastered) ISO into a partition that the preseed file is configured to not destroy?

Thanks!

-david

I've answered question 1 at [http://answers.launchpad.net/unetbootin/+question/37109](http://answers.launchpad.net/unetbootin/+question/37109) though I'll repeat it here for interested forum members:

> My older version, located at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) (direct downloads still available at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821) you want the .sh version of the package titled "UNetbootin Ubuntu 8.04") was actually capable of being run from command-line, though I scrapped that functionality since essentially all the users were using the GUI version. However, no I did not implement automatic installation for it, since that would mean different install mechanisms for each distro (preseed for debian-based, kickstart for redhat/fedora, etc). However, if all that's important for you is that you can do it remotely, wouldn't something like X tunneling over SSH or VNC do the job, or maybe virtualize your install environment via XEN or the like and SSH into that?

FYI, if you wanted to prepare your own script to automate this (shouldn't be that hard, all you need to do is add preseed generation functionality to my older .sh version) see [http://bazaar.launchpad.net/~gezakovacs/unetbootin/devel-new/annotate/geza0kovacs%40gmail.com-20080623062449-j05wya2zelowy60l?file_id=ubninst-20071028054253-vywnty97hfajhph9-17](http://bazaar.launchpad.net/~gezakovacs/unetbootin/devel-new/annotate/geza0kovacs%40gmail.com-20080623062449-j05wya2zelowy60l?file_id=ubninst-20071028054253-vywnty97hfajhph9-17) you'll probably be most interested in the "tohost" install mode section. As for info on generating preseed files (which you can automate the installation and pass username/password/etc configuration with) see [http://help.ubuntu.com/8.04/installation-guide/i386/preseed-using.html](http://help.ubuntu.com/8.04/installation-guide/i386/preseed-using.html) and [http://wiki.debian.org/DebianInstaller/Preseed](http://wiki.debian.org/DebianInstaller/Preseed)

Also, since you're doing this on remote servers, I'd suggest simply setting up an FTP server and do a local FTP-install from that, rather than using an ISO file, you can find info about that at [http://help.ubuntu.com/community/Installation/LocalNet](http://help.ubuntu.com/community/Installation/LocalNet) (you'll probably be most interested in the section titled "Advanced: Hands-Off, Preseeded Network Server Install")

As for question 2: edit /boot/grub/menu.lst and you can add kernel parameters after the line titled "kernel", under the UNetbootin section. FYI, on Windows, the file you want is c:\unetbtin\menu.lst, and on a USB drive, it would be the line beginning with "append" in syslinux.cfg.

As for question 3: when you reboot, the RAM is cleared, so I doubt that is possible. Of course, on MS-DOS and perhaps some other ancient operating systems, it was possible to load another OS in place with loadlin.exe, but no modern OS allows you to safely do this. Your best bet would be just automating the FTP install, perhaps on your own local FTP mirror if you have to automate this process on hundreds of computers, as mentioned above; that way you can avoid the partitioning issues you have when you want to reformat the partition you booted off of. I believe various linux distros (PCLinuxOS, Puppy, DSL, Slax, and a few others) have a "copy2ram" or "toram" option that basically does what you want (reboots, then loads ISO into RAM, rather than copying it directly into the RAM and retaining it after rebooting, though the effect is the same), but that functionality was broken in Ubuntu last time I checked. Again, though, if you're doing a massive deployment, setting up a local mirror and doing an FTP install would still likely be the safest bet.

---

### Post by Nate9009 on 2008-06-27
Thanks very much for all your work in making such a useful and concise program!  It's really appreciated !:)

I am trying to install a Live Version of Ubuntu onto my 1GB USB stick using UNetbootin's amazingness. So far I have tried using a previously downloaded .iso file of Ubuntu, as well as letting the program download and install the file itself from the Net.  Everything seems to go fine with no problems or errors, but when I reboot my computer, there is no option in BIOS to boot from my flash drive. (Side note, my computer is running Ubuntu)

I went to another computer that runs Vista and tried booting from USB and was told that the kernel image could not be found.  

Does anyone know what im doing wrong?  The installer was set to the correct location of my USB device and ran correctly (I think...).

---

### Post by tuxcantfly on 2008-06-27
> **Nate9009 said:**
> Thanks very much for all your work in making such a useful and concise program!  It's really appreciated !:)

I am trying to install a Live Version of Ubuntu onto my 1GB USB stick using UNetbootin's amazingness. So far I have tried using a previously downloaded .iso file of Ubuntu, as well as letting the program download and install the file itself from the Net.  Everything seems to go fine with no problems or errors, but when I reboot my computer, there is no option in BIOS to boot from my flash drive. (Side note, my computer is running Ubuntu)

I went to another computer that runs Vista and tried booting from USB and was told that the kernel image could not be found.  

Does anyone know what im doing wrong?  The installer was set to the correct location of my USB device and ran correctly (I think...).

Concerning the lack of an option in the BIOS to boot from the flash drive, that's a BIOS issue (consult your motherboard's manual, you may just find some useful info on USB booting). However, since you're running Ubuntu on that computer, you should be able to boot, using the following steps:

Let GRUB (the Ubuntu bootloader) start up, but don't let it boot Ubuntu yet. Instead, press ESC if needed to get to the boot menu (may be unnecessary), then press "c" to get to the grub command line.

Then, on the GRUB boot menu, enter the following commands:

```
root (hd1,0)
chainloader +1
boot
```

That should let your Ubuntu computer boot from the USB drive. Note that the device after root may not necessarily be (hd1,0) depending on your hard drive configuration; try different numbers for the first one if that one doesn't work; you can start typing "root (hd" and press TAB multiple times and it'll list the possible devices.

That issue on the Vista computer booting from USB (you did this straight from the BIOS boot menu I presume?) is strange, though. Are there the 2 files "ubnkern" and "ubninit" in the root directory of the USB drive, with sizes 1.8MB and 7.5MB (for 8.04) respectively? What operating system did you run UNetbootin from (Windows or Ubuntu, which version of each)? When you re-run UNetbootin on that Vista computer, do you get the same issue?

---

### Post by Nate9009 on 2008-06-28
> **tuxcantfly said:**
> Concerning the lack of an option in the BIOS to boot from the flash drive, that's a BIOS issue (consult your motherboard's manual, you may just find some useful info on USB booting). However, since you're running Ubuntu on that computer, you should be able to boot, using the following steps:

Let GRUB (the Ubuntu bootloader) start up, but don't let it boot Ubuntu yet. Instead, press ESC if needed to get to the boot menu (may be unnecessary), then press "c" to get to the grub command line.

Then, on the GRUB boot menu, enter the following commands:

```
root (hd1,0)
chainloader +1
boot
```

That should let your Ubuntu computer boot from the USB drive. Note that the device after root may not necessarily be (hd1,0) depending on your hard drive configuration; try different numbers for the first one if that one doesn't work; you can start typing "root (hd" and press TAB multiple times and it'll list the possible devices.

That issue on the Vista computer booting from USB (you did this straight from the BIOS boot menu I presume?) is strange, though. Are there the 2 files "ubnkern" and "ubninit" in the root directory of the USB drive, with sizes 1.8MB and 7.5MB (for 8.04) respectively? What operating system did you run UNetbootin from (Windows or Ubuntu, which version of each)? When you re-run UNetbootin on that Vista computer, do you get the same issue?

Thanks for the suggestion,  I'm going to try the BIOS commands right away!

I initially ran UNetbootin from Ubuntu, which is updated and recent.  Although the two files you mentioned that should be on the flash drive are not there.  The only file present is "ldlinux.sys" ?  Would this be a installation problem?  

As for the Vista error, yes I booted (or tried to) from the BIOS menu.  And got a error that said something along the lines of "Cannot find the Kernel image.  Followed by a "Boot:"  I am using Gutsy on my Ubuntu computer and am not sure about the Vista PC. (it was my buddy's)

---

### Post by tuxcantfly on 2008-06-28
> **Nate9009 said:**
> Thanks for the suggestion,  I'm going to try the BIOS commands right away!

I initially ran UNetbootin from Ubuntu, which is updated and recent.  Although the two files you mentioned that should be on the flash drive are not there.  The only file present is "ldlinux.sys" ?  Would this be a installation problem?  

As for the Vista error, yes I booted (or tried to) from the BIOS menu.  And got a error that said something along the lines of "Cannot find the Kernel image.  Followed by a "Boot:"  I am using Gutsy on my Ubuntu computer and am not sure about the Vista PC. (it was my buddy's)

In that case, the ISO file wasn't extracted. Did you have the package p7zip-full installed; it's required for ISO file extraction? Install it if you haven't already done so.

---

### Post by Nate9009 on 2008-06-28
I think I've run into a bit of a wall.  p7zip-full was installed before I ran UNetbootin.  Also, I tried using a already extracted .iso  file downloaded straight from the Ubuntu website (the same file UNet download when the distribution option is chosen).

I ran :

```
sudo apt-get install p7zip-full
```

just to make sure it is indeed installed, which it was.

P.S I'm about to harm my flash drive, its proving to be very frustrating.

P.P.S  The USB drive in question is a 1GB PNY Attache

P.P.P.S Does UNetbootin have a verbose/debugging option?  That would surely help! :D

---

### Post by tuxcantfly on 2008-06-28
> **Nate9009 said:**
> I think I've run into a bit of a wall.  p7zip-full was installed before I ran UNetbootin.  Also, I tried using a already extracted .iso  file downloaded straight from the Ubuntu website (the same file UNet download when the distribution option is chosen).

I ran :

```
sudo apt-get install p7zip-full
```

just to make sure it is indeed installed, which it was.

P.S I'm about to harm my flash drive, its proving to be very frustrating.

P.P.S  The USB drive in question is a 1GB PNY Attache

P.P.P.S Does UNetbootin have a verbose/debugging option?  That would surely help! :D

Try re-running UNetbootin from another computer (or your Windows install), if you have access to one, then. I just re-tested creating a liveUSB drive from an Ubuntu 7.10 iso file from a fresh 7.10 installation and it worked perfectly, so I'm getting the feeling the issue's on your side. Are you specifying the correct USB drive in the drop-down box on the bottom-right? I don't quite understand what you mean by "already extracted" iso file; the Ubuntu iso files aren't compressed; you just specify ISO file itself to UNetbootin. Is the ubuntu iso file you downloaded named "ubuntu-7.10-desktop-i386.iso"? Have you checked its md5sum for integrity [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) it may be corrupted.

As for the verbose/debugging mode, try running it from command-line, using:

```
sudo ./unetbootin-linux-235
```

---

### Post by soritong on 2008-06-29
I installed Linux Mint using unetbootin and everything seemed to go well. I installed it on my third hard drive.

However, when I boot, I dont get the option to go to Linux. It just goes striaght to Windows. I've changed the boot order in the BIOS but it still just goes into Windows.

i cant see the drive anymore in windows so I assume its been partitioned correctly already. is my install hosed up? since the windows and linux are on seperate drives, im guessing its an issue with the boot loader.

any way to fix this?

---

### Post by andrebrait on 2008-07-01
Version 2.35 for Windows crashes when extracting Linux Mint 5.0 R1 ISO. Version 2.29 works fine.

Please, add support for OpenSuSe 11.0 =D

---

### Post by tuxcantfly on 2008-07-03
> **andrebrait said:**
> Version 2.35 for Windows crashes when extracting Linux Mint 5.0 R1 ISO. Version 2.29 works fine.

Please, add support for OpenSuSe 11.0 =D

How/When does it crash while extracting? Does it simply hang, does the window disappear, or do you get the Microsoft Send Error Report dialog? Which file is it extracting when it crashes? Do you get the same issue when extracting the Ubuntu 8.04 desktop ISO or another ISO on that version? What is your target install media, Hard Disk or USB Drive? What Windows version are you on?

@soritong: How did you install it on your third hard drive? Did you simply create a LiveUSB, boot from it, and run the Linux Mint installer from it, or did you use another approach? If it booted from the LiveUSB fine, and you used the Mint installer and it failed at installing on the third hard drive, then the issue is with the Mint installer itself; try asking on the Mint forums about it then.

---

### Post by dvanex on 2008-07-20
Hello, my windows operating system was messed up during a power outage and I'm thinking of using Linux as an alternate OS. I am currently running off a feisty installation cd and have been trying to do a usb install of hardy (since I have no dvd burner). I've tried everything and have always gotten errors about kernel images and was wondering if someone with a working usb install could help me out. It looks like the only really large file that would be on the usb is filesystem.squashfs (inside the casper folder) so maybe someone could upload the rest of their setup in a .zip or .7z to rapidshare or some other website and post a link. Then people having trouble could just substitute their filesystem.squashfs and see if they can get it to work. Thanks in advance.

---

### Post by tad1073 on 2008-07-22
I dl'd unetbootin to my desktop chmoded it then ran it. I am installing arch to / but when I reboot and select unetbootin from grub I get error 15 file not found.

I want to install it to /media/disk which is partioned from /mnt/sdc1 but the only time I am offered a selection to install to is when I select usb which I do not have usb drives.

---

### Post by scrime on 2008-07-25
This is very cool but I have a problem.  I have a PC, with no cd-rom, usb boot, ability for second hdd or floppy. I want to install Ubuntu on it, so I dl´d the ubuntu-8.04.1-alternate-i386.iso and inserted the drive into another PC installed Windows in a small partition, ran this UNetbootin and selected the ISO on my flash drive.  I inserted the drive back into the PC, when it boots selected UNetbootin boot option, installation is good until it realizes I don have a cd-rom and won´t let me continue.  Any ideas?  Should I have copied the ISO to the Windoze drive, it seemed to me like it extracted the necessary files to the drive already.

---

### Post by JacquiG on 2008-07-27
> **tuxcantfly said:**
> What portion exactly are you referring to as "UNetbootin itself"? If the application itself (aka on Windows) isn't starting up, try running it from the command line, see if it generates any output and post it. If it does indeed complete but GRUB4DOS (the bootloader) fails, it usually outputs error messages, write them down and post them.

Anyhow, I haven't tested on Win9x in a while, since I don't have ready access to Win9x, so some portions may be broken (it's probably due to the Unicode support for non-US users I included in UNetbootin, which Win9x doesn't support, since non-US users far outnumber the <1% of the population still using Win9x), but since you said that 180 worked, you can still get the older releases at [http://sourceforge.net/project/showfiles.php?group_id=222386&package_id=268713](http://sourceforge.net/project/showfiles.php?group_id=222386&package_id=268713) and the really old releases at [http://sourceforge.net/project/showfiles.php?group_id=198821](http://sourceforge.net/project/showfiles.php?group_id=198821)

And if your old computer happens to support booting from USB, you can always just create a bootable DSL/TinyMe USB drive from another computer and boot it on the computer running Win9x.

If that isn't an option, you can always do the job manually; download [ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/dsl-4.3-initrd.iso](ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/dsl-4.3-initrd.iso) and use 7-zip [http://www.7-zip.org/](http://www.7-zip.org/) to extract out the files "linux24" and "minirt24.gz" and supply those as the "kernel" and "initrd" files to UNetbootin, and under the "options" section type in whatever comes after APPEND in "isolinux.cfg", which is:

```
ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=791 initrd=minirt24.gz nomce noapic quiet BOOT_IMAGE=knoppix
```


:(
Hi, I also have a Toshiba Portege and have been having a b&*^# of a time (ever) getting an OS on it. I currently a working XP installation. I've been able to frugal install Puppy but have problems with the video and have not gotten it to work beyond working the command line.

I started looking to DSL and (think) I've been able to boot with a floppy that can see my pcmcia cd but when I run the install DSL returns "Can't find KNOPPIX filesystem'. I thought this was unique to possibly the boot floppy and cd combo.

I've installed UnetBootin, selected DSL as distibution, it downloaded, extracted, prompted me for reboot. I select UnetBootin from the boot menu. GRLDR loads, Booting Unetbootin, sees my hdd and filesystem. I then end up at a screen with the penguin and a flashing cursor. Nothing more, disk activity or anything just a flashing cursor.

I followed the instructions above for a manual install. Got to the penguin, Welcome To DSL - then the same error message from above: "Can't find KNOPPIX filesystem."

:confused:
Any ideas how I can get a working linux distro on my laptop? Please! Preferably w/o USB/CD/DVD, etc. I"ll consider floppy boot assist. I want to wipe out WinXP but not until I 'KNOW' I've got a working linux install and am confident I'll have methods of re-installing (Linux) if things go south.

Please let me know if there is anything else I tell you that might help...thanks.

Jacqui

---

### Post by Sef on 2008-07-27
> This is very cool but I have a problem. I have a PC, with no cd-rom, usb boot, ability for second hdd or floppy. I want to install Ubuntu on it, so I dl´d the ubuntu-8.04.1-alternate-i386.iso and inserted the drive into another PC installed Windows in a small partition, ran this UNetbootin and selected the ISO on my flash drive. I inserted the drive back into the PC, when it boots selected UNetbootin boot option, installation is good until it realizes I don have a cd-rom and won´t let me continue. Any ideas? Should I have copied the ISO to the Windoze drive, it seemed to me like it extracted the necessary files to the drive already.

Check the [Server and Network Installations]("https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD").

---

### Post by theBrettman on 2008-08-06
Hi, I have a thinkpad 240x which is kind of old (P3 500MHz, 192MB) and it doesn't have a cdrom because of its size nor does it support booting from usb. I'm limited to floppy and network installs. So I found Unetbootin. I installed debian and then downloaded Unetbootin. It told me when downloading that it doesn't have a program to open it and asked if I want to download it anyway. I download it and then change the properties so I can execute and I dbl click it and it does NOTHING! So I try the wget way: wget $unetbootin.deb and it says: Resolving unetbootin.deb... failed: Name or service not known. It seems debian doesn't want me to have fluxbuntu! Now what do I do?

---

### Post by Vista H8TR 4 EVA on 2008-08-14
Thank You So Much For Making This I Tried MUBI But It Was Taking Litterally 2 Days.  And Beileve Me It Was Not The Computer.  This Took 24 Minutes Just Like It Would Of If It Were The Ubuntu CD Itself.  Great Job.:)

---

### Post by nooby on 2008-08-16
JacquiG, have you tried puppy linux. I failed to get DSL going but 
puppy worked on my system. 

[http://www.puppylinux.org/]("http://www.puppylinux.org/")

---

### Post by jaydoubleyou on 2008-08-18
> **scrime said:**
> This is very cool but I have a problem.  I have a PC, with no cd-rom, usb boot, ability for second hdd or floppy. I want to install Ubuntu on it, so I dl´d the ubuntu-8.04.1-alternate-i386.iso and inserted the drive into another PC installed Windows in a small partition, ran this UNetbootin and selected the ISO on my flash drive.  I inserted the drive back into the PC, when it boots selected UNetbootin boot option, installation is good until it realizes I don have a cd-rom and won´t let me continue.  Any ideas?  Should I have copied the ISO to the Windoze drive, it seemed to me like it extracted the necessary files to the drive already.

I have the same problem - I have an old laptop with a floppy drive & USB port (non-bootable) but no CD or network capability. I've tried installing a few distros using Unetbootin but most (including the alternate install of Xubuntu) threw their toys out of the pram when they realised there was no CD drive. The live CD is so slow it's unworkable (it's slow enough on a new-ish PC, on a PII laptop with 128MB of memory, forget it) and the only distro I've managed to get on there is Puppy, which is OK, but I'd prefer Ubuntu or one of its derivatives (preferably Xubuntu as I think it would be that bit faster).
Would also welcome any ideas!

---

### Post by Infra on 2008-08-19
Same problem here. Can't install from USB if I try to use the alternative cd. I need the alternative cd to install Ubuntu into a LVM on my EEE PC.

Anyone found any "fix" for this?

---

### Post by scrime on 2008-08-25
> **Sef said:**
> Check the [Server and Network Installations]("https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD").

Thanks Sef, I finally have it working, it was easy in the end although it took a huge amount of determination to get it to work.  I was obviously doing something wrong.

The only way I could get it working was this method [https://help.ubuntu.com/community/Installation/LocalNet#Basic:%20Hands-On%20Interactive%20Network%20Server%20Edition%20Install]("https://help.ubuntu.com/community/Installation/LocalNet#Basic:%20Hands-On%20Interactive%20Network%20Server%20Edition%20Install").  I could not get Bootp working.

The way I installed Ubuntu in the end was to create a bridged VM of Ubuntu server, installed Apache, DHCP3 and tftpboot.  Modified the nessesary files.  Sounds easy, took 2 solid days of effort, although now that I know what I was doing wrong I could do it in my sleep in about an hour.

Thanks again.
Mark.

---

### Post by Kazuki Mishima on 2008-08-25
Hello. I think UNetbootin is an awesome idea, but for some reason it doesn't seem to work correctly with my hard disk. I chose to install Ubunutu 8.04 NetInstall using the Hard Disk option. Although my hard disk has two partitions (one running Windows XP and the other holding Windows backup information), only one drive option appears when I chose the "Hard Disk" option and the "Show All Drives" option becomes unselectable. When I proceed with the installation and reboot, my BIOS boots Windows XP as normal rather than presenting the option to boot the Ubuntu installer. I've tried the USB installer, but my BIOS seems incapable of booting from a USB drive. Also, my CD burner is dead.

If you have any suggestions, I would be grateful. My Windows XP desktop (which would not contain Windows except that I share it with family members) has been prayed upon by a host of malware masquerading as "Anti-virus" and "Anti-spyware" applications and I'm anxious to establish Ubuntu Linux as another boot option and backup some files to a separate partition before I try to re-install Windows.

Thank you for UNetbootin and any advice you can give.

---

### Post by gaspx on 2008-08-25
> **Kazuki Mishima said:**
>  ..only one drive option appears when I chose the "Hard Disk" option and the "Show All Drives" option becomes unselectable. When I proceed with the installation and reboot, my BIOS boots Windows XP as normal rather than presenting the option to boot the Ubuntu installer.


Bare in mind that I only just started using UNetbootin 2 hours ago to solve a problem of mine.

The 'Show All Drives' option will become disabled when using your Hard Disk to store the downloaded files. This is (I think) because it wants to store the files to the *bootable* partition of your drive (which is usually C:\)

For my installation, I firstly downloaded the ISO from Ubuntu (ubuntu-8.04.1-desktop-i386.iso) and copied that to the C:\ drive.

Then use UNetbootin (o) Diskimage option, and specify the ubuntu ISO that you downloaded and put on C:\

The Hard Disk option will only give you the booted partition, so choose C:\

Once you have clicked OK, it will start to extract the Ubuntu installer files from the ISO and you will see new folders created and new files on your C:\ drive.

Upon reboot, you should then see another option to boot from UNetbootin.

Hope that helps!

---

### Post by ranger_cole on 2008-08-28
Can you use this program to install a version of linux on an external usb drive that currently is only used for storage and has no os installed?

---

### Post by BeautyandSong on 2008-09-01
I'm trying to install Xubuntu using unetbootin. At first I was trying to download 8.10, but it would quickly finish without Downloading anything. Even when I tried to reboot my computer, it would simply reboot normally and load my current OS. So I tried 8.04 instead and it actually took some time to download some files but when I rebooted by computer it did the same thing, it rebooted normally and it didn't do anything. 

Not sure what's going on. I'm running Linux Linpus Lite on an Acer Aspire One. A friend of mine says I don't have Grub installed, but if I go on Yumex, it says it's there. So I don't know what's going. Any help would be appreciated. :confused:

---

### Post by Asem on 2008-09-04
Hi every one

i try to install Ubuntu 8.04 using unetbootin hard drive method
but after choosing the keyboard layout and location the installer say that the there is no cd in the drive.

please can any one help me by pointing out what may have done wrong.

---

### Post by minhmeoke on 2008-09-10
@ranger_cole:
You could try partitioning the USB disk using parted magic. Then you should be able to perform a LiveUSB or full install to the new partition with UNetbootin.

@BeautyandSong, Asem:
The downloaded .iso disk image may have been corrupted. You could try redownloading from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) for ubuntu, or [http://xubuntu.org/get](http://xubuntu.org/get) for xubuntu, and then select the "diskimage" option in UNetbootin to use the .iso.

---

### Post by Kibagari on 2008-09-12
I've got a few issues with my current 8.04 install (graphics mainly, along with a problem with loading my panels). I also have another problem- my Cd/dvd drive is busted. This has led me to become very frustrated in my search to reinstall 8.04 so that everything can be copacetic again. 

EDIT: I forgot to mention that I'm running on AMD-64, which apparently Lubi doesn't support?

I tried using unetbootin on a Windows computer first to try to just make a LiveUSB, but when I tried the finished product on my computer, it said that there is no operating system on the drive. So I downloaded unetbootin onto this computer, found that my system has no idea what to do with the bin file that is the linux version of unetbootin, so I used the Windows version under WINE- still the same response.

All my files are backed up on another system at the moment so that I can just wipe the hard drive entirely. Is there a way to finagle this USB drive, or am I better off using LUBI and then LVPM?

And were I to use the LUBI->LVPM method of installing to a permanent partition, would I be able to wipe my drive entirely and install that virtual partition as the main OS as if I were installing from a LiveCD/LiveUSB and using the entire drive?

Sorry for the questions and the wall of text, I'm simply very confused about how all of this is supposed to happen, and my research seems to have proven a little fruitless.

---

### Post by mio75 on 2008-09-26
Hi,

I try to install ubuntu with unetbootin but when I reboot my pc(after finishing setup) nothing happen I can't boot on ubuntu. I don't know why

??

---

### Post by marcus01 on 2008-09-26
Hi, I'm new here and new to Ubuntu Linux. I'm trying to convert my desktop (winXP) to ubuntu but I'm having some trouble with it. I don't have a cdrom drive and so I followed the instructions here but when I tried installing it I'm stuck at the cdrom detection/failed to mount something something.

Note: I do not have a cdrom drive available in my PC
Here's a brief steps I did:
1. followed the instructions from here: [http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)
2. after booting from the usb and proceed with the installation, im stucked at "failed to mount cdrom"
3. Followed the steps below from: [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial/)

Installing Ubuntu 8.04 to the USB flashdrive via Windows: 

Download and launch Ubuntup8.exe, a Ubuntu8 folder is created 
Copy your Ubuntu 8.04 ISO to the Ubuntup8 folder 
From the Ubuntup8 folder, click fixu.bat and follow the onscreen instructions 
Once the fixu.bat script has finished, navigate to the new USB-Ubuntu folder inside the Ubuntup8 folder 
Copy all of the files from "within" the USB-Ubuntu folder to the "root" of your flash drive (not to a subfolder) 
Restart your PC and set your BIOS or Boot Menu to boot from the USB device 
If all goes well, you should be able to Run Ubuntu in Persistence Mode saving changes.

It just sits on a screen saying verifying dmi pool data.

Need your advise badly. Thanks in advance.

Update: this has been resolved. Seems like I used an alternate iso download instead of the livecd.

---

### Post by billgoldberg on 2008-10-10
I'm trying to install 8.10.

I have an external hdd with two partitions.

I've set the second with a boot flag and let unetbootin to it's job.

When booting it doesn't actually do anything, it just see a black screen and it stays that way untill I hard reset the machine.

Any help?

---

### Post by volneilo on 2008-10-12
Hmmm... got a problem too.. Installed Unetbootin in order to create a live USB with Puppy Linux. Carelessly I sent the installation to my Windows partition instead of the USB flash drive one... Now, every time I choose Windows in the GRUB menu, it loads Puppy. I've checked and confirmed that Windows installation is already there, but inaccessible. I've made many attempts to restore GRUB, including re-writing MBR, but it always points to Puppy instead of Windows... Could someone help me? Oh, and excuse me for the poor english... I'm from Brasil.
Thanks in advance! :)

---

### Post by Natanael_L on 2008-10-22
I'm too lazy to read the entire thread, so...:
 
Does dual boot work with this? I already have Vista (pre-installed) and Ubuntu (installed from LiveCD), so if I install Fedora (or any other distribution), are Fedora going to be added to my OS boot list in GRUB?
Currently GRUB is started when i boot my laptop, and it shows a list of some Ubuntu boot alternatives and a "default" Vista boot alternative.
Will I see Fedora at the end of that list if I use this for Fedora?
 
I really want to know, please answer soon.

---

### Post by notwen on 2008-11-09
I'm trying to re-install Windows XP on my new Dell Inspiron Mini 9.  I created a iso of Dell's Windows XP re-installation disc using the dd command and have successfully put it onto my USB drive, but when I boot from USB the normal Unetbootin screen comes up w/ the Default option and then continues to loop the 10sec countdown.  Any ideas and/or suggestions?  =]

In the end I'm wanting to dual-boot XP and Ubuntu on the mini9.

---edit---
Looking back, there is no mention of Windows support w/ Unetbootin? Is there any reason it "shouldn't" work? =x

---

### Post by MaindotC on 2008-11-11
I created a bootable USB using the current nightly build .iso from cdimag.ubuntu.com.  I booted my laptop using the USB drive and it booted just fine - even works w/ my wireless card.  When I download and install updates like the kernel upgrade, they're not saving (thought this was the point of a nightly build) and if I connect to a wireless network and store the network key in a keyring, that also isn't saved when I reboot w/ the USB drive.  How can I save updates and settings to the USB drive?

---

### Post by minhmeoke on 2008-11-22
@Kibagari: If the system reports no operating system on the drive, then either the installation failed completely (this should give you a BIOS Error) or your GRUB menu.lst is wrong (this should give you "Grub Error 15 File Not Found"). Also note that files downloaded in Linux are not executable by default, so you will have to manually set the file to executable with the command: "chmod +x unetbootin*"

@mio75, billgoldberg, volneilo: You will have to edit the GRUB menu.lst, there should be instructions for doing that in other sections of this forum.

@Natanael_L: The operating system installed by UNetbootin is exactly the same as the one installed by CD, so dual boot will work fine. Fedora will chain-load the boot menu by creating the default Fedora boot menu and adding an entry for Ubuntu. If you select the Ubuntu entry then the original Ubuntu menu appears, and from here there should be an option to boot Windows. If you want to put all the options into one menu, then you will have to edit the GRUB menu.lst.

@notwen: UNetbootin only works with Linux/BSD installations, since *nix and Windows boot/installation are very different. To create a Windows liveusb you can try using BartPE [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/) . A CD-less reinstallation is harder, if you can access the windows partition, then you could copy the i386 folder over to the USB drive, and run "winnt" from command prompt to start installation.

@strAlan: This thread is for hard-drive installations; there is a separate thread for usb-drive installations: [http://ubuntuforums.org/showthread.php?t=811397](http://ubuntuforums.org/showthread.php?t=811397) . To save data on the USB drive ("persistent" rather than "liveusb" install) follow the steps in this post: [http://ubuntuforums.org/showthread.php?p=6106470#post6106470](http://ubuntuforums.org/showthread.php?p=6106470#post6106470) . You should also edit syslinux.cfg and add "persistent" to the end of the "append" line, as shown here: [http://ubuntuforums.org/showpost.php?p=5089854&postcount=4](http://ubuntuforums.org/showpost.php?p=5089854&postcount=4)

---

### Post by theDaveTheRave on 2008-11-25
Hi all,

I'm performing the install as I type, obviously on another terminal!

so far... for ubuntu. Grab the appropriate debian windows installer from here
[URL="http://unetbootin.sourceforge.net/"]
http://unetbootin.sourceforge.net/[/URL]

downloaded and ran the file.

Selected ubuntu from the list and then the <netInstal> that was appropriate for my machine (in this instance an AMD dual core 64 bit).

At the bottom of the installer window is the location for the instalation, I want a "true" dual boot instal, and hence selected the c:\

I was then asked to reboot.

I had 2 options in my boot loader... one for the original XP and one for the "unetbootin".

I've now followed what looks like a "normal" ubuntu setup, however, it hasn't found my XP install and offered to dual boot... is this correct?

I've had a quick hunt on the forums, but nothing is telling me where I should go from here. Please help, I'm getting exceedingly anoyed at not having a Ubuntu desktop on my works pc!

David

---

### Post by SukiSuki on 2008-11-25
I'm new to all of this..

I tried unetbootin and, to make a long story short, I made a similar mistake to the one about the boot flag on[ [COLOR="Blue"]_this page_[/COLOR]]("https://help.ubuntu.com/community/Installation/FromWindows") so now all I can get is my bios and "Error Loading Operating System". 

I've backed everything up on an external drive, so I'm not worried.

So the current situation is: The bios doesn't seem to support booting from USB (it's not in the listed boot sequence options, but I'll try to make a bootable USB drive tomorrow anyway). The CD drive is busted, or I wouldn't have been using Unetbootin. The floppy drive probably works. I'm writing this from my girlfriend's mac...

So, I think the answer is for me to get a replacement CD drive; (this is kindof off topic) but if anyone has any ideas on how to move the boot flag back to a bootable partition I'm open to suggestion. Thanks.

---

### Post by minhmeoke on 2008-12-05
@theDaveTheRave: The installation generated by UNetbootin should be exactly the same as a standard (CD-based) Ubuntu install, so I am not sure why it is not autodetecting the windows partition. Can you post the output of "sudo fdisk -l", and check that there is a Windows FAT32 or NTFS partition present? If fdisk can see the Windows partition, then you should be able to make the windows entry appear by adding an entry to /boot/grub/menu.lst .

@SukiSuki: If you have access to another machine that can write floppies, you could try loading a utility floppy such as BootE [http://boot.everywhere.dk/](http://boot.everywhere.dk/) then set the bootable flag using fdisk. You could also remove the non-booting hard drive and hook it up as a secondary (slave) drive on another unix computer that can read/write the ext3 filesystem (I think MacOSX can do this with  ext2fsx [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/) ), and run fdisk from there. As a last resort, if your do not have any access to any install media and your BIOS supports PXE, then you could boot a minimal environment off of another computer via TFTP and run fdisk there.

---

### Post by heroidi on 2008-12-05
i like this tutorial so i translated it in albanian :D [http://ayih.org/tips_tricks/instaloni_ubuntun_pa_cd_duke_perdorur_unetbootingun-t2844.0.html;msg9466;topicseen#new](http://ayih.org/tips_tricks/instaloni_ubuntun_pa_cd_duke_perdorur_unetbootingun-t2844.0.html;msg9466;topicseen#new) here is a link

---

### Post by xzero1 on 2008-12-05
Please consider adding network install to the search keywords.

---

### Post by newbie2 on 2008-12-06
> **heroidi said:**
> i like this tutorial so i translated it in albanian :D [http://ayih.org/tips_tricks/instaloni_ubuntun_pa_cd_duke_perdorur_unetbootingun-t2844.0.html;msg9466;topicseen#new](http://ayih.org/tips_tricks/instaloni_ubuntun_pa_cd_duke_perdorur_unetbootingun-t2844.0.html;msg9466;topicseen#new) here is a link
hi heroidi... great work...if you want your translation into the latest releases , you read this : [http://unetbootin.sourceforge.net/#translations](http://unetbootin.sourceforge.net/#translations)
;)

---

### Post by jasonuk on 2008-12-24
Hello Ubuntu folks! Just tried to install Ubuntu using UNetbootin on my Dell inspiron 2650 (WinXP SP2) .

Runs through the download, decompress and reboot. Then I get this:

Try (hd0,0): FAT16: No UBNLDR
Try (hd0,1): NTFS5: 3
Try (hd0,2): invalid or null
Try (hd0,3): invalid or null
Try (fd0): invalid or null
Error: cannot find GRLDR in all devices. Press Ctrl+Alt+Del to restart

I can't find anything useful with UBNLDR, and all the other forum posts about GRLDR seem to refer to Wubi - and not unetbootin. I've copied GRLDR from grub and overwritten it as far as I can tell with the latest version. I'm not really sure what to do next - any ideas?

Hope everyone 's having a nice holiday

J

---

### Post by coodtec on 2008-12-28
Installation of Ubuntu 8.10 only consider about CD 	:sad:

---

### Post by theRightNee on 2008-12-30
hey everyone! i am trying to use UNetBootin to install archlinux, and i have the .iso downloaded and everything. Only problem is, after i reboot the machine, there is no option to boot "UNetBootin" as was promised. My HDD is partitioned a bit awkwardly (Ms-Dos on C, and XP on D) so could that be the problem? Thanks!

---

### Post by sockrebel on 2008-12-30
I was installing Ubuntu 8.10 via unetbootin (netinstall) on a laptop also previously running only Ubuntu.

When I boot up the laptop, I get the following error:
```
GRUB Loading stage1.5

GRUB loading, please wait...
Error 17
```

[http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540) says that I should "try defragmenting your hard drive and running "chkdsk /r" " but since Windows isn't on the computer, I don't think that applies.

In this thread [post 284]("http://ubuntuforums.org/showpost.php?p=4207983&postcount=284"), tuxcantfly says
> Unless you were booting UNetbootin off a USB stick (and GRUB got installed to the USB drive not the hard drive due to a bug in Fedora's installer, this occurs on Ubuntu due to a bug in d-i, it may also affect Fedora).

I think this is the case with my Ubuntu install, but haven't been able to find anything else about this bug.  Is there a known workaround when installing?  Any ideas?

thx!

---

### Post by blubaustin on 2009-01-05
what about ppc ubuntu linux.

---

### Post by shrinathk87 on 2009-01-08
> **theRightNee said:**
> hey everyone! i am trying to use UNetBootin to install archlinux, and i have the .iso downloaded and everything. Only problem is, after i reboot the machine, there is no option to boot "UNetBootin" as was promised. My HDD is partitioned a bit awkwardly (Ms-Dos on C, and XP on D) so could that be the problem? Thanks!

Hey, even i had the same problem. I had windows on E:\ and tried installing it. the option to boot is to be edited in the boot.ini file in the C:\ but since windows is in E:\, it dosent accept. i tried editing the boot.ini file, but didnt work. So, basically, i dont think that Unetbootin will work if windows is not on C:\.

Correct me if i am wrong, and if possible, please help us out!

Thanks.

---

### Post by sockrebel on 2009-01-08
> **shrinathk87 said:**
> Hey, even i had the same problem. I had windows on E:\ and tried installing it. the option to boot is to be edited in the boot.ini file in the C:\ but since windows is in E:\, it dosent accept. i tried editing the boot.ini file, but didnt work. So, basically, i dont think that Unetbootin will work if windows is not on C:\.

Correct me if i am wrong, and if possible, please help us out!

Thanks.

I was having problems installing ArchLinux via Unetbootin.  But this method worked fine: [http://wiki.archlinux.org/index.php/Install_from_USB_stick]("http://wiki.archlinux.org/index.php/Install_from_USB_stick")

I hope that works for you.

---

### Post by SnowflakeRV7 on 2009-01-18
Looks like this is a pretty active thread, and someone must have come across the same problem i'm having.  I have two hard disks in my computer, sda and sdb.  I'm currently running Ubuntu 8.10 from sdb, but it has been patched and upgraded so many times (from 6.06) that i'd like to do a fresh install onto sda (keeping my install on sdb just in case).

My current fdisk -l output:
```
rb4@corsair:~$ sudo fdisk -l

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00042f46

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          33      265041   83  Linux
/dev/sda2              34         555     4192965   82  Linux swap / Solaris
/dev/sda3             556       14685   113499225   83  Linux
/dev/sda4   *       14686       14946     2096482+  83  Linux

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003eadd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14759   118551636   83  Linux
/dev/sdb2           14760       14946     1502077+   5  Extended
/dev/sdb5           14760       14946     1502046   82  Linux swap / Solaris
rb4@corsair:~$
```

I have an .iso of the 8.10-desktop image, so I tried using that to create a boot partition on /dev/sda4.  I had to select "USB drive" and select "show all drives" before I could select /dev/sda4 though.  Once that was done, there was no indication in my /boot/grub/menu.lst that anything had changed... I think it's relying on the USB boot capability of my BIOS to take care of that for me.

How can I get it to do an install to /dev/sda4, and make the appropriate entries in my /boot/grub/menu.lst?

---

### Post by devildoc5 on 2009-01-20
I am trying to get unetbootin to work in puppy linux to "upgrade" to ubuntu but seem to be having some problems with the system.  I receive the following error after reboot.  Error 23, then it goes back to grub.  I believe (not sure though) this may have to do with the fact that it states that I need to install util-linux,udev, mtools, and p7-zip.   I am a very VERY recent convert and have no idea how to get these as they are not puppy packages, and have no idea what to do to install them.  Any help would be greatly appreciated.

System is a p3, 10G master HDD, 4G slave HDD with 128 M RAM.

---

### Post by Quin452 on 2009-01-21
Okay, so I've downloaded this same version several times now, and others.

Still, this is the one that seems to be the one I want to install Ubuntu.

So I've got a disk image, ergo, I don't need to download another.
However, do I just stick it on the C drive?
With the past versions, I've always gone to the 'try' ubuntu style, and the install doesn't work (my computer freezes) despite my own iso or the UNB download.

What's going on?

EDIT:  The download seems to download the program itself and not any installer - is this right?

((BTW: my system seems to crash even when using a CD, but only when I have Windows as my OS... tried various cds))

---

### Post by holla on 2009-01-31
I have the exact same problem.
Add to that my CD drive is angry about ubuntu. It is not working while installing ubuntu.
Please post if you get this problem solved

> **SnowflakeRV7 said:**
> Looks like this is a pretty active thread, and someone must have come across the same problem i'm having.  I have two hard disks in my computer, sda and sdb.  I'm currently running Ubuntu 8.10 from sdb, but it has been patched and upgraded so many times (from 6.06) that i'd like to do a fresh install onto sda (keeping my install on sdb just in case).

My current fdisk -l output:
```
rb4@corsair:~$ sudo fdisk -l

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00042f46

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          33      265041   83  Linux
/dev/sda2              34         555     4192965   82  Linux swap / Solaris
/dev/sda3             556       14685   113499225   83  Linux
/dev/sda4   *       14686       14946     2096482+  83  Linux

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003eadd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14759   118551636   83  Linux
/dev/sdb2           14760       14946     1502077+   5  Extended
/dev/sdb5           14760       14946     1502046   82  Linux swap / Solaris
rb4@corsair:~$
```

I have an .iso of the 8.10-desktop image, so I tried using that to create a boot partition on /dev/sda4.  I had to select "USB drive" and select "show all drives" before I could select /dev/sda4 though.  Once that was done, there was no indication in my /boot/grub/menu.lst that anything had changed... I think it's relying on the USB boot capability of my BIOS to take care of that for me.

How can I get it to do an install to /dev/sda4, and make the appropriate entries in my /boot/grub/menu.lst?

---

### Post by ugm6hr on 2009-01-31
> **holla said:**
> I have the exact same problem.
Add to that my CD drive is angry about ubuntu. It is not working while installing ubuntu.
Please post if you get this problem solved

If your BIOS does not allow booting from USB, unetbootin won't change that.

---

### Post by Clueless163 on 2009-04-04
I have an old laptop I want ubuntu installed on, it has no cd-rom or floppy but does have a usb port. Bad thing is that I can't boot from usb. Performing a network install is a bit confusing to me and I'm trying to understand the process. Help?

---

### Post by zivley on 2009-05-21
HELP!

I was trying to see if I can install ubuntu on FC4 using the command line .sh script, so I've downloaded the Ubuntu 8.04.....sh to it and then ran it, after reboot it drops me to the grub> prompt, I tried to do what I've found here in this thread in page 3
```

root (hd0,0)
configfile /menu.lst

```
to no avail, so I tried
```

find --set-root /wubi
kernel /wubi/linux
initrd /wubi/initrd.gz

```
and all I get is file not found errors and so
The problem is I don't have physical access to the server (some 7000 miles separates between us) and I'll be getting there only next week, I'm thinking of trying to make it work somehow.
Can you help??
Thanks,
Ziv

---

### Post by zivley on 2009-05-21
OK, nevermind, I've found it!
I can't explain what went wrong and why I didn't get the menu, but this is what I did, assume I did the installation to /dev/hda1

```

grub> setup (hd0)
grub> rootnoverify (hd0,0)
grub> makeactive
grub> chainloader +1
configfile /boot/grub/menu.lst

```
Voila! I've got into the grub menu where the Unetbootin option is available for boot.
From there I've got directly into the Ubuntu install.
This is a great program!
Thanks!

---

### Post by N700 on 2009-06-30
Could someone explain how, if you install Ubuntu in a blank partition on a Windows machine using UNetbootin, you actually start Linux on subsequent boots?

The documentation says that the bootloader is modified for one boot, and then changed back on the next boot into Windows. So, I'm confused.

I have a Windows machine here with 20GB or so unpartitioned space on the disk that I'd like to install Ubuntu into. Is UNetbootin the best way to go about this?

---

### Post by johnraff on 2009-06-30
I used Unetbootin to install Ubuntu in some spare disk space on a Win 98 machine with no problems. Ubuntu provides a disk partitioning tool, and installs GRUB to handle the boot options, so from thereon, instead of booting straight into Windows you'll get the Grub window, where you can choose to boot into Ubuntu or Windows.

---

### Post by N700 on 2009-07-01
> **johnraff said:**
> I used Unetbootin to install Ubuntu in some spare disk space on a Win 98 machine with no problems. Ubuntu provides a disk partitioning tool, and installs GRUB to handle the boot options, so from thereon, instead of booting straight into Windows you'll get the Grub window, where you can choose to boot into Ubuntu or Windows.
Thanks! Is that reliable, the installation of GRUB to boot Windows? From my experience with it, Windows tends to get a bit precious about anything else modifiying bits of it, and then it'll refuse to work, leading to spending 20+ hours doing a reinstall which I'd like to avoid.

It's Windows XP Pro if that makes any difference.

---

### Post by N700 on 2009-07-01
Actually, with Ubuntu is there any way of making a "non-bootable" install, such that the Windows bootloader is left alone and there is then a "dormant" Linux install in /dev/hda2, which won't do anything until a CD or USB stick is used to "trigger" booting into it?

If this is possible I'd prefer it to changing the Windows bootloader.

---

### Post by johnraff on 2009-07-03
> **N700 said:**
> Thanks! Is that reliable, the installation of GRUB to boot Windows? From my experience with it, Windows tends to get a bit precious about anything else modifiying bits of it, and then it'll refuse to work, leading to spending 20+ hours doing a reinstall which I'd like to avoid.

It's Windows XP Pro if that makes any difference.Well, of course there's no cast-iron guarantee, and you should definitely back up all important data before doing something major to your system like this, just in case. That said, I've done this a couple of times with no problems, and haven't heard of many cases where the Grub installation messed up. The Ubuntu installer seems to do a pretty good job. Just take it slowly and carefully. 

Here's a good guide:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Starting from Unetbootin you'll be doing something close to the "alternate" install referred to a bit down the page. (There's lots of good advice on that site.)

---

### Post by Oddballs on 2009-09-01
I used UNetbootin to download Ubuntu 9.04 onto my Dell INSPIRON | 1501 laptop that previously ran Windows XP. The screen on the laptop is broken, so I have it connected to a monitor. The things I read said that it would bring up a screen to select the OS, so I pressed down and than enter. After a minute or so My monitor displayed the desktop. I double clicked install and went easily through the first three steps and the screen shown in the screenshot came up. I have about 50 GB free, but I want to delete windows and run only on Linux. This is my first time changing OS or dealing with partitions at all, so it would be best if you dumbed it down a bit.

---

### Post by anand.partha on 2009-09-02
Best option would be to install ubuntu from windows is to follow this
[http://wubi-installer.org/](http://wubi-installer.org/)

i have done it and it was fairly straight forward...

Yo Ubuntu!!!

---

### Post by Ed.Hunt on 2009-11-14
I'm not having any luck using Unetbootin to do a Hard Disk Install.

My current OS is Ubuntu 9.10, but I'd like to try a different one.

From what I can tell, the problem might be with GRUB2. At reboot, I'm not getting the option to launch Unetbootin. Instead, 9.10 just starts loading.

It seems this issue has already been addressed:

[https://bugs.launchpad.net/ubuntu/+source/unetbootin/+bug/386862](https://bugs.launchpad.net/ubuntu/+source/unetbootin/+bug/386862)

However, Unetbootin doesn't seem to be working with 9.10.

---

### Post by johnraff on 2009-11-15
Have you tried the latest version from Unetbootin's site?
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Ed.Hunt on 2009-11-16
yes... I used 3.77

---

### Post by amsterdamharu on 2009-11-29
Tried unetbootin to install ... well anything that will work but no such luck.
Fedora-11-i686-Live hangs at first message
Fedora-12-i686-Live no root device found
ubuntu-8.04.3-alternate-i386.iso Asking for a DVD during setup
ubuntu-9.10-desktop-i386.iso Doesn't show anything because of my graphics card

Running windows xp and have some unused space on my harddisk I would like ubuntu or fedora installed, did it once on another computer but forgot how.

Don't have a DVD or USB drive I can use to boot and run setup so let unetbootin put all the files on C:, this is NTFS and that might be the problem.
Fedora doesn't boot at all and Ubuntu is asking to mount a cd rom but the setup is not on the cd rom.

---

### Post by amsterdamharu on 2009-11-29
Ok, remembered to replace some stuff after unetbootin was done and gone to here:
[http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/)

Then downloaded the files:
boot.img.gz
initrd.gz
vmlinuz

Then run unetbootin with the ubuntu-8.04.3-alternate-i386.iso and have it put all the files on C:.
When that was done I copied initrd.gz and vmlinuz to C:\install (overwrite) and rebooted.
This worked fine, got the setup running, the setup might be looking for iso's to mount so put ubuntu-8.04.3-alternate-i386.iso in c:\

---

### Post by reagen on 2010-01-10
hello. thanks for the program, it work great. i've successfully erased my windows xp and install ubuntu 8.10. however there's a er end up in the ubuntu desktop and instead just got stuck in some DOS like OS. when i check it seems i am running "ubuntu 8.10, kernel 2.6.27-16-generic" . it asks me to log in and when i did it just stand there with a "reagen@reagen:~$ " . waiting for command i dunno of. since everything is running fine, i assume it's not the installer 's problem, and i probably did something wrong during installation. i'm no computer expert ,so here 's me asking you guys : what is wrong and how do i fix it? any help would be appreciated. thanks anyway....

---

### Post by johnraff on 2010-01-11
It sounds as if you've installed just the basic command-line-only system. Maybe you forgot to select one of the desktop setups during the installation process. Two options I'd say: 
1)go back and do it over again, this time choosing "ubuntu desktop" or whatever when that menu comes up (arrows to go up and down, spacebar to select),or
2)carry on and install the ubuntu desktop (if that's what you want) by typing ```
sudo apt-get install ubuntu-desktop
``` at that command prompt you get. You'll be asked for your password, then a whole lot more stuff will install.

---

### Post by crtlbreak on 2010-01-11
> **reagen said:**
> ......... instead just got stuck in some DOS like OS. when i check it seems i am running "ubuntu 8.10, kernel 2.6.27-16-generic" . it asks me to log in and when i did it just stand there with a "reagen@reagen:~$ " . waiting for command i dunno of. since everything is running fine, ....

have you tried a 
```
startx
``` yet?

---

### Post by Matt_Johnson on 2010-01-11
Works Great !

---

### Post by reagen on 2010-01-11
> **johnraff said:**
> It sounds as if you've installed just the basic command-line-only system. Maybe you forgot to select one of the desktop setups during the installation process. Two options I'd say: 
1)go back and do it over again, this time choosing "ubuntu desktop" or whatever when that menu comes up (arrows to go up and down, spacebar to select),or
2)carry on and install the ubuntu desktop (if that's what you want) by typing ```
sudo apt-get install ubuntu-desktop
``` at that command prompt you get. You'll be asked for your password, then a whole lot more stuff will install.

> 
have you tried a 
 	Code:
 	startx 
 yet? 		                   		  		  		 		

Thanks for all the help. It works, and right now I'm trying stuff on my Ubuntu! Although "Panel Encountered problem while loading 'OAFIID:GNOME_Panel_TrashApplet'" keeps popping up everytime I log in...
Well, I guess that ain't much of a problem....
Thanks for everything, you're the best!

---

### Post by Jhon Butcher on 2010-01-12
If you boot off a USB drive, you can install it from there. Download the Ubuntu ISO, create a bootable USB drive and extract the ISO contents to the drive. See source for detailed instructions.

---

### Post by dave_h on 2010-02-01
I am trying to install Ubuntu 9.10 as a frugal install using Unetbootin (latest version) to an ntfs partition that has an existing Windows XP on it.

1. Is this possible? I am told it is but can I really install without destroying the Windows partition? Also will it work even though the partition is formatted as NTFS?
I have looked everywhere but no one seems to be able to answer these two fundamental questions. 

2. I have tried this but after install I get a boot choice of Windows XP or Unetbootin. Selecting the latter it starts to boot with > Booting 'UNetbootin'
but gets as far as an error 15. 
> Booting 'UNetbootin'
find --set-root /unetbtin/ubnkern
Error 15 File not found

grub4 dos stanza is
> find --set-root /unetbtin/ubnkern
kernel /unetbtin/ubnkern
initrd  /unetbtin/ubninit
boot

Rebooting to Windows XP I see:
1. the line > c:\ubnldr.mbr="UNetbootin"has been added to boot.ini
2. I see no grldr files. Should I?
3. a folder c:\unetbtin which contains a menu.lst

Anyone any ideas what's wrong. How to get this working?
Thank you.

---

### Post by nooby on 2010-02-03
Hi Dave,

I have something like that on my old WinXP machine but the HDD is acting up due to broken connection in power supply so I use another computer and that one has vista on it. 

What you experience there could be the incompatibility between Grub legacy and Grub2 and they have desribed how to solve it IIRC. 

but I have no link now. 

I did use UNetbootin too but on my Vista machine and had to uninstall it because some odd thing with HP and Vista locked the UNetbootin program from doing installs on USB after the Ubuntu install. 

Not the fault of Ubuntu. I wrote to the developer of UNetbootin but received no answer. 

So I did a wubi of Ubuntu 9.10 and then did a EasyBCD 1.7.2 with Neogrub but they tells me to use the 2.0 latest version due to the Grub2 incompatibility. 

You and I and DrG at brainstorm. ubuntu.org? and some of the people who love Puppy Linux are the only ones who wants to promote frugal install of Ubuntu. 

I have such now on my vista but I still fail to do the casper-rw file persistent but that could be due to me using the iso for live CD sessions and that one do automatic log in of a restricted user so maybe it is not able to save without editing the syslinux. 

I don't know if we can continue in this thread due to that one maybe dedicated to full install??? 

so either we do PM or start a new thread about frugal install on XP and Vista/Win7 because these are different to each other.

---

### Post by esclunatic on 2010-02-23
hi,im new to this ubuntu/linux stuff,but i have a couple of recycled pcs to experiment on
so instead of the xp pro junk,that im all to jaded about,i thought ide try it out....
tryed wubi yuck,my cd-rom is not reading correctly most of them are a bit accentric nowadays the usb`s i have are under 2 gigs so ive tryed some optional ways of installing
right now i am installing xp on half of my 8.5 gig drive partitioned in setup.then ill grab the iso files use netbootin and try to install on second half,if successfull ill format the xp side for extra space,its not very big.hopefully it works out.

---

### Post by Capital E on 2010-02-25
Hi, I have XP and have no way of recovering it so it's precious to me.

Anyway, I want to try ubuntu, and Unetbootin is pretty cool. But I've noticed that it's only a trial bases. If I "truly install" it through unetbootin, can I remove it like a program like wubi?

I'm worried, if I don't need ubuntu anymore ([SIZE="3"]especially since support end and lynx is coming out[/SIZE]), it'll be hard to get rid of it, and it might ruin my partition.

[B][SIZE="5"]With wubi, you can do a dualboot......and if you hate it, you can remove ubuntu as a program from XP.

_[COLOR="DarkSlateBlue"]But does that happen with Unetbootin too?[/COLOR]_ [/SIZE][/B]

---

### Post by crashcrew on 2010-03-12
**Problem installing with UNetbootin** 
I partitioned my hardrive with UNetbootin in order to dual boot with Win XP (just for gaming).

My partition is as follows: NTFS 200GB for XP, EXT4 145GB for Ubuntu, SWAP 5GB.

Everything goes smoothly until I get the following message:

***Installer needs to commit changes to partition tables but cannot do so because partitions on the following mount points could not be unmounted:***

***/cdrom***

***Please close any applications using these mount points.***


I don't have a CD in the drive nor is anything (that I'm aware of) using the drive.

Any ideas? 

Thanks in advance!

---

### Post by zivley on 2010-03-13
Check if you don't have a flash drive plugged in while trying to install, it may be mounted and detected as "cdrom".
Also, if you haven't shut down windows properly it may detect some file systems as kinda mounted while they're actually not

---

### Post by eltioseba on 2010-05-03
Hi, I have an old computer with no cd, no usb, no nothing :D

I`m trying to make an fresh install of xubuntu runnig the live cd from the hdd.
I remove the hdd from the computer and plug it in another one. The hdd is not bootable. Its completely clean. I can format it anyway. 

I have it in my windows like e:
The unetbootin problem. I select the hard drive, forcing it, and the process completes without problem.
Then a select in my bios to boot from that hdd but nothing happens. 

I assume unetbootin modifies an existing booting system. But what a need to do is to create it from scratch the hdd.

thanks in advance

---

### Post by amsterdamharu on 2010-05-04
Try to get grub4dos on that harddisk, never done it before but there is some documentation out there.

If grub4dos is installed you can post the content syslinux.conf on that harddisk so we can help translate the start menu to grub menu (grub4dos) in this case.

[http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial)

---

### Post by osviweb on 2010-08-06
Hello all

I'm trying to install ubuntu laptop 10.04 in a laptop with no cd-rom and no usb boot.
I have xp running and using unetbootin I could startup the iso of Ubuntu and with gparted prepare the Ext4 and swap partitions on the laptop harddisk.

I'm following istructions of what unetbootin calls Frugall Install.

After creating the partitions I've uninstalled and reinstalled again unetbootin from windows as suggested.

Here is the point. From live cd the installation fails. It ask me to select the partitions for install = fine ,then it advice me that I'll be able to install but not manage partitions because I'm on the same disk as the live cd,  then it try to unmount the partion cdrom (virtual) from which it runs Ubuntu Live cd itself and fails.

I've tried many times but it looks like Ubuntu Live cd works but cannot istall to the partitions I've prepared.

Why this Frugall install procedure fails?

thanks

---

### Post by amsterdamharu on 2010-08-08
You cannot unmount/resize the partition that the iso file is on because you need to read data on that "CD". When you unmount the partition it's like ejecting the CD.

I think Tinycore Linux runs out of memory so if unetbootin can put that ISO on your harddisk and then boot into tinycore you might be able to install gparted and resize but I'm not sure it would work.

---

### Post by Froodolt on 2010-11-25
Hello,

I am trying to install Linux Mint on my laptop. Becouse my laptop cant boot from usb and my cd-rom player doesn’t function, I want to install it from HDD using UNetbootin. The problem is that UNetbootin doesn’t seem to change grub2. UNetbootin tells me to reboot (no errors), but than the grub menu doesn’t show any option to run the Mint .iso. It just boots directly to Ubuntu.

Current setup:
Ubuntu 10.04

Installation setup:
unetbootin-linux-494
linuxmint-10-gnome-dvd-i386.iso (downloaded to hdd and selected for installation in UNetbootin)

After running UNetbootin:
```

sudo update-grub
[sudo] password for bas: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-25-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-24-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-23-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-23-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-22-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-22-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
```

It seems that UNetbootin doesnt change the grub menu. 
Or am I not getting it?

Does anybody know what goes wrong?

Thanks in advance for the help!

---

### Post by amsterdamharu on 2010-11-26
If unetbootin is done there should be a directory called casper in the root of the partition you choose to extract the iso to.

I had unetbootin do it on a usb and then got a syslinux.cfg in the in the root as well.

This is the part that starts mint 8 in compatible mode (from there you can update the installer and install).
```
label xforcevesa 
  menu label Start Linux Mint (compatibility mode) 
  kernel /casper/vmlinuz 
  append  file=/cdrom/preseed/mint.seed boot=casper xforcevesa initrd=/casper/initrd.lz ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll -- 
```Now you can manually put that in your /boot/grub/grub.cfg (yes it will overwrite after an updategrub but it'll work if you reboot after changing). Please don't mess it up or there is a chance that you can't boot anymore because of the messed up menu. Since you cannot boot with CD or USB it will be hard to change the menu when the HD is unbootable. If you copy and paste this at the end you should be fine.

```
menuentry "Linux Mint extracted ISO" {
        recordfail=1
    set quiet=0
    insmod ext2
    set root=(hd0,7)
    linux    /casper/vmlinuz  file=/cdrom/preseed/mint.seed boot=casper xforcevesa 
    initrd   /casper/initrd.lz ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll --  
}
```The line insmod ext2 assumes you have your casper directory on a ext2 partition.
set root=(hd0,7) Means you have the casper directory on the 7th partition of the first HD.
I am not sure if the "ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll --  " has to come at the end of the linux line or at the end of the "initrd   /casper/initrd.lz", I put it at the end of the initrd line but if it doesn't start mint then move that part to the end of the linux line like so:
```
    linux    /casper/vmlinuz  file=/cdrom/preseed/mint.seed boot=casper xforcevesa  ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll --
    initrd   /casper/initrd.lz 
```

---

### Post by bbalegere on 2011-08-15
Tutorial to install Ubuntu from Hard Disk using Grub4Dos.

[http://agnipulse.com/2011/08/install-ubuntu-hard-disk/](http://agnipulse.com/2011/08/install-ubuntu-hard-disk/)

---

### Post by madjr on 2011-09-04
i had the following problems so i used:


**apt config error:**
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/658865](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/658865)
[http://ubuntuforums.org/showthread.php?t=1663652](http://ubuntuforums.org/showthread.php?t=1663652)

*sudo rm /usr/lib/ubiquity/apt-setup/generators/40cdrom*

**migration assistant error/crash:**
*ubiquity --no-migration-assistant*

**unmount /cdrom:**
*sudo umount -l /cdrom*

or
[http://linuxers.org/howto/how-install-ubuntu-910-without-cddvd](http://linuxers.org/howto/how-install-ubuntu-910-without-cddvd)
sudo umount -l -r -f /cdrom

---

