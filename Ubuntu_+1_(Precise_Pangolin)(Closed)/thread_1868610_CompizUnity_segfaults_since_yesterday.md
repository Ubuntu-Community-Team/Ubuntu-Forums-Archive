---
title: "Compiz/Unity segfaults since yesterday"
date: 2011-10-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-10-24
Compiz/Unity was very stable (almost no crashes at all) until yesterday updates.
Today I'm seeing segfaults every hour or so.

All I did, besides being up-to-date with official repos is update nvidia-proprietary to 290.03 (64) and install Kernel 3.1 RC9.

Is it happening to you guys too? 


```
[  707.523484] compiz[16216]: segfault at 107 ip 00007f564b1c2fdd sp 00007ffff1d06a70 error 4 in libunityshell.so[7f564b0c5000+225000]
[  707.528207] swap_free: Bad swap offset entry 18800000188000
[  707.528211] BUG: Bad page map in process compiz  pte:3100000031000000 pmd:3cff0c067
[  707.528213] addr:00007f565def7000 vm_flags:08000070 anon_vma:          (null) mapping:ffff88040f74b2f8 index:1f3
[  707.528218] vma->vm_ops->fault: filemap_fault+0x0/0x440
[  707.528221] vma->vm_file->f_op->mmap: ext4_file_mmap+0x0/0x60
[  707.528223] Pid: 16216, comm: compiz Tainted: P            3.1.0-030100-generic #201110241006
[  707.528225] Call Trace:
[  707.528230]  [<ffffffff8113582c>] print_bad_pte+0x1dc/0x250
[  707.528232]  [<ffffffff81136592>] zap_pte_range+0x1b2/0x490
[  707.528236]  [<ffffffff815fae20>] ? __schedule+0x3f0/0x7f0
[  707.528238]  [<ffffffff8113758e>] unmap_page_range+0x1be/0x300
[  707.528240]  [<ffffffff8113779a>] unmap_vmas+0xca/0x170
[  707.528242]  [<ffffffff8113cdc6>] exit_mmap+0x96/0x140
[  707.528245]  [<ffffffff81063c94>] mmput+0x64/0x140
[  707.528247]  [<ffffffff8106a53f>] exit_mm+0x12f/0x170
[  707.528250]  [<ffffffff810e031b>] ? taskstats_exit+0x17b/0x240
[  707.528252]  [<ffffffff815fd5f5>] ? _raw_spin_lock_irq+0x15/0x20
[  707.528254]  [<ffffffff8106a801>] do_exit+0x171/0x420
[  707.528256]  [<ffffffff8106ab05>] do_group_exit+0x55/0xd0
[  707.528259]  [<ffffffff8107c5a7>] get_signal_to_deliver+0x227/0x4b0
[  707.528262]  [<ffffffff8101394b>] do_signal+0x5b/0x130
[  707.528264]  [<ffffffff815fa7c3>] ? printk+0x68/0x6d
[  707.528267]  [<ffffffff8129d52b>] ? security_file_permission+0x8b/0x90
[  707.528269]  [<ffffffff81013a85>] do_notify_resume+0x65/0x90
[  707.528271]  [<ffffffff815fdb7c>] retint_signal+0x48/0x8c
```

---

### Post by Harry33 on 2011-10-24
> **effenberg0x0 said:**
> Compiz/Unity was very stable (almost no crashes at all) until yesterday updates.
Today I'm seeing segfaults every hour or so.

All I did, besides being up-to-date with official repos is update nvidia-proprietary to 290.03 (64) and install Kernel 3.1 RC9.

Is it happening to you guys too? 


Why don't you install kernel 3.1 r10 from PP repos?
Nvidia-current_290.03 works very well in my 64-bit setup.
But there is soemthing odd about linux_3.1.
I am also using xserver 1.11.1.

---

### Post by effenberg0x0 on 2011-10-24
I have a long lasting issue with hpet / tsc clocksource and wrong pstate_0 on powernow-k8 (thus cpufreq speeds). It was supposedly fixed in previous releases, but it's back in newer AMD CPUs. Advanced CPU features, like turbo boosting individual cores, acknowledging runtime or BIOS overclocks and fast transitions between cores is not as effective as it should be by specs. I've been testing some different RCs and nightly kernels on Phenon and Opteron. It's already reported for kernel.org, but they're discussing the issue for a while and there doesn't seem to be consensus. 

I may give up on this battle and go for a more stable PP release, to be in sync with PP testing. 

Regards,
Effenberg

---

