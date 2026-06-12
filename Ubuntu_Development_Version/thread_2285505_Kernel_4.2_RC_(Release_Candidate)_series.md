---
title: "Kernel 4.2 RC (Release Candidate) series"
date: 2015-07-06
forum: Ubuntu Development Version
---

### Post by Doug S on 2015-07-06
Kernel 4.2RC1 is [available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D").

I have been running the Ubuntu version (as opposed to compiling my own). So far, so good.```
doug@s15:~$ uname -a
Linux s15 4.2.0-040200rc1-generic #201507051635 SMP Sun Jul 5 20:36:51 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```On a personal note, I have 3 simple patches for the intel_pstate driver in this kernel, but [my main patch set submission]("http://permalink.gmane.org/gmane.linux.power-management.general/58958") is on hold.

---

### Post by PaulW2U on 2015-07-06
For those that might be interested, an article from The Register.
> Linus Torvalds has loosed Linux 4.2-rc1 upon a waiting world, and rates it the biggest release candidate ever in terms of the volume of new code it contains.
[ONE MILLION new lines of code hit Linux Kernel]("http://www.theregister.co.uk/2015/07/06/one_million_new_lines_of_code_hit_linux_kernel/")

---

### Post by Doug S on 2015-07-17
Kernel 4.2RC2 has been available for several days.
There seems to be several different compiled versions in [the directory]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-rc2-unstable/").
I do notice significant configuration file changes between RC1 and RC2 ( the 040200rc2.201507160938 one is the only one I have installed ).

---

### Post by Gaylaird_Culbreth on 2015-07-19
I have  not been able to boot any 4.2x kernels on my Asus Chromebox ...hangs at Grub menu. No issues with 4.1x kernels...

---

### Post by fyfe54 on 2015-07-19
4.2 RC3 in Mainline.  So far so good.....
Sysem 76, Gazelle Pro.  Ubuntu 15.04.

---

### Post by Doug S on 2015-07-19
> **Gaylaird_Culbreth said:**
> I have  not been able to boot any 4.2x kernels on my Asus Chromebox ...hangs at Grub menu. No issues with 4.1x kernels...I wonder if your issue is a configuration file change as opposed to an actual kernel issue? Did you try the original 4.2RC1, or the more recent one, dated July 16th? I still have the 4.2RC1 from July 6th if you wanted to try it.

---

### Post by Doug S on 2015-08-11
I missed RC4 and RC5, but now running [Kernel 4.2RC6]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-rc6-unstable/"). All good, so far.

---

### Post by frostschutz on 2015-08-11
4.2-rc6 fixes an off-by-one issue with USB3 / xhci-ring.c that affected me and caused my USB3 speed to drop to USB1 levels in the 4.0/4.1 series.

Looking forward to 4.2 stable release :)

---

### Post by Doug S on 2015-08-28
I fell behind again, but am now running [4.2RC8]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-rc8-unstable/"). All is good.

---

### Post by Doug S on 2015-09-03
There appears to be a regression in kernel 4.2, at least on my system.
If I take my highest numbered CPU off-line, then suspend (pm-suspend) no longer works.
I have narrowed the regression down to between kernel 4.1 and kernel 4.2RC1, and am now continuing via bisecting the kernel.
Can anyone confirm or contradict?

Method of test (I have 8 CPUs):```
doug@s15:~$ sudo su
root@s15:/home/doug# echo -n 0 > /sys/devices/system/cpu/cpu7/online
root@s15:/home/doug# cat /sys/devices/system/cpu/cpu*/online
1
1
1
1
1
1
0
root@s15:/home/doug# pm-suspend

```
The system does not suspend.
If I take any other CPU off-line instead, or no CPU off-line, the system will suspend normally.

---

### Post by dino99 on 2015-09-03
by 'CPU' i suppose you mean 'CORE'

then i've a doubt about 'cpu off-line', is 'suspend' supposed to run in that case ?

---

### Post by Doug S on 2015-09-03
> **dino99 said:**
> by 'CPU' i suppose you mean 'CORE'

then i've a doubt about 'cpu off-line', is 'suspend' supposed to run in that case ?No, I meant CPU, or in my case 1 of 2 threads on core 3. 
However, I have tried to reduce the issue to its simplest form for this post and for my bisection. Perhaps I went too far.
The issue also occurs of I take CPUs 3 and 7, or core 3, off-line.

The behavior is both different than it used to be and inconsistent is all I am saying.

---

### Post by dino99 on 2015-09-03
the 'suspend' feature may have some limits not handled on system with many threaded cpus (lkml checks needed)

---

### Post by Doug S on 2015-09-03
> **dino99 said:**
> the 'suspend' feature may have some limits not handled on system with many threaded cpus (lkml checks needed)lkml: Yes, of course, and I will do so as soon as I have all of my supporting evidence (about 6 kernel compiles left, started at 17.)

My purpose with my post was just to try to get someone else to try this on another computer and confirm or deny.

---

### Post by matt_symes on 2015-09-03
I thought pm-suspend (pm-utils in general) was not used with systemd as it's not needed.

I'm still on 14.04 though so i am going by hearsay and not experience on this one.

---

### Post by Doug S on 2015-09-03
> **matt_symes said:**
> I thought pm-suspend (pm-utils in general) was not used with systemd as it's not needed.Matt, I wouldn't know, I tend to test these kernel RC series on a 14.04 server.

The culprit seems to be:

commit 87549141d516aee71d511138e27117c41e8aef68
Author: Viresh Kumar <[EMAIL="viresh.kumar@linaro.org"]viresh.kumar@linaro.org[/EMAIL]>
Date:   Wed Jun 10 02:13:21 2015 +0200
 
cpufreq: Stop migrating sysfs files on hotplug

---

### Post by matt_symes on 2015-09-03
> Matt, I wouldn't know, I tend to test these kernel RC series on a 14.04 server.

Ahh. You're on 14.04 as well then :)

---

### Post by Doug S on 2015-09-04
> **Doug S said:**
> The culprit seems to be:

commit 87549141d516aee71d511138e27117c41e8aef68
Author: Viresh Kumar <[EMAIL="viresh.kumar@linaro.org"]viresh.kumar@linaro.org[/EMAIL]>
Date:   Wed Jun 10 02:13:21 2015 +0200
 
cpufreq: Stop migrating sysfs files on hotplugAn update: It turns out that a pure suspend to ram via "# echo mem > /sys/power/state" works fine. For as yet unknown reasons, pm-suspend is failing here (from /var/log/pm-suspend.log):```
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
sh: echo: I/O error
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: Returned exit code 1.

Fri Sep  4 18:25:00 PDT 2015: Inhibit found, will not perform suspend
Fri Sep  4 18:25:00 PDT 2015: Running hooks for resume
```

---

### Post by dino99 on 2015-09-05
Good finding Doug,

As so many users have issues with the 'suspend' feature, it should be usefull to get a report sent with all your experiments & results. As that kind of feature has multiple events with the kernel & graphic driver & .... it possibly affect multiple packages

---

### Post by matt_symes on 2015-09-05
Have you tried debugging using the PM_DEBUG environmental variable ? Pass into pm-suspend as usual.

It uses "set -x" in /usr/lib/pm-utils/pm-action, the file that pm-suspend is symlinked to.

It will help identify why 95cpufreq is failing.

---

### Post by Doug S on 2015-09-05
> **matt_symes said:**
> Have you tried debugging using the PM_DEBUG environmental variable ? Pass into pm-suspend as usual.
It uses "set -x" in /usr/lib/pm-utils/pm-action, the file that pm-suspend is symlinked to
It will help identify why 95cpufreq is failing.I did not know that, thanks. Anyway, I have figured it out, and it has been confirmed / explained better on the [EMAIL="linux-pm@vger.kernel.org"]linux-pm@vger.kernel.org[/EMAIL] e-mail list. I'll copy the relevant text here:

```
Me:
> The echo line fails because the related CPU is offline.
> If the failed echo is the last pass through the loop,
> then the script interprets the overall execution of
> 94cpufreq as a failure and aborts the suspend. If the
> failed echo is not the last pass through the loop, then
> the bad exit code gets overwritten with a good one before
> the loop exits.
>
> Since the loop is merely setting a temporary governor,
> to test I just used performance mode anyway, and commented
> out the echo. pm-suspend with CPU 7 offline then worked fine.
>
> I have not yet gone back to any before the patch kernel
> to determine why it used to work (it is late in my time zone).
> However, I would have to assume that before the commit in
> question, the echo worked even if the CPU was offline.

Viresh Kumar:
 
So here is the story behind it.
- In your system all CPUs are independent, that is there are no links
  to cpufreq directory, so that check in the script is useless for
  you.
- The $COMMIT in question did a significant change. Earlier, while
  offlining the CPU, we used to remove the cpufreq directory from
  sysfs, which is not the case any more.
 
- So to be precise, following lines came to your rescue earlier:
 
# if we do not have a scaling_governor file, skip.
# [ -f "$gov" ] || continue
 
- But they don't after the patch, as the file and directory are
  present even if the CPU is offline.
- But because the CPU is offline, writing to those files isn't allowed
  and so the echo failed.
 
Solution to that is that we check for CPU offline as well in the
beginning of the script, and skip if the CPU is offline.

```So, I will post a bug report to the pm-utils bug list, and then enter one on launchpad linking to the upstream one.
First I wanted to try to make and test a fix so as to post a possible solution with the bug submission.
However, I am not very script savvy, and would welcome any inputs for how to replace the current check with one that checks the online status instead. I.E. checks this:```
$ cat /sys/devices/system/cpu/cpu*/online
1
0
1
1
1
0
1
```and executes or bypasses accordingly.

EDIT: Considering the special case of CPU 0, maybe it should be an additional test, instead of a replacement test.

---

### Post by matt_symes on 2015-09-05
If you just want to skip offline CPUs then something like this should work for you.

```
[ $(cat "$x/online") = "1" ] || continue;
```

No real need to check for the online files existence after that change outlined in your email exchange although you may want to just in case... Code defensively and all that.

EDIT

I've been meaning to ask; why are you offlining CPUs ?

EDIT2: Well done btw. Nice work !

EDIT3: after checking, I see that cpu0 does not have the online file, presumably because it cannot be offlined, so you do need to check for the existence of the online file in the loop.

I broke one of my golden rules by not checking first so I'm glad I did. 

Assumption is the mother of all *censored* ups :)

---

### Post by Doug S on 2015-09-06
Matt, I did not see your EDITs until now. I have been working for hours now trying to get this to work.

> **matt_symes said:**
> If you just want to skip offline CPUs then something like this should work for you.

```
[ $(cat "$x/online") = "1" ] || continue;
```

No real need to check for the online files existence after that change outlined in your email exchange although you may want to just in case... Code defensively and all that.Yes, that works great, Thanks. However... read on.

> **matt_symes said:**
> I've been meaning to ask; why are you offlining CPUs ?I was looking into [a bug report]("https://bugzilla.kernel.org/show_bug.cgi?id=80651"), which required taking some CPUs offline to create the resume from suspend issue whereby the CPU frequency locks up at the non-turbo maximum. I stumbled across the new kernel 4.2 issue and now a several day saga has ensued.

> **matt_symes said:**
> Well done btw. Nice work !Thanks.

> **matt_symes said:**
> after checking, I see that cpu0 does not have the online file, presumably because it cannot be offlined, so you do need to check for the existence of the online file in the loop.Yes, exactly, and that is what I have struggling with for hours now. I must be doing something dense.

Here is one of my more recent attempts, along with a bunch of my added debug stuff:
```
hibernate_cpufreq()
{
        ( cd /sys/devices/system/cpu/
        for x in cpu[0-9]*; do
                # if cpufreq is a symlink, it is handled by another cpu. Skip.
                [ -L "$x/cpufreq" ] && continue
                gov="$x/cpufreq/scaling_governor"
                # if we do not have a scaling_governor file, skip.
                [ -f "$gov" ] || continue
                echo "before $x online check"
                # if the CPU is offline, skip, unless no file, i.e. CPU0.
                if [ $(cat "$x/online") = "1" ] || [ ! -f "$x/online" ]; then
                        continue;
                fi
                echo "after $x online check"
                # if our temporary governor is not available, skip.
                grep -q "$TEMPORARY_CPUFREQ_GOVERNOR" \
                        "$x/cpufreq/scaling_available_governors" || continue
                savestate "${x}_governor" < "$gov"
                echo "$x"
                echo "$TEMPORARY_CPUFREQ_GOVERNOR"
                echo "$gov"
                echo "$TEMPORARY_CPUFREQ_GOVERNOR" > "$gov"
        done )
}
```But for reasons that I do not understand, it doesn't seem to work properly and I get this in /var/log/pm-suspend.log:```
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
before cpu0 online check
cat: cpu0/online: No such file or directory
/usr/lib/pm-utils/sleep.d/94cpufreq: 21: [: =: unexpected operator
before cpu1 online check
before cpu2 online check
before cpu3 online check
before cpu4 online check
before cpu5 online check
before cpu6 online check
before cpu7 online check
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
```By the way, all CPUs were on online. And if I do this:```
 
               ...
               echo "before $x online check"
                # if the CPU is offline, skip, unless no file, i.e. CPU0.
                [ $(cat "$x/online") = "1" -o ! -f "$x/online" ] || continue
                echo "after $x online check"
                ...

```Then I get this:```
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
before cpu0 online check
cat: cpu0/online: No such file or directory
/usr/lib/pm-utils/sleep.d/94cpufreq: 21: [: =: unexpected operator
before cpu1 online check
after cpu1 online check
cpu1
performance
cpu1/cpufreq/scaling_governor
before cpu2 online check
after cpu2 online check
cpu2
performance
cpu2/cpufreq/scaling_governor
before cpu3 online check
after cpu3 online check
cpu3
performance
cpu3/cpufreq/scaling_governor
before cpu4 online check
after cpu4 online check
cpu4
performance
cpu4/cpufreq/scaling_governor
before cpu5 online check
after cpu5 online check
cpu5
performance
cpu5/cpufreq/scaling_governor
before cpu6 online check
after cpu6 online check
cpu6
performance
cpu6/cpufreq/scaling_governor
before cpu7 online check
after cpu7 online check
cpu7
performance
cpu7/cpufreq/scaling_governor
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
```Notice that CPU 0 didn't save and get set to PERFORMANCE mode properly.
I have also tried about 53 other scenarios.

---

### Post by tista on 2015-09-06
Hi Doug,

Yes. Intel CPUs doesn't have online state on CPU0 (initial and primary) because at leaset 1 core must be always online. On the other hand, like Tegra K1, it has "LP" core as primary core outside of those CPU[0-4]. If so, Tegra K1 can handle online state on all of CPU[0-4]...

So you don't have to check CPU0 state out for setting scaling governor.

Regards.

---

### Post by Doug S on 2015-09-07
> **tista said:**
> Hi Doug,

Yes. Intel CPUs doesn't have online state on CPU0 (initial and primary) because at leaset 1 core must be always online. On the other hand, like Tegra K1, it has "LP" core as primary core outside of those CPU[0-4]. If so, Tegra K1 can handle online state on all of CPU[0-4]...

So you don't have to check CPU0 state out for setting scaling governor.

Regards.Yes, and the solution I am attempting to get working and propose isn't dependent on CPU0 at all, just the condition that if the file exists, that the CPU be online, and if it doesn't exist then assume the CPU is online. Note that there is a previous check and skip for the no governor or no CPU condition.

---

### Post by Doug S on 2015-09-07
Re: pm-suspend broken:

For reference, I have filed an [upstream bug report]("https://bugs.freedesktop.org/show_bug.cgi?id=91914") and an identical [launchpad one]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1493156"). I never figured out a final solution that works, but someone suggested to just force a good return code at the end of the subroutine, which is a good idea, allowing me to get back to what I was doing before this tangent.

---

### Post by matt_symes on 2015-09-09
Hi Doug.

Been afk for a couple of days.

To check for the existence of the file online you want to follow the syntax that checks for the existence of the gov file.

[ -f "$x/online" ] || continue;

That before the check for the value in the online file.

EDIT

BTW the reason why your check failed is because you need to check for the existence of the online file before checking it value.

Also you want to use an "and" comparison and not an"or" comparison so when checking the file exists, the "and" comparison would fail when the file does exist and short circuiting would ensure the test would then not try to get the value for the online file.

---

### Post by Doug S on 2015-09-11
> **matt_symes said:**
> Hi Doug.

Been afk for a couple of days.Hi Matt,
this time it was me that was afk for a couple of days.

> **matt_symes said:**
> To check for the existence of the file online you want to follow the syntax that checks for the existence of the gov file.

[ -f "$x/online" ] || continue;

That before the check for the value in the online file.Yes, but in this case I want to continue of the file doesn't exist, to cover the CPU0 case. I specifically did not want to specify CPU0, because I have read that in future it might not be forced to be CPU0.

> **matt_symes said:**
> BTW the reason why your check failed is because you need to check for the existence of the online file before checking it value.

Also you want to use an "and" comparison and not an"or" comparison so when checking the file exists, the "and" comparison would fail when the file does exist and short circuiting would ensure the test would then not try to get the value for the online file. I think I wanted "or" because I want "IF the file doesn't exist OR if its content says that the CPU is online THEN CONTINUE".
Anyway, I gave up and just forced a good return good and moved on. Now, I have another issue that I hope to get back today.

---

### Post by Doug S on 2015-10-11
> **Doug S said:**
> Re: pm-suspend broken:

For reference, I have filed an [upstream bug report]("https://bugs.freedesktop.org/show_bug.cgi?id=91914") and an identical [launchpad one]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1493156"). I never figured out a final solution that works, but someone suggested to just force a good return code at the end of the subroutine, which is a good idea, allowing me to get back to what I was doing before this tangent.There was continuing upstream discussion on this, and a patch has just been submitted for test and review that would negate the need for the bug reports I filed. If the patch set eventually gets merged, I'll cancel the bug reports.

---

### Post by aljosa2 on 2015-10-23
[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)

In both 4.2.4 and 4.1.11 folder the amd64.deb version is missing?

---

### Post by zika on 2015-10-24
> **aljosa2 said:**
> [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)
In both 4.2.4 and 4.1.11 folder the amd64.deb version is missing?64-bit version is missing in all branches for few days... In 999, 996 also...
```
[COLOR=#000000]rsync -a --exclude=dkms.conf --delete spl/ /home/kernel/COD/linux/debian/build/build-generic/spl/
[/COLOR]rsync: change_dir "/home/kernel/COD/linux//spl" failed: No such file or directory (2)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1183) [sender=3.1.0]
make: *** [/home/kernel/COD/linux/debian/stamps/stamp-build-generic] Error 23
```(end of build.log file...)

---

