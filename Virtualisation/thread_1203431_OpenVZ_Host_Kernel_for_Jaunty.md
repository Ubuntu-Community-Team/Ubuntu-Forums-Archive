---
title: "OpenVZ Host Kernel for Jaunty?"
date: 2009-07-03
forum: Virtualisation
---

### Post by DLLarson on 2009-07-03
Is there an OpenVZ kernel available for the 9.04 release?

Dale

---

### Post by bodhi.zazen on 2009-07-03
Not unless you want to compile your own.

Openvz is supported in LTS, or 8.04.

If you like the Debian / Ubuntu way, I suggest Proxmox. More up to date then 8.04 .

[http://www.montanalinux.org/proxmox-ve-review.html](http://www.montanalinux.org/proxmox-ve-review.html)

[http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

---

### Post by DLLarson on 2009-07-03
> **bodhi.zazen said:**
> Not unless you want to compile your own.

I've tried that with several recent versions from a GIT clone from OpenVZ's repository but the VE's hang on launch with a kernel OOPS (they run fine on the Ubuntu LTS OpenVZ kernel[8.04]):

```

[   58.210735] warning: `vzctl' uses 32-bit capabilities (legacy support in use)
[   58.214408] BUG: unable to handle kernel NULL pointer dereference at 00000000
[   58.214541] IP: [<f8b03994>] :vzmon:alloc_ve_tty_driver+0x34/0xe0
[   58.214633] *pde = 00000000
[   58.214638] Oops: 0000 [#1] SMP
[   58.214752] Modules linked in: vzethdev vznetdev simfs vzrst vzcpt tun vzdquota vzmon vzdev xt_tcpudp xt_length ipt_ttl xt_tcpmss xt_TCPMSS iptable_mangle iptable_filter xt_multiport xt_limit xt_dscp ipt_REJECT ip_tables x_tables video output lp parport snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd nvidia(P) soundcore psmouse snd_page_alloc i2c_nforce2 k8temp serio_raw agpgart pcspkr ohci1394 ieee1394 forcedeth
[   58.216698]
[   58.216744] Pid: 3375, comm: vzctl Tainted: P          (2.6.27.21-openvz1 #1 briullov)
[   58.216809] EIP: 0060:[<f8b03994>] EFLAGS: 00010286 CPU: 1
[   58.216863] EIP is at alloc_ve_tty_driver+0x34/0xe0 [vzmon]
[   58.216915] EAX: ecaac000 EBX: ecaac000 ECX: 00000030 EDX: 00000001
[   58.216967] ESI: 00000000 EDI: ecaac000 EBP: ec645e74 ESP: ec645e60
[   58.217011]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[   58.217011] Process vzctl (pid: 3375, veid: 0, ti=ec644000 task=ec608d10 task.ti=ec644000)
[   58.217011] Stack: f7bd0000 00000000 ec608d10 00000000 1c0017bf ec645ee4 f8b0437c c04a8c00
[   58.217011]        00000000 00100009 00000000 f8b05102 00000000 00000000 ec608d10 000000a1
[   58.217011]        00000000 00000000 f7bd0028 c05ef780 f7bd0000 f1e27720 c05ec8b4 c05ef780
[   58.217011]  Call Trace:
[   58.217011]  [<f8b0437c>] ? real_env_create+0x93c/0xe90 [vzmon]
[   58.217011]  [<f8b04c24>] ? vzcalls_ioctl+0x354/0x4d4 [vzmon]
[   58.217011]  [<c0495890>] ? do_page_fault+0x0/0x8e0
[   58.217011]  [<c04939d2>] ? error_code+0x72/0x80
[   58.217011]  [<f8afe1dd>] ? vzctl_ioctl+0x4d/0x5c [vzdev]
[   58.217011]  [<f8b048d0>] ? vzcalls_ioctl+0x0/0x4d4 [vzmon]
[   58.217011]  [<f8afe190>] ? vzctl_ioctl+0x0/0x5c [vzdev]
[   58.217011]  [<c01c47d8>] ? vfs_ioctl+0x28/0x90
[   58.217011]  [<c01c489e>] ? do_vfs_ioctl+0x5e/0x2e0
[   58.217011]  [<c01b5ca7>] ? filp_close+0x47/0x70
[   58.217011]  [<c01c4b59>] ? sys_ioctl+0x39/0x70
[   58.217011]  [<c0104052>] ? syscall_call+0x7/0xb
[   58.217011]  =======================
[   58.217011] Code: b8 98 f5 62 c0 89 55 ec ba d0 00 20 00 89 5d f4 89 75 f8 89 7d fc e8 ac 04 6b c7 85 c0 89 c3 74 5d b9 30 00 00 00 89 c7 8b 75 f0 <f3> a5 c7 80 ac 00 00 00 00 00 00 00 8b 55 f0 f6 83 90 00 00 00
[   58.217011] EIP: [<f8b03994>] alloc_ve_tty_driver+0x34/0xe0 [vzmon] SS:ESP 0068:ec645e60
[   58.222133] ---[ end trace 5b47c69c15ea7eb5 ]---

```

The kernel for LTS will run the existing VE's on Jaunty but I have other problems with it due the fact that Jaunty uses a newer GNU compiler than LTS. I get ton's of errors when rebuilding my NVidia graphics driver.

I'm thinking this has something to do with the VE's but I haven't been able to locate the problem yet.

> **bodhi.zazen said:**
> If you like the Debian / Ubuntu way, I suggest Proxmox. More up to date then 8.04 .

[http://www.montanalinux.org/proxmox-ve-review.html](http://www.montanalinux.org/proxmox-ve-review.html)

[http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

It's very cool but I'm using the system as an Ubuntu desktop system for house guests as well.

Thanks for the reply!

Dale

---

### Post by bodhi.zazen on 2009-07-03
If you are running a desktop, IMO it is easiest then to run 8.04 or proxmox with OpenVZ in a virtual machine (KVM, Virtualbox, or VMWare).

This way you can run 9,04 (or what have you) + Openvz in a VM, best of both worlds. Openvz runs just fine in a VM.

---

### Post by DLLarson on 2009-07-04
> **bodhi.zazen said:**
> If you are running a desktop, IMO it is easiest then to run 8.04 or proxmox with OpenVZ in a virtual machine (KVM, Virtualbox, or VMWare).

This way you can run 9,04 (or what have you) + Openvz in a VM, best of both worlds. Openvz runs just fine in a VM.

That's an excellent suggestion that didn't dawn on me. Thanks!

Dale

---

### Post by DLLarson on 2009-07-05
Just to tie this thread off....

To solve my problem I installed Jaunty 32bit desktop and installed vmware server 2.0 onto that. I then installed the latest Proxmox VE (PVE) into a 64bit VMware quest. Within the PVE host I rsync'ed all my existing 32 bit OpenVZ guests containers from my previous Ubuntu OpenVZ system.

All is working well. Proxmox VE is very cool.

Long live virtualization!

Thanks for all the help...
Dale

---

### Post by Parama on 2009-09-07
> **DLLarson said:**
> Just to tie this thread off....

To solve my problem I installed Jaunty 32bit desktop and installed vmware server 2.0 onto that. I then installed the latest Proxmox VE (PVE) into a 64bit VMware quest. Within the PVE host I rsync'ed all my existing 32 bit OpenVZ guests containers from my previous Ubuntu OpenVZ system.

If you really want the performance edge of Proxmox (the OpenVZ part in particular) you should consider installing Proxmox directly on the hardware as host. Installing Proxmox in a VMware Guest will just give you the limitations of both systems, I guess.

> **DLLarson said:**
> 
All is working well. Proxmox VE is very cool.

Long live virtualization!


I couldn't put it any better. Proxmox is indeed very cool. 
We're running a cluster of 6 Proxmox servers now and the number keeps increasing. 
Having a simple fall-back/backup plan for each guest system combined with load balancing makes an incredibly strong setup :)

---

### Post by Hackie2 on 2009-09-12
Hmm what about my little Intel Atom server? Atoms do not have any hardware virtualisation support. currently it is running intrepid with linux-image-2.6.26-1-vserver-686 from the debian repo. For openvz i was not able to find something useable till now, and i dont want to compile a kernel myself.

no other alternatives to proxmox? or when is the next LTS published? will it contain openvz?

---

### Post by bodhi.zazen on 2009-09-12
> **Hackie2 said:**
> Hmm what about my little Intel Atom server? currently it is running intrepid with linux-image-2.6.26-1-vserver-686 from the debian repo. For openvz i was not able to find something useable till now, and i dont want to compile a kernel myself.

no other alternatives to proxmox? or when is the next LTS published? will it contain openvz?

If you wish to run openvz, and use Ubuntu, and do not wish to compile a kernel, use Ubuntu 8.04.

If you wish something more up to date try Centos, there are rpm available for Centos.

The openvz site also has a few .deb, it the frazen kernel.

[http://wiki.openvz.org/Installation_on_Debian](http://wiki.openvz.org/Installation_on_Debian)

[https://help.ubuntu.com/community/OpenVZ](https://help.ubuntu.com/community/OpenVZ)

---

### Post by denver on 2009-09-12
For stable OpenVZ servers, i too recomend CentOS. Had some issues with Ubuntu and OpenVZ regarding memory usage inside the containers. OpenVZ does not require virtualization to work correctly. I does not do any hadrware abstraction. Its bassicaly a really really really good chroot :). As long as you configure your VM correctly you should see 95+% performance to that of a real system.

If you just want virtualization on your desktop, KVM/VirtualBox is far easyer to use.

---

### Post by narcisgarcia on 2010-03-24
As commented by Dorowan OpenVZ released a 2.6.32 Kernel with OpenVZ support. At the moment the only prebuild packages are for rpm-based distros, but server administrators need a reliable way to upgrade our LTS host servers, and LXC sowftare+docummentation is not ready for OpenVZ migration.

---

### Post by Hackie2 on 2010-03-24
> **narcisgarcia said:**
> As commented by Dorowan OpenVZ released a 2.6.32 Kernel with OpenVZ support. At the moment the only prebuild packages are for rpm-based distros, but server administrators need a reliable way to upgrade our LTS host servers, and LXC sowftare+docummentation is not ready for OpenVZ migration.
same problem here

Considering switching to debian squeeze which supports vserver, openvz. lxc is really not ready yet

---

