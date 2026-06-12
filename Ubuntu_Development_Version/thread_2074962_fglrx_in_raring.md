---
title: "fglrx in raring"
date: 2012-10-22
forum: Ubuntu Development Version
---

### Post by jfernyhough on 2012-10-22
Another release, another fglrx tracking thread.

AMD have just released their beta 12.11 drivers. While Quantal (and as such Raring) has working drivers in the repos (for HD5k+ cards) the AMD release is a little newer (fglrx 9.01 compared to 9.000).

The 12.11 beta adds official xserver 1.13 support, which is nice.

Download is here: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)
You need to extract it. ;)

Steps to build are fairly simple at the moment, though I'm assuming you're upgrading the driver and not installing fresh:

$ wget [http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-12.11-x86.x86_64.zip]("http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-12.10-x86.x86_64.zip")
$ unzip amd-driver-installer-catalyst-12.11-x86.x86_64.zip
$ sh ./amd-driver-installer-catalyst-12.11-x86.x86_64.run --buildpkg Ubuntu/raring
$ sudo dpkg -i *.deb
$ sudo nano /etc/ati/signature
```
9777c589791007f4aeef06c922ad54a2:ae59f5b9572136d99fdd36f0109d358fa643f2bd4a2644d9efbb4fe91a9f6590a145:f612f0b01f2565cd9bd834f8119b309bae11a1ed4a2661c49fdf3fad11986cc4f641f1ba1f2265909a8e34ff1699309bf211a7eb4d7662cd9f8e3faf14986d92f646f1bc
```

You'll need to add the above signature (taken from the repo fglrx 9.00) to remove the "Testing" watermark.

Reboot and all should be good!

---

### Post by jfernyhough on 2012-10-24
The 12.11 beta appears to add 1.13 support. Download: [http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-12.11-beta-x86.x86_64.zip](http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-12.11-beta-x86.x86_64.zip)

Status:
[s]Downloading[/s]
[s]Unpacking[/s]
[s]Building packages[/s]
[s]Installing .debs[/s]
No errors from DKMS
[s]Rebooting[/s]
Boots with Testing watermark
[s]Retrieving signature from repo fglrx 9.00[/s]
Added signature to /etc/ati/signature
Logged out, watermark is gone. :)

All seems good. Now to test other applications. ;)

---

### Post by jfernyhough on 2012-11-09
The 3.7 kernel has hit the repos so it's time to get some patches running.

I've had success manually applying the 3.7 patch [1] with a make.sh patch from Alberto [2]. This make.sh patch works around the version.h move.

After picking through the patch applying bit by bit (as the file is different to that the patch was created for) I generated a patch specific to 9.01 (attached). In case the patch won't apply (or whatever) I've attached a pre-patched version. Also attached is a signature from fglrx 9.00 that can be used to remove the testing watermark.

The process is the same as for previous releases, i.e.:

1) Download
2) Extract
3) Patch
4) Build
5) Install

I would add more details to the op but it seems editing is still disabled. Grr.

For this process I assume you have a working directory called "temp" in your home. Change this to suit. I use /dev/shm as a handy ramdisk. I also assume you download and extract the patches to that directory.

**Details:**

0) If this is the first time you've done this, install the necessary  development packages  (normally installed by the installer, if any are  missing they should be identified in the output of step 5):
$ sudo apt-get install dpkg-dev debhelper  dh-modaliases execstack

1) Once downloaded (the .run is in a .zip file. I shouldn't have to tell  you how to deal with that), extract the installer files so we can patch  manually:
$ sh ./amd-driver-installer-12-11-x86.x86_64.run --extract ~/temp/amd
$ cd ~/temp

2) Download and apply the attached patches (adapted from that in Vi0l0's(?) repo [1]):
$ cp 901.patch ~/temp/amd/common/lib/modules/fglrx/build_mod/
$ cp 37-make.patch ~/temp/amd/common/lib/modules/fglrx/build_mod/
$ cd ~/temp/amd/common/lib/modules/fglrx/build_mod/
$ patch -p0 < ./901.patch
$ patch -p0 < ./37-make.patch
$ cd ~/temp

4) Download and add a release signature (taken from Catalyst 12.10) to remove the testing watermark:
$ cp signature ~/temp/amd/common/etc/ati/

5) Build the packages (this will place the packages in the parent directory):
$ cd ~/temp/amd
$ ./ati-installer.sh 9.01 --buildpkg Ubuntu/raring

6) Change to the parent directory and install the debs:
$ cd ..
$ sudo dpkg -i *.deb

7) If you haven't done so already, create an Xorg.conf that will load fglrx:
$ sudo amdconfig --init

Hopefully DKMS will then build the kernel module successfully, you can reboot, and you're running kernel 3.7 with working fglrx!


[1] [http://catalyst.apocalypsus.net/files/arch-fglrx-3.7.patch](http://catalyst.apocalypsus.net/files/arch-fglrx-3.7.patch)
[2] [https://bazaar.launchpad.net/~ubuntu-branches/ubuntu/raring/fglrx-installer-updates/raring-proposed/revision/23](https://bazaar.launchpad.net/~ubuntu-branches/ubuntu/raring/fglrx-installer-updates/raring-proposed/revision/23)

---

### Post by jfernyhough on 2012-11-11
Quick bump for the make.sh patch. :)

---

### Post by MWisBest on 2012-11-15
I can't thank you enough for this! Kernel 3.7 was very nice but I wasn't able to get fglrx working with it until I read this. An issue I had been having with my laptop was that I was unable to resume from sleep mode, and now with fglrx it works!

The only issue I have run in to that I don't recall having with the 3.5 kernel is that when I start up the system the brightness on the display is really low at first. As soon as I log in to KDE though (I'm using Kubuntu) it goes back to normal, so not a huge deal.

---

### Post by Krisando on 2012-11-16
I followed every step closely but I get a watermark and it didn't workout with 3.7, not sure what went wrong.

---

### Post by jfernyhough on 2012-11-18
New beta release:
[http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-12.11-beta8-x86.x86_64.zip](http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-12.11-beta8-x86.x86_64.zip)

9.01.8

[s]Downloading[/s]
Trying a plain --buildpkg
Packages build, trying to install the debs.
DKMS errors with kernel 3.7.
Need to patch as for initial beta release.

Patched. Built. Installed. No complaints from DKMS. Next up: reboot!

Reboot done, though I had to boot in recovery mode and resume to get GDM to load. Might just be a first reboot thing? Everything else seems to be working OK.

Another reboot, comes up fine.

---

### Post by MWisBest on 2012-11-18
> **jfernyhough said:**
> New beta release:
[http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-12.11-beta8-x86.x86_64.zip](http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-12.11-beta8-x86.x86_64.zip)

9.01.8

[s]Downloading[/s]
Trying a plain --buildpkg
Packages build, trying to install the debs.
DKMS errors with kernel 3.7.
Need to patch as for initial beta release.

Patched. Built. Installed. No complaints from DKMS. Next up: reboot!

Reboot done, though I had to boot in recovery mode and resume to get GDM to load. Might just be a first reboot thing? Everything else seems to be working OK.

Another reboot, comes up fine.
Do you have a changelog between this and the first beta? I'm just wondering if it's worth my time to update or not.

---

### Post by jfernyhough on 2012-11-18
"AMD Catalyst 12.11 Beta 8 for Linux includes significant performance improvements for Left for Dead 2"

;)

[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst1211betadriver.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst1211betadriver.aspx)

---

### Post by jfernyhough on 2012-12-03
Beta 11 released:
[http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-12.11-beta11-x86.x86_64.zip](http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-12.11-beta11-x86.x86_64.zip)

Information:
[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst1211betadriver.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst1211betadriver.aspx)

Selected points:
Resolve missing fonts issue in XBMC [Windows only?]
Resolves stability issues found in the previous AMD Catalyst 12.11 Beta8 driver for Linux
 For users experiencing issues with HDMI Audio under Ubuntu 12.04,  users should try installing the &#8220;dkms-hda - 0.201211291615~precise1&#8221;  package from  [https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages]("https://code.launchpad.net/%7Eubuntu-audio-dev/+archive/alsa-daily/+packages") and reboot; this will resolve the HDMI Audio issue found in Ubuntu 12.04

My status:
[s]Download[/s]
[s]Trying a --buildpkg (no patches)[/s] -> DKMS failed.
Trying with existing patches -> DKMS "OK" -> depmod "OK"
Installation "OK"
[s]Reboot![/s]

Looks to be working fine. Steam doesn't segfault now, which is good. Driver version number is 9.01.8.

---

### Post by meborc on 2012-12-06
So what is the proper approach to get HD4xxx working? There used to be some legacy drivers, but does anyone know what is the status on this?

---

### Post by Bowmore on 2012-12-06
> **meborc said:**
> So what is the proper approach to get HD4xxx working? There used to be some legacy drivers, but does anyone know what is the status on this?
Still not upgraded to X-server 1.13 but there's a working legacy driver for Radeon HD 2xxx-4xxx series cards.

PPA: AMD Catalyst Legacy :
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)
The PPA downgrades X-server and includes a patch for the 3.5 kernel.

How To Install AMD Catalyst Legacy Drivers in Ubuntu 12.10
[http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html](http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html)

---

### Post by Stinger on 2012-12-08
@Bowmore
Thanks a lot for the provided links :grin:
Works perfectly with my Radeon HD 4670
( well the AMD/ATI driver never was and never will be perfect :biggrin:, but it works mostly)
Even got my splash screen back, it is missing when you use the open source driver.

I tried with these two:

[flight-of-the-navigator]("http://videos.mozilla.org/serv/mozhacks/flight-of-the-navigator/")
and
[Lights from Ellie Goulding]("http://lights.elliegoulding.com/")

---

### Post by 4ss4ssini on 2012-12-09
Thanks. Works perfectly with my HD 5870.

---

### Post by jfernyhough on 2012-12-12
There's a new fglrx package in X-Swat ([https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)) : **fglrx-installer-experimental-9**. Current version is 2:9.010.12-0ubuntu0~xup1 and it's built for raring so it should work with kernel 3.7.

$ sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
$ sudo apt-get update
$ sudo apt-get install fglrx-installer-experimental-9

Giving it a go myself now. :)

Currently 64-bit package is not built. Give it a minute.

---

### Post by Nemesis2012 on 2012-12-13
> **jfernyhough said:**
> There's a new fglrx package in X-Swat ([https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)) : **fglrx-installer-experimental-9**. Current version is 2:9.010.12-0ubuntu0~xup1 and it's built for raring so it should work with kernel 3.7.

$ sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
$ sudo apt-get update
$ sudo apt-get install fglrx-installer-experimental-9

Giving it a go myself now. :)

Currently 64-bit package is not built. Give it a minute.

no 64bit [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG] just upgraded to 13.04 64bit last night been trying to install the beta catalyst no luck so far going to try to patch it and see if it works

i found the  [&#8220;xorg crack pushers&#8221; team]("https://launchpad.net/%7Exorg-edgers")  xorg-edgers fresh X crack    [URL="https://launchpad.net/~xorg-edgers/+archive/ppa"]https://launchpad.net/~xorg-edgers/+archive/ppa
[/URL]

---

### Post by jfernyhough on 2012-12-13
I always forget about Edgers... not sure why. :D

Their fglrx is "based on new upstream release: 12.12" (2:9.010.12-0ubuntu1~xedgers~raring1) so it's newer than the beta on the AMD site. Interesting.

I've added that PPA so let's see what happens...

--edit
Grr... "Unsupported hardware" watermark...

Ah ha! A new embedded driver for 12.12: [http://support.amd.com/us/gpudownload/embedded/Pages/embedded_linux.aspx](http://support.amd.com/us/gpudownload/embedded/Pages/embedded_linux.aspx)
[http://www2.ati.com/drivers/embedded/9.01-121106a-150335C-EDG_Direct.zip](http://www2.ati.com/drivers/embedded/9.01-121106a-150335C-EDG_Direct.zip)

This would explain the watermark. Now to find which file to replace... I think it's /etc/ati/control

Yup, copying the control from 12.11b11 sorts out the watermark (attached).

---

### Post by Nemesis2012 on 2012-12-13
> **jfernyhough said:**
> I always forget about Edgers... not sure why. :D

Their fglrx is "based on new upstream release: 12.12" (2:9.010.12-0ubuntu1~xedgers~raring1) so it's newer than the beta on the AMD site. Interesting.

I've added that PPA so let's see what happens...

--edit
Grr... "Unsupported hardware" watermark...

Ah ha! A new embedded driver for 12.12: [http://support.amd.com/us/gpudownload/embedded/Pages/embedded_linux.aspx](http://support.amd.com/us/gpudownload/embedded/Pages/embedded_linux.aspx)
[http://www2.ati.com/drivers/embedded/9.01-121106a-150335C-EDG_Direct.zip](http://www2.ati.com/drivers/embedded/9.01-121106a-150335C-EDG_Direct.zip)

This would explain the watermark. Now to find which file to replace... I think it's /etc/ati/control

Yup, copying the control from 12.11b11 sorts out the watermark (attached).

i installed the beta catalyst for my 6950 form amd.com using Vi0l0's patch i seen the drivers form the repo's was embedded as well Vi0l0's patch let me install the beta catalyst on kernel 3.7 looks like its is working just fine so far on ubuntu 13.04 [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by Gompa on 2012-12-20
i installed the drivers from ppa: xorg-edgers/ppa

but i have a serious memory leak in xorg with these drivers 
(dont know if its driver related or xorg related but its a memory leak alright)

specs : 

acer 522 amd c-60
xubuntu 13.04
AMD Radeon HD 6290 Graphics
catalyst version 12.9
driver packaging version 9.01-121106a-150335C-EDG_Direct

kernel :  ```
uname -a
Linux Aspire-One-522 3.7.0-7-generic #15-Ubuntu SMP Sat Dec 15 14:13:08 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Xgen on 2012-12-22
Anybody got 12.12 working with the 3.8 kernel?

---

### Post by Nemesis2012 on 2012-12-31
> **Xgen said:**
> Anybody got 12.12 working with the 3.8 kernel?

12.12 is a embedded Driver

Vi0l0 has a patch for catalyst 12.11 on kernal 3.8 [https://bbs.archlinux.org/viewtopic.php?pid=1209006#p1209006](https://bbs.archlinux.org/viewtopic.php?pid=1209006#p1209006)

---

### Post by SPK201 on 2013-01-01
Since the fglrx driver doesn't work for me on Ubuntu 12.10 with Unity (only right-click menu and terminal can be opened), I'm going to upgrade to 13.04 and see if it solves the issue.

---

### Post by Nemesis2012 on 2013-01-04
> **SPK201 said:**
> Since the fglrx driver doesn't work for me on Ubuntu 12.10 with Unity (only right-click menu and terminal can be opened), I'm going to upgrade to 13.04 and see if it solves the issue.
what GPU you have?

---

### Post by jfernyhough on 2013-01-04
Nice. The 3.8 patch has been applied to the edgers package:

```
fglrx-installer (2:9.010.12-0ubuntu1~xedgers~raring2) raring; urgency=low

    * New upstream release (12.12)
    * debian/dkms.conf.in,fix-build-kernel-3.8.patch:
     - Add support for Linux 3.8.
  -- Rico Tzschichholz <email address hidden>   Wed, 12 Dec 2012 17:01:48 +0100
```

--edit
Looks to be working well with 3.8-rc2 from the mainline builds. It still has the "Unsupported hardware" watermark though, so you'll need to copy across /etc/ati/control as previously.

---

### Post by bullemina on 2013-01-05
Hello :)..

I'm trying to install the latest beta referenced in posts 17 using the instructions in post 3, but I keep getting errors when I install .deb packages.
I'm running 13.04, 3.7.0-7-generic # 15-Ubuntu.

Trying to patch manually, also use the pre-patched file located in post 17&#8203;&#8203;, nothing I do works. Do you have any idea?


DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
Setting up fglrx-amdcccle (2:9.010-0ubuntu1) ...
Setting up fglrx-dev (2:9.010-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.7.0-7-generic
modprobe: ../tools/modprobe.c:550: print_action: Assertion `kmod_module_get_initstate(m) == KMOD_MODULE_BUILTIN' failed.
Aborted (core dumped)
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by jfernyhough on 2013-01-05
That error message seemed to start a couple of driver releases ago and IFAICT occurs when building against a kernel not officially supported by AMD. The driver still works, though.

I'd recommend trying the *edgers* package. It works fine on my laptop (except for the watermark which is easy to fix).

---

### Post by bullemina on 2013-01-05
I thank you for the positive response :)
Then I try with Edgers package.

---

### Post by deri on 2013-01-07
fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.7.0-4-generic/updates/dkms/

depmod......

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up fglrx-amdcccle (2:9.010-0ubuntu1) ...
Setting up fglrx-dev (2:9.010-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.7.0-4-generic
modprobe: ../tools/modprobe.c:550: print_action: Assertion `kmod_module_get_initstate(m) == KMOD_MODULE_BUILTIN' failed.
Aborted (core dumped)
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by jverga on 2013-01-07
Been running Catalyst  12.12 on the 3.8  Mainline dailies for a few weeks now( I updated Vi0l0's and jfernyhough patches and made my own *.debs. Never fails to  build fglrx module when updating teh kernel. Everything is signed and I use Catalyst 12.10 control- so zero  watermarks.

 If ok w/mod I'll post links  for  my fglrx_9.010-0ubuntu1_amd64.deb,fglrx-amdcccle_9.010-0ubuntu1_amd64.deb and fglrx-dev_9.010-0ubuntu1_amd64.deb. I always end up w/ massive troubles from xorg-edgers ppa (they  do warn truthfully!).

My debs only work w/ kernel 3.8

---

### Post by jfernyhough on 2013-01-07
Post away - but you can always download just the fglrx packages from the PPA. :)

e.g.: [https://launchpad.net/~xorg-edgers/+archive/ppa/+sourcepub/2910109/+listing-archive-extra](https://launchpad.net/~xorg-edgers/+archive/ppa/+sourcepub/2910109/+listing-archive-extra)

Links:
      
[LIST]
[*]       [fglrx-amdcccle_9.010.12-0ubuntu1~xedgers~raring2_amd64.deb]("https://launchpad.net/%7Exorg-edgers/+archive/ppa/+files/fglrx-amdcccle_9.010.12-0ubuntu1%7Exedgers%7Eraring2_amd64.deb")          (5.6 MiB)
[*]       [fglrx-amdcccle_9.010.12-0ubuntu1~xedgers~raring2_i386.deb]("https://launchpad.net/%7Exorg-edgers/+archive/ppa/+files/fglrx-amdcccle_9.010.12-0ubuntu1%7Exedgers%7Eraring2_i386.deb")          (5.6 MiB)
[*]       [fglrx-dev_9.010.12-0ubuntu1~xedgers~raring2_amd64.deb]("https://launchpad.net/%7Exorg-edgers/+archive/ppa/+files/fglrx-dev_9.010.12-0ubuntu1%7Exedgers%7Eraring2_amd64.deb")          (69.3 KiB)
[*]       [fglrx-dev_9.010.12-0ubuntu1~xedgers~raring2_i386.deb]("https://launchpad.net/%7Exorg-edgers/+archive/ppa/+files/fglrx-dev_9.010.12-0ubuntu1%7Exedgers%7Eraring2_i386.deb")          (67.8 KiB)
[*]       [fglrx_9.010.12-0ubuntu1~xedgers~raring2_amd64.deb]("https://launchpad.net/%7Exorg-edgers/+archive/ppa/+files/fglrx_9.010.12-0ubuntu1%7Exedgers%7Eraring2_amd64.deb")          (76.9 MiB)
[*]       [fglrx_9.010.12-0ubuntu1~xedgers~raring2_i386.deb]("https://launchpad.net/%7Exorg-edgers/+archive/ppa/+files/fglrx_9.010.12-0ubuntu1%7Exedgers%7Eraring2_i386.deb")          (45.6 MiB)
[/LIST]

---

### Post by jfernyhough on 2013-01-08
New package for 12.11 coming shortly:

```

fglrx-installer (2:9.010-0ubuntu1) raring; urgency=low

  * New upstream release.
  * debian/[dkms.conf.in]("http://dkms.conf.in"),
    replace-archdata.acpi_handle-with-acpi_node.handle.patch:
    - Add support for Linux 3.8 (LP: #1095755).
      Thanks to Robert Hooker for the patch.
  * debian/substvars:
    - Remove versioned dependency on xserver-xorg-core.
  * debian/[10fglrx.in]("http://10fglrx.in"), debian/rules:
    - Fix paths which prevented OpenGL operations on hybrid systems
      on amd64 (LP: #1068661). Thanks to Nick Andrik for the patch.

Date: Tue, 08 Jan 2013 16:12:09 +0100
```

---

### Post by Nemesis2012 on 2013-01-09
> **jfernyhough said:**
> New package for 12.11 coming shortly:

```

fglrx-installer (2:9.010-0ubuntu1) raring; urgency=low

  * New upstream release.
  * debian/[dkms.conf.in]("http://dkms.conf.in"),
    replace-archdata.acpi_handle-with-acpi_node.handle.patch:
    - Add support for Linux 3.8 (LP: #1095755).
      Thanks to Robert Hooker for the patch.
  * debian/substvars:
    - Remove versioned dependency on xserver-xorg-core.
  * debian/[10fglrx.in]("http://10fglrx.in"), debian/rules:
    - Fix paths which prevented OpenGL operations on hybrid systems
      on amd64 (LP: #1068661). Thanks to Nick Andrik for the patch.

Date: Tue, 08 Jan 2013 16:12:09 +0100
```

it gave me the unsupported hardware watermark on a HD 6950

---

### Post by MadNachos on 2013-01-11
> **Nemesis2012 said:**
> it gave me the unsupported hardware watermark on a HD 6950

I get that as well with my HD 6870..seems pretty good otherwise.

edit: I found that the old fix to remove it still works fine, but make a backup copy of fglrx_drv.so to be safe.

```
#!/bin/sh
DRIVER=/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done
```

---

### Post by Nemesis2012 on 2013-01-11
> **MadNachos said:**
> I get that as well with my HD 6870..seems pretty good otherwise.

edit: I found that the old fix to remove it still works fine, but make a backup copy of fglrx_drv.so to be safe.

```
#!/bin/sh
DRIVER=/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done
```

its not letting me see my temp as well

---

### Post by bullemina on 2013-01-11
> **Nemesis2012 said:**
> its not letting me see my temp as well

I can se my temp. 7770

---

### Post by jfernyhough on 2013-01-11
> **MadNachos said:**
> I get that as well with my HD 6870..seems pretty good otherwise.

edit: I found that the old fix to remove it still works fine, but make a backup copy of fglrx_drv.so to be safe.

```
#!/bin/sh
DRIVER=/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done
```Or you could just replace /etc/ati/control with a release version?

---

### Post by MadNachos on 2013-01-11
> **jfernyhough said:**
> Or you could just replace /etc/ati/control with a release version?

Are you asking? 'Cus I don't know.

---

### Post by jfernyhough on 2013-01-11
Apologies. Instead of manually binary patching the driver you can just replace the control file which tells the driver which card IDs are supported. Given that the latest driver is based on a driver for embedded devices most normal desktop parts aren't supported by that driver. Replacing the control file with one from a desktop release simply replaces the compatible ID list.

In theory there may be incompatibilities between the beta driver releases and unsupported devices, which is why you get the watermark, but in practice the drivers have been pretty much the same.

---

### Post by bettlebrox on 2013-01-13
Will these drivers work with older ATI graphics card such as the Mobility Radeon HD 3400 Series?

Thanks!

---

### Post by jfernyhough on 2013-01-13
> **bettlebrox said:**
> Will these drivers work with older ATI graphics card such as the Mobility Radeon HD 3400 Series?No. There are not any fglrx drivers for cards older than the 5000-series which work with xserver 1.13.

If you want fglrx you'll have to stick with Precise; if you want to run Raring you can use the open-source drivers (which should by now perform about as well as well as the proprietary ones for most stuff).

---

### Post by erickwill on 2013-01-14
Any workaround to have any new driver or a radeon legacy driver running on kernel 3.7 or kernel 3.8 for radeon 4650?

---

### Post by MadNachos on 2013-01-14
> **jfernyhough said:**
> Apologies. Instead of manually binary patching the driver you can just replace the control file which tells the driver which card IDs are supported. Given that the latest driver is based on a driver for embedded devices most normal desktop parts aren't supported by that driver. Replacing the control file with one from a desktop release simply replaces the compatible ID list.

In theory there may be incompatibilities between the beta driver releases and unsupported devices, which is why you get the watermark, but in practice the drivers have been pretty much the same.

Gotcha, thanks for the info.

---

### Post by jfernyhough on 2013-01-14
> **erickwill said:**
> Any workaround to have any new driver or a radeon legacy driver running on kernel 3.7 or kernel 3.8 for radeon 4650?There is a patch on the Arch AUR that might give you kernel 3.7 support with xserver 1.12:

[https://aur.archlinux.org/packages/catalyst-total-hd234k/](https://aur.archlinux.org/packages/catalyst-total-hd234k/)

You'll have to download the tarball ([https://aur.archlinux.org/packages/ca/catalyst-total-hd234k/catalyst-total-hd234k.tar.gz](https://aur.archlinux.org/packages/ca/catalyst-total-hd234k/catalyst-total-hd234k.tar.gz)), extract the patch, and patch manually as previously (e.g. [http://ubuntuforums.org/showthread.php?t=1988444](http://ubuntuforums.org/showthread.php?t=1988444))

---

### Post by jfernyhough on 2013-01-14
Looks like there is a new driver (13.1) landing on Wednesday. This is probably based on the 12.12 embedded driver we already have in raring so I don't imagine there will be any major changes.

[quote="AndrewD"]Just a heads up - we will be posting logo certified Catalyst 13.1 on  Wednesday.   You can also expect new beta drivers in the next few weeks[/quote]

---

### Post by erickwill on 2013-01-14
> **jfernyhough said:**
> There is a patch on the Arch AUR that might give you kernel 3.7 support with xserver 1.12:

[https://aur.archlinux.org/packages/catalyst-total-hd234k/](https://aur.archlinux.org/packages/catalyst-total-hd234k/)

You'll have to download the tarball ([https://aur.archlinux.org/packages/ca/catalyst-total-hd234k/catalyst-total-hd234k.tar.gz](https://aur.archlinux.org/packages/ca/catalyst-total-hd234k/catalyst-total-hd234k.tar.gz)), extract the patch, and patch manually as previously (e.g. [http://ubuntuforums.org/showthread.php?t=1988444](http://ubuntuforums.org/showthread.php?t=1988444))

Thank you very much! ;)
Let me give this a shot and bring here the results :)

---

### Post by erickwill on 2013-01-14
> **jfernyhough said:**
> There is a patch on the Arch AUR that might give you kernel 3.7 support with xserver 1.12:

[https://aur.archlinux.org/packages/catalyst-total-hd234k/](https://aur.archlinux.org/packages/catalyst-total-hd234k/)

You'll have to download the tarball ([https://aur.archlinux.org/packages/ca/catalyst-total-hd234k/catalyst-total-hd234k.tar.gz](https://aur.archlinux.org/packages/ca/catalyst-total-hd234k/catalyst-total-hd234k.tar.gz)), extract the patch, and patch manually as previously (e.g. [http://ubuntuforums.org/showthread.php?t=1988444](http://ubuntuforums.org/showthread.php?t=1988444))

Hey JF,

Well, I tried all steps you mentioned but I am stuck at the recompilation process. Additionally I couldn't install dh-modaliases. I forgot to mention that I am on Debian Wheezy, using stock kernel 3.2 but wishing to switch to some recent kernel.

Here is what I got while recompiling:
```
erick@quarktech01:~/temp/amd$ ./ati-installer.sh 8.980 --buildpkg Debian/testing=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Debian/testing
cp: cannot stat `/home/erick/temp/amd/x710_64a/*': No such file or directory
Package build failed!
Package build utility output:
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 8.97.100.3-1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.67itKm
dpkg-buildpackage: host architecture amd64
 debian/rules build
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
	  mkdir -p usr/share/doc/fglrx; \
	  mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
	fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
	     usr/X11R6/lib \
	     usr/X11R6/lib64 \
	     usr/share usr/src     -type f | xargs chmod -x
find: `usr/X11R6/include': No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# set proper permissions on /etc files
if [ -d etc/ati ]; then			\
		chmod 755 etc/ati ;			\
		chmod 644 etc/ati/* ;		\
		chmod a+x etc/ati/*.sh ;	\
	fi
if [ -f debian/fglrx.default ]; then \
	  mv -v debian/fglrx.default debian/fglrx; \
	fi
`debian/fglrx.default' -> `debian/fglrx'
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
 fakeroot debian/rules binary
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
	  mkdir -p usr/share/doc/fglrx; \
	  mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
	fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
	     usr/X11R6/lib \
	     usr/X11R6/lib64 \
	     usr/share usr/src     -type f | xargs chmod -x
find: `usr/X11R6/include': No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# set proper permissions on /etc files
if [ -d etc/ati ]; then			\
		chmod 755 etc/ati ;			\
		chmod 644 etc/ati/* ;		\
		chmod a+x etc/ati/*.sh ;	\
	fi
if [ -f debian/fglrx.default ]; then \
	  mv -v debian/fglrx.default debian/fglrx; \
	fi
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
dh_testroot
dh_clean -k
dh_clean: dh_clean -k is deprecated; use dh_prep instead
dh_clean: Compatibility levels before 5 are deprecated (level 4 in use)
dh_installdirs
dh_installdirs: Compatibility levels before 5 are deprecated (level 4 in use)
# Create the directories to install into
dh_installdirs -pfglrx-driver \
		usr \
		usr/lib/xorg \
		usr/lib/xorg/modules \
		usr/lib/dri \
		usr/bin \
		usr/sbin \
		etc/acpi \
		etc/acpi/events \
		etc/default \
		etc/X11/Xsession.d
dh_installdirs: Compatibility levels before 5 are deprecated (level 4 in use)
# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pfglrx-driver \
		emul/ia32-linux/usr/lib \
		emul/ia32-linux/usr/lib/xorg \
		emul/ia32-linux/usr/lib/xorg/modules \
		emul/ia32-linux/usr/lib/dri
dh_installdirs: Compatibility levels before 5 are deprecated (level 4 in use)
dh_installdirs -pfglrx-driver-dev \
		usr \
		usr/include \
		usr/lib
dh_installdirs: Compatibility levels before 5 are deprecated (level 4 in use)
dh_installdirs -pfglrx-kernel-src \
		usr/src/modules/fglrx \
		usr/src/modules/fglrx/debian
dh_installdirs: Compatibility levels before 5 are deprecated (level 4 in use)
dh_installdirs -A -pfglrx-amdcccle \
		usr \
		usr/bin \
		usr/share \
		usr/share/applnk \
		usr/share/applications \
		usr/share/icons \
		usr/share/pixmaps
dh_installdirs: Compatibility levels before 5 are deprecated (level 4 in use)
dh_installdirs -p \
		usr/src
dh_installdirs: Compatibility levels before 5 are deprecated (level 4 in use)
dh_install
dh_install: Compatibility levels before 5 are deprecated (level 4 in use)
ldconfig -n usr/X11R6/lib/
make: ldconfig: Command not found
make: *** [binary] Error 127
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2

```

Appreciate any thoughts and thanks for your kind collaboration since seems AMD just **** us off.

---

### Post by jfernyhough on 2013-01-14
Firstly I've no idea how the Debian build environment differs to that of Ubuntu. In theory it should be compatible, but the fglrx driver debs in the respective repos are certainly of a different composition.

The most obvious thing is that you are trying to build for Debian/testing but the four Debian releases supported by the fglrx installer are named as etch, lenny, sid, and experimental. Hence I would try building for Debian/sid and see if that helps.

---

### Post by erickwill on 2013-01-14
> **jfernyhough said:**
> Firstly I've no idea how the Debian build environment differs to that of Ubuntu. In theory it should be compatible, but the fglrx driver debs in the respective repos are certainly of a different composition.

The most obvious thing is that you are trying to build for Debian/testing but the four Debian releases supported by the fglrx installer are named as etch, lenny, sid, and experimental. Hence I would try building for Debian/sid and see if that helps.

Maybe I can be strongly wrong in my idea, but at my first sight Ubuntu and Debian share a very similar architecture, otherwise I wouldn't be able to use a ubuntu kernel into debian, and I can confirm that is pretty much compatible.
I found in those log lines that there is a Debian/testing mention (that is correspondent to Wheezy).. and for this reason I wondered that should be a light at the end.. 
Again, appreciated all help and collaboration mainly why we are not in a Debian forum.

---

### Post by jfernyhough on 2013-01-15
Right. The log says it's trying to generate a package for Debian/testing. Unfortunately there are no files within the driver package that support "testing" or "wheezy". The four that are named are "etch" "lenny" "sid" and "experimental"; when the driver installer is extracted the supported releases can be seen in packages/Debian/dists

This is why I suggested trying to build with "Debian/sid" instead of "Debian/testing". Not using a different release, just a change in command.

Finally, there is a difference between the fglrx packages in Ubuntu and Debian, that is, you can't install the Debian fglrx-driver and fglrx-control debs in Ubuntu without some dependency problems, and you can't install the Ubuntu fglrx and fglrx-amdcccle debs in Debian. The binary driver itself will be the same, it's the generated deb files that are different. Look at what happens if you add sid sources to Ubuntu, or add random PPAs to Debian.

---

### Post by erickwill on 2013-01-15
> **jfernyhough said:**
> Right. The log says it's trying to generate a package for Debian/testing. Unfortunately there are no files within the driver package that support "testing" or "wheezy". The four that are named are "etch" "lenny" "sid" and "experimental"; when the driver installer is extracted the supported releases can be seen in packages/Debian/dists

This is why I suggested trying to build with "Debian/sid" instead of "Debian/testing". Not using a different release, just a change in command.

Finally, there is a difference between the fglrx packages in Ubuntu and Debian, that is, you can't install the Debian fglrx-driver and fglrx-control debs in Ubuntu without some dependency problems, and you can't install the Ubuntu fglrx and fglrx-amdcccle debs in Debian. The binary driver itself will be the same, it's the generated deb files that are different. Look at what happens if you add sid sources to Ubuntu, or add random PPAs to Debian.


Got it. Thank you for the clarification.
I will try your advice to compile for Debian/sid.
Appreciated! ;)

---

### Post by erickwill on 2013-01-16
Into compiling I am already stuck at.. :(

```
make: ldconfig: Command not found
make: *** [binary] Error 127
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2

```

I don't know if it matter but I wasn't able to install dh-modialiases for the compilation.

Appreciate any thought.

---

### Post by jfernyhough on 2013-01-16
Are you sure you should be trying this? The log is pretty straightforward as to which executable is missing.

I'm not going to answer any more as I don't think it's a good use of either of our time. You need to learn to search the web (e.g. using Google) and the Debian forums first, rather than posting every issue that crops up. At school did you raise your hand every time you couldn't do something? Or did you try and work it out yourself first?

(Aside: most pupils raise their hands at the first sign of difficulty. This requires the teacher to realise this isn't a good thing and promote a little independence and resilience in the pupils.)

Also remember that this forum is for the development version of Ubuntu. For example, I could suggest making sure you have build-essential installed - but is the Ubuntu version the same as the Debian version? You're running Wheezy, which is moving towards stable, and has various software several versions behind Raring.

---

### Post by erickwill on 2013-01-16
> **jfernyhough said:**
> Are you sure you should be trying this? The log is pretty straightforward as to which executable is missing.

I'm not going to answer any more as I don't think it's a good use of either of our time. You need to learn to search the web (e.g. using Google) and the Debian forums first, rather than posting every issue that crops up. At school did you raise your hand every time you couldn't do something? Or did you try and work it out yourself first?

(Aside: most pupils raise their hands at the first sign of difficulty. This requires the teacher to realise this isn't a good thing and promote a little independence and resilience in the pupils.)

Also remember that this forum is for the development version of Ubuntu. For example, I could suggest making sure you have build-essential installed - but is the Ubuntu version the same as the Debian version? You're running Wheezy, which is moving towards stable, and has various software several versions behind Raring.


Thank you very much for your so polite and kind reply. Really, you almost got me cry! ;)
I will  no respond to all you allegations cuz it's senseless for me.
Just one point.. a forum, whatever forum, is supposed to be a place of help and mutual collaboration and those who join it supposed to have this spirit, not making judgments but donating themselves for share knowledge, as I do in other forums where I help FYI.
For sure you do not represent all the users of this forum and maybe you are not in a good day... anyway.. chill out bud.. the life is too short to get freak and **** out with every breath.
But.......... THANKS anyway for your collaboration!

---

### Post by cariboo on 2013-01-17
@erickwill, this is the wrong sub-forum for what you are trying to do. We are here to discuss the development of Raring Ringail, Ubuntu and it's derivatives. For what you are trying to do, [Other OS/Distro Talk]("http://ubuntuforums.org/forumdisplay.php?f=401"), is probably a much better place to discuss what you want to do.

---

### Post by erickwill on 2013-01-17
> **cariboo907 said:**
> @erickwill, this is the wrong sub-forum for what you are trying to do. We are here to discuss the development of Raring Ringail, Ubuntu and it's derivatives. For what you are trying to do, [Other OS/Distro Talk]("http://ubuntuforums.org/forumdisplay.php?f=401"), is probably a much better place to discuss what you want to do.

Thanks ;)

---

### Post by jfernyhough on 2013-01-17
OK, people, 13.1 is out:
[http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip](http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip)

**Release notes:**
[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst131ProprietaryLinuxGraphicsDriverReleaseNotes.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst131ProprietaryLinuxGraphicsDriverReleaseNotes.aspx)

Selected highlights follow:

[B][COLOR=#333333]System Requirements:
[/COLOR][/B][COLOR=#333333]Before attempting to install the AMD Catalyst Linux software suite, the following software must be installed:[/COLOR]
 
[LIST]
[*] [COLOR=black]Xorg/Xserver 6.9 and above (up to 1.13)[/COLOR]
[*] [COLOR=black]Linux kernel 2.6 or above (up to 3.5)[/COLOR]
[*] glibc version 2.2 or 2.3
[*] POSIX Shared Memory (/dev/shm) support is required for 3D applications
[/LIST]
 [B][COLOR=#333333]New Features: 
[/COLOR][/B][COLOR=#333333]The following section provides a summary of new features in this driver version.[/COLOR]
 
[LIST]
[*][COLOR=black]XServer 1.13 support[/COLOR]
[*][COLOR=black]Ubuntu 12.10 Production Support[/COLOR]
[/LIST]
 **[COLOR=#333333]Resolved Issues[/COLOR]****[COLOR=#333333]:[/COLOR]**[COLOR=#333333]
[/COLOR][COLOR=#333333]This section provides information on resolved known issues in this release of the AMD Catalyst Linux software suite.[/COLOR]
 
[LIST]
[*] [COLOR=#333333][368958]: Driver release version is added to GL_VERSION[/COLOR]
[*] [COLOR=#333333][367282]: Bblank VGA display after resume from suspend[/COLOR]
[*] [COLOR=#333333][367245]: X crash for AMD PowerXpress&#8482; [/COLOR][COLOR=#333333]A+I High-Performance mode on Ubuntu 12.10[/COLOR]
[*] [COLOR=#333333][366820]  Performance of [/COLOR][COLOR=#333333]Valve Linux games[/COLOR]
[*] [COLOR=#333333][366805]: Segmentation fault when exit QtOpenGL applications such as AMD CodeXL[/COLOR]
[*] [COLOR=#333333][366425]: Xserver getting exit upon resume from suspend on RHEL 5.8 [/COLOR]
[*] [COLOR=#333333][364107]: VariBright not working when change AMD PowerPlay&#8482; [/COLOR][COLOR=#333333]settings in AMD Catalust Control Center:LE[/COLOR]
[*] [COLOR=#333333][363638]: VariBright doesn&#8217;t work after resume from suspend on "Trinity" [/COLOR][COLOR=#333333]platform[/COLOR]
[*] [COLOR=#333333][350759]: Flickering cursor when run some full-screen OpenGL games with CrossFire enabled[/COLOR]
[*] [COLOR=#333333][347895]: OpenGL performance [/COLOR][COLOR=#333333]on "Southern Islands" ASICs[/COLOR]
[*] [COLOR=#333333][344996]: 16 re-frames doesn&#8217;t work for H.264 @Level 5.1[/COLOR]
[*] [COLOR=#333333][337240]: Corruption when resize the Konsole window[/COLOR]
[*] [COLOR=#333333][304016]: One display goes black after changing from multi-display desktop from single independent [/COLOR]
[/LIST]
 [B][COLOR=#333333]Known Issues:
[/COLOR][/B][COLOR=#333333]The following section provides a summary of open issues that may be experienced with the AMD Catalyst Linux software suite. [/COLOR]
 
[LIST]
[*][356966]: Tearing appears at the top/left corner with monitor rotation + Vsync is enabled
[*][350671]: Corruption may be experienced when running Unigine Tropics 1.3
[*][341497]: OpenGL Bitmap performance may be impacted in certain situations
[/LIST]


**My status:**
[s]Downloading[/s]
[s]Extracting[/s]
Trying a --buildpkg. DKMS error. S'prise.
Trying to add in the Ubuntu patches from the latest repo version. => module builds, no DKMS errors, depmod completes.Reboot, seems fine. :)

---

### Post by jfernyhough on 2013-01-17
This time a slightly modified method to take advantage of the existing patches. :)

1) Extract driver packages
2) Add in Ubuntu patches for 3.7 and 3.8 support
3) Build
4) Install
5) Reboot

1) Download and extract:
```

$ cd ~/temp
$ wget http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip
$ unzip amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip
$ sh ./amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run --extract amd

```2) Add patches for 3.7 and 3.8 kernel support:
```

$ wget https://launchpad.net/ubuntu/+archive/primary/+files/fglrx-installer_9.010-0ubuntu2.debian.tar.gz

```Now open the zip and extract the files in dkms/patches to ~/temp/amd/packages/Ubuntu/dists/[source and quantal]/dkms/patches/ 
Both source and quantal probably isn't needed, it's a catch-all until I test one or the other.

Extract "dkms.conf.in" to ~/temp/amd/packages/Ubuntu/dists/[source and quantal]/

3) Build:
```

$ cd ~/temp/amd
$ ./ati-installer.sh 9.012 --buildpkg Ubuntu/raring

```4) Install:
```

$ cd ..
$ sudo dpkg -i *.deb

```5) Reboot. Use your favourite method. ;)

---

### Post by MadNachos on 2013-01-18
> **jfernyhough said:**
> 
[/code]5) Reboot. Use your favourite method. ;)

How dare you leave me hanging! How do I reboot?  ;)

Thanks for the info on the new version. I am way too caught up in work to keep track of this stuff so it really makes it easy for me. Much appreciated.

edit: Its working well for my with my HD 6870. Just a couple notes: amd-driver-installer-catalyst-13.1-linux-x86.x86_64.sh should be amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run and for some reason gunzip gave me an unknown extension error so I just used unzip. Otherwise your installation instructions are spot on. Thanks again.

---

### Post by jfernyhough on 2013-01-19
Thanks, updated my instructions. :)

---

### Post by JSeymour421 on 2013-01-19
Hey thanks for the guide very straight forward for 13.1 But I am having a problem here. After I do all the steps you mention with no errors. When I boot up linux i get a low graphic mode screen. I use > sudo amdconfig --initial then reboot but cant seem to get drivers up and running checked > sudo nano /etc/X11/xorg.conf on reboot and fglrx is in there just dont know what is going on. Oh prob would help If i said I use a 6620g+6750m switchable graphic combo in my laptop

---

### Post by jfernyhough on 2013-01-19
[s]Just to verify, did fglrx work previously? Which version?

Which kernel are you running? Did you reinstall for today's latest (3.8.0-1.5)?[/s]

> **JSeymour421 said:**
> I use a 6620g+6750m switchable graphic combo in my laptop

It may be the switchable graphics that's creating the problem. Anandtech have an article about problems with hybrid graphics and the 13.1 driver: [http://www.anandtech.com/show/6680/amds-mobility-catalyst-131-update-enduro-edition](http://www.anandtech.com/show/6680/amds-mobility-catalyst-131-update-enduro-edition)

---

### Post by Nemesis2012 on 2013-01-20
the new catalyst is in the xorg-edgers repo

---

### Post by jfernyhough on 2013-01-21
Hey! Guess what?

New "legacy" drivers!

Page:
[http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)

Link:
[http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip](http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip)

Download, test, let me know. I don't have an HD2000-4000 card to test with. ;)

---

### Post by bettlebrox on 2013-01-21
> **jfernyhough said:**
> No. There are not any fglrx drivers for cards older than the 5000-series which work with xserver 1.13.

If you want fglrx you'll have to stick with Precise; if you want to run Raring you can use the open-source drivers (which should by now perform about as well as well as the proprietary ones for most stuff).

That's what I thought, and thanks for letting me know. The Open Source drivers aren't bad, but I play a fair number of games on my laptop and the 3D throughput isn't as good as with the proprietary drivers. :sad:

---

### Post by bettlebrox on 2013-01-21
> **jfernyhough said:**
> Hey! Guess what?

New "legacy" drivers!

Page:
[http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)

Link:
[http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip](http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip)

Download, test, let me know. I don't have an HD2000-4000 card to test with. ;)

Just an FYI, these still only support X 1.12:

"Automated installer and Display Drivers for Xorg 6.9 to Xserver 1.12 and Kernel version up to 3.4".

:(

---

### Post by jfernyhough on 2013-01-21
I'm pretty sure they haven't edited the page since the 12.6 beta. The main 13.1 release has 1.13 and kernel 3.6 support; I'd assume this one does too. :)

Whether the patches work with this release to bring it up to kernel 3.8 is another matter. ;)

---

### Post by iniside on 2013-01-22
Using kernel 3.8rc4, xorg 1.13 and newest catalyst (13.1) all I get is black screen. It boot, then screen flick several times changing modes between analog and digital and it remains black.

Any ideas where to start diagnosing this problem ?

Radeon HD7850

edit:
Seems I solved my problem. Dunno what exactly issue was but here is what I have done in case anyone run into similiar issue:
1. I purged ALL unused kernels from system, leaving only two.
2. Then I purged all fglrx.
3. Removed xorg.conf
4 sudo update-grub2
5. reboot. 
6. I booted kernel 3.5 and installed drivers from here. Didn't run amdconfig.
7. restarted and booted from kernel 3.8 ( I have compiled it manually). 
8. Finally I run amdconfig --initial 
Now it's working fine.

---

### Post by bettlebrox on 2013-01-22
> **bettlebrox said:**
> Just an FYI, these still only support X 1.12:

"Automated installer and Display Drivers for Xorg 6.9 to Xserver 1.12 and Kernel version up to 3.4".

:(

I figured I try 'em and see what happens. ):P

They build work both without the patches on the first page, and with the patches. The resultant DEB files fail to install, with or without the patches.

Here's the contents of /var/lib/dkms/fglrx/8.970/build/make.log, which is from a build of the DEB's with the patches:

```
DKMS make.log for fglrx-8.970 for kernel 3.7.0-7-generic (i686)
Tue Jan 22 22:46:57 EST 2013
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.a .??* *.symvers
make -C /lib/modules/3.7.0-7-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.970/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-3.7.0-7-generic'
  CC [M]  /var/lib/dkms/fglrx/8.970/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.970/build/2.6.x/firegl_public.c: In function ‘KCL_MEM_AllocLinearAddrInterval’:
/var/lib/dkms/fglrx/8.970/build/2.6.x/firegl_public.c:2152:5: error: implicit declaration of function ‘do_mmap’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/var/lib/dkms/fglrx/8.970/build/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.970/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.7.0-7-generic'
make: *** [kmod_build] Error 2
build failed with return value 2
~
```
 
This is on a 32-bit 3.7 kernel:

uname -a
Linux micks-laptop 3.7.0-7-generic #15-Ubuntu SMP Sat Dec 15 14:12:30 UTC 2012 i686 i686 i686 GNU/Linux

Cheers!
Mick

---

### Post by jfernyhough on 2013-01-23
```

/var/lib/dkms/fglrx/8.970/build/2.6.x/firegl_public.c: In function &#8216;KCL_MEM_AllocLinearAddrInterval&#8217;:
/var/lib/dkms/fglrx/8.970/build/2.6.x/firegl_public.c:2152:5: error: implicit declaration of function &#8216;do_mmap&#8217; [-Werror=implicit-function-declaration] 
```Two things. One, is that the right driver? 8.970 doesn't tally with the 9.012 of 13.1... although this could be due to it being the "legacy" branch.

Two, it doesn't look like the patches from this thread are enough. Both of those errors ("kcl_mem" and "do_mmap") IIRC were fixed in a patch for kernel 3.5 so it might be worth looking back at the fglrx threads for quantal, or the legacy driver source from the repo for the 3.5 patches.

--edit
Oh, and three, why are you still running kernel 3.7? :P

---

### Post by bettlebrox on 2013-01-23
> **jfernyhough said:**
> 
--edit
Oh, and three, why are you still running kernel 3.7? :P
Because I've been putting off upgrading in case something breaks! ;)

I'll upgrade the kernel tonight and will try and build the packages tomorrow or over the weekend. I'll post an update later.

---

### Post by bettlebrox on 2013-01-23
> **jfernyhough said:**
> Two things. One, is that the right driver? 8.970 doesn't tally with the 9.012 of 13.1... although this could be due to it being the "legacy" branch.


I reran the amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run file without any arguments and it popped up a window that said (also see the attachment):

"Install Driver 8.97.100.7 on X.Org 6.9 or later."

I tried grepping the extracted files and I didn't find where this driver is being set. 

Also looking at [AMD's page]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx") it lists the version at the top of the page as 12.6 and at the bottom of the page it says:

"AMD Catalyst™ 13.1 Proprietary Linux x86 Display Driver".

Maybe AMD's just really confused about the version numbers? :)

I'll look at this some more either tomorrow or over the weekend.

---

### Post by Stinger on 2013-01-24
> **jfernyhough said:**
> Hey! Guess what?

New "legacy" drivers!

Page:
[http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)

Link:
[http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip](http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip)

Download, test, let me know. I don't have an HD2000-4000 card to test with. ;)

I have installed the fglrx-legacy package '2:8.97.100.7-makson1~ppa1'  from here [https://launchpad.net/~makson96/+archive/fglrx]("https://launchpad.net/~makson96/+archive/fglrx") but it's only for Quantal (yes I'm still using Quantal)

My graphics card is a Radeon HD 4670 and it works perfectly when I use the above ppa :D
It says:
> This repository is downgradeing X-Server from 1.13 to 1.12.4 (which is maximum version supported by the drivers). Also [COLOR="Red"]driver Catalyst 13.1 (fglrx 8.97.100.7)[/COLOR] is patched with this:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/993427](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/993427)
(comment 14), so it could work on Linux kernel 3.5.
Maybe this could work for Raring too, I mean applying the patch and downgrading X-server to 1.12.4 ?

---

### Post by MWisBest on 2013-01-29
I can't seem to get fglrx working now. Used to work with an AMD A8-4500M APU (AMD Radeon HD 7640G GPU) around the start of January or so. I now got a laptop with an AMD A10-4600M APU (AMD Radeon HD 7660G GPU) and I cannot get fglrx working. I boot up the computer, and X refuses to start. I don't think I had kernel 3.8 on the A8-4500M, was probably still 3.7 and I used 12.11 beta (the first beta they put out, I didn't bother upgrading) with the patches you provided here for kernel 3.7 support. I'm not sure why this isn't working. Any ideas? I can post the log for X refusing to start if needed, I'll just have to reinstall Kubuntu 13.04 afterwards because no matter what I do I always end up with issues after removing fglrx. Not a big deal though.

EDIT: I've tried installing from AMD, from the xorg-edgers repo, and even tried using the older version in the default Ubuntu repositories. All had the same issue.

---

### Post by jfernyhough on 2013-01-29
New beta release (13.2 beta 3).

There's still no official support for kernels newer than 3.5 yet. Hopefully the Ubuntu patches will still work (and as I write edgers don't yet have this version, wonder if it will be within two days of release as with the last ;))

[http://support.amd.com/us/kbarticles/Pages/RN_LN_CAT13-2_Beta.aspx](http://support.amd.com/us/kbarticles/Pages/RN_LN_CAT13-2_Beta.aspx)

**Selected highlights:**

[LIST]
[*][370476 ]: Resolves a Team Fortress 2 performance issue with Ubuntu  12.04/12.10 and AMD Radeon™ HD 7000, 6000 Series GPU. Up to 300%  performance improvement
[*][369298 ]: Resolves a Serious Sam 3 launching and corruption issue  with Ubuntu 12.04/12.10 and AMD Radeon™ HD 7000, 6000 Series GPU
[/LIST]
(Yeah, 300%...)


[B]Linux Distributions Supported:
[/B]The AMD Catalyst™ 13.2 Beta Driver for Linux is designed to support the following Linux distributions: 
 
[LIST]
[LIST]
[*]Red Hat Enterprise Linux suite 5.7, 5.8, 6.2 and 6.3
[*]SUSE Linux Enterprise 10 SP4 and 11 SP2
[*]OpenSUSE 11.4 and 12.1
[*]Ubuntu 12.10
[/LIST]
[/LIST]
 [B]System Requirements:
[/B]Before attempting to install the AMD Catalyst™ Linux graphics driver, the following software must be installed: 
 
[LIST]
[LIST]
[*]Xorg/Xserver 6.9 and above (up to 1.13)
[*]Linux kernel 2.6 or above (up to 3.5)
[*]glibc version 2.2 or 2.3
[*]POSIX Shared Memory (/dev/shm) support is required for 3D applications
[/LIST]
[/LIST]

---

### Post by jfernyhough on 2013-01-29
My status:
[s]Downloading[/s]
[s]Adding in Ubuntu patch pack.[/s]
Built, installed, DKMS builds module.

As before:
* Extract the driver
* Download the Ubuntu patches ([https://launchpad.net/~xorg-edgers/+archive/ppa/+files/fglrx-installer_9.012-0ubuntu1%7Exedgers%7Eraring1.debian.tar.gz](https://launchpad.net/~xorg-edgers/+archive/ppa/+files/fglrx-installer_9.012-0ubuntu1%7Exedgers%7Eraring1.debian.tar.gz)).
* Replace patches in [driver]/packages/Ubuntu/dists/source/dkms/patches
* Replace [driver]/packages/Ubuntu/dists/source/control
* Replace [driver]/packages/Ubuntu/dists/source/dkms.in
* Build debs
* Install
* Reboot

---

### Post by MWisBest on 2013-01-30
> **MWisBest said:**
> I can't seem to get fglrx working now. Used to work with an AMD A8-4500M APU (AMD Radeon HD 7640G GPU) around the start of January or so. I now got a laptop with an AMD A10-4600M APU (AMD Radeon HD 7660G GPU) and I cannot get fglrx working. I boot up the computer, and X refuses to start. I don't think I had kernel 3.8 on the A8-4500M, was probably still 3.7 and I used 12.11 beta (the first beta they put out, I didn't bother upgrading) with the patches you provided here for kernel 3.7 support. I'm not sure why this isn't working. Any ideas? I can post the log for X refusing to start if needed, I'll just have to reinstall Kubuntu 13.04 afterwards because no matter what I do I always end up with issues after removing fglrx. Not a big deal though.

EDIT: I've tried installing from AMD, from the xorg-edgers repo, and even tried using the older version in the default Ubuntu repositories. All had the same issue.

Well I found out the issue. Apparently UEFI booting breaks fglrx reading the GPU's BIOS. Probably a broken implementation of it. With my other laptop I couldn't even boot Linux via UEFI to begin with, now with this one I just can't start X using fglrx and UEFI. So, I went and enabled Legacy Support in the BIOS and installed the classic way. fglrx is working now; I installed via the xorg-edgers PPA.

By the way, that PPA has the latest beta already, but the version of it is very strange... "2:12.100~beta3-0ubuntu1~xedgers~raring1" I don't see where they're getting 12.100, so I'm going to wait on installing it as that doesn't seem right.

---

### Post by jfernyhough on 2013-01-30
The version number has changed. I'm not sure if it's a number jump or an alignment to the Catalyst version, but 12.100 is the correct number.

The edgers guys are doing a good job of updates. Only a couple of hours after the release. If they keep it up there won't be much reason for this thread. :D

---

### Post by MWisBest on 2013-01-31
> **jfernyhough said:**
> The version number has changed. I'm not sure if it's a number jump or an alignment to the Catalyst version, but 12.100 is the correct number.

The edgers guys are doing a good job of updates. Only a couple of hours after the release. If they keep it up there won't be much reason for this thread. :D

I updated via the xorg-edgers repo. It has a "Testing use only" watermark. Any ideas on how to get rid of it?

---

### Post by jfernyhough on 2013-01-31
> **MWisBest said:**
> "Testing use only" watermark. Any ideas on how to get rid of it?You need to copy across a release-version signature to /etc/ati/signature.

I've attached the signature from 13.1.

---

### Post by unheeding on 2013-02-11
I was able to build and install the fglrx driver using the instructions for 13.1, everything went good.  I rebooted, and then Unity wouldn't start.  I had this same problem a few weeks ago on kernel 3.5 with the fglrx that is in the repos.  I'm pretty sure an update to Unity fixed it.

Do you think this is caused because my packages (besides the kernel) are still on quantal?  The version of Unity appears to be the same in both raring and quantal (6.12), so that seems a little unlikely.  I'm going to try reinstalling the drivers and doing an aticonfig --initial, but if that doesn't work I'm happy to use the open source drivers.  However, any suggestions would be welcome!

---

### Post by akarimco on 2013-02-15
> **unheeding said:**
> I was able to build and install the fglrx driver using the instructions for 13.1, everything went good.  I rebooted, and then Unity wouldn't start.  I had this same problem a few weeks ago on kernel 3.5 with the fglrx that is in the repos.  I'm pretty sure an update to Unity fixed it.

Do you think this is caused because my packages (besides the kernel) are still on quantal?  The version of Unity appears to be the same in both raring and quantal (6.12), so that seems a little unlikely.  I'm going to try reinstalling the drivers and doing an aticonfig --initial, but if that doesn't work I'm happy to use the open source drivers.  However, any suggestions would be welcome!

I'm having this exact same problem, and sadly I'm just now getting back into Ubuntu after years of not using it, so I'm quite rusty and was only a small step above a noob when I stopped using it (I think Jaunty was the last time I used it). I'm about to try the driver in the standard repos as I'm totally clueless what to do and am just going to poke around... heck, that's how I learned what I already know anyway.

Edit: I just installed whatever fglrx the update manager wanted me to (I assume it was the fglrx available in the repos), and I'm stuck with the same result. Trying to reload Unity shows a ton of errors in Compiz...oh boy, I just couldn't leave well enough alone, could I! I love Linux, but dang, one little mistake and the whole thing comes apart at the seams!

---

### Post by jfernyhough on 2013-02-22
13.1 beta 6 is available from the Xorg Edgers PPA.

---

### Post by janos666 on 2013-02-22
I have the same problem with a Llano laptop running in UEFI boot mode (with the dedicated VGA disabled).

fglrx stopped working with a kernel upgrade. I tried to remove it but xserver didn't really got recovered. I had to use the nomodeset parameter at boot. But that's not too good.

I tried to use the xorg-edgers PPA a few days ago. I still don't have a working desktop with or without fglrx.
If I remove it now then I can't even use tty1 after booting with nomodoset (let alone the graphic desktop). I had to reinstall fglrx from recovery mode to be able to anything.

atifoncfig seems to detect the card since I ran a dist-upgrade today (it din't see anything lat time). But it's still broken. May be I need to do something with xserver to get it working again.
I tried some things to reset xserver but it didn't really work.

---

### Post by crepito on 2013-02-23
How is the performance of fglrx on 13.04, at its current state, compared to 12.04 for gaming? Does it bring some value?

---

### Post by cariboo on 2013-02-23
> **crepito said:**
> How is the performance of fglrx on 13.04, at its current state, compared to 12.04 for gaming? Does it bring some value?

Things are in a state of flux, as Raring is still in development, performance depends a lot on the state of updates, which can be done several times a day. Comparing it against a released version really means nothing. I'd suggest if you aren't helping test Raring, that you wait until it is released before trying to make comparisons.

---

### Post by Izy on 2013-02-25
> **jfernyhough said:**
> This time a slightly modified method to take advantage of the existing patches. :)

1) Extract driver packages
2) Add in Ubuntu patches for 3.7 and 3.8 support
3) Build
4) Install
5) Reboot

1) Download and extract:
```

$ cd ~/temp
$ wget http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip
$ unzip amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip
$ sh ./amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run --extract amd

```2) Add patches for 3.7 and 3.8 kernel support:
```

$ wget https://launchpad.net/ubuntu/+archive/primary/+files/fglrx-installer_9.010-0ubuntu2.debian.tar.gz

```Now open the zip and extract the files in dkms/patches to ~/temp/amd/packages/Ubuntu/dists/[source and quantal]/dkms/patches/ 
Both source and quantal probably isn't needed, it's a catch-all until I test one or the other.

Extract "dkms.conf.in" to ~/temp/amd/packages/Ubuntu/dists/[source and quantal]/

3) Build:
```

$ cd ~/temp/amd
$ ./ati-installer.sh 9.012 --buildpkg Ubuntu/raring

```4) Install:
```

$ cd ..
$ sudo dpkg -i *.deb

```5) Reboot. Use your favourite method. ;)

Did Someone try this with Kernel above 3.7.5? With Kernel 3.7.5 this solution works pretty well but I tried this with Kernel 3.7.6 and 3.8 and I get the error with "low graphic mode".  Has someone experience or a solution with that?

---

### Post by jfernyhough on 2013-02-25
Yes. Use the packages from the Edgers PPA.

---

### Post by jfernyhough on 2013-02-28
13.2 beta 7 is in Edgers. AMD page hasn't been updated from beta 6 yet, so no idea about changes. :D

---

### Post by xaliqen on 2013-03-18
Is there a good solution for installing fglrx 13.1 legacy drivers in Raring, yet?  Correct me if I'm wrong, but I'm pretty sure the Edgers PPA doesn't have the legacy package.

---

### Post by jfernyhough on 2013-03-19
There are no AMD legacy drivers for xorg 1.13. You'll have to stick with 1.12 (e.g. use 12.04 LTS) or use the open-source drivers.

---

### Post by Stinger on 2013-03-19
> **xaliqen said:**
> Is there a good solution for installing fglrx 13.1 legacy drivers in Raring, yet?  Correct me if I'm wrong, but I'm pretty sure the Edgers PPA doesn't have the legacy package.

Not yet. 
Although some packages for Raring are starting to arrive in the [AMD Catalyst Legacy ppa]("https://launchpad.net/~makson96/+archive/fglrx")
This ppa works for Precise and Quantal, I'm using it for Quantal myself.

> This repository is downgradeing X-Server from 1.13 to 1.12.4 (which is maximum version supported by the drivers). Also driver Catalyst 13.1 (fglrx 8.97.100.7) is patched with this:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/993427](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/993427)
(comment 14), so it could work on Linux kernel 3.5.

---

### Post by jfernyhough on 2013-03-25
Catalyst 13.3 beta 3 (fglrx 12.10.17) is out: [http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-3LINBetaDriver.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-3LINBetaDriver.aspx) (Note: this is still only for HD5000+ cards):

This isn't in Edgers yet so we can have some of our own driver building fun!

[COLOR=#333333]**[FONT=arial]Resolved Issues[/FONT]**[/COLOR]
 
[LIST]
[*][FONT=arial][370253]:  Serious Sam 3 - Color of Objects turning into be red when enabling separate shader object[/FONT] 
[*][FONT=arial][371937]:  Team Fortress 2 - Screen black issue while entering the game screen under cinnamon desktop environment[/FONT] 
[*][FONT=arial][371733]:  Team Fortress 2 - Change settings without restarting would reduce FPS down to the 20s/30s[/FONT] 
[*][FONT=arial][371374]:  Team Fortress 2 - Screen random flickering and corruptions in Lakeside Map[/FONT] 
[*][FONT=arial][369893]:  Xserver starting failure after switching to Power-Saving mode on PowerXpress A+I platform with Ubuntu 12.10[/FONT] 
[*][FONT=arial][368970]:  System cannot switch to Power-Saving mode on some HP PowerXpress A+I platforms[/FONT] 
[*][FONT=arial][370067]:  System hang up when logging out in Power-Saving mode on PowerXpress A+A platform[/FONT] 
[*][FONT=arial][371116]:  Startx failure in Power-Saving mode on PowerXpress A+I platform[/FONT] 
[*][FONT=arial][370316]:  Xserver crash in High-Performance mode on PowerXpress A+I platform with Intel Haswell[/FONT] 
[*][FONT=arial][373156]:  Login screen garbage on PowerXpress A+I system with latest Intel graphics driver[/FONT] 
[*][FONT=arial][372650]:  Black window issue for OpenGL applications when using XRender backend of kwin[/FONT] 
[*][FONT=arial][369981]:  Adding Kernel 3.7 support[/FONT] 
[*][FONT=arial][369982]:  Adding Kernel 3.8 support[/FONT] 
[/LIST]
 [COLOR=#333333]**[FONT=arial]Open Issues[/FONT]**[/COLOR]
 
[LIST]
[*][FONT=arial][372010]:  Failed to change Gamma setting in game option of Amnesia[/FONT] 
[*][FONT=arial][373836]:  Vsync application shows corruption filed[/FONT] 
[*][FONT=arial][373772]:  Team Fortress 2 &#8211; Game could not be loaded in &#8220;High Performance GPU&#8221; mode[/FONT] 
[*][FONT=arial][373906]:  Glxtest failed on VBO Test[/FONT] 
[*][FONT=arial][373909]:  Driver install via .deb package will cause OS desktop corruption[/FONT] 
[/LIST]
[COLOR=#333333]

**My status:**
[s]Downloading[/s]
[s]Unpacking[/s]
Trying to build using $ sh ./amd-driver-installer-catalyst-13.3-beta3-linux-x86.x86_64.run --buildpkg Ubuntu/raring
debs built (fglrx_12.100-0ubuntu1), installing
DKMS module build "OK"
depmod completes "OK"
Checking /etc/ati/signature: unsigned
Copying across signature from 13.2b3.

Rebooting... though "[/COLOR][FONT=arial][373909]:  Driver install via .deb package will cause OS desktop corruption" doesn't look promising! :D[/FONT]

[Edit: Post 1000! Woo!]

---

### Post by jfernyhough on 2013-03-26
OK, finally rebooted and everything looks fine in XFCE. I wonder if [FONT=arial]373909 is an edge-case...[/FONT]

---

### Post by samigina on 2013-03-27
Unity working ok with 13.3 beta 3.

---

### Post by nefarinus on 2013-03-31
Can u post this signature here I did everything just as u have written, and don't know how to get signature. plz help :)

---

### Post by Benjamindaines on 2013-04-02
Is there a patch for kernel 3.9 around?

---

### Post by jfernyhough on 2013-04-24
Catalyst 13.4 (fglrx 12.104) has been released. No release notes yet.

Page: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)
Download: [http://www2.ati.com/drivers/linux/amd-catalyst-13.4-linux-x86.x86_64.zip](http://www2.ati.com/drivers/linux/amd-catalyst-13.4-linux-x86.x86_64.zip)

My status:
[s]Downloading[/s]
Unpacking, trying a --buildpkg Ubuntu/raring
debs built, installing
DKMS "OK".
depmod "OK"
Signature check: driver is signed (as expected for a full release).
Rebooting.

Running fine with Liquorix 3.8-8. Going to test with kernel 3.9 (though I can't see it working :D).

Interesting!
$ dkms status
fglrx, 12.104, 3.8-8.dmz.1-liquorix-amd64, x86_64: installed
fglrx, 12.104, 3.9.0-030900rc8-generic, x86_64: installed

13.4 might have 3.9 support (which is good, as Raring will ship with 3.9).

Rebooted. Well, what do you know! 3.9 support! Nice!

---

### Post by rechter77 on 2013-04-25
Hi guy!!!
I have a Dell inspiron 14Z with ATI Radeon 7500M/7600M and I need install the drivers.
I already tried the additional drivers but not worked.
I tried too Andrikos PPA and nothing worked.
Anyone can help me ???
Thanks in advance.

Christopher

---

### Post by jmite on 2013-04-25
Has anybody managed to get this working on an AMD/Intel Hybrid (powerXpress) system? I've tried installing 13.4 in Raring, and get the "X is starting in low-graphics mode" screen.

---

### Post by jfernyhough on 2013-04-25
X Edgers now has fglrx-12 and fglrx-amdccle-12, packaging this latest release. Nice!

---

### Post by rechter77 on 2013-04-25
what is the repo ?

---

### Post by deadite66 on 2013-04-25
[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=raring](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=raring)

---

### Post by rechter77 on 2013-04-25
Thanks.
But look. When I install I lost my Unity ... :(

---

### Post by nardusg on 2013-05-29
new beta out... going to try and will report

---

### Post by jfernyhough on 2013-05-29
New thread for saucy: [http://ubuntuforums.org/showthread.php?t=2149585](http://ubuntuforums.org/showthread.php?t=2149585)

---

### Post by nardusg on 2013-05-29
> **jfernyhough said:**
> New thread for saucy: [http://ubuntuforums.org/showthread.php?t=2149585](http://ubuntuforums.org/showthread.php?t=2149585)

thanks

---

### Post by cariboo on 2013-05-29
Seeing as there is a new thread, there's no need to keep this one open. Thread Closed.

---

