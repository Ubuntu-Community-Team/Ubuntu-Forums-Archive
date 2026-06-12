---
title: "Kernel 3.4 released"
date: 2012-05-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jfernyhough on 2012-05-20
Kernel.org just announced the release of 3.4.

Yay?

(I'm still waiting for a working fglrx patch. :()

---

### Post by dino99 on 2012-05-21
it might not have much difference compared to the latest rc; and still not proposed into "source" or kernel-ppa.

---

### Post by Yellow Pasque on 2012-05-21
> **jfernyhough said:**
> (I'm still waiting for a working fglrx patch. :()
It should come soon. Just keep watching upstream and following your bug 993427 :) : [http://ati.cchtml.com/show_bug.cgi?format=multiple&id=495](http://ati.cchtml.com/show_bug.cgi?format=multiple&id=495)

---

### Post by Harry33 on 2012-05-22
New 3.4.0-3.7 (final 3.4.0) is in repos now.
Here:
[https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-3.7](https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-3.7)

There is one major change in those builds now:
* [Config] drop the virtual flavour in favour of a split generic et al

So, no virtual flavour, and the package
linux-image-3.4.0-*-generic has been split into these two:
- linux-image-3.4.0-3-generic
- linux-image-extra-3.4.0-3-generic

This to remind those installing the kernel manually without meta packages
(from linux-meta, package linux-image). Meta packages are not ready yet. Will be soon.

---

### Post by jppr on 2012-05-22
> **Harry33 said:**
> New 3.4.0-3.7 (final 3.4.0) is in repos now.
Here:
[https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-3.7](https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-3.7)

There is one major change in those builds now:
* [Config] drop the virtual flavour in favour of a split generic et al

So, no virtual flavour, and the package
linux-image-3.4.0-*-generic has been split into these two:
- linux-image-3.4.0-3-generic
- linux-image-extra-3.4.0-3-generic

This to remind those installing the kernel manually without meta packages
(from linux-meta, package linux-image). Meta packages are not ready yet. Will be soon.

And this kernel is broken, I was black screen when I install that kernel...

---

### Post by zika on 2012-05-22
3.4.0-3.7 is alive... ;)

---

### Post by VinDSL on 2012-05-22
> **zika said:**
> 3.4.0-3.7 is alive... ;)
Indeed!  :)

```
vindsl@Zuul:~$ uname -a
Linux Zuul 3.4.0-3-generic #7-Ubuntu SMP Mon May 21 20:37:25 UTC 2012 i686 i686 i686 GNU/Linux
```

```
vindsl@Zuul:~$ echo && echo "~ VinDSL 12.5.22 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch" && apt-cache policy xserver-xorg-core | grep Installed && echo

~ VinDSL 12.5.22 (vindsl.com) ~
Current Date/Time: Tue May 22 05:03:15 MST 2012
Distro Release: Ubuntu quantal (development branch)
Kernel Release: Linux 3.4.0-3-generic
Unity Release: unity 5.12.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 302.11

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

Xserver Xorg Core Branch
  Installed: 2:1.12.1.902+git20120520+server-1.12-branch.4a2b8eeb-0ubuntu0ricotz

vindsl@Zuul:~$
```

---

### Post by VinDSL on 2012-05-22
> **jppr said:**
> And this kernel is broken, I was black screen when I install that kernel...
Did you install *BOTH* images?

They split them now... or whatever reason(s).  ;)

---

### Post by Harry33 on 2012-05-22
> **jppr said:**
> And this kernel is broken, I was black screen when I install that kernel...

No it is not broken, working fine here.
Like VinDSL wrote both these image packages must be installed:
- linux-image-3.4.0-3-generic
- linux-image-extra-3.4.0-3-generic

This is because the image package is split into two parts.

---

### Post by pressureman on 2012-05-22
I'm still getting intermittent boot hangs with the latest package. I've edited my grub.cfg to removed "quiet" and change "splash" to "nosplash", so I can at least see the kernel oops when it hangs, instead of just being faced with a frozen Plymouth screen.

It booted OK this time, but the previous time it was something about a bug in timer.c, while the active process was apparmor_parser.

Will write down more details next time.

---

### Post by jimerickso on 2012-05-22
how does one go about getting the omap4 kernel 3.4.0-200-1?

---

### Post by zika on 2012-05-23
What stuff has been moved in *-extra*.deb?
Is that 4th .deb essential or it is optional?
I did not try to use 3.4-daily without that 4th package...

---

### Post by Harry33 on 2012-05-23
> **zika said:**
> What stuff has been moved in *-extra*.deb?
Is that 4th .deb essential or it is optional?
I did not try to use 3.4-daily without that 4th package...

I am afraid it is very essential.
You know the previous image-generic has been split into two pieces.
Just compare the sizes of those with the previous image-generic.
So, the extra package is not actually extra, it is the other half.

You will not be able to get to desktop without it, for example no mouse, no kbd.

---

### Post by zika on 2012-05-23
> **Harry33 said:**
> I am afraid it is very essential.
You know the previous image-generic has been split into two pieces.
Just compare the sizes of those with the previous image-generic.
So, the extra package is not actually extra, it is the other half.

You will not be able to get to desktop without it, for example no mouse, no kbd.Yes, looks like that... I've got some of that in the meantime... Thank You as usual...

---

### Post by pressureman on 2012-05-23
If it's so essential, why was it split into a separate package?

---

### Post by Harry33 on 2012-05-23
> **pressureman said:**
> If it's so essential, why was it split into a separate package?

It must be Debian policy. :)
This is a common explanation I often get.
If you look, you see a number of split packages in a Debian system.
Just see how many *-common.deb or *-data.deb and on and on packages there are.

In case of the linux 3.4.0-3, the virtual flavour was dropped in favour of split -generic.
Also (i386) generic-pae was collapsed into -generic.

---

### Post by pressureman on 2012-05-23
Debian has no such split kernel package, so I don't think it's due to their policy.

The *-common.deb and *-data.deb packages are usually in the case of config files or arch-independent files (eg. /usr/share/*) being separated from the platform-specific binaries and libs.

Judging by the linux-image and linux-image-extra packages, and the fact that linux-image-virtual has been dropped, it looks like linux-image has assumed the role of linux-image-virtual (approxy 32MB for amd64), and linux-image-extra has assumed the role of the former linux-image-generic, containing all the drivers for non-virtualised hardware.

---

### Post by Harry33 on 2012-05-24
> **pressureman said:**
> Debian has no such split kernel package, so I don't think it's due to their policy.

I meant generally splitting, not just the kernel. The policy is different if you compare to arch linux (only one kernel package).

> **pressureman said:**
> 
The *-common.deb and *-data.deb packages are usually in the case of config files or arch-independent files (eg. /usr/share/*) being separated from the platform-specific binaries and libs.

Judging by the linux-image and linux-image-extra packages, and the fact that linux-image-virtual has been dropped, it looks like linux-image has assumed the role of linux-image-virtual (approxy 32MB for amd64), and linux-image-extra has assumed the role of the former linux-image-generic, containing all the drivers for non-virtualised hardware.

Linux-image-*-generic contains very important files and cannot be left uninstalled.
Linux-image-extra-*-generic depends on linux-image-*-generic.

---

### Post by pressureman on 2012-05-24
> **Harry33 said:**
> Linux-image-*-generic contains very important files and cannot be left uninstalled.
Linux-image-extra-*-generic depends on linux-image-*-generic.

linux-image-*-generic contains *vmlinuz*, eg. the actual kernel, without which booting ain't gonna happen. It also contains a modest set of kernel modules, device drivers, and firmware.

linux-image-extra-*-generic contains just a big collection of kernel modules / device drivers.

I can kinda see the logic to the decision now, especially if the linux-image-virtual no longer needs a specifically compiled vmlinuz.

---

### Post by pressureman on 2012-05-26
I'm *still* experiencing boot hangs with the latest 3.4 kernel package (at least 90% of the time), but I think I've found an upstream bug that could be the culprit...

[https://bugzilla.kernel.org/show_bug.cgi?id=43054](https://bugzilla.kernel.org/show_bug.cgi?id=43054) - Enabling CONFIG_X86_X2APIC results in hard lock up on Lenovo W520

I'm running a not-dissimilar Thinkpad T500, and tried disabling VT-d in my BIOS as referred to in the bug. So far two out of two boots succeeded.

The other suggested workaround is the 'nox2apic' kernel cmdline param. CONFIG_X86_X2APIC was also enabled on the 3.2 kernel, and when I come to think of it, I *did* experience very occasionaly boot hangs with that - nowhere near the frequency of hangs as with the 3.4 kernel however.

---

### Post by philinux on 2012-05-26
[http://voices.canonical.com/kernelteam/2012/05/26/quantal-linux-kernel-3-4-0-3-8-uploaded/](http://voices.canonical.com/kernelteam/2012/05/26/quantal-linux-kernel-3-4-0-3-8-uploaded/)

---

### Post by jfernyhough on 2012-05-26
Why do pages not have RSS feeds any more? Gah.

---

### Post by zika on 2012-05-26
Last two or three days (for the first time in a long time) daily versions of mainlike kernel freezes after initial boot on the way to DE... Am I the only one? ;)

---

### Post by pressureman on 2012-05-26
> **zika said:**
> Last two or three days (for the first time in a long time) daily versions of mainlike kernel freezes after initial boot on the way to DE... Am I the only one? ;)

Before or after lightdm appears?

---

### Post by lukax on 2012-05-26
> **jfernyhough said:**
> Kernel.org just announced the release of 3.4.

Yay?

(I'm still waiting for a working fglrx patch. :()

Same problem here... Still didn´t find a working patch :(

---

### Post by VinDSL on 2012-05-26
> **philinux said:**
> [http://voices.canonical.com/kernelteam/2012/05/26/quantal-linux-kernel-3-4-0-3-8-uploaded/](http://voices.canonical.com/kernelteam/2012/05/26/quantal-linux-kernel-3-4-0-3-8-uploaded/)
Thanks!  ;)

> **zika said:**
> Last two or three days (for the first time in a long time) daily versions of mainlike kernel freezes after initial boot on the way to DE... Am I the only one? ;)
Just upgraded from 3.4.0-3.7 to 3.4.0-3.8...

```
vindsl@Zuul:~$ uname -a
Linux Zuul 3.4.0-3-generic #8-Ubuntu SMP Sat May 26 01:44:29 UTC 2012 i686 i686 i686 GNU/Linux
```

Still booting without issue(s).  Drat!

---

### Post by jerrylamos on 2012-05-26
One of my test pc's updated to #8 booted O.K.  Will try another tomorrow.

Jerry

p.s.  #8 seems to boot kinda slow (do note I'm running Lucid Lynx on another pc - zoom!)

---

### Post by zika on 2012-05-27
> **VinDSL said:**
> Thanks!  ;)


Just upgraded from 3.4.0-3.7 to 3.4.0-3.8...

```
vindsl@Zuul:~$ uname -a
Linux Zuul 3.4.0-3-generic #8-Ubuntu SMP Sat May 26 01:44:29 UTC 2012 i686 i686 i686 GNU/Linux
```Still booting without issue(s).  Drat!3.4 (3.8 )from Ubuntu repos is working OK as is 3.4-quantal from Mainline. It started first with drm-next and spread to daily... ;)
> **pressureman said:**
> Before or after lightdm appears?Before I even get login prompt using &#8222;text&#8220; mode...

Update&#8321;: The same with today's daily package. At different place but still harder than Alt-SysRq-B... ;)

---

### Post by VinDSL on 2012-05-27
> **zika said:**
> 3.4 (3.8 )from Ubuntu repos is working OK as is 3.4-quantal from Mainline. It started first with drm-next and spread to daily... ;)
Hrm...

I'm holding back (probably) 150 package upgrades, right now, because "they" want to uninstall various gnome-shell components.  

Homey don't play that game. LoL!

Maybe there's a stinker or two, in those upgrades, that I'm unaware of...  ;)

---

### Post by zika on 2012-05-27
> **VinDSL said:**
> Hrm...

I'm holding back (probably) 150 package upgrades, right now, because "they" want to uninstall various gnome-shell components.  

Homey don't play that game. LoL!

Maybe there's a stinker or two, in those upgrades, that I'm unaware of...  ;)Kernels I'm mentioning are not from Ubuntu repos, as I've wrote (I think) above... ;)

---

### Post by pressureman on 2012-05-27
> **zika said:**
> 3.4 (3.8 )from Ubuntu repos is working OK as is 3.4-quantal from Mainline. It started first with drm-next and spread to daily... ;)
Before I even get login prompt using „text“ mode...

Update&#8321;: The same with today's daily package. At different place but still harder than Alt-SysRq-B... ;)

Could it be this possibly? [https://bugzilla.kernel.org/show_bug.cgi?id=43054](https://bugzilla.kernel.org/show_bug.cgi?id=43054)

---

### Post by zika on 2012-05-27
> **pressureman said:**
> Could it be this possibly? [https://bugzilla.kernel.org/show_bug.cgi?id=43054](https://bugzilla.kernel.org/show_bug.cgi?id=43054)I think not... I'll investigate...
I'm plagued with PMP SRST CONFIG_SATA_PMP=n bug for quite some time... ;)

Update&#8321;: Seems that it is not that bug that bugs me... ;)

Update&#8322;: Still not working daily (29-May) and one of messages is: &#8222;Fixing recursive fault but reboot needed&#8220;. Of course, reboot does not help...  Especially since only HW Reset is available... ;)

---

### Post by jerrylamos on 2012-05-29
20120528 i386 12.10 iso on Acer Aspire 5253 notebook up and running.  Installing from USB flash memory, same image as used on Acer Aspire 1 netbook and Compaq Presario tower yesterday.  Usual bunch of curios:

1. Wireless didn't connect, so ubiquity asked to connect.  I checked the box then ubiquity window disappeared.  Tried it a couple times, same result.

2. Tried to continue without wireless.  Got to the time zone screen then ubiquity window disappeared.  Tried it a couple times, same result.

3. Connected ethernet wire, then wireless automatically connected.  Disconnected ethernet wire and wireless stayed up.

4. Now install completed.

5. Asked continue or restart.  I selected restart, which rebooted the USB again.  All sorts of screen artifacts.

6. Shutdown, removed USB, booted O.K.  No battery indicator, that's a separate thread.

7. Doing updates...none actually.

Jerry

---

### Post by zika on 2012-05-31
Now I'm officially scared that 3.4 (and 3.5 ...) are going to be trouble at my place. Still no working daily on my machine since several days ago... ;)
It looks as it is having something to do with radeon...

---

### Post by dino99 on 2012-05-31
3.4 on i386 run fine here on radeon (xserver-xorg 1.12 installed from edgers ppa)

---

### Post by zika on 2012-05-31
> **dino99 said:**
> 3.4 on i386 run fine here on radeon (xserver-xorg 1.12 installed from edgers ppa)AMD64, full XE-PPA,... ;( Strange... This is the first time that I do have such long-standing problem with daily...

---

### Post by pressureman on 2012-05-31
I'm still getting fairly reproducible kernel oopses at boot time with 3.4, on a Thinkpad T500 with Intel graphics.

Fortunately I still kept a 3.2 kernel from the precise install. I'm hoping that whatever issue is affecting 3.4 will be resolved in 3.5.

---

### Post by zika on 2012-05-31
> **pressureman said:**
> I'm still getting fairly reproducible kernel oopses at boot time with 3.4, on a Thinkpad T500 with Intel graphics.

Fortunately I still kept a 3.2 kernel from the precise install. I'm hoping that whatever issue is affecting 3.4 will be resolved in 3.5.
3.4.0-030400.201205221131
&
3.4.0-3.8
work just fine here...
Only daily, and other mainline after 2012-05-22 are not...

Update&#8321;: No luck with 3.5-rc1 also... ;( ([http://ubuntuforums.org/showthread.php?t=1994605](http://ubuntuforums.org/showthread.php?t=1994605))

Update&#8322;: [http://ubuntuforums.org/showpost.php?p=11993030&postcount=3](http://ubuntuforums.org/showpost.php?p=11993030&postcount=3)

---

