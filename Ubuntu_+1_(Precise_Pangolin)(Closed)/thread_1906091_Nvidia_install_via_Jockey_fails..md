---
title: "Nvidia install via Jockey fails."
date: 2012-01-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kyleabaker on 2012-01-08
I'm trying to install the proprietary Nvidia-173 driver via Jockey and it fails to install successfully every time I try. Are there known issues with the Nvidia drivers and Precise at the moment?

I'm really waiting for the 295.09 drivers to be released in a ppa, but I can't seem to get any of them to install at the moment. Any suggestions?

---

### Post by ronacc on 2012-01-08
hand install the 290.10 driver downloaded direct from nvidia I opened a bug on this 2 months ago . [ https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/897681]( https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/897681) . add yourself to it .

edit: the 295.09 will probably work too , I haven't tried it yet though .

---

### Post by kyleabaker on 2012-01-08
> **ronacc said:**
> edit: the 295.09 will probably work too , I haven't tried it yet though .

I'm waiting for 295.09 since it includes a fix for my video card and causes problems with Unity. About installing it by hand, I've downloaded the ".run" package for 295.09, but I'm semi-lost on how to install it.

I must run it as root, but also X must not be running. I'm not sure quiet how to accomplish this.

Am I to enter TTY1 and kill X some how?

---

### Post by ronacc on 2012-01-08
you can reboot to recovery mode and then login to a terminal session , cd to the dir where you have the .run and then run
```
 sudo sh NVIDIA<tab to complete> 
``` select yes to each question except the last one about modifying your xorg.conf .

---

### Post by kyleabaker on 2012-01-08
> **ronacc said:**
> you can reboot to recovery mode and then login to a terminal session , cd to the dir where you have the .run and then run
```
 sudo sh NVIDIA<tab to complete> 
``` select yes to each question except the last one about modifying your xorg.conf .

I rebooted into recovery mode and selected "root" from the menu. Navigated to the installer and ran it, but I was prompted with something along these lines...

> Unable to create directory: /tmp/selfgz473/<some-path-here>. : Read-only file system.

---

### Post by ronacc on 2012-01-08
hmm I see what you mean , I haven't done it that way in awhile you used to be able to select a normal terminal from the menu , I just copy the .run over
from a working install and wait until the boot stops when it can't get to x and install from there , that won't help since you are able to get to desktop . I'll look around and see how to kill x without it just restarting , I forget right now , It will be awhile though I'll be away from the computer for a couple of hrs .

---

### Post by ronacc on 2012-01-08
just thought of this , from the recovery root terminal run ```
 init 3 
``` and  then the  "sud sh ......" .

---

### Post by kyleabaker on 2012-01-08
> **ronacc said:**
> just thought of this , from the recovery root terminal run ```
 init 3 
``` and  then the  "sud sh ......" .

Was hopeful, but I'm still getting the same error.

---

### Post by Pilot6 on 2012-01-08
> **kyleabaker said:**
> I'm waiting for 295.09 since it includes a fix for my video card and causes problems with Unity. About installing it by hand, I've downloaded the ".run" package for 295.09, but I'm semi-lost on how to install it.

I must run it as root, but also X must not be running. I'm not sure quiet how to accomplish this.

Am I to enter TTY1 and kill X some how?
Where did you download this file from?

---

### Post by kyleabaker on 2012-01-08
> **Pilot6 said:**
> Where did you download this file from?

[http://www.nvnews.net/vbulletin/showthread.php?p=2514702]("http://www.nvnews.net/vbulletin/showthread.php?p=2514702")

---

### Post by mc4man on 2012-01-08
Out of curiousity - 
are you first choosing the "remount" option in recovery menu & then from the 2nd recovery menu selecting the root prompt option, ect.?
(the initial recovery menu is read only

---

### Post by Pilot6 on 2012-01-08
Thanks. Downloaded and installed them. A few bugs less ))

---

### Post by kyleabaker on 2012-01-08
> **mc4man said:**
> Out of curiousity - 
are you first choosing the "remount" option in recovery menu & then from the 2nd recovery menu selecting the root prompt option, ect.?
(the initial recovery menu is read only

Thanks for the hint! I've finally installed Nvidia 295.09 successfully and my video card is loving me for it. :D

How to:
[LIST=1]
[*]Download the [Nvidia package]("http://www.nvnews.net/vbulletin/showthread.php?t=122606") appropriate for your system.
[*]Reboot and select Recovery Mode on startup.
[*]Select the option to Remount drives and Read/Write permissions.
[*]Select Root (or Netroot).
[*]Change directory to the Nvidia package that you downloaded.
[*]Run the installer: sudo sh NVIDIA-*
[*]Follow through the installer steps (I noticed a few distro scripts failed, but the installer worked successfully). Make sure to run xconfig as part of the installer when prompted to.
[*]After installer completes, remove the Nouveau xserver module: sudo apt-get purge xserver-xorg-video-nouveau
[*]Restart your machine: sudo shutdown -r now
[*]After starting up normally and logging in, you can adjust your video settings using: sudo nvidia-settings
[*]Logout and log back in and your finished!
[/LIST]

Sounds like a lot, but its really not bad at all. Thanks all who helped with managing to run the installer!

---

### Post by paul_in_london on 2012-01-08
Hmm. Didn't realise that version was out. I'm using the xorg-edgers ppa and the latest available version of nvidia-current from there seems to be 290.10.

I prefer using debs so I thought I'd try installing nvidia-current-updates from here:

[https://launchpad.net/~portis25/+archive/cnav/+build/3055417](https://launchpad.net/~portis25/+archive/cnav/+build/3055417)

but no go:

```
paul@precise-64:~$ sudo dpkg -i ~/Downloads/nvidia-current-updates_295.09-0_amd64.deb 
[sudo] password for paul: 
Selecting previously unselected package nvidia-current-updates.
(Reading database ... 222830 files and directories currently installed.)
Unpacking nvidia-current-updates (from .../nvidia-current-updates_295.09-0_amd64.deb) ...
dpkg: dependency problems prevent configuration of nvidia-current-updates:
 nvidia-current-updates depends on xorg-video-abi-10; however:
  Package xorg-video-abi-10 is not installed.
dpkg: error processing nvidia-current-updates (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 nvidia-current-updates
paul@precise-64:~$
```

EDIT: whereas nvidia-current depends on xorg-video-abi-11:

```
Package: nvidia-current
Source: nvidia-graphics-drivers
Priority: optional
Section: misc
Installed-Size: 179673
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 290.10-0ubuntu1~xedgers~precise1
Recommends: nvidia-settings
Replaces: nvidia-180-modaliases, nvidia-185-modaliases, nvidia-current-modaliases
Provides: xorg-driver-video
Depends: x11-common (>= 1:7.0.0), make, sed (>> 3.0), dkms, linux-libc-dev, libc6-dev, linux-headers-generic | linux-headers, patch, acpid, libc6 (>= 2.2.5), libgcc1 (>= 1:4.1.1), libx11-6, libxext6, libxv1, libxvmc1, zlib1g (>= 1:1.1.4), xorg-video-abi-11, xserver-xorg-core (>= 2:1.10.99.901)
Conflicts: nvidia-180-modaliases, nvidia-185-modaliases, nvidia-current-modaliases
Filename: pool/main/n/nvidia-graphics-drivers/nvidia-current_290.10-0ubuntu1~xedgers~precise1_amd64.deb
Size: 58453546
MD5sum: 17bbbba658e51031d1fcbab0f7f042fc
SHA1: dcd5c62a06fafb1ce3fe19d1202514eff2260f34
Description-en_GB: NVIDIA binary Xorg driver, kernel module and VDPAU library
 The binary driver provide optimized hardware acceleration of OpenGL
 applications via a direct-rendering X Server. AGP, PCIe, SLI, TV-out and
 flat panel displays are also supported.
 .
 This package also includes the source for building the kernel module
 required by the Xorg driver, and provides NVIDIA's implementation of the
 Video Decode and presentation API. The latter enables acceleration for
 GeForce 8 and later series cards for H.264 video.
 .
 GPUs such as GeForce series 6 or newer are supported.
```

so I'm not too sure how nvidia-current relates to nvidia-current-updates.

EDIT2:

Just found this:

[http://askubuntu.com/questions/66548/whats-the-difference-between-the-nvidia-current-and-nvidia-current-updates-pac](http://askubuntu.com/questions/66548/whats-the-difference-between-the-nvidia-current-and-nvidia-current-updates-pac)

but I've only ever used nvidia-current in recent releases.

---

### Post by paul_in_london on 2012-01-12
Still no sign of **nvidia-current** 295.09 from xorg-edgers. This package depends on **xorg-video-abi-11**. 

**nvidia-current-updates** 295.09 is available here:

[https://launchpad.net/~portis25/+arc...+build/3055417](https://launchpad.net/~portis25/+arc...+build/3055417)

but it isn't installable because it depends on **xorg-video-abi-10**. :confused:

I know I could use nvidia's own installer (and I've done that before), but it can mess up the sym links so I'd rather wait for a deb.

---

### Post by kyleabaker on 2012-01-12
I'm still unable to install any of the Nvidia drivers via their deps. They always fail midway through and leave my desktop broken on next startup.

---

### Post by paul_in_london on 2012-01-13
Thought for a second I was about to get the **nvidia-current** upgrade, but no:

```
paul@precise-64:~$ sudo aptitude full-upgrade                                   
The following packages will be upgraded: 
  nvidia-current{b} 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 58.4 MB of archives. After unpacking 1,024 B will be freed.
The following packages have unmet dependencies:
  nvidia-current: **[COLOR="Red"]Depends: xorg-video-abi-10[/COLOR]** which is a virtual package.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     nvidia-current              



Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.

```

The weird thing is, the currently installed version of **nvidia-current** (if you'll pardon the pun) depends on **xorg-video-abi-11**:

```
paul@precise-64:~$ apt-cache show nvidia-current

Package: nvidia-current
Source: nvidia-graphics-drivers
Priority: optional
Section: misc
Installed-Size: 179673
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
**[COLOR="Red"]Version: 290.10-0ubuntu1~xedgers~precise1[/COLOR]**
Recommends: nvidia-settings
Replaces: nvidia-180-modaliases, nvidia-185-modaliases, nvidia-current-modaliases
Provides: xorg-driver-video
Depends: x11-common (>= 1:7.0.0), make, sed (>> 3.0), dkms, linux-libc-dev, libc6-dev, linux-headers-generic | linux-headers, patch, acpid, libc6 (>= 2.2.5), libgcc1 (>= 1:4.1.1), libx11-6, libxext6, libxv1, libxvmc1, zlib1g (>= 1:1.1.4),
 **[COLOR="Red"]xorg-video-abi-11[/COLOR]**, xserver-xorg-core (>= 2:1.10.99.901)
Conflicts: nvidia-180-modaliases, nvidia-185-modaliases, nvidia-current-modaliases
Filename: pool/main/n/nvidia-graphics-drivers/nvidia-current_290.10-0ubuntu1~xedgers~precise1_amd64.deb
Size: 58453546
MD5sum: 17bbbba658e51031d1fcbab0f7f042fc
SHA1: dcd5c62a06fafb1ce3fe19d1202514eff2260f34
Description-en_GB: NVIDIA binary Xorg driver, kernel module and VDPAU library
 The binary driver provide optimized hardware acceleration of OpenGL
 applications via a direct-rendering X Server. AGP, PCIe, SLI, TV-out and
 flat panel displays are also supported.
 .
 This package also includes the source for building the kernel module
 required by the Xorg driver, and provides NVIDIA's implementation of the
 Video Decode and presentation API. The latter enables acceleration for
 GeForce 8 and later series cards for H.264 video.
 .
 GPUs such as GeForce series 6 or newer are supported.
 .
 See /usr/share/doc/nvidia-current/README.txt.gz for a complete list of
 supported GPUs and PCIIDs

```

---

### Post by kyleabaker on 2012-01-13
Ah, so I'm unable to install nvidia drivers due to a dependency on abi 10 rather than abi 11?

---

### Post by paul_in_london on 2012-01-13
> **kyleabaker said:**
> Ah, so I'm unable to install nvidia drivers due to a dependency on abi 10 rather than abi 11?

Yep. And I carelessly thought ok, I'll purge nvidia-current then reinstall it...except I couldn't until I temporarily purged xorg-edgers ppa. Now after re-enabling xorg-edgers I've also got various other packages held back that I didn't have held back before because of modified dependencies I suppose.

Doh!

At least I've got my previous version of nvidia-current back I suppose.

---

### Post by effenberg0x0 on 2012-01-13
Is this the return of one of those cases in which this was needed:

$ sudo nano /etc/X11/xorg.conf
```

Section "ServerFlags"
    Option "IgnoreABI" "true"
EndSection

```
I mean, if you manage to --force the install, it would only run with that server flag?
I run no non-default PPAs, so I have no way to test it.

---

### Post by xyzzyman on 2012-01-13
> **kyleabaker said:**
> Thanks for the hint! I've finally installed Nvidia 295.09 successfully and my video card is loving me for it. :D

How to:
[LIST=1]
[*]Download the [Nvidia package]("http://www.nvnews.net/vbulletin/showthread.php?t=122606") appropriate for your system.
[*]Reboot and select Recovery Mode on startup.
[*]Select the option to Remount drives and Read/Write permissions.
[*]Select Root (or Netroot).
[*]Change directory to the Nvidia package that you downloaded.
[*]Run the installer: sudo sh NVIDIA-*
[*]Follow through the installer steps (I noticed a few distro scripts failed, but the installer worked successfully). Make sure to run xconfig as part of the installer when prompted to.
[*]After installer completes, remove the Nouveau xserver module: sudo apt-get purge xserver-xorg-video-nouveau
[*]Restart your machine: sudo shutdown -r now
[*]After starting up normally and logging in, you can adjust your video settings using: sudo nvidia-settings
[*]Logout and log back in and your finished!
[/LIST]

Sounds like a lot, but its really not bad at all. Thanks all who helped with managing to run the installer!

Another tip is to always leave the .run file there. Since you are installing manually instead of a .deb, you will have to reinstall whenever the kernel updates. Much easier to have the .run available.

---

### Post by effenberg0x0 on 2012-01-13
> **xyzzyman said:**
> Another tip is to always leave the .run file there. Since you are installing manually instead of a .deb, you will have to reinstall whenever the kernel updates. Much easier to have the .run available.

Good tip to keep the installer at hand. I usually run "sudo ./NVIDIA-Linux-x86_64-290*run -K" (to just quickly build the kernel module, since the driver files are already there) and eventually use the --update function (which no one seems to ever recommend, don't know why - Maybe it has some problem I'm not aware of, but IMO it works ok).

---

### Post by kyleabaker on 2012-01-14
Thanks guys! Both very good tips!

---

