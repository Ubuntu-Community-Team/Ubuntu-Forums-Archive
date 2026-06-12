---
title: "Kernel 4.12RC (Release Candidate) series"
date: 2017-05-14
forum: Ubuntu Development Version
---

### Post by Doug S on 2017-05-14
Kernel 4.12-rc1 is [available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.12-rc1/"). It is a [large change]("https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.12-rc1-Released")

The BFQ scheduler has been added, but so far I haven't figured out how to actually use it (and I started a few days ago with some kernel somewhere between 4.11 and 4.12-rc1). Perhaps naively, I thought it would appear on this list:

```
$ cat /sys/block/sda/queue/scheduler
noop deadline [cfq]

```I've tried a few kernel configurations.

---

### Post by IanW on 2017-05-15
Pretty sure you meant:-

> **Doug S said:**
> Kernel 4.1**2**-rc1 is [available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.12-rc1/"). It is a [large change]("https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.12-rc1-Released")

:P

---

### Post by Doug S on 2017-05-16
> **IanW said:**
> Pretty sure you meant:-



:PYes, Thanks. Fixed.

---

### Post by #&amp;thj^% on 2017-05-17
> **Doug S said:**
> Kernel 4.12-rc1 is [available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.12-rc1/"). It is a [large change]("https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.12-rc1-Released")

The BFQ scheduler has been added, but so far I haven't figured out how to actually use it (and I started a few days ago with some kernel somewhere between 4.11 and 4.12-rc1). Perhaps naively, I thought it would appear on this list:

```
$ cat /sys/block/sda/queue/scheduler
noop deadline [cfq]

```I've tried a few kernel configurations.

Doug if you know different, and I suspect you do.;)
This is all I know to date:
> BFQ can be found in Linux from 4.12.0, but only for the new blk-mq  framework. The version for blk of BFQ can instead be found in the  following systems. First, BFQ is the default I/O scheduler in [Manjaro]("http://manjaro.org"), [Mageia]("https://www.mageia.org/"), [OpenMandriva]("http://openmandriva.org"), [Sabayon]("http://www.sabayon.org"), [Arch Linux ARM]("http://archlinuxarm.org") (for Marvell Kirkwood) and [ROSA]("http://www.rosalab.com"), as well as in the [Zen Kernel]("http://zen-kernel.org/"), the [pf-kernel]("http://pf.natalenko.name/"), [CyanoGenMod]("http://cyanogenmod.org") for several devices, and many kernels for smartphones. In addition, BFQ is optionally available in [Arch]("http://www.archlinux.org/"), [openSUSE]("http://opensuse.org/"), [PCLinuxOS]("http://www.pclinuxos.com/") and [Gentoo]("http://www.gentoo.org/"). We record a few tens of downloads per day from people using other distributions as well. The feedback we have received so far basically confirms the expected latency drop and throughput boost in everyday use.
But I was able to get it with 4.11
```
cat /sys/block/sda/queue/scheduler
noop deadline cfq [bfq] 

```
Tried to find the links I followed.... but I've not yet found them.

---

### Post by Doug S on 2017-05-17
> **1fallen said:**
> But I was able to get it with 4.11
```
cat /sys/block/sda/queue/scheduler
noop deadline cfq [bfq] 

```
Tried to find the links I followed.... but I've not yet found them.Well, at least I know if I ever figure out how to get it to work, it will appear in the list. Thanks.

On another note, I noticed my console screen never blanks now, as of kernel 4.12-rc1 (Ubuntu server edition 16.04.2). This appears to not be a bug and is by design. The relevant commit is copied below:```
$ [COLOR="#FF0000"]git show a4199f5[/COLOR]
commit a4199f5eb8096d63828f7333fa45650a7b0a99ed
Author: Tim Gardner <tim.gardner@canonical.com>
Date:   Wed Mar 22 09:07:20 2017 -0600

    tty: Disable default console blanking interval

    BugLink: http://bugs.launchpad.net/bugs/869017

    Console blanking is not enabling DPMS power saving (thereby negating any
    power-saving benefit), and is simply turning the screen content blank. This
    means that any crash output is invisible which is unhelpful on a server
    (virtual or otherwise).

    Furthermore, CRT burn in concerns should no longer govern the default case.
    Affected users could always set consoleblank on the kernel command line.

    Signed-off-by: Tim Gardner <tim.gardner@canonical.com>
    Cc: Greg Kroah-Hartman <gregkh@linuxfoundation.org>
    Cc: Jiri Slaby <jslaby@suse.com>
    Cc: Adam Borowski <kilobyte@angband.pl>
    Cc: Scot Doyle <lkml14@scotdoyle.com>
    Signed-off-by: Greg Kroah-Hartman <gregkh@linuxfoundation.org>

diff --git a/drivers/tty/vt/vt.c b/drivers/tty/vt/vt.c
index 5c4933b..9c99452 100644
--- a/drivers/tty/vt/vt.c
+++ b/drivers/tty/vt/vt.c
@@ -181,7 +181,7 @@ int console_blanked;

 static int vesa_blank_mode; /* 0:none 1:suspendV 2:suspendH 3:powerdown */
 static int vesa_off_interval;
-static int blankinterval = 10*60;
+static int blankinterval;
 core_param(consoleblank, blankinterval, int, 0444);

 static DECLARE_WORK(console_work, console_callback);

```I have put a blank time back into grub (still short because I was debugging):
```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 [COLOR="#FF0000"]consoleblank=60[/COLOR]"
```

---

### Post by #&amp;thj^% on 2017-05-17
Still looking for the links, and this may or may not be useful. (For you specifically)
From my bash history I installed like so:
```
sudo apt-get install kernel-wedge makedumpfile xmlto docbook-utils transfig sharutils
sudo apt-get install kernel-wedge makedumpfile xmlto docbook-utils transfig sharutils
sudo  apt-get source linux-image-$(uname -r) ##Or point to your specific version##
```

Once you get all your patching done, you will also have to add it to Grub:
```
sudo nano /etc/default/grub
```
Mine looks like this so it will load.

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[COLOR=#ff0000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash elevator=bfq"[/COLOR]
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



```

Anyway if this is useful Great, if not...Just kindly disregard.:)

---

### Post by Doug S on 2017-05-17
Well, O.K. I added the specific "elevator" line to my grub and now the computer just crashes during boot.

```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 consoleblank=300 [COLOR="#FF0000"]elevator=bfq[/COLOR]"
```

Running this:
```
$ [COLOR="#FF0000"]scripts/diffconfig .config-4.12.0-041200rc1-generic .config[/COLOR]
-DEBUG_INFO_DWARF4 y
-DEBUG_INFO_REDUCED n
-DEBUG_INFO_SPLIT n
-GDB_SCRIPTS y
 DEBUG_INFO y -> n
 IOSCHED_BFQ n -> y
+BFQ_GROUP_IOSCHED y

```if I run a stock 4.12-rc1 kernel then I get this, which makes sense because it isn't there:```
May 17 15:41:55 s15 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/[COLOR="#FF0000"]vmlinuz-4.12.0-rc1-stock[/COLOR] root=UUID=bcbc624b-892b-46ca-9e9e-102daf644170 ro ipv6.disable=1 consoleblank=300 [COLOR="#FF0000"]elevator=bfq[/COLOR] crashkernel=384M-:128M
May 17 15:41:55 s15 kernel: [    2.588339] I/O scheduler bfq not found
May 17 15:41:55 s15 kernel: [    2.975534] I/O scheduler bfq not found
May 17 15:41:55 s15 kernel: [    4.064114] I/O scheduler bfq not found
```
If I run the first kernel, but without specifying the "elevator=bfq" in the command line, I get:
```
May 17 23:52:59 s15 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/[COLOR="#FF0000"]vmlinuz-4.12.0-rc1-bfq[/COLOR] root=UUID=bcbc624b-892b-46ca-9e9e-102daf644170 ro ipv6.disable=1 consoleblank=300 crashkernel=384M-:128M
May 17 23:52:59 s15 kernel: [    1.419558] io scheduler bfq registered
```But it still doesn't appear in the list:
```
$ [COLOR="#FF0000"]cat /sys/block/sda/queue/scheduler[/COLOR]
noop deadline [cfq]

```

---

### Post by #&amp;thj^% on 2017-05-18
Thanks for trying.
Doug i have not yet tried with kernel 4.12 yet so no relevant help from me.:(
And if the truth be told here, at least mine;)
I find much better performance schedules with just the Low-Lat kernels.
I run them so often...guess that makes me a fan boy.:D
Will take a look again @BFQ later in the release cycle.
Don't know if you have had a look here yet? [http://git.kernel.dk/cgit/linux-block/commit/?h=for-next&id=0789bd7bdb5bd036fe3df96c19528f46127a0160](http://git.kernel.dk/cgit/linux-block/commit/?h=for-next&id=0789bd7bdb5bd036fe3df96c19528f46127a0160)
Which really suprise's me, due to fact that Torvalds has been very stern in the past about not having another schedule moudule in the kernel. (A bit dated:[http://yarchive.net/comp/linux/scheduler.html](http://yarchive.net/comp/linux/scheduler.html))

---

### Post by mrfelker on 2017-05-19
Just installed 4.12.0-041200rc1-generic
on Ubuntu MATE.     No problems yet.    I have to follow the discussion for tuning.

---

### Post by IanW on 2017-05-22
Kernel 4.12rc2 has arrived in the [PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.12-rc2/")

All builds seem to have succeeded.

---

### Post by aljosa2 on 2017-05-22
**Kernel 4.12 ACPI warnings, bugs and other errors on Asus G752VS**
[https://bugzilla.kernel.org/show_bug.cgi?id=195843](https://bugzilla.kernel.org/show_bug.cgi?id=195843)

---

### Post by lonniehenry-gmail on 2017-05-22
Unsure what has happened.  I have a Elantech touchpad that works with 4.12rc1 kernel but does not with 4.12rc2  or new daily kernels. Asus u305ua zenbook with Mate 17.10 updated.
 Any ideas what changed and how to fix.

---

### Post by #&amp;thj^% on 2017-05-22
I had the same... I just made a **"/etc/X11/xorg.conf.d" **file
And named it "**synaptics.conf**"
I'll bet if you look there, you won't see one...Right?
The Contents for mine is as follows:
```
Section "InputClass"
Identifier "Touchpad" # required
MatchIsTouchpad "yes" # required
Driver "synaptics" # required
Option "MinSpeed" "0.5"
Option "MaxSpeed" "1.0"
Option "AccelFactor" "0.075"
Option "TapButton1" "1"
Option "TapButton2" "2" # multitouch
Option "TapButton3" "3" # multitouch
Option "VertTwoFingerScroll" "1" # multitouch
Option "HorizTwoFingerScroll" "1" # multitouch
Option "VertEdgeScroll" "1"
Option "CoastingSpeed" "8"
Option "CornerCoasting" "1"
Option "CircularScrolling" "1"
Option "CircScrollTrigger" "7"
Option "EdgeMotionUseAlways" "1"
Option "LBCornerButton" "8" # browser "back" btn
Option "RBCornerButton" "9" # browser "forward" btn
EndSection
```
Had to reboot for it to work.

---

### Post by lonniehenry-gmail on 2017-05-23
Didn't work for me.  I will keep looking for a solution.  Thanks for the suggestion 1fallen.

---

### Post by lonniehenry-gmail on 2017-05-25
Touchpad corrected in 5/25 daily.

---

### Post by #&amp;thj^% on 2017-05-25
> **lonniehenry-gmail said:**
> Touchpad corrected in 5/25 daily.
Thanks for posting this...will  give it go tomorrow. 
Too many honey do's today. :)

---

### Post by Chanath on 2017-05-26
> **lonniehenry-gmail said:**
> Unsure what has happened.  I have a Elantech touchpad that works with 4.12rc1 kernel but does not with 4.12rc2  or new daily kernels. Asus u305ua zenbook with Mate 17.10 updated.
 Any ideas what changed and how to fix.

Would this kernel make touchpad work? I was told that the touchpad is from Synaptics. Xinit doesn't even see it.

---

### Post by lonniehenry-gmail on 2017-05-26
Chanath, the short answer is I don't know.  The long answer is I tried the 5/25 daily kernel and it worked.  4.12rc2 didn't and 412rc1 did work.  All 3 kernels load the same mods so I don't know what other thing causes these results.  In my case the elantech needed elan_i2c and it appeared in all kernels.  So....

---

### Post by zika on 2017-05-29
**HeadsUp**: Mainline: 999 from 27.05.17 forward and 4.12rc3 do not boot on several machines of mine... 994 (27.05.17.) does boot nice.
Update&#8321;: 994 (starting 30.05.17.) joined the club...

---

### Post by #&amp;thj^% on 2017-05-29
Thanks zika ;)...I can also confirm on 17.10 **"no boot"**.
Oddly it boots with 17.04.
```
 $ inxi -S && echo $DESKTOP_SESSION 
System:    Host: me-750-417c Kernel: 4.12.0-041200rc3-lowlatency x86_64 (64 bit)
           Desktop: Gnome 3.24.1 Distro: Ubuntu 17.04
           gnome-wayland

```
Still can not get [bfq] to work yet though.
```
$ cat /sys/block/sda/queue/scheduler
noop deadline [cfq] 
```
@Doug S, have you had any luck or progress yet?

---

### Post by Doug S on 2017-05-29
I was away and missed -rc2 week. I use my main 16.04.2 test server for this stuff, and yes -rc3 does not boot for me either.
I observe that there are significant kernel configuration changes between -rc1 and -rc3, so I compiled a -rc3 using the -rc1 Ubuntu kernel configuration. However, it doesn't boot either. I'll start a kernel bisection, perhaps later today.

> **1fallen said:**
> 
Still can not get [bfq] to work yet though.
```
$ cat /sys/block/sda/queue/scheduler
noop deadline [cfq] 
```
@Doug S, have you had any luck or progress yet?No, I have made no progress on the bfq issue.

---

### Post by Doug S on 2017-05-29
O.K. the bad commit is:```
cbed27cdf0e3f7ea3b2259e86b9e34df02be3fe4 is the first bad commit
commit cbed27cdf0e3f7ea3b2259e86b9e34df02be3fe4
Author: Mikulas Patocka <mpatocka@redhat.com>
Date:   Tue Apr 18 15:07:11 2017 -0400

    x86/PAT: Fix Xorg regression on CPUs that don't support PAT
```And with that commit number, I finally found [an e-mail thread]("https://lkml.org/lkml/2017/5/29/534") about it.

---

### Post by rrnbtter on 2017-05-30
Greetings,
rrnbtter@rrnbtter-110-15ISK:~$ inxi1
inxi -Sxx && $DESKTOP_SESSION
System:    Host: rrnbtter-110-15ISK Kernel: 4.12.0-041200rc3-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome  (Gtk 3.22.15-0ubuntu1) dm: lightdm
           Distro: Ubuntu Artful Aardvark (development branch)
ubuntu

---

### Post by zika on 2017-05-30
> **1fallen said:**
> Thanks zika ;)...I can also confirm on 17.10 **"no boot"**.
Oddly it boots with 17.04.```
 $ inxi -S && echo $DESKTOP_SESSION 
System:    Host: me-750-417c Kernel: 4.12.0-041200rc3-lowlatency x86_64 (64 bit)
           Desktop: Gnome 3.24.1 Distro: Ubuntu 17.04
           gnome-wayland
```That is an insightfull detail. Good to know.
Update&#8321;: 30.05.17. 996 does work...

---

### Post by Doug S on 2017-05-30
> **zika said:**
> That is an insightfull detail. Good to know.It is a processor dependent problem (I think). So, I am wondering if processor differences was actually the difference here.

> **zika said:**
> Update&#8321;: 30.05.17. 996 does work...I can not find build 996. The daily from today still doesn't work for me. I did it two ways, from the actual Ubuntu daily compiled kernel and also from the kernel.org tree, updating and checking out -rc3+ to the latest commit (3f173bde7e4320211e77a83f936fb754e7591006) and compiling myself.

---

### Post by #&amp;thj^% on 2017-05-30
> **Doug S said:**
> It is a processor dependent problem (I think). So, I am wondering _if processor differences was actually the difference here._



Was wondering the same myself. :confused: The Email Link you provided was a good thought provoking read.:)
> **Doug S said:**
> The daily from today still doesn't work for me. I did it two ways, from the actual Ubuntu daily compiled kernel and also from the kernel.org tree, updating and checking out -rc3+ to the latest commit (3f173bde7e4320211e77a83f936fb754e7591006) and compiling myself.
I have not yet tried 4.12rc3 on 16.04....but it works on 17.04.....<<<But not on 17.10>>> Still no boot for me.
[ CPU: Intel i5-6400 (4) @ 3.300GHz]

---

### Post by Doug S on 2017-05-30
Here is [another link]("http://marc.info/?l=linux-kernel&m=149616508331421&w=2") to the thread I found about the no boot issue. I have added my test results to the end of the thread, not being aware of progress in the meantime. My results were consistent with the other two that reported their results for the 3 tests.

---

### Post by zika on 2017-05-31
> **Doug S said:**
> I can not find build 996.drm-next
Update&#8321;: As of today 996(drm-next) does not boot either.
HU [https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/unstable?field.series_filter=artful](https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/unstable?field.series_filter=artful)
4.12.0-0.1 does boot
4.12.0-1.2 does not... (skip autoremove ... ;))

---

### Post by #&amp;thj^% on 2017-05-31
Ok I just installed the .debs
```
inxi -Sxxx && echo $DESKTOP_SESSION
System:Host: me-750-417c Kernel: 4.12.0-041200rc3-lowlatency x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.2 (Gtk 3.22.15-0ubuntu1) info: gnome-shell dm: gdm3
           Distro: Ubuntu Artful Aardvark (development branch)
           gnome
           loginctl show-session 4 -p Type 
          _** Type=x11**_


```

---

### Post by Doug S on 2017-06-01
About our failing to boot issue, I found [this]("http://marc.info/?l=linux-kernel&m=149633715201838&w=2").
I'm doing "git pull"s a couple of times a day, and should notice when it gets there.

---

### Post by #&amp;thj^% on 2017-06-01
> **Doug S said:**
> About our failing to boot issue, I found [this]("http://marc.info/?l=linux-kernel&m=149633715201838&w=2").
I'm going "git pull"s a couple of times a day, and should notice when it gets there.

Thanks Doug your hard work is very much appreciated!
Kind Regards

---

### Post by mrfelker on 2017-06-01
Kernel 4.12rc3 fails to boot on a physical drive or in a VMware WS 12.5.6 VM.   Since rc2 works in both instances, rc3 seems to be a regression.     Anybody else had different result?.

---

### Post by mrfelker on 2017-06-01
4.12rc3 did boot in a Virtualbox (testbuild 5.23).    On my physical machine, the compiler was complaining about possible missing firm for 4.12rc3 but not rc2.   Then it would not boot rc3 but will boot rc2.   

My host is openSUSE Leap 42.3.

---

### Post by Doug S on 2017-06-02
For the -rc3 will not boot issue, originally found by zika, the fix is now in the mainline tree:```
$ [COLOR="#FF0000"]git show c08d517[/COLOR]
commit c08d517480ea342cc43acdacc5cf4a795e18151d
Author: Ingo Molnar <mingo@kernel.org>
Date:   Thu Jun 1 15:52:23 2017 +0200

    Revert "x86/PAT: Fix Xorg regression on CPUs that don't support PAT"

    This reverts commit cbed27cdf0e3f7ea3b2259e86b9e34df02be3fe4.
```I'm busy with something else at the moment and so can not make a kernel to try it right now. Pretty much tested by many people, including me, already though.

EDIT:```
cod/tip/daily/2017-06-02 mainline build
These binary packages represent builds of the mainline or stable Linux kernel tree at the commit below:

  cod/tip/daily/2017-06-02 (3b1e342be265f7df915c68c7c6e450956d8865aa)

```that daily commit is after the reversion commit, so the daily should boot fine.

---

### Post by zika on 2017-06-04
> **Doug S said:**
> For the -rc3 will not boot issue, originally found by zika, the fix is now in the mainline tree:```
$ [COLOR=#FF0000]git show c08d517[/COLOR]
commit c08d517480ea342cc43acdacc5cf4a795e18151d
Author: Ingo Molnar <mingo@kernel.org>
Date:   Thu Jun 1 15:52:23 2017 +0200

    Revert "x86/PAT: Fix Xorg regression on CPUs that don't support PAT"

    This reverts commit cbed27cdf0e3f7ea3b2259e86b9e34df02be3fe4.
```I'm busy with something else at the moment and so can not make a kernel to try it right now. Pretty much tested by many people, including me, already though.

EDIT:```
cod/tip/daily/2017-06-02 mainline build
These binary packages represent builds of the mainline or stable Linux kernel tree at the commit below:

  cod/tip/daily/2017-06-02 (3b1e342be265f7df915c68c7c6e450956d8865aa)

```that daily commit is after the reversion commit, so the daily should boot fine.999 works now, writing this from it. Nice. Thank You.

---

### Post by Doug S on 2017-06-05
kernel [4.12-rc4 is available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.12-rc4/"). It boots fine on my test server.```
$ uname -a
Linux s15 4.12.0-041200rc4-generic #201706042031 SMP Mon Jun 5 00:32:36 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by #&amp;thj^% on 2017-06-08
Dang these low-lat kernels are just getting better and better. (Much bigger also ;))
Ran it pretty hard yesterday Encoding some DVD's with Handbrake (with 2 pass) and CPU seldom ran higher than 50%. (Kudo's)
With Arch I run at least 80 to 96% and of course the heat goes up>>>but not bad, well under my comfort level. :D
```
inxi -C && uname -r
CPU: Quad core Intel Core i5-6400 (-MCP-) cache: 6144 KB 
        clock speeds: max: 3300 MHz 1: 2294 MHz 2: 911 MHz 3: 1033 MHz 4: 1512 MHz
        4.12.0-041200rc4-lowlatency


```
But still no luck with the bfq issue.
Greetz to zika! :)

EDIT: BTW has any one had any luck with:
```
sudo grep -i switcheroo /boot/config-*
[sudo] password for me: 
/boot/config-4.10.0-22-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-4.12.0-041200rc3-lowlatency:CONFIG_VGA_SWITCHEROO=y
/boot/config-4.12.0-041200rc4-lowlatency:CONFIG_VGA_SWITCHEROO=y


```

---

### Post by Rustan on 2017-06-15
How to enable BFQ on Kernel v.4.12 series?
CONFIG_SCSI_MQ_DEFAULT=y *or* scsi_mod.use_blk_mq=1

```
cat /sys/block/sd*/queue/scheduler
[mq-deadline] kyber bfq none
[mq-deadline] kyber bfq none
```

---

### Post by Doug S on 2017-06-15
> **Rustan said:**
> How to enable BFQ on Kernel v.4.12 series?
CONFIG_SCSI_MQ_DEFAULT=y *or* scsi_mod.use_blk_mq=1

```
cat /sys/block/sd*/queue/scheduler
[mq-deadline] kyber bfq none
[mq-deadline] kyber bfq none
```If I set CONFIG_SCSI_MQ_DEFAULT=y in my kernel configuration, it doesn't work for me. First, the unchanged Ubuntu kernel:

```
$ [COLOR="#FF0000"]cat /sys/block/sd?/queue/scheduler[/COLOR]
noop deadline [cfq]
noop deadline [cfq]

$ [COLOR="#FF0000"]uname -a[/COLOR]
Linux s15 [COLOR="#FF0000"]4.12.0-041200rc5-generic[/COLOR] #201706112031 SMP Mon Jun 12 00:32:34 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```Then alter the kernel configuration (I also disable some debug stuff, halving the compile time and kernel size): ```

[COLOR="#FF0000"]$ scripts/diffconfig .config-4.12.0-041200rc5-generic .config[/COLOR]
-DEBUG_INFO_DWARF4 y
-DEBUG_INFO_REDUCED n
-DEBUG_INFO_SPLIT n
-GDB_SCRIPTS y
 DEBUG_INFO y -> n
 [COLOR="#FF0000"]SCSI_MQ_DEFAULT n -> y[/COLOR]
```And get:```
~$ uname -a
Linux s15 4.12.0-rc5-stockq #262 SMP Thu Jun 15 14:53:52 PDT 2017 x86_64 x86_64 x86_64 GNU/Linux

doug@s15:~$ [COLOR="#FF0000"]cat /sys/block/sd?/queue/scheduler[/COLOR]
[none]
[none]

```

---

### Post by Rustan on 2017-06-15
```
~$ uname -a
Linux home 4.12.0-2-generic #3-Ubuntu SMP Mon Jun 12 12:40:30 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
~$ cat /sys/block/sd*/queue/scheduler
[none] 
[none] 
~$ sudo modprobe bfq
~$ cat /sys/block/sd*/queue/scheduler
[none] bfq 
[none] bfq 
~$ echo bfq > /sys/block/sda/queue/scheduler
~$ cat /sys/block/sd*/queue/scheduler
[bfq] none
[none] bfq
```

---

### Post by #&amp;thj^% on 2017-06-15
> **Rustan said:**
> ```
~$ uname -a
Linux home 4.12.0-2-generic #3-Ubuntu SMP Mon Jun 12 12:40:30 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
~$ cat /sys/block/sd*/queue/scheduler
[none] 
[none] 
~$ sudo modprobe bfq
~$ cat /sys/block/sd*/queue/scheduler
[none] bfq 
[none] bfq 
~$ echo bfq > /sys/block/sda/queue/scheduler
~$ cat /sys/block/sd*/queue/scheduler
[bfq] none
[none] bfq
```
Thanks! ;)
running a Low-latency ATM so a no go here:
```
sudo modprobe bfq
[sudo] password for me: 
modprobe: FATAL: Module bfq not found in directory /lib/modules/4.10.0-23-lowlatency

```
Will give it a go tomorrow with generic 4.12.

---

### Post by Doug S on 2017-06-15
> **Rustan said:**
> ```
~$ uname -a
Linux home 4.12.0-2-generic #3-Ubuntu SMP Mon Jun 12 12:40:30 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
~$ cat /sys/block/sd*/queue/scheduler
[none] 
[none] 
~$ sudo modprobe bfq
~$ cat /sys/block/sd*/queue/scheduler
[none] bfq 
[none] bfq 
~$ echo bfq > /sys/block/sda/queue/scheduler
~$ cat /sys/block/sd*/queue/scheduler
[bfq] none
[none] bfq
```O.K. Thanks, that works for me also.

---

### Post by aljosa2 on 2017-06-26
Asus G752VS laptop, Ubuntu 17.04.
Just installed new kernel 4.12-rc7, my ELAN touchpad is still completely dead:
( comment #74: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1653456](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1653456) )

> [    5.320298] i2c_hid i2c-ELAN1203:00: i2c-ELAN1203:00 supply vdd not found, using dummy regulator
[    5.581767] hid-multitouch 0018:04F3:3043.0007: Ignoring the extra HID_DG_INPUTMODE
[    5.581851] input: ELAN1203:00 04F3:3043 Touchpad as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-1/i2c-ELAN1203:00/0018:04F3:3043.0007/input/input16
[    5.581967] hid-multitouch 0018:04F3:3043.0007: input,hidraw6: I2C HID v1.00 Mouse [ELAN1203:00 04F3:3043] on i2c-ELAN1203:00

Additionally, my wifi stopped working too:

> [4.542384] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-30.ucode failed with error -2
[4.542606] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-29.ucode failed with error -2
[4.542617] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-28.ucode failed with error -2
[4.542626] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-27.ucode failed with error -2
[4.542704] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-26.ucode failed with error -2
[4.542714] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-25.ucode failed with error -2
[4.542723] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-24.ucode failed with error -2
[4.542732] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-23.ucode failed with error -2
[4.542816] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-22.ucode failed with error -2
[4.542817] iwlwifi 0000:02:00.0: no suitable firmware found!
[4.542836] iwlwifi 0000:02:00.0: minimum version required: iwlwifi-8000C-22
[4.542853] iwlwifi 0000:02:00.0: maximum version supported: iwlwifi-8000C-30
[4.542870] iwlwifi 0000:02:00.0: check git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git

and I'm also getting the following "Firmware Bug" message:

> [4.440279] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xfed40000-0xfed4087f flags 0x200] vs fed40080 f80
[4.440343] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xfed40000-0xfed4087f flags 0x200] vs fed40080 f80

---

### Post by aljosa2 on 2017-07-03
Operating system: Ubuntu 17.04.
Non-Optimus laptop ASUS G752VS-GC063D-CST256: 17.3" FHD LED 1920x1080, Intel Core i7-6700HQ (3.50Ghz), 16GB DDR4, 256GB M.2 NVMe SSD + 1TB HDD 7200rpm, DVDRW-DL, Nvidia GTX1070 8GB GDDR5, Wifi 802.11ac+Bluetooth 4.1 (Dual band) 2*2, Gb LAN, HDMI, mDP, Intel WiDi, USB3.0 x4, USB3.1-Type C(Gen2) with Thunderbolt, HD webcam, Illuminated KB.

I have just installed the new Linux 4.12 kernel.
My ELAN touchpad is still completely dead. Additionally my wifi stopped working too and I'm also getting 'Firmware Bug' message regarding "tpm_crb MSFT0101:00".
The complete DMESG output file is attached here (comment #75)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1653456](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1653456)
and here are the problematic lines:


> [4.304205] systemd[1]: cgmanager.service: Cannot add dependency job, ignoring: Unit cgmanager.service is masked.[4.304214] systemd[1]: cgproxy.service: Cannot add dependency job, ignoring: Unit cgproxy.service is masked.


[4.459298] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xfed40000-0xfed4087f flags 0x200] vs fed40080 f80
[4.459372] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xfed40000-0xfed4087f flags 0x200] vs fed40080 f80


[4.552235] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-30.ucode failed with error -2
[4.552360] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-29.ucode failed with error -2
[4.552372] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-28.ucode failed with error -2
[4.552381] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-27.ucode failed with error -2
[4.553686] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-26.ucode failed with error -2
[4.553701] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-25.ucode failed with error -2
[4.553709] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-24.ucode failed with error -2
[4.553718] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-23.ucode failed with error -2
[4.555649] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-22.ucode failed with error -2
[4.555653] iwlwifi 0000:02:00.0: no suitable firmware found!
[4.555699] iwlwifi 0000:02:00.0: minimum version required: iwlwifi-8000C-22
[4.555730] iwlwifi 0000:02:00.0: maximum version supported: iwlwifi-8000C-30
[4.555761] iwlwifi 0000:02:00.0: check git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git


[4.557843] uvcvideo: Found UVC 1.00 device USB2.0 HD UVC WebCam (0bda:57fa)
[4.560734] uvcvideo 1-4:1.0: Entity type for entity Realtek Extended Controls Unit was not initialized!
[4.560736] uvcvideo 1-4:1.0: Entity type for entity Extension 4 was not initialized!
[4.560737] uvcvideo 1-4:1.0: Entity type for entity Processing 2 was not initialized!
[4.560737] uvcvideo 1-4:1.0: Entity type for entity Camera 1 was not initialized!
[4.560795] input: USB2.0 HD UVC WebCam as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/input/input11
[4.560860] usbcore: registered new interface driver uvcvideo
[4.560861] USB Video Class driver (1.1.1)


[4.572636] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[4.572691] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[4.572712] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[4.572727] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[4.572744] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[4.572756] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[4.572767] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)


[4.998229] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[4.998308] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[4.998360] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[4.998426] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[4.999322] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[4.999670] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[4.999824] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[4.999888] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[4.999948] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[4.999997] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[5.000047] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[5.000099] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[5.000137] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[5.000174] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[5.000211] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[5.000248] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[5.000290] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)


[5.100442] i2c_hid i2c-ELAN1203:00: i2c-ELAN1203:00 supply vdd not found, using dummy regulator
[5.303057] hid-multitouch 0018:04F3:3043.0007: Ignoring the extra HID_DG_INPUTMODE
[5.303118] input: ELAN1203:00 04F3:3043 Touchpad as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-1/i2c-ELAN1203:00/0018:04F3:3043.0007/input/input16
[5.303204] hid-multitouch 0018:04F3:3043.0007: input,hidraw6: I2C HID v1.00 Mouse [ELAN1203:00 04F3:3043] on i2c-ELAN1203:00


[6.959695] bridge: filtering via arp/ip/ip6tables is no longer available by default. Update your scripts to load br_netfilter if you need this.
[6.965177] IPv6: ADDRCONF(NETDEV_UP): lxcbr0: link is not ready
[7.283325] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[7.297382] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.297414] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.297432] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.297450] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.297472] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.297489] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.297507] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.300868] r8169 0000:03:00.0 enp3s0: link down
[7.300933] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[7.614021] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.614079] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.614114] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.614148] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.614180] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.614213] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.614245] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.614278] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.614310] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.614342] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.614375] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.614407] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.614439] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.614573] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.614613] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.614657] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.614736] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.648440] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[7.998074] nvidia-modeset: Allocated GPU:0 (GPU-36946fb5-8d25-dcea-2d69-172acaad0a58) @ PCI:0000:01:00.0
[8.000197] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[8.000297] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[8.000453] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)
[8.000514] ACPI Warning: \_SB.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170303/nsarguments-95)


---

### Post by #&amp;thj^% on 2017-07-11
@Doug S or anyone for that matter have you seen this?
```

hwmon_device_register() is deprecated. Please convert the driver to use hwmon_device_register_with_info().
```

EDIT: Never mind old bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1666653](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1666653)
> Seth Forshee (sforshee) wrote on 2017-02-22: 	#3

This is a warning meant for driver developers and can safely be ignored.
Changed in linux (Ubuntu):
status: 	Confirmed &#8594; Invalid 

There was a patch...but it breaks my kernel
Patch
```

diff --git a/drivers/thermal/thermal_hwmon.c b/drivers/thermal/thermal_hwmon.c
index 541af59..c4a508a 100644
--- a/drivers/thermal/thermal_hwmon.c
+++ b/drivers/thermal/thermal_hwmon.c
@@ -59,14 +59,6 @@  static LIST_HEAD(thermal_hwmon_list);
 static DEFINE_MUTEX(thermal_hwmon_list_lock);
 
 static ssize_t
-name_show(struct device *dev, struct device_attribute *attr, char *buf)
-{
-	struct thermal_hwmon_device *hwmon = dev_get_drvdata(dev);
-	return sprintf(buf, "%s\n", hwmon->type);
-}
-static DEVICE_ATTR_RO(name);
-
-static ssize_t
 temp_input_show(struct device *dev, struct device_attribute *attr, char *buf)
 {
 	int temperature;
@@ -165,15 +157,12 @@  int thermal_add_hwmon_sysfs(struct thermal_zone_device *tz)
 
 	INIT_LIST_HEAD(&hwmon->tz_list);
 	strlcpy(hwmon->type, tz->type, THERMAL_NAME_LENGTH);
-	hwmon->device = hwmon_device_register(NULL);
+	hwmon->device = hwmon_device_register_with_info(NULL, hwmon->type,
+							hwmon, NULL, NULL);
 	if (IS_ERR(hwmon->device)) {
 		result = PTR_ERR(hwmon->device);
 		goto free_mem;
 	}
-	dev_set_drvdata(hwmon->device, hwmon);
-	result = device_create_file(hwmon->device, &dev_attr_name);
-	if (result)
-		goto free_mem;
 
  register_sys_interface:
 	temp = kzalloc(sizeof(*temp), GFP_KERNEL);
@@ -222,10 +211,8 @@  int thermal_add_hwmon_sysfs(struct thermal_zone_device *tz)
  free_temp_mem:
 	kfree(temp);
  unregister_name:
-	if (new_hwmon_device) {
-		device_remove_file(hwmon->device, &dev_attr_name);
+	if (new_hwmon_device)
 		hwmon_device_unregister(hwmon->device);
-	}
  free_mem:
 	if (new_hwmon_device)
 		kfree(hwmon);
@@ -267,7 +254,6 @@  void thermal_remove_hwmon_sysfs(struct thermal_zone_device *tz)
 	list_del(&hwmon->node);
 	mutex_unlock(&thermal_hwmon_list_lock);
 
-	device_remove_file(hwmon->device, &dev_attr_name);
 	hwmon_device_unregister(hwmon->device);
 	kfree(hwmon);
 }


```

---

### Post by Doug S on 2017-07-12
> **1fallen said:**
> @Doug S or anyone for that matter have you seen this?
```

hwmon_device_register() is deprecated. Please convert the driver to use hwmon_device_register_with_info().
```
I have not seen it. I'll watch for it in future.
(I fell a few weeks behind with this RC series, and have not caught up)

> **1fallen said:**
> 
There was a patch...but it breaks my kernel
Patch
```

diff --git a/drivers/thermal/thermal_hwmon.c b/drivers/thermal/thermal_hwmon.c
... deleted this ...

```Yes, I believe that patch has now been reverted. Here is a git log from a pull of just now:
```
$ [COLOR="#FF0000"]git log --oneline drivers/thermal/thermal_hwmon.c[/COLOR]
3feb479 [COLOR="#FF0000"]Revert[/COLOR] "thermal: thermal_hwmon: Convert to hwmon_device_register_with_info()"
7611fb6 thermal: thermal_hwmon: Convert to hwmon_device_register_with_info()
f37fabb thermal: hwmon: Properly report critical temperature in sysfs
de6b0c1 thermal: hwmon: use permission-specific DEVICE_ATTR variants
f4c5924 thermal: hwmon: EXPORT_SYMBOL_GPL for thermal hwmon sysfs

```However, I do not know where that revertion is with respect to the various release tags. i.e. it might be after 4.12, not sure.

EDIT:

The reversion is actually from a few months ago:```
$ [COLOR="#FF0000"]git describe 3feb479[/COLOR]
v4.10-rc5-108-g3feb479

```and:```
commit 3feb479cea37fc623cf4e705631b2e679cbfbd7a
Author: Fabio Estevam <fabio.estevam@nxp.com>
Date:   Mon Jan 23 13:13:58 2017 -0200

    Revert "thermal: thermal_hwmon: Convert to hwmon_device_register_with_info()"

    This reverts commit 7611fb68062f ("thermal: thermal_hwmon: Convert to
    hwmon_device_register_with_info()").

    Pavel Machek reported breakage in the Nokia N900 due to this commit.

    We can revisit a proper fix for the warning later.

```

---

### Post by #&amp;thj^% on 2017-07-12
> **Doug S said:**
> I have not seen it. I'll watch for it in future.
(I fell a few weeks behind with this RC series, and have not caught up)

Yes, I believe that patch has now been reverted. Here is a git log from a pull of just now:
```
$ [COLOR="#FF0000"]git log --oneline drivers/thermal/thermal_hwmon.c[/COLOR]
3feb479 [COLOR="#FF0000"]Revert[/COLOR] "thermal: thermal_hwmon: Convert to hwmon_device_register_with_info()"
7611fb6 thermal: thermal_hwmon: Convert to hwmon_device_register_with_info()
f37fabb thermal: hwmon: Properly report critical temperature in sysfs
de6b0c1 thermal: hwmon: use permission-specific DEVICE_ATTR variants
f4c5924 thermal: hwmon: EXPORT_SYMBOL_GPL for thermal hwmon sysfs

```However, I do not know where that revertion is with respect to the various release tags. i.e. it might be after 4.12, not sure.

Thanks Doug S ;), I think for now I'll just let it go, as it dose not have any Ill effects on my system.
Last I heard they had it listed as a "Won't Fix".
I'll Just have to wait and see.:) I guess.
Kind Regards

---

