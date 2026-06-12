---
title: "Kernel 5.2RC (Release Candidate) series"
date: 2019-05-20
forum: Ubuntu Development Version
---

### Post by Doug S on 2019-05-20
Kernel 5.2-rc1 is available from the [Ubuntu Mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.2-rc1/") and [Kernel.org]("https://www.kernel.org/"). (Several builds failed.)
I still only use the TEO (Timer Events Oriented) idle governor, introduced in the 5.1RC kernel cycle.

```
doug@s15:~$ grep . /sys/devices/system/cpu/cpuidle/* && uname -a
/sys/devices/system/cpu/cpuidle/available_governors:ladder menu teo
/sys/devices/system/cpu/cpuidle/current_driver:intel_idle
/sys/devices/system/cpu/cpuidle/current_governor:teo
Linux s15 5.2.0-rc1-stock #593 SMP PREEMPT Mon May 20 13:33:44 PDT 2019 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by lonniehenry-gmail on 2019-06-03
I have been trying to use the mainline kernel for 5.2 daily on my asus laptop.  I always try the new kernels during the testing stage.  I had no problem with 5.1, but when I try to boot any of the 5.2 dailies with the logitech mouse receiver plugged in, it stops and does not boot.  If I don't plug in the receiver, I get a normal boot.  Then I plug in the receiver and after a couple of minutes, the mouse starts working.  I have read that the Logitech receivers drivers were going to be added  to the kernel.  Would that work be stopping the boot sequence.  How do I try to figure it out?

Eaon and Disco partitions on an Asus Zenbook

---

### Post by mrfelker on 2019-06-04
What's up with rc3.   The directory does not have any compiled code and hasn't for a couple of days.   I've never seen anything like this.

---

### Post by Doug S on 2019-06-04
> **mrfelker said:**
> What's up with rc3.   The directory does not have any compiled code and hasn't for a couple of days.  I've never seen anything like this.actually, it happens occasionally that the build gets broken. If it doesn't get sorted out after a few days someone usually inquires in the kernel IRC channel (It can help to look back in the IRC logs for a few days, to see if someone mentioned it already. ( [https://irclogs.ubuntu.com/2019/06/04/%23ubuntu-kernel.html](https://irclogs.ubuntu.com/2019/06/04/%23ubuntu-kernel.html) , for example. No activity for the past few days.). Note that often the kernel team doesn't seem to know the daily mainline build is broken. Also have a look at [the build log]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.2-rc3/BUILD.LOG") for anything obvious. 

I am behind an RC at the moment, but will try to catch up in a few days.

EDIT 1: Some of the builds, including AMD64, worked in today's (2019.06.04) [daily]("https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2019-06-04/").
EDIT 2: There is [IRC channel activity today]("https://irclogs.ubuntu.com/2019/06/05/%23ubuntu-kernel.html") (2019.06.05) on the build failures.
EDIT 3: [Kernel 5.2-rc3 is available from the mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.2-rc3/"). All day (2019.06.05) I have been running one I compiled myself without any issues.

---

### Post by corradoventu on 2019-06-09
Installed kernel 5.2.0-050200rc4-generic ```
corrado@corrado-p9-ee-0523:~$ inxi -SCx
System:    Host: corrado-p9-ee-0523 Kernel: 5.2.0-050200rc4-generic x86_64 bits: 64 compiler: gcc v: 8.3.0 
           Desktop: Gnome 3.32.2 Distro: Ubuntu 19.10 (Eoan Ermine) 
CPU:       Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP arch: Kaby Lake rev: 9 L2 cache: 3072 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31296 
           Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 800 
corrado@corrado-p9-ee-0523:~$ 
```
No errors at install but errors at 1st boot:```
.........
giu 09 10:58:43 corrado-p9-ee-0523 gnome-shell[1440]: [AppIndicatorSupport-FATAL] unable to update overlay icon
giu 09 10:58:43 corrado-p9-ee-0523 gnome-shell[1440]: [AppIndicatorSupport-FATAL] unable to update overlay icon
giu 09 10:58:50 corrado-p9-ee-0523 PackageKit[1236]: refresh-cache transaction /210_ccdeaded from uid 1000 finished with success after 8228ms
giu 09 10:58:50 corrado-p9-ee-0523 snapd[825]: snapmgr.go:258: cannot read snap info of snap "gnome-system-monitor" at revision 83: cannot find installed snap "gnome-system-monitor" at revision 83: missing file /snap/gnome-system-monitor/83/meta/snap.yaml
giu 09 10:58:51 corrado-p9-ee-0523 PackageKit[1236]: resolve transaction /211_cbadebbd from uid 1000 finished with success after 1223ms
giu 09 10:58:52 corrado-p9-ee-0523 gnome-software[1941]: Only 8 apps for recent list, hiding
giu 09 10:58:52 corrado-p9-ee-0523 PackageKit[1236]: resolve transaction /212_eaebaead from uid 1000 finished with success after 282ms
giu 09 10:58:52 corrado-p9-ee-0523 PackageKit[1236]: resolve transaction /213_aeccdecb from uid 1000 finished with success after 271ms
giu 09 10:58:52 corrado-p9-ee-0523 gnome-software[1941]: hiding category graphics featured applications: found only 1 to show, need at least 9
giu 09 10:59:05 corrado-p9-ee-0523 PackageKit[1236]: search-file transaction /214_edaeacad from uid 1000 finished with success after 12671ms
giu 09 10:59:05 corrado-p9-ee-0523 PackageKit[1236]: search-file transaction /215_eebebdad from uid 1000 finished with success after 344ms
giu 09 10:59:05 corrado-p9-ee-0523 PackageKit[1236]: search-file transaction /216_adeccede from uid 1000 finished with success after 325ms
giu 09 10:59:06 corrado-p9-ee-0523 PackageKit[1236]: search-file transaction /217_eeaccbdb from uid 1000 finished with success after 339ms
giu 09 10:59:06 corrado-p9-ee-0523 PackageKit[1236]: search-file transaction /218_cecaeeab from uid 1000 finished with success after 325ms
giu 09 10:59:06 corrado-p9-ee-0523 PackageKit[1236]: get-details transaction /219_bdbcacaa from uid 1000 finished with success after 278ms
giu 09 10:59:07 corrado-p9-ee-0523 gnome-software[1941]: Failed to load snap icon: local snap has no icon
giu 09 10:59:07 corrado-p9-ee-0523 snapd[825]: snapmgr.go:258: cannot read snap info of snap "gnome-system-monitor" at revision 83: cannot find installed snap "gnome-system-monitor" at revision 83: missing file /snap/gnome-system-monitor/83/meta/snap.yaml
giu 09 10:59:07 corrado-p9-ee-0523 gnome-software[1941]: Failed to load snap icon: local snap has no icon
giu 09 10:59:16 corrado-p9-ee-0523 systemd-resolved[780]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
```

```
corrado@corrado-p9-ee-0523:~$ snap list
Name                  Version                     Rev   Tracking  Publisher   Notes
core                  16-2.39                     6964  stable    canonical&#10003;  core
core18                20190508                    970   stable    canonical&#10003;  base
gnome-3-28-1804       3.28.0-10-gaa70833.aa70833  51    stable/…  canonical&#10003;  -
gnome-calculator      3.32.1                      406   stable/…  canonical&#10003;  -
gnome-characters      v3.32.1+git2.3367201        280   stable/…  canonical&#10003;  -
gnome-logs            3.32.0-4-ge8f3f37ca8        61    stable/…  canonical&#10003;  -
gnome-system-monitor                              83    stable/…  canonical&#10003;  broken
gtk-common-themes     0.1-16-g2287c87             1198  stable/…  canonical&#10003;  -
corrado@corrado-p9-ee-0523:~$ 
```

snap refresh is unsuccessful:
```
corrado@corrado-p9-ee-0523:~$ snap refresh gnome-system-monitor
snap "gnome-system-monitor" has no updates available
corrado@corrado-p9-ee-0523:~$ 

```
After a while now gnome-system-monitor is ok

---

### Post by Doug S on 2019-06-19
> **lonniehenry-gmail said:**
> I have been trying to use the mainline kernel for 5.2 daily on my asus laptop.  I always try the new kernels during the testing stage.  I had no problem with 5.1, but when I try to boot any of the 5.2 dailies with the logitech mouse receiver plugged in, it stops and does not boot.  If I don't plug in the receiver, I get a normal boot.  Then I plug in the receiver and after a couple of minutes, the mouse starts working.  I have read that the Logitech receivers drivers were going to be added  to the kernel.  Would that work be stopping the boot sequence.  How do I try to figure it out?

Eaon and Disco partitions on an Asus ZenbookHave you tried 5.2-rc5? I only know of bisecting the kernel as a way to isolate the exact commit that caused your problem. That being said, I did find [an upstream bug report]("https://bugzilla.kernel.org/show_bug.cgi?id=203619") and also see a fix recently added to the kernel:

```
commit 3ed224e273ac5880eeab4c3043a6b06b0478dd56
Author: Hans de Goede <hdegoede@redhat.com>
Date:   Wed Jun 5 14:44:08 2019 +0200

    HID: logitech-dj: Fix 064d:c52f receiver support

```And it seems "recently' means 5.2-rc5:
```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]git tag --contains 3ed224e273ac5880eeab4c3043a6b06b0478dd56[/COLOR]
v5.2-rc5

```

---

### Post by lonniehenry-gmail on 2019-06-21
Doug S - I tried the newest 5.2-rc5 and the problem was solved.  I figured that it would be fixed at some point.  I thank you for following up on the issue.

---

### Post by DougieFresh4U on 2019-07-01
Not to be picky but in your sig you list Dapper Duck but it's Dapper Drake.
I go back as far as Breezy Badger and loved getting the free cd's from ship it.

---

### Post by lonniehenry-gmail on 2019-07-02
You are right.  I misremebered.  I dualed Dapper and continued to try all the newest developement versions as soon as they came out.  Dumped windows after a year or so.

---

### Post by IanW on 2019-07-08
Good news - Linus has dubbed 5.2 "Bobtail Squid" & pushed it out of the nest.
Bad news   - Today's build has failed for both AMD64 & i386.

---

### Post by Doug S on 2019-07-08
> **IanW said:**
> Good news - Linus has dubbed 5.2 "Bobtail Squid" & pushed it out of the nest.
Bad news   - Today's build has failed for both AMD64 & i386.Interesting. I am still on kernel 5.2-rc5, due to some continuing testing. I see the daily build worked until yesterday. I'll try to compile it myself shortly.

EDIT 1: Looks like a messed up kernel configuration file to me.
EDIT 2: Reported on [kernel IRC channel]("https://irclogs.ubuntu.com/2019/07/08/%23ubuntu-kernel.html"). result: "this is a bug introduced by the compiler hardening options being turned on by default"
EDIT 3: Compiles fine for me, probably because I am using an old version of the compiler.
EDIT 4: [Bug report]("https://bugs.launchpad.net/ubuntu/+source/gcc-9/+bug/1830961")

---

### Post by IanW on 2019-07-09
There is more bad news however.
[Phoronix]("https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=1") is reporting that anything later than 18.04LTS won't boot on the new Ryzen 3000 CPU's.
There is much discussion of what the cause may be in the comments.

---

### Post by Doug S on 2019-07-09
> **IanW said:**
> There is more bad news however.
[Phoronix]("https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=1") is reporting that anything later than 18.04LTS won't boot on the new Ryzen 3000 CPU's.
There is much discussion of what the cause may be in the comments.Yes, but it is my understanding (without looking at your link) that the issue is a systemd problem. I saw a bug report just yesterday about it, with a patch. I'll see if I can find it again. Oh, it was while I was still on the kernel channel on IRC. See [here]("https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1835809").

---

### Post by IanW on 2019-07-10
> **Doug S said:**
> Yes, but it is my understanding (without looking at your link) that the issue is a systemd problem. I saw a bug report just yesterday about it, with a patch. I'll see if I can find it again. Oh, it was while I was still on the kernel channel on IRC. See [here]("https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1835809").

Thanks.

---

### Post by Doug S on 2019-07-11
For users wanting to compile the mainline 5.2 kernel for themselves, and with the newer compiler included with 19.10 do this:

```
doug@serv-ee:~/temp-k-git/linux$ git diff
diff --git a/Makefile b/Makefile
index 3e4868a6498b..d8ccc47215be 100644
--- a/Makefile
+++ b/Makefile
@@ -630,8 +630,8 @@ ifdef CONFIG_FUNCTION_TRACER
   CC_FLAGS_FTRACE := -pg
 endif

-RETPOLINE_CFLAGS_GCC := -mindirect-branch=thunk-extern -mindirect-branch-register
-RETPOLINE_VDSO_CFLAGS_GCC := -mindirect-branch=thunk-inline -mindirect-branch-register
+RETPOLINE_CFLAGS_GCC := -mindirect-branch=thunk-extern -mindirect-branch-register -fcf-protection=none
+RETPOLINE_VDSO_CFLAGS_GCC := -mindirect-branch=thunk-inline -mindirect-branch-register -fcf-protection=none
 RETPOLINE_CFLAGS_CLANG := -mretpoline-external-thunk
 RETPOLINE_VDSO_CFLAGS_CLANG := -mretpoline
 RETPOLINE_CFLAGS := $(call cc-option,$(RETPOLINE_CFLAGS_GCC),$(call cc-option,$(RETPOLINE_CFLAGS_CLANG)))
```And it should then compile.
References:
[https://bugs.launchpad.net/ubuntu/+source/gcc-9/+bug/1830961]("https://bugs.launchpad.net/ubuntu/+source/gcc-9/+bug/1830961")
[https://www.spinics.net/lists/linux-kbuild/msg22298.html]("https://www.spinics.net/lists/linux-kbuild/msg22298.html")
[https://patchwork.kernel.org/patch/11037379/]("https://patchwork.kernel.org/patch/11037379/")

---

### Post by mrfelker on 2019-07-15
Latest successful build for amd64 that I could find is [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.2-rc7//](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.2-rc7//)   This is 2 weeks old.  Never seen this before.

---

### Post by IanW on 2019-07-16
A Phoronix comment says the newer kernels use the -mindirect-branch flag to deal with retpolines.
This is not compatible with Ubuntu's chosen fcf-protection flag.

See [Launchpad bug #1830961]("https://bugs.launchpad.net/ubuntu/+source/gcc-9/+bug/1830961")

---

### Post by IanW on 2019-07-17
UPDATE - I got a 5.2.0-8 kernel yesterday through the normal update channels.

---

### Post by Doug S on 2019-07-18
> **mrfelker said:**
> Latest successful build for amd64 that I could find is [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.2-rc7//](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.2-rc7//)   This is 2 weeks old.  Never seen this before.You can also see people on the bug report asking for the mainline build to be fixed. However it has to wait for the fix, which has been picked up, to make it into the upstream mainline, which it hasn't yet. It'll first appear in the dailies, but not as of [today]("https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2019-07-18/"). Hopefully by kernel 5.3-rc1.

---

### Post by Doug S on 2019-07-20
> **Doug S said:**
> You can also see people on the bug report asking for the mainline build to be fixed. However it has to wait for the fix, which has been picked up, to make it into the upstream mainline, which it hasn't yet. It'll first appear in the dailies, but not as of [today]("https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2019-07-18/"). Hopefully by kernel 5.3-rc1.The patch has been merged into [upstream mainline]("https://www.spinics.net/lists/linux-kbuild/msg22538.html"), so the Ubuntu daily for July 21st should compile properly.

---

### Post by IanW on 2019-07-22
> **Doug S said:**
> The patch has been merged into [upstream mainline]("https://www.spinics.net/lists/linux-kbuild/msg22538.html"), so the Ubuntu daily for July 21st should compile properly.

Daily is now showing a successful 5.3.0-999 build for 5.3rc1, but the 5.2 final releases (5.2, 5.2.1 & 5.2.2) are still showing as failed.

---

### Post by Doug S on 2019-07-23
> **IanW said:**
> Daily is now showing a successful 5.3.0-999 build for 5.3rc1, but the 5.2 final releases (5.2, 5.2.1 & 5.2.2) are still showing as failed.Keep in mind that the patch barely made into kernel 5.3-rc1, as the merge request was well past the usual merge window for an -rc1. It will take time to propagate to other branches.

Todays Ubuntu mainline for [5.2.2]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.2.2/") compiled properly.

I was a week out, and thought 5.3-rc1 wasn't due for another week.

---

### Post by IanW on 2019-07-24
> **Doug S said:**
> Todays Ubuntu mainline for [5.2.2]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.2.2/") compiled properly.

Good to hear. I'll give it a try later today.

---

### Post by zika on 2019-07-24
Beware: 994 of today panics on one of the machines that I work on...
Update&#8321;: Resolved (26.07.19.) Did not try yesterday's baking so it could have been resolved yesterday already...

---

