---
title: "fglrx in saucy"
date: 2013-05-29
forum: Ubuntu Development Version
---

### Post by jfernyhough on 2013-05-29
**[SIZE=4]Latest driver:[/SIZE]**

19 August: AMD have released Catalyst 13.8 beta 2.

[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-8LINBetaDriver.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-8LINBetaDriver.aspx)

**Highlights of the AMD Catalyst&#8482; 13.8 Beta Driver for Linux:**
This release of AMD Catalyst&#8482; Linux introduces support for the following new features:

[LIST]
[*]OpenGL 4.3 support 
[*]Dynamic primary surface resizing 
[*]Kernel 3.10 support 
[*]SLED 11 SP3 support 
[/LIST]
**Resolved Issues:**

[LIST]
[*][380355] Source Engine games hang when running on the High Performance ASIC 
[*][330287] Maya 2012 Paint brush fails to leave trails in real time while painting at some areas when desktop effects enabled 
[*][345211] Incorrect object picking in Autodesk Maya using UAV selection solver 
[*][376838] Autodesk Maya fluids display visually very pixelated even at higher resolutions of the fluid voxels 
[*][376823] Mesh/polygons selection take too long to select and deselect compared to Nvidia in Maya 2011-2013 
[*][372767] Unigine Heaven 4.0 crash in high performance GPU 
[*][376891] Enable Optimization on SGPU for 11% Performance gain (unigine heaven) 
[*][377640] Unigine Heaven OGL stops responding at high resolutions with VSync enabled 
[*][376842] Left4Dead2 Corruption is observed 
[*][378135] Left4Dead2 Yellow Screen Bug 
[*][379940] Left4Dead2 Gamma Correction Corruption 
[*][381765] Visual artifacts for XvBA playback with CABAC=No 
[*][380590] The menus are unbelievably slow with vsync disabled for XBMC 
[*][381120] Kernel 3.10 support 
[*][379176] &#8220;Testing use only&#8221; watermark removed 
[*][356014] AA does not function with desktop effects enabled 
[/LIST]
**Open Issues:**

[LIST]
[*][370421] Quake4 fails to render in game sky properly at certain points with High Performance GPU 
[*][377432] Unigine Heaven at high resolution and settings will show intermittent corruptions in crossfire 
[*][380998] System hang when running Counter Strike: Source at low settings on Linux 
[*][382494] C4Engine show corruptions with GL_ARB_texture_array enabled 
[/LIST]

Direct download: [http://www2.ati.com/drivers/beta/amd-catalyst-13.8-beta2-linux-x86.x86_64.zip](http://www2.ati.com/drivers/beta/amd-catalyst-13.8-beta2-linux-x86.x86_64.zip)

Building and installation is as easy as:

```
$ unzip amd-catalyst-13.8-beta2-linux-x86.x86_64.zip
$ sh ./amd-catalyst-13.8-beta2-linux-x86.x86_64.run --buildpkg Ubuntu/saucy
$ sudo dpkg -i *.deb
```

Note: it's not strictly necessary to build the debs but I find it useful, for example when I upgrade a kernel and modules aren't automatically rebuilt.

**[SIZE=4]Latest Ubuntu packages[/SIZE]**

*3 August:* fglrx 13.200 (based on 13.8 beta 1) is in Edgers: [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") (fglrx: 2:13.200~beta-0ubuntu1~xedgers~saucy2), packaged by Rico Tzschichholz.

fglrx 13.100 packages (based on 13.6 beta) are available in saucy-proposed (fglrx: 2:13.101-0ubuntu1), packaged by Alberto Milone.

[B][SIZE=4]Latest kernel patches

[/SIZE][/B]The drivers currently support 3.11-rc5 (3.11.0-2-generic). For unofficial patches for kernel 3.10 see the next post. These should not be necessary, however, and the patches are deprecated. I'm leaving the post for people interested in the process and for future reference!.

---

### Post by jfernyhough on 2013-05-29
**[SIZE=4]Patch latest[/SIZE]**

Krzysztof Kolasa has made available patches which add kernel 3.10 compatibility [1]. I have adapted these slightly and attached them to this post along with ready-patched files. As always, use these at your own risk (WFM, YMMV, ROFLFAQ, etc.).

**[SIZE=4]Manual patching instructions[/SIZE]**

Note: this process is not for the inexpert. Don't ask for help if you can't follow instructions! :D

The process is the same as for previous releases, i.e.:

1) Download
2) Extract
3) Patch
4) Build
5) Install

For this process I assume you have a working directory called "temp" in  your home. Change this to suit. I use /dev/shm as a handy ramdisk. I  also assume you download and extract the patches to that directory.

**Details:**

0) If this is the first time you've done this, install the necessary   development packages  (normally installed by the installer, if any are   missing they should be identified in the output of step 5):
$ sudo apt-get install dpkg-dev debhelper  dh-modaliases execstack

1) Once downloaded (the .run is in a .zip file. I shouldn't have to tell   you how to deal with that), extract the installer files so we can  patch  manually:
$ sh ./amd-driver-installer-catalyst-13-6-beta-x86.x86_64.run --extract ~/temp/amd
$ cd ~/temp

2) Download, extract to ~/temp, and apply the attached patches (adapted from that in kolasa's GitHub repo [1]):
$ patch -p0 < ./310.patch

4) Download and add a release signature (taken from Catalyst 13.4) to remove the testing watermark:
$ cp signature ~/temp/amd/common/etc/ati/

5) Build the packages (this will place the packages in the parent directory):
$ cd ~/temp/amd
$ ./ati-installer.sh 13.101 --buildpkg Ubuntu/saucy

6) Change to the parent directory and install the debs:
$ cd ..
$ sudo dpkg -i *.deb

7) If you haven't done so already, create an Xorg.conf that will load fglrx:
$ sudo amdconfig --init

[1] [https://github.com/kolasa/fglrx-13.101/commit/ae7de2751be17484bc98d82e1c1901e5d432e430](https://github.com/kolasa/fglrx-13.101/commit/ae7de2751be17484bc98d82e1c1901e5d432e430)

---

### Post by jfernyhough on 2013-06-04
Reserved.

---

### Post by jfernyhough on 2013-06-21
Updated debs are now in the repos.

---

### Post by darkphoenix16 on 2013-06-25
> **jfernyhough said:**
> Updated debs are now in the repos.

I'm on Saucy with kernel 3.9.0-7-generic and 13.101-0ubuntu1_amd64 fglrx from fglrx-updates or fglrx

My computer hangs when attempting to startx X using fglrx.  I cannot switch to another console to kill the process or see startx output.  I looked at the fglrx log android not see any entry marked (EE).  I've also looked through dmesg and syslogs

As a final effort I installed the 104 driver from the AMD website which works properly.  Please update the fglrx deb files please :)

---

### Post by vinibali on 2013-07-05
Hey, ive got some problems with the patching.
Can someone help me? :)
Im on stable 3.10

```
balazs@balazs-GA-A75-D3H:/media/ramdisk$ sudo patch -p0 < ./310.patchcan't find file to patch at input line 15
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|From ae7de2751be17484bc98d82e1c1901e5d432e430 Mon Sep 17 00:00:00 2001
|From: Krzysztof Kolasa <kkolasa@winsoft.pl>
|Date: Sat, 1 Jun 2013 23:18:12 +0200
|Subject: [PATCH] Add support for kernel 3.10.0-rc3
|
|---
| drm_proc.h      | 15 ++++++++++
| firegl_public.c | 90 +++++++++++++++++++++++++++++++++++++++++++++++++++++----
| 2 files changed, 100 insertions(+), 5 deletions(-)
|
|diff --git a/drm_proc.h b/drm_proc.h
|index 1e3ab4a..3879352 100644
|--- amd/common/lib/modules/fglrx/build_mod/drm_proc.h
|+++ amd/common/lib/modules/fglrx/build_mod/drm_proc.h
--------------------------
File to patch: 



```

---

### Post by jfernyhough on 2013-07-05
1) Just use the debs from the repo. They work fine, there's no need to patch at the moment.

2) You shouldn't need to use sudo for the patching process. The error also indicates you haven't extracted the driver files to the place the patch is expecting (i.e. /media/ramdisk/amd ).

---

### Post by vinibali on 2013-07-06
there was the driver :confused:
however, i made a clear install yday, and its use the 3.10-2(?) from default.
now it works, thanks :)

---

### Post by jfernyhough on 2013-07-15
Looks like 13.6 supports kernel 3.11-rc1, which is nice. Or at least DKMS builds the kernel modules!

---

### Post by arfett on 2013-07-17
Any ideas?

[http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-13-6-beta-x86.x86_64.zip](http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-13-6-beta-x86.x86_64.zip) extracted to ~/temp/amd

~/temp $ patch -p0 < ./310.patch
patching file amd/common/lib/modules/fglrx/build_mod/drm_proc.h
Hunk #1 FAILED at 95.
Hunk #2 FAILED at 121.
2 out of 2 hunks FAILED -- saving rejects to file amd/common/lib/modules/fglrx/build_mod/drm_proc.h.rej
patching file amd/common/lib/modules/fglrx/build_mod/firegl_public.c

---

### Post by slickymaster on 2013-07-17
> **jfernyhough said:**
> Looks like 13.6 supports kernel 3.11-rc1, which is nice. Or at least DKMS builds the kernel modules!

Yes. I can confirm that.

---

### Post by vinibali on 2013-07-18
> **arfett said:**
> Any ideas?

[http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-13-6-beta-x86.x86_64.zip](http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-13-6-beta-x86.x86_64.zip) extracted to ~/temp/amd

~/temp $ patch -p0 < ./310.patch
patching file amd/common/lib/modules/fglrx/build_mod/drm_proc.h
Hunk #1 FAILED at 95.
Hunk #2 FAILED at 121.
2 out of 2 hunks FAILED -- saving rejects to file amd/common/lib/modules/fglrx/build_mod/drm_proc.h.rej
patching file amd/common/lib/modules/fglrx/build_mod/firegl_public.c

Use the fglrx or fglrx-updates from the ubuntu repo, that works with the 3.10 and the others sad with 3.11 too!

---

### Post by jverga on 2013-07-19
> **slickymaster said:**
> Yes. I can confirm that.


slicky and  jferny; which FGLRX 13.6 debs are you installing that work with kernel 3.11?

---

### Post by jfernyhough on 2013-07-19
```
fglrx:
  Installed: 2:13.101-0ubuntu2
  Candidate: 2:13.101-0ubuntu2
  Version table:
 *** 2:13.101-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/restricted amd64 Packages
        100 /var/lib/dpkg/status
```The official ones from the repo.

---

### Post by slickymaster on 2013-07-19
> **jverga said:**
> slicky and  jferny; which FGLRX 13.6 debs are you installing that work with kernel 3.11?

```
slickymaster@IMT:~$ apt-cache policy fglrx
fglrx:
  Installed: 2:13.101-0ubuntu2
  Candidate: 2:13.101-0ubuntu2
  Version table:
     2:13.101-0ubuntu2 0
        500 http://pt.archive.ubuntu.com/ubuntu/ saucy/restricted i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by jverga on 2013-07-19
Thanks slicky and  jferny  took the plunge. FGLRX working nice  w/ 3.11 daily (on Raring  actually).

---

### Post by slickymaster on 2013-07-19
> **jverga said:**
> Thanks slicky and  jferny  took the plunge. FGLRX working nice  w/ 3.11 daily (on Raring  actually).

Glad you've got it working. :p

---

### Post by jfernyhough on 2013-08-01
Catalyst 13.8 beta has just been released.

[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-8LINBetaDriver.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-8LINBetaDriver.aspx)

**Highlights of the AMD Catalyst&#8482; 13.8 Beta Driver for Linux:**
This release of AMD Catalyst&#8482; Linux introduces support for the following new features:

[LIST]
[*]OpenGL 4.3 support
[*]Dynamic primary surface resizing
[*]Kernel 3.10 support
[*]SLED 11 SP3 support
[/LIST]
**Resolved Issues:**

[LIST]
[*][380355] Source Engine games hang when running on the High Performance ASIC
[*][330287] Maya 2012 Paint brush fails to leave trails in real time while painting at some areas when desktop effects enabled
[*][345211] Incorrect object picking in Autodesk Maya using UAV selection solver
[*][376838] Autodesk Maya fluids display visually very pixelated even at higher resolutions of the fluid voxels
[*][376823] Mesh/polygons selection take too long to select and deselect compared to Nvidia in Maya 2011-2013
[*][372767] Unigine Heaven 4.0 crash in high performance GPU
[*][376891] Enable Optimization on SGPU for 11% Performance gain (unigine heaven)
[*][377640] Unigine Heaven OGL stops responding at high resolutions with VSync enabled
[*][376842] Left4Dead2 Corruption is observed
[*][378135] Left4Dead2 Yellow Screen Bug
[*][379940] Left4Dead2 Gamma Correction Corruption
[*][381765] Visual artifacts for XvBA playback with CABAC=No
[*][380590] The menus are unbelievably slow with vsync disabled for XBMC
[*][381120] Kernel 3.10 support
[*][379176] &#8220;Testing use only&#8221; watermark removed
[*][356014] AA does not function with desktop effects enabled
[/LIST]
**Open Issues:**

[LIST]
[*][370421] Quake4 fails to render in game sky properly at certain points with High Performance GPU
[*][377432] Unigine Heaven at high resolution and settings will show intermittent corruptions in crossfire
[*][380998] System hang when running Counter Strike: Source at low settings on Linux
[*][382494] C4Engine show corruptions with GL_ARB_texture_array enabled
[/LIST]

Direct download: [http://www2.ati.com/drivers/beta/amd-catalyst-13.8-beta1-linux-x86.x86_64.zip](http://www2.ati.com/drivers/beta/amd-catalyst-13.8-beta1-linux-x86.x86_64.zip)

---

### Post by jfernyhough on 2013-08-01
There may be some issues:

```
$ LIBGL_DEBUG=verbose fglrxinfo
libGL: AtiGetClientDriverName: 13.20.4 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/fglrx/dri/fglrx_dri.so
ukiDynamicMajor: failed to open /proc/ati/major
Setting of real/effective user Id to 0/0 failed
ukiDynamicMajor: failed to open /proc/ati/major
ukiDynamicMajor: failed to open /proc/ati/major
ukiDynamicMajor: failed to open /proc/ati/major
libGL error: open uki failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6500M/5600/5700 Series
OpenGL version string: 2.1 (4.3.12438 Compatibility Profile Context 9.01)
```

---

### Post by jfernyhough on 2013-08-02
If you have the same error (i.e. not being allowed access to direct rendering) you will need to change some permissions:

```
$ sudo chmod -R a+rX /proc/ati
```

Thanks to Cdh over on the Arch forums for this! [https://bbs.archlinux.org/viewtopic.php?pid=1307170#p1307170](https://bbs.archlinux.org/viewtopic.php?pid=1307170#p1307170)

Edit:
There's a patch: [http://phoronix.com/forums/showthread.php?82948-AMD-Catalyst-13-8-Beta-Driver-For-Linux-Released&p=348029#post348029](http://phoronix.com/forums/showthread.php?82948-AMD-Catalyst-13-8-Beta-Driver-For-Linux-Released&p=348029#post348029)

```
--- firegl_public.c_old 2013-07-29 17:54:07.000000000 +0200
+++ firegl_public.c_new 2013-08-02 02:59:07.000000000 +0200
@@ -821,7 +821,7 @@
     KCL_DEBUG1(FN_FIREGL_PROC, "minor %d, proc_list 0x%08lx\n", minor, (unsigned long)proc_list);
     if (!minor)
     {
-        root = KCL_create_proc_dir(NULL, "ati", S_IFDIR);
+        root = KCL_create_proc_dir(NULL, "ati", S_IFDIR|S_IRUGO|S_IXUGO);
     }
 
if (!root)
```

Edit 2:
Attached is pre-patched firegl_public.c.

---

### Post by jfernyhough on 2013-08-03
2:13.200~beta-0ubuntu1~xedgers~saucy2 is now available in the Edgers PPA.

[https://launchpad.net/~xorg-edgers/+archive/ppa/+sourcepub/3403649/+listing-archive-extra](https://launchpad.net/~xorg-edgers/+archive/ppa/+sourcepub/3403649/+listing-archive-extra)

---

### Post by cariboo on 2013-08-03
Removed double post.

---

### Post by jfernyhough on 2013-08-06
There appear to be horrible memory leaks with both Catalyst 13.7 (fglrx 13.150) and 13.8 (13.200) manifesting when people run Source games (TF2, L4D2) and occasionally with XBMC. The driver is locking an increasing amount of memory (apparently trying to reserve the full system memory), leading to swapping and system unresponsiveness. Killing the process does not return the memory, so a reboot is needed.

For now, if you use any of these applications or have this issue, Catalyst 13.6 (fglrx 13.101) is the most recent "safe" driver. There are other issues with 13.6, but none quite so severe!

---

### Post by jfernyhough on 2013-08-19
Catalyst 13.8 beta 2 is available:

[http://www2.ati.com/drivers/beta/amd-catalyst-13.8-beta2-linux-x86.x86_64.zip](http://www2.ati.com/drivers/beta/amd-catalyst-13.8-beta2-linux-x86.x86_64.zip)

No changes to the release information.

On a related note, the memory leaks I found with Source games and 13.8beta1 (13.200) haven't occurred since I upgraded to mesa 9.3~git.

Edit: Packages install, DKMS builds the kernel modules and depmod completes, so this also seems to have kernel 3.11 support. Let's see if the fixes for the /proc/ati permissions errors are also included!

Edit 2: The /proc/ati permissions fix has not been included, so you'll have to run *sudo chmod -R a+rX /proc/ati* after each boot to get direct rendering. I imagine the same patch as before will work, but I'll wait to check.

---

### Post by Espionage724 on 2013-09-10
> **jfernyhough said:**
> Catalyst 13.8 beta 2 is available:

[http://www2.ati.com/drivers/beta/amd-catalyst-13.8-beta2-linux-x86.x86_64.zip](http://www2.ati.com/drivers/beta/amd-catalyst-13.8-beta2-linux-x86.x86_64.zip)

Edit 2: The /proc/ati permissions fix has not been included, so you'll have to run *sudo chmod -R a+rX /proc/ati* after each boot to get direct rendering. I imagine the same patch as before will work, but I'll wait to check.

Hmm, seems the fglrx installer on the xorg-edgers PPA is still on beta1 as of currently. Probably easy questions, but:

1. Is it really that simple to install the driver via 3 commands (unzip, build the debs, install the debs)? I recall the unofficial fglrx wiki mentioning you had to install a bunch of other packages like dkms and stuff.
Edit: To answer my own question, it seems so :) During the deb building, it prompts to install packages I don't have... never knew :p

2. Is there a way to automate the chmod command on /proc/ati? Possibly via a startup script?

---

### Post by jfernyhough on 2013-09-10
The patch for the previous version fixing the /proc/ati permissions problem works fine on beta 2 (it's one line). I was waiting for the new version to appear in Edgers but that doesn't seem to have happened yet - which is a bit odd!

DKMS and the other requirements will likely already be installed if you're a typical U+1 tester - otherwise there may be a few deps that will be identified when you try to build.

---

### Post by Espionage724 on 2013-09-10
Ah, thanks for the response.

Seems I ran into a slight issue. Right now I'm using today's 3.11 kernel build, and when fglrx does its thing with DKMS, it fails. make.log mentions **FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol 'acpi_bus_get_device'**

Checking [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/CHANGES](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/CHANGES) mentions:
"ACPI: Move acpi_bus_get_device() from bus.c to scan.c"

---

### Post by jfernyhough on 2013-09-10
Now that's an error I haven't seen before. Does it also happen with the standard repo kernel? (I'm assuming not, as this does seem like more of an idealistic error rather than any real problem!)

This change may also be the reason why the driver hasn't been updated in Edgers - if there are kernel configuration changes then the driver teams will have to deal with them. It's not ideal if this breaks third-party stuff, though. It might be worth reporting that as a regression.

The /proc/ati issue seems to be a driver issue - others have had the same problem e.g. on Arch. I'm really surprised AMD didn't fix it in beta 2.

---

### Post by Espionage724 on 2013-09-10
> **jfernyhough said:**
> Now that's an error I haven't seen before. Does it also happen with the standard repo kernel? (I'm assuming not, as this does seem like more of an idealistic error rather than any real problem!)

Works fine on the included 3.11 kernel on today's saucy build (3.11.0-6-generic)

---

### Post by jfernyhough on 2013-09-10
Worth keeping an eye on with future daily kernels, but those things are slippery. Last time I tried them I found strange issues appeared and disappeared with great regularity.

---

### Post by Espionage724 on 2013-09-12
> **Espionage724 said:**
> Ah, thanks for the response.

Seems I ran into a slight issue. Right now I'm using today's 3.11 kernel build, and when fglrx does its thing with DKMS, it fails. make.log mentions **FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol 'acpi_bus_get_device'**

Checking [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/CHANGES](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/CHANGES) mentions:
"ACPI: Move acpi_bus_get_device() from bus.c to scan.c"

I reported it here: [http://ati.cchtml.com/show_bug.cgi?id=906](http://ati.cchtml.com/show_bug.cgi?id=906)

Apparently, the problem is that the "Module license must be changed to GPL"

---

### Post by Espionage724 on 2013-09-14
Hmm, so about kolasa's Github; how am I exactly supposed to use it?

[https://github.com/kolasa/fglrx-13.20.11](https://github.com/kolasa/fglrx-13.20.11)

It looks like I should compile it, but how? If I compile it, is it supposed to give me some patch file to use to patch the driver itself? The 2nd post mentions some patch file I should be able to get somewhere...

---

### Post by jfernyhough on 2013-09-19
Catalyst 13.9 (fglrx 13.152) is here: [http://www2.ati.com/drivers/linux/amd-catalyst-13.9-linux-x86.x86_64.zip](http://www2.ati.com/drivers/linux/amd-catalyst-13.9-linux-x86.x86_64.zip)

No changelog yet.

Edit:

According to the Phoronix thread, 13.9 is based on 13.6, not 13.8. I have no idea what AMD are doing.

Might be time to try the OSS driver again.

Edit2:

OK, so performance on Source games with the OSS driver is massively better than I've had before with fglrx. The point may be close for fglrx to be retired.

---

### Post by MountainX on 2013-09-29
> **jfernyhough said:**
> Catalyst 13.9 (fglrx 13.152) is here: [http://www2.ati.com/drivers/linux/amd-catalyst-13.9-linux-x86.x86_64.zip](http://www2.ati.com/drivers/linux/amd-catalyst-13.9-linux-x86.x86_64.zip)

Edit2:

OK, so performance on Source games with the OSS driver is massively better than I've had before with fglrx. The point may be close for fglrx to be retired.

I tried the OSS driver again and the performance in regular use (just opening applications, moving windows, etc.) is horrible. I have 3 large monitors, so maybe that's why. There's also a Firefox text editing bug with the OSS driver. So I prefer to use the fglrx driver. I would appreciate any updated info about the fglrx driver and kernel 3.11 (Saucy). Thanks

---

### Post by jfernyhough on 2013-09-30
Catalyst 13.10 beta has been released: [http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-10LINBetaDriver.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-10LINBetaDriver.aspx)

**Resolved Issues:**

[LIST]
[*][383176] System hang up when startx after setting up an Eyefinity desktop
[*][384193] Permission issue with procfs on kernel 3.10
[*][373812] System hang observed while running disaster stress test on Ubuntu 12.10
[*][383109] Hang is observed when running Unigine on Linux
[*][383573] AC/DC switching is not automatically detected
[*][383075] Laptop backlight adjustment is broken
[*][383430] Glxtest failures observed in log file with forcing on Anti-Aliasing
[*][383372] Cairo-dock is broken
[*][378333] Severe desktop corruption is observed when enabled compiz in certain cases
[*][384509] glClientWaitSync is waiting even when timeout is 0
[*][382494] C4Engine get corruption with GL_ARB_texture_array enabled
[/LIST]

Looks like it will need a patch for kernel 3.11 upwards.

---

### Post by jfernyhough on 2013-09-30
> **MountainX said:**
> I tried the OSS driver again and the performance in regular use (just opening applications, moving windows, etc.) is horrible. I have 3 large monitors, so maybe that's why. There's also a Firefox text editing bug with the OSS driver. So I prefer to use the fglrx driver. I would appreciate any updated info about the fglrx driver and kernel 3.11 (Saucy). ThanksDid you enable radeon.dpm=1 on your GRUB boot line? Otherwise performance isn't great as the power profile (and so clock rate) doesn't change.

---

### Post by MountainX on 2013-09-30
> **jfernyhough said:**
> Catalyst 13.10 beta has been released: [http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-10LINBetaDriver.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-10LINBetaDriver.aspx)

Looks like it will need a patch for kernel 3.11 upwards.

Thanks for that. I see this:

[B]System requirements:
Linux kernel 2.6 or above (up to 3.10)  [/B]

---

### Post by MountainX on 2013-09-30
> **jfernyhough said:**
> Did you enable radeon.dpm=1 on your GRUB boot line? Otherwise performance isn't great as the power profile (and so clock rate) doesn't change.

No. But the Firefox text editing bug irritated me so much I couldn't deal with the radeon driver even if the performance was better.

---

### Post by cYbercOsmOnauT on 2013-11-21
fglrx 13.250 didn't compile correctly with the new Kernel 3.12.1. I am not a C coder but the error was a simple type error and everything looks like working fine after booting with the new kernel. I created a patch for others who have the same problem. After unpacking the patch file do the following
```
sudo mv kuid.patch /var/lib/dkms/fglrx/13.250/source
cd /var/lib/dkms/fglrx/13.250/source
sudo patch -p1 < kuid.patch
```
and if you already had 3.12.1 installed (with the compile error) do
```
sudo dpkg-reconfigure fglrx
```

---

### Post by cariboo on 2013-11-21
Seeing as Saucy has been released, it's time to start a new thread. Closed.

---

