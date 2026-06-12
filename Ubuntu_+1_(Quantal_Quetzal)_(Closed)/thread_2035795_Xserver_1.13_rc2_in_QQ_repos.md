---
title: "Xserver 1.13 rc2 in QQ repos"
date: 2012-07-31
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-07-31
There is a new xserver in the Qq repos now.
Xserver 1.13 rc2 can be found here:

[https://launchpad.net/ubuntu/quantal/+source/xorg-server/2:1.12.99.902-0ubuntu1](https://launchpad.net/ubuntu/quantal/+source/xorg-server/2:1.12.99.902-0ubuntu1)

However, in order to install it successfully, you need to have all input and video drivers built against the new abi bump:
- xorg-input-abi-18
- xorg-video-abi-13

These are not yet available.

---

### Post by dino99 on 2012-07-31
the latest 1.12.99.902 into the archive wants to remove nvidia-current right now

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1031243](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1031243)

---

### Post by Harry33 on 2012-07-31
> **dino99 said:**
> the latest 1.12.99.902 into the archive wants to remove nvidia-current right now

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1031243](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1031243)

This is not a bug actually.
It will remove all xserver1.12 input and video drivers, including the proprietary drivers, if they are not built against the new ABI.
These new drivers are not yet available, so this is more a timing issue than a bug.

In other words, current nvidia-current depends on xorg-video-abi-12, while it should depend on xorg-video-abi-13 in order to work with xserver1.13 branch.

---

### Post by dino99 on 2012-07-31
> **Harry33 said:**
> This is not a bug actually.
It will remove all xserver1.12 input and video drivers, including the proprietary drivers, if they are not built against the new ABI.
These new drivers are not yet available, so this is more a timing issue than a bug.

In other words, current nvidia-current depends on xorg-video-abi-12, while it should depend on xorg-video-abi-13 in order to work with xserver1.13 branch.

Agree but then they should stay into built queue (pending) instead of been publicated.

---

### Post by dext on 2012-07-31
the Nvidia Drivers you need for 1.13 [ftp://download.nvidia.com/XFree86/Linux-x86_64/304.30/](ftp://download.nvidia.com/XFree86/Linux-x86_64/304.30/) & [ftp://download.nvidia.com/XFree86/Linux-x86/304.30/](ftp://download.nvidia.com/XFree86/Linux-x86/304.30/)

---

### Post by Harry33 on 2012-08-01
The correct nvidia-current_304.30 can be downloaded from xorg-edgers PPA for QQ.
Also the necessrary other drivers (input and video) can be obtained from there.
And of course a git version of xserver1.13.

There is, however, something worng about the 3D I think.
I cannot login to gnome-shell. It crashes and system returns to the login screen.
However, gnome-panel (classic) works just fine, referring an issue with 3 D.

Just opened a new thread for Xorg-edgers PPA.

---

### Post by kansasnoob on 2012-08-01
It would seem that someone got a bit punch-happy when figuring out this transition :)

For more than 48 hours now I get:

```
The following packages will be REMOVED:
  ubuntu-desktop xorg xserver-xorg xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-geode
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau
  xserver-xorg-video-openchrome xserver-xorg-video-r128 xserver-xorg-video-s3
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion
  xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware
The following NEW packages will be installed:
  libframe6 libgeis1 libgrail5 libimobiledevice3 linux-headers-3.5.0-7
  linux-headers-3.5.0-7-generic linux-image-3.5.0-7-generic
  linux-image-extra-3.5.0-7-generic
The following packages have been kept back:
  libexttextcat-data libexttextcat0
The following packages will be upgraded:
  binfmt-support ca-certificates-java folks-common ginn gir1.2-gtk-2.0
  gir1.2-gtksource-3.0 gir1.2-rb-3.0 gir1.2-ubuntuoneui-3.0 gnome-contacts
  gnome-session gnome-session-bin gnome-session-common gnome-session-fallback
  gtk2-engines-pixbuf gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons
  gvfs-fuse gvfs-libs hwdata ibus ibus-gtk ibus-gtk3 libavformat53 libburn4
  libcairo-perl libcogl-common libcogl-pango0 libcogl9 libfolks-eds25
  libfolks-telepathy25 libfolks25 libgail-common libgail18 libgdata-common
  libgdata13 libgrip0 libgtk-vnc-2.0-0 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libgtksourceview-3.0-0 libgtksourceview-3.0-common
  libgvnc-1.0-0 libibus-1.0-0 libisofs6 libkpathsea6 libnm-glib-vpn1
  libnm-glib4 libnm-util2 libnux-3.0-0 libnux-3.0-common libpango-perl libpci3
  libpostproc52 libraw5 librhythmbox-core6 libsdl1.2debian libshout3
  libswscale2 libubuntuoneui-3.0-1 libunity-2d-private0 libunity-core-6.0-5
  linux-generic linux-headers-generic linux-headers-generic-pae
  linux-image-generic linux-libc-dev network-manager nux-tools pciutils
  python-dirspec python-ibus python-mako python-simplejson
  python-ubuntu-sso-client python-ubuntuone-control-panel
  python-ubuntuone-storageprotocol rhythmbox rhythmbox-data rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins rhythmbox-ubuntuone sni-qt
  ubuntu-docs ubuntu-minimal ubuntu-sso-client ubuntu-sso-client-qt
  ubuntu-standard ubuntuone-control-panel ubuntuone-control-panel-common
  ubuntuone-control-panel-gtk ubuntuone-control-panel-qt unity unity-2d
  unity-2d-common unity-2d-launcher unity-2d-panel unity-2d-places
  unity-2d-shell unity-2d-spread unity-common unity-services update-notifier
  update-notifier-common usb-creator-common usb-creator-gtk xserver-common
  xserver-xorg-core xserver-xorg-input-mouse
115 upgraded, 8 newly installed, 27 to remove and 2 not upgraded.
Need to get 75.4 MB of archives.

```

I may try a new daily soon to see what happens ;)

Maybe they spiked the water cooler at Canonical :lolflag:

---

### Post by cariboo on 2012-08-01
@kansasnoob, I'm getting the same thing, I intend on using:

```
sudo aptitude safe-upgrade
```

until the dependencies are fixed. :D

---

### Post by Harry33 on 2012-08-01
One good solution to get forward is to disable proposed repository first and only then do the upgrade. Xserver 1.13 is in the proposed repo.

---

### Post by kansasnoob on 2012-08-01
That last comment was meant to be totally tongue-in-cheek :D

You just seldom see a 48 hour+ lapse before all the bits-n-pieces get uploaded to the repos. It's no big deal.

I'm hoping this bug will be fixed:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/988290](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/988290)

It's frustrating ATM ;)

---

### Post by VinDSL on 2012-08-01
> **Harry33 said:**
> There is a new xserver in the Qq repos now.
Oh, joy!  Thanks, harry!!!

I totally FUBAR'ed 12.10...

NextStep:  "sudo ppa-purge xorg-edgers"  LoL! :D

BBL

---

### Post by Harry33 on 2012-08-02
> **VinDSL said:**
> Oh, joy!  Thanks, harry!!!

I totally FUBAR'ed 12.10...

NextStep:  "sudo ppa-purge xorg-edgers"  LoL! :D

BBL

Gnome classic still works with the new xserver 1.13 and nvidia-current.
Unity and Gnome-shell does not.

---

### Post by VinDSL on 2012-08-02
> **Harry33 said:**
> Gnome classic still works with the new xserver 1.13 and nvidia-current.
Unity and Gnome-shell does not.
I'm stuck in ABI dependency hell.  LoL! :D

I cannot get past Plymouth (in the gui).  It either sticks or black screens on me.

I've got a foot in both camps (1.12 & 1.13) and apt-get and aptitude are confused.

I haven't discovered the right combination in CLI yet, to wash, rinse, and restyle xserver core and nvidia-current (to the same version).

My installation is reporting one version -- the kernel module is reporting another e.g. there is an epic mismatch, and apt-get/aptitude don't know what to do.  So, they do nothing.

This is fun!  I'll chart the proper course sooner-or-later... :)

---

### Post by Harry33 on 2012-08-02
> **VinDSL said:**
> I'm stuck in ABI dependency hell.  LoL! :D

I cannot get past Plymouth (in the gui).  It either sticks or black screens on me.

I've got a foot in both camps (1.12 & 1.13) and apt-get and aptitude are confused.

I haven't discovered the right combination in CLI yet, to wash, rinse, and restyle xserver core and nvidia-current (to the same version).

My installation is reporting one version -- the kernel module is reporting another e.g. there is an epic mismatch, and apt-get/aptitude don't know what to do.  So, they do nothing.

This is fun!  I'll chart the proper course sooner-or-later... :)

Why don't you just remove (from the console) both xserver packages and its driver packages including nvidia-current. All it does is that you od not have a desktop. That's all.
Then with wget (from console) download the correct ones and install them at the same time (manually with dpkg).
When installing new xserver or new drivers, I usually keep the old versions already in advance downloaded and ready for a recovery, in case of trouble.

---

### Post by VinDSL on 2012-08-02
> **Harry33 said:**
> Why don't you just remove (from the console) both xserver packages and its driver packages including nvidia-current.[...]

Then with wget (from console) download the correct ones and install them at the same time (manually with dpkg).
Easier said than done...

I cannot find the "correct ones" to install, because they delete them from the PPA as soon as the "new ones" arrive.  :)

In the meantime, I'll just putz around and see if some upgrade or another takes care of it.

---

### Post by VinDSL on 2012-08-02
Alrighty then...

I'm up again.  Not sure how I did it, or what's installed.  LoL!

nvidia-current is now 304.30 - xserver-core 12.99 something-or-another.

I'll go do some investigating...  :)

---

### Post by VinDSL on 2012-08-02
Okay, I did some housekeeping.  Here's where I stand...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-2-aug-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-2-aug-2012-1.png")[/INDENT]


```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.5.20 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch" && apt-cache policy xserver-xorg-core | grep Installed && echo"Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xse~ VinDSL Unity Debug Script 12.5.20 (vindsl.com) ~-xorg-core | grep Installed &&Current Date/Time: Thu Aug  2 18:29:02 MST 2012
Distro Release: Ubuntu quantal (development branch)
**[COLOR="DarkRed"]Kernel Release: Linux 3.5.0-7-generic[/COLOR]**
Unity Release: unity 6.0.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
**[COLOR="DarkRed"]OpenGL version string:  2.1.2 NVIDIA 304.30[/COLOR]**

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

[B][COLOR="DarkRed"]Xserver Xorg Core Branch
  Installed: 2:1.12.99.903+git20120801.afa53fe7-0ubuntu0ricotz[/COLOR][/B]

vindsl@Zuul:~$ 

```


Survived a reboot, and...

You aren't going to believe this, but I swear it's the truth!

My Home/Pictures folder disappeared about 2-3 months ago.  And, I didn't have a backup.  I lost a couple of years of graphics, wallpapers, and so forth.  I was mortified!

Now (gulp) they are all back again.  :D

Seriously?!?!?!?  You gotta be kidding...

Heh!  This has got to be the weirdest thing I've ever experienced in all of Ubudom...

---

### Post by Harry33 on 2012-08-03
Now what the ....

You have the xorg-edgers PPA enabled. From there you are using nvidia-current, xserver 1.13 and the git version of mesa and drm too.

So, it seems the 3D works now.
Would nvidia-current after all support the 3D.
Could this be due to mesa and drm?
I have to check it out.

Do you have this issue (from xorg-edgers) with unity?
> July 13th: Mesa currently has problems with unity where the launcher  icons are invisible, it's suggested to hold mesa back to the 0529  version, stop using this PPA, or use another session such as gnome or  unity-2d until it is fixed.

---

### Post by VinDSL on 2012-08-03
> **Harry33 said:**
> Now what the ....

Do you have this issue (from xorg-edgers) with unity?
Heh!  I must be on the right path.  :D

I judge, the only reason this setup is working for me is because I'm running LXDE/Openbox on top of Ubu 12.10 3D.

Put another way, 3D so called is working fine, but Unity/GS aren't.

The only app I've found that doesn't work is Firefox.  When I try to load Fx, it spits me out to the LightDM login menu.

After several attempts to load Fx in LXDE/Openbox, I decided to try Unity 3D.  Unity starts to load, but splits me back to the login menu.

Gnome3 aka GS does the same thing, e.g. starts to load, then spits me out to login.

LXDE, sans Firefox, continues to work just fine.  ;)

---

### Post by paul_in_london on 2012-08-03
> **VinDSL said:**
> Heh!  I must be on the right path.  :D

I judge, the only reason this setup is working for me is because I'm running LXDE/Openbox on top of Ubu 12.10 3D.

Put another way, 3D so called is working fine, but Unity/GS aren't.

The only app I've found that doesn't work is Firefox.  When I try to load Fx, it spits me out to the LightDM login menu.

After several attempts to load Fx in LXDE/Openbox, I decided to try Unity 3D.  Unity starts to load, but splits me back to the login menu.

Gnome3 aka GS does the same thing, e.g. starts to load, then spits me out to login.

LXDE, sans Firefox, continues to work just fine.  ;)

Yep, in gnome-classic and lxde/openbox (two separate 64 bit installs) no version of FF wants to play ball, but all my other browsers seem to work! Definitely seems to be related to this xserver upgrade (1.13 rc2) and possibly the nvidia-current driver, but other than that I haven't really got anything to go on.

---

### Post by Harry33 on 2012-08-05
Just tested that not even the newest beta release of nvidia-current (304.32) works with 3D desktops (like gnome-shell) if xserver 1.13 branch is used (like 1.12.99.-*).

---

### Post by flipper T on 2012-08-05
hi

sorry if i am being a little slow, but to clarify, is the current advice to wait & not to install nvidia drivers, regardless of their source?

i upgrade from 12.04, but i must have chosen wrong option as nvidia drivers gone & now using nouveau.

ps has there been any official notification when this will be resolved.

pps i know its alpha.

---

### Post by VinDSL on 2012-08-05
> **flipper T said:**
> sorry if i am being a little slow, but to clarify, is the current advice to wait & not to install nvidia drivers, regardless of their source?
Well, from my perspective...  It all depends on your tolerance to pain.

Xserver 1.13 & nvidia-current 304.30/304.32 has been a major PITA so far, but that's why I got into "testing".  So, I'm happy as a lark. I couldn't even boot into Ubu 12.10 for 2 days. It was wonderful. I was dancing on the keyboard so much, I don't even know how I fixed it. :)

If, however, you don't enjoy hitting yourself in the head with hammers, I would strongly suggest holding off on upgrading xserver, nvidia-current, kernel 3.6, and so forth, and so on.

As harry stated, above, Unity & GS are still borked. So, if you run those DEs, you'll be working from CLI, not your desktop.  Then, again, some ppl prefer to use the command line interface.

Seriously, I judge that most ppl will find xserver 1.13 & nvidia-current 304.32 to be a living hell (at this stage).  But, to each his own.  ;)

---

