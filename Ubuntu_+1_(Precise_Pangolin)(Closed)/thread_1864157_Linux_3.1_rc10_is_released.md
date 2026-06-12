---
title: "Linux 3.1 rc10 is released"
date: 2011-10-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-10-18
So the release version is on next week.

[https://lkml.org/lkml/2011/10/18/2](https://lkml.org/lkml/2011/10/18/2)

---

### Post by JMB74 on 2011-10-18
First official upload to PP for 3.1 as well.

[https://lists.ubuntu.com/archives/kernel-team/2011-October/017486.html](https://lists.ubuntu.com/archives/kernel-team/2011-October/017486.html)

> We've uploaded a new Precise linux kernel.  

This is the first upload of the v3.1 series. 

The most notable change is:        * rebase to v3.1-rc10 

The full changelog can be found at:    [https://launchpad.net/ubuntu/+source/linux/3.1.0-1.1](https://launchpad.net/ubuntu/+source/linux/3.1.0-1.1)

---

### Post by Harry33 on 2011-10-18
Up and running, downloaded from Precise repos.

[https://launchpad.net/ubuntu/+source/linux/3.1.0-1.1](https://launchpad.net/ubuntu/+source/linux/3.1.0-1.1)

---

### Post by paul_in_london on 2011-10-19
I'd been using rc9 for a while and downloaded the daily a couple of days ago. I see rc10 is now in ppa kernel mainline, but I think I'll just wait for the kernel update to come through the PP repos.

---

### Post by tista on 2011-10-19
Guys,

I've tried to run such 3.1.0-1.1 on amd64... ;)
Seemed to work well looks like daily build mainline packges...

cheers.

---

### Post by VinDSL on 2011-10-19
Smooth, baby!

LINKAGE:  [https://launchpad.net/ubuntu/+source/linux/3.1.0-1.1/+build/2861018](https://launchpad.net/ubuntu/+source/linux/3.1.0-1.1/+build/2861018)

Like riding in a Cadillac!  :)


```
i386 build of linux 3.1.0-1.1 in ubuntu precise RELEASE

Wed Oct 19 03:01:06 MST 2011
Ubuntu precise (development branch)
Linux 3.1.0-1-generic
unity 4.22.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 280.13

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

```

---

### Post by Atamisk on 2011-10-19
I compiled and ran an rc9 kernel exactly 1 hour before the rc10 flag was put on the git repo... i think i'll wait for 3.1 release now, because i'm off of rc10 by a single commit :P.

(yes i know i don't have to compile, but i'm playing around with the menuconfig to try and  see just how light i can get the kernel to be)

---

### Post by paul_in_london on 2011-10-19
The kernel updates have arrived through the repos now.

```
paul@precise-64:~$ uname -a
Linux precise-64 3.1.0-1-generic #1-Ubuntu SMP Tue Oct 18 19:22:01 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
paul@precise-64:~$
```

---

### Post by ventrical on 2011-10-19
I can't get the new kernel to come up in terminal of show up in system Monitor.

What am I doing wrong?

---

### Post by cecilpierce on 2011-10-19
I dont see it yet, what repo are you using ?

---

### Post by ventrical on 2011-10-19
> **cecilpierce said:**
> I dont see it yet, what repo are you using ?


These here.

---

### Post by ventrical on 2011-10-19
Maby I have to change my preferences.

---

### Post by paul_in_london on 2011-10-19
> **ventrical said:**
> Maby I have to change my preferences.

Your screenshot refers to Oneiric. Haven't you changed your /etc/apt/sources.list to point to precise? I'm using the main mirror by the way.

---

### Post by ventrical on 2011-10-19
> **paul_in_london said:**
> Your screenshot refers to Oneiric. Haven't you changed your /etc/apt/sources.list to point to precise? I'm using the main mirror by the way.

Sure do Paul.


  

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Beta i386 (20110901)]/ precise main restricted

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Beta i386 (20110901)]/ precise main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe main multiverse restricted
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports universe main multiverse restricted


I just manually downloaded the packages and used :

sudo dpkg -i

 but to no aval.  Grub bootloader ran ..etc.. System Monitor says I have Precsie .. but can't get the kernel version to come up for validation.

---

### Post by paul_in_london on 2011-10-19
> **ventrical said:**
> Sure do Paul.


  

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Beta i386 (20110901)]/ precise main restricted

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Beta i386 (20110901)]/ precise main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe main multiverse restricted
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports universe main multiverse restricted


I just manually downloaded the packages and used :

sudo dpkg -i

 but to no aval.  Grub bootloader ran ..etc.. System Monitor says I have Precsie .. but can't get the kernel version to come up for validation.

It's late here. Just having a nightcap :)

To clarify in case I'm misunderstanding what you're saying, when you reboot and bring up the grub menu to select the kernel you want to boot can you see your newly installed kernel listed (3.1.0-1-generic I presume)? And when you boot, what does uname -a tell you?

---

### Post by ronacc on 2011-10-19
I'm getting the same as ventrical I am set for precise and the main repo and the new kernel does not show up in synaptic or with apt-get either upgrade or dist-upgrade .

---

### Post by paul_in_london on 2011-10-19
Hmm. That's a bit strange. I used synaptic earlier tonight as a bit of a last resort to obtain the kernel upgrade via the main mirror because aptitude (my first preference) and apt-get wouldn't do it.

My sources.list:

```
deb http://archive.ubuntu.com/ubuntu precise main restricted

deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb http://archive.ubuntu.com/ubuntu precise-security main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb-src http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb-src http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu precise-security restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb-src http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://archive.ubuntu.com/ubuntu precise-proposed restricted main multiverse universe
```

```
paul@precise-64:~$ uname -a
Linux precise-64 3.1.0-1-generic #1-Ubuntu SMP Tue Oct 18 19:22:01 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
paul@precise-64:~$ 
```

With apt-get at the moment I have:

```
paul@precise-64:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  icedtea-6-jre-cacao icedtea-6-jre-jamvm openjdk-6-jre openjdk-6-jre-headless
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
paul@precise-64:~$
```

---

### Post by ventrical on 2011-10-19
> **paul_in_london said:**
> It's late here. Just having a nightcap :)

To clarify in case I'm misunderstanding what you're saying, when you reboot and bring up the grub menu to select the kernel you want to boot can you see your newly installed kernel listed (3.1.0-1-generic I presume)? And when you boot, what does uname -a tell you?

No.. it is not registered in the grub bootloader nor wil it show up with uname-a command.

  I am trying a commit on another system.

I'll get back.

---

### Post by paul_in_london on 2011-10-19
> **ventrical said:**
> No.. it is not registered in the grub bootloader nor wil it show up with uname-a command.

  I am trying a commit on another system.

I'll get back.

Are you dual-booting? This install is on /dev/sda2 and grub was updated, but I couldn't see the new kernel listed after a reboot until I booted into my other PP install on /dev/sda1 and ran update-grub and rebooted again. I suppose I should reinstall grub from this install, but anyway...

---

### Post by ventrical on 2011-10-19
I got it on another commit.

It could be that the other commit was an old beta.

madame@madame-ME051:~$ uname -a
Linux madame-ME051 3.1.0-1-generic #1-Ubuntu SMP Tue Oct 18 19:11:28 UTC 2011 i686 i686 i386 GNU/Linux
madame@madame-ME051:~$ 


thanks

whew...that was a tough one  :)

works beautiful though

---

### Post by ronacc on 2011-10-19
thanks paul I copied your sources.list and that brought it in for me . I'll examine it and my original and see what the diffs are , I thought I had everything changed over to precise but I guess not .

---

### Post by ventrical on 2011-10-20
> **paul_in_london said:**
> Are you dual-booting? This install is on /dev/sda2 and grub was updated, but I couldn't see the new kernel listed after a reboot until I booted into my other PP install on /dev/sda1 and ran update-grub and rebooted again. I suppose I should reinstall grub from this install, but anyway...


@paul_in_London,

Yes.. I have 4 partitions. I went to the first partition and  <sudo update-grub> and it worked just great. I now have all the instances of the new kernel indexed in the Grub Bootloaded startup screen.!  :) - so I really did not need the other commit ..but thats alright because I have a lot of hardware resources and also I will be able to test on both tower desktop and laptop.

Thanks a lot.

regrards, ventrical

---

### Post by paul_in_london on 2011-10-20
@ventrical, ronacc:

Good to hear it's working for you now! :)

---

### Post by sbglobal79 on 2011-10-20
I compiled and ran an rc9 kernel exactly 1 hour before the rc10 flag was put on the git report.

---

### Post by MAFoElffen on 2011-10-21
I'm running 3.1.0~rc10 off the mainline PPA and it's running... Although I have a confirmed/triaged bug open on the 3.x series. Now they say it's upstream and if I would file the upstream, but upstreams bugzilla is down for a while... I guess they got hacked (security breach as they called it)..

Since it is 3.x, the bug affects both Oneiric and Precise. (lost of function, but not a show stopper in any way.)

---

### Post by Harry33 on 2011-10-22
> **MAFoElffen said:**
> I'm running 3.1.0~rc10 off the mainline PPA and it's running... Although I have a confirmed/triaged bug open on the 3.x series. Now they say it's upstream and if I would file the upstream, but upstreams bugzilla is down for a while... I guess they got hacked (security breach as they called it)..

Since it is 3.x, the bug affects both Oneiric and Precise. (lost of function, but not a show stopper in any way.)

3.1.0 rc10 is in the Precise repos now.
What exactly is the bug you are talking about in 3.x versions of Linux kernel?

---

### Post by buzzmandt on 2011-10-22
agreed, what is this bug in the 3x series?
I have the new kernel installed and it's working quite lovely

---

### Post by MAFoElffen on 2011-10-22
> **Harry33 said:**
> 3.1.0 rc10 is in the Precise repos now.
What exactly is the bug you are talking about in 3.x versions of Linux kernel?
Here it is:
[**Linux 3.0.x kernel with Ubuntu does not take runlevel 2-4 arguments as boot options.**]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875352")

Summary: 2.6.x series linux kernels previous (even 2.6.32.x, which is not previous) to 3.x used to take runlevel arguments from the boot line. Ubuntu was a little distinct in that instead of taking a number (example "1" for runlevel 1, "2" for ...), it instead used "single", text", etc.  

Since kernel version 3.x the "text" kernel boot option has been gone.

Yes, we could change the runlevel boot default in files.  We can still change the runlevel at the command line (once booted).  We could change the default in grub to 
```

GRUB_GFXPAYLOAD_LINUX=text

```To force it to boot into TTY Text... 

But that is not the point.  If X borks, an update fails, a bad dist-upgrade... a user needs an easy way back in to at least a commandline.  Having that runlevel option at boot retains that flexibility.  Yes, single is an option for that, but sometimes you really need a full working system.  (Low-end x layers on some server installs... etc.)

Current Status- Sort of Upstream, kernel.org got their site hacked and even though its site is mostly back up, their bugzilla seems to still be away...

---

### Post by ventrical on 2011-10-22
Here is some graphic activity I only get with Precise and the new RC kernel.

[http://www.youtube.com/watch?v=udZD9c5bO3I](http://www.youtube.com/watch?v=udZD9c5bO3I)

---

### Post by JMB74 on 2011-10-26
Now updated to 3.1 final.

[https://launchpad.net/ubuntu/precise/+source/linux/3.1.0-2.2](https://launchpad.net/ubuntu/precise/+source/linux/3.1.0-2.2)

---

