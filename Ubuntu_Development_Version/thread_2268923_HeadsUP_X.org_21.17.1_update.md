---
title: "HeadsUP: X.org 2:1.17.1 update"
date: 2015-03-12
forum: Ubuntu Development Version
---

### Post by zika on 2015-03-12
```
The following packages will be REMOVED:  xserver-xorg-video-all xserver-xorg-video-ati xserver-xorg-video-intel xserver-xorg-video-modesetting xserver-xorg-video-nouveau xserver-xorg-video-qxl xserver-xorg-video-radeon
The following packages will be upgraded:
  x11-common xorg xserver-common xserver-xephyr xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-openchrome xserver-xorg-video-r128 xserver-xorg-video-s3
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware xwayland
23 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
Need to get 3975 kB of archives.
After this operation, 4978 kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.
```Reason:```
The following packages have unmet dependencies:
 xserver-xorg-core : Breaks: xserver-xorg-video-modesetting (< 0.10) but 0.9.0-1build1 is installed.
 xserver-xorg-video-qxl : Depends: xorg-video-abi-18 which is a virtual package.
 xserver-xorg-video-intel : Depends: xorg-video-abi-18 which is a virtual package.
 xserver-xorg-video-ati : Depends: xorg-video-abi-18 which is a virtual package.
 xserver-xorg-video-radeon : Depends: xorg-video-abi-18 which is a virtual package.
 xserver-xorg-video-modesetting : Depends: xorg-video-abi-18 which is a virtual package.
 xserver-xorg-video-nouveau : Depends: xorg-video-abi-18 which is a virtual package.
```Proposed-Vivid.

---

### Post by dino99 on 2015-03-12
might be ok now, as some packages was having the 'pending' status for a while

i does not get these errors, but  the meta-packages are also removed to let me choose only what i need

---

### Post by zika on 2015-03-12
> **9d9 said:**
> might be ok now, as some packages was having the 'pending' status for a while
i does not get these errors, but  the meta-packages are also removed to let me choose only what i needNo, it is not, yet...
Yes, only autodetection packages are on standby waiting for xorg-video-abi-nn (in this case nn=18) as usual. I was just giving HU for those who use dist-upgrade and have forced &#8222;yes&#8220; in their scripts.
Yes, I do know there are such here... ;)
For example:> [COLOR=#333333][FONT=Ubuntu]Users of Rage, Mach, or Radeon boards may remove this package only if[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu] they use Driver "r128", "mach64", or "radeon" in /etc/X11/xorg.conf[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu] instead of relying on autodetection.[/FONT][/COLOR](from xserver-xorg-video-ati documents...)

---

### Post by ventrical on 2015-03-12
Thanks for heads up. It worked ok on my kubuntu install with nvidia. Haven't tried my other boxes yet/


Regards..

---

### Post by harry332 on 2015-03-13
You must remove xserver-xorg-video-modesetting. It is no longer supported.
The old version has the wrong ABI and it cannot be kept installed.
This is the reason:
xorg-server (2:1.17.1-0ubuntu1) vivid; urgency=medium

  * Merge with 1.17 branch.
    - ABI bumped.
    - Patches refreshed.
    - Modesetting moved to xorg-server.

---

### Post by zika on 2015-03-13
> **harry332 said:**
> You must remove xserver-xorg-video-modesetting. It is no longer supported.
The old version has the wrong ABI and it cannot be kept installed.
This is the reason:
xorg-server (2:1.17.1-0ubuntu1) vivid; urgency=medium

  * Merge with 1.17 branch.
    - ABI bumped.
    - Patches refreshed.
    - Modesetting moved to xorg-server.Yes, modesetting is gone but that is not enough yet to pull full-upgrade.

Update&#8321; (Idle for stray minute or so so...): To clarify: Driven by experience from previous U+1 cycles i felt oblidged to give HU for those who might get into trouble with this upgrade. Most of (detection/meta)packages affected with this I even do not have installed on my machines as documented couple of U+1 ago... I do use /etc/X11/xorg.conf still so I'm kind-of-safe... ;)
Update&#8322; (-" "-): There are nice news: Before, if You tried to remove xserver-xorg-video-* You would get ubuntu-desktop, xorg... removed. Now, after this upgrade, You can safely remove all xserver-xorg-video-* and maintain Your /etc/X11/xorg.conf control over X... This update is not to be taken as suggestion, just as a report... ;)
Update&#8323; (-" "- a.k.a. iddle fingers): So, if You allow removal of packages listed ((as) above) You can go on with dist-upgrade (not waiting for virtual xorg-video-abi-18) and, after that, (re)install xserver-xorg-video-all and Bob is Your uncle and everything is new and in its place. ;)
Update&#8324;: I'm very impressed with the fact that dependencies are now rearranged in such a way that this whole reinstall was possible. Hat down for developers.

---

### Post by Cavsfan on 2015-03-13
Thanks for the heads up. I updated some xorg stuff earlier but now I see it wants to dist-upgrade a bunch of xorg stuff and that is the version it would go to.
I don't mess with proposed so this is in the normal updates.

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy xserver-xorg-core
xserver-xorg-core:
  Installed: 2:1.16.2.901-1ubuntu4
  Candidate: 2:1.17.1-0ubuntu2
  Version table:
     2:1.17.1-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/main amd64 Packages
 *** 2:1.16.2.901-1ubuntu4 0
        100 /var/lib/dpkg/status
```

 Think I'll hold off on that for a while until I hear it's ok.

Or did you say it was OK?

---

