---
title: "Kernel 5.8 RC (Release Canidate) series"
date: 2020-06-14
forum: Ubuntu Development Version
---

### Post by Doug S on 2020-06-14
Kernel 5.8-rc1 is available from [kernel.org]("https://www.kernel.org/") and the [Ubuntu Mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.8-rc1/"), although the file names are currently incorrect missing the -rc1.

I have only had it running for a few minutes:

```
doug@s18:~$ uname -a
Linux s18 5.8.0-050800-lowlatency #202006142031 SMP PREEMPT Sun Jun 14 20:39:09 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

We have a running thread during each mainline kernel release cycle.

Previous cycle threads:
[5.7]("https://ubuntuforums.org/showthread.php?t=2440607")
[5.6]("https://ubuntuforums.org/showthread.php?t=2436608")
[5.5]("https://ubuntuforums.org/showthread.php?t=2432815")
[5.4]("https://ubuntuforums.org/showthread.php?t=2428734")
[5.3]("https://ubuntuforums.org/showthread.php?t=2423441")
[5.2]("https://ubuntuforums.org/showthread.php?t=2419363")
[5.1]("https://ubuntuforums.org/showthread.php?t=2414938")
[5.0]("https://ubuntuforums.org/showthread.php?t=2409811")
[4.20]("https://ubuntuforums.org/showthread.php?t=2405365")
4.19 ?
[4.18]("https://ubuntuforums.org/showthread.php?t=2394500")
[4.17]("https://ubuntuforums.org/showthread.php?t=2389561")
[4.16]("https://ubuntuforums.org/showthread.php?t=2384781")
[4.15]("https://ubuntuforums.org/showthread.php?t=2378956")
[4.14]("https://ubuntuforums.org/showthread.php?t=2371638")

---

### Post by zika on 2020-06-15
[https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.8-rc1-Released](https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.8-rc1-Released)
```
:~$ uname -a
Linux *++* 5.8.0-050800daily20200615-generic #202006142201 SMP Mon Jun 15 02:06:29 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by mIk3_08 on 2020-06-15
Wow. This is really big. [Click here]("https://news.softpedia.com/news/linus-torvalds-announces-massive-linux-kernel-5-8-update-530256.shtml") for more info.

---

### Post by corradoventu on 2020-06-15
```
corrado@corrado-p9-gg-0506:~$ inxi -SCG
System:    Host: corrado-p9-gg-0506 Kernel: 5.8.0-050800-generic x86_64 bits: 64 Desktop: Gnome 3.36.3 
           Distro: Ubuntu 20.10 (Groovy Gorilla) 
CPU:       Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP L2 cache: 3072 KiB 
           Speed: 3902 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 3903 2: 3900 3: 3901 4: 3901 
Graphics:  Device-1: Intel HD Graphics 630 driver: i915 v: kernel 
           Device-2: ARC USB 2.0 Camera type: USB driver: uvcvideo 
           Display: x11 server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa Intel HD Graphics 630 (KBL GT2) v: 4.6 Mesa 20.0.7 
corrado@corrado-p9-gg-0506:~$ 

```

---

### Post by Doug S on 2020-06-15
> **zika said:**
> [https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.8-rc1-Released](https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.8-rc1-Released) I had not realized it was such a big release. Oh, even a new record!!!

---

### Post by Doug S on 2020-06-25
Just a caution before kernel 5.8-rc3:

I saw [this]("https://marc.info/?l=linux-kernel&m=159309158328161&w=2"), copied below:

```
On Thu, Jun 25, 2020 at 02:27:46PM +0200, Paolo Bonzini wrote:
> > Given the regression fix nature of this patch, is it being taken care
> > of by anyone (tip in particular) already?
> 
> I was waiting for tip to pick it up, but I can as well with an Acked-by
> (KVM is broken by the patch but there's nothing KVM specific in it).

https://git.kernel.org/tip/5d5103595e9e53048bb7e70ee2673c897ab38300

will be in -rc3, most likely.
```

---

### Post by IanW on 2020-06-26
Anyone have any idea when Canonical will _sign_ a newer kernel than 5.4.0-28?

---

### Post by dino99 on 2020-06-26
The Groovy Gorilla (active development)Linux trunk series
 5.4.0-40.44	proposed (main)	17 hours ago
 5.4.0-26.30	release (main)	2020-04-24

---

### Post by IanW on 2020-06-27
Thanks. I was hoping for 5.6 or better for AMD's k10temp  sensor support.

I guess we may not see that until kernel freeze in October, and jump straight from 5.4 to 5.7 or 5.8.

---

### Post by dino99 on 2020-06-27
You can easily install a newer kernel if you need/want from [https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by IanW on 2020-06-27
> **dino99 said:**
> You can easily install a newer kernel if you need/want from [https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)

I kinda think I need signed kernels, as I dual boot on a UEFI system.

EDIT: update-secureboot-policy says secureboot NOT enabled. I'm a derp!

EDIT 2: Now happily running kernel 5.7.0-050700-generic

---

### Post by Doug S on 2020-06-29
I see that [-rc3]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.8-rc3/") still has busted files names. I have gone on the kernel channel on IRC and asked if it can be fixed.

---

### Post by dino99 on 2020-06-29
Your wish is coming :p
linux-5.7 (5.7.0-9.10) groovy; urgency=medium

  * Groovy update: v5.7.2 upstream stable release

---

### Post by corradoventu on 2020-07-01
suffix rcx disappeared in filenames for last 5.8 RC:
linux-headers-5.7.0-050700rc7_5.7.0-050700rc7.202005242331_all.deb   ... 5.7 RC7
linux-headers-5.8.0-050800_5.8.0-050800.202006282330_all.deb             ... 5.8 RC3 - no rc3 suffix, just datetime

---

### Post by Doug S on 2020-07-01
> **corradoventu said:**
> suffix rcx disappeared in filenames for last 5.8 RC:
linux-headers-5.7.0-050700rc7_5.7.0-050700rc7.202005242331_all.deb   ... 5.7 RC7
linux-headers-5.8.0-050800_5.8.0-050800.202006282330_all.deb             ... 5.8 RC3 - no rc3 suffix, just datetimeYes, and as noted in my 1st and 12th posts. Just a couple of days ago, I went [on IRC]("https://irclogs.ubuntu.com/2020/06/29/%23ubuntu-kernel.html") and asked about it.

The thing that always surprises me when the mainline PPA breaks in some way is nobody ever seems to notice until one of us from here (often me) tells them about it.

Anyway, let just see what happens for -rc4.

---

### Post by Doug S on 2020-07-05
> **Doug S said:**
> Yes, and as noted in my 1st and 12th posts. Just a couple of days ago, I went [on IRC]("https://irclogs.ubuntu.com/2020/06/29/%23ubuntu-kernel.html") and asked about it.

The thing that always surprises me when the mainline PPA breaks in some way is nobody ever seems to notice until one of us from here (often me) tells them about it.

Anyway, let just see what happens for -rc4.Well, still busted file naming for [-rc4]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.8-rc4/")

---

### Post by pqwoerituytrueiwoq on 2020-07-06
Guess 5.7 is as far as i am gonna get on mainline with 20.04 for now... wanted to try the new amd_engery module (still can but... no VB...)
```
$ sudo dpkg -i /tmp/kernel-5.8.0-050800/linux-*.deb
Selecting previously unselected package linux-headers-5.8.0-050800.
(Reading database ... 339543 files and directories currently installed.)
Preparing to unpack .../linux-headers-5.8.0-050800_5.8.0-050800.202007052030_all.deb ...
Unpacking linux-headers-5.8.0-050800 (5.8.0-050800.202007052030) ...
Selecting previously unselected package linux-headers-5.8.0-050800-generic.
Preparing to unpack .../linux-headers-5.8.0-050800-generic_5.8.0-050800.202007052030_amd64.deb ...
Unpacking linux-headers-5.8.0-050800-generic (5.8.0-050800.202007052030) ...
Selecting previously unselected package linux-image-unsigned-5.8.0-050800-generic.
Preparing to unpack .../linux-image-unsigned-5.8.0-050800-generic_5.8.0-050800.202007052030_amd64.deb ...
Unpacking linux-image-unsigned-5.8.0-050800-generic (5.8.0-050800.202007052030) ...
Selecting previously unselected package linux-modules-5.8.0-050800-generic.
Preparing to unpack .../linux-modules-5.8.0-050800-generic_5.8.0-050800.202007052030_amd64.deb ...
Unpacking linux-modules-5.8.0-050800-generic (5.8.0-050800.202007052030) ...
Setting up linux-headers-5.8.0-050800 (5.8.0-050800.202007052030) ...
Setting up linux-headers-5.8.0-050800-generic (5.8.0-050800.202007052030) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.8.0-050800-generic

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
**make -j12 KERNELRELEASE=5.8.0-050800-generic -C /lib/modules/5.8.0-050800-generic/build M=/var/lib/dkms/virtualbox/6.1.6/build...(bad exit status: 2)**
**ERROR (dkms apport): kernel package linux-headers-5.8.0-050800-generic is not supported**
**Error! Bad return status for module build on kernel: 5.8.0-050800-generic (x86_64)**
Consult /var/lib/dkms/virtualbox/6.1.6/build/make.log for more information.
   ...done.
Setting up linux-modules-5.8.0-050800-generic (5.8.0-050800.202007052030) ...
Setting up linux-image-unsigned-5.8.0-050800-generic (5.8.0-050800.202007052030) ...
I: /boot/vmlinuz.old is now a symlink to vmlinuz-5.7.7-050707-generic
I: /boot/initrd.img.old is now a symlink to initrd.img-5.7.7-050707-generic
I: /boot/vmlinuz is now a symlink to vmlinuz-5.8.0-050800-generic
I: /boot/initrd.img is now a symlink to initrd.img-5.8.0-050800-generic
Processing triggers for linux-image-unsigned-5.8.0-050800-generic (5.8.0-050800.202007052030) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.8.0-050800-generic

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
**make -j12 KERNELRELEASE=5.8.0-050800-generic -C /lib/modules/5.8.0-050800-generic/build M=/var/lib/dkms/virtualbox/6.1.6/build...(bad exit status: 2)**
[B]ERROR (dkms apport): kernel package linux-headers-5.8.0-050800-generic is not supported
Error! Bad return status for module build on kernel: 5.8.0-050800-generic (x86_64)
Consult /var/lib/dkms/virtualbox/6.1.6/build/make.log for more information.
   ...done.[/B]
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.8.0-050800-generic
modinfo: ERROR: could not get modinfo from 'da903x': No such file or directory
W: initramfs-tools configuration sets RESUME=UUID=7d77d03d-e876-4707-8d39-af23af9cb1bf
W: but no matching swap device is available.
I: The initramfs will attempt to resume from /dev/sdb2
I: (UUID=f19176ad-6f15-434c-a987-d68e02067657)
I: Set the RESUME variable to override this.
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.8.0-050800-generic
Found initrd image: /boot/initrd.img-5.8.0-050800-generic
Found linux image: /boot/vmlinuz-5.7.7-050707-generic
Found initrd image: /boot/initrd.img-5.7.7-050707-generic
Found linux image: /boot/vmlinuz-5.4.0-40-generic
Found initrd image: /boot/initrd.img-5.4.0-40-generic
Found linux image: /boot/vmlinuz-5.4.0-39-generic
Found initrd image: /boot/initrd.img-5.4.0-39-generic
done
```

---

### Post by Doug S on 2020-07-06
@corradoventu : I saw that you added to [bug 1873441]("https://bugs.launchpad.net/ubuntu/+source/linux-oem-5.6/+bug/1873441"). About this error:

```
modinfo: ERROR: could not get modinfo from 'da903x': No such file or directory
```

That fix was done downstream from mainline.
I get the same error also, and have done for a a couple of kernels now.

---

### Post by corradoventu on 2020-07-06
With the new 'busted' names installing RC4 the new kernel REPLACES RC3 instead adding a new one. May be an advantage? or a problem?

---

### Post by Doug S on 2020-07-06
> **corradoventu said:**
> With the new 'busted' names installing RC4 the new kernel REPLACES RC3 instead adding a new one. May be an advantage? or a problem?Oh, absolutely a problem. We often have to go back "N" versions to find where something broke so as to make a kernel bisection start and end points well defined. I need old -rc versions often.

On one test server I have 76 kernels, back to 4.10.0. On another I have 50, back to 5.2.0-rc1.

---

### Post by Doug S on 2020-07-10
> **Doug S said:**
> @corradoventu : I saw that you added to [bug 1873441]("https://bugs.launchpad.net/ubuntu/+source/linux-oem-5.6/+bug/1873441"). About this error:

```
modinfo: ERROR: could not get modinfo from 'da903x': No such file or directory
```

That fix was done downstream from mainline.
I get the same error also, and have done for a a couple of kernels now.Actually, I was wrong there. This error is somehow Ubuntu only, I don't get it on the kernels I build myself. I also observe that it went away and came back. So, when I did an update today I got (I misssed a few -rc's, and deleted all of my own kernels):

```
update-initramfs: Generating /boot/initrd.img-5.8.0-050800-lowlatency
modinfo: ERROR: could not get modinfo from 'da903x': No such file or directory  [COLOR="#FF0000"]<<<< Problem returned[/COLOR]
...
update-initramfs: Generating /boot/initrd.img-5.7.0-050700rc6-lowlatency   [COLOR="#FF0000"]<<< No problem[/COLOR]
update-initramfs: Generating /boot/initrd.img-5.7.0-050700rc3-lowlatency
modinfo: ERROR: could not get modinfo from 'da903x': No such file or directory
update-initramfs: Generating /boot/initrd.img-5.7.0-050700rc1-lowlatency
modinfo: ERROR: could not get modinfo from 'da903x': No such file or directory
update-initramfs: Generating /boot/initrd.img-5.7.0-050700-lowlatency
...
update-initramfs: Generating /boot/initrd.img-5.6.0-050600rc4-lowlatency
modinfo: ERROR: could not get modinfo from 'da903x': No such file or directory
update-initramfs: Generating /boot/initrd.img-5.6.0-050600rc2-lowlatency
modinfo: ERROR: could not get modinfo from 'da903x': No such file or directory
update-initramfs: Generating /boot/initrd.img-5.6.0-050600rc1-lowlatency
modinfo: ERROR: could not get modinfo from 'da903x': No such file or directory  [COLOR="#FF0000"]<<<< first time[/COLOR]
update-initramfs: Generating /boot/initrd.img-5.6.0-050600-lowlatency
modinfo: ERROR: could not get modinfo from 'da903x': No such file or directory
...
update-initramfs: Generating /boot/initrd.img-5.5.0-050500rc1-lowlatency
...
update-initramfs: Generating /boot/initrd.img-5.4.0-050400rc1-lowlatency
update-initramfs: Generating /boot/initrd.img-5.4.0-050400-lowlatency
update-initramfs: Generating /boot/initrd.img-5.4.0-37-generic
update-initramfs: Generating /boot/initrd.img-5.4.0-33-generic
update-initramfs: Generating /boot/initrd.img-5.4.0-29-generic
update-initramfs: Generating /boot/initrd.img-5.4.0-26-generic
update-initramfs: Generating /boot/initrd.img-5.4.0-24-generic
update-initramfs: Generating /boot/initrd.img-5.4.0-21-generic
update-initramfs: Generating /boot/initrd.img-5.4.0-18-generic
update-initramfs: Generating /boot/initrd.img-5.4.0-14-generic
update-initramfs: Generating /boot/initrd.img-5.4.0-12-generic
update-initramfs: Generating /boot/initrd.img-5.4.0-9-generic
update-initramfs: Generating /boot/initrd.img-5.2.0-050200-lowlatency
update-initramfs: Generating /boot/initrd.img-5.2.0-rc1-stock
update-initramfs: Generating /boot/initrd.img-5.1.0-050100-lowlatency
Setting up libglib2.0-0:amd64 (2.64.3-1~ubuntu20.04.1) ...
```

---

### Post by pqwoerituytrueiwoq on 2020-07-10
So what exactly is this reading?
```
$ sensors amd_energy-*
amd_energy-isa-0000
Adapter: ISA adapter
Ecore000:    594.13 kJ
Ecore001:    594.10 kJ
Ecore002:    594.18 kJ
Ecore003:    594.24 kJ
Ecore004:    594.08 kJ
Ecore005:    594.05 kJ
Esocket0:      3.51 MJ
```
I think it may be total reading power consumed, but getting usable data out of that would require post processing across at least 2 snapshots

---

### Post by Doug S on 2020-07-10
> **pqwoerituytrueiwoq said:**
> So what exactly is this reading?
```
$ sensors amd_energy-*
amd_energy-isa-0000
Adapter: ISA adapter
Ecore000:    594.13 kJ
Ecore001:    594.10 kJ
Ecore002:    594.18 kJ
Ecore003:    594.24 kJ
Ecore004:    594.08 kJ
Ecore005:    594.05 kJ
Esocket0:      3.51 MJ
```
I think it may be total reading power consumed, but getting usable data out of that would require post processing across at least 2 snapshotsI am not familiar with AMD processors and their MSRs (Machine Specific Registers). But yes, I think you would have to take two samples and subtract. I assume your uptime is significant, otherwise that is a lot of energy.

Anyway, yes it looks like energy per core and total energy, likely since boot, or since the last wrap around. 3.51 Mega Joules. At a wild guess of 10 watts processor package power that's like an uptime of 98 hours or 98 hours since the last joule counter wrap around.

I know there has been work done on turbostat (an Intel tool, but in the kernel source tree) to support AMD processors. Try it, because if it knows about the AMD energy MSRs, it will do the math for you.

Here is my computer:

```
doug@s18:~$ sudo ~/turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgTmp,PkgWatt,GFXWatt,IRQ --interval 6
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt GFXWatt
0.03    800     190     30      1.93    0.00
0.02    800     96      29      1.92    0.00
0.02    800     122     29      1.93    0.00
0.02    800     109     29      1.93    0.00
```

and using energy instead of power:

```
doug@s18:~$ sudo ~/turbostat --Summary --quiet --Joules --show Busy%,Bzy_MHz,PkgTmp,Pkg_J,GFXWatt,IRQ --interval 6
Busy%   Bzy_MHz IRQ     PkgTmp  Pkg_J
0.04    800     240     30      11.47
0.03    800     133     30      11.49
0.03    800     151     29      11.50
0.02    800     98      29      11.63
0.02    800     105     29      11.58
```

and 11.50 / 6 = 1.917 watts. I often use joules as a way to get an extra digit, even though the counters aren't really that accurate at such low power.

And just for completeness, here is the same, but adding some load:
```
doug@s18:~$ sudo ~/turbostat --Summary --quiet --Joules --show Busy%,Bzy_MHz,PkgTmp,Pkg_J,GFXWatt,IRQ --interval 6
Busy%   Bzy_MHz IRQ     PkgTmp  Pkg_J
0.03    1047    328     30      11.58
0.02    800     173     30      11.49
9.00    4580    5239    45      82.57
25.31   4600    15590   49      182.96
39.87   4600    24567   51      245.12
50.22   4600    29669   50      286.86
62.36   4600    35775   50      322.80
73.98   4600    41415   49      352.23
92.98   4600    48704   50      394.95
100.26  4600    51085   50      408.75
100.26  4600    51241   52      409.85
100.26  4600    51136   52      412.53
100.26  4600    51124   51      414.59

```

EDIT: Actually, I wonder if turbostat knows about your relatively new processor. Looking at its history in git shows the last AMD related edit as:

```
commit 3316f99a9f1b68c578c57e76792bd19da1c7d423
Author: Calvin Walton <calvin.walton@kepstin.ca>
Date:   Fri [COLOR="#FF0000"]Aug 17[/COLOR] 12:34:42 [COLOR="#FF0000"]2018[/COLOR] -0400

    tools/power turbostat: Also read package power on AMD F17h (Zen)

    The package power can also be read from an MSR...
```

---

### Post by pqwoerituytrueiwoq on 2020-07-11
so yea there is a issue with this, but idk how much power the system pulls in sleep mode, now how muck power this is, i assume this in in joules, only place i have ever seen that is on surge protectors
before going to sleep (*puts computer to sleep mode*)
```
$ sensors -Au amd_energy-*
amd_energy-isa-0000
Ecore000:
  energy1_input: 660251.872
Ecore001:
  energy2_input: 660354.366
Ecore002:
  energy3_input: 660292.309
Ecore003:
  energy4_input: 660340.455
Ecore004:
  energy5_input: 660280.489
Ecore005:
  energy6_input: 660188.385
Esocket0:
  energy7_input: 3938647.414
```

in the morning (woken from sleep mode)
*7-8 hours later
```
$ sensors -Au amd_energy-*
amd_energy-isa-0000
Ecore000:
  energy1_input: 720980.453
Ecore001:
  energy2_input: 720966.457
Ecore002:
  energy3_input: 720981.142
Ecore003:
  energy4_input: 720984.914
Ecore004:
  energy5_input: 720965.693
Ecore005:
  energy6_input: 720992.887
Esocket0:
  energy7_input: 4000923.488
```

---

### Post by Doug S on 2020-07-11
So 2 watts in sleep mode, seems high, but reasonable to me.

(4000923.488 - 3938647.414) / 3600 / 8 = 2.16 watts

If readers are wondering why this stuff is on this thread, it is because some of this stuff is new in kernel 5.8 (I think).

---

### Post by pqwoerituytrueiwoq on 2020-07-11
that was only 2 watts!?, ok that is nothing, probably just the wake process there
amd_energy new in linux 5.8: [https://www.phoronix.com/scan.php?page=news_item&px=AMD-Energy-Driver-Working-Well](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Energy-Driver-Working-Well)

---

### Post by Doug S on 2020-07-13
Kernel 5.8-rc5 is available, but still with the incorrect files names.
If someone wants to go on IRC and ask about the file names, please do, referring to [the last time]("https://irclogs.ubuntu.com/2020/06/29/%23ubuntu-kernel.html").

I am getting some error:
```
Jul 13 07:01:08 s18 kernel: [    9.429363] bpfilter: Loaded bpfilter_umh pid 826
Jul 13 07:01:08 s18 kernel: [    9.432623] bpfilter: write fail -22
Jul 13 07:01:08 s18 kernel: [    9.432676] bpfilter: write fail -22
Jul 13 07:01:08 s18 kernel: [    9.458993] bpfilter: Loaded bpfilter_umh pid 836
Jul 13 07:01:08 s18 kernel: [    9.459132] bpfilter: write fail -22
Jul 13 07:01:08 s18 kernel: [    9.459185] bpfilter: write fail -22
```

And I do observe a possibly related [change]("https://lkml.org/lkml/2020/7/12/312")

```
commit 6955a76fbcd56d27c84c01353101048e366d070f
Author: Christoph Hellwig <hch@lst.de>
Date:   Wed May 13 08:46:58 2020 +0200

    bpfilter: switch to kernel_write

    While pipes don't really need sb_writers projection, __kernel_write is an
    interface better kept private, and the additional rw_verify_area does not
    hurt here.

    Signed-off-by: Christoph Hellwig <hch@lst.de>

diff --git a/net/bpfilter/bpfilter_kern.c b/net/bpfilter/bpfilter_kern.c
index c0f0990f30b6..1905e01c3aa9 100644
--- a/net/bpfilter/bpfilter_kern.c
+++ b/net/bpfilter/bpfilter_kern.c
@@ -50,7 +50,7 @@ static int __bpfilter_process_sockopt(struct sock *sk, int optname,
        req.len = optlen;
        if (!bpfilter_ops.info.pid)
                goto out;
-       n = __kernel_write(bpfilter_ops.info.pipe_to_umh, &req, sizeof(req),
+       n = kernel_write(bpfilter_ops.info.pipe_to_umh, &req, sizeof(req),
                           &pos);
        if (n != sizeof(req)) {
                pr_err("write fail %zd\n", n);

```
I doubt that this is the exact problem commit, but that is actually part of the whole set of 17 commits.

EDIT: Hmmm... dmesg seems to require root (sudo) privileges now. It didn't for kernel 5.8-rc1, but does for 5.8-rc4 (I missed -rc2 and -rc3). (here is a good example of why the files names should keep the -rc designations.)

---

### Post by zika on 2020-07-14
Not a solution but a workaround:```
sudo nano /etc/modprobe.d/blacklist-pfilter.conf
```
insert: ```
install bpfilter /bin/false
```
close and refresh initramfs: ```
sudo update-initramfs -ckall
``` (if You want to refresh all, in other case just put the name of kernel You want to refresh)...
As far as name of kernel is concerened, I kind of like it because this way it spares me from removing previous rc... ;) Dmesg shoul ask for sudo pass for numerous safety reasons...

---

### Post by Doug S on 2020-07-14
> **zika said:**
> As far as name of kernel is concerned, I kind of like it because this way it spares me from removing previous rc... ;)Well, sorry zika, I wined on IRC again and now it is fixed...

---

### Post by Doug S on 2020-07-14
> **zika said:**
> Dmesg should ask for sudo pass for numerous safety reasons...Well, the same information is also in /var/log/kern.log, available to anyone. One problem I observe with linux is no concern for backwards compatibility. These type of changes create a cascading ton of work as documentation becomes obsolete.

---

### Post by zika on 2020-07-14
> **Doug S said:**
> Well, the same information is also in /var/log/kern.log, available to anyone. One problem I observe with linux is no concern for backwards compatibility. These type of changes create a cascading ton of work as documentation becomes obsolete.
True for kern.log but that does not make it right... ;) About documentation: better not to start, I'll get banned for complaining. Never mind, that made me, for decades, learn to learn much quickly... ;)

---

### Post by Doug S on 2020-07-16
re: dmesg now needs root permissions:> **zika said:**
> True for kern.log but that does not make it right... ;)see [this]("https://lists.ubuntu.com/archives/ubuntu-devel/2020-June/041063.html"). And, actually the access rights for /var/log/kern.log are restricted.

```
doug@s18:~/temp-k-git/linux$ grep CONFIG_SECURITY_DMESG_RESTRICT .con*
.config:CONFIG_SECURITY_DMESG_RESTRICT=y
...
.config-5.8.0-050800rc1-lowlatency:# CONFIG_SECURITY_DMESG_RESTRICT is not set
.config-5.8.0-050800rc4-lowlatency:CONFIG_SECURITY_DMESG_RESTRICT=y
.config-5.8.0-050800rc5-lowlatency:CONFIG_SECURITY_DMESG_RESTRICT=y
.config-5.8-rc1-doug:# CONFIG_SECURITY_DMESG_RESTRICT is not set
...

```
and:
```
doug@s18:~/temp-k-git/linux$ ls -l /var/log/kern.log
-rw-r----- 1 syslog adm 1217129 Jul 15 15:20 /var/log/kern.log

```

---

### Post by zika on 2020-07-17
I did not have any relationship with that change... ;)
It's OK with me.

---

### Post by Doug S on 2020-07-19
Kernel [5.8-rc6]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.8-rc6/") is available. There are a lot of kernel configuration file changes between -rc5 and -rc6.

---

### Post by zebra2 on 2020-07-20
Thanks for pointing out this problem. I agree with the Link provided posted by [COLOR=#000000]Matthew Ruffell, that these various logs should be admin protected. Actually I don't see how linux has survived this long with this vulnerability.  If an intruder can mine my network data he is no longer blocked by closed ports. It may be a long shot, but possible. Also a good reason to make sure that gufw is active.

 PS 
This discussion is a diversion from the OP ([/COLOR]Kernel 5.8 RC (Release Canidate) series) but without regard for that is a great discussion point.

---

### Post by Cavsfan on 2020-07-20
> **Doug S said:**
> Kernel [5.8-rc6]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.8-rc6/") is available. There are a lot of kernel configuration file changes between -rc5 and -rc6.

It installed without any errors or problems.
```
cavsfan@groovy:~$ inxi -SMCG
System:    Host: groovy Kernel: 5.8.0-050800rc6-lowlatency x86_64 bits: 64 Desktop: Xfce 4.14.2 
           Distro: Ubuntu 20.10 (Groovy Gorilla) 
Machine:   Type: Desktop System: ASUS product: All Series v: N/A serial: <superuser/root required> 
           Mobo: ASUSTeK model: Z87-K v: Rev X.0x serial: <superuser/root required> UEFI: American Megatrends v: 1103 
           date: 01/02/2014 
CPU:       Topology: Quad Core model: Intel Core i7-4770K bits: 64 type: MT MCP L2 cache: 8192 KiB 
           Speed: 3498 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 3499 2: 3498 3: 3499 4: 3500 5: 3501 6: 3502 7: 3502 
           8: 3499 
Graphics:  Device-1: NVIDIA GM200 [GeForce GTX 980 Ti] driver: nvidia v: 450.57 
           Display: x11 server: X.Org 1.20.8 driver: nvidia resolution: 3840x2160~60Hz 
           OpenGL: renderer: GeForce GTX 980 Ti/PCIe/SSE2 v: 4.6.0 NVIDIA 450.57 



```

---

### Post by Cavsfan on 2020-07-26
Kernel [5.8-rc7]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.8-rc7") is available.

---

### Post by corradoventu on 2020-07-27
In the page [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.8-rc7/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.8-rc7/)
I see:
Test amd64/self-tests failed (rc=2, on=amd64, time=0:01:05, log=amd64/self-tests/log)
... self-tests failed... what does it mean? is the kernel unreliable?
however I installed it and seems working fine.

---

### Post by Doug S on 2020-07-27
> **corradoventu said:**
> In the page [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.8-rc7/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.8-rc7/)
I see:
Test amd64/self-tests failed (rc=2, on=amd64, time=0:01:05, log=amd64/self-tests/log)
... self-tests failed... what does it mean? is the kernel unreliable?
however I installed it and seems working fine.The Ubuntu mainline build process appears to also build a lot of, if not all of, the tools and tests and such. It appears to fail while attempting to link "tools/testing/selftests/bpf/tools/build/bpftool/disasm.o".

This has nothing to do with the kernel itself, and it compiled fine.

However notice it is bpfilter related, and my bpfilter error issues started with -rc5

Without any proof, I think too much new code was added too deep into this -rc series. In my opinion, a violation of their own rules, but Linus himself did it, so who am I to comment. See the release notes for [-rc5]("https://lore.kernel.org/lkml/CAHk-=wgX5+Q_trdMPaaQZmko0Og_eqAYoyMa_8S3ie+1Us6rkw@mail.gmail.com/"), in particular:

```
In addition to the outright fixes, there's a few cleanups that are
just prep for 5.9. They all look good and simple too.
```Ya, no.

---

### Post by Doug S on 2020-07-28
> **Doug S said:**
> Kernel 5.8-rc5 is available,... 
I am getting some error:
```
Jul 13 07:01:08 s18 kernel: [    9.429363] bpfilter: Loaded bpfilter_umh pid 826
Jul 13 07:01:08 s18 kernel: [    9.432623] bpfilter: write fail -22
Jul 13 07:01:08 s18 kernel: [    9.432676] bpfilter: write fail -22
Jul 13 07:01:08 s18 kernel: [    9.458993] bpfilter: Loaded bpfilter_umh pid 836
Jul 13 07:01:08 s18 kernel: [    9.459132] bpfilter: write fail -22
Jul 13 07:01:08 s18 kernel: [    9.459185] bpfilter: write fail -22
```
It seems the default for iptables/nftables was changed. Couldn't run my VM's either. Do:

```
# update-alternatives --set iptables /usr/sbin/iptables-nft
# update-alternatives --set ip6tables /usr/sbin/ip6tables-nft
# update-alternatives --set arptables /usr/sbin/arptables-nft
# update-alternatives --set ebtables /usr/sbin/ebtables-nft
```and re-boot fixed.

References: [https://askubuntu.com/questions/1262629/on-new-linux-kernel-5-8rc7-in-ubuntu-20-docker-will-not-start]("https://askubuntu.com/questions/1262629/on-new-linux-kernel-5-8rc7-in-ubuntu-20-docker-will-not-start") and [https://wiki.debian.org/iptables]("https://wiki.debian.org/iptables")

---

### Post by fooman on 2020-07-28
Thanks for that Doug,  was wondering why my VPN would not not connect with 5.8.  That fixed it!  :guitar:

---

### Post by IanW on 2020-08-03
5.8 has now been released by Linus.

[https://lore.kernel.org/lkml/20200802220243.GA20003@Gentoo/T/](https://lore.kernel.org/lkml/20200802220243.GA20003@Gentoo/T/)

And has appeared in the PPA

[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.8/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.8/)

---

### Post by corradoventu on 2020-08-03
corrado@corrado-n4-gorilla-x:~$ uname -a
Linux corrado-n4-gorilla-x 5.8.0-050800-generic #202008022230 SMP Sun Aug 2 22:33:21 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
corrado@corrado-n4-gorilla-x:~$ inxi -SC
System:    Host: corrado-n4-gorilla-x Kernel: 5.8.0-050800-generic x86_64 bits: 64 Desktop: N/A 
           Distro: Ubuntu 20.10 (Groovy Gorilla) 
CPU:       Topology: Quad Core model: Intel Core i5-1035G1 bits: 64 type: MT MCP L2 cache: 6144 KiB 
           Speed: 2457 MHz min/max: 400/3600 MHz Core speeds (MHz): 1: 2062 2: 2796 3: 2878 4: 2939 5: 2774 6: 2736 7: 3418 
           8: 2147 
corrado@corrado-n4-gorilla-x:~$

---

### Post by Cavsfan on 2020-08-11
Kernel [5.8.1]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.8.1") is available.

Edit: Whoops, forgot this thread is for release candidate versions.

---

