---
title: "Linux 3.2-rc5 released"
date: 2011-12-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-12-10
Here is the release announcement:
[https://lkml.org/lkml/2011/12/9/419](https://lkml.org/lkml/2011/12/9/419)

Linus writes:

> It's been a bit over a week, and I'm sad to report that -rc5 is bigger
(at least in number of commits - most of the commits are pretty small,
so it's possible that the *diff* ends up being smaller, but I didn't
check) than both -rc2 and -rc4 were.

---

### Post by JMB74 on 2011-12-10
[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-precise.git;a=commitdiff;h=084b7172c1281a55f39db452d71234dae94a85a8](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-precise.git;a=commitdiff;h=084b7172c1281a55f39db452d71234dae94a85a8)

*[COLOR=DarkGreen]* Start new release, Bump ABI, rebase to 3.2-rc5[/COLOR]*

A new kernel rebased to RC5 being prepared, so hopefully will see that in the precise repos before long.

---

### Post by JMB74 on 2011-12-10
> **JMB74 said:**
> A new kernel rebased to RC5 being prepared, so hopefully will see that in the precise repos before long.

Now building.

[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-4.10](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-4.10)

---

### Post by paul_in_london on 2011-12-10
Yes, just installed it from ppa kernel mainline. :)

---

### Post by VinDSL on 2011-12-10
Can you tell, I'm anxious to see if it works (on my i686 install)?!?!?  LoL!  :D


[INDENT]**Ubuntu 12.04 [COLOR="DarkOrange"] / [/COLOR] Conky 1.8.1-5 [COLOR="DarkOrange"] / [/COLOR] Lua [COLOR="DarkOrange"] / [/COLOR] Unity [COLOR="DarkOrange"] / [/COLOR] Banshee [COLOR="DarkOrange"] / [/COLOR]Custom iGoogle Weather API**  [SIZE="1"]**(Click image to expand)**[/SIZE]

[[IMG]http://vindsl.com/images/vindsl-desktop-10-dec-2011-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-10-dec-2011-2.png")[/INDENT]

---

### Post by VinDSL on 2011-12-10
w00t!

Build uploading to server now...

**Edit**

Dang!

```
Finished 6 minutes ago ([COLOR="DarkRed"]**took 8 hours, 16 minutes, 51.3 seconds**[/COLOR]) 
```

Probably all the refreshes I was doing!  :D

Alrighty, then.  I'll download it and see what happens.

If this doesn't work, I think I'll do a fresh install...

---

### Post by VinDSL on 2011-12-10
**Hallelujah!!!**

[INDENT]**Ubuntu 12.04 [COLOR="DarkOrange"] / [/COLOR] Conky 1.8.1-5 [COLOR="DarkOrange"] / [/COLOR] Lua [COLOR="DarkOrange"] / [/COLOR] Unity [COLOR="DarkOrange"] / [/COLOR] Banshee [COLOR="DarkOrange"] / [/COLOR]Custom iGoogle Weather API**  [SIZE="1"]**(Click image to expand)**[/SIZE]

[[IMG]http://vindsl.com/images/vindsl-desktop-10-dec-2011-3(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-10-dec-2011-3.png")[/INDENT]


**Early Christmas Gift**...  :D

```
vindsl@Zuul:~$ echo && date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && echo && /usr/lib/nux/unity_support_test -p -f || echo && dpkg -s mesa-utils && echo && lspci -nn | grep Ethernet && echo

Sat Dec 10 19:30:18 MST 2011
Ubuntu precise (development branch)
Linux 3.2.0-4-generic
unity 4.24.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 285.05.09

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

02:01.0 Ethernet controller [0200]: Intel Corporation 82547EI Gigabit Ethernet Controller [8086:1019]

vindsl@Zuul:~$ 

```

---

### Post by VinDSL on 2011-12-10
Oh, my...

This is nice!  Really nice!!!

I play a Flash game on FaceBook called "Cafe World", which is V resource-intensive.

This machine (normally) drags, shakes, and stutters when playing CW, but it's a totally different experience now.

Heh!  Never seen a kernel update make this much difference.

Hope it survives a reboot... Haven't tried that yet.

Think I'll enjoy it for a while, before attempting a cold boot. :)

---

### Post by VinDSL on 2011-12-11
Two Hours Later...

Unity survived a cold boot, but Gnome Shell wasn't as fortunate.  LoL!

Put another way, Unity is shutting down & rebooting normally, but Gnome Shell has no network connection, after login, and it hangs during shut down -- same thing Unity was doing before.

Hrm...

Anyway, it's closer to being fixed.  ;)

---

### Post by donniezazen on 2011-12-11
[SIZE="3"]It seems like power regression issues might go away pretty soon.[/SIZE]

---

### Post by VinDSL on 2011-12-12
Hrm...

I'm having the same network/hang on shutdown prob off n' on -- only less often now -- about 50/50 chance of network working on boot.

I think I'll start a separate thread on this.

When it happened this morning, on first boot, I did a little forensics in cli, and got this:

```
ERROR:root:Could not find def gateway info in /proc 
ERROR:root:Could not find default gateway by running route 
```

I remember this years ago.  Seems like a regression...

---

### Post by dino99 on 2011-12-12
have dropped nm & now use wicd (less headaches :))

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635)

---

### Post by VinDSL on 2011-12-12
> **dino99 said:**
> have dropped nm & now use wicd (less headaches :))

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635)
Thanks, Dino!!!  Worked a treat!

Couldn't get 3.2.0-4 to boot this morning (no network, hung on shutdown).  Tried 5-6 times.  Failed on every attempt.

I installed wicd -- removed network-manager (in that order).

Network app indicator is missing now, from the panel, but I cold/warm booted this machine several times, and the network/shutdown worked each time.  w00t!

Hopefully, they'll get this fixed, once and for all... but this is a GREAT workaround, in the meantime!

Thanks, again!  ;)

---

### Post by Harry33 on 2011-12-12
> **VinDSL said:**
> Thanks, Dino!!!  Worked a treat!

Couldn't get 3.2.0-4 to boot this morning (no network, hung on shutdown).  Tried 5-6 times.  Failed on every attempt.

I installed wicd -- removed network-manager (in that order).

Network app indicator is missing now, from the panel, but I cold/warm booted this machine several times, and the network/shutdown worked each time.  w00t!

Hopefully, they'll get this fixed, once and for all... but this is a GREAT workaround, in the meantime!

Thanks, again!  ;)

Actually you still have a number of netwoprk manager libraries installed, needed elsewhere:
- gir1.2-networkmanager-1.0 (gnome-shell)
- libnm-glib4 (gnome-control-center, gnome-shell)
- libnm-gtk-common (gnome-control-center)
- libnm-gtk0 (gnome-control-center)
- libnm-util2 (gnome-control-center, gnome-shell)

---

### Post by ptn107 on 2011-12-12
Just fetched it and built it myself.  So far no problems.  Time to upload.

deb [http://ppa.launchpad.net/ptn107/ppa/ubuntu](http://ppa.launchpad.net/ptn107/ppa/ubuntu) oneiric main

---

### Post by VinDSL on 2011-12-13
> **Harry33 said:**
> Actually you still have a number of netwoprk manager libraries installed, needed elsewhere:
- gir1.2-networkmanager-1.0 (gnome-shell)
- libnm-glib4 (gnome-control-center, gnome-shell)
- libnm-gtk-common (gnome-control-center)
- libnm-gtk0 (gnome-control-center)
- libnm-util2 (gnome-control-center, gnome-shell)
Yep!

There's a vpn library in there too...

As long as I have a network connection (and can shutdown this machine at night) I'll live without network-manager for a while.

I'm sure they'll patch it sooner or later.  They always do.  ;)

---

### Post by zika on 2011-12-13
Mainline is a bit quiet these days...?

---

### Post by VinDSL on 2011-12-15
[COLOR="DarkOrange"]_**Update - 2 days later (an eternity in "dev release years")**_
[/COLOR]
Just wanted to remark...

I've cold booted/warm booted/upgraded this machine several times, in the past 2 days, and it's behaved admirably since switching from network-manager to wicd.

Thus, I think we've found the culprit!

Many thanks to dino99...  ;)

---

### Post by dino99 on 2011-12-15
> **VinDSL said:**
> [COLOR="DarkOrange"]_**Update - 2 days later (an eternity in "dev release years")**_
[/COLOR]
Just wanted to remark...

switching from network-manager to wicd.

Thus, I think we've found the culprit!

Many thanks to dino99...  ;)

I'm pleased too :)
but still wonder why plymouth, randomly, show me that weird message about: waiting network configuration (even with wicd). This happen not so often but.

---

### Post by effenberg0x0 on 2011-12-15
> **dino99 said:**
> I'm pleased too :)
but still wonder why plymouth, randomly, show me that weird message about: waiting network configuration (even with wicd). This happen not so often but.

@Dino I could only get 100% rid of it by:

sudo apt-get remove --purge network-manager network-manager-gnome modem-manager

Fixing my /etc/network/interfaces and /etc/resolv.conf manually:
address 192.168.1.101
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1

resolv.conf was empty after removing network-manager. I added the network DNS plus other I use (Google, OpenDNS)

Curiously, on the leftovers from network-manager, one entry in  /etc/network/interfaces was wrong (network 192.168.0.0). Actually the network parameter isn't even needed if you provide the other ones. Then the boot process got fast again.

Check for network-manager leftovers in these files, there probably is something wrong there.

---

### Post by Harry33 on 2011-12-16
There is a kernel update in Precise repos: 3.2.0-5.11
Here:
[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-5.11](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-5.11)
[FONT=monospace]
[/FONT]> 
[ Upstream Kernel Changes ]
* rebase to upstream 55b02d2f
-- Leann Ogasawara <email address hidden>   Mon, 12 Dec 2011 07:08:10 -0800


---

### Post by VinDSL on 2011-12-16
> **Harry33 said:**
> There is a kernel update in Precise repos: 3.2.0-5.11
Here:
[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-5.11](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-5.11)
Booted up just fine.

Thanks, Harry!

---

### Post by VinDSL on 2011-12-17
**Linux 3.2-rc6**...

> Mainline Build v3.2-rc6
 
The mainline build for v3.2-rc6 is now complete and available at the URL
below:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc6-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc6-precise/)

See the CHANGES file for the list of changes from the previous version:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc6-precise/CHANGES](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc6-precise/CHANGES)

Note that these builds do not contain any Ubuntu specific patches and
are not supported.

Kernel Team

-- 
kernel-team mailing list
[email]kernel-team@lists.ubuntu.com[/email]
[https://lists.ubuntu.com/mailman/listinfo/kernel-team](https://lists.ubuntu.com/mailman/listinfo/kernel-team)

I'm sticking with Linux 3.2.0-5.11 precise, for now... working great!  ;)

---

### Post by dino99 on 2011-12-17
Thanks Vince

so many bug fixes into the changelog; i enjoy such release. Hopes we get it with the ubuntu tweaks in the early next week.

---

### Post by paul_in_london on 2011-12-17
> **VinDSL said:**
> **Linux 3.2-rc6**...



I'm sticking with Linux 3.2.0-5.11 precise, for now... working great!  ;)

Yes, I just discovered that 3.2-rc6 has arrived in ppa kernel mainline so I'm using that now. :)

---

