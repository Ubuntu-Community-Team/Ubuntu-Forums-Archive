---
title: "How to stop linux-image-*-generic interfering with VirtualBox Guest Additions?"
date: 2016-07-01
forum: Virtualisation
---

### Post by &amp;KyT$0P# on 2016-07-01
I have a VirtualBox VM running Xubuntu 16.04 LTS amd64 as the guest.
The kernel packages for Ubuntu 16.04, for instance [linux-image-4.4.0-28-generic]("http://packages.ubuntu.com/xenial-updates/amd64/linux-image-4.4.0-28-generic/filelist") and [linux-image-extra-4.4.0-28-generic]("http://packages.ubuntu.com/xenial-updates/amd64/linux-image-extra-4.4.0-28-generic/filelist"), include kernel modules that are part of VirtualBox Guest Additions.  These "stray" kernel modules are interfering significantly with the ability to install and use Guest Additions.

Because they are a special Ubuntu version, installing Guest Additions from the VirtualBox ISO does not work properly (if at all - installing a Guest Additions version older than the kernel modules version, such as 5.0.12, doesn't even allowed).  This means I don't get to have 3D acceleration inside the VM.  So I tried installing from the Ubuntu package repositories, which worked initially, but broke upon apt-get dist-upgrade due to dkms detecting the stray modules.

Apparently, after purging the Ubuntu package Guest Additions, the Guest Additions version 5.0.20 could be installed fine from the ISO, but it asked to confirm removing leftover parts of a 3rd-party install or something like that, and I said yes.  (Looks like it deleted the modules from linux-image-*-generic packages.)
Guest Additions *seems* to work fine at this point, without all the glitching and application-crashing I saw before, but I'm not sure how stable this "good" setup is and I somehow doubt that it will stay good after the next dist-upgrade...

I'm not happy about just deleting the stray modules and reboot, because the next kernel upgrade will include them again.  And unless I'm misunderstanding something about the nature of updates to 16.04 LTS, I need to keep the system fully updated irregularly, so ignoring this and leaving the kernel(s) as-is / not updated won't work either.

So how to "permanently" disable or get rid of these stray modules in such a way that Guest Additions installed from the ISO won't also be disabled or otherwise impaired?

Thanks

---

### Post by Habitual on 2016-07-02
You didn't specify which version of Virtualbox or how that version got installed.
I have in the past installed VBoxGuestAdditions*.iso files and those remain on my hard drive for some unknown reason.
I have Oracle Virtualbox 5.0.24 from [the Virtualbox site]("https://www.virtualbox.org/wiki/Linux_Downloads") and I'm not on Ubuntu.

I have these remnants on my hard drive:
```
/home/jj/.VirtualBox/VBoxGuestAdditions_4.3.18.iso
/home/jj/.VirtualBox/VBoxGuestAdditions_4.3.10.iso
/usr/share/virtualbox/VBoxGuestAdditions.iso
```

My hope is that the newer should replace the former, but I have no reason to install [the newer.]("http://download.virtualbox.org/virtualbox/5.0.16/VBoxGuestAdditions_5.0.16.iso") 
Interesting,
Good Luck.

---

### Post by &amp;KyT$0P# on 2016-07-02
Oops, sorry.. VirtualBox version is 5.0.2 (and can't upgrade atm) but I don't know what you mean by "how that version got installed"?

Guest Additions 5.0.2 doesn't work with Ubuntu 16.04 or various other relatively recent OSes, so I keep a few newer Guest Additions ISOs on hand.

---

### Post by MAFoElffen on 2016-07-02
He asked if your original install of Virtualbox was from Oracle, from VirtualBox.org, or from the Ubuntu Repo's.

---

### Post by &amp;KyT$0P# on 2016-07-02
It's a .deb package I downloaded from [https://www.virtualbox.org/wiki/Linux_Downloads]("https://www.virtualbox.org/wiki/Linux_Downloads") along with the Extension Pack.


* To clarify: the host OS is Lubuntu 14.04, and these Guest Additions ISOs were never "installed" on the host nor are they remnants of anything; I manually downloaded them.

---

### Post by &amp;KyT$0P# on 2016-07-03
Actually I noticed that there is a /etc/kernel/postinst.d directory containing various scripts which get executed on every kernel upgrade... this looks interesting here, but I can't find enough documentation about it to make use of it.
Specifically, my questions are, how are the scripts in postinst.d passed information about the new kernel, and how to guarantee my script to run first?

---

### Post by MAFoElffen on 2016-07-03
Next is... that version of the VirtualBox Guest Additions ISO, that comes with VirtualBox 5.0.2... only supports LTS versions up to Ubuntu 14.04.3. You will need to update VirtualBox to use a Guest Additions ISO that supports 16.04.

So right at this moment-- VirtualBox 5.0.2 is old. Current is 5.0.20. Version 5.0.20 supports the newer Linux kernel series.

If you doubt me on that, look at the VirtualBox.org repo for the VM Guest Additions ISO, version 5.0.2...

---

### Post by &amp;KyT$0P# on 2016-07-03
I have no doubt that the 5.0.2 Guest Additions don't work ;)
I've used newer Guest Additions with older VirtualBox before without any issues.. the problem here is not the newer kernel itself, but the fact the Ubuntu package of the kernel comes with some VirtualBox Guest Additions modules.
Are you suggesting that upgrading the host's VirtualBox would block the stray kernel modules inside the guest? :confused:

---

### Post by MAFoElffen on 2016-07-03
Well, if no issues with a newer Guest Additions iso, then try that. If it spits an error on the version number of the newer ISO, then upgrade the VirtualBox version...

EDIT-- Wait... is the Kernel version you are having an issue with 4.4.0-28?

if so, then 
```

sudo apt-cache show gcc

```
and tell me which version is there...

---

### Post by &amp;KyT$0P# on 2016-07-03
Yes it's the upgrade to 4.4.0-28.

Kernel 4.4.0-24 (the only other kernel installed) has the same issue with installing Guest Additions from the ISO, but there I could at least install the Guest Additions from the package manager without problems.

---
[FONT=Courier New]sudo apt-cache gcc[/FONT] gives this
```
E: Invalid operation gcc
```

---

### Post by MAFoElffen on 2016-07-03
My mistake, edited my last to reflect:
```

sudo apt-cache show gcc

```
 Mine shows that the version is [4:5.3.1-1ubuntu1]("https://launchpad.net/ubuntu/xenial/arm64/gcc/4:5.3.1-1ubuntu1")... For VirtualBox, using the newer kernels, the GCC compiler needs to be gcc version (the part past the colon) of greater than gcc version 4.9.

---

### Post by deadflowr on 2016-07-03
apt-cache needs another command.
several include showpkg policy show
example:
```
apt-cache policy gcc
```
gives this (for 16.04)
```
gcc:
  Installed: 4:5.3.1-1ubuntu1
  Candidate: 4:5.3.1-1ubuntu1
  Version table:
 *** 4:5.3.1-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
```

as there is no need to read the apt-cache commands as root, no need for sudo when you run them.

---

### Post by &amp;KyT$0P# on 2016-07-03
> **MAFoElffen said:**
> My mistake, edited my last to reflect:
```

sudo apt-cache show gcc

```
 Mine shows that the version is [4:5.3.1-1ubuntu1]("https://launchpad.net/ubuntu/xenial/arm64/gcc/4:5.3.1-1ubuntu1")... For VirtualBox, using the newer kernels, the GCC compiler needs to be gcc version (the part past the colon) of greater than gcc version 4.9.
Same here:
```
$ apt-cache show gcc
Package: gcc
Priority: optional
Section: devel
Installed-Size: 44
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GCC Maintainers <debian-gcc@lists.debian.org>
Architecture: amd64
Source: gcc-defaults (1.150ubuntu1)
**[COLOR="#FF0000"]Version: 4:5.3.1-1ubuntu1[/COLOR]**
Provides: c-compiler
Depends: cpp (>= 4:5.3.1-1ubuntu1), gcc-5 (>= 5.3.1-3~)
Recommends: libc6-dev | libc-dev
Suggests: gcc-multilib, make, manpages-dev, autoconf, automake, libtool, flex, bison, gdb, gcc-doc
Conflicts: gcc-doc (<< 1:2.95.3)
Filename: pool/main/g/gcc-defaults/gcc_5.3.1-1ubuntu1_amd64.deb
Size: 5244
MD5sum: df1516b203a66a86a728eab7a4c349e8
SHA1: 93d83d4bc56d8720faaca87cd2b44dfdd4c94fa8
SHA256: 4afc5ce013cc7a562692eca2e4f429029974afca5fee02a8fa166341553a34bd
Description-en: GNU C compiler
 This is the GNU C compiler, a fairly portable optimizing compiler for C.
 .
 This is a dependency package providing the default GNU C compiler.
Description-md5: c7efd71c7c651a9ac8b2adf36b137790
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Build-Essential: yes
Origin: Ubuntu
Supported: 5y
Task: ubuntu-desktop, ubuntu-usb, kubuntu-desktop, kubuntu-full, edubuntu-desktop, edubuntu-usb, xubuntu-core, xubuntu-desktop, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, ubuntustudio-desktop-core, ubuntustudio-desktop, ubuntu-gnome-desktop, ubuntukylin-desktop


```

---

### Post by &amp;KyT$0P# on 2016-07-12
I'm confused now.  Wanted to get exact error message(s) to post here, so I set up a second Xubuntu 16.04 VM, installed Guest Additions 5.0.20, reboot, upgraded the kernel, and... no problems? :confused:
So this means, either I initially clicked the wrong Guest Additions ISO, or I've screwed up my 16.04 VM some other way :-k

(On a maybe-related note, it seems that postinst.d scripts are executed alphabetically, so if I end up needing to go that route, have to make sure its name comes before "dkms" in the alphabet.)

---

### Post by &amp;KyT$0P# on 2016-07-18
I did another kernel upgrade on this VM, and it's not "giving errors", just that the version of the kernel modules provided by Guest Additions has to be newer than 5.0.18_Ubuntu (well, according to dkms anyway).  I was testing the "extra" VM with Guest Additions 5.0.20 - and now I conclude that if installed Guest Additions is newer than 5.0.18_Ubuntu, there should be no issues with kernel upgrades.
Some of the modules from the package manager Guest Additions are newer than that and some are not.  The mixed result just happens to seem to work as expected. 8-[

So the solution here is either to just use Guest Additions 5.0.20 or later, or guess my way through writing a postinst script to delete the "stock" Guest Additions related kernel modules.  (I might end up trying to do both at once actually. ;) )

---

### Post by MAFoElffen on 2016-07-18
So it is solved with the now new kernel version for Ubuntu 14.04? Whic kernel version is that now?

So for others reading this later, to summarize which kernel had a problem with which version of VirtualBox, (so others know)
```

VirtualBox version 5.0.2 has problems running on Linux kernel version 4.4.0-28

```
I take it by your last post that you now confirm that it is doing okay for you with the new kernel. If now solved. please mark your thread as solved so other may find a solution to their similar problems.

---

### Post by &amp;KyT$0P# on 2016-07-18
> So it is solved with the now new kernel version for Ubuntu 14.04?
Not solved quite yet but at least I know now that it's purely about the Guest Additions version string - and so a recent enough Guest Additions is supposed to "just work" in this situation regardless of how it's installed.  I also looked at the postinst scripts on my system, and it looks like the new kernel version is passed in the command line?  Will have to play with that more.

The situation with the kernel is still the same.  What changed on this VM is that the package manager Guest Additions, which I had left installed for the mean time, got an update as well.  It was with that update I saw the dkms messages.

> Whic kernel version is that now?
Currently on 4.4.0-31-generic.

> If now solved. please mark your thread as solved so other may find a solution to their similar problems.
I would like to post a working postinst script before marking this solved.

---

### Post by &amp;KyT$0P# on 2016-07-19
It's solved now  :KS

To summarize and tie up the remaining loose ends here:

Solution #1 is, as said above, to just use the VirtualBox Guest Additions 5.0.20 or newer.

Solution #2, the use of postinst.d script, is required if using Guest Additions 5.0.18 or earlier, and maybe-required if using the Guest Additions from the package manager.  It works mostly as expected, but there is a big catch.  If reinstalling an existing kernel, and this postinst.d script is set up, you must completely reinstall the Guest Additions as well - and, I think, do so while running that specific kernel.  Otherwise the result is broken Guest Additions with that kernel.

Anyway, with that said...

Save this as /etc/kernel/postinst.d/cvboxguest:
```
#!/bin/bash
[ -n "$1" ] && rm -fvR "/lib/modules/$1/kernel/ubuntu/vbox"
```
Set it executable:
```
sudo chmod +x /etc/kernel/postinst.d/cvboxguest
```
And that's it, everything should be taken care of at the next kernel upgrade.

---

