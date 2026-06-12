---
title: "XEN and cpufreq freezes on AMD X2 64 during boot (and how to solve)"
date: 2008-06-05
forum: Virtualisation
---

### Post by birne1970 on 2008-06-05
Hi there, 

I tried to install XEN from the repositories on Ubuntu 8.04 LTS 64 Bit Server on a AMD X2 64 Bit System supplied by Hetzner, a large (and great) root server provider in germany.

Unfortunately it didn't work from scratch but it seems to be working now.

During the reboot after installing ubuntu-xen-server package, I got a scary long error message and the boot process froze:

```
Jun  5 16:11:38 herby kernel: [   65.724552] powernow-k8: fid trans failed, fid 0xa, curr 0x0
Jun  5 16:11:38 herby kernel: [   65.724569] Unable to handle kernel paging request at ffff8808f1551ff8 RIP:
Jun  5 16:11:38 herby kernel: [   65.724637]  [<ffffffff88465080>] :cpufreq_stats:cpufreq_stats_update+0x40/0x70
Jun  5 16:11:38 herby kernel: [   65.724833] PGD 23f3067 PUD 0
Jun  5 16:11:38 herby kernel: [   65.725011] Oops: 0002 [1] SMP
Jun  5 16:11:38 herby kernel: [   65.725187] CPU 0
Jun  5 16:11:38 herby kernel: [   65.725307] Modules linked in: cpufreq_stats cpufreq_powersave cpufreq_userspace cpufreq_conservative cpufreq_ondemand bridge parport_pc lp parport loop ipv6 snd_hda_intel s
nd_pcm snd_timer snd_page_alloc snd_hwdep snd soundcore 8250_pnp 8250 k8temp pcspkr i2c_piix4 button serial_core i2c_core evdev shpchp pci_hotplug pata_acpi pata_atiixp sg ata_generic ehci_hcd ohci_hcd sd_m
od usbcore ssb r8169 raid10 raid456 async_xor async_memcpy async_tx xor multipath linear dm_mirror dm_snapshot dm_mod thermal fan powernow_k8 freq_table processor raid1 raid0 md_mod atiixp ahci sata_nv sata
_sil sata_via libata via82cxxx ide_core 3w_9xxx 3w_xxxx scsi_mod xfs ext3 jbd ext2 mbcache reiserfs
Jun  5 16:11:38 herby kernel: [   65.729768] Pid: 5037, comm: modprobe Not tainted 2.6.24-18-xen #1
Jun  5 16:11:38 herby kernel: [   65.729831] RIP: e030:[<ffffffff88465080>]  [<ffffffff88465080>] :cpufreq_stats:cpufreq_stats_update+0x40/0x70
Jun  5 16:11:38 herby kernel: [   65.729960] RSP: e02b:ffff8800ef0adb78  EFLAGS: 00010246
Jun  5 16:11:38 herby kernel: [   65.730023] RAX: 0000000000000000 RBX: 0000000000000000 RCX: ffff8800f1552000
Jun  5 16:11:38 herby kernel: [   65.730088] RDX: 00000000ffffffff RSI: ffff8800ef05b200 RDI: ffffffff88467080
Jun  5 16:11:38 herby kernel: [   65.730152] RBP: 00000000ffff1863 R08: 0000000000000008 R09: 0000000000000000
Jun  5 16:11:38 herby kernel: [   65.730216] R10: ffff880001c5d700 R11: ffffffff80217e10 R12: 00000000ffffffff
Jun  5 16:11:38 herby kernel: [   65.730280] R13: 00000000ffffffff R14: 0000000000000001 R15: 0000000000000000
Jun  5 16:11:38 herby kernel: [   65.730345] FS:  00007fd4565396e0(0000) GS:ffffffff805c6000(0000) knlGS:0000000000000000
Jun  5 16:11:38 herby kernel: [   65.730413] CS:  e033 DS: 0000 ES: 0000
Jun  5 16:11:38 herby kernel: [   65.730476] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun  5 16:11:38 herby kernel: [   65.730541] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun  5 16:11:38 herby kernel: [   65.730605] Process modprobe (pid: 5037, threadinfo ffff8800ef0ac000, task ffff8800ef043800)
Jun  5 16:11:38 herby kernel: [   65.730674] Stack:  0000000000000000 ffff8800ef0adc68 ffff8800ef05b200 ffffffff88465122
Jun  5 16:11:38 herby kernel: [   65.731027]  ffff8800ef043800 0000000000000000 00000000fffffffe 0000000000000000
Jun  5 16:11:38 herby kernel: [   65.731322]  ffff8800ef0adc68 ffffffff80474561 ffffffff806d0ea0 ffff8800ef0adc68
Jun  5 16:11:38 herby kernel: [   65.731557] Call Trace:
Jun  5 16:11:38 herby kernel: [   65.731684]  [<ffffffff88465122>] :cpufreq_stats:cpufreq_stat_notifier_trans+0x72/0xc0
Jun  5 16:11:38 herby kernel: [   65.731758]  [notifier_call_chain+0x31/0x60] notifier_call_chain+0x31/0x60
Jun  5 16:11:38 herby kernel: [   65.731826]  [__srcu_notifier_call_chain+0x5a/0x90] __srcu_notifier_call_chain+0x5a/0x90
Jun  5 16:11:38 herby kernel: [   65.731893]  [powernow_k8:cpufreq_notify_transition+0x8e/0x1910] cpufreq_notify_transition+0x8e/0xc0
Jun  5 16:11:38 herby kernel: [   65.731961]  [powernow_k8:powernowk8_target+0x2bd/0x690] :powernow_k8:powernowk8_target+0x2bd/0x690
Jun  5 16:11:38 herby kernel: [   65.732030]  [cpufreq_governor_performance+0x22/0x30] cpufreq_governor_performance+0x22/0x30
Jun  5 16:11:38 herby kernel: [   65.732095]  [__cpufreq_governor+0x40/0xf0] __cpufreq_governor+0x40/0xf0
Jun  5 16:11:38 herby kernel: [   65.732159]  [__cpufreq_set_policy+0x139/0x180] __cpufreq_set_policy+0x139/0x180
Jun  5 16:11:38 herby kernel: [   65.732225]  [processor:cpufreq_update_policy+0xc0/0xd10] cpufreq_update_policy+0xc0/0xf0
Jun  5 16:11:38 herby kernel: [   65.732292]  [handle_update+0x0/0x10] handle_update+0x0/0x10
Jun  5 16:11:38 herby kernel: [   65.732362]  [parport_pc:parport_parse_param+0x87/0xb0] :cpufreq_stats:cpufreq_stats_init+0x87/0xa5
Jun  5 16:11:38 herby kernel: [   65.732428]  [sys_init_module+0x18e/0x1a90] sys_init_module+0x18e/0x1a90
Jun  5 16:11:38 herby kernel: [   65.732994]  [<ffffffff8029a1d0>] __kmalloc+0x0/0x160
Jun  5 16:11:38 herby kernel: [   65.733062]  [system_call+0x68/0x6d] system_call+0x68/0x6d
Jun  5 16:11:38 herby kernel: [   65.733127]  [system_call+0x0/0x6d] system_call+0x0/0x6d
Jun  5 16:11:38 herby kernel: [   65.733193]
Jun  5 16:11:38 herby kernel: [   65.733254]
Jun  5 16:11:38 herby kernel: [   65.733255] Code: 48 01 04 d1 48 89 6e 08 c7 05 ee 1f 00 00 01 00 00 00 48 8b
Jun  5 16:11:38 herby kernel: [   65.734631] RIP  [<ffffffff88465080>] :cpufreq_stats:cpufreq_stats_update+0x40/0x70
Jun  5 16:11:38 herby kernel: [   65.734767]  RSP <ffff8800ef0adb78>
Jun  5 16:11:38 herby kernel: [   65.734838] CR2: ffff8808f1551ff8
Jun  5 16:11:38 herby kernel: [   65.734908] ---[ end trace 2d435378f215cb0a ]---

```

First I tried the all famous acpi=off kernel parameter wich worked but left me without any ACPI support. Then I disabled only loading of cpufreq by

```
mv /etc/init.d/loadcpufreq /etc/init.d/loadcpufreq.backup
```

and now I can have XEN and ACPI (yet not cpu frequence throtteling).

It seems to me that [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/225732]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/225732") describes the same problem.

Is there any other way to fix this problem?

Will I run in trouble with my solution?

Thanks in advance,

   birne

---

### Post by C38a7r1zvl on 2008-06-09
I am having the exact same problem. Apparently - as of now - there is no solution to this as frequency scaling has deliberately been omitted from incluson in Xen kernels. I'd enjoy being proven wrong though.. :)

---

### Post by zxcvbs on 2008-06-12
Same error, here. With ArchLinux. And an Amd 64 X2 4000, compilling from 2.6.8.18 xen source.

How do you dump the kernel booting without a serial connection to another pc.
Greetings.

---

### Post by detlef1959 on 2008-06-15
Hi birne1970, how do you know the console output on crashed hetzner server?
Kind regards
detlef1959

---

