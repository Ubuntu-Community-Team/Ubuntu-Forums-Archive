---
title: "Kernel 4.11RC (Release Candidate) series"
date: 2017-03-05
forum: Ubuntu Development Version
---

### Post by Doug S on 2017-03-05
Kernel 4.11rc-1 has just been made available from [kernel.org]("https://www.kernel.org/"). Expect to see it in the [Ubuntu mainline]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") PPA soon.

I have been running it without issue all of today (the only thing added to what I was running was the 4.11-rc1 tag).

On a personal note, there is a new tool, [tools/power/x86/intel_pstate_tracer/intel_pstate_tracer.py]("https://patchwork.kernel.org/patch/9570867/"), for acquiring and post processing, or just post processing a previously acquired, intel_pstate (CPU frequency scaling driver) trace, which I contributed to. If you use the intel_pstate CPU frequency scaling driver, try it. (To check do: "cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver")( I guess you would need to get the source code to get that script. If you do, I would suggest putting it, meaning the script, intel_pstate_tracer.py, into some working directory to test/play with it.)

EDIT: Now available in [Ubuntu mainline PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11-rc1/").

---

### Post by fyfe54 on 2017-03-05
Downloaded and installed.  So far, so good.

---

### Post by fthx on 2017-03-06
NVMe power management is here ! See the dedicated thread in this section.

---

### Post by Doug S on 2017-03-13
Kernel 4.11rc-2 is [available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11-rc2/"). I've only been running it for a few minutes.

---

### Post by Doug S on 2017-03-24
I am having an infrequent issue with [ksmd]("https://www.kernel.org/doc/Documentation/vm/ksm.txt"). When the problem occurs, twice now, the computer locks up and the only way out seems to be the reset button. I'm always running VM guests at the time. One CPU is locked up at a very primitive level, causing NMI watchdog failed messages every 22 seconds. I am still on 4.11-rc2, and will try -rc3 shortly.

Example log segment:```
Mar 24 07:08:17 s15 kernel: [79244.063597]  ret_from_fork+0x2c/0x40
Mar 24 07:08:45 s15 kernel: [79272.001582] NMI watchdog: BUG: soft lockup - CPU#5 stuck for 22s! [ksmd:64]
Mar 24 07:08:45 s15 kernel: [79272.002490] Modules linked in: binfmt_misc vhost_net vhost tap xt_conntrack ipt_REJECT nf_reject_ipv4 ebtable_filter ebtables ip6_tables xt_CHECKSUM iptable_mangle $
Mar 24 07:08:45 s15 kernel: [79272.006523]  autofs4 btrfs raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear crct10dif_p$
Mar 24 07:08:45 s15 kernel: [79272.008726] CPU: 5 PID: 64 Comm: ksmd Tainted: G    B D      L  4.11.0-rc2-doug #220
Mar 24 07:08:45 s15 kernel: [79272.009853] Hardware name: System manufacturer System Product Name/P8Z68-M PRO, BIOS 4003 05/09/2013
Mar 24 07:08:45 s15 kernel: [79272.010963] task: ffff943bcc820000 task.stack: ffffb9aa81af8000
Mar 24 07:08:45 s15 kernel: [79272.012097] RIP: 0010:native_queued_spin_lock_slowpath+0x17c/0x1a0
Mar 24 07:08:45 s15 kernel: [79272.013219] RSP: 0018:ffffb9aa81afbd70 EFLAGS: 00000202 ORIG_RAX: ffffffffffffff10
Mar 24 07:08:45 s15 kernel: [79272.014381] RAX: 0000000000000101 RBX: ffff943915a54b38 RCX: 0000000000000001
Mar 24 07:08:45 s15 kernel: [79272.015523] RDX: 0000000000000101 RSI: 0000000000000001 RDI: ffffea5ec5569530
Mar 24 07:08:45 s15 kernel: [79272.016686] RBP: ffffb9aa81afbd70 R08: 0000000000000101 R09: ffff9439cb5e5ca8
Mar 24 07:08:45 s15 kernel: [79272.017868] R10: 0000000000000000 R11: 0000000000015aa8 R12: ffffea5ec5569530
Mar 24 07:08:45 s15 kernel: [79272.019020] R13: 0000000000000004 R14: ffff9439cb5e5ca8 R15: ffffc00000000fff
Mar 24 07:08:45 s15 kernel: [79272.020187] FS:  0000000000000000(0000) GS:ffff943bdf340000(0000) knlGS:0000000000000000
Mar 24 07:08:45 s15 kernel: [79272.021345] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar 24 07:08:45 s15 kernel: [79272.022534] CR2: 00007f756408e000 CR3: 00000003afa09000 CR4: 00000000000426e0
Mar 24 07:08:45 s15 kernel: [79272.023653] Call Trace:
Mar 24 07:08:45 s15 kernel: [79272.024733]  _raw_spin_lock+0x20/0x30
Mar 24 07:08:45 s15 kernel: [79272.025822]  follow_page_pte+0x10c/0x650
Mar 24 07:08:45 s15 kernel: [79272.026872]  follow_page_mask+0x1ee/0x5b0
Mar 24 07:08:45 s15 kernel: [79272.027905]  ? find_vma+0x68/0x70
Mar 24 07:08:45 s15 kernel: [79272.028947]  ksm_scan_thread+0xc08/0x12a0
Mar 24 07:08:45 s15 kernel: [79272.029997]  ? wake_atomic_t_function+0x60/0x60
Mar 24 07:08:45 s15 kernel: [79272.031010]  kthread+0x101/0x140
Mar 24 07:08:45 s15 kernel: [79272.032009]  ? try_to_merge_with_ksm_page+0xa0/0xa0
Mar 24 07:08:45 s15 kernel: [79272.033020]  ? kthread_create_on_node+0x60/0x60
Mar 24 07:08:45 s15 kernel: [79272.034053]  ret_from_fork+0x2c/0x40
Mar 24 07:08:45 s15 kernel: [79272.035057] Code: c0 74 e6 4d 85 c9 c6 07 01 74 30 41 c7 41 08 01 00 00 00 e9 51 ff ff ff 83 fa 01 0f 84 af fe ff ff 8b 07 84 c0 74 08 f3 90 8b 07 <84> c0 75 f8 b8 $
Mar 24 07:09:13 s15 kernel: [79300.002949] NMI watchdog: BUG: soft lockup - CPU#5 stuck for 22s! [ksmd:64]

```

---

### Post by mrfelker on 2017-03-27
Kernel 4.11 rc4 works great

---

### Post by Doug S on 2017-04-01
Does anybody know what happened to CONFIG_TIMER_STATS in the kernel configuration for this series? And why? I use /proc/timer_stats often, and was surprised to find it gone. It doesn't even seem to be an option in "make menuconfig" now. (supposed to be under the Kernel Hacking menu, with the prompt: "Collect kernel timers statistics")

EDIT: It seems to have been removed. Drat.

```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]git show dfb4357 | head -19[/COLOR]
commit dfb4357da6ddbdf57d583ba64361c9d792b0e0b1
Author: Kees Cook <keescook@chromium.org>
Date:   Wed Feb 8 11:26:59 2017 -0800

    time: Remove CONFIG_TIMER_STATS

    Currently CONFIG_TIMER_STATS exposes process information across namespaces:

    kernel/time/timer_list.c print_timer():

            SEQ_printf(m, ", %s/%d", tmp, timer->start_pid);

    /proc/timer_list:

     #11: <0000000000000000>, hrtimer_wakeup, S:01, do_nanosleep, cron/2570

    Given that the tracer can give the same information, this patch entirely
    removes CONFIG_TIMER_STATS.

```See [also]("https://patchwork.kernel.org/patch/9563287/").

---

### Post by mc4man on 2017-04-01
Ot to some extent, Do the kernel ppa builds allow use of nvidia drivers?

---

### Post by Doug S on 2017-04-04
Kernel 4.11-rc5 has been available for a couple of days. There is patch available for my comment #5 issue, and I am running that now, after establishing a baseline of 2 fails in 24 hours with -rc5.  There was another bug in the memory management stuff and the fix is included in -rc5.

---

### Post by Doug S on 2017-04-11
Kernel 4.11-rc6 contains the patch for the issue I mentioned in comment #5.

---

### Post by wgarcia on 2017-04-11
I think I was getting the bug you mention ins comment #5 with 4.10.0.14-generic . Since the kernel upgraded in Zesty (first to 4.10.0.15 and now to 4.10.0.19), I haven't seen it any more. I opened a bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1677491](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1677491)

but I closed it as with the kernel upgrades I stopped seeing this bug. The piece I pasted from the syslog does not include it, but I also saw:

```
NMI watchdog: BUG: soft lockup - CPU#5 stuck for 22s! [ksmd:64]
```

in my syslog for one of my CPUs.

---

### Post by Doug S on 2017-04-12
> **Doug S said:**
> Does anybody know what happened to CONFIG_TIMER_STATS in the kernel configuration for this series? And why? I use /proc/timer_stats often, and was surprised to find it gone. It doesn't even seem to be an option in "make menuconfig" now. (supposed to be under the Kernel Hacking menu, with the prompt: "Collect kernel timers statistics")

EDIT: It seems to have been removed. Drat.

```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]git show dfb4357 | head -19[/COLOR]
commit dfb4357da6ddbdf57d583ba64361c9d792b0e0b1
Author: Kees Cook <keescook@chromium.org>
Date:   Wed Feb 8 11:26:59 2017 -0800

    time: Remove CONFIG_TIMER_STATS

    Currently CONFIG_TIMER_STATS exposes process information across namespaces:

    kernel/time/timer_list.c print_timer():

            SEQ_printf(m, ", %s/%d", tmp, timer->start_pid);

    /proc/timer_list:

     #11: <0000000000000000>, hrtimer_wakeup, S:01, do_nanosleep, cron/2570

    [COLOR="#FF0000"]Given that the tracer can give the same information[/COLOR], this patch entirely
    removes CONFIG_TIMER_STATS.

```See [also]("https://patchwork.kernel.org/patch/9563287/").Does anybody know how to get the same information using the tracer?
My worry with this is that I tend to use the trace abilities for other things at the same time as using the now removed method of /proc/timer_stats

---

### Post by Doug S on 2017-04-12
> **wgarcia said:**
> I think I was getting the bug you mention ins comment #5 with 4.10.0.14-generic . Since the kernel upgraded in Zesty (first to 4.10.0.15 and now to 4.10.0.19), I haven't seen it any more. I opened a bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1677491](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1677491)

but I closed it as with the kernel upgrades I stopped seeing this bug. The piece I pasted from the syslog does not include it, but I also saw:

```
NMI watchdog: BUG: soft lockup - CPU#5 stuck for 22s! [ksmd:64]
```

in my syslog for one of my CPUs.I think there was more than one mm (memory management) related bug. There were significant changes between kernel 4.10 and 4.11-rc1. I do not think my particular issue existed in kernel 4.10, but am not sure. I also don't think this particular patch could possibly have been backported already, as it is only 3 days into 4.11-rc6.

Yes, sometime after the initial event, I tended to get the "CPU#N stuck for 22s!" message also.

Note: Due to [forums troubles]("https://ubuntuforums.org/showthread.php?t=2331266&page=36&p=13631956#post13631956"), I couldn't actually see your posting until just now, even though I knew it was there.

---

### Post by wgarcia on 2017-04-13
I just got a freeze with this message in 4.10.0.19. I'm getting this only in one of my systems running Zesty, though, I'm running it in three different machines. I will reopen the bug just in case.

---

### Post by Doug S on 2017-04-13
> **wgarcia said:**
> I just got a freeze with this message in 4.10.0.19. I'm getting this only in one of my systems running Zesty, though, I'm running it in three different machines. I will reopen the bug just in case.I would suggest to try kernel 4.11-rc6 on that computer. It has all the current fixes.

For myself, and it sounds similar for you, this is such a rare event that it is hard to know for certain that it is fixed. Also, it is hard on the system because it is a "reset" button type crash.

The related commits that I am aware of are:
3fe87967c536e828bf1ea14b3ec3827d1101152e  mm: convert remove_migration_pte() to use page_vma_mapped_walk()
4b0ece6fa0167b22c004ff69e137dc94ee2e469e  mm: migrate: fix remove_migration_pte() for ksm pages
ace71a19cec5eb430207c3269d8a2683f0574306  mm: introduce page_vma_mapped_walk()
d75450ff40df0199bf13dfb19f435519ff947138   mm: fix page_vma_mapped_walk() for ksm pages

EDIT: My issues have been related to ksmd and while running virtual machines. Both fixes listed above have been ksm related. If I am not running VM's ksmd seems to have nothing to do:

While not running VM's:
```
doug@s15:~/temp-k-git/linux$ [COLOR="#FF0000"]grep . /sys/kernel/mm/ksm/*[/COLOR]
/sys/kernel/mm/ksm/full_scans:0
/sys/kernel/mm/ksm/merge_across_nodes:1
/sys/kernel/mm/ksm/pages_shared:0
/sys/kernel/mm/ksm/pages_sharing:0
/sys/kernel/mm/ksm/pages_to_scan:100
/sys/kernel/mm/ksm/pages_unshared:0
/sys/kernel/mm/ksm/pages_volatile:0
/sys/kernel/mm/ksm/run:1
/sys/kernel/mm/ksm/sleep_millisecs:200
/sys/kernel/mm/ksm/use_zero_pages:0

```While running VM's:
```
/sys/kernel/mm/ksm/full_scans:178
/sys/kernel/mm/ksm/merge_across_nodes:1
/sys/kernel/mm/ksm/pages_shared:204235
/sys/kernel/mm/ksm/pages_sharing:445520
/sys/kernel/mm/ksm/pages_to_scan:100
/sys/kernel/mm/ksm/pages_unshared:1506060
/sys/kernel/mm/ksm/pages_volatile:147225
/sys/kernel/mm/ksm/run:1
/sys/kernel/mm/ksm/sleep_millisecs:200
/sys/kernel/mm/ksm/use_zero_pages:0

```

---

### Post by Doug S on 2017-04-16
Kernel 4.11-rc7 is available from [kernel.org]("https://www.kernel.org/"), and the [Ubuntu mainline PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11-rc7/").
I'm running it now.

EDIT:
"190 files changed, 2093 insertions(+), 1130 deletions(-)"
seems a little high for an -rc7.

---

### Post by IanW on 2017-04-18
> **Doug S said:**
> 
EDIT:
"190 files changed, 2093 insertions(+), 1130 deletions(-)"
seems a little high for an -rc7.

Looks like a bunch of stuff has been reverted because it's not quite ready.
See [Linus' announcement]("http://lkml.iu.edu/hypermail/linux/kernel/1704.2/00277.html").

[QUOTE=Linus Torvalds]
Things have been pretty calm this past week (the beginning of the week
seemed particularly calm, and then as usual Friday happened..). We
have a number of reverts for things that didn't work out and aren't
worth trying to fix at this point, that's also normal (and people will
look at it for the next version instead).[/QUOTE]

---

### Post by Doug S on 2017-04-25
There is an [-rc8]("https://lwn.net/Articles/720726/") this cycle. I don't know that I'll get to it, as I am doing comparison tests between several -rc7 kernels and do not want the overhead of changing right now.

---

### Post by Doug S on 2017-05-02
While [kernel 4.11]("https://www.kernel.org/") has been released, but it seems [the mainline PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") build is broken again, and so it hasn't been posted. From the daily([http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/BUILD.LOG.amd64]("http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/BUILD.LOG.amd64")):```
dh_builddeb -plinux-image-4.11.0-999-generic -- -Zbzip2 -z9
dpkg-deb: error: obsolete compression type 'bzip2'; use xz or gzip instead
```Someone did ask about it [on irc]("https://irclogs.ubuntu.com/2017/05/01/%23ubuntu-kernel.html#t11:30"), but didn't get a response.

My own compile worked fine.

EDIT 1: The same spot in the mainline 4.11-rc8 build log says:```
dh_builddeb -plinux-image-4.11.0-041100rc8-generic -- -Zbzip2 -z9
dpkg-deb: warning: deprecated compression type 'bzip2'; use xz or gzip instead
dpkg-deb: warning: ignoring 1 warning about the control file(s)
```

EDIT 2: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687534]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687534")

---

### Post by fyfe54 on 2017-05-04
4.11 mainline kernel now available.  
So far, so good.....

---

### Post by #&amp;thj^% on 2017-05-04
Runing very nicely here also:
```
inxi -Sxx && echo $DESKTOP_SESSION
System:    Host: me-ThinkPad-T430 Kernel: 4.11.0-041100-lowlatency x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.1 (Gtk 3.22.11-0ubuntu3) dm: gdm3
           Distro: Ubuntu 17.04
           gnome-wayland

```
**NOTE:** Normal warning's on possible missing firmware...but silky smooth here.

---

### Post by IanW on 2017-05-10
Looks like Nvidia's new 381.22 driver now speaks 4.11

---

### Post by rrnbtter on 2017-05-10
Greetings,
Works well here also.

```
 inxi -Sxx && $DESKTOP_SESSIONSystem:    Host: rrnbtter-110-15ISK Kernel: 4.11.0-041100-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome  (Gtk 3.22.12-1ubuntu1) dm: lightdm
           Distro: Ubuntu Artful Aardvark (development branch)
ubuntu

```

---

