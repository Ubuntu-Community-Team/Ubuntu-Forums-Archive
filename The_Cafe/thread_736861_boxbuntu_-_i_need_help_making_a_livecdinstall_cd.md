---
title: "boxbuntu - i need help making a livecd/install cd"
date: 2008-03-27
forum: The Cafe
---

### Post by chris4585 on 2008-03-27
I've been trying to build a livecd that works for a while now, i'm asking for help making a install cd or livecd to distribute a distro i want to call boxbuntu, but the only solution i've gotten is making a backup of it in iso form using remastersys, allowing someone else to make the livecd install cd, i dont have the iso uploaded as of now, but if anyone has any interest in helping me i would upload it and see what you can do

About boxbuntu - boxbuntu uses openbox as the windows manager and k.mandla's fbpanel's layout, which works pretty nice, i have a few programs installed, synaptic, gdm, gnome-system-monitor, firefox, links2, mousepad, conky, totem, alsaplayer, openbox, switch2, and a few others, my goal is to be very minimal without losing too much function or polish

---

### Post by JeffoOfMetal on 2008-03-27
You might try Reconstructor. [http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/) I'm trying to use it to create my own little distro. Good luck!

---

### Post by xArv3nx on 2008-03-27
> I thought I would make a easy and simple guide to making a customized version of klikit. I am sure we have all came across those remaster how-tos and found them difficult, too verbose, or just not understandable. So I tried to write something that was complete but simple, explained just enough to have a idea but didnt overwhelm, and most of all - that just plain works!

Let me know how I did?
------------------------------------------------------------
insert klikit cd

open Konsole, gnome-terminal, aterm, xterm or whatever terminal program you prefer

sudo su
to change to root

cd Desktop
to change to the Desktop

mkdir build
to make a folder to work in

cd build/ 
change to that directory

mkdir customlivecd
make a folder for the current cd contents

cp -a /media/cdrom0/* customlivecd/
copy everything from the cd (adjust for your cd drive) to the folder

mkdir /mnt/squashmount
make a folder to use for mounting the squashed filesystem

mount -t squashfs -o loop customlivecd/casper/filesystem.squashfs /mnt/squashmount/
mount the current squashed file system

mkdir extractedsquash
make a folder to hold the contents of the un-squashed file system

cp -a /mnt/squashmount/* extractedsquash/
copy everything out of the squashed filesystem to our folder

umount /mnt/squashmount
unmount the squash file system

rm customlivecd/casper/filesystem.squashfs
remove the old squashfs since we will be making a new one

cp /etc/resolv.conf extractedsquash/etc/
copy the resolv.conf file over so we will have internet resolution when we work

mount -t proc -o bind /proc/ extractedsquash/proc/
mount proc system

chroot extractedsquash/
change root to be extractedsquash so we work as if the folder is our actual system

apt-get update/upgrade/remove/install/whatever
add/remove software phase! *discussion to follow in thread

exit
to leave the chroot and get back to the real system

umount extractedsquash/proc/ 
unmount proc

rm extractedsquash/etc/resolv.conf
remove our resolv.conf

mksquashfs extractedsquash/ customlivecd/casper/filesystem.squashfs
making the new squashed system from the one we extracted and changed

cd customlivecd/

mkisofs -r -V "image name" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o ../klikit-CCV-version.iso .
this is all one line, and dont forget the dot at the end

open the build folder on your desktop and the iso should be there ready to burn....

-------------------------------------------------------------

So how was it?

> Some explanation - 

the squashfs is a squashed up file system and that is what gets installed, so what we are doing is un-squashing it, telling our system (chroot) to change root to that system and let us work in it as if it were our own system, then we exit, squash it back up, and make a iso. 

Only in that terminal where you did the chroot are you working IN the new system, if you open a new terminal you will be in YOUR system. Be careful not to confuse the two, it really sucks to remove about 200mb of packages only to find out it was YOUR system that you did it to, especially when the kernel was one of those. Doh!

Oh, you need a few gigs of space (minimum) to do this with a CD size image. My method removes stuff as you go along so it doesn't eat up as much space but I would still have about 3gigs of free space before trying it.


Now some tips - 

add/remove phase - you can add/remove anything that is in the repos that are listed in the squashed systems sources.list so go wild.... Be aware that the more you install the larger your system will be and you may make it too big to fit on a CD. I usually remove first and keep track of how much I have removed, then I have a idea of about how much I can install. Please remember that it is not the download size but the X amount of space used once it is installed that you need to worry about. 

add/remove phase - when finished you should use the command apt-get clean to clean out the packages that were downloaded when you installed stuff

add/remove phase - you should at least use the purge option when you remove something like apt-get remove --purge packagename I would actually suggest using apt-get autoremove --purge packagename this will purge the packages and *should* remove the dependencies that are not needed anymore BUT be careful with this. You can also install and use deborphan to clean up leftover stuff.

add/remove phase - dpkg -l (that is a lower case L) will give you a listing of all the packages installed or you can always look at your system to determine what is or isnt installed. dpkg -l > list.txt will give you a text file with the list of installed packages. 

mkisofs -r -V "image name" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o ../klikit-CCV-version.iso .
This command makes the iso and the "image name" is what you want the actual label to be which is what shows up as the icon name when you insert the CD. Do not make it too long. The name.iso at the end is just what you want the iso name to be. This command goes on one line. do not hit enter part of the way thru just keep typing and it will wrap itself and be fine. Watch for spacing and make sure to add the dot at the end.

Once you do this a couple times and get familiar with it you can do it without thinking about it.

stuff I left out but you may want to research - 
update/remove filesystem.manifest
remove/change other stuff on the disk
generate md5

Have fun.

---

### Post by az on 2008-03-27
This is how I build the Ubuntu-Rescue-Remix live USB and live CD images:

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

As you can tell from the title, they are build from scratch, and not reconstructed.  I start with an empty directory.

---

### Post by chris4585 on 2008-03-27
> **az said:**
> This is how I build the Ubuntu-Rescue-Remix live USB and live CD images:

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

As you can tell from the title, they are build from scratch, and not reconstructed.  I start with an empty directory.

i actually had this page up and was considering doing this today to see how well it worked

With this did you get what you wanted?

---

### Post by notwen on 2008-03-27
> About boxbuntu - boxbuntu uses openbox as the windows manager and k.mandla's fbpanel's layout, which works pretty nice, i have a few programs installed, synaptic, gdm, gnome-system-monitor, firefox, links2, mousepad, conky, totem, alsaplayer, openbox, switch2, and a few others, my goal is to be very minimal without losing too much function or polish

This looks very nice.  Keep us updated on your quest to get a LiveCD/install disc made.  =]

---

### Post by capink on 2008-03-27
And if you want a clean system, you can make a new custom Ubuntu from scratch using debootstarp and then apply the steps of the guide to make a live cd out of it.

here is short howto make a custom ubuntu system using debootstrap:

1. Create a directory whrere you will create the new system:

```
export WORK=~/work
```

```
sudo mkdir -p ${WORK}/rootfs
```



2. Install debootstrap

```
sudo apt-get update && sudo apt-get install debootstrap
```

3. Run debootstrap to install the basic packages:

```
sudo debootstrap gutsy ${WORK}/rootfs
```

Replace gutsy with any other version you want (e.g. lenny, fesity, etch, .....)

This step will take time as the deb files are downloaded.


Now you have a system the contain the basic packages. At this stage this system can only work as chroot system. But in the next steps we will modify it to be full system.



4. Prepare the new system before chrooting into it:

Modify the new system sources list:

```
sudo gedit ${WORK}/rootfs/etc/apt/sources.list
```

And place the following text into it:


> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free 

Note: Replace gutsy with your version name




Copy the following files to have internet access within the chroot environment:

```
for i in /etc/resolv.conf /etc/hosts /etc/hostname; do sudo cp -pv $i ${WORK}/rootfs/etc/; done
```



5. Chroot into the new system:

```
sudo mount -t proc proc ${WORK}/rootfs/proc
```

```
sudo mount -t sysfs sysfs ${WORK}/rootfs/sys
```

```
sudo mount --bind /dev ${WORK}/rootfs/dev
```

```
sudo chroot ${WORK}/rootfs /bin/bash
```


[COLOR="Blue"]Note: All commands in blue are run within chroot.[/COLOR]

```
[COLOR="Blue"]LANG=[/COLOR]
```


6. Once in chroot, modify the new system:

```
[COLOR="#0000ff"]apt-get update[/COLOR]
```

This will give you GPG warning because of third party repositories (Codecs repositories). Ignore it and proceed.



Install the multimedia keyrings ( to prevent apt from complaining about missing GPG ):

```
[COLOR="#0000ff"]apt-get -qq install wget && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | apt-key add -[/COLOR]
```



Install some important packages not included in the base install performed by debootstrap:

First of these important packages is the kernel. Debootstrap does not install a kernel. To install it:

```
[COLOR="#0000ff"]apt-get install linux-image-generic linux-headers-generic linux-restricted-modules-generic ubuntu-standard[/COLOR]
```


Now, we have a complete command line system



To have a graphical system, install:

```
[COLOR="#0000ff"]apt-get install xorg gdm openbox fbpanel thunar firefox mplayer w32codecs scite gqview xarchiver roxterm gtk2-engines xcursor-themes ttf-bitstream-vera ttf-dejavu ttf-freefont[/COLOR]
```

you can replace the packges above with your preferred apps. just do not forget to install xorg and a login manager like gdm.


7. Exit chroot:

```
[COLOR="#0000ff"]exit[/COLOR]
```



8. Unmount Chroot dev and proc since we are not going to use them again.


```
sudo umount ${WORK}/rootfs/proc
```
```
sudo umount ${WORK}/rootfs/dev
```
```
sudo umount ${WORK}/rootfs/sys
```



Now you have a complete Ubuntu system in the directory ${WORK}/rootfs. You can make a live cd from it by following the guide in my signature. just do not forget to look at the debootstrap appendix in the guide for slight modification of the commands.

---

### Post by chris4585 on 2008-03-27
thank you for taking time to help all and especially the post above, i have a qustion, if i do this - i'm confused about how to modify the system - like i tried remastersys dist option, apparently it didnt like my setup, wouldnt even let me run without .xsession-error message, my guess its made specificly for gnome.. but i'm asking i want to put my fbpanel's profiles in there, and when i did the remastersys dist option it had the default look, how and when will i need to modify it to my profiles?


(update) i think i see how to edit it now

---

### Post by chris4585 on 2008-03-27
right now capink i'm trying your guide, hope it works

---

### Post by SomeGuyDude on 2008-03-27
Keep us posted, that screenshot looks pretty wicked. I'd love to give it a shot.

---

### Post by chris4585 on 2008-03-27
> **SomeGuyDude said:**
> Keep us posted, that screenshot looks pretty wicked. I'd love to give it a shot.

thank you for the support, i'm not making promises but i have a strong feeling i can get this to work if i keep trying

---

### Post by chris4585 on 2008-03-27
i'm having problems with...


5. Chroot into the new system:

Code:

sudo mount -t proc proc "$deboot"/proc

Code:

sudo mount -t sysfs sysfs "$deboot"/sys

Code:

sudo mount --bind /dev "$deboot"/dev



i get this

chris@chris-desktop:~$ for i in /etc/resolv.conf /etc/hosts /etc/hostname; do sudo cp -pv $i "$deboot"/etc/; done
`/etc/resolv.conf' -> `/home/chris/deboot/etc/resolv.conf'
`/etc/hosts' -> `/home/chris/deboot/etc/hosts'
`/etc/hostname' -> `/home/chris/deboot/etc/hostname'
chris@chris-desktop:~$ sudo mount -t proc proc "$deboot" /proc
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
chris@chris-desktop:~$ sudo mount -t sysfs sysfs "$deboot" /sys
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
chris@chris-desktop:~$ sudo mount --bind /dev "$deboot" /dev
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
chris@chris-desktop:~$ sudo chroot $deboot /bin/bash
root@chris-desktop:/# LANG=

---

### Post by capink on 2008-03-28
> **chris4585 said:**
> i'm having problems with...

chris@chris-desktop:~$ sudo mount -t proc proc "$deboot" /proc


You have put an extra space between "$deboot" /proc. the command should be:

```
sudo mount -t proc proc "$deboot"/proc
```


same for the other commands as well.

please we you resume the steps make sure that you redefine the variable deboot first. 

Also I have edited the previous post by making all commands that should be run within chroot highlighted with blue.

---

### Post by az on 2008-03-29
> **chris4585 said:**
> i actually had this page up and was considering doing this today to see how well it worked

With this did you get what you wanted?

The CD and USB images for perfectly.  It's a little simpler than the instructions in the previous few posts.

---

### Post by chris4585 on 2008-03-29
> **az said:**
> The CD and USB images for perfectly.  It's a little simpler than the instructions in the previous few posts.

i might try your way, if i dont get anywhere with the previous tutorial i'm going to try the ones i've seen till i get it right, i'm still working on the previous tutorial though, thanks for the response =)

---

### Post by jedi453 on 2008-04-02
I've attempted to follow the process given by capink a few times now without success. I am attempting to create a custom minimal liveCD as well, if successful this will be my first. I have been able to make an ISO and boot it, but it boots to an unfamiliar non-graphical bash which doesn't seem to give access to any of the installed software. Each command is preceded by "(initramfs"), is there a way to set a default to boot to the terminal or to the desktop (openbox), or have I followed the procedure wrong? Thanks.

---

### Post by chris4585 on 2008-04-03
i havent gotten successful  yet, but i've been very busy the past week.. if i get any luck i'll let you know

---

### Post by az on 2008-04-03
> **jedi453 said:**
> I've attempted to follow the process given by capink a few times now without success. I am attempting to create a custom minimal liveCD as well, if successful this will be my first. I have been able to make an ISO and boot it, but it boots to an unfamiliar non-graphical bash which doesn't seem to give access to any of the installed software. Each command is preceded by "(initramfs"), 

Are you booting from a CD or from Qemu or vmware.  That may be your problem.  Most of the time, qemu doesn't boot squashfs images properly, so it can't find "/" and you get dropped to a busybox shell in your initrd.  This has nothing to do with how you built your iso or base system.

If you can't get a rewritable cd or if burning a cd is impractical, test out your live system by booting from USB and when it's working fine, put it on CD...  Writing the image to USB takes almost no time at all and is easy to test.

---

### Post by jedi453 on 2008-04-04
You were right az, I was able to boot the cd regularly, but when I used Qemu it went to the busybox command line. Thanks! I suggest that anyone else testing there cd's double check after a fail in qemu. 

chris4585, If you already have a hard drive install of boxbuntu, you might be able to bypass the debootstrap process and follow Capink's guide for making a live cd from a hard drive installation:

[http://ubuntuforums.org/showthread.php?t=688872]("http://ubuntuforums.org/showthread.php?t=688872")

Good Luck!

---

### Post by jedi453 on 2008-04-09
I combined Capink's debootstrap and the [Make LiveCD from install]("http://ubuntuforums.org/showthread.php?t=688872") with the Custom LiveCD Tutorial. The result is a Debootstrapped system on a LiveCD using ISOLinux. I'm not sure how to get fbpanel to start from outside of the LiveCD, but I have gotten Openbox running. I also don't know how to customize the Desktop before compressing the disk. Well, here's what I have anyway, everything that isn't commented with "//" are terminal commands or needs to be copied and pasted into gedit or nano. The comments explain it. To run fbpanel from inside the cd right 
click once x boots, click "terminal emulator" and enter "sudo fbpanel". Run "nm-applet" to start the network manager. As setup this will be about 250 MB ISO. But take at least 1 GB to make.



// LiveCD using syslinux, combined methods:
//http://ubuntuforums.org/showthread.php?t=736861
//https://help.ubuntu.com/community/LiveCDCustomizationFromScratch
//http://ubuntuforums.org/showthread.php?t=688872
//Tested on Ubuntu, made in Ubuntu

// define variables
 ```

deboot=~/work/chroot
export WORK=~/work
export CD=~/work/image
export FORMAT=squashfs
export FS_DIR=casper

```


```

cd ~/
mkdir ~/work
cd work
mkdir chroot

```
//get debootstrap can skip if you already have it
```

sudo apt-get update && sudo apt-get install debootstrap

```


//begin debootstrap, i386 works on AMD64 too! (I think)  The "gutsy" is the name of the ubuntu distro. This will take some time:
```

sudo debootstrap --arch i386 gutsy chroot

```

// Open Up the deboot's source list, needed for it to get packages
// if you have gedit, I recommend it; else, use nano or similar
```

sudo gedit ~/work/chroot/etc/apt/sources.list

```

// In the following, use the same ubuntu version as deboot step, in place of "gutsy", if necessary
// copy the following text into it... between the two "// ***" lines
// Some text will already be there, replace it with the text below
//  *** BEGIN sources.list   copy this into the new file:
```

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

deb http://packages.medibuntu.org/ gutsy free non-free 

```
//  *** END sources.list    


// This will keep your internet connection for the upcoming steps
```

for i in /etc/resolv.conf /etc/hosts /etc/hostname; do sudo cp -pv $i ~/work/chroot/etc/; done

```

```

sudo chroot chroot /bin/bash
mount /proc
mount /sys
mount -t devpts none /dev/pts
LANG=
apt-get update

```
// This will remove the warning you may have just seen
// copy the full line below don't stop at the //
```

apt-get -qq install wget && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | apt-key add -

```

// Important packages, to make a command-line system
// While it runs it will give a kernel number, remember it
```

apt-get install linux-image-generic linux-headers-generic linux-restricted-modules-generic ubuntu-standard

```
```

locale-gen en_CA.UTF-8
apt-get install ubuntu-standard casper

```



// replace $(uname -r) with the version of The DEBOOTSTRAP system (ex. 2.6.22-14-generic), these are important packages
```

sudo apt-get install mkisofs squashfs-tools linux-ubuntu-modules-$(uname -r)

```


// Important: you'll have to install xorg if you want a window manager, the following does that
// A random blue screen may pop up in the terminal after this
// It just wants to know the desired possible screen resolutions
// Just hit enter to skip that screen
```

apt-get install xorg gdm

```

// install desired window manager and packages ex.  IMPORTANT don't forget to uncomment below to add a window manager, select you choice of "xfce4","kde","gnome","openbox"
// apt-get install xfce4
// apt-get install kde
// apt-get install gnome
// apt-get install openbox* fbpanel
// important packages for a live-cd
```

apt-get install discover1 laptop-detect os-prober xresprobe

```
//some packages, one of the howto's includes them, they are useful, but not necessary:
// I've added a few that I recommend
```

apt-get install openbox* obconf fbpanel thunar firefox scite gqview xarchiver gtk2-engines xcursor-themes ttf-bitstream-vera ttf-dejavu ttf-freefont synaptic gnome-system-monitor conky totem alsaplayer mousepad network-manager network-manager-gnome xvt cupsys gnome-mount

```
// IMPORTANT: Install desired packages (and programs) with apt-get ex.
// apt-get install abiword
```

openbox --replace

```
// Change Xinit file
```

nano etc/X11/xinit/xinitrc

```
// *** begin additions: add this to the file
```

exec openbox
exec fbpanel

```
// *** end additions

// install ubiquity:  the ubuntu installer
```

apt-get install gparted ubiquity ntfs-3g

```
// apt-get install network-manager network-manager-gnome


// The 5 lines below get rid of "non-system users":
```

for i in `cat /etc/passwd | awk -F":" '{print $1}'`
do
	uid=`cat /etc/passwd | grep "^${i}:" | awk -F":" '{print $3}'`
	[ "$uid" -gt "999" -a  "$uid" -ne "65534"  ] && userdel --force ${i} 2>/dev/null
done

```

// remove unnecessary apt setup files
```

apt-get clean

```
```

rm -rf /tmp/*
rm /etc/resolv.conf

```

// replace "$(uname -r)" with deboot's kernel version ex. "2.6.22-14-generic"
```

depmod -a $(uname -r)
update-initramfs -u -k $(uname -r)

```

// Delete some files that aren't good for livecd's
```

for i in "/etc/hosts /etc/hostname /etc/resolv.conf /etc/timezone /etc/fstab /etc/mtab /etc/shadow /etc/shadow- /etc/gshadow  /etc/gshadow- /etc/gdm/gdm-cdd.conf /etc/gdm/gdm.conf-custom /etc/X11/xorg.conf /boot/grub/menu.lst /boot/grub/device.map"
do
	rm $i
done 2>/dev/null

```

// remove more unneeded files
```

find /var/run /var/log /var/mail /var/spool /var/lock /var/backups /var/tmp -type f -exec rm {} \;
rm -r /tmp/* /root/* 2>/dev/null

```

// Create login config file
```

[ -f "/etc/gdm/factory-gdm.conf" ] && cp -f /etc/gdm/factory-gdm.conf /etc/gdm/gdm.conf 2>/dev/null

```

// Create important empty files
```

for i in dpkg.log lastlog mail.log syslog auth.log daemon.log faillog lpr.log mail.warn user.log boot debug mail.err messages wtmp bootstrap.log dmesg kern.log mail.info
do
	touch /var/log/${i}
done

```

// Exit the live-cd directory
```

umount -l -f /proc
umount -l -f /sys
umount /dev/pts
exit

```

```

for i in ~/work/chroot/proc/* ~/work/chroot/dev/* ~/work/chroot/sys/* ~/work/chroot/tmp/* ~/work/chroot/home/* ~/work/chroot/lost+found
do sudo rm -r ${i}
done

```
// install some packages needed for you system:
//sudo apt-get install syslinux
//sudo apt-get install squashfs-tools
//sudo apt-get install mkisofs
//sudo apt-get install sbm
```

sudo apt-get install syslinux squashfs-tools mkisofs sbm

```

// make directories to put final image in
```

sudo mkdir image image/casper image/isolinux image/install

```

// The next steps set up the kernel, replace the "**"s with the right numbers
// They are particular to the kernel used for the debootstrap
// for me they are "22" , "14" , "22" , "14" ; respectively
```

sudo cp chroot/boot/vmlinuz-2.6.**-**-generic image/casper/vmlinuz

sudo cp chroot/boot/initrd.img-2.6.**-**-generic image/casper/initrd.gz

```
// These will prepare important files for the cd (it copies them to the image folder), you may or may not need sudo
```

sudo cp /usr/lib/syslinux/isolinux.bin image/isolinux/

sudo cp /boot/memtest86+.bin image/install/memtest
sudo cp /boot/sbm.img image/install/


```
// Make a isolinux.txt file
```

sudo nano image/isolinux/isolinux.txt

```
// *** COPY The following into that file, then save it "Ctrl-O", "Enter", and exit "Ctrl-x":
```

This is an Ubuntu Remix Live CD.

For the default live system, enter "live". 
 To verify the CD for errors, enter "check".
 To run memtest86+, enter "memtest"

```
// *** END isolinux.txt contents


// Generate manifest, for install
```

sudo chroot ~/work/chroot dpkg-query -W --showformat='${Package} ${Version}\n' | sudo tee ~/work/image/casper/filesystem.manifest
sudo cp -v ~/work/image/casper/filesystem.manifest{,-desktop}
REMOVE='ubiquity casper live-initramfs user-setup discover1 xresprobe os-prober libdebian-installer4'
for i in $REMOVE 
do
	sudo sed -i "/${i}/d" ${CD}/${FS_DIR}/filesystem.manifest-desktop
done


```


```

sudo nano image/isolinux/isolinux.cfg

```

// add "desktop=wm" to append line of "live lable" where "wm" is your window manager... 
// Just after "initrd=..." don't forget a space
// *** COPY The following into that file, then save it "Ctrl-O" and exit "Ctrl-x":
```

DEFAULT live
LABEL live
  menu label ^Start or install Ubuntu
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz desktop=openbox quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel /casper/vmlinuz
  append  boot=casper integrity-check initrd=/casper/initrd.gz quiet splash --
LABEL memtest
  menu label ^Memory test
  kernel /install/memtest
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1

```
// *** END isolinux.cfg contents


// compress the chroot, helps it fit on the cd.
```

sudo mksquashfs chroot image/casper/filesystem.squashfs

```
// Create README.diskdefines
```

sudo nano image/README.diskdefines

```

// *** BEGIN: Readme.diskdefines  text:
```

#define DISKNAME  Ubuntu 7.10 "Gutsy Gibbon" - Release i386 **Remix**
#define TYPE  binary
#define TYPEbinary  1
#define ARCH  i386
#define ARCHi386  1
#define DISKNUM  1
#define DISKNUM1  1
#define TOTALNUM  0
#define TOTALNUM0  1


```
// *** END: Readme.diskdefines

//get  md5sums and put them into md5sum.txt
```

sudo -s
(cd image && find . -type f -print0 | xargs -0 md5sum > md5sum.txt)
exit

```
// Create iso
```

cd image
sudo mkisofs -r -V "$IMAGE_NAME" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o ../ubuntu-remix.iso .

```
// Your ISO Image should then be in ~/work/ubuntu-remix.iso

---

### Post by capink on 2008-04-09
> **jedi453 said:**
> I'm not sure how to get fbpanel to start from outside of the LiveCD, but I have gotten Openbox running. 


To make fbpanel start automatically with you have to the following (in the filesystem of the live cd ofcourse):


1. Make a script that will run your custom desktop environment:

```
sudo cp /usr/bin/openbox-session /usr/bin/openbox-fbpanel-session
```

```
sudo gedit /usr/bin/openbox-fbpanel-session
```

you will find the following line at the bottom:

> exec /usr/bin/openbox "$@"

just above this line insert the following:

```
if which fbpanel; then
	fbpanel &
fi
```




2. Register you custom desktop environment with gdm as follows:

```
sudo cp -v /usr/share/xsessions/openbox.desktop /usr/share/xsessions/openbox-fbpanel.desktop
```

```
sudo gedit /usr/share/xsessions/openbox-fbpanel.desktop
```

paste the following:

```
[Desktop Entry]
Encoding=UTF-8
Name=Openbox Fbpanel Session
Comment=Use this session to run Openbox as your desktop environment
Exec=openbox-fbpanel-session
Icon=
Type=Application
```


N.B: You could directly edit /usr/bin/openbox-session to automatically start fbpanel and it will work fine. But this file will be overwirtten at the next upgrade of openbox.

---

### Post by fimblo on 2008-04-14
A few years ago I used "linux live!" to do this. ([http://www.linux-live.org](http://www.linux-live.org))

It was really, really, simple- you install what you want on your machine, run the live shell scripts, and there you go, out drops a .iso file which you can burn and run.

Pathetically simple.

give it a shot!

---

### Post by Scotty Bones on 2008-04-14
This might make things simpler

[http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)

it can create live-cd style full back-ups or custom distro from your current install.

---

### Post by chris4585 on 2008-04-14
I'm sorry i havent really paid attention to this thread, havent had time, but i havent forgotten about it, everyone's efforts in helping me isnt being wasted :)

---

### Post by chris4585 on 2008-04-14
> **Scotty Bones said:**
> This might make things simpler

[http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)

it can create live-cd style full back-ups or custom distro from your current install.

thanks, but i put in my first post that i've already used remastersys and it failed at what i wanted to do, i appreciate the help though, remastersys is good at backing up, but not the best at creating a distro

---

### Post by jedi453 on 2008-04-29
Here's a newer version of the instructions that I posted before. They add the fbpanel setup that you explain on your site. They also will automatically boot conky, fbpanel and nm-applet. They take at least 3 GB of space as configured. I tested them on Hardy, and Gutsy (both 64-bit) (for Gutsy just make the explained changes, you'll also use a kernel version of 2.6.22-14-generic rather than 2.6.24-16-generic.) This will make a system from scratch (not from the hard drive install), tell me if it works. Good luck.

 LiveCD using syslinux, combined methods:
[http://ubuntuforums.org/showthread.php?t=736861](http://ubuntuforums.org/showthread.php?t=736861)
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)
[http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)
Tested on Ubuntu Hardy Heron and Gutsy Gibbon

 define variables
```

deboot=~/work/chroot
export WORK=~/work
export CD=~/work/image
export FORMAT=squashfs
export FS_DIR=casper

```
```

cd ~/
mkdir ~/work
cd work
mkdir chroot

```

get debootstrap can skip if you already have it
```

sudo apt-get update && sudo apt-get install debootstrap

```


begin debootstrap, i386 works on AMD64 too! (32 bit mode though)  The "hardy" is the name of the ubuntu distro. This will take some time:
```

sudo debootstrap --arch i386 hardy chroot

```
 Open Up the deboot's source list, needed for it to get packages
 if you have gedit, I recommend it; else, use nano or similar
```

sudo gedit ~/work/chroot/etc/apt/sources.list

```

 In the following, use the same ubuntu version as deboot step, in place of "hardy", if necessary
 copy the following text into it... between the two "// ***" lines
 Some text will already be there, replace it with the text below
//  *** BEGIN sources.list   copy this into the new file:
```

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

deb http://packages.medibuntu.org/ hardy free non-free 

```
//  *** END sources.list    



 This will keep your internet connection for the upcoming steps
```

for i in /etc/resolv.conf /etc/hosts /etc/hostname; do sudo cp -pv $i ~/work/chroot/etc/; done

```
Chroot into the new system:
```

sudo chroot chroot /bin/bash
mount /proc
mount /sys
mount -t devpts none /dev/pts
LANG=
apt-get update

```
 This will remove the warning you may have just seen
```

apt-get -qq install wget && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | apt-key add -

apt-get update

```
 Important packages, to make a command-line system
 While it runs it will give a kernel number, remember it
```

apt-get install linux-image-generic linux-headers-generic linux-restricted-modules-generic ubuntu-standard

locale-gen en_CA.UTF-8
apt-get install ubuntu-standard casper



```

 replace $(uname -r) with the version of The DEBOOTSTRAP system (ex. 2.6.24-16-generic), these are important packages
```

sudo apt-get install mkisofs squashfs-tools linux-ubuntu-modules-$(uname -r)

```


 Important: you'll have to install xorg if you want a window manager, the following does that
 A random blue screen may pop up in the terminal after this
 It just wants to know the desired possible screen resolutions
 Just hit enter to skip that screen
```

apt-get install xorg gdm

```


 important packages for a live-cd
```

apt-get install discover1 laptop-detect os-prober xresprobe

```
some packages, one of the howto's includes them, they are useful, some are necessary for this tutorial:
 I've added a few that I recommend
```

apt-get install openbox* obconf fbpanel thunar firefox scite gqview xarchiver gtk2-engines xcursor-themes ttf-bitstream-vera ttf-dejavu ttf-freefont synaptic gnome-system-monitor conky totem alsaplayer mousepad network-manager network-manager-gnome xvt cupsys gnome-mount xfce4-terminal gksu gnome-alsamixer feh grub

```
 IMPORTANT: Install desired packages (and programs) with apt-get, example:
 apt-get install abiword
```
apt-get install unzip
```

 Some useful, but optional, rescue CD packages. They also can help interface with NTFS partitions
```

sudo apt-get install gparted testdisk partimage xfsprogs reiserfsprogs jfsutils ntfs-3g ntfsprogs dosfstools mtools

```


```

openbox --replace

```
 Change Xinit file
```

nano etc/X11/xinit/xinitrc

```
// *** begin additions: add this to the file
```

exec openbox

```
// *** end additions

 install ubiquity:  the ubuntu installer
```

apt-get install gparted ubiquity ntfs-3g

```
 apt-get install network-manager network-manager-gnome


 The 5 lines below get rid of "non-system users":
```

for i in `cat /etc/passwd | awk -F":" '{print $1}'`
do
	uid=`cat /etc/passwd | grep "^${i}:" | awk -F":" '{print $3}'`
	[ "$uid" -gt "999" -a  "$uid" -ne "65534"  ] && userdel --force ${i} 2>/dev/null
done


```
 remove unnecessary apt setup files
```

apt-get clean

rm -rf /tmp/*
rm /etc/resolv.conf

```
 replace "$(uname -r)" with deboot's kernel version ex. "2.6.22-14-generic"
```

depmod -a $(uname -r)
update-initramfs -u -k $(uname -r)

```

 Delete some files that aren't good for livecd's
```

for i in "/etc/hosts /etc/hostname /etc/resolv.conf /etc/timezone /etc/fstab /etc/mtab /etc/shadow /etc/shadow- /etc/gshadow  /etc/gshadow- /etc/gdm/gdm-cdd.conf /etc/gdm/gdm.conf-custom /etc/X11/xorg.conf /boot/grub/menu.lst /boot/grub/device.map /home/*"
do
	rm $i
done 2>/dev/null

```

 remove more unneeded files
```

find /var/run /var/log /var/mail /var/spool /var/lock /var/backups /var/tmp -type f -exec rm {} \;
rm -r /tmp/* /root/* 2>/dev/null

```

 Create login config file
```

[ -f "/etc/gdm/factory-gdm.conf" ] && cp -f /etc/gdm/factory-gdm.conf /etc/gdm/gdm.conf 2>/dev/null

```

 Create important empty files
```

for i in dpkg.log lastlog mail.log syslog auth.log daemon.log faillog lpr.log mail.warn user.log boot debug mail.err messages wtmp bootstrap.log dmesg kern.log mail.info
do
	touch /var/log/${i}
done

```

Make Configuration files for FBpanel
```

nano /etc/fbpanel/upper

```
// *** Begin upper   --- Paste this code into nano, then save the file
```

# fbpanel  config file
# see http://fbpanel.sf.net/docs.html for complete configuration guide

Global {
edge = top
allign = left
margin = 0
widthtype = percent
width = 100
height = 26
transparent = true
tintcolor = #ffffff
alpha = 68
setdocktype = true
setpartialstrut = true
}

Plugin {
type = menu
config {
icon = start-here
name = Applications
systemmenu {
}
separator {
}
item {
icon = gnome-settings
name = configure Panel
command = configure
}
}
}

Plugin {
type = space
config {
size = 3
}
}


Plugin {
type = menu
config {
icon = computer
name = System
item {
icon = exit
name = Exit session
command = killall openbox
}
item {
icon = gnome-settings
name = GTK-Switcher
action = switch2
}
item {
icon = gnome-settings
name = GDM Setup
action = gksu gdmsetup
}
item {
icon = gnome-settings
name = Shutdown
action = gksu poweroff
}
item {
icon = gnome-settings
name = Reboot
action = gksu reboot
}
}
}

Plugin {
type = space
config {
size = 8
}
}

Plugin {
type = launchbar
config {
button {
icon = gnome-globe
tooltip = Browse the web
action = firefox
}
}
}

Plugin {
type = launchbar
config {
button {
icon = gnome-terminal
tooltip = Terminal
action = xfce4-terminal
}
}
}

Plugin {
type = launchbar
config {
button {
icon = synaptic
tooltip = Synaptic Package Manager
action = gksu synaptic
}
}
}

Plugin {
type = launchbar
config {
button {
icon = mousepad
tooltip = Editor
action = mousepad
}
}
}

Plugin {
type = launchbar
config {
button {
icon = folder_home
tooltip = Thunar
action = thunar
}
}
}

Plugin {
type = launchbar
config {
button {
icon = gnome-audio
tooltip = alsaplayer
action = alsaplayer
}
}
}

Plugin {
type = launchbar
config {
button {
icon = applets-screenshooter
tooltip = Take a screenshot in 5 seconds (output /home/user/)
action = scrot -cd 5
}
}
}

Plugin {
type = pager
config {
showwallpaper = true
}
}

Plugin {
type = launchbar
config {
button {
icon = audio-volume-high
tooltip = Adjust volumes
action = xterm alsamixer
}
}
}

Plugin {
type = launchbar
config {
button {
icon = process-stop
tooltip = Kill a unresponsive program
action = xkill
}
}
}

Plugin {
    type = space
    expand = true
    config {
        size = 30
    }   
}  


Plugin {
    type = tray
}

# Digital Clock
Plugin {
    type = dclock
    config {
        ClockFmt = %R
        TooltipFmt = %A %x
        Action = xmessage Please define some command &
    }
}

```
//  *** End upper

 Configure Bottom panel for FBpanel
```

nano /etc/fbpanel/lower

```

// *** Begin lower, Copy and paste the following into nano
```

# fbpanel  config file
# see http://fbpanel.sUntitledf.net/docs.html for complete configuration guide

Global {

edge = bottom
allign = left
margin = 0
widthType = percent
width = 100
heightType = pixel
height = 26
roundCorners = false
transparent = true
tintColor = #ffffff
alpha = 39
}

Plugin {
type = space
config {
size = 2
}
}

Plugin {
type = wincmd
config {
icon = gnome-fs-desktop
#image = /usr/share/fbpanel/images/gnome-fs-desktop.svg
tooltip = Left click to iconify all windows. Middle click to shade them.
}
}

Plugin {
type = space
config {
size = 7
}
}

Plugin {
type = taskbar
expand = true
config {
ShowIconified = true
ShowMapped    = true
ShowAllDesks  = false
tooltips = true
IconsOnly = false
MaxTaskWidth = 150
}
}

Plugin {
type = space
config {
size = 3
}
}

Plugin {
type = launchbar
config {
button {
icon = exit
tooltip = Exit session
action = killall openbox
}
}
}

```
// ** End lower

 make fbpanel start on startup
```

nano /etc/xdg/openbox/autostart.sh

```
// *** BEGIN: Paste The following after the last line in the file
```

sleep 0;
feh --bg-scale /usr/share/background.jpg &
fbpanel --profile upper & fbpanel --profile lower &
nm-applet &
conky &

```
// *** END

 Exit the live-cd directory
```

umount -l -f /proc
umount -l -f /sys
umount /dev/pts
exit

```
 Copy and image to the background file,  REPLACE "/home/ubuntu/image.jpg" with the path to your jpeg image, use a jpeg.
```

sudo cp /home/ubuntu/image.jpg ~/work/chroot/usr/share/background.jpg

```
```

for i in ~/work/chroot/proc/* ~/work/chroot/dev/* ~/work/chroot/sys/* ~/work/chroot/tmp/* ~/work/chroot/lost+found
do sudo rm -r ${i}
done

```
 install some packages needed for you system:
```

sudo apt-get install syslinux squashfs-tools mkisofs sbm

```

 make directories to put final image in
```

sudo mkdir image image/casper image/isolinux image/install

```

 The next steps set up the kernel, replace the "**"s with the right numbers
 They are particular to the kernel used for the debootstrap
 for me they are "24" , "16" , "24" , "16" ; respectively
```

sudo cp chroot/boot/vmlinuz-2.6.**-**-generic image/casper/vmlinuz

sudo cp chroot/boot/initrd.img-2.6.**-**-generic image/casper/initrd.gz

```
 These will prepare important files for the cd (it copies them to the image folder), you may or may not need sudo
```

sudo cp /usr/lib/syslinux/isolinux.bin image/isolinux/

sudo cp /boot/memtest86+.bin image/install/memtest
sudo cp /boot/sbm.img image/install/


```
 Make a isolinux.txt file
```

sudo nano image/isolinux/isolinux.txt

```
// *** COPY The following into that file, then save it "Ctrl-O", "Enter", and exit "Ctrl-x":
```

This is an Ubuntu Remix Live CD.

For the default live system, enter "live". 
 To verify the CD for errors, enter "check".
 To run memtest86+, enter "memtest"

```
// *** END isolinux.txt contents


 Generate manifest, for install
```

sudo chroot ~/work/chroot dpkg-query -W --showformat='${Package} ${Version}\n' | sudo tee ~/work/image/casper/filesystem.manifest
sudo cp -v ~/work/image/casper/filesystem.manifest{,-desktop}
REMOVE='ubiquity casper live-initramfs user-setup discover1 xresprobe os-prober libdebian-installer4'
for i in $REMOVE 
do
	sudo sed -i "/${i}/d" ${CD}/${FS_DIR}/filesystem.manifest-desktop
done

```


 Set up Isolinux boot config file
```

sudo nano image/isolinux/isolinux.cfg

```

 add "desktop=wm" to append line of "live lable" where "wm" is your window manager... This is already done for openbox...
 Just after "initrd=..." don't forget a space
// *** COPY The following into that file, then save it "Ctrl-O" and exit "Ctrl-x":
```

DEFAULT live
LABEL live
  menu label ^Start or install Ubuntu
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz desktop=openbox quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel /casper/vmlinuz
  append  boot=casper integrity-check initrd=/casper/initrd.gz quiet splash --
LABEL memtest
  menu label ^Memory test
  kernel /install/memtest
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1

```
// *** END isolinux.cfg contents

 compress the chroot, helps it fit on the cd.
```

sudo mksquashfs chroot image/casper/filesystem.squashfs -nolzma

```
 Create README.diskdefines
```

sudo nano image/README.diskdefines

```

// *** BEGIN: Readme.diskdefines  text:
```


#define DISKNAME  Ubuntu 8.04 "Hardy Heron" - Release i386 **Remix**
#define TYPE  binary
#define TYPEbinary  1
#define ARCH  i386
#define ARCHi386  1
#define DISKNUM  1
#define DISKNUM1  1
#define TOTALNUM  0
#define TOTALNUM0  1


```
// *** END: Readme.diskdefines

get  md5sums and put them into md5sum.txt
```

sudo -s
(cd image && find . -type f -print0 | xargs -0 md5sum > md5sum.txt)
exit

```
 Create iso
```

cd image
sudo mkisofs -r -V "$IMAGE_NAME" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o ../ubuntu-remix.iso .

```
// Your ISO Image should then be in ~/work/ubuntu-remix.iso

---

### Post by jedi453 on 2008-04-29
Just as a reminder that wont work in Qemu, but It works from cd for me.

---

### Post by chris4585 on 2008-04-30
> **jedi453 said:**
> Just as a reminder that wont work in Qemu, but It works from cd for me.

Thank you, i'll have to find some free time to finally do this, thank you so much for spending time on doing this.  I really hope it works

---

### Post by altariel on 2008-04-30
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)
works wonders ... 
so happy that finally it's as easy as in PCLinuxOS to create a live cd of ones installed system!

---

### Post by jedi453 on 2008-07-14
I've made a few liveCD's using this process now. You can change a few settings and end up with different windowmanagers, different panel's, etc. I was just wondering though, Is there a way to reduce ram usage. Even with windowLab it uses about the same amount of ram. I'm wondering if it's xorg. Is there a lightweight, but still fully functional alternative?

P.S.: I've changed the process slightly to add a little more functionality.

Here's the changes:

for /etc/apt/sources.list I used:
```


deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse

deb http://packages.medibuntu.org/ hardy free non-free

```

When it says to add your own packages I added a few:
```

apt-get install genius gnome-genius transmission brasero gaim gimp gdebi midori dillo zip unzip unrar rar lzma lzma-dev abiword gnumeric dvd+rw-tools

```
genius/gnome-genius: great arbitrary precision calculator
transmission: Bittorrent client, in Ubuntu
Brasero: CD/DVD burning, in Ubuntu
midori: Browser, Lighter than Firefox, but similar
dillo: very fast and light browser, not quite as simple to use
zip - lzma: some compression/decompression methodsfor xarchiver
abiword/gnumeric: small light word processor/ spreadsheet
dvd+rw-tools: for brasero, allows one to burn dvd's


I also put the attached (as a .zip) rc.xml this in /etc/skel/.config/openbox/ (In the liveCD's root directory, ~/work/chroot/etc/skel/.config/openbox/)
It's a great little configuration for openbox. It's called Onyx-citrus. I think it gives openbox a nice Ubuntu-like feel. 


P.P.S: I have an iso made. I just need somewhere to post it. I could use bittorrent, but I'm not sure how to make a working torrent. If anyone wants the iso, please just tell me how to make a torrent in transmission (specifically what to use for the announce url) and I can leave my computer on from time to time.

---

### Post by Wild_Doogy on 2009-01-12
INTERESTING THING:

I used my 8GB zipstick as the storage device for the extracting/copying.
It is formated as FAT32 and terminal gave my some interesting stuff when I copied the stuff from the mounted SQUASH to my zipstick, it failed to preserve the ownership of the files. 
My guess is that the fat32 file system cant do ownership.....  
Anyhow, its still extracting so I will see how this plays out  :-)

---

