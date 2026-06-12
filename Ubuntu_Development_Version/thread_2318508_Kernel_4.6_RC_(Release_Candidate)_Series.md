---
title: "Kernel 4.6 RC (Release Candidate) Series"
date: 2016-03-26
forum: Ubuntu Development Version
---

### Post by Doug S on 2016-03-26
Starting our usual Release Candidate (rc) series thread for Kernel 4.6.

Kernel 4.6-rc1 is available at [kernel.org]("https://www.kernel.org/") and I assume we can expect it shortly on the [Ubuntu Kernel PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D").

EDIT: Running 4.6-rc1 now, but haven't done much with it so far.

---

### Post by tokyobadger on 2016-03-27
Adds an average of 8 seconds to boot over 4.5. Not working with nvidia proprietary (yet) here. YMMV

---

### Post by zika on 2016-03-27
1. For a week (999 and now rc1) now:```
Oops: 0000 [#1] SMP[   24.989637] Modules linked in: snd_usb_audio(+) snd_usbmidi_lib snd_hwdep media snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer snd soundcore input_leds serio_raw i2c_piix4 shpchp floppy(+) k10temp 8250_fintek mac_hid it87 hwmon_vid
amd64_edac_mod edac_mce_amd edac_core autofs4 hid_generic usbhid hid amdkfd amd_iommu_v2 radeon i2c_algo_bit ttm drm_kms_helper r8169 mii syscopyarea sysfillrect sysimgblt fb_sys_fops ahci drm libahci wmi fjes
[   24.989919] CPU: 1 PID: 293 Comm: systemd-udevd Not tainted 4.6.0-040600rc1-generic #201603261930
[   24.989962] Hardware name: Gigabyte Technology Co., Ltd. GA-870A-UD3/GA-870A-UD3, BIOS F5 08/01/2011
[   24.990006] task: ffff8801f2d89a00 ti: ffff8801f28e4000 task.ti: ffff8801f28e4000
[   24.990042] RIP: 0010:[<ffffffffc03eba4a>]  [<ffffffffc03eba4a>] usb_audio_probe+0x2ca/0x9a0 [snd_usb_audio]
[   24.990098] RSP: 0018:ffff8801f28e7a80  EFLAGS: 00010246
[   24.990124] RAX: 0000000000000000 RBX: 0000000000000000 RCX: 0000000000000000
[   24.990159] RDX: ffff8801f31c8580 RSI: 0000000000000000 RDI: ffff8800cf9047c0
[   24.990193] RBP: ffff8801f28e7af8 R08: ffff8801f2be3f40 R09: ffffffff813f03ec
[   24.990227] R10: ffffea00033d6800 R11: ffff8800cf86ae72 R12: ffff8800ca91cc00
[   24.990262] R13: 0000000000000002 R14: ffff8800ca91cc54 R15: ffff8800cf85de09
[   24.990297] FS:  00007f0f963fd8c0(0000) GS:ffff8801ffc40000(0000) knlGS:0000000000000000
[   24.990336] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   24.990364] CR2: 0000000000000014 CR3: 00000001f29a6000 CR4: 00000000000006e0
[   24.990399] Stack:
[   24.990410]  ffff8801f2db3f48 0000000000000000 ffff8800cf598c00 ffff8801f2db3f48
[   24.990456]  0000000000000246 0000000000000246 ffff8801f6161000 3864304253551be6
[   24.990498]  0000393133303a63 00000000c613f146 ffff8800cf580898 ffff8800cf580800
[   24.990540] Call Trace:
[   24.990558]  [<ffffffff816227dd>] usb_probe_interface+0x1bd/0x300
[   24.990589]  [<ffffffff8155618c>] driver_probe_device+0x22c/0x440
[   24.990620]  [<ffffffff81556471>] __driver_attach+0xd1/0xf0
[   24.990648]  [<ffffffff815563a0>] ? driver_probe_device+0x440/0x440
[   24.990680]  [<ffffffff81553c2c>] bus_for_each_dev+0x6c/0xc0
[   24.990709]  [<ffffffff8155586e>] driver_attach+0x1e/0x20
[   24.990736]  [<ffffffff815552fb>] bus_add_driver+0x1eb/0x280
[   24.990765]  [<ffffffff81556df0>] driver_register+0x60/0xe0
[   24.990794]  [<ffffffff81621124>] usb_register_driver+0x84/0x140
[   24.990824]  [<ffffffffc0418000>] ? 0xffffffffc0418000
[   24.990856]  [<ffffffffc041801e>] usb_audio_driver_init+0x1e/0x1000 [snd_usb_audio]
[   24.990894]  [<ffffffff81002123>] do_one_initcall+0xb3/0x200
[   24.990923]  [<ffffffff811dbc71>] ? __vunmap+0x81/0xd0
[   24.990950]  [<ffffffff811fa256>] ? kmem_cache_alloc_trace+0x176/0x1e0
[   24.990982]  [<ffffffff811fb4b1>] ? kfree+0x151/0x160
[   24.991009]  [<ffffffff81192b86>] do_init_module+0x5f/0x1df
[   24.991038]  [<ffffffff8110dcd8>] load_module+0x16a8/0x1c40
[   24.991066]  [<ffffffff8110a390>] ? __symbol_put+0x60/0x60
[   24.991096]  [<ffffffff81399e6d>] ? ima_post_read_file+0x7d/0xa0
[   24.991126]  [<ffffffff8110e4e6>] SYSC_finit_module+0xe6/0x120
[   24.991156]  [<ffffffff8110e53e>] SyS_finit_module+0xe/0x10
[   24.991186]  [<ffffffff81839ef6>] entry_SYSCALL_64_fastpath+0x1e/0xa8
[   24.991217] Code: 02 00 8b 75 ac 4c 89 e7 e8 c4 75 00 00 85 c0 89 c1 0f 88 ae 00 00 00 49 8b 7c 24 10 e8 10 ef f6 ff 85 c0 89 c1 0f 88 9a 00 00 00 <80> 7b 14 00 0f 85 4c 04 00 00 49 63 04 24 4c 89 24 c5 c0 ca 40
[   24.991415] RIP  [<ffffffffc03eba4a>] usb_audio_probe+0x2ca/0x9a0 [snd_usb_audio]
[   24.991459]  RSP <ffff8801f28e7a80>
[   24.991477] CR2: 0000000000000014
[   24.991496] ---[ end trace 59392501b5d20ddb ]---

```2. super long wait for net
3. reboot waits until REISUB... ;)
Update&#8321;: ad 2.: if I replace two snd-usb modules from 4.6 with 4.5 ones, that do work nicely, I do not get sound, alsa list is empty, do not get that trace, do not get super long wait for the net so it seems that there is only one bug here: alsa-snd-usb... ;)
Update&#8322;: ad 2.: went back to card 0: [HDA ATI SB] [ALC892 Digital] ... ;) That do work nice...
Update&#8323;: With 2. not solved but taken from the table 1.&3. are OK...
Update&#8324;: Bug [reported]("https://bugzilla.kernel.org/show_bug.cgi?id=115591"), connected to already existing bug (mea culpa) and mail sent to proper place upstream. It seems that [fix]("https://bugzilla.kernel.org/show_bug.cgi?id=115301#c4") is on its way... ;)

---

### Post by Doug S on 2016-03-27
> **tokyobadger said:**
> Adds an average of 8 seconds to boot over 4.5. Not working with nvidia proprietary (yet) here. YMMVOn my Ubuntu server 16.04 I get 1.73 additional seconds boot time compared to kernel 4.4.0-15-generic.

Not observing zika type problems.

---

### Post by MikeMecanic on 2016-03-30
It is the second time I'm removing 4.6-rc1 (Kylin and Ubuntu).  It does not restart (freezing weird slash screen) and boots extremely slowly, up to 40 seconds.  Reducing the LVM boot partition by half (255Mb) gives 20 seconds instead of 10.  Not to mention DE unstable issues that started in 4.5 stable.     Will try it a third time  by the end of the week.

---

### Post by zika on 2016-03-30
> **Doug S said:**
> Not observing zika type problems.Do You have (any) USB audio device or USB>S/PDIF converter? If not (as I wrote above, once that kind of device is removed all is OK) then You should not see such error(s), simple as that... If You do have such a device connected and You do not observe any error(s) I would like to know which device it is to try to find source of trouble here. Thank You in advance.
---
[COLOR=#000000][FONT=Ubuntu]Ignota nulla curatio morbi.[/FONT][/COLOR]

---

### Post by Doug S on 2016-03-30
> **zika said:**
> Do You have (any) USB audio device or USB>S/PDIF converter? If not (as I wrote above, once that kind of device is removed all is OK) then You should not see such error(s), simple as that... If You do have such a device connected and You do not observe any error(s) I would like to know which device it is to try to find source of trouble here. Thank You in advance.
---
[COLOR=#000000][FONT=Ubuntu]Ignota nulla curatio morbi.[/FONT][/COLOR]No, the computer is a server, and only has a keyboard attached. It is my main test server, it was 14.04 based, but I recently did a fresh install of 16.04 server edition.

By the way, has anyone that is using the intel_pstate driver noticed any regression? In 4.6-rc1 there were significant changes in how the CPU frequency scaling drivers (both acpi-cpufreq and intel_pstate) functions are called. There is a report of a regression on an i5-4200M, where the CPU frequency is holding at a high level when the system is idle.

---

### Post by QDR06VV9 on 2016-03-30
> **Doug S said:**
> 
By the way, has anyone that is using the intel_pstate driver noticed any regression? In 4.6-rc1 there were significant changes in how the CPU frequency scaling drivers (both acpi-cpufreq and intel_pstate) functions are called. There is a report of a regression on an i5-4200M, where the CPU frequency is holding at a high level when the system is idle.
Doug I have have only been running this since this morning but I really don't notice any diff's yet
```
grep -i pstate /boot/config-$(uname -r)
CONFIG_X86_INTEL_PSTATE=y

```
```
/sys/kernel/debug/tracing# cat available_filter_functions | grep -i pstate
fpstate_init
fpu__activate_fpstate_read
fpu__activate_fpstate_write
fpu__current_fpstate_write_begin
fpu__current_fpstate_write_end
copy_fpstate_to_sigframe
fpstate_sanitize_xstate
atom_get_min_pstate
atom_get_max_pstate
atom_get_turbo_pstate
core_get_min_pstate
core_get_max_pstate_physical
intel_pstate_get
intel_pstate_verify_policy
intel_pstate_update_util
core_get_max_pstate
knl_get_turbo_pstate
core_get_turbo_pstate
show_num_pstates
intel_pstate_hwp_set
intel_pstate_set_policy
intel_pstate_set_min_pstate
intel_pstate_stop_cpu
intel_pstate_cpu_init

```
Specs
```
System:    Host: me-Lenovo-B570 Kernel: 4.6.0-040600rc1-lowlatency x86_64 (64 bit)
           Desktop: MATE 1.12.1  Distro: Ubuntu 16.04 xenial
Machine:   System: LENOVO (portable) product: 1068AJU v: Lenovo B570
           Mobo: LENOVO model: Emerald Lake v: FAB1
           Bios: LENOVO v: 44CN43WW date: 10/27/2011
CPU:       Dual core Intel Pentium B950 (-MCP-) speed/max: 799/2100 MHz
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
           Display Server: X.Org 1.18.1 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile
           GLX Version: 3.0 Mesa 11.1.2
Network:   Card-1: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express)
           driver: ath9k
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 160.0GB (37.4% used)
Info:      Processes: 181 Uptime: 2 min Memory: 341.9/3865.4MB
           Client: Shell (bash) inxi: 2.2.35 


```

But on my AMD Tower it is a mess for me at least.

---

### Post by MikeMecanic on 2016-03-31
On the arrival of Kernel 4.5 stable, the LVM boot partition size was double and is now 512MB.  Since then (Kylin-Gnome-Ubuntu) I was not able to run the latest Kernel (multiple issues) when using LVM encrypted.  

But today I made a fresh install and set partitions manually and things are now back to normal.  The culprit seems to be LVM encrypted that needs attention?  

```
ux@b2:~$ dpkg --list | grep linux-image   
ii [COLOR=#ff0000] linux-image[/COLOR]-4.4.0-16-generic      4.4.0-16.32                                                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii [COLOR=#ff0000] linux-image[/COLOR]-4.6.0-040600rc1-generic   4.6.0-040600rc1.201603261930                             amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP
ii [COLOR=#ff0000] linux-image[/COLOR]-extra-4.4.0-16-generic    4.4.0-16.32                                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii [COLOR=#ff0000] linux-image-[/COLOR]generic                   4.4.0.16.17                                                                  amd64        Generic Linux kernel image
```
  
All the best,

---

### Post by MikeMecanic on 2016-04-04
[Kernel 4.6-rc2]("https://lkml.org/lkml/2016/4/3/148")
  
In one word: Stable 
  
There was a patch for GTX-900 series last week in rc1:[Nouveau]("http://www.phoronix.com/scan.php?page=article&item=linux-46-features&num=1")
 

 ```
Linux u 4.6.0-040600rc2-generic #201604031130 SMP Sun Apr 3 15:32:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by engineer on 2016-04-05
How did you install the 4.6 kernel?

I'm running a stable xenial beta at the moment. I then tried to add the kernel-ppa, which does not seem to contain kernel for recent versions of ubuntu. I finally found .deb files at [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"), which I did try to install. There are three files (linux-image, linux-headers*all and linux-headers*generic), which I installed. First I got some errors regarding dkms and the i915 module, but after rebooting with the 4.4 kernel and uninstalling, a second install of these .debs went without error.

Nevertheless, I still could not get the 4.6rc2 kernel to boot. It's displaying the purple screen with "Ubuntu" and the five dots on it. Sometimes it hangs on the first, sometimes on the third dot. I'm trying to run it on a Lenovo Thinkpad Carbon 2nd generation (the one with the adaptive keyboard, with a Haswell i7 CPU).

I got these errors in my /var/log/kern.log

```
Apr  5 09:39:03 -laptop-x kernel: [   19.771572] acpi_call: module verification failed: signature and/or required key missing - tainting kernel
Apr  5 09:39:03 -laptop-x kernel: [   19.775002] thinkpad_ec: thinkpad_ec_request_row: arg0 rejected: (0x01:0x00)->0x00
Apr  5 09:39:03 -laptop-x kernel: [   19.775005] thinkpad_ec: thinkpad_ec_read_row: failed requesting row: (0x01:0x00)->0xfffffffb
Apr  5 09:39:03 -laptop-x kernel: [   19.775007] thinkpad_ec: initial ec test failed
Apr  5 09:39:03 -laptop-x kernel: [   19.830052] thinkpad_ec: thinkpad_ec_request_row: arg0 rejected: (0x01:0x00)->0x00
Apr  5 09:39:03 -laptop-x kernel: [   19.830055] thinkpad_ec: thinkpad_ec_read_row: failed requesting row: (0x01:0x00)->0xfffffffb
Apr  5 09:39:03 -laptop-x kernel: [   19.830057] thinkpad_ec: initial ec test failed
```

```
Apr  5 09:43:54 -laptop-x kernel: [  310.352253] mce: [Hardware Error]: Machine check events logged
Apr  5 09:43:54 -laptop-x kernel: [  310.352257] CPU1: Package temperature above threshold, cpu clock throttled (total events = 1624)
Apr  5 09:43:54 -laptop-x kernel: [  310.352259] mce: [Hardware Error]: Machine check events logged
Apr  5 09:43:54 -laptop-x kernel: [  310.359268] CPU0: Core temperature/speed normal
Apr  5 09:43:54 -laptop-x kernel: [  310.359269] CPU1: Core temperature/speed normal
```

```
Apr  5 13:17:35 -laptop-x kernel: [13131.503684] thinkpad_ec: thinkpad_ec_request_row: arg0 rejected: (0x01:0x00)->0x00
Apr  5 13:17:35 -laptop-x kernel: [13131.503686] thinkpad_ec: thinkpad_ec_read_row: failed requesting row: (0x01:0x00)->0xfffffffb
Apr  5 13:17:35 -laptop-x kernel: [13131.503688] thinkpad_ec: initial ec test failed
```

Seems to be related to ACPI. Did anybody of you get it to run on a recent Thinkpad? Any ideas, what to change or will I have to wait for another release candidate or the final version?

---

### Post by MikeMecanic on 2016-04-05
Get the Ubuntu PPA there instead:   [PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D")
  
There are many ways to install the latest Kernel.  The easiest one would be with Gnome Software (open with Software installer) but you must respect the sequence:  

 Order of download (x64) and installation in Gnome Software (good for any Kernel release):
 
 1-    linux-headers-..._all.deb                  
 2-    linux-headers-...amd64.deb
 3-    linux-image-...amd64.deb
 if shown
 4-    linux-image-extra-...amd64.deb 
                      
 Good luck,

---

### Post by izznogooood on 2016-04-05
Boot time seems ok in rc2, have "looking for btrfs" blinking for some seconds and "_" even though i have "quiet splash"

---

### Post by engineer on 2016-04-06
Still no success:

I tried to install the header packages first (the linux-image package is not yet installed, but also nothing complained about missing dependencies):

The headers-all package installed fine, but I got the following errors, when installing the amd64 specific package:

```
dpkg -i linux-headers-4.6.0-040600rc2-generic_4.6.0-040600rc2.201604031130_amd64.deb 
(Reading database ... 421270 files and directories currently installed.)
Preparing to unpack linux-headers-4.6.0-040600rc2-generic_4.6.0-040600rc2.201604031130_amd64.deb ...
Unpacking linux-headers-4.6.0-040600rc2-generic (4.6.0-040600rc2.201604031130) over (4.6.0-040600rc2.201604031130) ...
Setting up linux-headers-4.6.0-040600rc2-generic (4.6.0-040600rc2.201604031130) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.6.0-040600rc2-generic /boot/vmlinuz-4.6.0-040600rc2-generic
ERROR (dkms apport): kernel package linux-headers-4.6.0-040600rc2-generic is not supported
Error! Bad return status for module build on kernel: 4.6.0-040600rc2-generic (x86_64)
Consult /var/lib/dkms/tp-smapi/0.41/build/make.log for more information.
```

The content of /var/lib/dkms/tp-smapi/0.41/build/make.log:

```
DKMS make.log for tp-smapi-0.41 for kernel 4.6.0-040600rc2-generic (x86_64)
Wed Apr  6 08:20:22 CEST 2016
make: Entering directory '/usr/src/linux-headers-4.6.0-040600rc2-generic'
  LD      /var/lib/dkms/tp-smapi/0.41/build/built-in.o
  CC [M]  /var/lib/dkms/tp-smapi/0.41/build/thinkpad_ec.o
In file included from include/linux/module.h:18:0,
                 from /var/lib/dkms/tp-smapi/0.41/build/thinkpad_ec.c:33:
/var/lib/dkms/tp-smapi/0.41/build/thinkpad_ec.c: In function ‘__check_force_io’:
include/linux/moduleparam.h:344:67: error: return from incompatible pointer type [-Werror=incompatible-pointer-types]
  static inline type __always_unused *__check_##name(void) { return(p); }
                                                                   ^
include/linux/moduleparam.h:396:35: note: in expansion of macro ‘__param_check’
 #define param_check_bool(name, p) __param_check(name, p, bool)
                                   ^
include/linux/moduleparam.h:146:2: note: in expansion of macro ‘param_check_bool’
  param_check_##type(name, &(value));       \
  ^
/var/lib/dkms/tp-smapi/0.41/build/thinkpad_ec.c:100:1: note: in expansion of macro ‘module_param_named’
 module_param_named(force_io, force_io, bool, 0600);
 ^
/var/lib/dkms/tp-smapi/0.41/build/thinkpad_ec.c: In function ‘check_dmi_for_ec’:
/var/lib/dkms/tp-smapi/0.41/build/thinkpad_ec.c:469:1: warning: the frame size of 1728 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
cc1: some warnings being treated as errors
scripts/Makefile.build:297: recipe for target '/var/lib/dkms/tp-smapi/0.41/build/thinkpad_ec.o' failed
make[1]: *** [/var/lib/dkms/tp-smapi/0.41/build/thinkpad_ec.o] Error 1
Makefile:1427: recipe for target '_module_/var/lib/dkms/tp-smapi/0.41/build' failed
make: *** [_module_/var/lib/dkms/tp-smapi/0.41/build] Error 2
make: Leaving directory '/usr/src/linux-headers-4.6.0-040600rc2-generic'

```

The linux-image package then installs fine, but does not boot, as mentioned in my earlier post. I'm guessing that some system processes require the header files to correctly hook to the kernel to make system calls.

I got the very same .deb file to install without any errors, although I don't know, what I did differently.

---

### Post by Doug S on 2016-04-11
I see that -rc3 is available, but that the [Ubuntu build]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc3-wily/") failed. It built fine for me.

---

### Post by MikeMecanic on 2016-04-11
Delayed?  It&#8217;s not possible to load rc-3 because there&#8221;s only one file available.  All daily builds are also delayed, the switch is close for April 9[SUP]th[/SUP] and 10[SUP]th[/SUP].  I just hope that the menu bug is not the reason.  I don&#8217;t have that bug and I don&#8217;t remember seeing it in 2016.
 
 **There&#8217;s a bug in the network switch since last update:  Loosing the switch.**
 
 
 If I close the switch without closing the VPN switch first, I loose the network icon (_permanent: Must restart to recover the switch_).  Same apply when I re-open the computer but it is intermittent.  To be confirm on lower Kernel&#8230;

    [PHP]
Commit Log for Sat Apr  9 13:19:41 2016
   
  Upgraded the following packages:

 network-manager-openvpn (0.9.10.0-1ubuntu2) to 1.1.93-1

 network-manager-openvpn-gnome (0.9.10.0-1ubuntu2) to 1.1.93-1

 network-manager-pptp (1.0.8-2ubuntu1) to 1.1.93-1

 network-manager-pptp-gnome (1.0.8-2ubuntu1) to 1.1.93-1
   
 Commit Log for Sat Apr  9 02:48:19 2016
   
   Upgraded the following packages:

 libnm-gtk-common (1.0.10-1ubuntu1) to 1.1.93-1ubuntu1

 libnm-gtk0 (1.0.10-1ubuntu1) to 1.1.93-1ubuntu1

 network-manager-gnome (1.0.10-1ubuntu1) to 1.1.93-1ubuntu1

  
 Installed the following packages:

 libnma-common (1.1.93-1ubuntu1)

 libnma0 (1.1.93-1ubuntu1)

[/PHP]

---

### Post by izznogooood on 2016-04-11
I've been running rc-2 since it came out now and very happy with it. But there is one thing that's a bit annoying. On every boot after grub it halts for 2-3 seconds flashing "scanning for btrfs" in the upper left corner. I have "quiet splash" enabled so why is it doing that? (Yes I use btrfs)

---

### Post by MikeMecanic on 2016-04-11
> **izznogooood said:**
> (Yes I use btrfs)

Try ext4 instead.  But this is bug in rc2.  I made a little modification in the  boot sequence (Grub) because Kylin shows a very long spash screen.

  	 	 	 	   [LEFT] [COLOR=#000000][FONT=Calibri][SIZE=2]GRUB_HIDDEN_TIMEOUT=3   to 10 (your choice)

[/SIZE][/FONT][/COLOR]    	 	 	 	   [COLOR=#000000][FONT=Calibri][SIZE=2]GRUB_CMDLINE_LINUX_DEFAULT="quiet"[/SIZE][/FONT][/COLOR]
[/LEFT]

---

### Post by izznogooood on 2016-04-11
> **MikeMecanic said:**
>                       [LEFT] [COLOR=#000000][FONT=Calibri][SIZE=2]GRUB_HIDDEN_TIMEOUT=3   to 10 (your choice)
[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Calibri][SIZE=2]GRUB_CMDLINE_LINUX_DEFAULT="quiet"[/SIZE][/FONT][/COLOR]
[/LEFT]


Thanks for the tips, but my boot is still less than 10sec so it's more of a OCD thing. But its nice to know its a bug :)

---

### Post by MikeMecanic on 2016-04-11
> **izznogooood said:**
> Thanks for the tips, but my boot is still less than 10sec so it's more of a OCD thing. But its nice to know its a bug :)

  	 	 	 	   Well, I’m not quite sure it’s a rc-2 bug, but I'm sure of one thing, it’s a Kylin bug that last for a long time now.    
 
 
 Having an Intel graphic I don’t have any of your bugs, in fact I don’t have any bugs in this cycle.  If one arise, it as always been easy to fix since the beginning of the cycle.  Try Mayo clinic Web page...:)

---

### Post by izznogooood on 2016-04-11
> **MikeMecanic said:**
> Well, I’m not quite sure it’s a rc-2 bug, but I'm sure of one thing, it’s a Kylin bug

I'm on plain ubuntu.

---

### Post by MikeMecanic on 2016-04-12
Just made a fresh install and everything is normal.   
 
 
 All the best,
  

```
xx@uk:~$ uname -r
4.6.0-040600rc3-generic
```

---

### Post by engineer on 2016-04-13
Still no success here with rc3. The above mentioned bug (?) when building the tp-smapi module is still there.

Did somebody else succeed with kernel 4.6 series on a Thinkpad?

---

### Post by izznogooood on 2016-04-13
No success with rc-3, Virtualbox and Nvidia modules failed.

---

### Post by mortenc on 2016-04-13
> **engineer said:**
> Still no success here with rc3. The above mentioned bug (?) when building the tp-smapi module is still there.

Did somebody else succeed with kernel 4.6 series on a Thinkpad?

Just tested on a T450s. I just removed the tp-smapi-dkms package in favor of acpi-call-dkms (which should do the same or even better on newer thinkpads).

 Also I had to get rid of virtualbox-dkms and virtualbox-guest-dkms. I know, not a very sensible solution to get the kernel to build, but since I'm wating for every new kernel since I ran in different i915 bugs I was willing to pay this price. 

Building the kernel was successfull afterwards, but unfortunately the kernel hangs while booting, have to investigate this further.

---

### Post by Doug S on 2016-04-18
Kernel 4.6-rc4 is [available]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-rc4-wily/").
I have compiled and installed it, but not running it yet.

---

### Post by MikeMecanic on 2016-04-18
Video glitch here and there in RC2 were not present in RC3.  On Legacy mode, Unity remains stable.

                        
```
$ dpkg --list | grep linux-image

 ii [COLOR=#ff3333]** linux-image**[/COLOR]-4.6.0-040600rc4-generic        4.6.0-040600rc4.201604172330               amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP

```

---

### Post by izznogooood on 2016-04-18
Both rc-3 rc-4 fail with Nvidia kernel module (461).

---

### Post by narges2 on 2016-04-20
I am working with 4.6.0-rc2+. When I boot with this kernel, and try to re-compile the source code, I get null reference BUG for cachefiles. I can successfully compile and install with 4.4 or 4.5. 

$uname -r 
4.6.0-rc2+

$make 
... freeze ... 

$dmesg 

[  115.373875] BUG: unable to handle kernel NULL pointer dereference at 0000000000000098
[  115.374476] IP: [<ffffffffc02fca8e>] cachefiles_mark_object_inactive+0x5e/0xb0 [cachefiles]
[  115.374477] PGD 0 
[  115.375063] Oops: 0000 [#2] SMP 
[  115.376068] Modules linked in: nfsv3 rpcsec_gss_krb5 nfsv4 cachefiles 8021q garp mrp stp llc autofs4 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm nfsd auth_rpcgss nfs_acl nfs parport_pc ppdev lockd irqbypass crct10dif_pclmul ipmi_ssif dcdbas ipmi_devintf crc32_pclmul ghash_clmulni_intel aesni_intel grace aes_x86_64 lrw sunrpc gf128mul glue_helper ablk_helper cryptd joydev input_leds sb_edac mei_me edac_core mei shpchp ioatdma lpc_ich ipmi_si 8250_fintek ipmi_msghandler wmi fscache lp acpi_power_meter parport mac_hid mlx4_en mlx4_core ixgbe hid_generic tg3 usbhid dca vxlan ip6_udp_tunnel megaraid_sas hid udp_tunnel ptp fjes pps_core mdio
[  115.376072] CPU: 12 PID: 374 Comm: kworker/u289:3 Tainted: G      D   I     4.6.0-rc2+ #26
[  115.376075] Hardware name: Dell Inc. PowerEdge R730xd/0599V5, BIOS 1.0.4 08/28/2014
[  115.376084] Workqueue: fscache_object fscache_object_work_func [fscache]
[  115.376086] task: ffff881ffd9e2ac0 ti: ffff881ffd6dc000 task.ti: ffff881ffd6dc000
[  115.376093] RIP: 0010:[<ffffffffc02fca8e>]  [<ffffffffc02fca8e>] cachefiles_mark_object_inactive+0x5e/0xb0 [cachefiles]
[  115.376096] RSP: 0018:ffff881ffd6dfd88  EFLAGS: 00010246
[  115.376098] RAX: 0000000000000000 RBX: ffff883fefe06e00 RCX: 0000000000000034
[  115.376100] RDX: ffff88407ffe8ff0 RSI: ffff883fee8fc590 RDI: ffff88407ffe8fe8
[  115.376102] RBP: ffff881ffd6dfd98 R08: ffff883fef834128 R09: ffff883fefafc728
[  115.376104] R10: ffff883fef834a28 R11: ffffea007fe43fc0 R12: ffff883fee8fc480
[  115.376106] R13: ffff882010baf200 R14: ffff883fefe06e00 R15: ffff883fe68822cc
[  115.376109] FS:  0000000000000000(0000) GS:ffff88201ed80000(0000) knlGS:0000000000000000
[  115.376111] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  115.376114] CR2: 0000000000000098 CR3: 0000000001e06000 CR4: 00000000001406e0
[  115.376116] Stack:
[  115.376124]  ffff883fee8fc480 ffff883fefe06e00 ffff881ffd6dfdc0 ffffffffc02fb735
[  115.376132]  ffff883fee8fc480 ffff883fefe06e98 ffff88200f2a8180 ffff881ffd6dfdf8
[  115.376139]  ffffffffc011260d ffff883fee8fc480 000000000000006d ffff883fee8fc510
[  115.376141] Call Trace:
[  115.376146]  [<ffffffffc02fb735>] cachefiles_drop_object+0x65/0xe0 [cachefiles]
[  115.376152]  [<ffffffffc011260d>] fscache_drop_object+0xed/0x1e0 [fscache]
[  115.376158]  [<ffffffffc01123cc>] fscache_object_work_func+0x9c/0x1f0 [fscache]
[  115.376166]  [<ffffffff81096693>] process_one_work+0x153/0x400
[  115.376169]  [<ffffffff8109710e>] worker_thread+0x4e/0x4a0
[  115.376173]  [<ffffffff810970c0>] ? rescuer_thread+0x360/0x360
[  115.376177]  [<ffffffff8109c459>] kthread+0xc9/0xe0
[  115.376183]  [<ffffffff81806222>] ret_from_fork+0x22/0x40
[  115.376186]  [<ffffffff8109c390>] ? kthread_park+0x60/0x60
[  115.376208] Code: 8d bc 24 10 01 00 00 f0 41 80 a4 24 10 01 00 00 fe c6 83 20 01 00 00 00 31 f6 e8 de 1e dc c0 49 8b 84 24 f8 00 00 00 48 8b 40 30 <48> 8b 80 98 00 00 00 f0 48 01 83 30 01 00 00 b8 01 00 00 00 f0 
[  115.376211] RIP  [<ffffffffc02fca8e>] cachefiles_mark_object_inactive+0x5e/0xb0 [cachefiles]
[  115.376212]  RSP <ffff881ffd6dfd88>
[  115.376212] CR2: 0000000000000098
[  115.376214] ---[ end trace 44f6f0d103c4988f ]---

---

### Post by Doug S on 2016-04-20
Hi and welcome to Ubuntu forums,

I recall your issue from over on [ask]("http://askubuntu.com/questions/758813/kernel-4-6-rc2-crash-on-make").
It is not unusual to have issues with early rc kernels, particularly ones in between the tags (if I understand correctly, your particular kernel is somewhere between 4.6-rc2 and 4.6-rc3, resulting in -rc2+).
Can you not move up to the latest 4.6-rc4 kernel and see if that works? As I mentioned over on ask, I have not had any problems compiling the kernel while running any of 4.6-rc1 through 4.6-rc4.

---

### Post by MikeMecanic on 2016-04-21
Your not the only one experiencing problems with rc3 and even rc4.  Here&#8217;s another technique for loading [custom kernel]("http://linuxdaddy.com/").  The web site is some time one week behind schedule.  You must be precise when modifying the command lines.  Changing the rc number or removing them for the final release and adding the new date must be done properly because it won&#8217;t work (missing or wrong character).
 
 
 The PPA [date]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") is always available each Sunday night EST. Make sure you select the 64 bit version.  I would start by removing the rc2+ one at start all over again with the help of Synaptic (search for linux-image) or :

 ```
sudo apt-get purge linux-headers-4.6.0-040600rc2+ linux-headers-4.6.0-040600rc2+-generic linux-image-4.6.0-040600rc2+-generic
```[LEFT]If << rc >> still shown:  dpkg --list | grep linux-image
 Then
[/LEFT]
  ```
dpkg -l | grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg &#8211;purge
```[LEFT]                  
[/LEFT]
```
sudo apt autoremove
```
Good luck,

     	 	 	 	   EDIT:  Because of the + sign, the command line may not work.  In Synaptic, search for linux-image and mark rc2+ for complete removal.  Then in Status, search and delete the rc2+ headers in: Installed or residual conf.  Apply changes.
   [LEFT]

 


[/LEFT]

---

### Post by Doug S on 2016-04-24
Kernel 4.6-rc5 is available from [kernel.org]("https://www.kernel.org/"), but not yet on the [Ubuntu mainline PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D"), perhaps soon. I have not stolen the Ubuntu kernel configuration for quite some time, so am going to wait for the mainline PPA before I compile my own kernel with the stolen kernel configuration.

---

### Post by MikeMecanic on 2016-04-24
Calm as usual.  Rc 5 seems to be the biggest so far.
 
 
 ```
df -h | grep ^/dev/sda1

 [COLOR=#ff3333]**/dev/sda1  **[/COLOR]     231M  120M   99M  55% /boot
 dpkg --list | grep linux-image
 ii [COLOR=#ff3333]** linux-image**[/COLOR]-4.6.0-040600rc4-generic        4.6.0-040600rc4.201604172330                        amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP
 ii  [COLOR=#ff3333]**linux-image**[/COLOR]-4.6.0-040600rc5-generic        4.6.0-040600rc5.201604242031                        amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP
 dpkg --list | grep linux-image
 ii  [COLOR=#ff3333]**linux-image**[/COLOR]-4.6.0-040600rc5-generic        4.6.0-040600rc5.201604242031                        amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP
 df -h | grep ^/dev/sda1/dev/sda1   
 [COLOR=#ff3333]**/dev/sda1**[/COLOR]       231M   65M  154M  30% /boot

```

---

### Post by zika on 2016-05-08
In Canonical kernel team (unstable): linux (4.6.0-1.2) yakkety, and it is working fine... ;)

---

### Post by rrnbtter on 2016-05-14
Greeting,
Yakkety gets its own kernel in 4.6 RC7, released two days ago.
Working fine on my Intel system.
FYI

---

### Post by MikeMecanic on 2016-05-15
> **rrnbtter said:**
> Greeting,
Yakkety gets its own kernel in 4.6 RC7, released two days ago.
Working fine on my Intel system.
FYI

Works fine in Xenial also.  Here&#8217;s an amazing article on what&#8217;s next for [4.6 stable]("https://www.linux.com/news/greg-kh-update-linux-kernel-46-next-week-new-security-features").

EDIT:  That marks the end of another successful cycle.
  Keep in mind that rc7 remains first in the loading sequence.  You must enter the Grub menu to run the last Kernel.
 
 ```
 
  ~$ **dpkg --list | grep linux-image**
 ii  [COLOR=#ff3333]**linux-image**[/COLOR]-4.6.0-040600-generic             4.6.0-040600.201605151930                     amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP
 ii [COLOR=#ff3333]** linux-image**[/COLOR]-4.6.0-040600rc7-generic         4.6.0-040600rc7.201605081830                   amd64        Linux kernel image for version 4.6.0 on 64 bit x86 SMP

```

---

### Post by izznogooood on 2016-06-04
I got an update (xenial-proposed) to the nvidia driver today. 

Kernel 4.6-rc2-7 now works :)

---

### Post by IanW on 2016-06-04
WARNING! I got the "error getting socket: address family not supported by protocol" problem when attempting to boot into 4.6.1 today.

---

### Post by dino99 on 2016-06-05
4.6.0-7.8 from canonical-kernel-team ppa works fine here

---

