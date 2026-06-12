---
title: "Kernel 5.14 RC (Release Candidate) series"
date: 2021-07-13
forum: Ubuntu Development Version
---

### Post by Doug S on 2021-07-13
Kernel 5.14-rc1 has been released, but all versions did not build on the [Ubuntu mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.14-rc1/").
I have to compile the kernel myself anyhow, and that worked fine:

```
doug@s19:~$ uname -a
Linux s19 5.14.0-rc1-stock #901 SMP PREEMPT Tue Jul 13 07:13:01 PDT 2021 x86_64 x86_64 x86_64 GNU/Linux
```

Here is the link back trail to previous rc series threads:

[5.13]("https://ubuntuforums.org/showthread.php?t=2461891"), [5.12]("https://ubuntuforums.org/showthread.php?t=2458625"), [5.11]("https://ubuntuforums.org/showthread.php?t=2455791"), [5.10]("https://ubuntuforums.org/showthread.php?t=2452692"), [5.9]("https://ubuntuforums.org/showthread.php?t=2448933"), [5.8]("https://ubuntuforums.org/showthread.php?t=2445465"), [5.7]("https://ubuntuforums.org/showthread.php?t=2440607"), [5.6]("https://ubuntuforums.org/showthread.php?t=2436608"), [5.5]("https://ubuntuforums.org/showthread.php?t=2432815"), [5.4]("https://ubuntuforums.org/showthread.php?t=2428734"), [5.3]("https://ubuntuforums.org/showthread.php?t=2423441"), [5.2]("https://ubuntuforums.org/showthread.php?t=2419363"), [5.1]("https://ubuntuforums.org/showthread.php?t=2414938"), [5.0]("https://ubuntuforums.org/showthread.php?t=2409811"), [4.20]("https://ubuntuforums.org/showthread.php?t=2405365"), 4.19 ?, [4.18]("https://ubuntuforums.org/showthread.php?t=2394500"), [4.17]("https://ubuntuforums.org/showthread.php?t=2389561"), [4.16]("https://ubuntuforums.org/showthread.php?t=2384781"), [4.15]("https://ubuntuforums.org/showthread.php?t=2378956"), [4.14]("https://ubuntuforums.org/showthread.php?t=2371638").

---

### Post by zika on 2021-07-16
[https://www.youtube.com/watch?v=y3rPmkjUyxY](https://www.youtube.com/watch?v=y3rPmkjUyxY)

---

### Post by Doug S on 2021-07-16
The compile actually seems to work fine, but there seems to be a spurious "+" sign in the path. From the log file:

```
  SIGN    /home/kernel/COD/linux/debian/linux-modules-5.14.0-051400rc1-generic[COLOR="#FF0000"]//[/COLOR]lib/modules/5.14.0-051400rc1-generic[COLOR="#FF0000"]+[/COLOR]/kernel/sound/xen/snd_xen_front.ko
  SIGN    /home/kernel/COD/linux/debian/linux-modules-5.14.0-051400rc1-generic[COLOR="#FF0000"]//[/COLOR]lib/modules/5.14.0-051400rc1-generic[COLOR="#FF0000"]+[/COLOR]/kernel/sound/usb/snd-usb-audio.ko
  DEPMOD  /home/kernel/COD/linux/debian/linux-modules-5.14.0-051400rc1-generic[COLOR="#FF0000"]//[/COLOR]lib/modules/5.14.0-051400rc1-generic[COLOR="#FF0000"]+[/COLOR]
```

Now notice no "+" sign:

```
mv /home/kernel/COD/linux/debian/linux-modules-5.14.0-051400rc1-generic/lib/modules/5.14.0-051400rc1-generic/modules.order \
	/home/kernel/COD/linux/debian/linux-modules-5.14.0-051400rc1-generic/lib/modules/5.14.0-051400rc1-generic/_
mv: cannot stat '/home/kernel/COD/linux/debian/linux-modules-5.14.0-051400rc1-generic/lib/modules/5.14.0-051400rc1-generic/modules.order': No such file or directory
```

I haven't seen any traffic on the kernel channel on [IRC]("https://irclogs.ubuntu.com/2021/07/15/%23ubuntu-kernel.html") about the build problems. (I looked at many days, not just the day of the link.)

Here is the same/similar stuff from my compile log, noting that multi-threaded ordering will be different:

```
  SIGN    debian/linux-image/lib/modules/5.14.0-rc1-stock2/kernel/sound/virtio/virtio_snd.ko
  SIGN    debian/linux-image/lib/modules/5.14.0-rc1-stock2/kernel/sound/x86/snd-hdmi-lpe-audio.ko
  SIGN    debian/linux-image/lib/modules/5.14.0-rc1-stock2/kernel/sound/xen/snd_xen_front.ko
  DEPMOD  debian/linux-image/lib/modules/5.14.0-rc1-stock2
```

and I don't have the "mv" step.

---

### Post by zika on 2021-07-18
It seems that, one week later, we have first .deb files ready on Ubuntu mainline...
```
 :~$ uname -r
5.14.0-051400rc2daily20210719-generic
```
Update&#8321;:
It works nice on a rather old machine. On a rather new machine: no boot... Who would have said...

---

### Post by Doug S on 2021-07-19
> **zika said:**
> It seems that, one week later, we have first .deb files ready on Ubuntu mainline...
```
 :~$ uname -r
5.14.0-051400rc2daily20210719-generic
```Aghhh, finally. It is late here, I'll try it tomorrow.

With 5.14-rc1 I just had:

```
Message from syslogd@s19 at Jul 18 19:34:09 ...
 kernel:[469844.099059] watchdog: BUG: soft lockup - CPU#10 stuck for 22s! [kworker/10:0:556474]

Message from syslogd@s19 at Jul 18 19:34:37 ...
 kernel:[469872.099056] watchdog: BUG: soft lockup - CPU#10 stuck for 48s! [kworker/10:0:556474]
...
Message from syslogd@s19 at Jul 18 19:38:21 ...
 kernel:[470096.099034] watchdog: BUG: soft lockup - CPU#10 stuck for 257s! [kworker/10:0:556474]
client_loop: send disconnect: Connection reset
```

Which I also had at [the end of the 5.13-rc series]("https://ubuntuforums.org/showthread.php?t=2461891&p=14047257#post14047257"), but thought it was a BIOS upgrade issue. But it is a very brutal test that I am running.

EDIT: ... the next monring ...
Now I get another compile error:

```
doug@s19:~/temp-k-git/linux$ time make -j13 olddefconfig bindeb-pkg LOCALVERSION=-stock > bla
 dpkg-source --before-build .
 debian/rules binary
make[5]: *** [COLOR="#FF0000"]No rule to make target 'debian/canonical-revoked-certs.pem', needed by 'certs/x509_revocation_list'.  Stop.[/COLOR]
make[5]: *** Waiting for unfinished jobs....
make[4]: *** [Makefile:1842: certs] Error 2
make[4]: *** Waiting for unfinished jobs....
make[3]: *** [debian/rules:7: build-arch] Error 2
dpkg-buildpackage: error: debian/rules binary subprocess returned exit status 2
make[2]: *** [scripts/Makefile.package:83: bindeb-pkg] Error 2
make[1]: *** [Makefile:1560: bindeb-pkg] Error 2
make: *** [Makefile:351: __build_one_by_one] Error 2
```And so needed to add this to my compile procedure:

```
doug@s19:~/temp-k-git/linux$ scripts/config --disable SYSTEM_REVOCATION_KEYS
```

So, to summarize: For a new rc compile, starting with the mainline PPA kernel configuration file:

```
doug@s19:~/temp-k-git/linux$ scripts/config --disable SYSTEM_TRUSTED_KEYS
doug@s19:~/temp-k-git/linux$ scripts/config --disable DEBUG_INFO
doug@s19:~/temp-k-git/linux$ scripts/config --disable SYSTEM_REVOCATION_KEYS
```

resulting in, after compile:

```
doug@s19:~/temp-k-git/linux$ scripts/diffconfig .config-5.14.0-051400rc2-lowlatency .config
-DEBUG_INFO_BTF y
-DEBUG_INFO_BTF_MODULES y
-DEBUG_INFO_COMPRESSED n
-DEBUG_INFO_DWARF4 y
-DEBUG_INFO_DWARF_TOOLCHAIN_DEFAULT n
-DEBUG_INFO_REDUCED n
-DEBUG_INFO_SPLIT n
-GDB_SCRIPTS y
-PAHOLE_HAS_SPLIT_BTF y
 AS_VERSION 23690 -> 23400
 CC_VERSION_TEXT "gcc (Ubuntu 10.3.0-6ubuntu1) 10.3.0" -> "gcc (Ubuntu 9.3.0-17ubuntu1~20.04) 9.3.0"
 DEBUG_INFO y -> n
 GCC_VERSION 100300 -> 90300
 LD_VERSION 23690 -> 23400
 SYSTEM_REVOCATION_KEYS "debian/canonical-revoked-certs.pem" -> ""
 SYSTEM_TRUSTED_KEYS "debian/canonical-certs.pem" -> ""
```

---

### Post by zika on 2021-07-19
5.14 came, also, from Ubuntu repositories, so, now, it's a bit more stable source...
```
:~$ apt search 5.14|grep install
linux-headers-5.14.0-1-generic/impish,now 5.14.0-1.1 amd64 [installed,automatic]
linux-image-5.14.0-1-generic/impish,now 5.14.0-1.1 amd64 [installed,automatic]
linux-modules-5.14.0-1-generic/impish,now 5.14.0-1.1 amd64 [installed,automatic]
linux-modules-extra-5.14.0-1-generic/impish,now 5.14.0-1.1 amd64 [installed,automatic]
linux-unstable-headers-5.14.0-1/impish,impish,now 5.14.0-1.1 all [installed,automatic
```
It works quite nice on old machine.
On new one:
```
[   14.520056] gpio gpiochip2: (gpio_aaeon): tried to insert a GPIO c>
[   14.520099] gpiochip_add_data_with_key: GPIOs 0..-1 (gpio_aaeon) f>
[   14.520140] gpio-aaeon: probe of gpio-aaeon.0 failed with error -22
```
I'll have to see what that means, in a kind of rush right now... Looks to me more for Pi than for Ryzen (where this happens) but little do I know now...
Update&#8321;: GPIO hurdle jumped over but something else does make kernel stall just like that from mainline. Will investigate more...
Update&#8322;: Got some spare time and got **5.14** workin' on that newer machine in **drm-tip** flavour. Searching for difference to fugure out a reason why that one works and other two do not...
Update&#8323;: Daily finally booted OK. 5.14.0-2 from Ubuntu started having same issue as Daily had... Waiting for 5.14.0-3... ;) DrmTip is OK all the time since it started working...
Update&#8324;: Finally, waiting was worthwhile. All 3 (drmtip, daily and rc3) are working nice.

---

### Post by Doug S on 2021-08-04
Ever since kernel 5.14-rc1 I have been getting (for example):

```
Jul 13 07:34:05 s19 kernel: Unknown command line parameters: BOOT_IMAGE=/boot/vmlinuz-5.14.0-rc1-stock
```but I don't know what the problem is:

My command lines have been:

```
Aug 02 08:12:14 s19 kernel: Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.14.0-rc3-teo root=UUID=0ac356c1-caa9-4c2e-8229-4408bd998dbd ro ipv6.disable=1 consoleblank=314 intel_pstate=active intel_pstate=no_hwp msr.allow_writes=on cpuidle.governor=teo
```

and:

```
Aug 04 15:23:03 s19 kernel: Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.14.0-rc3-teo2 root=UUID=0ac356c1-caa9-4c2e-8229-4408bd998dbd ro ipv6.disable=1 consoleblank=450 intel_pstate=passive intel_pstate=no_hwp cpufreq.default_governor=ondemand msr.allow_writes=on cpuidle.governor=teo
```

For as yet unknown reasons (but the kernel version has been eliminated) my system is starting with HWP enabled regardless, since July 6th, which does coincide with [a BIOS update]("https://ubuntuforums.org/showthread.php?t=2461891&p=14047257#post14047257"), but the system at first lists HWP as disabled:

```
Aug  4 16:24:44 s19 kernel: [    0.000000] intel_pstate: HWP disabled... Doug...3
``` and then later on it is enabled:

```
Aug  4 16:24:44 s19 kernel: [    0.374427] intel_pstate: HWP enabled... Doug...1
```Note: I put the flags there, just to be sure where the messages came from.

Going backwards quickly these weeks.
Note: for also unknown reasons, I am unable to go back to the previous BIOS version as a test. Seems to have been a one way trip, which is counter to the most basic of system rules. Sigh...

EDIT: I added another flag and edited above. O.K. so flag 3 doesn't prove anything, because it is just saying what the command line is telling it. So this looks like a BIOS issue.

---

### Post by xyz-t on 2021-08-04
> **Doug S said:**
> E
Note: for also unknown reasons, I am unable to go back to the previous BIOS version as a test. Seems to have been a one way trip, which is counter to the most basic of system rules. Sigh...

EDIT: I added another flag and edited above. O.K. so flag 3 doesn't prove anything, because it is just saying what the command line is telling it. So this looks like a BIOS issue.

That means you have a BIOS parameter(s) that prevents flashing an older version.

Lenovo > Security > UEFI BIOS Update Option (1) > Secure RollBack Prevention > Disabled > Allows flashing to older version / Enabled > Prevents flashing previous ones.

UEFI BIOS Update Option (2) > Windows UEFI Firmware Update > Disabled > BIOS will skip Windows UEFI firmware update.

Both are disabled and previous versions are working. From memory, I do believe they were enabled out of the box.

```
uname -r
5.14.0-051400rc4-generic
```

I hope you're not too affected by the fires mate and you have air conditioning. 

Take care,

---

### Post by Doug S on 2021-08-06
> **xyz-t said:**
> That means you have a BIOS parameter(s) that prevents flashing an older version.
Lenovo > Security > UEFI BIOS Update Option (1) > Secure RollBack Prevention > Disabled > Allows flashing to older version / Enabled > Prevents flashing previous ones.
UEFI BIOS Update Option (2) > Windows UEFI Firmware Update > Disabled > BIOS will skip Windows UEFI firmware update.
Thanks.
This Motherboard is an ASUS Prime Z490-A, and so far I still haven't been able to go back to BIOS version 1003. I contacted ASUS, but they merely referred me to a procedure that I had already tried and had already said didn't work in my initial inquiry to them. Grrr...

> **xyz-t said:**
> I hope you're not too affected by the fires mate and you have air conditioning.We have been lucky, with only a couple of days of haze, so far. We don't have air conditioning.

---

### Post by Doug S on 2021-08-07
> **Doug S said:**
> Ever since kernel 5.14-rc1 I have been getting (for example):

```
Jul 13 07:34:05 s19 kernel: Unknown command line parameters: BOOT_IMAGE=/boot/vmlinuz-5.14.0-rc1-stock
```but I don't know what the problem is:
I bisected the kernel only to find this:

```
doug@s19:~/temp-k-git/linux$ git show 86d1919a4fb0d9c115dd1d3b969f5d1650e45408
commit 86d1919a4fb0d9c115dd1d3b969f5d1650e45408
Author: Andrew Halaney <ahalaney@redhat.com>
Date:   Wed Jun 30 18:56:28 2021 -0700

    init: print out unknown kernel parameters

    It is easy to foobar setting a kernel parameter on the command line
    without realizing it, there's not much output that you can use to assess
    what the kernel did with that parameter by default.

    Make it a little more explicit which parameters on the command line
    _looked_ like a valid parameter for the kernel, but did not match anything
    and ultimately got tossed to init.  This is very similar to the unknown
    parameter message received when loading a module.

    This assumes the parameters are processed in a normal fashion, some
    parameters (dyndbg= for example) don't register their parameter with the
    rest of the kernel's parameters, and therefore always show up in this list
    (and are also given to init - like the rest of this list).

    [COLOR="#FF0000"]Another example is BOOT_IMAGE= is highlighted as an offender, which it
    technically is, but is passed by LILO and GRUB so most systems will see
    that complaint.[/COLOR]

    An example output where "foobared" and "unrecognized" are intentionally
    invalid parameters:

      Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.12-dirty debug log_buf_len=4M foobared unrecognized=foo
      [COLOR="#FF0000"]Unknown command line parameters[/COLOR]: foobared [COLOR="#FF0000"]BOOT_IMAGE=/boot/vmlinuz-5.12-dirty[/COLOR] unrecognized=foo

    Link: https://lkml.kernel.org/r/20210511211009.42259-1-ahalaney@redhat.com
    Signed-off-by: Andrew Halaney <ahalaney@redhat.com>
    Suggested-by: Steven Rostedt <rostedt@goodmis.org>
    Suggested-by: Borislav Petkov <bp@suse.de>
    Acked-by: Borislav Petkov <bp@suse.de>
    Signed-off-by: Andrew Morton <akpm@linux-foundation.org>
    Signed-off-by: Linus Torvalds <torvalds@linux-foundation.org>

diff --git a/init/main.c b/init/main.c
index e9c42a183e33..d4f7af4cf560 100644
--- a/init/main.c
+++ b/init/main.c
@@ -872,6 +872,47 @@ void __init __weak arch_call_rest_init(void)
        rest_init();
 }

+static void __init print_unknown_bootoptions(void)
+{
+       char *unknown_options;
+       char *end;
+       const char *const *p;
+       size_t len;
+
+       if (panic_later || (!argv_init[1] && !envp_init[2]))
+               return;
+
+       /*
+        * Determine how many options we have to print out, plus a space
+        * before each
+        */
+       len = 1; /* null terminator */
+       for (p = &argv_init[1]; *p; p++) {
+               len++;
+               len += strlen(*p);
+       }
+       for (p = &envp_init[2]; *p; p++) {
+               len++;
+               len += strlen(*p);
+       }
+
+       unknown_options = memblock_alloc(len, SMP_CACHE_BYTES);
+       if (!unknown_options) {
+               pr_err("%s: Failed to allocate %zu bytes\n",
+                       __func__, len);
+               return;
+       }
+       end = unknown_options;
+
+       for (p = &argv_init[1]; *p; p++)
+               end += sprintf(end, " %s", *p);
+       for (p = &envp_init[2]; *p; p++)
+               end += sprintf(end, " %s", *p);
+
+       pr_notice("Unknown command line parameters:%s\n", unknown_options);
+       memblock_free(__pa(unknown_options), len);
+}
+
 asmlinkage __visible void __init __no_sanitize_address start_kernel(void)
 {
        char *command_line;
@@ -913,6 +954,7 @@ asmlinkage __visible void __init __no_sanitize_address start_kernel(void)
                                  static_command_line, __start___param,
                                  __stop___param - __start___param,
                                  -1, -1, NULL, &unknown_bootoption);
+       print_unknown_bootoptions();
        if (!IS_ERR_OR_NULL(after_dashes))
                parse_args("Setting init args", after_dashes, NULL, 0, -1, -1,
                           NULL, set_init_arg);
```

---

### Post by Doug S on 2021-08-08
> **Doug S said:**
> For as yet unknown reasons (but the kernel version has been eliminated) my system is starting with HWP enabled regardless, since July 6th, which does coincide with [a BIOS update]("https://ubuntuforums.org/showthread.php?t=2461891&p=14047257#post14047257"), but the system at first lists HWP as disabled:

```
Aug  4 16:24:44 s19 kernel: [    0.000000] intel_pstate: HWP disabled... Doug...3
``` and then later on it is enabled:

```
Aug  4 16:24:44 s19 kernel: [    0.374427] intel_pstate: HWP enabled... Doug...1
```Note: I put the flags there, just to be sure where the messages came from.

Note: for also unknown reasons, I am unable to go back to the previous BIOS version as a test. Seems to have been a one way trip, which is counter to the most basic of system rules.

EDIT: I added another flag and edited above. O.K. so flag 3 doesn't prove anything, because it is just saying what the command line is telling it. So this looks like a BIOS issue.

I added yet another patch to the intel_pstate driver, checking the state of the HWP enable bit in the MSR extremely early in the boot cycle:
```
Aug  6 08:03:47 s19 kernel: [    0.000000] intel_pstate: HWP disabled... Doug...3
Aug  6 08:03:47 s19 kernel: [    0.000000] intel_pstate: ... but HWP already enabled in processor ...
```This is almost certainly a BIOS issue, and I have an escalation in progress with ASUS.

---

### Post by Doug S on 2021-08-08
Kernel version 5.14-rc5 is available from both [kernel.org]("https://www.kernel.org/") and [the Ubuntu mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.14-rc5/").

Likely nobody cares, but:
Kernel 5.14-rc1 included some changes to the teo (Timer Events Orientated) idle governor, but also introduced a regression if idle state 0 was disabled. Fixed in -rc5.
I think most use the default menu idle governor and don't typically disable idle states.

```
doug@s19:~$ uname -a
Linux s19 5.14.0-rc5-stock #928 SMP PREEMPT Sun Aug 8 17:01:48 PDT 2021 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by DougieFresh4U on 2021-08-10
Not sure what my issue is but when trying to install from mainline I'm
getting this messege for rc5 headers or that matter any of the 5.14:

[B][HTML][B][B]dpkg: error: unable to read filedescriptor flags for
 <package status and progress file descriptor>: Bad file descriptor[/B][/B][/HTML][/B]

I usually install kernels the 'easy' way by using the .deb

---

### Post by Smask on 2021-08-12
> **DougieFresh4U said:**
> Not sure what my issue is but when trying to install from mainline I'm
getting this messege for rc5 headers or that matter any of the 5.14:

[HTML][B][B]dpkg: error: unable to read filedescriptor flags for
 <package status and progress file descriptor>: Bad file descriptor[/B][/B][/HTML]

Got the same error message when trying to install OpenHantek deb file from GitHub.

Edit:
I built OpenHantek6022 from source, gdebi still barfed the same way. Then I tried install it using dpkg --install the .deb file. No problem.
 [https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/1756238](https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/1756238)

---

### Post by IanW on 2021-08-23
Linus pushed 5.14 RC-7 out of the nest on Sunday, he says it's unlikely to need an RC-8.

[https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.14-rc7#](https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.14-rc7#)

It's already appeared on the PPA - [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.14-rc7/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.14-rc7/)

---

### Post by Doug S on 2021-08-30
[Kernel 5.14]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.14/") has been released. As IanW mentioned last week might be the case, indeed there was no -RC8 this cycle.```
doug@s19:~$ uname -a
Linux s19 5.14.0-stock #931 SMP PREEMPT Mon Aug 30 07:45:51 PDT 2021 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Doug S on 2021-09-06
> **Doug S said:**
> I added yet another patch to the intel_pstate driver, checking the state of the HWP enable bit in the MSR extremely early in the boot cycle:
```
Aug  6 08:03:47 s19 kernel: [    0.000000] intel_pstate: HWP disabled... Doug...3
Aug  6 08:03:47 s19 kernel: [    0.000000] intel_pstate: ... but HWP already enabled in processor ...
```This is almost certainly a BIOS issue, and I have an escalation in progress with ASUS.Update: While ASUS has been responsive about the BIOS issue, we seems to have severe communication issues and have yet to agree that an issue even exists. They claim BIOS version 1003 and 2103 behave the same, but I do not think they are doing the test correctly, simple as it is. My older ASUS Z390-P motherboard, with an older BIOS doesn't have the issue.

---

