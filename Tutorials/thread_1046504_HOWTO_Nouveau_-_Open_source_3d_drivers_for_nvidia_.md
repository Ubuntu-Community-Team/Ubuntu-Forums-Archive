---
title: "HOWTO: Nouveau - Open source 3d drivers for nvidia graphic cards"
date: 2009-01-21
forum: Tutorials
---

### Post by Hakimio on 2009-01-21
[SIZE="4"]_HOWTO: Nouveau - Open source 3d drivers for nvidia graphic cards_[/SIZE]
[SIZE="2"]_[COLOR="Red"]Updated 2011-10-18[/COLOR]_[/SIZE]
[SIZE="2"]_[COLOR="Red"]Ubuntu 10.04 or later required[/COLOR]_[/SIZE]

[SIZE="3"]**Intro**[/SIZE]

Nouveau is a project which aims at producing Open Source 3D drivers for nVidia cards. In this tutorial I would like to explain how to compile and install latest version of nouveau drivers.
You can find nouveau developement news and chat with other nouveau users at [phoronix](http://www.phoronix.com/forums/forumdisplay.php?f=45).

This guide is meant for people who would like to test the latest nouveau **3D** drivers (if you are interested only in 2D driver, it would be safer to just use stable drivers that can be installed from ubuntu repository or install the latest version from [xorg-edgers ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)). As these drivers are not considered 100% stable yet, this guide is targeted at advanced users.

To have a better vision of what to expect from nouveau drivers take a look at [feature matrix](http://nouveau.freedesktop.org/wiki/FeatureMatrix) (some nvidia chip code names can be found [here](http://nouveau.freedesktop.org/wiki/CodeNames). Also "lspci | grep VGA" can be used to find out the codename).

[SIZE="3"]**Part A: Removing nvidia drivers**[/SIZE]
[LIST=1]
[*]Uninstall it
[LIST]
[*]If you installed the drivers using ubuntu official repository:
```
sudo apt-get --purge remove nvidia-glx-* nvidia-settings
```
[*]If you used nvidia installer from nvidia website(replace VERSION with nvidia driver version!):
```
sudo sh NVIDIA-Linux-x86-VERSION-pkg1.run --uninstall
```
[/LIST]
[*]Save all the important things you were working on, switch to virtual console by pressing by pressing Ctrl+Alt+F1 (you can switch back by pressing Ctrl+Alt+F7), login and stop gnome display manager
```
sudo service gdm stop
```
[*]Run the following command to generate xorg.conf file
```
sudo Xorg -configure
```
[*]Copy the generated file to /etc/X11
```
sudo cp xorg.conf /etc/X11
```
[*]Open the file with nano editor
```
sudo nano /etc/X11/xorg.conf
```
[*]Search for *Driver "nvidia"* line in Device section (editor's search functionality can be activated by pressing Ctrl+W) and if you can find it replace it with *Driver "nouveau"* and press Ctrl+O and Ctrl+X to save and exit. 
[*]Restart computer.
```
sudo reboot
```
[/LIST]

[SIZE="3"]**Part B: Installing DRM kernel modules**[/SIZE]

[LIST=1]
[*]First of all, to compile latest DRM modules kernel version requirements should be fulfilled. Take a look at [this Makefile](http://cgit.freedesktop.org/nouveau/linux-2.6/tree/Makefile)(first 3 lines) to find out the required kernel version (for example, if it states "VERSION = 3", "PATCHLEVEL = 1" & "SUBLEVEL = 0" kernel version 3.1.0 is required).
[*]Once you know the required kernel version, download needed packages depending on your architecture (32bit or 64bit) (you can find your architecture by running *uname -m* - if it replies i686, you are running 32bit ubuntu, otherwise if it says x86_64, you are running 64bit version) from [this page](http://kernel.ubuntu.com/~kernel-ppa/mainline/):
[LIST]
[*]32bit:
[LIST=1]
[*]linux-headers-***_i386.deb
[*]linux-headers-***_all.deb
[*]linux-image-***_i386.deb
[/LIST]
[*]64bit:
[LIST=1]
[*]linux-headers-***_amd64.deb
[*]linux-headers-***_all.deb
[*]linux-image-***_amd64.deb
[/LIST]
[/LIST]
[*]After installing the kernel restart to boot the newly installed kernel
[*]Now we have two options
[LIST] 
[*]to clone whole nouveau kernel repository which takes really a lot of time even with high speed i-net connection and requires git installation (--depth 1 is used to avoid downloading history)
```
sudo apt-get install git-core
git clone --depth 1 git://anongit.freedesktop.org/nouveau/linux-2.6 master
```
[*]or just download daily snapshot which should be pretty fast
```
wget http://people.freedesktop.org/~pq/nouveau-drm/master.tar.gz
```
[/LIST]
[*]If you downloaded the daily snapshot, you can use the following command to unpack it, otherwise just skip to next step
```
tar -xzvf master.tar.gz
```
[*]Enter master/drivers/gpu/drm/nouveau directory
```
cd master/drivers/gpu/drm/nouveau
```
[*]Exchange Makefile in the directory with one that will be used to compile the modules
```
mv Makefile Makefile.orig 
wget -O Makefile "http://cgit.freedesktop.org/nouveau/linux-2.6/plain/nouveau/Makefile?h=master-compat"
```
[*]Compile the modules
```
NOUVEAUROOTDIR=../../../.. make
```
[*]Install them
```
sudo make install NOUVEAUROOTDIR=../../../..
```
[*]Go back to the directory you downloaded the source code
```
cd ../../../../..
```
[/LIST]

[SIZE="3"]**Part C: Installing libdrm**[/SIZE]
[LIST=1]
[*]Dependency installation
```
sudo apt-get install git-core autoconf libtool libpthread-stubs0-dev libpciaccess-dev
```
[*]Download libdrm sources
```
git clone git://anongit.freedesktop.org/git/mesa/drm/
```
[*]Enter drm directory
```
cd drm
```
[*]Run autogeneration and configuration scripts with some flags (libdir flag is used because libdrm is installed in none standard directory in ubuntu)
```
./autogen.sh --enable-nouveau-experimental-api --prefix=/usr --libdir=/lib --disable-intel --disable-radeon
```
[*]Compile the library
```
make
```
[*]Install it
```
sudo make install
```
[*]Return to parent directory
```
cd ..
```
[/LIST]

[SIZE="3"]**Part D: 2D driver installation**[/SIZE]
[LIST=1]
[*]Dependency installation
```
sudo apt-get install xorg-dev xutils-dev
```
[*]Download the sources
```
git clone --depth 1 git://anongit.freedesktop.org/nouveau/xf86-video-nouveau
```
[*]Enter the source directory
```
cd xf86-video-nouveau
```
[*]Run autogeneration and configuration scripts
```
./autogen.sh PKG_CONFIG_PATH=/lib/pkgconfig
```
[*]Compile the drivers
```
make
```
[*]Copy the driver to /usr/lib/xorg/modules/drivers directory
```
sudo cp src/.libs/nouveau_drv.so /usr/lib/xorg/modules/drivers
```
[*]Let's tell to the system about new libraries
```
sudo ldconfig
```
[*]Back to parent directory
```
cd ..
```
[/LIST]

[SIZE="3"]**Part E: 3D driver installation**[/SIZE]
[LIST=1]
[*]More dependencies
```
sudo apt-get install g++ libtalloc-dev bison flex
```
[*]Acquire the sources
```
git clone git://anongit.freedesktop.org/git/mesa/mesa
```
[*]Enter mesa directory
```
cd mesa
```
[*]Run autogeneration and configuration scripts
```
./autogen.sh --enable-glx-tls --disable-asm --with-dri-drivers= --with-gallium-drivers=swrast,nouveau --enable-texture-float --disable-asm --enable-opengl --disable-gles2 --disable-openvg --enable-dri --enable-glx --enable-xvmc --disable-va --disable-vdpau --disable-osmesa --disable-egl --disable-xorg --disable-d3d1x --disable-xa --disable-gbm --disable-xlib-glx --disable-gallium-egl --disable-gallium-gbm --disable-gallium-llvm --disable-xcb --enable-driglx-direct --enable-glx-tls --enable-glu PKG_CONFIG_PATH=/lib/pkgconfig
```
[*]Compile the driver
```
make PKG_CONFIG_PATH=/lib/pkgconfig
```
[*]Copy the required file to /usr/lib and make a link in /usr/lib/dri
```
sudo cp lib/gallium/nouveau_dri.so /usr/lib
sudo ln -s /usr/lib/nouveau_dri.so /usr/lib/dri/nouveau_dri.so
```
If after running "sudo ln -s /usr/lib/nouveau_dri.so /usr/lib/dri/nouveau_dri.so" you get an error saying "No such file or directory" create "dri" folder inside "/usr/lib" and try again:
```
sudo mkdir /usr/lib/dri
sudo ln -s /usr/lib/nouveau_dri.so /usr/lib/dri/nouveau_dri.so
```
[*]Tell to the system about new libraries
```
sudo ldconfig
```
[*]Because in this tutorial we replaced nouveau 2D drivers that come with Ubuntu, we'll need to take additional step to make sure that the drivers we just installed are not overwritten by the ones provided by ubuntu during software update. We'll have to lock driver version with apt-get and synaptic:
[LIST=1]
[*]Run the following commands (to unlock package version replace "hold" with "install")
```
echo libdrm-nouveau1 hold | sudo dpkg --set-selections
echo xserver-xorg-video-nouveau hold | sudo dpkg --set-selections
echo libdrm2 hold | sudo dpkg --set-selections
```
[*]Use instructions in [this ubuntu help tutorial](https://help.ubuntu.com/community/PinningHowto#Synaptic) to lock libdrm-nouveau1, xserver-xorg-video-nouveau and libdrm2 package versions.
[/LIST]
[*]That's it. Now you can restart your pc to see if the drivers work (If something goes wrong, don't panic - just take a look at "If graphical environment doesn't start" section in Appendix). You can check if the 3D driver loaded correctly by taking a look at /var/log/Xorg.0.log
```
grep nouveau_dri /var/log/Xorg.0.log
```
the output should be something similar to:
```
[  1639.620] (II) AIGLX: Loaded and initialized /usr/lib/dri/nouveau_dri.so
```
[/LIST]

[SIZE="3"]**Appendix: If graphical environment doesn't start**[/SIZE]
[LIST=1]
[*]This step is only needed if you are on wireless network and can only connect to internet when network manager applet is running. In that case you'll have to boot up ubuntu live cd and download the following deb packages for ubuntu version and architecture you have installed:
[LIST=1]
[*][libdrm-nouveau1](http://packages.ubuntu.com/maverick/libdrm-nouveau1)
[*][xserver-xorg-video-nouveau](http://packages.ubuntu.com/maverick/libdrm2)
[*][libdrm2](http://packages.ubuntu.com/maverick/libdrm2)
[/LIST]
[*]Boot up to recovery mode of the official ubuntu kernel
[*] Unlock package versions which contents we have overwritten
```
echo libdrm-nouveau1 install | sudo dpkg --set-selections
echo xserver-xorg-video-nouveau install | sudo dpkg --set-selections
echo libdrm2 install | sudo dpkg --set-selections

```
[*]Now depending if you have downloaded the deb packages or will just be using apt-get run the following commands:
[LIST]
[*]deb package installation (replace '/directory/with deb packages' with the real path):
```
cd '/directory/with deb packages'
sudo dpkg -i *.deb
```
[*]apt-get:
```
sudo apt-get install --reinstall libdrm-nouveau1 xserver-xorg-video-nouveau libdrm2
```
[/LIST]
[*]Reboot
```
sudo reboot
```
[*]Select kernel that is provided by ubuntu developers
[*]Finally you can remove kernel packages you have installed when following this guide
[/LIST]

[SIZE="3"]**Resources**[/SIZE]
[Install Nouveau](http://nouveau.freedesktop.org/wiki/InstallNouveau)
[Gallium3D How to](http://nouveau.freedesktop.org/wiki/GalliumHowto)
[Nouveau FAQ](http://nouveau.freedesktop.org/wiki/FAQ)

---

### Post by TSJason on 2009-03-13
Thanks for compiling this. It's fun playing with new code. I actually have it working half decent on jaunty.

---

### Post by floogy on 2009-03-14
When these drivers will be stable, would this then enable future Xen Dom0 to use more then 800x600 px resolution when using nvidia cards?

---

### Post by Hakimio on 2009-03-14
> **TSJason said:**
> Thanks for compiling this. It's fun playing with new code. I actually have it working half decent on jaunty.
Nice to see that it was helpful to you :) 
Just curious: did you try the 3d driver or just the 2d. If 3d, what VGA you have and how was the overall experience? Did you try running some 3d apps?
> **floogy said:**
> When these drivers will be stable, would this then enable future Xen Dom0 to use more then 800x600 px resolution when using nvidia cards?
[QUOTE=Nouveau FAQ]It really is not easy to predict any dates, as showstoppers may appear anytime. Very few, usually none, of the developers are paid to work on Nouveau, so all progress depends on their free time and interests.[/quote]
Don't know anything about Xen issues though.

---

### Post by floogy on 2009-03-14
I asked that, because Xen-Kernels and nvidia-modules have to be patched to work together. But I read that these patches are using workarounds like IGNORE_XEN_PRESENCE=1. Therefor these so called solutions are very unstable or unuseable. Some people reported system halt and crashes all 3 or 5 hours.
[http://www.nvnews.net/vbulletin/showthread.php?t=122900](http://www.nvnews.net/vbulletin/showthread.php?t=122900)
[http://www.meinews.net/nvidia-t266401.html](http://www.meinews.net/nvidia-t266401.html) (sorry, german)

I'm not able to get useful resolutions with the nv driver at all.

I got a GeForce 6600 GT, and tested yesterday the ppa nouveau packages from launchpad for hardy, but that didn't work either. 
```
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2) (prog-if 00 [VGA controller])
```

Also I wasn't able to set up the nouveau driver to get X running. Started by startx I got a blank black screen and couldn't go back to any tty so I must reset the computer and reboot. With gdm it failed too, but offered the failsafe vesa configuration tool (failsafeDexconf).

[http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages)
[https://launchpad.net/~raof/+archive/ppa](https://launchpad.net/~raof/+archive/ppa)

xorg.conf nv and nouveau:
[http://paste.pocoo.org/show/107880/](http://paste.pocoo.org/show/107880/)

Xorg.0.log nouveau:
[http://paste.pocoo.org/show/107881/](http://paste.pocoo.org/show/107881/)
There was no backtrace: output. That's the EOF.
```
# egrep '(\(EE|\(WW|\(!!)' /var/log/Xorg.0.log.nouveau_1	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) NOUVEAU(0): Bad V_BIOS checksum
(EE) NOUVEAU(0): wrong DRM version
(EE) NOUVEAU(0): DRI pre-initialisation failed.  Setting NoAccel
(!!) NOUVEAU(0): ... BIOS signature not found
(!!) NOUVEAU(0): Raw DCB entry 0: 01000300 00000028
(!!) NOUVEAU(0): Raw DCB entry 1: 04010312 00000000
(!!) NOUVEAU(0): Raw DCB entry 2: 04010310 00000028
(!!) NOUVEAU(0): Raw DCB entry 3: 02020321 0000c080
(WW) NOUVEAU(0): Failed to set up write-combining range (0xc000001a,0x1)
(WW) NOUVEAU(0): Failed to set up write-combining range (0xc0000018,0x3)
(WW) NOUVEAU(0): Failed to set up write-combining range (0xc0000010,0xb)
(WW) NOUVEAU(0): Failed to set up write-combining range (0xc0000000,0x1b)
(WW) Configured Mouse: No Device specified, looking for one...
```

I guess the problem is the wrong drm version in the ppa repo:
 (EE) NOUVEAU(0): wrong DRM version

```
libdrm2:
  Installed: 2.4.1+git20090212-0~ppa1~hardy
  Candidate: 2.4.1+git20090212-0~ppa1~hardy
  Version table:
 *** 2.4.1+git20090212-0~ppa1~hardy 0
        500 http://ppa.launchpad.net hardy/main Packages
        100 /var/lib/dpkg/status
     2.3.0-4ubuntu1 0
        500 http://de.archive.ubuntu.com hardy/main Packages
        500 http://archive.ubuntu.com hardy/main Packages
```

Unfortunatly I got svere problems with my package sytem yesterday when removing nouveau packages and downgrading libdrm2 to hardy back again I wasn't no more able to reinstall the removed nvidia-glx-new because of dpkg-diversion conflicts with the old traces of nvidia-glx.

The diversion problem was somewhat complex:
[http://paste.pocoo.org/show/107883/](http://paste.pocoo.org/show/107883/)

Now I got the propritary binary driver running again.

---

### Post by Hakimio on 2009-03-14
> **floogy said:**
> I guess the problem is the wrong drm version in the ppa repo:
 (EE) NOUVEAU(0): wrong DRM version
Instead of using precompiled packages, try installing the latest 2d driver using my guide.

---

### Post by tonyturbo23 on 2009-04-14
Great Guide.

I got to step 17. Then I get this msg. 

checking for LIBDRM_NOUVEAU... configure: error: Package requirements (libdrm_nouveau) were not met:

No package 'libdrm_nouveau' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBDRM_NOUVEAU_CFLAGS
and LIBDRM_NOUVEAU_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I'm a complete noob so any help would be greatly appreciated.

Cheers,

---

### Post by Hakimio on 2009-04-15
> **tonyturbo23 said:**
> Great Guide.

I got to step 17. Then I get this msg. 

checking for LIBDRM_NOUVEAU... configure: error: Package requirements (libdrm_nouveau) were not met:

No package 'libdrm_nouveau' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBDRM_NOUVEAU_CFLAGS
and LIBDRM_NOUVEAU_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I'm a complete noob so any help would be greatly appreciated.

Cheers,
Please try to CAREFULLY follow steps 1-6 in part B. It seems that you ever skipped some step or drm compilation/installation was unseccessful. If that doesn't help, please report and I'll check if the guide needs to be updated.

---

### Post by ashmew2 on 2009-04-15
Seeing Nouveau in action will be a delight to the eyes once its final version is released.. :guitar:

---

### Post by tonyturbo23 on 2009-04-15
After step 4, I got this error

libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
configure.ac:24: installing `./missing'
tests/Makefile.am: installing `./depcomp'
configure.ac:130: required file `libdrm/intel/Makefile.in' not found
configure.ac:130: required file `libdrm/nouveau/Makefile.in' not found
configure.ac:130: required file `libdrm/nouveau/libdrm_nouveau.pc.in' not found
autoreconf: automake failed with exit status: 1[/I]

I might just downgrade to 8.04 and hope that my nvidia card works with that.

---

### Post by Hakimio on 2009-04-16
> **tonyturbo23 said:**
> After step 4, I got this error

libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
configure.ac:24: installing `./missing'
tests/Makefile.am: installing `./depcomp'
configure.ac:130: required file `libdrm/intel/Makefile.in' not found
configure.ac:130: required file `libdrm/nouveau/Makefile.in' not found
configure.ac:130: required file `libdrm/nouveau/libdrm_nouveau.pc.in' not found
autoreconf: automake failed with exit status: 1[/I]

I might just downgrade to 8.04 and hope that my nvidia card works with that.
Ubuntu version shouldn't be an issue. I use 8.10 here too. Anyway, just tried to run autogen here and there were no problems, but instead of "**tests**/Makefile.am: installing `./depcomp'" I get "**libdrm**/Makefile.am: installing `./depcomp'".
It seems either you are doing sth wrong or there were some problems with their scripts which they recently fixed. Please run 
```
git pull
```
in the drm directory, rerun autogen script and, if you still get any errors, copy entire autogen output to pastebin.com and drop here a link.

---

### Post by Jenkins1 on 2009-06-30
Hi,

I get the below error when doing ./autogen.sh (stage 4) in the first post.


configure: WARNING: unrecognized options: --enable-maintainer-mode

any ideas?

---

### Post by Jenkins1 on 2009-07-01
I have managed to install the driver but I can't configure two separate x sessions. One for my laptop screen and one for external screen. How can I do this my current xorg.conf is attached

---

### Post by Hakimio on 2009-07-02
> **Jenkins1 said:**
> I have managed to install the driver but I can't configure two separate x sessions. One for my laptop screen and one for external screen. How can I do this my current xorg.conf is attached
Have you tried following [this](http://en.gentoo-wiki.com/wiki/X.Org/Dual_Monitors#XRandR_1.2_Specification) guide? If you have, could you also post your Xorg.0.log (/var/log)?

---

### Post by Jenkins1 on 2009-08-02
I have successfully configured my external screen and I can make it rotate independently from my laptop screen. How ever only when the screen is rotated the refresh rate is to slow. You can actually see the screen updating across from left to right. The screen will work in portrait mode with the nvidia driver. But independent rotation can only be achieved with nouvea. my xorg is attached.

Many thanks

---

### Post by dinxter on 2009-09-29
great guide kakimio :) just to note, gallium3d is now merged (as of 17th july 2009) and developed in mainline (as i understand it) so no need to checkout a gallium branch. its not built by default on karmic but adding --enable-gallium-nouveau to configure should do it. i'll see about some sort of very-likely-to-break packaging

---

### Post by dinxter on 2009-09-29
oh, and building kenel modules in the drm tree (drm/linux-core) will no longer work. nouveau driver work is now in a kernel branch 
git://anongit.freedesktop.org/git/nouveau/linux-2.6 
be warned, its a very very big branch!

---

### Post by Hakimio on 2009-09-29
Thanks, **dinxter**

Most likely I'll update the guide just after the ubuntu 9.10 final release.

---

### Post by dinxter on 2009-09-29
> **Hakimio said:**
> Thanks, **dinxter**

Most likely I'll update the guide just after the ubuntu 9.10 final release.
probably best to wait til then, theres been a few changes.
updating the packages in karmic using git is easy enough (with the help of a well written howto :) ), i'm just trying to fiddle with the gallium enabled mesa git package to get gallium up and running, to the best of its current abilities. we'll see how it goes :) i'll add gallium support to the drm/xorg/driver ppa below once i get it sorted
[https://launchpad.net/~sevenmachines/+archive/nouveau]("https://launchpad.net/%7Esevenmachines/+archive/nouveau")

---

### Post by Phonic_P on 2009-12-31
Hi and thanks for this guide.
I have been having issues with resolution on ALL Ubuntu & Kubuntu with the Nvidia driver (96) and decided to give Nouveau a go. I had received advice from the kubuntu forum [http://kubuntuforums.net/forums/index.php?topic=3109198.0]("http://kubuntuforums.net/forums/index.php?topic=3109198.0") and was advised to check this guide.
In doing so everything went great till step 5 for 2D ```
make
```
and got > make: *** No targets specified and no makefile found.  Stop.
What should I do?
here is a link to previous attempts [http://kubuntuforums.net/forums/index.php?topic=3109198.0]("http://kubuntuforums.net/forums/index.php?topic=3109198.0")
[FONT="System"][COLOR="Green"]PS I had intended to attach the Xorg.0.log file as a .txt but it would not attach as it was 37kb and the attachments for .txt can only be 19.5kb where as .doc can be 195kb so the xorg.0.log is attached as a .doc file.[/COLOR][/FONT]

---

### Post by TSJason on 2009-12-31
> **Phonic_P said:**
> 
In doing so everything went great till step 5 for 2D ```
make
```


What was the output of your ./autogen.sh?

---

### Post by Phonic_P on 2009-12-31
> **TSJason said:**
> What was the output of your ./autogen.sh?

Being a noob where would I find a log of that particular output?

---

### Post by Hakimio on 2010-01-01
> **Phonic_P said:**
> Hi and thanks for this guide.
I have been having issues with resolution on ALL Ubuntu & Kubuntu with the Nvidia driver (96) and decided to give Nouveau a go. I had received advice from the kubuntu forum [http://kubuntuforums.net/forums/index.php?topic=3109198.0]("http://kubuntuforums.net/forums/index.php?topic=3109198.0") and was advised to check this guide.
In doing so everything went great till step 5 for 2D ```
make
```
and got 
What should I do?
I guess something went wrong during configuration (missing dependency?) or you skipped "./autogen.sh" step. Try running ```
./configure
``` inside drm directory. Then post the output in some pastebin or attach it to your post.

Anyway, keep in mind that as noted by dinxter this guide is **OUTDATED**. I'll have some time to update it only in February.

For now, you could just use some PPA like [xorg-edgers fresh X crack](https://launchpad.net/~xorg-edgers/+archive/ppa) (nightly builds) to install xserver-xorg-video-nouveau package.

---

### Post by Phonic_P on 2010-01-12
Thanks for your advice, I tried again with the ```
sh autogen.sh
``` in drm directory, as advised by sithlord48  from kubuntu forum.  As well I have tried the ./configure angle you just suggested. Attached is the output from my attempts.

---

### Post by Hakimio on 2010-01-13
> **Phonic_P said:**
> Thanks for your advice, I tried again with the ```
sh autogen.sh
``` in drm directory, as advised by sithlord48  from kubuntu forum.  As well I have tried the ./configure angle you just suggested. Attached is the output from my attempts.
Why are you running everything as root?
Do you have pkg-config installed?
```
pkg-config --version
```
Do you have pkg.m4 in /usr/share/aclocal ?
```
ls /usr/share/aclocal | grep pkg
```

---

### Post by Phonic_P on 2010-01-13
> **Hakimio said:**
> Why are you running everything as root?
Do you have pkg-config installed?
```
pkg-config --version
```
Do you have pkg.m4 in /usr/share/aclocal ?
```
ls /usr/share/aclocal | grep pkg
```

I was running in root as I thought it might save time typing my password.
No pkg-config was not installed but I did install it and checked with ```
ls /usr/share/aclocal | grep pkg
``` which replied **[COLOR="Red"]pkg[/COLOR]**.m4
I also manualy checked if it was in /usr/share/aclocal, which it was.
I then started again and it went fine till > 7. Enter linux-core directory and compile kernel modules
```
cd linux-core ; make nouveau.o
```
 This is the reply ```
bash: cd: linux-core: No such file or directory
make: *** No rule to make target `nouveau.o'.  Stop.
```
I have attached the output from my terminal/konsole session.
PS: Will it matter that I'm trying to install on both ubuntu & kubuntu?
ALSO: I followed the advice from > For now, you could just use some PPA like xorg-edgers fresh X crack (nightly builds) to install xserver-xorg-video-nouveau package. and added their PPA to my systems software sources, only to discover they were already installed. but when I wrote an xorg.conf file suggested @ [http://ossnotebook.blogspot.com/2009/08/how-to-make-nouveau-driver-work-in.html]("http://ossnotebook.blogspot.com/2009/08/how-to-make-nouveau-driver-work-in.html") my xserver blew a gasket and would not start nor when I tried to log in via recovery mode.  So I reinstalled the OS again.

---

### Post by Hakimio on 2010-01-13
> **Phonic_P said:**
> I was running in root as I thought it might save time typing my password.
That's a bad idea. Instead you could just increase [timeout time](http://shibuvarkala.blogspot.com/2009/12/how-to-change-sudo-password-remembering.html).
> **Phonic_P said:**
> I then started again and it went fine till  This is the reply ```
bash: cd: linux-core: No such file or directory
make: *** No rule to make target `nouveau.o'.  Stop.
```
I have attached the output from my terminal/konsole session.
It seems --enable-nouveau-experimental-api switch is now required. Try running:
```
./configure --enable-nouveau-experimental-api --prefix=/usr/
```
then "make" and "sudo make install".
> **Phonic_P said:**
> PS: Will it matter that I'm trying to install on both ubuntu & kubuntu?
No, it doesn't matter. 
> **Phonic_P said:**
> ALSO: I followed the advice from  and added their PPA to my systems software sources, only to discover they were already installed. but when I wrote an xorg.conf file suggested @ [http://ossnotebook.blogspot.com/2009/08/how-to-make-nouveau-driver-work-in.html]("http://ossnotebook.blogspot.com/2009/08/how-to-make-nouveau-driver-work-in.html") my xserver blew a gasket and would not start nor when I tried to log in via recovery mode.  So I reinstalled the OS again.
[LIST]
[*]What VGA do you have? Is it supported (see the tutorial's notes section)?
[*]You don't have to edit screen section, only device in xorg.conf .
If sth goes wrong when starting X server at least save a copy of Xorg.0.log. 
[*]Instead of reinstalling the system you could have just used ubuntu live cd to edit xorg.conf or boot to CLI ("Recovery mode" (?) or sth like that in the grub menu ) and used nano editor which is pretty easy to use too.
[/LIST]

---

### Post by Phonic_P on 2010-01-13
> **Hakimio said:**
> 
[LIST]
[*]What VGA do you have? Is it supported (see the tutorial's notes section)?
[*]You don't have to edit screen section, only device in xorg.conf .
If sth goes wrong when starting X server at least save a copy of Xorg.0.log. 
[*]Instead of reinstalling the system you could have just used ubuntu live cd to edit xorg.conf or boot to CLI ("Recovery mode" (?) or sth like that in the grub menu ) and used nano editor which is pretty easy to use too.
[/LIST]

AMD Athlon 64 CPU, 1G RAM, Nvidia GeForce Mx440se (64mb) GPU, on a K8T800-A MB using HDTV as monitor.
Thanks for you're advise The new code for ./configure worked well but I still cannot get passed #7 Enter linux-core directory and compile kernel modules```
cd linux-core ; make nouveau.o
```
```
bash: cd: linux-core: No such file or directory
make: *** No rule to make target `nouveau.o'.  Stop.
```
I have attached outputs

---

### Post by Hakimio on 2010-01-13
> **Phonic_P said:**
> AMD Athlon 64 CPU, 1G RAM, Nvidia GeForce Mx440se (64mb) GPU, on a K8T800-A MB using HDTV as monitor.
Your graphic adapter is NV10 family (NV17 card to be more precise) and many things are still "Work In Progress". Don't expect things to work flawlesly. See [Feature matrix](http://nouveau.freedesktop.org/wiki/FeatureMatrix) for more details.
> **Phonic_P said:**
> Thanks for you're advise The new code for ./configure worked well but I still cannot get passed #7 Enter linux-core directory and compile kernel modules```
cd linux-core ; make nouveau.o
```
```
bash: cd: linux-core: No such file or directory
make: *** No rule to make target `nouveau.o'.  Stop.
```
I have attached outputs
As I have already stated the guide is OUTDATED.
I guess now steps in 2D section should be sth like:
```

./configure --enable-nouveau-experimental-api --prefix=/usr/
make
sudo make install
sudo modprobe nouveau

```
then just go to step **11**.

Don't expect any help with 3D section until next month as currently I am pretty busy.

---

### Post by Phonic_P on 2010-01-13
I have **[COLOR="Magenta"]really[/COLOR]** appreciated the time you have given me already and cannot thank you enough as you're replies, in this post, have been quite rapid compared to my other posts.
I shall attempt to use the code you have divulged and if it won't work I'll try to hold off till the new guide is written or nouveau takes over from vesa. 
Once again thanks for ALL you have done.

---

### Post by bladerunner6 on 2010-01-19
anyone know how to activate the drivers within the 2.6.33.xxx kernel ?

---

### Post by Darxus on 2010-11-11
In Ubuntu Maverick all you need to do is install the package libgl1-mesa-dri-experimental from the Universal archive, and deactivate the proprietary nvidia driver via System / Administration / Additional Drivers.

---

### Post by gufide on 2010-11-20
does this driver support nvidia gts360m for notebook?

---

### Post by SeijiSensei on 2010-11-20
I also don't see any references to VDPAU in this thread.  Any support for that?  I thought it was pretty much an open interface, but I could certainly be wrong.

---

### Post by peely on 2011-01-09
> **SeijiSensei said:**
> I also don't see any references to VDPAU in this thread.  Any support for that?  I thought it was pretty much an open interface, but I could certainly be wrong.

Nouveau currently doesn't support VDPAU or any other media offload API.

---

### Post by Hakimio on 2011-03-18
Guide finally updated. 
Please test and report any issues.

---

### Post by salvatorect on 2011-04-30
Hi,

is this guide valid for Ubuntu 11.04?
I cannot go through passage 3 of part A. After executing sudo Xorg -configure it says "number of created screens does not match number of detected devices".
My hardware configuration is:
Acer Aspire 5635WLMi
Intel Core 2 Duo processor T7200
nVidia GeForce Go 7300 128 MB
2 GB DDR2

---

### Post by Hakimio on 2011-04-30
> **salvatorect said:**
> Hi,

is this guide valid for Ubuntu 11.04?
I cannot go through passage 3 of part A. After executing sudo Xorg -configure it says "number of created screens does not match number of detected devices".

Yes, it was tested for 11.04. The error might be due to nvidia proprietary drivers. After running the command, is "xorg.conf.new"
file created? If it's created, could you upload it somewhere? Do you have xorg.conf file in /etc/X11/? Did you stop gdm server as mentioned in the guide?

---

### Post by salvatorect on 2011-04-30
> **Hakimio said:**
> Yes, it was tested for 11.04. The error might be due to nvidia proprietary drivers. After running the command, is "xorg.conf.new"
file created? If it's created, could you upload it somewhere? Do you have xorg.conf file in /etc/X11/? Did you stop gdm server as mentioned in the guide?

In the meanwhile I tried many installing/uninstalling operations so I am not sure whether nvidia drivers are completely uninstalled or not.
After running the command, "xorg.conf.new" is in fact created in my home directory. I pasted its content at the end of this post.
I did have a xorg.conf file in /etc/X11/ but after uninstalling nvidia drivers it prevented me to run the desktop manager so I deleted it (or left it completely blank). Now I am able to start desktop manager but only in low resolution mode (1024x768, while correct is 1280x800).
Yes, I stopped gdm server as mentioned in the guide.

Thanks for help.

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	Screen      2  "Screen2" RightOf "Screen1"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dbe"
	Load  "extmod"
	Load  "record"
	Load  "dri"
	Load  "dri2"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "WrappedFB"          	# [<bool>]
        #Option     "GLXVBlank"          	# [<bool>]
        #Option     "ZaphodHeads"        	# <str>
	Identifier  "Card0"
	Driver      "nouveau"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card1"
	Driver      "fbdev"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card2"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device     "Card2"
	Monitor    "Monitor2"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by Hakimio on 2011-04-30
> **salvatorect said:**
> In the meanwhile I tried many installing/uninstalling operations so I am not sure whether nvidia drivers are completely uninstalled or not.
After running the command, "xorg.conf.new" is in fact created in my home directory. I pasted its content at the end of this post.
I did have a xorg.conf file in /etc/X11/ but after uninstalling nvidia drivers it prevented me to run the desktop manager so I deleted it (or left it completely blank). Now I am able to start desktop manager but only in low resolution mode (1024x768, while correct is 1280x800).
Yes, I stopped gdm server as mentioned in the guide.

Thanks for help.

If you actually left xorg.conf blank, you should just delete it.
The reason for getting low resolution, most probably is that you are using vesa instead of nouveau drivers (2D nouveau drivers should be installed by default in ubuntu - check if you have xserver-xorg-video-nouveau package installed). 
You could try deleting two Screen sections which identifiers are "Screen1" and "Screen2" (only leave Screen0) in xorg.conf.new, then rename xorg.conf.new to xorg.conf, copy it to /etc/X11 and try to restart. For some reason, you have two additional screens and two additional VGA cards listed, both of which are using wrong drivers for some reason.

---

### Post by salvatorect on 2011-04-30
> **Hakimio said:**
> If you actually left xorg.conf blank, you should just delete it.
The reason for getting low resolution, most probably is that you are using vesa instead of nouveau drivers (2D nouveau drivers should be installed by default in ubuntu - check if you have xserver-xorg-video-nouveau package installed). 
You could try deleting two Screen sections which identifiers are "Screen1" and "Screen2" (only leave Screen0) in xorg.conf.new, then rename xorg.conf.new to xorg.conf, copy it to /etc/X11 and try to restart. For some reason, you have two additional screens and two additional VGA cards listed, both of which are using wrong drivers for some reason.

The package xserver-xorg-video-nouveau is installed; actually the package (I think it is more precisely a metapackage) xserver-xorg-video-all is installed. I've also installed the package nouveau-firmware, don't know if useful. Also the package nvidia-common is installed - I didn't uninstalled it beacuse it requires to uninstall ubuntu-desktop as well. However it seems that nvidia drivers shouldn't be installed (nvidia-current, nvidia-glx-* etc. are all unselected).
With this package configuration I edited xorg.conf.new and copied it to /etc/X11/xorg.conf. The file content after edited is attached at the end of this post. However it doesn't work. During start up the screen flash two or three times and then stops. With Ctrl-Alt-F1 I am able to login in the virtual terminal and then I deleted xorg.conf thus allowing X to start correctly (but always in low resolution) after reboot.
What's wrong? Why it seems so difficult to have nouveau in my computer? Actually I have always used proprietary nvidia drivers and never tried to use nouveau, but with 11.04 I was not able to use Unity, so trying nouveau.

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dbe"
	Load  "extmod"
	Load  "record"
	Load  "dri"
	Load  "dri2"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "WrappedFB"          	# [<bool>]
        #Option     "GLXVBlank"          	# [<bool>]
        #Option     "ZaphodHeads"        	# <str>
	Identifier  "Card0"
	Driver      "nouveau"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by Hakimio on 2011-04-30
After the flashing, copy /var/log/Xorg.0.log somewhere else (so it wouldn't be overwritten) and then show it here.

BTW, ubuntu-desktop is just a meta-package. It only depends on all the ubuntu default packages, but doesn't contain anything. It's fairly safe to uninstall it.

---

### Post by salvatorect on 2011-05-01
> **Hakimio said:**
> After the flashing, copy /var/log/Xorg.0.log somewhere else (so it wouldn't be overwritten) and then show it here.

BTW, ubuntu-desktop is just a meta-package. It only depends on all the ubuntu default packages, but doesn't contain anything. It's fairly safe to uninstall it.

Here is the log after flashing:

```
[    31.667] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    31.667] X Protocol Version 11, Revision 0
[    31.667] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    31.667] Current Operating System: Linux salvo-laptop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    31.667] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=4a6b9059-8482-4ca2-b97f-846dd5d8ef0a ro quiet splash quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap vt.handoff=7
[    31.667] Build Date: 19 April 2011  03:33:17PM
[    31.667] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    31.667] Current version of pixman: 0.20.2
[    31.667] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    31.667] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    31.667] (==) Log file: "/var/log/Xorg.0.log", Time: Sun May  1 09:15:02 2011
[    31.667] (==) Using config file: "/etc/X11/xorg.conf"
[    31.667] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    31.684] (==) ServerLayout "X.org Configured"
[    31.684] (**) |-->Screen "Screen0" (0)
[    31.684] (**) |   |-->Monitor "Monitor0"
[    31.684] (**) |   |-->Device "Card0"
[    31.684] (**) |-->Input Device "Mouse0"
[    31.684] (**) |-->Input Device "Keyboard0"
[    31.684] (==) Automatically adding devices
[    31.684] (==) Automatically enabling devices
[    31.684] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    31.684] 	Entry deleted from font path.
[    31.684] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    31.684] 	Entry deleted from font path.
[    31.684] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    31.684] (**) ModulePath set to "/usr/lib/xorg/modules"
[    31.684] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    31.684] (WW) Disabling Mouse0
[    31.684] (WW) Disabling Keyboard0
[    31.684] (II) Loader magic: 0x81ffde0
[    31.684] (II) Module ABI versions:
[    31.684] 	X.Org ANSI C Emulation: 0.4
[    31.684] 	X.Org Video Driver: 10.0
[    31.684] 	X.Org XInput driver : 12.3
[    31.684] 	X.Org Server Extension : 5.0
[    31.686] (--) PCI:*(0:1:0:0) 10de:01d7:1025:0090 rev 161, Mem @ 0xcd000000/16777216, 0xd0000000/268435456, 0xce000000/16777216
[    31.686] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    31.686] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    31.686] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[    31.686] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    31.686] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[    31.686] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    31.686] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[    31.686] (II) LoadModule: "dbe"
[    31.697] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    31.697] (II) Module dbe: vendor="X.Org Foundation"
[    31.697] 	compiled for 1.10.1, module version = 1.0.0
[    31.697] 	Module class: X.Org Server Extension
[    31.697] 	ABI class: X.Org Server Extension, version 5.0
[    31.697] (II) Loading extension DOUBLE-BUFFER
[    31.697] (II) LoadModule: "extmod"
[    31.698] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    31.698] (II) Module extmod: vendor="X.Org Foundation"
[    31.698] 	compiled for 1.10.1, module version = 1.0.0
[    31.698] 	Module class: X.Org Server Extension
[    31.698] 	ABI class: X.Org Server Extension, version 5.0
[    31.698] (II) Loading extension MIT-SCREEN-SAVER
[    31.698] (II) Loading extension XFree86-VidModeExtension
[    31.698] (II) Loading extension XFree86-DGA
[    31.698] (II) Loading extension DPMS
[    31.698] (II) Loading extension XVideo
[    31.698] (II) Loading extension XVideo-MotionCompensation
[    31.698] (II) Loading extension X-Resource
[    31.698] (II) LoadModule: "record"
[    31.698] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    31.698] (II) Module record: vendor="X.Org Foundation"
[    31.698] 	compiled for 1.10.1, module version = 1.13.0
[    31.698] 	Module class: X.Org Server Extension
[    31.698] 	ABI class: X.Org Server Extension, version 5.0
[    31.698] (II) Loading extension RECORD
[    31.698] (II) LoadModule: "dri"
[    31.699] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    31.699] (II) Module dri: vendor="X.Org Foundation"
[    31.699] 	compiled for 1.10.1, module version = 1.0.0
[    31.699] 	ABI class: X.Org Server Extension, version 5.0
[    31.699] (II) Loading extension XFree86-DRI
[    31.699] (II) LoadModule: "dri2"
[    31.699] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    31.699] (II) Module dri2: vendor="X.Org Foundation"
[    31.699] 	compiled for 1.10.1, module version = 1.2.0
[    31.699] 	ABI class: X.Org Server Extension, version 5.0
[    31.699] (II) Loading extension DRI2
[    31.699] (II) LoadModule: "glx"
[    31.700] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    31.700] (II) Module glx: vendor="X.Org Foundation"
[    31.700] 	compiled for 1.10.1, module version = 1.0.0
[    31.700] 	ABI class: X.Org Server Extension, version 5.0
[    31.700] (==) AIGLX enabled
[    31.700] (II) Loading extension GLX
[    31.700] (II) LoadModule: "nouveau"
[    31.700] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    31.724] (II) Module nouveau: vendor="X.Org Foundation"
[    31.724] 	compiled for 1.10.0, module version = 0.0.16
[    31.724] 	Module class: X.Org Video Driver
[    31.724] 	ABI class: X.Org Video Driver, version 10.0
[    31.725] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[    31.725] (II) NOUVEAU driver for NVIDIA chipset families :
[    31.725] 	RIVA TNT    (NV04)
[    31.725] 	RIVA TNT2   (NV05)
[    31.725] 	GeForce 256 (NV10)
[    31.725] 	GeForce 2   (NV11, NV15)
[    31.725] 	GeForce 4MX (NV17, NV18)
[    31.725] 	GeForce 3   (NV20)
[    31.725] 	GeForce 4Ti (NV25, NV28)
[    31.726] 	GeForce FX  (NV3x)
[    31.726] 	GeForce 6   (NV4x)
[    31.726] 	GeForce 7   (G7x)
[    31.726] 	GeForce 8   (G8x)
[    31.726] (++) using VT number 7

[    31.726] drmOpenDevice: node name is /dev/dri/card0
[    32.274] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    32.274] drmOpenDevice: node name is /dev/dri/card0
[    32.280] drmOpenByBusid: drmOpenMinor returns -1
[    32.280] drmOpenDevice: node name is /dev/dri/card1
[    32.286] drmOpenByBusid: drmOpenMinor returns -1
[    32.286] drmOpenDevice: node name is /dev/dri/card2
[    32.290] drmOpenByBusid: drmOpenMinor returns -1
[    32.290] drmOpenDevice: node name is /dev/dri/card3
[    32.294] drmOpenByBusid: drmOpenMinor returns -1
[    32.294] drmOpenDevice: node name is /dev/dri/card4
[    32.299] drmOpenByBusid: drmOpenMinor returns -1
[    32.299] drmOpenDevice: node name is /dev/dri/card5
[    32.303] drmOpenByBusid: drmOpenMinor returns -1
[    32.303] drmOpenDevice: node name is /dev/dri/card6
[    32.308] drmOpenByBusid: drmOpenMinor returns -1
[    32.308] drmOpenDevice: node name is /dev/dri/card7
[    32.312] drmOpenByBusid: drmOpenMinor returns -1
[    32.312] drmOpenDevice: node name is /dev/dri/card8
[    32.316] drmOpenByBusid: drmOpenMinor returns -1
[    32.316] drmOpenDevice: node name is /dev/dri/card9
[    32.321] drmOpenByBusid: drmOpenMinor returns -1
[    32.321] drmOpenDevice: node name is /dev/dri/card10
[    32.325] drmOpenByBusid: drmOpenMinor returns -1
[    32.325] drmOpenDevice: node name is /dev/dri/card11
[    32.330] drmOpenByBusid: drmOpenMinor returns -1
[    32.330] drmOpenDevice: node name is /dev/dri/card12
[    32.335] drmOpenByBusid: drmOpenMinor returns -1
[    32.335] drmOpenDevice: node name is /dev/dri/card13
[    32.341] drmOpenByBusid: drmOpenMinor returns -1
[    32.341] drmOpenDevice: node name is /dev/dri/card14
[    32.346] drmOpenByBusid: drmOpenMinor returns -1
[    32.346] drmOpenDevice: node name is /dev/dri/card15
[    32.351] drmOpenByBusid: drmOpenMinor returns -1
[    32.351] drmOpenDevice: node name is /dev/dri/card0
[    32.360] drmOpenDevice: node name is /dev/dri/card0
[    32.366] drmOpenDevice: node name is /dev/dri/card1
[    32.373] drmOpenDevice: node name is /dev/dri/card2
[    32.379] drmOpenDevice: node name is /dev/dri/card3
[    32.385] drmOpenDevice: node name is /dev/dri/card4
[    32.391] drmOpenDevice: node name is /dev/dri/card5
[    32.396] drmOpenDevice: node name is /dev/dri/card6
[    32.401] drmOpenDevice: node name is /dev/dri/card7
[    32.406] drmOpenDevice: node name is /dev/dri/card8
[    32.411] drmOpenDevice: node name is /dev/dri/card9
[    32.417] drmOpenDevice: node name is /dev/dri/card10
[    32.422] drmOpenDevice: node name is /dev/dri/card11
[    32.427] drmOpenDevice: node name is /dev/dri/card12
[    32.432] drmOpenDevice: node name is /dev/dri/card13
[    32.437] drmOpenDevice: node name is /dev/dri/card14
[    32.442] drmOpenDevice: node name is /dev/dri/card15
[    32.447] (EE) [drm] failed to open device
[    32.447] (EE) No devices detected.
[    32.447] 
Fatal server error:
[    32.447] no screens found
[    32.447] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    32.447] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    32.447] 

```

Here is the log after trying "sudo Xorg -configure":
```
[    94.874] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    94.874] X Protocol Version 11, Revision 0
[    94.874] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    94.874] Current Operating System: Linux salvo-laptop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    94.874] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=4a6b9059-8482-4ca2-b97f-846dd5d8ef0a ro quiet splash quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap vt.handoff=7
[    94.875] Build Date: 19 April 2011  03:33:17PM
[    94.875] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    94.875] Current version of pixman: 0.20.2
[    94.875] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    94.875] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    94.876] (==) Log file: "/var/log/Xorg.0.log", Time: Sun May  1 09:16:06 2011
[    94.876] (II) Loader magic: 0x81ffde0
[    94.876] (II) Module ABI versions:
[    94.876] 	X.Org ANSI C Emulation: 0.4
[    94.876] 	X.Org Video Driver: 10.0
[    94.876] 	X.Org XInput driver : 12.3
[    94.876] 	X.Org Server Extension : 5.0
[    94.877] (--) PCI:*(0:1:0:0) 10de:01d7:1025:0090 rev 161, Mem @ 0xcd000000/16777216, 0xd0000000/268435456, 0xce000000/16777216
[    94.878] List of video drivers:
[    94.878] 	s3
[    94.878] 	trident
[    94.878] 	intel
[    94.878] 	sis
[    94.878] 	s3virge
[    94.878] 	tseng
[    94.878] 	ztv
[    94.878] 	v4l
[    94.878] 	radeon
[    94.878] 	savage
[    94.878] 	ark
[    94.878] 	i740
[    94.878] 	cirrus
[    94.878] 	tdfx
[    94.878] 	apm
[    94.879] 	sisusb
[    94.879] 	i128
[    94.879] 	mach64
[    94.879] 	geode
[    94.880] 	rendition
[    94.880] 	siliconmotion
[    94.880] 	mga
[    94.880] 	voodoo
[    94.881] 	nouveau
[    94.881] 	qxl
[    94.881] 	openchrome
[    94.881] 	neomagic
[    94.881] 	chips
[    94.882] 	ati
[    94.882] 	r128
[    94.883] 	fbdev
[    94.884] 	vesa
[    94.885] (II) LoadModule: "s3"
[    94.885] (II) Loading /usr/lib/xorg/modules/drivers/s3_drv.so
[    94.896] (II) Module s3: vendor="X.Org Foundation"
[    94.896] 	compiled for 1.10.0, module version = 0.6.3
[    94.896] 	Module class: X.Org Video Driver
[    94.896] 	ABI class: X.Org Video Driver, version 10.0
[    94.896] (II) LoadModule: "trident"
[    94.897] (II) Loading /usr/lib/xorg/modules/drivers/trident_drv.so
[    94.911] (II) Module trident: vendor="X.Org Foundation"
[    94.911] 	compiled for 1.10.0, module version = 1.3.4
[    94.911] 	Module class: X.Org Video Driver
[    94.911] 	ABI class: X.Org Video Driver, version 10.0
[    94.912] (II) LoadModule: "intel"
[    94.912] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    94.934] (II) Module intel: vendor="X.Org Foundation"
[    94.935] 	compiled for 1.10.1, module version = 2.14.0
[    94.935] 	Module class: X.Org Video Driver
[    94.935] 	ABI class: X.Org Video Driver, version 10.0
[    94.935] (II) LoadModule: "sis"
[    94.935] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[    94.969] (II) Module sis: vendor="X.Org Foundation"
[    94.969] 	compiled for 1.10.0, module version = 0.10.3
[    94.969] 	Module class: X.Org Video Driver
[    94.969] 	ABI class: X.Org Video Driver, version 10.0
[    94.969] (II) LoadModule: "s3virge"
[    94.969] (II) Loading /usr/lib/xorg/modules/drivers/s3virge_drv.so
[    94.982] (II) Module s3virge: vendor="X.Org Foundation"
[    94.982] 	compiled for 1.10.0, module version = 1.10.4
[    94.982] 	Module class: X.Org Video Driver
[    94.982] 	ABI class: X.Org Video Driver, version 10.0
[    94.982] (II) LoadModule: "tseng"
[    94.982] (II) Loading /usr/lib/xorg/modules/drivers/tseng_drv.so
[    94.997] (II) Module tseng: vendor="X.Org Foundation"
[    94.998] 	compiled for 1.10.0, module version = 1.1.0
[    94.998] 	Module class: X.Org Video Driver
[    94.998] 	ABI class: X.Org Video Driver, version 10.0
[    94.998] (II) LoadModule: "ztv"
[    94.998] (II) Loading /usr/lib/xorg/modules/drivers/ztv_drv.so
[    95.004] (II) Module ztv: vendor="X.Org Foundation"
[    95.004] 	compiled for 1.10.0, module version = 0.0.1
[    95.004] 	ABI class: X.Org Video Driver, version 10.0
[    95.004] (II) LoadModule: "v4l"
[    95.004] (II) Loading /usr/lib/xorg/modules/drivers/v4l_drv.so
[    95.017] (II) Module v4l: vendor="X.Org Foundation"
[    95.017] 	compiled for 1.10.0, module version = 0.1.1
[    95.017] 	ABI class: X.Org Video Driver, version 10.0
[    95.017] (II) LoadModule: "radeon"
[    95.017] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    95.081] (II) Module radeon: vendor="X.Org Foundation"
[    95.081] 	compiled for 1.10.0, module version = 6.14.0
[    95.081] 	Module class: X.Org Video Driver
[    95.081] 	ABI class: X.Org Video Driver, version 10.0
[    95.095] (II) LoadModule: "savage"
[    95.095] (II) Loading /usr/lib/xorg/modules/drivers/savage_drv.so
[    95.117] (II) Module savage: vendor="X.Org Foundation"
[    95.117] 	compiled for 1.10.0, module version = 2.3.2
[    95.117] 	Module class: X.Org Video Driver
[    95.117] 	ABI class: X.Org Video Driver, version 10.0
[    95.117] (II) LoadModule: "ark"
[    95.117] (II) Loading /usr/lib/xorg/modules/drivers/ark_drv.so
[    95.130] (II) Module ark: vendor="X.Org Foundation"
[    95.130] 	compiled for 1.10.0, module version = 0.7.3
[    95.130] 	Module class: X.Org Video Driver
[    95.130] 	ABI class: X.Org Video Driver, version 10.0
[    95.130] (II) LoadModule: "i740"
[    95.130] (II) Loading /usr/lib/xorg/modules/drivers/i740_drv.so
[    95.141] (II) Module i740: vendor="X.Org Foundation"
[    95.141] 	compiled for 1.10.0, module version = 1.3.2
[    95.141] 	Module class: X.Org Video Driver
[    95.141] 	ABI class: X.Org Video Driver, version 10.0
[    95.141] (II) LoadModule: "cirrus"
[    95.142] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_drv.so
[    95.146] (II) Module cirrus: vendor="X.Org Foundation"
[    95.146] 	compiled for 1.10.0, module version = 1.3.2
[    95.146] 	Module class: X.Org Video Driver
[    95.146] 	ABI class: X.Org Video Driver, version 10.0
[    95.146] (II) LoadModule: "tdfx"
[    95.146] (II) Loading /usr/lib/xorg/modules/drivers/tdfx_drv.so
[    95.151] (II) Module tdfx: vendor="X.Org Foundation"
[    95.151] 	compiled for 1.10.0, module version = 1.4.3
[    95.151] 	Module class: X.Org Video Driver
[    95.151] 	ABI class: X.Org Video Driver, version 10.0
[    95.151] (II) LoadModule: "apm"
[    95.151] (II) Loading /usr/lib/xorg/modules/drivers/apm_drv.so
[    95.166] (II) Module apm: vendor="X.Org Foundation"
[    95.167] 	compiled for 1.10.0, module version = 1.2.3
[    95.167] 	Module class: X.Org Video Driver
[    95.167] 	ABI class: X.Org Video Driver, version 10.0
[    95.167] (II) LoadModule: "sisusb"
[    95.167] (II) Loading /usr/lib/xorg/modules/drivers/sisusb_drv.so
[    95.176] (II) Module sisusb: vendor="X.Org Foundation"
[    95.176] 	compiled for 1.10.0, module version = 0.9.4
[    95.176] 	Module class: X.Org Video Driver
[    95.176] 	ABI class: X.Org Video Driver, version 10.0
[    95.176] (II) LoadModule: "i128"
[    95.176] (II) Loading /usr/lib/xorg/modules/drivers/i128_drv.so
[    95.177] (II) Module i128: vendor="X.Org Foundation"
[    95.177] 	compiled for 1.10.0, module version = 1.3.4
[    95.177] 	Module class: X.Org Video Driver
[    95.177] 	ABI class: X.Org Video Driver, version 10.0
[    95.177] (II) LoadModule: "mach64"
[    95.178] (II) Loading /usr/lib/xorg/modules/drivers/mach64_drv.so
[    95.193] (II) Module mach64: vendor="X.Org Foundation"
[    95.193] 	compiled for 1.10.0, module version = 6.8.2
[    95.193] 	Module class: X.Org Video Driver
[    95.194] 	ABI class: X.Org Video Driver, version 10.0
[    95.194] (II) LoadModule: "geode"
[    95.194] (II) Loading /usr/lib/xorg/modules/drivers/geode_drv.so
[    95.212] (II) Module geode: vendor="X.Org Foundation"
[    95.212] 	compiled for 1.10.0, module version = 2.11.12
[    95.213] 	Module class: X.Org Video Driver
[    95.213] 	ABI class: X.Org Video Driver, version 10.0
[    95.213] (II) LoadModule: "rendition"
[    95.213] (II) Loading /usr/lib/xorg/modules/drivers/rendition_drv.so
[    95.221] (II) Module rendition: vendor="X.Org Foundation"
[    95.221] 	compiled for 1.10.0, module version = 4.2.4
[    95.221] 	Module class: X.Org Video Driver
[    95.221] 	ABI class: X.Org Video Driver, version 10.0
[    95.221] (II) LoadModule: "siliconmotion"
[    95.221] (II) Loading /usr/lib/xorg/modules/drivers/siliconmotion_drv.so
[    95.232] (II) Module siliconmotion: vendor="X.Org Foundation"
[    95.232] 	compiled for 1.10.0, module version = 1.7.4
[    95.232] 	Module class: X.Org Video Driver
[    95.232] 	ABI class: X.Org Video Driver, version 10.0
[    95.233] (II) LoadModule: "mga"
[    95.233] (II) Loading /usr/lib/xorg/modules/drivers/mga_drv.so
[    95.246] (II) Module mga: vendor="X.Org Foundation"
[    95.246] 	compiled for 1.10.0, module version = 1.4.13
[    95.246] 	Module class: X.Org Video Driver
[    95.246] 	ABI class: X.Org Video Driver, version 10.0
[    95.247] (II) LoadModule: "voodoo"
[    95.248] (II) Loading /usr/lib/xorg/modules/drivers/voodoo_drv.so
[    95.257] (II) Module voodoo: vendor="X.Org Foundation"
[    95.257] 	compiled for 1.10.0, module version = 1.1.0
[    95.257] 	Module class: X.Org Video Driver
[    95.257] 	ABI class: X.Org Video Driver, version 10.0
[    95.257] (II) LoadModule: "nouveau"
[    95.258] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    95.258] (II) Module nouveau: vendor="X.Org Foundation"
[    95.258] 	compiled for 1.10.0, module version = 0.0.16
[    95.258] 	Module class: X.Org Video Driver
[    95.258] 	ABI class: X.Org Video Driver, version 10.0
[    95.258] (II) LoadModule: "qxl"
[    95.258] (II) Loading /usr/lib/xorg/modules/drivers/qxl_drv.so
[    95.275] (II) Module qxl: vendor="X.Org Foundation"
[    95.275] 	compiled for 1.10.0, module version = 0.0.0
[    95.275] 	Module class: X.Org Video Driver
[    95.275] 	ABI class: X.Org Video Driver, version 10.0
[    95.275] (II) LoadModule: "openchrome"
[    95.275] (II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
[    95.301] (II) Module openchrome: vendor="http://openchrome.org/"
[    95.301] 	compiled for 1.10.0, module version = 0.2.904
[    95.301] 	Module class: X.Org Video Driver
[    95.301] 	ABI class: X.Org Video Driver, version 10.0
[    95.301] (II) LoadModule: "neomagic"
[    95.301] (II) Loading /usr/lib/xorg/modules/drivers/neomagic_drv.so
[    95.303] (II) Module neomagic: vendor="X.Org Foundation"
[    95.303] 	compiled for 1.10.0, module version = 1.2.5
[    95.303] 	Module class: X.Org Video Driver
[    95.303] 	ABI class: X.Org Video Driver, version 10.0
[    95.303] (II) LoadModule: "chips"
[    95.303] (II) Loading /usr/lib/xorg/modules/drivers/chips_drv.so
[    95.319] (II) Module chips: vendor="X.Org Foundation"
[    95.319] 	compiled for 1.10.0, module version = 1.2.3
[    95.319] 	Module class: X.Org Video Driver
[    95.319] 	ABI class: X.Org Video Driver, version 10.0
[    95.319] (II) LoadModule: "ati"
[    95.320] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    95.335] (II) Module ati: vendor="X.Org Foundation"
[    95.335] 	compiled for 1.10.0, module version = 6.14.0
[    95.335] 	Module class: X.Org Video Driver
[    95.335] 	ABI class: X.Org Video Driver, version 10.0
[    95.335] (II) LoadModule: "r128"
[    95.335] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[    95.345] (II) Module r128: vendor="X.Org Foundation"
[    95.345] 	compiled for 1.10.0, module version = 6.8.1
[    95.345] 	Module class: X.Org Video Driver
[    95.345] 	ABI class: X.Org Video Driver, version 10.0
[    95.345] (II) LoadModule: "fbdev"
[    95.345] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    95.345] (II) Module fbdev: vendor="X.Org Foundation"
[    95.345] 	compiled for 1.10.0, module version = 0.4.2
[    95.345] 	ABI class: X.Org Video Driver, version 10.0
[    95.345] (II) LoadModule: "vesa"
[    95.345] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    95.346] (II) Module vesa: vendor="X.Org Foundation"
[    95.346] 	compiled for 1.10.0, module version = 2.3.0
[    95.346] 	Module class: X.Org Video Driver
[    95.346] 	ABI class: X.Org Video Driver, version 10.0
[    95.346] (WW) Falling back to old probe method for s3
[    95.346] (WW) Falling back to old probe method for trident
[    95.346] (WW) Falling back to old probe method for sis
[    95.346] (WW) Falling back to old probe method for s3virge
[    95.346] (WW) Falling back to old probe method for tseng
[    95.346] (WW) Falling back to old probe method for z4l
[    95.346] (II) z4l driver for Video4Linux
[    95.346] (WW) Falling back to old probe method for v4l
[    95.346] (II) v4l driver for Video4Linux
[    95.346] (WW) Falling back to old probe method for ark
[    95.346] (WW) Falling back to old probe method for i740
[    95.346] (WW) Falling back to old probe method for cirrus
[    95.346] (II) Loading sub module "cirrus_laguna"
[    95.346] (II) LoadModule: "cirrus_laguna"
[    95.346] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_laguna.so
[    95.347] (II) Module cirrus_laguna: vendor="X.Org Foundation"
[    95.347] 	compiled for 1.10.0, module version = 1.0.0
[    95.347] 	ABI class: X.Org Video Driver, version 10.0
[    95.347] (II) Loading sub module "cirrus_alpine"
[    95.347] (II) LoadModule: "cirrus_alpine"
[    95.347] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_alpine.so
[    95.348] (II) Module cirrus_alpine: vendor="X.Org Foundation"
[    95.348] 	compiled for 1.10.0, module version = 1.0.0
[    95.348] 	ABI class: X.Org Video Driver, version 10.0
[    95.348] (WW) Falling back to old probe method for apm
[    95.348] (WW) Falling back to old probe method for sisusb
[    95.348] (WW) Falling back to old probe method for i128
[    95.348] (WW) Falling back to old probe method for siliconmotion
[    95.348] (WW) Falling back to old probe method for voodoo
[    95.348] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[    95.348] (II) NOUVEAU driver for NVIDIA chipset families :
[    95.348] 	RIVA TNT    (NV04)
[    95.348] 	RIVA TNT2   (NV05)
[    95.348] 	GeForce 256 (NV10)
[    95.348] 	GeForce 2   (NV11, NV15)
[    95.348] 	GeForce 4MX (NV17, NV18)
[    95.348] 	GeForce 3   (NV20)
[    95.348] 	GeForce 4Ti (NV25, NV28)
[    95.348] 	GeForce FX  (NV3x)
[    95.348] 	GeForce 6   (NV4x)
[    95.348] 	GeForce 7   (G7x)
[    95.348] 	GeForce 8   (G8x)
[    95.348] (WW) Falling back to old probe method for neomagic
[    95.348] (II) FBDEV: driver for framebuffer: fbdev
[    95.349] (II) VESA: driver for VESA chipsets: vesa
[    95.376] (++) Using config file: "/home/salvo/xorg.conf.new"
[    95.378] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    95.380] (==) ServerLayout "X.org Configured"
[    95.380] (**) |-->Screen "Screen0" (0)
[    95.380] (**) |   |-->Monitor "Monitor0"
[    95.380] (**) |   |-->Device "Card0"
[    95.380] (**) |-->Screen "Screen1" (1)
[    95.380] (**) |   |-->Monitor "Monitor1"
[    95.380] (**) |   |-->Device "Card1"
[    95.380] (**) |-->Screen "Screen2" (2)
[    95.380] (**) |   |-->Monitor "Monitor2"
[    95.380] (**) |   |-->Device "Card2"
[    95.380] (**) |-->Input Device "Mouse0"
[    95.380] (**) |-->Input Device "Keyboard0"
[    95.380] (==) Automatically adding devices
[    95.380] (==) Automatically enabling devices
[    95.381] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    95.381] 	Entry deleted from font path.
[    95.381] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    95.381] 	Entry deleted from font path.
[    95.381] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    95.381] (**) ModulePath set to "/usr/lib/xorg/modules"
[    95.381] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    95.381] (WW) Disabling Mouse0
[    95.381] (WW) Disabling Keyboard0
[    95.381] (EE) [drm] No DRICreatePCIBusID symbol
[    95.382] (II) Loading sub module "fbdevhw"
[    95.382] (II) LoadModule: "fbdevhw"
[    95.382] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    95.382] (II) Module fbdevhw: vendor="X.Org Foundation"
[    95.382] 	compiled for 1.10.1, module version = 0.0.2
[    95.382] 	ABI class: X.Org Video Driver, version 10.0
[    95.382] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    95.382] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    95.383] (**) FBDEV(0): claimed PCI slot 1@0:0:0
[    95.383] (II) FBDEV(0): using default device
[    95.383] (WW) Falling back to old probe method for vesa
[    95.383] Number of created screens does not match number of detected devices.
  Configuration failed.

```

---

### Post by Hakimio on 2011-05-01
> **salvatorect said:**
> Here is the log after flashing:

```
[    32.447] (EE) [drm] failed to open device
[    32.447] (EE) No devices detected.

```

[_Nouveau troubleshooting guide_](http://nouveau.freedesktop.org/wiki/TroubleShooting#Xorgfailstostartwith.22.28EE.29.5Bdrm.5Dfailedtoopendevice.22) says it might be because of incompatible libdrm version. Did you compile and install libdrm yourself or only used libdrm provided in ubuntu repositories?

---

### Post by salvatorect on 2011-05-01
> **Hakimio said:**
> [_Nouveau troubleshooting guide_](http://nouveau.freedesktop.org/wiki/TroubleShooting#Xorgfailstostartwith.22.28EE.29.5Bdrm.5Dfailedtoopendevice.22) says it might be because of incompatible libdrm version. Did you compile and install libdrm yourself or only used libdrm provided in ubuntu repositories?

No, I didn't compile it, just used that one in ubuntu repositories. Shouldn't it be compatible with latest kernel, also provided by ubuntu repositories?

---

### Post by Hakimio on 2011-05-01
> **salvatorect said:**
> No, I didn't compile it, just used that one in ubuntu repositories. Shouldn't it be compatible with latest kernel, also provided by ubuntu repositories?

According to [_this bug report_](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/528488) last year there were some problems with ubuntu packages. If you are using only ubuntu packages and have completely removed nvidia proprietary driver, maybe you should file a bug report?

---

### Post by salvatorect on 2011-05-01
> **Hakimio said:**
> According to [_this bug report_](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/528488) last year there were some problems with ubuntu packages. If you are using only ubuntu packages and have completely removed nvidia proprietary driver, maybe you should file a bug report?

How can I be sure that I am using only ubuntu packages? I installed my system more than 1 year ago and I have made a lot of installing\uninstalling operations until now.
BTW I tried to jump directly to part B, assuming that nvidia drivers are correctly removed (and my system still doesn't accept to use nouveau beacause drm and other stuff is not correctly installed). But unfortunately I am still blocked in step 2!!! I am not able to install the latest linux kernel. I downloaded linux kernel version 2.6.39-rc4-natty 32 bit as explained in the howto (3 files). But after installing and rebooting the new kernel doesn't start. During boot it stops and caps lock led keep flashing and I had to hard reset and boot with the previous kernel (2.6.38 ). What's wrong with my pc?

---

### Post by Hakimio on 2011-05-01
> **salvatorect said:**
> How can I be sure that I am using only ubuntu packages? I installed my system more than 1 year ago and I have made a lot of installing\uninstalling operations until now.
You can check the origin of the packages you have installed with synaptic package manager. Just click on "Origin" button in the lower left corner.
> BTW I tried to jump directly to part B, assuming that nvidia drivers are correctly removed (and my system still doesn't accept to use nouveau beacause drm and other stuff is not correctly installed). But unfortunately I am still blocked in step 2!!! I am not able to install the latest linux kernel. I downloaded linux kernel version 2.6.39-rc4-natty 32 bit as explained in the howto (3 files). But after installing and rebooting the new kernel doesn't start. During boot it stops and caps lock led keep flashing and I had to hard reset and boot with the previous kernel (2.6.38 ). What's wrong with my pc?
You could also try compiling kernel modules with 2.6.38 and it might work. Just don't forget to install "linux-header" packages for your kernel (they might be installed by default, but I am not sure about that) before compiling.

---

### Post by slaykristian on 2011-08-02
Hi! Great "How-to"!
So... just a question!

I compiled the driver with your procedure under Natty and a vanilla kernel 3.0-rt.

With some problems, but at the end the procedure was ok!
(if you want I can write some operations that I followed for be able to compile)
My problem is after the system boot.
Gdm doesn't start and if I try with textual interface to do a "startx" command, nothing to do... The error message say "(EE) No devices detected. Fatal server error: no screens found"!

I'm using a Dell Inspiron 1520 notebook with NVIDIA GeForce 8400M

Can you help me?!

Thanks in advance!

Christian

---

### Post by Hakimio on 2011-08-03
> **slaykristian said:**
> 
Gdm doesn't start and if I try with textual interface to do a "startx" command, nothing to do... The error message say "(EE) No devices detected. Fatal server error: no screens found"!


After you get "Fatal server error: no screens found" error, copy /var/log/Xorg.0.log somewhere else (so it wouldn't be overwritten) and then show it here. Ie:
```
cp /var/log/Xorg.0.log /home/YOUR_USERNAME/
```

---

### Post by slaykristian on 2011-08-03
This is the Xorg.0.log:
```
[   754.498] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[   754.500] X Protocol Version 11, Revision 0
[   754.501] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   754.501] Current Operating System: Linux chri-Inspiron-1520 3.0.0-slayk-rt3 #2 SMP PREEMPT RT Tue Jul 26 19:12:43 CEST 2011 i686
[   754.502] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-slayk-rt3 root=UUID=163082aa-0f8f-465d-83e3-f95fe868b6fc ro single
[   754.503] Build Date: 21 May 2011  11:38:35AM
[   754.503] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[   754.504] Current version of pixman: 0.20.2
[   754.505] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   754.506] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   754.508] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug  3 17:20:52 2011
[   754.509] (==) Using config file: "/etc/X11/xorg.conf"
[   754.510] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   754.511] Parse error on line 41 of section Monitor in file /etc/X11/xorg.conf
	"Option" is not a valid keyword in this section.
[   754.512] (EE) Problem parsing the config file
[   754.513] (EE) Error parsing the config file
[   754.513] 
Fatal server error:
[   754.515] no screens found
[   754.515] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[   754.518] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   754.519] 
[   754.520]  ddxSigGiveUp: Closing log
```

Thanks!
Christian

---

### Post by Hakimio on 2011-08-03
The log is saying that there is something wrong with your /etc/X11/xorg.conf. Maybe some typos or made some mistakes while copying some text?
```
[   754.511] Parse error on line 41 of section Monitor in file /etc/X11/xorg.conf
	"Option" is not a valid keyword in this section.
[   754.512] (EE) Problem parsing the config file
[   754.513] (EE) Error parsing the config file
```

---

### Post by slaykristian on 2011-08-04
Thanks for tips! I solved my problem and it works perfectly!

Your solution is very good for vanilla -rt kernels that didn't function with nvidia proprietary drivers.

But, as in my previous post I said, I encountered some errors in phase of compiling drivers 2d & 3d.
The problems were due at the location of headers and sources of my vanilla kernel (in a folder placed in my home dir).
After solved this, (I copied all elements of headers folder in sources folder with the union of files), the problem was the command in point 4 of section "E" of your "how-to".
With your command (probably for old version of git mesa driver), the system does not compile "nouveau_dri.so".

So, I used this command:
```
./autogen.sh --with-dri-drivers= --with-gallium-drivers=swrast,nouveau --enable-debug \
 --enable-texture-float --disable-asm --enable-opengl --disable-gles2 --disable-openvg \
 --enable-dri --enable-glx --enable-xvmc --disable-va --disable-vdpau --disable-osmesa \
 --disable-egl --disable-xorg --disable-d3d1x --disable-xa --disable-gbm --disable-xlib-glx \
 --disable-gallium-egl --disable-gallium-gbm --disable-gallium-llvm --disable-xcb \
 --enable-driglx-direct --enable-glx-tls --enable-glu --enable-glw --disable-motif PKG_CONFIG_PATH=/lib/pkgconfig

```

as I found here [http://nouveau.freedesktop.org/wiki/GalliumHowto](http://nouveau.freedesktop.org/wiki/GalliumHowto) 

And then I ran:
```
make PKG_CONFIG_PATH=/lib/pkgconfig
```

After this, I re-took your points.

My last problem was the Xorg configuration.
I resumed an old backup of my Xorg, I insert "nouveau" in "Driver" and some data for change the resolution of my laptop display.
When I'll come back to my home, I'll paste here my Xorg.conf .

Thanks a lot again.

---

### Post by Hakimio on 2011-08-04
> **slaykristian said:**
> the problem was the command in point 4 of section "E" of your "how-to".
With your command (probably for old version of git mesa driver), the system does not compile "nouveau_dri.so".

Maybe the configuration scripts changed since the time I updated the guide. I will try it myself again and see if I can reproduce the problem you had.


Anyway, glad the guide was helpful to you :)

---

### Post by nankura on 2011-08-05
is this guide still valid?

someone in this post said in 10.10 all you have to do is install 
 libgl1-mesa-dri-experimental 

and disable your main driver in jockey

or do i still have to follow the guide?

Also im wondering if this kills the screen tearing problem, the latest nvidia drivers ( appearently since the 200 series drivers ) have had trouble communicate with VSync and compositing window managers

And i have yet to find a permanent fix, 

But im wondering if using the Nouveau 3D Driver will fix this little issue and finally let me use compositing

---

### Post by Hakimio on 2011-08-06
> **nankura said:**
> is this guide still valid?

someone in this post said in 10.10 all you have to do is install 
 libgl1-mesa-dri-experimental 

and disable your main driver in jockey

or do i still have to follow the guide?

Drivers in ubuntu repository are outdated. The guide is for those who need the latest version.


> **nankura said:**
> But im wondering if using the Nouveau 3D Driver will fix this little issue and finally let me use compositing

Don't know.

---

### Post by SeanCly10 on 2011-09-28
I've been fighting a losing battle to try and get 3D with an old GeForce 6800...worked fine up to 9.10, won't hardly do 2D with anything past that.

The proprietary drivers have been nothing but problems...is there 3D support for a card this old with nouveau? And if so, will the posted instructions work to install it?

---

### Post by Hakimio on 2011-09-28
> **SeanCly10 said:**
> The proprietary drivers have been nothing but problems...is there 3D support for a card this old with nouveau? And if so, will the posted instructions work to install it?

Nouveau supports pretty well 6800, but don't expect good performance. Also, if you don't need the latest 3d drivers, you could just libgl1-mesa-dri-experimental package from ubuntu repository which provides pretty old 3d nouveau driver.

---

### Post by SeanCly10 on 2011-09-28
Well, I don't plan on playing any graphics-intense games or anything with it...just making sure my wife's Facebook games don't look like stop-motion.

How does one install the experimental package?

---

### Post by Hakimio on 2011-09-28
> **SeanCly10 said:**
> Well, I don't plan on playing any graphics-intense games or anything with it...just making sure my wife's Facebook games don't look like stop-motion.

How does one install the experimental package?

Use synaptic package manager or run the following command:
```
sudo apt-get install libgl1-mesa-dri-experimental
```

Also you'll need to install xserver-xorg-video-nouveau for 2D and uninstall official nvidia driver to avoid conflicts.

---

### Post by SeanCly10 on 2011-09-28
Ok, I installed the driver as specified, and removed the xorg.conf. It doesn't seem like 3D is working, though...I try to switch on desktop effects and it tells me it can't.

Is there something else I need to do to enable the 3D?

---

### Post by Hakimio on 2011-09-29
> **SeanCly10 said:**
> Ok, I installed the driver as specified, and removed the xorg.conf. It doesn't seem like 3D is working, though...I try to switch on desktop effects and it tells me it can't.

Is there something else I need to do to enable the 3D?

Compiz doesn't work with nouveau, so you can't have all the fancy effects with nouveau. To test 3d you can just run glxgears or some 3d game. Also you can take a look at /var/log/Xorg.0.log to see if the driver was loaded correctly.

---

### Post by SeanCly10 on 2011-09-29
Alrighty, I see that the driver loaded correctly, and glxgears gives me about 300-350 FPS. That about what I should expect?

---

### Post by Hakimio on 2011-09-30
> **SeanCly10 said:**
> Alrighty, I see that the driver loaded correctly, and glxgears gives me about 300-350 FPS. That about what I should expect?

Yeah, I guess so.
BTW, if you are using gnome 2.32 or older version, you can still enable compositing built-in in gnome default window manager called metacity. For more info, see instructions [here]("http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/").

---

### Post by tamashumi on 2011-10-12
Hi,

After issuing command ```
NOUVEAUROOTDIR=../../../.. make
``` I'm getting following error:
```

make -C /lib/modules/2.6.38-11-generic/build KCPPFLAGS="-I/media/home/nouveau/master/include/drm" SUBDIRS="/media/home/nouveau/master/drivers/gpu/drm" CONFIG_DRM=m CONFIG_DRM_KMS_HELPER=m CONFIG_DRM_TTM=m CONFIG_DRM_NOUVEAU=m CONFIG_DRM_NOUVEAU_KMS=n CONFIG_DRM_NOUVEAU_BACKLIGHT=y CONFIG_DRM_NOUVEAU_DEBUG=y CONFIG_DRM_I2C_CH7006=m CONFIG_DRM_I2C_SIL164=m CONFIG_DRM_TDFX=n CONFIG_DRM_R128=n CONFIG_DRM_RADEON=n CONFIG_DRM_MGA=n CONFIG_DRM_I810=n CONFIG_DRM_I830=n CONFIG_DRM_I915=n CONFIG_DRM_SIS=n CONFIG_DRM_SAVAGE=n CONFIG_DRM_VIA=n CONFIG_DRM_VMWGFX=n EXTRA_CFLAGS=" -DCONFIG_DRM_NOUVEAU_BACKLIGHT -DCONFIG_DRM_NOUVEAU_DEBUG " modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
Makefile:631: "WARNING: Appending $KCPPFLAGS (-I/media/home/nouveau/master/include/drm) from command line to kernel $CPPFLAGS"
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_auth.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_buffer.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_bufs.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_cache.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_context.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_dma.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_drv.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_fops.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_gem.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_ioctl.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_irq.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_lock.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_memory.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_proc.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_stub.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_vm.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_agpsupport.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_scatter.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/ati_pcigart.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_pci.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_platform.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_sysfs.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_hashtab.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_sman.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_mm.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_crtc.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_modes.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_edid.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_info.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_debugfs.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_encoder_slave.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_trace_points.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_global.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_usb.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_ioc32.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_fb_helper.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_crtc_helper.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_dp_i2c_helper.o
  LD [M]  /media/home/nouveau/master/drivers/gpu/drm/drm_kms_helper.o
  LD [M]  /media/home/nouveau/master/drivers/gpu/drm/drm.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/i2c/ch7006_drv.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/i2c/ch7006_mode.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/i2c/sil164_drv.o
  LD [M]  /media/home/nouveau/master/drivers/gpu/drm/i2c/ch7006.o
  LD [M]  /media/home/nouveau/master/drivers/gpu/drm/i2c/sil164.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/ttm/ttm_agp_backend.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/ttm/ttm_memory.o
  CC [M]  /media/home/nouveau/master/drivers/gpu/drm/ttm/ttm_tt.o
/media/home/nouveau/master/drivers/gpu/drm/ttm/ttm_tt.c: In function ‘ttm_tt_swapin’:
/media/home/nouveau/master/drivers/gpu/drm/ttm/ttm_tt.c:488:3: error: implicit declaration of function ‘shmem_read_mapping_page’
/media/home/nouveau/master/drivers/gpu/drm/ttm/ttm_tt.c:488:13: warning: assignment makes pointer from integer without a cast
/media/home/nouveau/master/drivers/gpu/drm/ttm/ttm_tt.c: In function ‘ttm_tt_swapout’:
/media/home/nouveau/master/drivers/gpu/drm/ttm/ttm_tt.c:561:11: warning: assignment makes pointer from integer without a cast
make[3]: *** [/media/home/nouveau/master/drivers/gpu/drm/ttm/ttm_tt.o] Error 1
make[2]: *** [/media/home/nouveau/master/drivers/gpu/drm/ttm] Error 2
make[1]: *** [_module_/media/home/nouveau/master/drivers/gpu/drm] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make: *** [modules] Error 2

```

Any idea what could be wrong?

---

### Post by Hakimio on 2011-10-12
> **tamashumi said:**
> Any idea what could be wrong?

Just a guess: old kernel version? What kernel are you using?

---

### Post by tamashumi on 2011-10-12
> **Hakimio said:**
> Just a guess: old kernel version? What kernel are you using?

Thx for reply :)

It was from kernel: 2.6.38-11
Fresh install of Ubuntu 11.04 (natty), plus apt-get update/upgrade.

Is it wrong kernel? I checked Makefile according to instruction for supported kernel version info but haven't found it :F

I just have tried get through whole procedure again with fresh install of 11.10 Beta 2 (oneric without apt-get update/upgrade), kernel 3.0.0-11
Everything went fine unitil 3D driver installation (fine despite I had to install some 2 additional packages for pciaccess and llvm).

Afeter command ```
sudo cp lib/gallium/nouveau_dri.so /usr/lib
``` no file found.  lib/gallium contains files:
r300_dri.so
r600_dri.so
swrast_dri.so
That's strange because I did run the script autorun.sh with all those disable/enable flags.
I think script was run successfully. Last part of the command output attached. You can see, no 'error' there.

EDIT:
01:00.0 VGA compatible controller: nVidia Corporation GF110 [GeForce GTX 560 Ti] (rev a1)

---

### Post by Hakimio on 2011-10-12
> **tamashumi said:**
> Thx for reply :)

It was from kernel: 2.6.38-11
Fresh install of Ubuntu 11.04 (natty), plus apt-get update/upgrade.

Is it wrong kernel? I checked Makefile according to instruction for supported kernel version info but haven't found it :F

The makefile says it needs 3.1:
```
VERSION = 3
PATCHLEVEL = 1
```
I have included in the tutorial a link to a site where you can get the deb packages of the latest kernel.
> **tamashumi said:**
> I just have tried get through whole procedure again with fresh install of 11.10 Beta 2 (oneric without apt-get update/upgrade), kernel 3.0.0-11
Everything went fine unitil 3D driver installation (fine despite I had to install some 2 additional packages for pciaccess and llvm).

Afeter command ```
sudo cp lib/gallium/nouveau_dri.so /usr/lib
``` no file found.  lib/gallium contains files:
r300_dri.so
r600_dri.so
swrast_dri.so
That's strange because I did run the script autorun.sh with all those disable/enable flags.
I think script was run successfully. Last part of the command output attached. You can see, no 'error' there.

Yeah, [slaykristian complained]("http://ubuntuforums.org/showpost.php?p=11117220&postcount=53") about that a while ago. The switches for autogen should be updated. I think I'll do that this weekend.

---

### Post by tamashumi on 2011-10-12
Thanks for info.

Do you think upgrading kernel 3.0 up to 3.1 will change anything or better wait for the command update? :)

I saw you wrote Compiz won't work with nouveau. I Saw at the end of [this]("http://www.seanius.net/blog/2010/04/nouveau-gallium-and-compiz-on-debian/") that it might be possible. How do you think?

Just bought GTX 560 Ti and I'll be really happy if it would run my dual head desktop with single monitor rotated including Compiz. Is such a miracle by any chance possible? ;)

---

### Post by Hakimio on 2011-10-13
> **tamashumi said:**
> Thanks for info.

Do you think upgrading kernel 3.0 up to 3.1 will change anything or better wait for the command update? :)
No, instead of upgrading kernel just try replacing the autogen line in the tutorial with the one suggested by slaykristian:
```
./autogen.sh --with-dri-drivers= --with-gallium-drivers=swrast,nouveau --enable-debug \
 --enable-texture-float --disable-asm --enable-opengl --disable-gles2 --disable-openvg \
 --enable-dri --enable-glx --enable-xvmc --disable-va --disable-vdpau --disable-osmesa \
 --disable-egl --disable-xorg --disable-d3d1x --disable-xa --disable-gbm --disable-xlib-glx \
 --disable-gallium-egl --disable-gallium-gbm --disable-gallium-llvm --disable-xcb \
 --enable-driglx-direct --enable-glx-tls --enable-glu --enable-glw --disable-motif PKG_CONFIG_PATH=/lib/pkgconfig
```

> **tamashumi said:**
> I saw you wrote Compiz won't work with nouveau. I Saw at the end of [this]("http://www.seanius.net/blog/2010/04/nouveau-gallium-and-compiz-on-debian/") that it might be possible. How do you think?

Just bought GTX 560 Ti and I'll be really happy if it would run my dual head desktop with single monitor rotated including Compiz. Is such a miracle by any chance possible? ;)
Last time I checked it didn't work because some of the required extensions were not implemented, but it was long ago and things might have changed since then. You could try launching compiz after the 3d driver installation yourself and you could ask some developers on IRC (freenode server, nouveau channel) if there is any way to get compiz running with nouveau.

---

### Post by tamashumi on 2011-10-13
> **Hakimio said:**
> No, instead of upgrading kernel just try replacing the autogen line in the tutorial with the one suggested by slaykristian: (...)
Now I get```
configure: WARNING: unrecognized options: --with-dri-drivers, --with-gallium-drivers, --enable-debug, --enable-texture-float, --disable-asm, --enable-opengl, --disable-gles2, --disable-openvg, --enable-dri, --enable-glx, --enable-xvmc, --disable-va, --disable-vdpau, --disable-osmesa, --disable-egl, --disable-xorg, --disable-d3d1x, --disable-xa, --disable-gbm, --disable-xlib-glx, --disable-gallium-egl, --disable-gallium-gbm, --disable-gallium-llvm, --disable-xcb, --enable-driglx-direct, --enable-glx-tls, --enable-glu, --enable-glw, --disable-motif
```

Full log attached just in case.

> **Hakimio said:**
> Last time I checked it didn't work because some of the required extensions were not implemented, but it was long ago and things might have changed since then. You could try launching compiz after the 3d driver installation yourself and you could ask some developers on IRC (freenode server, nouveau channel) if there is any way to get compiz running with nouveau.
I really appropriate the help, thanks Hakimio. How can I give a bean? :) 

I already have some work late because of playing around that issue. Might be optimal to eliminate the issue with a stronger bullet. That's why replacement ATI Radeon's card is on the way to me. With my previous HD4870 setting the setup I like worked fine. I hope ATI haven't broke that yet. Keep your finger crossed than ;)

Still I can test something with Nvidia if any advice (up to Saturaday morning). You are welcome, maybe someone else will use the solution if I succeed.

---

### Post by Hakimio on 2011-10-13
> **tamashumi said:**
> 

I already have some work late because of playing around that issue. Might be optimal to eliminate the issue with a stronger bullet.

If you don't have time to play with the compilation of the latest open source 3d driver, you can just install an older version from ubuntu software repository. The package is called "libgl1-mesa-dri-experimental". 
Anyway, just wondering: what's so bad about the proprietary driver, that you are so desperately trying to get the open source one working?

---

### Post by tamashumi on 2011-10-13
Proprietary driver is limited.

Short story: because I would like to work like I used before GPU change.
[IMG]http://upload.metakmin.net/monitor-setup.gif[/IMG]

This includes Compiz with couple plugins and shortcuts which are real usability goodies.

[Long story]("http://ubuntuforums.org/showthread.php?t=1857961")

I'm desperate because I was like 'challenge accepted' when realized the new card doesn't run the way I need.

---

### Post by Hakimio on 2011-10-18
The guide was updated.

---

### Post by tachibana on 2012-02-01
Can anyone send me Makefile from "http://cgit.freedesktop.org/nouveau/linux-2.6/plain/nouveau/Makefile?h=master-compat". This repository does not respond.

---

### Post by RoarBeast on 2012-02-18
can't load glx because something mismatch
```

[  5701.236] (II) LoadModule: "glx"
[  5701.237] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  5701.237] (II) Module glx: vendor="X.Org Foundation"
[  5701.237]    compiled for 1.9.0, module version = 1.0.0
[  5701.237]    ABI class: X.Org Server Extension, version 4.0
[  5701.237] (EE) module ABI major version (4) doesn't match the server's version (5)
[  5701.237] (II) UnloadModule: "glx"
[  5701.237] (II) Unloading glx
[  5701.237] (EE) Failed to load module "glx" (module requirement mismatch, 0)

```
can someone tell me how to solve this problem?

---

### Post by firekage on 2013-04-17
I would like to ask for Your help - i would like to enable vsync in nouveau. Is it possible? If yes, than how?

---

