---
title: "Problem updating ubuntu (unmet dependencies + mismatch on package)"
date: 2018-03-27
forum: Ubuntu Development Version
---

### Post by jorritTyb on 2018-03-27
Yesterday I tried to update my ubuntu 18 system and now the nvidia driver is no longer working. I tried to do sudo apt-get update followed by sudo apt-get upgrade but that gives me the following errors:

```

The following packages have unmet dependencies:
  libnvidia-ifr1-390 : Depends: libnvidia-gl-390 but it is not installed
  libnvidia-ifr1-390:i386 : Depends: libnvidia-gl-390:i386 but it is not installed
  nvidia-driver-390 : Depends: libnvidia-gl-390 (= 390.42-0ubuntu1+gpu18.04.1) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution)

```

So I try the apt --fix-broken install but this gives me:

```

Preparing to unpack .../libnvidia-gl-390_390.42-0ubuntu1+gpu18.04_1_amd64.deb ...
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /user/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package

```

I also tried to purge all nvidia packages but that didn't work either.

Any solutions to this? If possible I'd like to revert whatever was updated that causes this but no idea how to do that.

Thanks

---

### Post by wildmanne39 on 2018-03-27
*Thread moved to **Ubuntu Development Version, a more appropriate forum**.*

---

### Post by SeijiSensei on 2018-03-27
Many people are having issues with NVIDIA support in the upcoming release. I've just decided to wait until the actual release and am relying on the nouveau driver for now.

---

### Post by jorritTyb on 2018-03-27
Ok that's fine but how do I recover from this? At this moment I cannot update/upgrade anything as I get these errors

---

### Post by #&amp;thj^% on 2018-03-27
For what ever reason I have noticed a few users here using "apt-get" instead of just "apt" from 16.04 and 17.10 and newer. (Seems to cause apt related problems)
EDIT: These problems are seen with the combination of "apt-get" and "apt".

And have you yet tried: 
```

sudo apt-get clean
sudo apt-get update
sudo apt-get install -f
sudo dpkg -a --configure
sudo apt-get dist-upgrade
```

I myself rarely use apt-get any longer>(To be noted only)
EG:
```
sudo apt clean
sudo apt update
sudo apt install -f
sudo dpkg -a --configure
sudo apt dist-upgrade
Or
sudo apt full-upgrade
```
I'm not saying this will fix your present problem, but just what I have noticed.

---

### Post by tinylagarto on 2018-03-27
> **jorritTyb said:**
> I tried to do sudo apt-get update followed by sudo apt-get upgrade but that gives me the following errors:


Did you try a:

```
sudo apt dist-upgrade
```

That is what I use exclusively, especially when you are on a development release, as it ensures to replace all older packages with newer versions and even remove older packages and dependencies.

---

### Post by jorritTyb on 2018-03-27
These commands didn't fix it. sudo dpkg -a --configure (after doing the other commands you mentioned) works a long time and then says:

> 
Errors were encountered while processing:
 nvidia-driver-390
 libnvidia-ifr1-390:amd64
 libnvidia-ifr1-390:i386


A dist-upgrade or even a full-upgrade doesn't help either.

Almost every apt (or apt-get) command that I try complains about 'unmet dependencies' and recommends that I do 'apt --fix-broken install'. However that command keeps erroring out with the 'dpkg-divert' error. Is there a way of force removing those nvidia packages?  I tried purge but that gives the errors above again.

Edit: if all else fails I'm willing to go back to the normal version of ubuntu too. However, no idea how to do that now given the state this is in?


So no matter what I do I can't seem to get rid of these three erroring packages. Any clues? Thanks!

---

### Post by jorritTyb on 2018-03-28
Nobody has any idea on how I can get unstuck here? Thanks

---

### Post by cariboo on 2018-03-28
If you have synaptic installed you could try and fix it that way by removing the broken packages.

---

### Post by jorritTyb on 2018-03-28
How would I do that with synaptic? Note that I cannot open a graphical environment (broken drivers). Everything has to be done with commandline

---

### Post by mc4man on 2018-03-28
The dirvert deal mentioned nvidia-340, were you using that at some point?
Also you're using the ppa , for a little bit their 18.04 packages won't have worked, should be ok now & there is a new build moments ago.

Have you tried from a tty - 
```
sudo apt purge *nvidia*
```

---

### Post by jorritTyb on 2018-03-28
Oh indeed. Simply booted up my computer and everything is suddenly fine! Thanks!

---

### Post by jorritTyb on 2018-03-28
Well solved... I still can't switch to the nvidia-390 drivers from within the Driver Manager and as I do a lot of 3D work I actually need that driver. So if there is a solution to that then that would be nice too. The 390 driver is listed and marked as recommended but if I select it the list refreshes and it goes back to the X.Org one

Ok so now that I'm back in my system I can easier paste error messages. Here is a summary:

First I did: sudo apt purge *nvidia*:

```

Reading package lists... Done
Building dependency tree        
Reading state information... Done
Note, selecting 'boinc-nvidia-cuda' for glob '*nvidia*'
Note, selecting 'nvidia-390-dev' for glob '*nvidia*'
...
Note, selecting 'libnvidia-common-390' instead of 'libnvidia-common'
Note, selecting 'nvidia-kernel-source-390' instead of 'nvidia-kernel-source'
Note, selecting 'nvidia-utils-390' instead of 'nvidia-smi'
Note, selecting 'nvidia-utils-390' instead of 'nvidia-utils'
...
Package 'libnvidia-gl-390' is not installed, so not removed
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libcuinj64-9.1 : Depends: libcuda1 (>= 387.26) but it is not installable or
                           libcuda-9.1-1
 libnvidia-ifr1-390:i386 : Depends: libnvidia-gl-390:i386 but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

Ok then I do: sudo apt clean. No problems.

Then: sudo apt update:

```

Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:2 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic InRelease                                                                      
Hit:3 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) bionic InRelease                                                                         
Hit:4 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) bionic-updates InRelease                                           
Hit:5 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) bionic-backports InRelease      
Ign:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release
Reading package lists... Done
Building dependency tree        
Reading state information... Done
242 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

Then: sudo apt install -f:

```

Reading package lists... Done
Building dependency tree        
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  bbswitch-dkms lib32gcc1 libc6-i386 libcapnp-0.6.1 libgraphite2-3:i386 libharfbuzz0b:i386 libicu-le-hb0:i386 libllvm5.0 libllvm5.0:i386 libmirclient9 libmircommon7 libmircore1 libmirprotobuf3 libruby2.3 linux-image-4.2.0-42-generic
  linux-image-4.4.0-34-generic linux-image-extra-4.2.0-42-generic linux-image-extra-4.4.0-34-generic nvidia-prime ruby2.3
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
The following NEW packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
0 upgraded, 2 newly installed, 0 to remove and 242 not upgraded.
28 not fully installed or removed.
Need to get 29,1 MB of archives.
After this operation, 147 MB of additional disk space will be used.
Do you want to continue? [Y/n]  
Get:1 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic/main i386 libnvidia-gl-390 i386 390.48-0ubuntu0~gpu18.04.1 [14,8 MB]
Get:2 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic/main amd64 libnvidia-gl-390 amd64 390.48-0ubuntu0~gpu18.04.1 [14,3 MB]                                                                                                     
Fetched 29,1 MB in 13s (2.225 kB/s)                                                                                                                                                                                                          
Setting up libsystemd0:amd64 (237-3ubuntu6) ...
(Reading database ... 347234 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-390_390.48-0ubuntu0~gpu18.04.1_i386.deb ...
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.48-0ubuntu0~gpu18.04.1_i386.deb (--unpack):
 new libnvidia-gl-390:i386 package pre-installation script subprocess returned error exit status 2
Preparing to unpack .../libnvidia-gl-390_390.48-0ubuntu0~gpu18.04.1_amd64.deb ...
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.48-0ubuntu0~gpu18.04.1_amd64.deb (--unpack):
 new libnvidia-gl-390:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-390_390.48-0ubuntu0~gpu18.04.1_i386.deb
 /var/cache/apt/archives/libnvidia-gl-390_390.48-0ubuntu0~gpu18.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Then I try: dkpg -a --configure:

```

Setting up libudev1:i386 (237-3ubuntu6) ...
Setting up nvidia-kernel-source-390 (390.48-0ubuntu0~gpu18.04.1) ...
dpkg: dependency problems prevent configuration of nvidia-driver-390:
 nvidia-driver-390 depends on libnvidia-gl-390 (= 390.48-0ubuntu0~gpu18.04.1); however:
  Package libnvidia-gl-390:amd64 is not installed.

dpkg: error processing package nvidia-driver-390 (--configure):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead (0.100.0-20) ...
ureadahead will be reprofiled on next reboot
Setting up libnvidia-fbc1-390:i386 (390.48-0ubuntu0~gpu18.04.1) ...
Setting up libnvidia-fbc1-390:amd64 (390.48-0ubuntu0~gpu18.04.1) ...
Setting up libsystemd0:i386 (237-3ubuntu6) ...
Processing triggers for initramfs-tools (0.130ubuntu3) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-12-generic
dpkg: dependency problems prevent configuration of libnvidia-ifr1-390:amd64:
 libnvidia-ifr1-390:amd64 depends on libnvidia-gl-390; however:
  Package libnvidia-gl-390:amd64 is not installed.

dpkg: error processing package libnvidia-ifr1-390:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnvidia-ifr1-390:i386:
 libnvidia-ifr1-390:i386 depends on libnvidia-gl-390; however:
  Package libnvidia-gl-390:i386 is not installed.

dpkg: error processing package libnvidia-ifr1-390:i386 (--configure):
 dependency problems - leaving unconfigured
Setting up libnvidia-compute-390:amd64 (390.48-0ubuntu0~gpu18.04.1) ...
Setting up libnvidia-compute-390:i386 (390.48-0ubuntu0~gpu18.04.1) ...
Setting up nvidia-dkms-390 (390.48-0ubuntu0~gpu18.04.1) ...
dpkg: error: version '-' has bad syntax: revision number is empty
dpkg: error: version '-' has bad syntax: revision number is empty
dpkg: error: version '-' has bad syntax: revision number is empty
dpkg: error: version '-' has bad syntax: revision number is empty
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Loading new nvidia-390.48 DKMS files...
Building for 4.15.0-12-generic
Building for architecture x86_64
Building initial module for 4.15.0-12-generic
Done.

nvidia:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-12-generic/updates/dkms/

nvidia-modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-12-generic/updates/dkms/

nvidia-drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-12-generic/updates/dkms/

nvidia-uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-12-generic/updates/dkms/

depmod...

DKMS: install completed.
Setting up libnvidia-cfg1-390:amd64 (390.48-0ubuntu0~gpu18.04.1) ...
Setting up xserver-xorg-video-nvidia-390 (390.48-0ubuntu0~gpu18.04.1) ...
Processing triggers for libc-bin (2.27-0ubuntu2) ...
Setting up udev (237-3ubuntu6) ...
update-initramfs: deferring update (trigger activated)
Setting up systemd (237-3ubuntu6) ...
Processing triggers for man-db (2.8.2-1) ...
Setting up libnvidia-decode-390:amd64 (390.48-0ubuntu0~gpu18.04.1) ...
Setting up libnvidia-decode-390:i386 (390.48-0ubuntu0~gpu18.04.1) ...
Processing triggers for dbus (1.12.2-1ubuntu1) ...
Setting up nvidia-compute-utils-390 (390.48-0ubuntu0~gpu18.04.1) ...
Setting up libnvidia-common-390 (390.48-0ubuntu0~gpu18.04.1) ...
Setting up e2fsprogs-l10n (1.44.1-1) ...
Setting up libnss-systemd:amd64 (237-3ubuntu6) ...
Setting up libpam-systemd:amd64 (237-3ubuntu6) ...
Setting up libnvidia-encode-390:amd64 (390.48-0ubuntu0~gpu18.04.1) ...
Setting up libnvidia-encode-390:i386 (390.48-0ubuntu0~gpu18.04.1) ...
Setting up nvidia-compute-no-dkms-390 (390.48-0ubuntu0~gpu18.04.1) ...
Setting up nvidia-utils-390 (390.48-0ubuntu0~gpu18.04.1) ...
Setting up nvidia-compute-390 (390.48-0ubuntu0~gpu18.04.1) ...
Processing triggers for initramfs-tools (0.130ubuntu3) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-12-generic
Processing triggers for libc-bin (2.27-0ubuntu2) ...
Errors were encountered while processing:
 nvidia-driver-390
 libnvidia-ifr1-390:amd64
 libnvidia-ifr1-390:i386
jorrit@JorritsComputer:~$ sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree        
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libnvidia-ifr1-390 : Depends: libnvidia-gl-390 but it is not installed
 libnvidia-ifr1-390:i386 : Depends: libnvidia-gl-390:i386 but it is not installed
 nvidia-driver-390 : Depends: libnvidia-gl-390 (= 390.48-0ubuntu0~gpu18.04.1) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

And: sudo apt full-upgrade:

```

Reading package lists... Done
Building dependency tree        
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libnvidia-ifr1-390 : Depends: libnvidia-gl-390 but it is not installed
 libnvidia-ifr1-390:i386 : Depends: libnvidia-gl-390:i386 but it is not installed
 nvidia-driver-390 : Depends: libnvidia-gl-390 (= 390.48-0ubuntu0~gpu18.04.1) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
jorrit@JorritsComputer:~$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  bbswitch-dkms lib32gcc1 libc6-i386 libcapnp-0.6.1 libgraphite2-3:i386 libharfbuzz0b:i386 libicu-le-hb0:i386 libllvm5.0 libllvm5.0:i386 libmirclient9 libmircommon7 libmircore1 libmirprotobuf3 libruby2.3 linux-image-4.2.0-42-generic
  linux-image-4.4.0-34-generic linux-image-extra-4.2.0-42-generic linux-image-extra-4.4.0-34-generic nvidia-prime ruby2.3
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
The following NEW packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
0 upgraded, 2 newly installed, 0 to remove and 242 not upgraded.
3 not fully installed or removed.
Need to get 0 B/29,1 MB of archives.
After this operation, 147 MB of additional disk space will be used.
Do you want to continue? [Y/n]  
(Reading database ... 347234 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-390_390.48-0ubuntu0~gpu18.04.1_i386.deb ...
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.48-0ubuntu0~gpu18.04.1_i386.deb (--unpack):
 new libnvidia-gl-390:i386 package pre-installation script subprocess returned error exit status 2
Preparing to unpack .../libnvidia-gl-390_390.48-0ubuntu0~gpu18.04.1_amd64.deb ...
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.48-0ubuntu0~gpu18.04.1_amd64.deb (--unpack):
 new libnvidia-gl-390:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-390_390.48-0ubuntu0~gpu18.04.1_i386.deb
 /var/cache/apt/archives/libnvidia-gl-390_390.48-0ubuntu0~gpu18.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

sudo apt --fix-broken install gives me:

```

Reading package lists... Done
Building dependency tree        
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  bbswitch-dkms lib32gcc1 libc6-i386 libcapnp-0.6.1 libgraphite2-3:i386 libharfbuzz0b:i386 libicu-le-hb0:i386 libllvm5.0 libllvm5.0:i386 libmirclient9 libmircommon7 libmircore1 libmirprotobuf3 libruby2.3 linux-image-4.2.0-42-generic
  linux-image-4.4.0-34-generic linux-image-extra-4.2.0-42-generic linux-image-extra-4.4.0-34-generic nvidia-prime ruby2.3
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
The following NEW packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
0 upgraded, 2 newly installed, 0 to remove and 242 not upgraded.
3 not fully installed or removed.
Need to get 0 B/29,1 MB of archives.
After this operation, 147 MB of additional disk space will be used.
Do you want to continue? [Y/n]  
(Reading database ... 347234 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-390_390.48-0ubuntu0~gpu18.04.1_i386.deb ...
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.48-0ubuntu0~gpu18.04.1_i386.deb (--unpack):
 new libnvidia-gl-390:i386 package pre-installation script subprocess returned error exit status 2
Preparing to unpack .../libnvidia-gl-390_390.48-0ubuntu0~gpu18.04.1_amd64.deb ...
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.48-0ubuntu0~gpu18.04.1_amd64.deb (--unpack):
 new libnvidia-gl-390:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-390_390.48-0ubuntu0~gpu18.04.1_i386.deb
 /var/cache/apt/archives/libnvidia-gl-390_390.48-0ubuntu0~gpu18.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


So with all this I'm still left with a system that I cannot update as the package system is broken and I also cannot go back to the nvidia 390 drivers.

Synaptic is also throwing all kinds of errors like this:

```

E: /tmp/apt-dpkg-install-doqeuC/188-libnvidia-gl-390_390.42-0ubuntu1_i386.deb: new libnvidia-gl-390:i386 package pre-installation script subprocess returned error exit status 2

```

BTW. I tried to remove the ppa too but I simply can't seem to get rid of this nvidia-390 errors.


Edit: ok. So even though synaptic gave lots of errors it did fix some things because after doing that and repeating the commands above everything is now fine. I no longer get 'broken package / dependency' errors and I can select the 'Using NVIDIA driver metapackage from nvidia-driver-390 (Recommended Driver)' in the Driver Manager. However my resolution is like 800x600 pixels or something. How do I fix my resolution now? I think I'm close to a solution. Just that awful resolution.


Never mind.... The broken nvidia-390 errors are back :-( :-( :-(  Apparently it broke again after I asked the Driver Manager to get the recommended nvidia-390 package.

Any ideas?

---

### Post by mc4man on 2018-03-29
Does this show anything of interest?
```
dpkg-divert --list
```

---

### Post by jorritTyb on 2018-03-29
> **mc4man said:**
> Does this show anything of interest?
```
dpkg-divert --list
```

That says:

```

[FONT=monospace][COLOR=#000000]diversion of /usr/lib/x86_64-linux-gnu/libEGL.so to /usr/lib/x86_64-linux-gnu/libEGL.so.[/COLOR]
distrib by nvidia-340
diversion of /usr/share/dict/words to /usr/share/dict/words.pre-dictionaries-common by d
ictionaries-common
diversion of /usr/bin/pod2latex to /usr/bin/pod2latex.bundled by libpod-latex-perl
diversion of /usr/lib/i386-linux-gnu/libGLESv2.so.2 to /usr/lib/i386-linux-gnu/libGLESv2
.so.2.distrib by nvidia-340
diversion of /usr/lib/x86_64-linux-gnu/libGLESv2.so.2 to /usr/lib/x86_64-linux-gnu/libGL
ESv2.so.2.distrib by nvidia-340
diversion of /usr/share/man/man1/pod2latex.1.gz to /usr/share/man/man1/pod2latex.bundled
.1.gz by libpod-latex-perl
diversion of /usr/share/vim/vim80/doc/help.txt to /usr/share/vim/vim80/doc/help.txt.vim-
tiny by vim-runtime
diversion of /usr/lib/x86_64-linux-gnu/libEGL.so.1 to /usr/lib/x86_64-linux-gnu/libEGL.s
o.1.distrib by nvidia-340
diversion of /usr/share/man/man1/sh.1.gz to /usr/share/man/man1/sh.distrib.1.gz by dash
diversion of /usr/share/man/man1/config_data.1.gz to /usr/share/man/man1/config_data.div
erted.1.gz by libmodule-build-perl
diversion of /usr/lib/i386-linux-gnu/libGLESv2.so to /usr/lib/i386-linux-gnu/libGLESv2.s
o.distrib by nvidia-340
diversion of /usr/lib/i386-linux-gnu/libEGL.so to /usr/lib/i386-linux-gnu/libEGL.so.dist
rib by nvidia-340
diversion of /usr/lib/i386-linux-gnu/libGL.so to /usr/lib/i386-linux-gnu/libGL.so.distri
b by nvidia-340
diversion of /usr/lib/libreoffice/share/basic/script.xlc to /usr/lib/libreoffice/share/b
asic/script.xlc.noaccess by libreoffice-base
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.
1.distrib by nvidia-340
diversion of /usr/lib/x86_64-linux-gnu/libGL.so to /usr/lib/x86_64-linux-gnu/libGL.so.di
strib by nvidia-340
diversion of /usr/lib/libreoffice/share/basic/dialog.xlc to /usr/lib/libreoffice/share/b
asic/dialog.xlc.noaccess by libreoffice-base
diversion of /usr/lib/i386-linux-gnu/libEGL.so.1 to /usr/lib/i386-linux-gnu/libEGL.so.1.
distrib by nvidia-340
diversion of /usr/bin/config_data to /usr/bin/config_data.diverted by libmodule-build-pe
rl
diversion of /bin/sh to /bin/sh.distrib by dash
diversion of /usr/share/initramfs-tools/hooks/klibc to /usr/share/initramfs-tools/hooks/
klibc^i-t by klibc-utils
diversion of /usr/lib/x86_64-linux-gnu/libGLESv2.so to /usr/lib/x86_64-linux-gnu/libGLES
v2.so.distrib by nvidia-340
diversion of /usr/share/vim/vim80/doc/tags to /usr/share/vim/vim80/doc/tags.vim-tiny by 
vim-runtime
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.di
strib by nvidia-340


```


[/FONT]

---

### Post by mc4man on 2018-03-29
Well you have about 12 diversions for nvidia-340 that shouldn't be there. Honestly I've no real idea about the proper way for a user to remove them.
dpkg-divert does have a --remove command but not sure exactly how to use..
Maybe try installing nvidia-340, if it installs then go ahead & completely remove it, maybe that'll remove the diversions for you.

---

### Post by jorritTyb on 2018-03-30
Given that this seems hard to solve. What's the easiest way for me to go back to a stable version of ubuntu?

---

### Post by dino99 on 2018-03-30
You are one of the many who hit the nvidia+cuda+"64/32" mess. Thats not something new, and well exposed on the nvidia/cuda forum.
Purging the related ppa is the first step (ppa-purge run on activated ppa), then nvidia is the second step (if still needed), and cuda indeed.
After that done, clean the system via gtkorphan and bleachbit (as root, but carefully select the options), and reboot.
Glance again at 'dpkg-divert --list' and 'journalctl -b' to grab the situation.
That should set a stable system; if not, then bionic is on the way to be released soon, and do a fresh clean new installation with a new user to get rid of the old possible borked home's settings .
):P

---

### Post by jorritTyb on 2018-03-30
> **dino99 said:**
> You are one of the many who hit the nvidia+cuda+"64/32" mess. Thats not something new, and well exposed on the nvidia/cuda forum.
Purging the related ppa is the first step (ppa-purge run on activated ppa), then nvidia is the second step (if still needed), and cuda indeed.
After that done, clean the system via gtkorphan and bleachbit (as root, but carefully select the options), and reboot.
Glance again at 'dpkg-divert --list' and 'journalctl -b' to grab the situation.
That should set a stable system; if not, then bionic is on the way to be released soon, and do a fresh clean new installation with a new user to get rid of the old possible borked home's settings .
):P

Um... That's skipping a lot of things I don't know how to do. I think I can ppa-purge. That's no problem but then you say 'nvidia is the second step and cuda'? What does that mean? Is there some kind of guide to setting this up? I though just selecting 'recommend driver' in the Driver Manager should work but that breaks my system every time. I'm pretty much a noob with this I'm afraid.

---

### Post by dino99 on 2018-03-30
'nvidia is the second step and cuda'?

i was speaking about  'purging' of course

---

### Post by jorritTyb on 2018-03-30
Ok. Well my system 'works' now in the sense that the Xorg driver is back into business. But I *really* would like to use the nvida-390 driver. In the Driver Manager this driver is seen as recommended but I try to select it it simply switches back to the XOrg one. Any way to use the 390 driver? 

Thanks

---

### Post by jorritTyb on 2018-04-02
Seems that things have gotten better and I managed to partially solve my problem. The nvidia-390 driver is now installed and is apparently being used. However performance is very bad compared to earlier. While I used to have consistently about 60 fps in (for example) Minecraft it is now about 10-11 fps. Am I still not using the correct drivers? I did remove that ppa where I used to get my drivers from but I'm not sure I can safely use that. Hints are welcome. Thanks

Edit: the nvidia packages are *still* giving issues... I can't imagine that I'm the only ubuntu user with nvidia cards? How do other people solve this?

---

### Post by jorritTyb on 2018-04-03
Sorry for bumping this but I'm getting a bit desperate here. I'm happy with two solutions. Either getting the proprietary nvidia drivers working on bionic or else a way to revert my system back to the previous stable version of ubuntu. As it is now my system is basically unusable for what I need to do.

Thanks!

---

### Post by mc4man on 2018-04-03
By now you could have done a 100 fresh installs, why not just do that & be done with the problems?

---

### Post by #&amp;thj^% on 2018-04-03
:D I can't help but to agree with mc4man.
Sorry just trying to be helpful.

---

### Post by jorritTyb on 2018-04-03
Well a fresh install wipes everything I guess. That's of course possible but it is a lot of work. Also I guess I was hoping for a solution with bionic too. But ok. I think I'll have to do that then. Thanks for the reply

---

### Post by zika on 2018-04-04
Never have wanted to move to another house just because I had to fix something being that even hard thing to do... ;)
But, re-install could be done (and it has been done) with keeping almost everything as it was, just in a new environment...
Good readings:

[https://askubuntu.com/questions/269880/re-install-ubuntu-without-losing-data-in-home-folder/269892](https://askubuntu.com/questions/269880/re-install-ubuntu-without-losing-data-in-home-folder/269892)
[https://ubuntuforums.org/showthread.php?t=2057342](https://ubuntuforums.org/showthread.php?t=2057342)
and so on...

---

### Post by jorritTyb on 2018-04-04
I have one remaining question though. Where can I follow progress on support for nvidia on bionic? What's the best place/resource for this kind of information?

---

### Post by zika on 2018-04-04
```
apt changelog nvidia-[COLOR=#00ff00]*put_number_You_want_to follow*[/COLOR]
```

---

### Post by stutteringp0et2 on 2018-05-01
As root:

for FILE in $(dpkg-divert --list | grep nvidia-340 | awk '{print $3}'); do dpkg-divert --remove $FILE; done

When it's done, you can:

apt --fix-broken install
apt update
apt upgrade

---

### Post by cariboo on 2018-05-01
Thread closed, as it looks like the op solved it, and Bionic has been released.

---

