---
title: "Kernel 4.1 RC (Release Candidate) series"
date: 2015-04-26
forum: Ubuntu Development Version
---

### Post by Doug S on 2015-04-26
Kernel 4.1 RC1 has been released on [Kernel.org]("https://www.kernel.org/"). I assume it will show up in [the Ubuntu Kernel PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") pretty quick.

O.K. so far, but haven't done much yet. Since the Ubuntu kernel configuration wasn't available yet, I just used the default for all the new configuration settings (and there were lots, which is normal for an RC1).

---

### Post by rrnbtter on 2015-04-27
Greetings,
It has quite a change list but one noticeable change in usability is an improvement in the menu mouse click sensitivity that has been persistent in Firefox. The 37.0.2 update didn't fix it but this morning the problem seem fixed with the kernel update.

---

### Post by Doug S on 2015-05-04
[Kernel 4.1RC2 is now available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.1-rc2-vivid/"). I have only a few hours on it. So far so good.

---

### Post by warren3 on 2015-05-05
Hi.

I have given this kernel a whirl with 15.04.  I was hoping 15.04 with its stock 3.19 kernel would solve my system lock-ups.  No joy, so I might as well try this and hope for the best.

---

### Post by rrnbtter on 2015-05-05
Greetings,
I have been using RC1 since yesterday morning with no issues. But getting ready to switch back to 3.19 for WW conversion.

---

### Post by tokyobadger on 2015-05-06
> **Doug S said:**
> [Kernel 4.1RC2 is now available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.1-rc2-vivid/"). I have only a few hours on it. So far so good.
I just tried 4.1RC2 and got a loop at login ie I couldn't login.

What are you running on?
I have the xorg-edgers ppa nvidia-349.16 on a 15.04 base with repos now pointed at Wily; everything fine on 4.0 Final.

---

### Post by QDR06VV9 on 2015-05-06
> **tokyobadger said:**
> I just tried 4.1RC2 and got a loop at login ie I couldn't login.

What are you running on?
I have the xorg-edgers ppa nvidia-349.16 on a 15.04 base with repos now pointed at Wily; everything fine on 4.0 Final.
tokyobadger have you tried this ppa [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
It is just a clean install of the nvidia drivers.
But rarely do we get the patch for nvidia early in kernel cycles.
Regards

---

### Post by tokyobadger on 2015-05-06
Thanks runrickus

I have not tried the mamarley ppa - are there advantages over the xorg-edgers ppa?

Re: nvidia patching - many years ago I used to roll my own kernels on "less automated" distros, issues with nvidia drivers at that time were almost always non-kernel-related, usually xorg; I switched to Ubuntu about 5 years ago as life got busier and I needed the more automated approach, just curious now as to why nvidia drivers now need patching for newer kernels

---

### Post by Doug S on 2015-05-06
> **tokyobadger said:**
> I just tried 4.1RC2 and got a loop at login ie I couldn't login.
What are you running on?
I have the xorg-edgers ppa nvidia-349.16 on a 15.04 base with repos now pointed at Wily; everything fine on 4.0 Final.I am running it on an otherwise 14.04 Ubuntu server, no GUI. I actually build my RC series kernels from the kernel.org source, and just use the Ubuntu kernel configuration file.
Also, I run with an additional, yet to be accepted or rejected, intel_pstate driver patch set.

---

### Post by tokyobadger on 2015-05-06
@Doug S: thanks for clarifying. Several iterations of difference. 

@others: still unclear as to why a new kernel would need patches for nvidia - and yes I will google myself too ;-)

---

### Post by QDR06VV9 on 2015-05-06
> **tokyobadger said:**
> Thanks runrickus

I have not tried the mamarley ppa - are there advantages over the xorg-edgers ppa?

Re: nvidia patching - many years ago I used to roll my own kernels on "less automated" distros, issues with nvidia drivers at that time were almost always non-kernel-related, usually xorg; I switched to Ubuntu about 5 years ago as life got busier and I needed the more automated approach, just curious now as to why nvidia drivers now need patching for newer kernels
For me it was just a cleaner install without pulling in a lot of other stuff like uvm etc etc
I was going to try to install this kernel a little later today though will let you know how it goes..
Regards

---

### Post by QDR06VV9 on 2015-05-06
So RC2 wont install with nvida
This is the output
```
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.1.0-040100rc2-lowlatency /boot/vmlinuz-4.1.0-040100rc2-lowlatency
[U][B]Error! Bad return status for module build on kernel: 4.1.0-040100rc2-lowlatency (x86_64)
Consult /var/lib/dkms/nvidia-349/349.16/build/make.log for more information.[/B][/U]
Setting up linux-image-4.1.0-040100rc2-lowlatency (4.1.0-040100rc2.201505032335) ...
```
So for fun I unistalled the nvidia driver and reinstall still produces 
```
DKMS: install completed.
Building initial module for 4.1.0-040100rc2-lowlatency
[U][B]ERROR (dkms apport): kernel package linux-headers-4.1.0-040100rc2-lowlatency is not supported
Error! Bad return status for module build on kernel: 4.1.0-040100rc2-lowlatency (x86_64)
Consult /var/lib/dkms/nvidia-349/349.16/build/make.log for more information.[/B][/U]
Setting up nvidia-libopencl1-349 (349.16-100ubuntu100~ppa0~vivid) ...
Setting up nvidia-opencl-icd-349 (349.16-100ubuntu100~ppa0~vivid) ...
Setting up nvidia-prime (0.8.1) ...
nvidia-prime start/running, process 13631
Setting up nvidia-settings (349.16-100ubuntu100~ppa0~vivid) ...
Processing triggers for initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-4.1.0-040100rc2-lowlatency
Processing triggers for libc-bin (2.21-0ubuntu4) ...

```

Also this from [http://rglinuxtech.com/?p=1426](http://rglinuxtech.com/?p=1426)

> Some have suggested fixing these errors by simply editing the offending  kernel code to disable the GPL-only rule, but this is in fact the wrong  thing to do.  
 Either the kernel development team makes the change, or  NVIDIA has to change their code.
Regards

---

### Post by zika on 2015-05-07
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2015-05-07-unstable/BUILD.LOG.amd64](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2015-05-07-unstable/BUILD.LOG.amd64) :

```
[COLOR=#000000]-- dchroot -c precise-amd64 --directory=/home/kernel/COD/linux -- fakeroot debian/rules clean[/COLOR]I: [precise-amd64-10677425-f446-4062-89c8-88109cf637f7 chroot] Running command: **â&#8364;&#339;fakeroot debian/rules cleanâ&#8364;**
/usr/bin/fakeroot: line 178: debian/rules: No such file or directory
-- dchroot -c precise-amd64 --directory=/home/kernel/COD/linux -- /bin/bash
I: [precise-amd64-53e272b0-e867-4497-a90c-9809b7c25666 chroot] Running command: **â&#8364;&#339;/bin/bashâ&#8364;**
/bin/bash: line 1: debian/rules: No such file or directory
/usr/bin/fakeroot: line 178: debian/rules: No such file or directory
```

---

### Post by QDR06VV9 on 2015-05-07
Hi zika is that a "make" error?
or just info?
Long time no see.
If it is make error
maybe try
```
if dpkg -l | grep -q '^ii\s\+make\s'; then
    sudo apt-get --reinstall install make
else
    sudo apt-get install make
fi
```
Maybe I am not understanding.
Kind Regards

---

### Post by zika on 2015-05-07
> **runrickus said:**
> Hi zika is that a "make" error?
or just info?
Long time no see.
If it is make error
maybe try
```
if dpkg -l | grep -q '^ii\s\+make\s'; then
    sudo apt-get --reinstall install make
else
    sudo apt-get install make
fi
```
Maybe I am not understanding.
Kind RegardsMy bad, I've edited my previous post and added relevant URL... ;)
Mea culpa.
Update&#8321;: Resolved...

---

### Post by syntaxerror74 on 2015-05-08
> **zika said:**
> My bad, I've edited my previous post and added relevant URL... ;)
Watch out for the colon at the end, it breaks your link :rolleyes:

```
cat $i | sed -e 's/PKGVER/4.1.0/g' 
```
Ugh. UUOC never seems to die out...(and I thought these folks may have 
way more scripting experience than I have, and I'm not a rookie myself)

---

### Post by zika on 2015-05-09
> **syntaxerror74 said:**
> Watch out for the colon at the end, it breaks your link :rolleyes:No *syntax error* anymore... ;) Corrected. Somehow Forum remembered that colon even though I've inserted space between URL and colon. Thank You. In the meantime real *syntax error* from the content of aforementioned URL was also corrected... ;)

---

### Post by rrnbtter on 2015-05-10
Greetings,
Wily 4.0.2 Kernel up and running

System:    Host: rrnbtter-Satellite-L305 Kernel: 4.0.2-040002-generic i686 (32 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.10 wily

---

### Post by zika on 2015-05-10
> **rrnbtter said:**
> Greetings,
Wily **4.0**.2 Kernel up and running

System:    Host: rrnbtter-Satellite-L305 Kernel: **4.0**.2-040002-generic i686 (32 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.10 wily[http://ubuntuforums.org/showthread.php?t=2266435&highlight=kernel+4.0+final](http://ubuntuforums.org/showthread.php?t=2266435&highlight=kernel+4.0+final)

---

### Post by rrnbtter on 2015-05-10
Greetings,
Perhaps I should have started a new thread for the Wily Kernel. All the previous are for Vivid which is off topic.

---

### Post by Doug S on 2015-05-12
> **rrnbtter said:**
> Perhaps I should have started a new thread for the Wily Kernel. All the previous are for Vivid which is off topic.Herein, we always have a thread going for the current RC (Release Candidate) series, independent of the version of Ubuntu running on the computer.


Can anyone confirm or deny: For any Kernel 4.1RC1 or 2 or 3: After a suspend, only CPU 0 comes back on-line.

For Kernel 4.0 things work fine for me upon resume from suspend.
This issue could well be processor dependent, mine is an i7-2600K.

---

### Post by Doug S on 2015-05-13
> **Doug S said:**
> Can anyone confirm or deny: For any Kernel 4.1RC1 or 2 or 3: After a suspend, only CPU 0 comes back on-line.... 16 kernel compiles later... 

I bisected the kernel. The culprit seems to be:
```
3c18d447b3b36a8d3c90dc37dfbd363cdb685d0a is the first bad commit
commit 3c18d447b3b36a8d3c90dc37dfbd363cdb685d0a
Author: Juri Lelli <juri.lelli@arm.com>
Date:   Tue Mar 31 09:53:37 2015 +0100

    sched/core: Check for available DL bandwidth in cpuset_cpu_inactive()

    Hotplug operations are destructive w.r.t. cpusets. In case such an
    operation is performed on a CPU belonging to an exlusive cpuset, the
    DL bandwidth information associated with the corresponding root
    domain is gone even if the operation fails (in sched_cpu_inactive()).

    For this reason we need to move the check we currently have in
    sched_cpu_inactive() to cpuset_cpu_inactive() to prevent useless
    cpusets reconfiguration in the CPU_DOWN_FAILED path.

    Signed-off-by: Juri Lelli <juri.lelli@arm.com>
    Signed-off-by: Peter Zijlstra (Intel) <peterz@infradead.org>
    Cc: Juri Lelli <juri.lelli@gmail.com>
    Link: http://lkml.kernel.org/r/1427792017-7356-2-git-send-email-juri.lelli@arm.com
    Signed-off-by: Ingo Molnar <mingo@kernel.org>

:040000 040000 10f8d81afdc8e625f8e6720883d3eb42c28d452b c08264528890941bad35d5d4cc134c03f259c534 M      kernel
```EDIT: I made a mistake somewhere. I'll post the correct commit culprit once I figure it out.

EDIT 2: ... another bunch of kernel compiles later ... Proper culprit identified and edited above. The fix is 533445c6e533 "sched/core: Fix regression in cpuset_cpu_inactive() for suspend", which I am trying now.
EDIT 3: Patch works fine and fixes the issue.

---

### Post by Cavsfan on 2015-05-14
I don't know if you care about this or not but it is some news yesterday May 13th about kernel 4.1 being on the final release of Wily.

> Being based on Vivid, Ubuntu 15.10 uses its Linux 3.19 kernel packages,  but the Ubuntu 
developers announced today, after an Ubuntu Kernel Team  meeting, that they will switch 
soon to Linux kernel 4.0 and that the  final release of Ubuntu 15.10 (Wily Werewolf) will 
most likely be  powered by Linux kernel 4.1.

[http://linux.softpedia.com/blog/Ubuntu-15-10-Wily-Werewolf-to-Use-Linux-Kernel-4-1-Most-Likely-481002.shtml](http://linux.softpedia.com/blog/Ubuntu-15-10-Wily-Werewolf-to-Use-Linux-Kernel-4-1-Most-Likely-481002.shtml)

I was wondering myself as to which one 15.10 would go with.

---

### Post by dino99 on 2015-05-14
That one works smootly

linux (4.0.0-1.1) wily; urgency=low

  [ Upstream Kernel Changes ]
  * rebase to v4.0.1
  * rebase to v4.0-rc5
    - LP: #1428947
    - LP: #1410704
    - LP: #1412800
    - LP: #1400215
    - LP: #1411193
    - LP: #1412800
    - LP: #1408295
  * rebase to v4.0-rc6
    - LP: #1436745
  * rebase to v4.0-rc7
  * rebase to v4.0 final

 -- Leann Ogasawara <email address hidden>  Wed, 06 May 2015 06:29:00 -0700

---

### Post by Doug S on 2015-05-17
> **Doug S said:**
> Can anyone confirm or deny: For any Kernel 4.1RC1 or 2 or 3: After a suspend, only CPU 0 comes back on-line.The fix for this issue (533445c6e533 "sched/core: Fix regression in cpuset_cpu_inactive() for suspend") will be in kernel 4.1RC4.

---

### Post by Doug S on 2015-05-18
Kernel 4.1rc4 is [available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D"). I have been running it for 7 hours or so without issues.

---

### Post by mrfelker on 2015-05-19
I have not got Wily to boot with the latest Wily kernel from the lmainline (4.04).  Has anybody else boot 4.04?

---

### Post by Doug S on 2015-05-25
Kernel 4.1RC5 is [available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.1-rc5-unstable/").

Both the Ubuntu, and my own compiled, versions of kernels are not working for me at the moment. I am still recovering things after a hard disk failure two days ago on my test computer. My issues are NOT specific to this kernel series, but rather I have done something wrong while recovering things (and haven't looked into it yet).

---

### Post by ronacc on 2015-05-25
I have the 64bit rc5 ( ubuntu version ) running here , seems good so far .

---

### Post by den_ on 2015-05-25
My system froze after a while with rc5, 14.04, Intel Sandy Bridge Graphics and oibaf repo for mesa and Intel drivers, while I was using VirtualBox and Win 7 guest. Besides that, other stuff seem to work well.

---

### Post by Doug S on 2015-06-01
Kernel 4.1RC6 is [available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.1-rc6-unstable/").
It will be several hours before I get a chance to try it.

---

### Post by zika on 2015-06-06
For those that want to try a glimpse of AMDGPU: drm-next... ;)

---

### Post by Gaylaird_Culbreth on 2015-06-06
Today's Mainline Daily is the first kernel that isn't giving me the annoying "GPU Pipe A FIFO underun" message every time I shur down or reboot my Asus Chromebox. More better Haswell graphics I hope. Nice!

---

### Post by Ian_Worrall on 2015-06-08
Kernel 4.1 has gone to rc7. Not in Mainline PPA yet.

EDIT: - RC7 now in [Mainline PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.1-rc7-unstable/").

---

### Post by harry332 on 2015-06-11
Linux 4.0.0-1 is now in Launchpad.
[https://launchpad.net/ubuntu/+source/linux/4.0.0-1.1](https://launchpad.net/ubuntu/+source/linux/4.0.0-1.1)
The build is still at the "new" stage and not yet in proposed repo.
I installed it manually and it is working fine, at least in Gnome-shell DE with Intel GPU.

---

### Post by Doug S on 2015-06-14
Seems there is the rather unusual kernel 4.1RC8 this cycle. Not in [Ubuntu PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") yet.

Edit: 
It is [there]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.1-rc8-unstable/") now.

---

### Post by zika on 2015-06-16
> **zika said:**
> For those that want to try a glimpse of AMDGPU: drm-next... ;)Very nice prospects for AMD in 4.2 ... ;) (amdgpu& other(s))

---

### Post by Ian_Worrall on 2015-06-16
4.1 went to rc8 because:-

1: Some changes to md still weren't quite there
2: Linus is on vacation and didn't want to open 4.2 from the beach.

---

### Post by philinux on 2015-06-22
Released
[http://www.omgubuntu.co.uk/2015/06/linux-4-1-kernel-new-features?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2015/06/linux-4-1-kernel-new-features?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by QDR06VV9 on 2015-06-22
> **zika said:**
> Very nice prospects for AMD in 4.2 ... ;) (amdgpu& other(s))  And This ! >   Highlights of Linux 4.1 include:      EXT4 gains file-system level encryption (thanks to Google)     Logitech lg4ff driver improves ‘force feedback’ for gaming wheels     Toshiba laptop driver gains USB sleep charging and backlight improvements     Rumble support for Xbox One controller     Better battery reporting in Wacom tablet driver     Various misc. power improvements for both ARM and x86 devices     Samsung Exynos 3250 power management improvements     Support for the Bamboo Pad     Lenovo OneLink Pro Dock gains USB support     Support for Realtek 8723A, 8723B, 8761A, 8821 Wi-Fi cards

```
 uname -r
4.1.0-040100-generic

```
About 7 hours under heavy use ,I had a total lock-up. Had to hard power down.
That's a first for this lappy, Logs show nothing. I still have it installed, just going through normal pace now.

---

### Post by Doug S on 2015-06-24
I only got around to trying kernel 4.1 yesterday and today. All seems fine.

dmidecode seems to be working again, due to [a fix in the kernel configuration.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1462822")

---

### Post by dino99 on 2015-06-25
> **Doug S said:**
> I only got around to trying kernel 4.1 yesterday and today. All seems fine.

dmidecode seems to be working again, due to [a fix in the kernel configuration.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1462822")

Thanks Doug for finding that issue.

---

### Post by steveo314 on 2015-06-25
Using 4.1 final on xubuntu wily and don't have any issues.

---

### Post by fooman on 2015-07-02
installed 4.1.1 yesterday...all seems to be running great!

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.1.1-unstable/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.1.1-unstable/)

```
Current Date/Time: Thu Jul  2 16:57:13 EDT 2015
Distro Release: Ubuntu Wily Werewolf (development branch)
Kernel Release: Linux 4.1.1-040101-generic
Gnome Release: GNOME Shell 3.16.2
Unity Release: unity 7.3.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 480/PCIe/SSE2
OpenGL version string:  4.2.0 NVIDIA 304.125
```

---

