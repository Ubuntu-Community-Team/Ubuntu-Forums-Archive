---
title: "multiarch amd64 on i386"
date: 2011-11-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by seeker5528 on 2011-11-02
If you haven't broke your system yet, you aren't trying hard enough.

If you are a masochist, don't think the risk of breakage will be high enough this development cycle, etc... etc... enable multiarch in your i386 installation (assuming you have a 64 bit processor of course) then have a go at installing :amd64 packages.

To enable, create a file in '/etc/dpkg/dpkg.cfg.d/' named 'multiarch' with the contents ```
foreign-architecture amd64
```

Then update the package list```
sudo apt-get update
```


Then to install a 64 bit linux-image package you need some other packages installed first ```
sudo apt-get install gcc-4.6-base:amd64 libacl1:amd64 libattr1:amd64 libc6:amd64 libdbus-1-3:amd64 libgcc1:amd64 libselinux1:amd64 libudev0:amd64 linux-base
```

You can't have the same version of kernel in both i386 and amd64 varieties so you need an older kernel image to boot into if you want the 64 bit one to be current, so if you don't already have one installed you may have to visit [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to download an older kernel-image package to install.

Reboot.

On the grub menu, go to the 'Previous Linux versions' entry and choose one of the kernels listed there to boot. 

Once booted with an older kernel, remove the current version of the kernel image package in synaptic, letting it remove the metapackages that depend on it as well.

The kernel packages are not packaged in a multiarch friendly way, you can install the image and it works, but you have to manually download it then force it to install, so you need to know the current package name if you want to use apt do download it, it's the numbers between image and generic that change linux-image-3.1.0-2-generic_3.1.0-2.3_amd64.deb

So if you make a directory dedicated to the purpose and change to it:

```
mkdir DebDownload
cd DebDownload
```

For the kernel image listed above the download/install process might look something like ```
apt-get download linux-image-2.1.0-2-generic:amd64
dpkg -i --force-depends *.deb
```

With the current amd64 package for the kernel image installed, it should be the default kernel during boot up, so after rebooting you should be running the 64 bit kernel.

So far this is relatively safe, easy to undo.

Since the kernel image package is not friendly to multiarch on i386 and you have to force it to install, apt will think it's broken, which means 'apt-get install' and Synaptic and other apt front ends won't work either because the will all want you to deal with the 'broken' package before allowing you to install anything else.

What I've been doing is using Synaptic, marking the kernel-image package for removal so Synaptic is happy, then selecting the packages I want to install to see what Synaptic would want to install or remove. You don't want to let Synaptic actually install/remove anything because it would cause your 64 bit kernel to be removed, which you need for the 64 bit stuff.

If Synaptic doesn't want to remove anything, that's pretty easy to deal with. Select your packages you want to upgrade/install go to 'File --> Generate package download script' point Synaptic at your 'DebDownload' directory (or whatever you decided to name it) as the location to save the script using a name like 'upgrades' for the name of the script. To install from the generated list you would then do ```
cd DebDownload
./upgrades
sudo dpkg -i *.deb
```

After doing this a few times Synaptic should remember the location as a 'recent location' when you choose to generate the script and if you don't delete the script you can just click on the existing script and Synaptic will overwrite it when generating the new script. 

To keep things somewhat sane you would want to move or delete the existing deb files after they have been successfully installed. Things that did install previously may have issues when upgrading so there is an argument for keeping previous versions of the packages around so you can downgrade if necessary.

If things need to be removed to install :amd64 versions, then I try to keep the changes to a single package or a short list and do ```
apt-get download package1 package2 etc..
sudo dpkg -r package1 package2 etc...
sudo dpkg -i *.deb
``` 

If there are complaints about dependencies when doing 'dpkg -r' when removing the things Synaptic indicated would be removed then do ```
sudo dpkg -r --force-depends package1 package2 etc..
```for the packages dpkg complained about before installing the packages that were downloaded.

If there is a complaint about a package not being removed because it is an essential package you *could* do ```
dpkg -r --force-depends --force-remove-essential some-package
``` but you might want to think twice about that, some of these can be done without too much fuss, others might totally break the system if they are removed. Some essential packages that include files that are needed during package installation could be dealt with by making a copy of the necessary executable in some alternate location in the path so after the essential package is removed there is a version of the executable available to install the :amd64 package, then delete the copy in the alternate location after the installation is successful.

Since there is an elevated risk of breakage you probably want to be familiar with the chroot process. Personally I use [System Rescue CD](http://www.sysresccd.org/Main_Page), choosing the 64 bit kernel option from it's boot menu.

Once booted do ```
fdisk -l
``` to determine which partition is your Ubuntu partition, if you don't already know. 

Then you need to make a mount point and do some mounting, if your ubuntu parition was '/dev/sda1' ```
cd /mnt
mkdir ubuntu
mount /dev/sda1 ubuntu
mount -o bind /dev ubuntu/dev
mount -o bind /proc ubuntu/proc
mount -o bind /sys ubuntu/sys
```

Then, since System Rescue CD doesn't use bash as it's shell, you have to specify that you want to run bash when you chroot your Ubuntu partition.

```
chroot ubuntu bash
```

Not sure what all it makes sense to bug report for multiarch issues at this time since multiarch on i386 will probably be unsupported for a while, but if you successfully installed something, then an update with no new dependencies breaks it, that seems like a likely suspect.

So far I have one bug report [bug #885361](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/885361), don't know how much I will really get into it.

EDIT: Looks like my bug was identified as a duplicate in the time it took to write this post [bug #871083](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/871083). 

Later, Seeker

---

### Post by MadCow108 on 2011-11-02
whats the point of this?
you have some few applications that require 64 bit but want the rest to stay 32 bit?

I guess your time is better spent in helping out with the x32 abi which will do what you want just much better.
[http://sites.google.com/site/x32abi/](http://sites.google.com/site/x32abi/)

---

### Post by seeker5528 on 2011-11-02
> **MadCow108 said:**
> whats the point of this?

The point is eventually (when is a whole other question) you should be able to migrate from i386 to a fully 64 bit system.

Short term it's more interesting and more useful for those who have to odd thing that needs 32 bit.

In the long run as the issues get sorted out, I expect the more-useful-to-more-people purpose will be to migrate them to 64 bit when upgrading to a new release or allowing people to stick with a generally 32 bit system while installing 64 bit versions of software where 64 bit makes more difference, media encoders, video editing, CAD, etc...

Personally I don't re-install unless a hardware issue forces it or I totally screw up my system to the point where I can't limp along with some quirky issue until an updated package fixes it or I figure out how to fix it.

Both of my systems I do stuff with when it's slow at work are 32 bit installations, one of them recently got upgraded to a 64 bit processor.

My home system with Ubuntu is 32 bit because my hard drive where I had the 64 bit version installed died and I chose to resurrect an older 32 bit install off of a partition on another computer, that was unbootable because the partition ran out of space, which was 32 bit because the original install was a derivative of Ubuntu that was only available in a 32 bit version. Takes less time to wrangle the boot stuff to the changed device name than to reinstall, since I remove some of the default stuff and install other KDE, Gnome and Lubuntu stuff.

My machine that I use the most is a 64 bit Debian installation, has been for quite a while. Don't see that it makes that big a difference generally speaking, so it's not a real pressing thing to get the 32 bit installs migrated to 64 bit, but eventually even the netbook and other portable devices are going to want to be 64 bit.

On the resurrected install I did have to upgrade through 3 releases and then to the development release of Ubuntu to get current, so it did take longer to get current than if I had installed fresh, but the initial get-it-going-with-the-software-I generally-use time was shorter.

Later, Seeker

---

### Post by TerminX on 2011-11-04
> **seeker5528 said:**
> The point is eventually (when is a whole other question) you should be able to migrate from i386 to a fully 64 bit system.
You can do that now if you know what you're doing and don't mind a little pain and suffering.  I did it myself on the system I'm typing this message on now... no chroot, no debootstrap, nothing but busybox-static, dpkg/dpkg-deb and a whole lot of voodoo. ;)

---

### Post by seeker5528 on 2011-11-04
> **TerminX said:**
> You can do that now if you know what you're doing and don't mind a little pain and suffering.

It's not worth the effort for most people. I did it for my Debian install before the multiarch stuff started, had to chroot from System Rescue CD 2 or 3 times during the process, should be easier now with multiarch, but not quite there yet.

At least Debian helps you out by providing an i386 package of a 64 bit kernel image, never understood why this wasn't done in Ubuntu.

If I remember correctly, something provided in base files provides the package management stuff with the information about what your native architecture is, so possibly 'dpkg --force-architecture' on the basefiles:amd64 package and setting the foreign architecture to i386 might be manageable. Any way you do it, it's going to be some work.

Later, Seeker

---

