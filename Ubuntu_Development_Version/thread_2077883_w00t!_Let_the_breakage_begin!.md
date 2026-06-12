---
title: "w00t! Let the breakage begin!"
date: 2012-10-29
forum: Ubuntu Development Version
---

### Post by VinDSL on 2012-10-29
First breakage in UbuRR... YaY!  :D

Installed these new packages via Synaptic (raring/main) @ 2:20AM local time.
```

Installed the following packages:
kmod (9-2ubuntu1)
libkmod2 (9-2ubuntu1)

```

Immediately afterward, I "tried" to install nVidia 304.60 (noobslab) but KMOD could not find some non-existant file.
```

WARNING: could not open /tmp/mkinitramfs blah, blah, blah, does not exist

``` 

Boom, Fail, Loser, Goodbye!  No nVidia drivers.

I just "tried" to remove kmod & libkmod2, but Synaptic wants to remove Unity et al. along with them. I'll pass...

Cannot modify anything kernel related, now -- anything that requires generating an initramfs.

First big time breakage in a while.  UbuRR is gonna be fun!  :guitar:

---

### Post by VinDSL on 2012-10-29
Doing a little forensics... kmod (9-2ubuntu1) & libkmod2 (9-2ubuntu1) were superseded almost immediately.

Must have flown in, under the wire, when I updated/upgraded from CLI, today...

```

vindsl@Zuul:~$ apt-cache policy kmod
kmod:
  Installed: 9-2ubuntu2
  Candidate: 9-2ubuntu2
  Version table:
 *** 9-2ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status

vindsl@Zuul:~$ apt-cache policy libkmod2
libkmod2:
  Installed: 9-2ubuntu2
  Candidate: 9-2ubuntu2
  Version table:
 *** 9-2ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status

vindsl@Zuul:~$ apt-cache policy module-init-tools
module-init-tools:
  Installed: 9-2ubuntu2
  Candidate: 9-2ubuntu2
  Version table:
 *** 9-2ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
     3.16-1ubuntu6 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main i386 Packages
vindsl@Zuul:~$ 

```

Note to devs:  KMOD still has issues!  Might want to move it back into "-proposed".  :D

But, wait... what's this "module-init-tools"?

Heh!  When I "tried" removing "module-init-tools", guess what?!?!?  It wanted to remove "kmod", but nothing else. 

```

Commit Log for Mon Oct 29 12:49:29 2012

Downgraded the following packages:
module-init-tools

Removed the following packages:
kmod

```

Score, Winner, Pinned, Yes!  :KS

I could care less about the KMOD library.  Let sleeping dogs lie, you know?

Just installed nVidia 304.51 (edgers) and it built just fine.  

nVidia 304.60 (noobslab) evidently hasn't been patched for Linux 3.6.3.

Anyway, looks like I cheated death, yet again.  Let's see if it survives a cold-boot...

**EDIT**

Number 5 Is Alive!

Bring on the breakage...

---

### Post by zika on 2012-10-29
Bitten by the same bug. But```
~$ apt-cache policy module-init-tools 
module-init-tools:
  Installed: 9-2ubuntu2
  Candidate: 9-2ubuntu2
  Version table:
 *** 9-2ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main amd64 Packages
        100 /var/lib/dpkg/status
```Nevertheless Your advice made me DL 3.16 and I'm back on track... Thank You...
```
echo "module-init-tools hold"|dpkg --set-selections
```
will keep it there until the storm is gone...

---

### Post by ventrical on 2012-10-29
I downloaded all those recent file upgrades/installs and there is nothing remarkable on THIS machine. However, I  am running the 3.7.xxRC2 kernel and 310.14 nVidia-current.

---

### Post by VinDSL on 2012-10-29
> **ventrical said:**
> I downloaded all those recent file upgrades/installs and there is nothing remarkable on THIS machine. However, I  am running the 3.7.xxRC2 kernel and 310.14 nVidia-current.If you're in a whimsical mood...

Purge nVidia 310.14, then re-install it.

That'll be the test...  ;)

---

### Post by zika on 2012-10-29
> **ventrical said:**
> I downloaded all those recent file upgrades/installs and there is nothing remarkable on THIS machine. However, I  am running the 3.7.xxRC2 kernel and 310.14 nVidia-current.You might have not noticed because it produces error but install ends without breakage. Try update-initramfs on Your kernel...

---

### Post by zika on 2012-10-29
> **VinDSL said:**
> If you're in a whimsical mood...

Purge nVidia 310.14, then re-install it.

That'll be the test...  ;)It's easier and safer to update-initramfs a kernel that is not necessary for every-day usage... ;)

---

### Post by VinDSL on 2012-10-29
> **zika said:**
> It's easier and safer to update-initramfs a kernel that is not necessary for every-day usage... ;)
Heh!  Pride goeth before destruction, you know?  :D

---

### Post by grahammechanical on 2012-10-29
This is also happening on Linux 3.5.0.17.

I just booted and trie3d to update. It failed due to a missing package header. I fixed that and upgraded in the terminal and got this:

> update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
cp: cannot stat `/lib/modprobe.d/*': No such file or directory
E: /usr/share/initramfs-tools/hooks/kmod failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.5.0-17-generic with 1.
dpkg: error processing initramfs-tools (--unpack):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

I opened synaptic and found that kmod and module-init-tools were tagged to be upgraded. Ran the upgrade and they are now at 9-2ubuntu2.

Safe to reboot? I will find out tomorrow.

---

### Post by VinDSL on 2012-10-29
> **grahammechanical said:**
> This is also happening on Linux 3.5.0.17 [...]

I opened synaptic and found that kmod and module-init-tools were tagged to be upgraded. Ran the upgrade and they are now at 9-2ubuntu2.

Safe to reboot? I will find out tomorrow.
Be sure to get a good night's sleep. LoL!  :D

Here's mine...

```

vindsl@Zuul:~$ apt-cache policy module-init-tools
module-init-tools:
  Installed: 3.16-1ubuntu6
  Candidate: 9-2ubuntu2
  Version table:
     9-2ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ raring/main i386 Packages
 *** 3.16-1ubuntu6 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main i386 Packages
        100 /var/lib/dpkg/status
vindsl@Zuul:~$ 

```

```

vindsl@Zuul:~$ sudo update-initramfs -u
[sudo] password for vindsl: 
update-initramfs: Generating /boot/initrd.img-3.6.3-030603-generic
vindsl@Zuul:~$ 

```

---

### Post by ventrical on 2012-10-29
> **VinDSL said:**
> If you're in a whimsical mood...

Purge nVidia 310.14, then re-install it.

That'll be the test...  ;)

Mamma mia!

```

dale@dale-desktop:~$ sudo apt-get remove nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  esound-common hal hal-info libaccess-bridge-java libaccess-bridge-java-jni
  libapt-inst1.4 libattica0.3 libaudiofile0 libaudiofile1 libbabl-0.0-0
  libboost-iostreams1.46.1 libboost-serialization1.49.0 libcamel-1.2-39
  libcelt0-0 libcmis-0.2-0 libebackend-1.2-2 libedata-book-1.2-13
  libedata-cal-1.2-15 libept1 libesd0 libfm-gtk1 libfm1 libgdata1.9-cil
  libgegl-0.0-0 libglew1.6 libglewmx1.6 libhal-storage1 libhal1 libllvm3.0
  libmagickcore3 libmagickcore3-extra libmagickcore4 libmagickcore4-extra
  libmagickwand3 libmagickwand4 libmcs1 libmusicbrainz3-6 libmusicbrainz4c2a
  libnepomukcore4 libnepomukdatamanagement4 libntfs10 libnux-2.0-0
  libnux-2.0-common libopenspc0 libpoppler19 libpoppler25 libpoppler27
  libreoffice-l10n-common librhythmbox-core5 librpmio2 libvpx0 libx264-116
  libx264-120 openoffice.org-common p7zip python-central python-gmenu
  unity-2d-common wine1.2 wine1.2-gecko
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  nvidia-current
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 107 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 1049099 files and directories currently installed.)
Removing nvidia-current ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
INFO:Disable nvidia-current
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Success
INFO:Unapplying quirk ThinkPad T420s
DEBUG:Removing /usr/share/X11/xorg.conf.d/10-nvidia-current-thinkpad-t420s.conf ...
DEBUG:Processing quirk Latitude E6530
DEBUG:Success
INFO:Unapplying quirk Latitude E6530
DEBUG:Removing /usr/share/X11/xorg.conf.d/10-nvidia-current-latitude-e6530.conf ...
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.7.0-030700rc2-generic
WARNING: could not open /tmp/mkinitramfs_3qLOHY/lib/modules/3.7.0-030700rc2-generic/modules.builtin: No such file or directory
dale@dale-desktop:~$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  esound-common hal hal-info libaccess-bridge-java libaccess-bridge-java-jni
  libapt-inst1.4 libattica0.3 libaudiofile0 libaudiofile1 libbabl-0.0-0
  libboost-iostreams1.46.1 libboost-serialization1.49.0 libcamel-1.2-39
  libcelt0-0 libcmis-0.2-0 libebackend-1.2-2 libedata-book-1.2-13
  libedata-cal-1.2-15 libept1 libesd0 libfm-gtk1 libfm1 libgdata1.9-cil
  libgegl-0.0-0 libglew1.6 libglewmx1.6 libhal-storage1 libhal1 libllvm3.0
  libmagickcore3 libmagickcore3-extra libmagickcore4 libmagickcore4-extra
  libmagickwand3 libmagickwand4 libmcs1 libmusicbrainz3-6 libmusicbrainz4c2a
  libnepomukcore4 libnepomukdatamanagement4 libntfs10 libnux-2.0-0
  libnux-2.0-common libopenspc0 libpoppler19 libpoppler25 libpoppler27
  libreoffice-l10n-common librhythmbox-core5 librpmio2 libvpx0 libx264-116
  libx264-120 openoffice.org-common p7zip python-central python-gmenu
  unity-2d-common wine1.2 wine1.2-gecko
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  nvidia-current
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/37.4 MB of archives.
After this operation, 107 MB of additional disk space will be used.
Selecting previously unselected package nvidia-current.
(Reading database ... 1048941 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_310.14-0ubuntu1~xedgers~quantal3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up nvidia-current (310.14-0ubuntu1~xedgers~quantal3) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: skip creation of /usr/lib32/libOpenCL.so because associated file /usr/lib32/nvidia-current/libOpenCL.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: using /usr/lib/nvidia-current/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Success
INFO:Applying quirk ThinkPad T420s
DEBUG:{'Files': {}, 'Vendor': {}, 'Monitor': {}, 'Screen': {0: ['\tIdentifier "My Screen"\n', '\tOption "RegistryDwords" "EnableBrightnessControl=1"\n']}, 'Module': {}, 'SubSection': {}, 'DRI': {}, 'InputDevice': {}, 'Extensions': {}, 'InputClass': {}, 'ServerLayout': {}, 'Device': {0: ['\tIdentifier "My Card"\n', '\tDriver "nvidia"\n', '\tOption "NoLogo" "True"\n']}, 'VideoAdaptor': {}, 'Comments': {}, 'ServerFlags': {}, 'Modes': {}}
DEBUG:Creating /usr/share/X11/xorg.conf.d/10-nvidia-current-thinkpad-t420s.conf
DEBUG:Processing quirk Latitude E6530
DEBUG:Success
INFO:Applying quirk Latitude E6530
DEBUG:{'Files': {}, 'Vendor': {}, 'Monitor': {}, 'Screen': {0: ['\tIdentifier "My Screen"\n', '\tOption "RegistryDwords" "EnableBrightnessControl=1"\n']}, 'Module': {}, 'SubSection': {}, 'DRI': {}, 'InputDevice': {}, 'Extensions': {}, 'InputClass': {}, 'ServerLayout': {}, 'Device': {0: ['\tIdentifier "My Card"\n', '\tDriver "nvidia"\n', '\tOption "NoLogo" "True"\n']}, 'VideoAdaptor': {}, 'Comments': {}, 'ServerFlags': {}, 'Modes': {}}
DEBUG:Creating /usr/share/X11/xorg.conf.d/10-nvidia-current-latitude-e6530.conf
Loading new nvidia-current-310.14 DKMS files...
Building only for 3.7.0-030700rc2-generic
Building for architecture i686
Building initial module for 3.7.0-030700rc2-generic
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.7.0-030700rc2-generic/updates/dkms/

depmod.....

DKMS: install completed.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.7.0-030700rc2-generic
WARNING: could not open /tmp/mkinitramfs_o3mMqu/lib/modules/3.7.0-030700rc2-generic/modules.builtin: No such file or directory
dale@dale-desktop:~$ 

```

ok.. and now re-boot!

I'll be back .. soon ?
 :)lol

---

### Post by ventrical on 2012-10-29
Actually it rebooted like a champ!

What did I not do wrong .. err or right ? :)

---

### Post by ventrical on 2012-10-29
btw .. I do have raring proposed repo enabled.

---

### Post by serdotlinecho on 2012-10-29
```
serdotlinecho@raring:~$ lsmod | grep nouveau
nouveau               823577  3 
ttm                    75534  1 nouveau
drm_kms_helper         45271  1 nouveau
drm                   230463  5 ttm,drm_kms_helper,nouveau
i2c_algo_bit           13197  1 nouveau
mxm_wmi                12859  1 nouveau
video                  18847  1 nouveau
wmi                    18590  2 mxm_wmi,nouveau
```sudo apt-get dist-upgrade...y....downloading...installing the updates....bla...bla...bla

> WARNING: could not open /tmp/mkinitramfs blah, blah, blah, does not existHaaaa?

```
serdotlinecho@raring:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
WARNING: could not open /tmp/mkinitramfs_PxSwSD/lib/modules/3.5.0-17-generic/modules.builtin: No such file or directory
```Version checking.

```
serdotlinecho@raring:~$ dpkg -l | egrep 'kmod|module-init-tools|nouveau'
ii  kmod                                      9-2ubuntu2                                  i386         tools for managing Linux kernel modules
ii  libdrm-nouveau1a:i386                     2.4.39-0ubuntu1                             i386         Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-nouveau2:i386                      2.4.39-0ubuntu1                             i386         Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libkmod2:i386                             9-2ubuntu2                                  i386         libkmod shared library
ii  module-init-tools                         9-2ubuntu2                                  all          transitional dummy package (module-init-tools to kmod)
ii  xserver-xorg-video-nouveau                1:1.0.2-0ubuntu3                            i386         X.Org X server -- Nouveau display driver
```Tried to remove kmod.

```
serdotlinecho@raring:~$ sudo apt-get remove kmod
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 adduser : Depends: passwd (>= 1:4.0.12) but it is not going to be installed
           Recommends: ecryptfs-utils (>= 67-1) but it is not going to be installed
 openssh-client : Depends: passwd but it is not going to be installed
 procps : Depends: initscripts but it is not going to be installed
 unity-webapps-common : Depends: unity-webapps-service (>= 2.3.8-0ubuntu3) but it is not going to be installed
 upstart : Depends: initscripts but it is not going to be installed
           Depends: mountall but it is not going to be installed
           Depends: ifupdown (>= 0.6.10ubuntu5)
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```Hmmm, reboot?

---

### Post by Harry33 on 2012-10-30
New module-init-tools (9-2ubuntu2) depends on two new packages:
- kmod
- libkmod2

The old module-init-tools (3.1.6-1ubuntu6) seems to have been split now.

Also note this:
> 
kmod (9-2ubuntu2) raring; urgency=low
 * Don't copy /lib/modprobe.d/* in our version of the kmod
   initramfs hook; we currently don't ship anything there.


---

### Post by zika on 2012-10-30
> **Harry33 said:**
> New module-init-tools (9-2ubuntu2) depends on two new packages:
- kmod2
- libkmod2

The old module-init-tools (3.1.6-1ubuntu6) seems to have been split now.

Also note this:Do tell us when the time comes to unlock module-init-tools... ;)

---

### Post by dino99 on 2012-10-30
hm, i cant find that kmod2 package, nor been used by module-init-tools.
but get the initramfs issue.

[https://bugs.launchpad.net/ubuntu/+source/kmod/+bug/1073062](https://bugs.launchpad.net/ubuntu/+source/kmod/+bug/1073062)

---

### Post by Harry33 on 2012-10-30
> **dino99 said:**
> hm, i cant find that kmod2 package, nor been used by module-init-tools.
but get the initramfs issue.

[https://bugs.launchpad.net/ubuntu/+source/kmod/+bug/1073062](https://bugs.launchpad.net/ubuntu/+source/kmod/+bug/1073062)

:P Sorry, I did mean kmod and libkmod2 packages.

---

### Post by Harry33 on 2012-10-30
The thread title should perhaps say something about kmod.

---

### Post by jerrylamos on 2012-10-30
At least 3 times today hung up solid mouse wouldn't move etc. etc. power cycle time.  So dead there wasn't even anything in /var/crash.

---

### Post by zika on 2012-10-31
New kmod came along. I bit the bullet.
```
echo "module-init-tools install"|dpkg --set-selections
```
unlocked module-init-tools. I crossed my fingers and did update-initramfs. Same warning appeared. I rebooted and I'm writing from new kernel images. So, that warning is not announcing obstruction...
Conclusion: there is a problem still in kmod but it is not fatal, at least I dodged a bullet this time...

---

### Post by jppr on 2012-10-31
I don´t have any Kmod promlems... I just did fresh QQ installation (without upgrade),  then I upgrade in the RR and system runs without any problems, and I use Proposed-updates :)

---

### Post by zika on 2012-10-31
> **jppr said:**
> I don´t have any Kmod promlems... I just did fresh QQ installation (without upgrade),  then I upgrade in the RR and system runs without any problems, and I use Proposed-updates :)What's new in raring-proposed?
```
  cpp-4.7 firefox firefox-globalmenu firefox-gnome-support g++-4.7 gcc-4.7
  gcc-4.7-base gstreamer1.0-plugins-base gstreamer1.0-x libgcc-4.7-dev libgcc1
  libgomp1 libgpod-common libgpod4 libgstreamer-plugins-base1.0-0 libitm1
  libnautilus-extension1a libquadmath0 libstdc++6 libstdc++6-4.7-dev nautilus
  nautilus-data nvidia-common thunderbird thunderbird-globalmenu
  thunderbird-gnome-support ubuntu-drivers-common
```...

---

### Post by VinDSL on 2012-10-31
> **zika said:**
> What's new in raring-proposed?
```
  cpp-4.7 firefox firefox-globalmenu firefox-gnome-support g++-4.7 gcc-4.7
  gcc-4.7-base gstreamer1.0-plugins-base gstreamer1.0-x libgcc-4.7-dev libgcc1
  libgomp1 libgpod-common libgpod4 libgstreamer-plugins-base1.0-0 libitm1
  libnautilus-extension1a libquadmath0 libstdc++6 libstdc++6-4.7-dev nautilus
  nautilus-data nvidia-common thunderbird thunderbird-globalmenu
  thunderbird-gnome-support ubuntu-drivers-common
```...
Exactly!  :D

KMOD is an upstream project.  They've been working on it for quite a while.

The problem is, someone at Canonical accepted it (before it was fully cooked) and moved it from proposed into main.

---

### Post by zika on 2012-10-31
> **VinDSL said:**
> Exactly!  :D

KMOD is an upstream project.  They've been working on it for quite a while.

The problem is, someone at Canonical accepted it (before it was fully cooked) and moved it from proposed into main.How raw are these (and other) packages in raring-proposed? What level of problems is to be expected if one would embark in using them...?

---

### Post by dino99 on 2012-10-31
"proposed" is now used to:
- avoid the "partial" updates when all the dependencies are not rebuilt/ready
- test the new versions on the devs side before sending them in the "wild"

The target is to lowering the useless report bugs as much as possible. But if you enable "proposed" then you get the previous ubuntu experience with the bleeding edge packages.

---

### Post by jppr on 2012-10-31
All new updates are Proposed-update [https://lists.ubuntu.com/archives/raring-changes/2012-October/thread.html](https://lists.ubuntu.com/archives/raring-changes/2012-October/thread.html)
Your own choise use you them or not... :popcorn:

---

### Post by zika on 2012-10-31
> **jppr said:**
> All new updates are Proposed-update [https://lists.ubuntu.com/archives/raring-changes/2012-October/thread.html](https://lists.ubuntu.com/archives/raring-changes/2012-October/thread.html)
Your own choise use you them or not... :popcorn:As it has been in previous more than a half-dozen testing cycles I've chosen to participate...

---

### Post by zika on 2012-11-05
```
Preparing to replace docbook-xml 4.5-7ubuntu1 (using .../docbook-xml_4.5-7.1_all.deb) ...
update-catalog: Suppressing action on super catalog. Invoking trigger instead.
update-catalog: Please rebuild the package being set up with a version of debhelper fixing #477751.

```...

---

### Post by VinDSL on 2012-11-05
Nautilus 3.4.2 finally broke, after the last update (an hour ago).

I've been nursing 3.4.2, until now, but all attempts to resuscitate it have failed.  :-({|=

So, Nautilus 3.7.1, it is...

---

### Post by Stinger on 2012-11-05
> **VinDSL said:**
> 

So, Nautilus 3.7.1, it is...


That'll be the day ! :biggrin:

---

### Post by VinDSL on 2012-11-05
> **Stinger said:**
> That'll be the day ! :biggrin:
Bwahahaha!  Yeah, I know...

Personally, I prefer to use PCManFM which, BTW, is still working just fine.  ;)

Anyway, Nautilus 3.4.2 is terminally broken, AFAIK.

---

### Post by mc4man on 2012-11-05
> **Stinger said:**
> That'll be the day ! :biggrin:

If you want it it's in the staging ppa (needs  glib/gtk from the testing ppa.
If you going the GS route in Ubuntu then the 3 ppa's will be your only 'easy' path
Atm no sense using 3.7+ gtk in a unity session, already breaks elements of light-themes 
(the latest glib breaks some unity indicators but that will be addressed I believe

---

### Post by ventrical on 2012-11-06
> **VinDSL said:**
> Bwahahaha!  Yeah, I know...

Personally, I prefer to use PCManFM which, BTW, is still working just fine.  ;)

Anyway, Nautilus 3.4.2 is terminally broken, AFAIK.

Same here .  Nautilus has become some sort of carbon copy ghost of itself. Oddly enough I can have them both running together.

---

### Post by VinDSL on 2012-11-06
> **ventrical said:**
> Same here .  Nautilus has become some sort of carbon copy ghost of itself. Oddly enough I can have them both running together.
Yep, you can run Nautilus & PCManFM side-by-side, both at the same time -- one with user privileges, the other in root auth -- and any other combination you can imagine.  They are very happy to coexist on the same desktop. 

The funny thing is, when Nautilus 3.4.2 was working, I often forgot which FM I was running.  They both worked equally well.  LoL!  :D

I used Nautilus 3.7.1 for a few hours, last night.  It worked okay, but you definitely have to go about things a different way -- using cut n' paste, instead of 'move" (which is a PITA now).  If 'they' would add "move to the other tab" instead of opening another instance of the browser, it would help, but I'm not holding my breath. 

I'm going to sorely miss the split pane mode, especially when I do file transfers between my local machine in Arizona, and remote server in Georgia.

Without the split pane(s), I really have no use for Nautilus, but I'll let it languish in the background, like a "ghost" walking the hallways of my PC.  ;)

---

### Post by Stinger on 2012-11-06
> **mc4man said:**
> If you want it it's in the staging ppa (needs  glib/gtk from the testing ppa.
If you going the GS route in Ubuntu then the 3 ppa's will be your only 'easy' path
Atm no sense using 3.7+ gtk in a unity session, already breaks elements of light-themes 
(the latest glib breaks some unity indicators but that will be addressed I believe
Well lucky me, I'm not using Unity ;)
and thanks for the info, Rico Tzschichholz is doing great, I hope it will land in the Gnome3 ppa or better yet in main (maybe I'm a bit too optimistic ? :rolleyes:)

---

