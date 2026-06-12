---
title: "Kernel 5.9 RC (Release Candidate) series"
date: 2020-08-16
forum: Ubuntu Development Version
---

### Post by Doug S on 2020-08-16
Kernel 5.9-rc1 is available from [kernel.org]("https://www.kernel.org/"), and the [Ubuntu Mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.9-rc1/").

I have been running very close to 5.9-rc1 all day.

We have a running thread during each mainline kernel release cycle.

Previous cycle threads: [5.8]("https://ubuntuforums.org/showthread.php?t=2445465"), [5.7]("https://ubuntuforums.org/showthread.php?t=2440607"), [5.6]("https://ubuntuforums.org/showthread.php?t=2436608"), [5.5]("https://ubuntuforums.org/showthread.php?t=2432815"), [5.4]("https://ubuntuforums.org/showthread.php?t=2428734"), [5.3]("https://ubuntuforums.org/showthread.php?t=2423441"), [5.2]("https://ubuntuforums.org/showthread.php?t=2419363"), [5.1]("https://ubuntuforums.org/showthread.php?t=2414938"), [5.0]("https://ubuntuforums.org/showthread.php?t=2409811"), [4.20]("https://ubuntuforums.org/showthread.php?t=2405365"), 4.19 ?, [4.18]("https://ubuntuforums.org/showthread.php?t=2394500"), [4.17]("https://ubuntuforums.org/showthread.php?t=2389561"), [4.16]("https://ubuntuforums.org/showthread.php?t=2384781"), [4.15]("https://ubuntuforums.org/showthread.php?t=2378956"), [4.14]("https://ubuntuforums.org/showthread.php?t=2371638").

I can only comment on the stuff I work with and know about: The intel_pstate driver is introducing "passive mode with HWP enabled". This changes the default behavior of the grub command line option "intel_pstate=passive", as that used to imply to disable HWP. Now it doesn't. So if you want to run passive without HWP, you have to specify both.

Also, they are starting to tighten MSR (Machine Specific Register) access. So you need to specify that now also, or change it afterwards.

So, an example grub command line option:

```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 consoleblank=450 [COLOR="#FF0000"]intel_pstate=passive intel_pstate=no_hwp msr.allow_writes=on[/COLOR] cpuidle_sysfs_switch cpuidle.governor=teo"
```
Actually, I think the idle governor switch enable isn't needed anymore. I'll check and edit this later (test in progress at the moment).

After boot MSR write access control is via "/sys/module/msr/parameters/allow_writes", [on/off/default].

EDIT: Ya, the idle governor switch enable command line thing isn't needed anymore and since 5.8-rc1:

```
b52e93e4e86c cpuidle: Make cpuidle governor switchable to be the default behaviour
$ git tag --contains b52e93e4e86c
v5.8
v5.8-rc1
v5.8-rc2
v5.8-rc3
v5.8-rc4
v5.8-rc5
v5.8-rc6
v5.8-rc7
v5.9-rc1

```

---

### Post by corradoventu on 2020-08-20
canidate or candidate?

---

### Post by zika on 2020-08-20
> **corradoventu said:**
> canidate or candidate?What is the meaning of word: **canidate**? I can not find it, eve though I've tried hard. To see where is possible missunderstanding... ;)

---

### Post by dino99 on 2020-08-20
Simply pointing to the missing 'd' wile typing , aka typo :P

---

### Post by Doug S on 2020-08-20
> **corradoventu said:**
> canidate or candidate?Yes, typo. It should be candidate. I can not figure out how to edit the title.

---

### Post by sudodus on 2020-08-20
> **Doug S said:**
> Yes, typo. It should be candidate. I can not figure out how to edit the title.

Edit post #1, select 'Advanced', and there is a box, where you can edit the title.

By the way, is there something in particular, that you think is good or bad with this new kernel?

---

### Post by Doug S on 2020-08-20
> **sudodus said:**
> Edit post #1, select 'Advanced', and there is a box, where you can edit the title.Oh, thanks. Yes, I forgot to go to "advanced".

> **sudodus said:**
> By the way, is there something in particular, that you think is good or bad with this new kernel?Oh Boy, I don't know how much to get into it. I have been having a spat with Intel (at least the members of the linux power management group) for many months now. HWP (HardWare Pstate) control does not work properly and can result in overruns for busy periodic workflows. For the new "passive mode with HWP enabled", pretty much all of my tests, so far, suggest that it uses more power, sometimes a lot more, when compared to passive with HWP disabled or the acpi-cpufreq driver with the same governor. I could go on and on. There are a great many e-mails on the linux-pm list about it. [This]("https://marc.info/?l=linux-pm&m=159769839401767&w=2") is one reference from a couple of days ago. To be fair, we should let this play out before venting too much.

An obvious question is why don't I just use the acpi-cpufreq driver and move on? Because the "tools/power/x86/intel_pstate_tracer/intel_pstate_tracer.py" is a very good system debugging tool (I wrote most of it) and I would like to be able to use it.

Beyond the intel_pstate driver and idle stuff, I don't really follow other kernel changes.

---

### Post by sudodus on 2020-08-20
Thanks Doug S :-)

---

### Post by kevdog on 2020-08-22
What does HWP actually target?  Why would I want to make these changes or stay with the defaults?  I understand your workaround which is pretty straightforward but just an in general question of why I should care.

---

### Post by Doug S on 2020-08-22
> **kevdog said:**
> What does HWP actually target?Within the intel_pstate CPU frequency scaling driver, and for new enough processors (>= 6th gen (A.K.A Skylake)), HWP (HardWare Pstate) control offloads the actual work into the processor itself.

> **kevdog said:**
> Why would I want to make these changes or stay with the defaults?For some time now, the intel_pstate driver has had a mode called "passive", a.k.a. intel_cpufreq, basically implementing similar functionality and governors as the acpi-cpufreq CPU frequency scaling driver, without the limitations of just a few frequencies. Until this kernel 5.9-rc1, setting intel_pstate=passive on the command line also implied HWP, if the processor had it, would be disabled. Now it doesn't. My OP comments were an attempt to make users aware of this change.

Now, until a few months ago, I never owned an Intel processor with HWP (I had a i7-2600k on my test server). I was rather surprised to discover that it doesn't actually work properly. It seems to get confused with periodic workflow, thinking the system is idle and fully spinning down. Rather than idle exit latencys on the order of 10's of microseconds, they become 10's of milliseconds (when one includes full frequency spin up time), causing overruns in the workflow. This is a timing window type event and rather low probability, Anyway, for me that is why I run always with intel_pstate=passive. The new passive with HWP is relatively untested, and users might be surprised to find they are running it instead of the "passive" they are used to.

> **kevdog said:**
>  I understand your workaround which is pretty straightforward but just an in general question of why I should care.In reality, I think most people either run the defaults, which would be intel_pstate active mode with HWP if they have it or no HWP if they don't, or intel_pstate=disable, which would then be acpi_cpufreq. I think most, including Intel, don't care.

In terms of the road map for the kernel, a lot of effort is being put into the schedutil frequency scaling governor and it will be the preferred governor in the future. Some of this stuff is a stepping stone in that direction.

---

### Post by Doug S on 2020-09-07
Kernel 5.9-rc4 is [available]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.9-rc4/"). I have only been running it for a short time, so far.

---

### Post by Cavsfan on 2020-09-11
> **Doug S said:**
> Kernel 5.9-rc4 is [available]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.9-rc4/"). I have only been running it for a short time, so far.

Just installed rc4 and the resolution with my Nvidia card is too small about 640x480.
```
$ uname -a
Linux Groovy 5.9.0-050900rc4-generic #202009070130 SMP Mon Sep 7 01:35:52 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

So, back on
```
$ uname -r
5.8.0-18-generic

```

Perhaps the next rc version...

---

### Post by P-I H on 2020-09-12
rc4 works fine on my computer. Installed rc4 8/9 and made update since. Today dash to panel stooped working. Used the script to install the development version on this website
 [https://github.com/home-sweet-gnome/dash-to-panel/wiki/Installation](https://github.com/home-sweet-gnome/dash-to-panel/wiki/Installation)

```
p-i@pi-ASUS-B450-F:~$ screenfetch
                          ./+o+-       p-i@pi-ASUS-B450-F
                  yyyyy- -yyyyyy+      OS: Ubuntu 20.10 groovy
               ://+//////-yyyyyyo      Kernel: x86_64 Linux 5.9.0-050900rc4-generic
           .++ .:/++++++/-.+sss/`      Uptime: 23m
         .:++o:  /++++++++/:--:/-      Packages: 1814
        o:+o+:++.`..```.-/oo+++++/     Shell: bash 5.0.17
       .:+o:+o/.          `+sssoo+/    Resolution: 2560x1440
  .++/+:+oo+o:`             /sssooo.   DE: GNOME 3.37.90
 /+++//+:`oo+o               /::--:.   WM: Mutter
 \+/+o+++`o++o               ++////.   WM Theme: Adwaita
  .++.o+++oo+:`             /dddhhh.   GTK Theme: Yaru-light [GTK2/3]
       .+.o+oo:.          `oddhhhh+    Icon Theme: Yaru
        \+.++o+o``-````.:ohdhhhhh+     Font: Ubuntu 11
         `:o+++ `ohhhhhhhhyo++os:      Disk: 5,5T / 9,3T (62%)
           .o:`.syhhhhhhh/.oo++o`      CPU: AMD Ryzen 7 1700 Eight-Core @ 16x 3,75GHz
               /osyyyyyyo++ooo+++/     GPU: AMD Radeon RX 5700 (NAVI10, DRM 3.39.0, 5.9.0-050900rc4-generic, LLVM 10.0.1)
                   ````` +oo+++o\:     RAM: 1874MiB / 15934MiB
                          `oo++.      
p-i@pi-ASUS-B450-F:~$
```

---

### Post by kevdog on 2020-09-12
@DougS

That was a really nice reply. Thanks for taking the time to explain all of that stuff.

---

### Post by jagsdesai on 2020-09-28
I couldn't delete this post, so those who can... go ahead and delete this post.

---

### Post by slickymaster on 2020-09-29
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by fooman on 2020-10-06
Was having some trouble getting the 5.9 kernel installed with my Nvidia GTX970 card.  Was using the Nvidia 450 driver and just today noticed there was a 455 driver available,  so installed the newer driver and then tried the 5.9 kernel again ... This time it installed with no errors and is running great!

---

### Post by fooman on 2020-10-12
5.9 is out:

```
$ uname -a
Linux jackel-GA-990FXA-UD5 5.9.0-050900-generic #202010112230 SMP Sun Oct 11 22:34:01 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by IanW on 2020-10-12
> **fooman said:**
> 5.9 is out:

```
$ uname -a
Linux jackel-GA-990FXA-UD5 5.9.0-050900-generic #202010112230 SMP Sun Oct 11 22:34:01 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

Yes. Pity Groovy's "Kernel Freeze" was _last_ Thursday, meaning it won't ship with 5.9 by default.

---

