---
title: "XEN kernel does not boot in 16.04"
date: 2016-04-28
forum: Virtualisation
---

### Post by Roel_de_Wildt on 2016-04-28
Hi,

I don't know if I'm at the right place but I have a problem to boot the XEN kernel in Ubuntu Server 16.04 LTS. After connecting a serial console I got a lot of Call traces in the console logging. 

This is the first trace I get:
```

[    5.491811] ------------[ cut here ]------------
[    5.494139] WARNING: CPU: 1 PID: 96 at /build/linux-Ay7j_C/linux-4.4.0/arch/x86/xen/multicalls.c:129 xen_mc_flush+0x1a3/0x1b0()
[    5.497433] Modules linked in:
[    5.497477] CPU: 1 PID: 96 Comm: modprobe Not tainted 4.4.0-21-generic #37-Ubuntu
[    5.500388] Hardware name: VMware, Inc. VMware Virtual Platform/440BX Desktop Reference Platform, BIOS 6.00 09/21/2015
[    5.504122]  0000000000000200 00000000719694bd ffff88041fbe7be8 ffffffff813e93c3
[    5.505409]  0000000000000000 ffffffff81c9d3b0 ffff88041fbe7c20 ffffffff81080f62
[    5.509409]  ffff88042c88b8a0 0000000000000001 00007ffc2b1f4000 0000000000000000
[    5.513409] Call Trace:
[    5.514129]  [<ffffffff813e93c3>] dump_stack+0x63/0x90
[    5.514173]  [<ffffffff81080f62>] warn_slowpath_common+0x82/0xc0
[    5.514217]  [<ffffffff810810aa>] warn_slowpath_null+0x1a/0x20
[    5.514260]  [<ffffffff8101d9c3>] xen_mc_flush+0x1a3/0x1b0
[    5.514304]  [<ffffffff8101e21e>] xen_leave_lazy_mmu+0xe/0x20
[    5.514348]  [<ffffffff811c0b9d>] remap_pfn_range+0x34d/0x430
[    5.514392]  [<ffffffff8100407a>] map_vdso+0x11a/0x240
[    5.514436]  [<ffffffff810041f7>] arch_setup_additional_pages+0x27/0x30
[    5.517409]  [<ffffffff81268057>] load_elf_binary+0xb27/0x1170
[    5.517453]  [<ffffffff81212bee>] search_binary_handler+0x9e/0x1d0
[    5.517497]  [<ffffffff81214353>] do_execveat_common.isra.33+0x533/0x710
[    5.517541]  [<ffffffff8121455c>] do_execve+0x2c/0x30
[    5.517585]  [<ffffffff810964db>] call_usermodehelper_exec_async+0xfb/0x150
[    5.517629]  [<ffffffff810963e0>] ? umh_complete+0x40/0x40
[    5.517673]  [<ffffffff8182488f>] ret_from_fork+0x3f/0x70
[    5.517717]  [<ffffffff810963e0>] ? umh_complete+0x40/0x40
[    5.517786] ---[ end trace 12b21bca028d4d36 ]---
[    5.518687] ------------[ cut here ]------------

```
It isn't possible to upload the full log in this forum. The full log until the 512KB limit is at [http://pastebin.com/ySZy0DqE](http://pastebin.com/ySZy0DqE)

Kind regards,
Roel

---

### Post by deadflowr on 2016-04-28
*Thread moved to **Virtualisation**.*

---

### Post by Ze Ha on 2016-04-28
As far as I know, it is a known bug in 16.04.
[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Installing_Xen_host_in_UEFI_mode](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Installing_Xen_host_in_UEFI_mode)

Try to use legacy mode instead of UEFI (If you really used UEFI)

---

### Post by MAFoElffen on 2016-04-28
Note: I edited your first post to put your output within code tags. Take that as an example of how to do that in the future (all output and commands)

My Xen server is 16.04, but not headless, and not on a UEFI system (legacy). Running fine.

Questions:
- What make/model of system is this on?
- What BIOS type is it?

---

### Post by Roel_de_Wildt on 2016-04-28
I'm testing this on a existing vmware vSphere 6.0 server as I want to known if I would replace vmware into xen.

I have a setup running with 14.04.4 and this setup boot correctly into xen on the same vmware vSphere 6.0 server as a virtual machine. I'm using the BIOS mode for the firmware.

The system is a self build machine based on a Supermicro X8DAH motherboard and a Intel Xeon E5645 with 96GB ECC RAM.

The steps to reproduce are as follow:
- Install Ubuntu 16.04 Server
- Install xen-hypervisor
- Install latest updates
- Reboot
- Select in GRUB the default "Xen" kernel and the kernel begins to boot but gives a trace and stops booting.

---

### Post by Ze Ha on 2016-04-28
And what do you think about this: [https://wiki.debian.org/Xen](https://wiki.debian.org/Xen) ?
Try to find "Xen kernel crash" on that page!
> Note : On servers with huge memory, Xen kernel crash
 
But... I don't know what does "huge memory" mean.

---

### Post by Roel_de_Wildt on 2016-04-29
> **Ze Ha said:**
> And what do you think about this: [https://wiki.debian.org/Xen](https://wiki.debian.org/Xen) ?
Try to find "Xen kernel crash" on that page!

But... I don't know what does "huge memory" mean.

I don't know which "huge memory" they reference to. Following the wiki of xen [http://wiki.xenproject.org/wiki/Xen_Project_Release_Features](http://wiki.xenproject.org/wiki/Xen_Project_Release_Features) it supports 4TB RAM, in this context 96GB RAM is low amount.

I've read your URL in the debian wiki and installed ubuntu 16.04 server on my computer and there it does boot the xen kernel. So there must be some bug in either in VMWare ESXi 6.0 and/or in the xen kernel shipped with ubuntu 16.04.

---

### Post by MAFoElffen on 2016-04-29
> **Ze Ha said:**
> And what do you think about this: [https://wiki.debian.org/Xen](https://wiki.debian.org/Xen) ?
Try to find "Xen kernel crash" on that page!

But... I don't know what does "huge memory" mean.
Current Server hardware is 1 TB of RAM. This year AMD is supposed to release their 64-core Opteron... which prompted others to follow with 20-24-core chips... and a Promise to make that 1TB range of RAM seen small.

So I guess description that is subjective and from the writer's perspective.

The published limts spec'ed in Citrix, (Xen's commercial version) says that the limit Xen supports is 1TB RAM, but that if a host has one or more 32-bit paravirtualized guests (Linux VMs) running, that it limts that supported maximum to 128GB RAM.

IMHO, That would be a commercial venture because of cost.

The reason to set a limit, is that without it... Dom0 has a tendency to take over memory and "balloon"... meaning it soaks it up on it's own. I'm thinking that there was a time when it would take memeory, and not release it. Then when it needed more, it would take more... until... Not sure it still does this, will have to ask my son of the details of that (System Engineer, who supports Enterprize Citrix server farms).

Even more important on limited resource management/balancing...

---

