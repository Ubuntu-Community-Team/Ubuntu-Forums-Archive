---
title: "Can't install nvidia-319"
date: 2013-04-24
forum: Ubuntu Development Version
---

### Post by ryanvade on 2013-04-24
I am trying to install nvidia-319 for bumblebee 3.2. Apparently 319 is the only working driver for bumblebee 3.2. So I tried to install it. :
```
sudo apt-get install  nvidia-319 nvidia-settings-319
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-304 : Conflicts: xorg-driver-binary
 nvidia-319 : Conflicts: xorg-driver-binary
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

Can I just ignore the dependencies temporarily? Just to replace the current nvidia driver with 319?

---

### Post by QDR06VV9 on 2013-04-24
I had to use synaptic to make sense of it all.
But just choose nvidia-319-dev    and that should pull in nvidia-settings-319
If any other Nvidia Drivers are installed it will remove them.
I did not try "sudo apt-get install nvidia-319-dev && sudo apt-get install nvidia-settings-319"
So if you want to try that it might go smooth?

---

### Post by ajmcello on 2013-06-13
I have the same problem with 319. Suggestions? TIA

db1# apt-get install nvidia-319
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-304 : Conflicts: xorg-driver-binary
 nvidia-319 : Recommends: nvidia-settings-319 but it is not going to be installed
              Recommends: nvidia-persistenced but it is not installable
              Conflicts: xorg-driver-binary
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
db1# apt-get install nvidia-319-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-319-dev : Depends: nvidia-319 (>= 319.23) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


software-properties-gtk says:

db1> sudo software-properties-gtk
gpg: /tmp/tmpierrqy/trustdb.gpg: trustdb created
Warning: install transaction not completed successfully: Transaction failed: Package dependencies cannot be resolved
 The following packages have unmet dependencies:

nvidia-304: Depends: x11-common (>= 1:7.0.0) but 1:7.7+1ubuntu4 is to be installed
            Depends: libgcc1 (>= 1:4.1.1) but 1:4.8.1-3ubuntu1 is to be installed
            Depends: zlib1g (>= 1:1.1.4) but 1:1.2.8.dfsg-1ubuntu1 is to be installed
            Depends: xorg-video-abi-14 but it is not going to be installed
nvidia-319: Depends: x11-common (>= 1:7.0.0) but 1:7.7+1ubuntu4 is to be installed
            Depends: zlib1g (>= 1:1.1.4) but 1:1.2.8.dfsg-1ubuntu1 is to be installed
            Depends: xorg-video-abi-14 but it is not going to be installed

---

### Post by QDR06VV9 on 2013-06-13
> **ajmcello said:**
> I have the same problem with 319. Suggestions? TIA

db1# apt-get install nvidia-319
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-304 : Conflicts: xorg-driver-binary
 nvidia-319 : Recommends: nvidia-settings-319 but it is not going to be installed
              Recommends: nvidia-persistenced but it is not installable
              Conflicts: xorg-driver-binary
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
db1# apt-get install nvidia-319-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-319-dev : Depends: nvidia-319 (>= 319.23) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


software-properties-gtk says:

db1> sudo software-properties-gtk
gpg: /tmp/tmpierrqy/trustdb.gpg: trustdb created
Warning: install transaction not completed successfully: Transaction failed: Package dependencies cannot be resolved
 The following packages have unmet dependencies:

nvidia-304: Depends: x11-common (>= 1:7.0.0) but 1:7.7+1ubuntu4 is to be installed
            Depends: libgcc1 (>= 1:4.1.1) but 1:4.8.1-3ubuntu1 is to be installed
            Depends: zlib1g (>= 1:1.1.4) but 1:1.2.8.dfsg-1ubuntu1 is to be installed
            Depends: xorg-video-abi-14 but it is not going to be installed
nvidia-319: Depends: x11-common (>= 1:7.0.0) but 1:7.7+1ubuntu4 is to be installed
            Depends: zlib1g (>= 1:1.1.4) but 1:1.2.8.dfsg-1ubuntu1 is to be installed
            Depends: xorg-video-abi-14 but it is not going to be installed


Just to be sure, You are using raring (13.10)?
and make sure your fully updated
sudo apt-get update
sudo apt-get upgrade
If this is the case add these two lines to your  ?etc/apt/sources.list

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) raring main 
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) raring main 

sudo apt-get update
sudo apt-get install nvidia-319

I supect you are on saucy though.
regards

---

### Post by ajmcello on 2013-06-14
I am on saucy (13.10)

---

### Post by Harry33 on 2013-06-14
Please do remove nvidia-304 before attempting to install nvidia-319.
Only 1 driver should be installed.
The nvidia-319 in official saucy repo (restricted main) does not have any dependency issues in a pure saucy setup.

---

### Post by ajmcello on 2013-06-14
I've tried everything I can think of. Here's what I get now:


apt-get remove nvidia-304

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'nvidia-304' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 59 not upgraded.


apt-get install nvidia-319       
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-304 : Conflicts: xorg-driver-binary
 nvidia-319 : Recommends: nvidia-settings-319 but it is not going to be installed
              Conflicts: xorg-driver-binary
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

apt-get remove xorg-driver-binary
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'xorg-driver-binary' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 59 not upgraded.

---

### Post by ajmcello on 2013-06-14
software properties gtk still says this, even after I removed nvidia-304 and what not. Did a apt-get update, apt-get dist-upgrade, reboot. 

for nvidia-319:

 The following packages have unmet dependencies:

nvidia-304: Depends: x11-common (>= 1:7.0.0) but 1:7.7+1ubuntu4 is to be installed
            Depends: libgcc1 (>= 1:4.1.1) but 1:4.8.1-3ubuntu1 is to be installed
            Depends: zlib1g (>= 1:1.1.4) but 1:1.2.8.dfsg-1ubuntu1 is to be installed
            Depends: xorg-video-abi-14 but it is not going to be installed
nvidia-319: Depends: x11-common (>= 1:7.0.0) but 1:7.7+1ubuntu4 is to be installed
            Depends: zlib1g (>= 1:1.1.4) but 1:1.2.8.dfsg-1ubuntu1 is to be installed
            Depends: xorg-video-abi-14 but it is not going to be installed

---

### Post by cariboo on 2013-06-14
@ajmcello what command did you use to remove the 304 driver, and did you reboot to make sure you were using the nouveau driver after removing the closed source Nvidia driver?

---

### Post by ajmcello on 2013-06-14
I use apt-get. Whatever I try, it fails when trying to use 319.

aptitude search '~i?provides(xorg-driver-binary)'         
i A nvidia-304-updates                                                      - NVIDIA binary Xorg driver, kernel module and VDPAU library                       


apt-get install nvidia-319                                
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-304 : Conflicts: xorg-driver-binary
 nvidia-319 : Recommends: nvidia-settings-319 but it is not going to be installed
              Conflicts: xorg-driver-binary
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.




I've tried removing 304, and it installs 310, I remove 310 and it installs 304, all automaticly.

aptitude search nouveau  

i   libdrm-nouveau1a                                                        - Userspace interface to nouveau-specific kernel DRM services -- runtime           
p   libdrm-nouveau1a:i386                                                   - Userspace interface to nouveau-specific kernel DRM services -- runtime           
i   libdrm-nouveau1a-dbg                                                    - Userspace interface to nouveau-specific kernel DRM -- debugging symbols          
p   libdrm-nouveau1a-dbg:i386                                               - Userspace interface to nouveau-specific kernel DRM -- debugging symbols          
i   libdrm-nouveau2                                                         - Userspace interface to nouveau-specific kernel DRM services -- runtime           
i   libdrm-nouveau2:i386                                                    - Userspace interface to nouveau-specific kernel DRM services -- runtime           
p   libdrm-nouveau2-dbg                                                     - Userspace interface to nouveau-specific kernel DRM -- debugging symbols          
p   libdrm-nouveau2-dbg:i386                                                - Userspace interface to nouveau-specific kernel DRM -- debugging symbols          
i   nouveau-firmware                                                        - Firmware for nVidia graphics cards                                               
i   xserver-xorg-video-nouveau                                              - X.Org X server -- Nouveau display driver                                         
p   xserver-xorg-video-nouveau:i386                                         - X.Org X server -- Nouveau display driver                                         
i   xserver-xorg-video-nouveau-dbg                                          - X.Org X server -- Nouveau display driver (debug symbols)                         
p   xserver-xorg-video-nouveau-dbg:i386                                     - X.Org X server -- Nouveau display driver (debug symbols)

---

### Post by cariboo on 2013-06-14
If you use:

```
sudo apt-get purge nvidia-304
```

that should remove the driver without installing another driver, unless you removed nouveau too.

---

### Post by ajmcello on 2013-06-15
I purged nvidia-304. Can't purge 304-updates. Still can't install nvidia-319 no matter what, says it has a conflict with the xorg driver binary
 
 aptitude search '~i?provides(xorg-driver-binary)' 
i A nvidia-304-updates              - NVIDIA binary Xorg driver, kernel module a

apt-get purge nvidia-304-updates

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-image-extra-3.9.0-4-generic
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  nvidia-304 nvidia-current nvidia-settings-304
The following packages will be REMOVED:
  nvidia-304-updates* nvidia-current-updates* nvidia-settings-319*
The following NEW packages will be installed:
  nvidia-304 nvidia-current nvidia-settings-304
0 upgraded, 3 newly installed, 3 to remove and 3 not upgraded.
Need to get 1,823 kB/69.9 MB of archives.
After this operation, 325 kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

---

### Post by pqwoerituytrueiwoq on 2013-06-15
Installed it on a clean install made with the June 15th daily disk image of xubuntu
[[IMG]http://i.imgur.com/ZKonInrs.png[/IMG]]("http://i.imgur.com/ZKonInr.png")
has anyone tried deleting [FONT=courier new]/etc/X11/xorg.conf[/FONT]?

---

### Post by xeizo on 2013-06-15
There is an updated version of 319.23 in the repos now, which installs against kernel 3.10. No need for xorg-edgers anymore if running the latest kernel.  Sadly, moving from Gallium to Nvidia under Kernel 3.10  killed Unity and Gnome Classic, but strange enough so does Gnome-Shell work fine. One wouldn't think of Gnome-Shell as a fallback desktop, but in this case it is ... important to keep Nautilus 3.6.3 though as the desktop itself is destroyed when using a newer Nautilus.  Gallium works fine with all of the above, but it can't run games properly, using the Linux-port of Portal as a test. Changing to Nvidia, while breaking a lot of the desktop stuff except Gnome-Shell, indeed makes it possible to run Portal properly!  Ubuntu 13.10 is in a VERY buggy state right now, I don't think 13.04 ever was this buggy during it's release-cycle, but it's still Alpha so things will/must improve a lot  :-)  Btw, running yesterdays build of Ubuntu fully updated and extended with ubuntu-gnome-desktop, yesterdays build of Ubuntu Gnome was too buggy to use but the normal Ubuntu was usable enough to have as a base install.

---

### Post by dino99 on 2013-06-15
nothing buggy here on i386, even with nautilus 3.9.0  :P

---

### Post by xeizo on 2013-06-15
> **dino99 said:**
> nothing buggy here on i386, even with nautilus 3.9.0  :P  Well, I run 64-bit and it seems rather common for things to be fixed later in 64-bit which is strange since all desktop/laptop-processors have been 64-bit for nearly ten years ...  Otherwise, the Nautilus-problem seems like a known bug, you can't have normal desktop-functionality in Gnome-Shell with anything later than 3.6.3. Usually it manifests itself in a pure white desktop. Of course one can turn the functionality off and have all the screen estate being filled with just a pretty wallpaper, much like in KDE, in that case later Nautilus-versions will do.  Anyway, Linux is in much need of a SOLID desktop, which seems just like a wish at the moment. Even Microsoft is struggling GUI-wise with its Windows 8-debacle ....

---

### Post by QDR06VV9 on 2013-06-15
Anyway, Linux is in much need of a SOLID desktop, which seems just like a wish at the moment. Even Microsoft is struggling GUI-wise with its Windows 8-debacle ....[/QUOTE]
 +1
But keep in mind saucy is in Development..

---

### Post by ajmcello on 2013-06-15
> **xeizo said:**
> There is an updated version of 319.23 in the repos now, which installs against kernel 3.10. No need for xorg-edgers anymore if running the latest kernel.  Sadly, moving from Gallium to Nvidia under Kernel 3.10  killed Unity and Gnome Classic, but strange enough so does Gnome-Shell work fine. One wouldn't think of Gnome-Shell as a fallback desktop, but in this case it is ... important to keep Nautilus 3.6.3 though as the desktop itself is destroyed when using a newer Nautilus.  Gallium works fine with all of the above, but it can't run games properly, using the Linux-port of Portal as a test. Changing to Nvidia, while breaking a lot of the desktop stuff except Gnome-Shell, indeed makes it possible to run Portal properly!  Ubuntu 13.10 is in a VERY buggy state right now, I don't think 13.04 ever was this buggy during it's release-cycle, but it's still Alpha so things will/must improve a lot  :-)  Btw, running yesterdays build of Ubuntu fully updated and extended with ubuntu-gnome-desktop, yesterdays build of Ubuntu Gnome was too buggy to use but the normal Ubuntu was usable enough to have as a base install.

What repo do I need for 3.10?

I am completely current as of this post with saucy sisters.

uname -a
Linux db1 3.9.0-6-generic #13-Ubuntu SMP Fri Jun 14 15:47:09 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by xeizo on 2013-06-15
> **ajmcello said:**
> What repo do I need for 3.10?  I am completely current as of this post with saucy sisters.  uname -a Linux db1 3.9.0-6-generic #13-Ubuntu SMP Fri Jun 14 15:47:09 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux  There's no PPA for 3.10, but it can be downloaded manually here:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)  It will install against the latest Nvidia-blob which IS in the normal repos, install it so:  Download headers, headers-all and the kernel, put them in a directory and issue the following on the command-line when standing in the same directory:  sudo dpkg -i linux*.deb

---

### Post by ajmcello on 2013-06-15
Thanks, I finally got 319 installed. I had to break the system (interupt apt-get remove after it removed nvidia-310 or 304), and install 319 manually by downloading the package.

During the process, the following held me back, so I removed them:

libcublas5.0
libcudart5.0
libcufft5.0
libcuinj64-5.0
libcupti5.0
libcupti-dev
libcurand5.0
libcusparse5.0
libnpp5.0
libnvtoolsext5.0
libthrust-dev
libvdpau-dev
nvidia-cuda-dev
nvidia-cuda-toolkit
nvidia-opencl-dev
nvidia-profiler
nvidia-visual-profiler
opencl-headers

Good to go with nvidia-319 and nvidia-319-dev and kernel 3.10

> **xeizo said:**
> There's no PPA for 3.10, but it can be downloaded manually here:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)  It will install against the latest Nvidia-blob which IS in the normal repos, install it so:  Download headers, headers-all and the kernel, put them in a directory and issue the following on the command-line when standing in the same directory:  sudo dpkg -i linux*.deb

---

### Post by pqwoerituytrueiwoq on 2013-06-15
> **xeizo said:**
> There's no PPA for 3.10, but it can be downloaded manually here:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)
while there is no ppa there is a way to autodetect updates and get notifyed about them
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme)

---

