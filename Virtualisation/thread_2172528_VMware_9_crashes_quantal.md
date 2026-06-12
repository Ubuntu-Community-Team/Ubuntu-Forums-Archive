---
title: "VMware 9 crashes quantal"
date: 2013-09-05
forum: Virtualisation
---

### Post by albi2 on 2013-09-05
Hello Ubuntu friends!

Just have some troubel with my ubuntu System 12.10 quantal after i finished the installation of VMware Workstation 9 the system just goes crazy... :confused:

When i try to login an enter the pass word in just switches to the bash with following messages:

I managed to use another TTY so i can Post you guys any ideas?
```
kernel: [   49.380186] general protection fault: 0000 [#1] SMP 
kernel: [   49.380205] CPU 0 
kernel: [   49.380211] Modules linked in: ip6table_filter ip6_tables iptable_filter ip_tables x_tables dm_crypt vmnet(O) vsock(O) vmci(O) vmmon(O) joydev snd_hda_codec_hdmi snd_hda_codec_realtek coretemp arc4 kvm dell_wmi snd_hda_intel snd_hda_codec snd_hwdep snd_pcm sparse_keymap snd_seq_midi snd_rawmidi snd_seq_midi_event dell_laptop dcdbas microcode snd_seq rts5139(C) snd_timer snd_seq_device uvcvideo videobuf2_core videodev videobuf2_vmalloc videobuf2_memops wmi iwlwifi snd psmouse mac80211 btusb cfg80211 soundcore snd_page_alloc lpc_ich parport_pc serio_raw ppdev mei mac_hid rfcomm bnep bluetooth lp parport binfmt_misc nls_iso8859_1 ghash_clmulni_intel aesni_intel cryptd aes_x86_64 ahci libahci i915 drm_kms_helper drm i2c_algo_bit video r8169
kernel: [   49.380434] 
kernel: [   49.380436] Pid: 2601, comm: vmware-hostd Tainted: P         C O 3.5.0-39-generic #60-Ubuntu Dell Inc. Inspiron 5721/0T5XWG
kernel: [   49.380466] RIP: 0010:[<ffffffffa0fdb21f>]  [<ffffffffa0fdb21f>] **_HostIF_SafeRDMSR+0xf/0x30_** [vmmon] *(whats that?)*
kernel: [   49.380494] RSP: 0018:ffff88023057bb08  EFLAGS: 00010246
kernel: [   49.380508] RAX: 0000000000000000 RBX: 0000000000000001 RCX: 0000000000000491
kernel: [   49.380527] RDX: 0000000000000000 RSI: ffff88024dfc6d90 RDI: 0000000000000491
kernel: [   49.380544] RBP: ffff88023057bb08 R08: ffff88025f216800 R09: ffffffffa0fd9882
kernel: [   49.380562] R10: 0000000005865a14 R11: 0000000000000246 R12: 0000000000000000
kernel: [   49.380580] R13: ffff88024dfc6d80 R14: ffff88024dfc6d80 R15: 00007ffffacb6320
kernel: [   49.380599] FS:  00007ff4de81c740(0000) GS:ffff88025f200000(0000) knlGS:0000000000000000
kernel: [   49.380619] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
kernel: [   49.380634] CR2: 0000000000db93e0 CR3: 0000000230733000 CR4: 00000000001407f0
kernel: [   49.380652] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
kernel: [   49.380670] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
kernel: [   49.380689] Process vmware-hostd (pid: 2601, threadinfo ffff88023057a000, task ffff88025067dc00)
kernel: [   49.380711] Stack:
kernel: [   49.380717]  ffff88023057bb38 ffffffffa0fdeb73 ffffffffa0fdeaf0 ffff88023057bb68
kernel: [   49.381711]  ffff88024dfc6d80 0000000000000000 ffff88023057bb58 ffffffffa0fda990
 [   49.382678]  ffff88024dfc6d80 00000000fffffff4 ffff88023057bb88 ffffffffa0fe096c
 [   49.383644] Call Trace:
 [   49.384612]  [<ffffffffa0fdeb73>] Vmx86GetMSR+0x83/0xd0 [vmmon]
 [   49.385580]  [<ffffffffa0fdeaf0>] ? Vmx86GetUnavailPerfCtrsOnCPU+0x150/0x150 [vmmon]
 [   49.386549]  [<ffffffffa0fda990>] HostIF_CallOnEachCPU+0x20/0x40 [vmmon]
 [   49.387517]  [<ffffffffa0fe096c>] Vmx86_GetAllMSRs+0x2c/0x50 [vmmon]
 [   49.388487]  [<ffffffffa0fd84df>] LinuxDriver_Ioctl+0x72f/0xd60 [vmmon]
 [   49.389465]  [<ffffffffa0fd91d5>] ? HostIF_GlobalUnlock+0x15/0x20 [vmmon]
 [   49.390449]  [<ffffffff8140e0c5>] ? misc_open+0x105/0x1c0
 [   49.391467]  [<ffffffff811874ff>] ? chrdev_open+0xaf/0x1a0
 [   49.392454]  [<ffffffff8132ff6e>] ? radix_tree_lookup_slot+0xe/0x10
 [   49.393445]  [<ffffffff81123ebe>] ? find_get_page+0x1e/0xa0
 [   49.394435]  [<ffffffff81125f54>] ? filemap_fault+0x114/0x450
 [   49.395423]  [<ffffffff8117d11f>] ? mem_cgroup_update_page_stat+0x1f/0x60
 [   49.396404]  [<ffffffff81123b67>] ? unlock_page+0x27/0x30
 [   49.397382]  [<ffffffff81147bb1>] ? __do_fault+0x421/0x530
 [   49.398354]  [<ffffffff8114ac54>] ? handle_pte_fault+0x94/0x430
 [   49.399322]  [<ffffffff81192768>] ? path_openat+0x108/0x430
 [   49.400286]  [<ffffffff8114bd49>] ? handle_mm_fault+0x259/0x320
 [   49.401240]  [<ffffffff81686e3c>] ? do_page_fault+0x1cc/0x4e0
 [   49.402193]  [<ffffffffa0fd8b28>] LinuxDriver_UnlockedIoctl+0x18/0x20 [vmmon]
 [   49.403152]  [<ffffffff81194c99>] do_vfs_ioctl+0x99/0x590
 [   49.404114]  [<ffffffff8116ed20>] ? kmem_cache_free+0x20/0x100
 [   49.405097]  [<ffffffff8118dc93>] ? putname+0x33/0x50
 [   49.406044]  [<ffffffff81195229>] sys_ioctl+0x99/0xa0
 [   49.406973]  [<ffffffff8168b469>] system_call_fastpath+0x16/0x1b
 [   49.407890] Code: 83 c4 01 e8 e4 51 15 e0 44 89 e0 48 3b 43 08 72 e9 48 89 df e8 93 3c 19 e0 eb 9e 90 55 48 89 e5 0f 1f 44 00 00 31 c0 89 c2 89 f9 <0f> 32 31 ff 41 89 c0 48 c1 e2 20 89 f8 4c 09 c2 48 89 16 5d c3 
 [   49.409917] RIP  [<ffffffffa0fdb21f>] HostIF_SafeRDMSR+0xf/0x30 [vmmon]
 [   49.410926]  RSP <ffff88023057bb08>
 [   49.416702] ---[ end trace 0c25b58eda6c3d75 ]---
```


I have also the Setup Log 

```
[12,153] 
[12,154] 
[12,154] Installer running.
[12,154] Command Line Arguments:
[12,154] ['/tmp/vmis.wWwCgm/install/vmware-installer/vmware-installer.py', '--set-setting', 'vmware-installer', 'libconf', '/tmp/vmis.wWwCgm/install/vmware-installer/lib/libconf', '--install-component', '/tmp/vmis.wWwCgm/install/vmware-installer', '--install-bundle', '/home/albi/Downloads/Vmware 9 for liux/./VMware-Workstation-Full-9.0.0-812388.x86_64.bundle', '']
[13,393] Successfully loaded GTK libraries.
[13,414] Using UI type gtk
[13,428] Opening database file /etc/vmware-installer/database
[16,694] Could not locate installer App Control.
[16,696] Opening database file /etc/vmware-installer/database
[16,759] destination /tmp/tmpYpevHX/.installer/5.0.0/include/versions.py already exists, overwriting.
[16,761] destination /tmp/tmpYpevHX/.installer/5.0.0/include/initscript.py already exists, overwriting.
[16,762] destination /tmp/tmpYpevHX/.installer/5.0.0/__init__.py already exists, overwriting.
[16,764] destination /tmp/tmpYpevHX/.installer/5.0.0/include/systemType.py already exists, overwriting.
[16,765] destination /tmp/tmpYpevHX/.installer/5.0.0/include/update.py already exists, overwriting.
[16,792] destination /tmp/tmpYpevHX/.installer/9.0.0/include/versions.py already exists, overwriting.
[16,793] destination /tmp/tmpYpevHX/.installer/9.0.0/include/systemType.py already exists, overwriting.
[16,794] destination /tmp/tmpYpevHX/.installer/9.0.0/include/initscript.py already exists, overwriting.
[16,795] destination /tmp/tmpYpevHX/.installer/9.0.0/include/update.py already exists, overwriting.
[16,795] destination /tmp/tmpYpevHX/.installer/9.0.0/__init__.py already exists, overwriting.
[16,809] destination /tmp/tmpYpevHX/.installer/9.2.0/include/initscript.py already exists, overwriting.
[16,810] destination /tmp/tmpYpevHX/.installer/9.2.0/include/update.py already exists, overwriting.
[16,811] destination /tmp/tmpYpevHX/.installer/9.2.0/__init__.py already exists, overwriting.
[16,811] destination /tmp/tmpYpevHX/.installer/9.2.0/include/versions.py already exists, overwriting.
[16,812] destination /tmp/tmpYpevHX/.installer/9.2.0/include/systemType.py already exists, overwriting.
[16,816] destination /tmp/tmpYpevHX/.installer/9.2.0/include/update.py already exists, overwriting.
[16,817] destination /tmp/tmpYpevHX/.installer/9.2.0/include/initscript.py already exists, overwriting.
[16,818] destination /tmp/tmpYpevHX/.installer/9.2.0/__init__.py already exists, overwriting.
[16,818] destination /tmp/tmpYpevHX/.installer/9.2.0/include/systemType.py already exists, overwriting.
[16,819] destination /tmp/tmpYpevHX/.installer/9.2.0/include/versions.py already exists, overwriting.
[16,823] destination /tmp/tmpYpevHX/.installer/9.2.0/include/update.py already exists, overwriting.
[16,824] destination /tmp/tmpYpevHX/.installer/9.2.0/include/initscript.py already exists, overwriting.
[16,825] destination /tmp/tmpYpevHX/.installer/9.2.0/__init__.py already exists, overwriting.
[16,826] destination /tmp/tmpYpevHX/.installer/9.2.0/include/versions.py already exists, overwriting.
[16,827] destination /tmp/tmpYpevHX/.installer/9.2.0/include/systemType.py already exists, overwriting.
[16,831] destination /tmp/tmpYpevHX/.installer/9.2.0/include/update.py already exists, overwriting.
[16,832] destination /tmp/tmpYpevHX/.installer/9.2.0/include/initscript.py already exists, overwriting.
[16,833] destination /tmp/tmpYpevHX/.installer/9.2.0/__init__.py already exists, overwriting.
[16,834] destination /tmp/tmpYpevHX/.installer/9.2.0/include/versions.py already exists, overwriting.
[16,834] destination /tmp/tmpYpevHX/.installer/9.2.0/include/systemType.py already exists, overwriting.
[16,839] destination /tmp/tmpYpevHX/.installer/9.2.0/include/update.py already exists, overwriting.
[16,840] destination /tmp/tmpYpevHX/.installer/9.2.0/include/initscript.py already exists, overwriting.
[16,841] destination /tmp/tmpYpevHX/.installer/9.2.0/__init__.py already exists, overwriting.
[16,842] destination /tmp/tmpYpevHX/.installer/9.2.0/include/versions.py already exists, overwriting.
[16,842] destination /tmp/tmpYpevHX/.installer/9.2.0/include/systemType.py already exists, overwriting.
[16,854] destination /tmp/tmpYpevHX/.installer/5.0.0/include/versions.py already exists, overwriting.
[16,855] destination /tmp/tmpYpevHX/.installer/5.0.0/include/initscript.py already exists, overwriting.
[16,856] destination /tmp/tmpYpevHX/.installer/5.0.0/include/update.py already exists, overwriting.
[16,857] destination /tmp/tmpYpevHX/.installer/5.0.0/__init__.py already exists, overwriting.
[16,858] destination /tmp/tmpYpevHX/.installer/5.0.0/include/systemType.py already exists, overwriting.
[16,869] destination /tmp/tmpYpevHX/.installer/1.12.0/include/versions.py already exists, overwriting.
[16,869] destination /tmp/tmpYpevHX/.installer/1.12.0/__init__.py already exists, overwriting.
[16,871] destination /tmp/tmpYpevHX/.installer/1.12.0/include/update.py already exists, overwriting.
[16,871] destination /tmp/tmpYpevHX/.installer/1.12.0/include/systemType.py already exists, overwriting.
[16,872] destination /tmp/tmpYpevHX/.installer/1.12.0/include/initscript.py already exists, overwriting.
[16,877] destination /tmp/tmpYpevHX/.installer/9.0.0/include/versions.py already exists, overwriting.
[16,877] destination /tmp/tmpYpevHX/.installer/9.0.0/__init__.py already exists, overwriting.
[16,878] destination /tmp/tmpYpevHX/.installer/9.0.0/include/systemType.py already exists, overwriting.
[16,879] destination /tmp/tmpYpevHX/.installer/9.0.0/include/initscript.py already exists, overwriting.
[16,881] destination /tmp/tmpYpevHX/.installer/9.0.0/include/update.py already exists, overwriting.
[16,897] destination /tmp/tmpYpevHX/.installer/5.0.0/include/initscript.py already exists, overwriting.
[16,898] destination /tmp/tmpYpevHX/.installer/5.0.0/include/update.py already exists, overwriting.
[16,899] destination /tmp/tmpYpevHX/.installer/5.0.0/__init__.py already exists, overwriting.
[16,899] destination /tmp/tmpYpevHX/.installer/5.0.0/include/versions.py already exists, overwriting.
[16,900] destination /tmp/tmpYpevHX/.installer/5.0.0/include/systemType.py already exists, overwriting.
[16,904] destination /tmp/tmpYpevHX/.installer/9.0.0/include/initscript.py already exists, overwriting.
[16,905] destination /tmp/tmpYpevHX/.installer/9.0.0/include/versions.py already exists, overwriting.
[16,906] destination /tmp/tmpYpevHX/.installer/9.0.0/include/systemType.py already exists, overwriting.
[16,908] destination /tmp/tmpYpevHX/.installer/9.0.0/include/update.py already exists, overwriting.
[16,909] destination /tmp/tmpYpevHX/.installer/9.0.0/__init__.py already exists, overwriting.
[17,002] Not running in a virtual machine.

[17,009] Running on a real machine!
[17,064] 4096

[20,664] Cannot use vmware-app-control to shut down open VMs, defaulting to fallback message.
[20,678] Ignored execution error: [Errno 2] No such file or directory when running command: [None, 'stoppable']
[33,999] This system has KVM enabled. You cannot run VMs with KVM enabled.
[41,595] 3.5.0-39-generic

[52,927] Attempting to change symlink /usr/lib/vmware/bin/vmware-modconfig to permission 493. Operation is not allowed, skipping.
[52,927] Attempting to change symlink /usr/lib/vmware/bin/vmware-modconfig-console to permission 493. Operation is not allowed, skipping.
[52,928] Attempting to change symlink /usr/lib/vmware/bin/vmware-gksu to permission 493. Operation is not allowed, skipping.
[52,928] Attempting to change symlink /usr/lib/vmware/bin/vmware-vmblock-fuse to permission 493. Operation is not allowed, skipping.
[54,021] Prelink not present, skipping configuration.
[58,574] Configuring Bridged network vmnet0
Configuring hostonly network vmnet1, probing for unused subnet ...
Configuring NAT network vmnet8, probing for unused subnet ...
Configured default networks - Bridged, Hostonly, NAT

[2013-09-05 22:04:01,843]  Adding system startup for /etc/init.d/vmware ...
   /etc/rc0.d/K08vmware -> ../init.d/vmware
   /etc/rc6.d/K08vmware -> ../init.d/vmware
   /etc/rc2.d/S19vmware -> ../init.d/vmware
   /etc/rc3.d/S19vmware -> ../init.d/vmware
   /etc/rc4.d/S19vmware -> ../init.d/vmware

[2013-09-05 22:04:01,846] Installed Service: vmware
[2013-09-05 22:04:03,297] Stopping VMware services:
   VMware Authentication Daemon[71G done
   VM communication interface socket family[71G done
   Virtual machine communication interface[71G done
   Virtual machine monitor[71G done
   Blocking file system[71G done

[2013-09-05 22:04:04,912] Starting VMware services:
   Virtual machine monitor[71Gfailed
   Virtual machine communication interface[71Gfailed
   VM communication interface socket family[71Gfailed
   Blocking file system[71G done
   Virtual ethernet[71Gfailed
   VMware Authentication Daemon[71G done

[2013-09-05 22:04:14,272] 
[2013-09-05 22:04:14,272] 
[2013-09-05 22:04:14,272] Installer running.
[2013-09-05 22:04:14,273] Command Line Arguments:
[2013-09-05 22:04:14,273] ['/tmp/vmis.wWwCgm/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-vmx', 'regular', '/lib/modules/3.5.0-39-generic/misc/vmmon.ko']
[2013-09-05 22:04:14,453] Successfully loaded GTK libraries.
[2013-09-05 22:04:14,456] Using UI type gtk
[2013-09-05 22:04:14,458] Opening database file /etc/vmware-installer/database
[2013-09-05 22:04:14,826] 
[2013-09-05 22:04:14,827] 
[2013-09-05 22:04:14,827] Installer running.
[2013-09-05 22:04:14,828] Command Line Arguments:
[2013-09-05 22:04:14,828] ['/tmp/vmis.wWwCgm/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-vmx', 'regular', '/usr/lib/vmware/symvers/vmmon-3.5.0-39-generic']
[2013-09-05 22:04:15,002] Successfully loaded GTK libraries.
[2013-09-05 22:04:15,005] Using UI type gtk
[2013-09-05 22:04:15,007] Opening database file /etc/vmware-installer/database
[2013-09-05 22:04:20,085] 
[2013-09-05 22:04:20,085] 
[2013-09-05 22:04:20,085] Installer running.
[2013-09-05 22:04:20,085] Command Line Arguments:
[2013-09-05 22:04:20,085] ['/tmp/vmis.wWwCgm/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-vmx', 'regular', '/lib/modules/3.5.0-39-generic/misc/vmnet.ko']
[2013-09-05 22:04:20,250] Successfully loaded GTK libraries.
[2013-09-05 22:04:20,252] Using UI type gtk
[2013-09-05 22:04:20,254] Opening database file /etc/vmware-installer/database
[2013-09-05 22:04:20,692] 
[2013-09-05 22:04:20,692] 
[2013-09-05 22:04:20,692] Installer running.
[2013-09-05 22:04:20,693] Command Line Arguments:
[2013-09-05 22:04:20,693] ['/tmp/vmis.wWwCgm/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-vmx', 'regular', '/usr/lib/vmware/symvers/vmnet-3.5.0-39-generic']
[2013-09-05 22:04:20,862] Successfully loaded GTK libraries.
[2013-09-05 22:04:20,865] Using UI type gtk
[2013-09-05 22:04:20,867] Opening database file /etc/vmware-installer/database
[2013-09-05 22:04:25,140] 
[2013-09-05 22:04:25,140] 
[2013-09-05 22:04:25,140] Installer running.
[2013-09-05 22:04:25,140] Command Line Arguments:
[2013-09-05 22:04:25,140] ['/tmp/vmis.wWwCgm/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-vmx', 'regular', '/lib/modules/3.5.0-39-generic/misc/vmblock.ko']
[2013-09-05 22:04:25,319] Successfully loaded GTK libraries.
[2013-09-05 22:04:25,322] Using UI type gtk
[2013-09-05 22:04:25,324] Opening database file /etc/vmware-installer/database
[2013-09-05 22:04:25,729] 
[2013-09-05 22:04:25,729] 
[2013-09-05 22:04:25,729] Installer running.
[2013-09-05 22:04:25,729] Command Line Arguments:
[2013-09-05 22:04:25,730] ['/tmp/vmis.wWwCgm/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-vmx', 'regular', '/usr/lib/vmware/symvers/vmblock-3.5.0-39-generic']
[2013-09-05 22:04:25,934] Successfully loaded GTK libraries.
[2013-09-05 22:04:25,936] Using UI type gtk
[2013-09-05 22:04:25,938] Opening database file /etc/vmware-installer/database
[2013-09-05 22:04:28,809] 
[2013-09-05 22:04:28,809] 
[2013-09-05 22:04:28,810] Installer running.
[2013-09-05 22:04:28,810] Command Line Arguments:
[2013-09-05 22:04:28,810] ['/tmp/vmis.wWwCgm/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-vmx', 'regular', '/lib/modules/3.5.0-39-generic/misc/vmci.ko']
[2013-09-05 22:04:28,963] Successfully loaded GTK libraries.
[2013-09-05 22:04:28,965] Using UI type gtk
[2013-09-05 22:04:28,967] Opening database file /etc/vmware-installer/database
[2013-09-05 22:04:29,333] 
[2013-09-05 22:04:29,334] 
[2013-09-05 22:04:29,334] Installer running.
[2013-09-05 22:04:29,334] Command Line Arguments:
[2013-09-05 22:04:29,334] ['/tmp/vmis.wWwCgm/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-vmx', 'regular', '/usr/lib/vmware/symvers/vmci-3.5.0-39-generic']
[2013-09-05 22:04:29,535] Successfully loaded GTK libraries.
[2013-09-05 22:04:29,537] Using UI type gtk
[2013-09-05 22:04:29,539] Opening database file /etc/vmware-installer/database
[2013-09-05 22:04:31,986] 
[2013-09-05 22:04:31,986] 
[2013-09-05 22:04:31,986] Installer running.
[2013-09-05 22:04:31,986] Command Line Arguments:
[2013-09-05 22:04:31,986] ['/tmp/vmis.wWwCgm/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-vmx', 'regular', '/lib/modules/3.5.0-39-generic/misc/vsock.ko']
[2013-09-05 22:04:32,191] Successfully loaded GTK libraries.
[2013-09-05 22:04:32,193] Using UI type gtk
[2013-09-05 22:04:32,195] Opening database file /etc/vmware-installer/database
[2013-09-05 22:04:33,044] 
[2013-09-05 22:04:33,044] 
[2013-09-05 22:04:33,044] Installer running.
[2013-09-05 22:04:33,044] Command Line Arguments:
[2013-09-05 22:04:33,044] ['/tmp/vmis.wWwCgm/install/vmware-installer/vmware-installer.py', '--register-file', 'vmware-vmx', 'regular', '/usr/lib/vmware/symvers/vsock-3.5.0-39-generic']
[2013-09-05 22:04:33,206] Successfully loaded GTK libraries.
[2013-09-05 22:04:33,208] Using UI type gtk
[2013-09-05 22:04:33,210] Opening database file /etc/vmware-installer/database
[2013-09-05 22:05:03,667] Stopping VMware services:
   VMware Authentication Daemon[71G done
   VM communication interface socket family[71G done
   Virtual machine communication interface[71G done
   Virtual machine monitor[71G done
   Blocking file system[71G done
make: Entering directory `/tmp/modconfig-RUdJu9/vmmon-only'
/usr/bin/make -C /lib/modules/3.5.0-39-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-39-generic'
  CC [M]  /tmp/modconfig-RUdJu9/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/modconfig-RUdJu9/vmmon-only/linux/driver.o
  CC [M]  /tmp/modconfig-RUdJu9/vmmon-only/linux/hostif.o
  CC [M]  /tmp/modconfig-RUdJu9/vmmon-only/common/apic.o
  CC [M]  /tmp/modconfig-RUdJu9/vmmon-only/common/comport.o
  CC [M]  /tmp/modconfig-RUdJu9/vmmon-only/common/cpuid.o
  CC [M]  /tmp/modconfig-RUdJu9/vmmon-only/common/hashFunc.o
  CC [M]  /tmp/modconfig-RUdJu9/vmmon-only/common/memtrack.o
  CC [M]  /tmp/modconfig-RUdJu9/vmmon-only/common/phystrack.o
  CC [M]  /tmp/modconfig-RUdJu9/vmmon-only/common/task.o
  CC [M]  /tmp/modconfig-RUdJu9/vmmon-only/common/vmx86.o
  CC [M]  /tmp/modconfig-RUdJu9/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/modconfig-RUdJu9/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/modconfig-RUdJu9/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/modconfig-RUdJu9/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-39-generic'
/usr/bin/make -C $PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= postbuild
make[1]: Entering directory `/tmp/modconfig-RUdJu9/vmmon-only'
make[1]: `postbuild' is up to date.
make[1]: Leaving directory `/tmp/modconfig-RUdJu9/vmmon-only'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/modconfig-RUdJu9/vmmon-only'
make: Entering directory `/tmp/modconfig-RUdJu9/vmnet-only'
/usr/bin/make -C /lib/modules/3.5.0-39-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-39-generic'
  CC [M]  /tmp/modconfig-RUdJu9/vmnet-only/driver.o
  CC [M]  /tmp/modconfig-RUdJu9/vmnet-only/hub.o
  CC [M]  /tmp/modconfig-RUdJu9/vmnet-only/userif.o
  CC [M]  /tmp/modconfig-RUdJu9/vmnet-only/netif.o
  CC [M]  /tmp/modconfig-RUdJu9/vmnet-only/bridge.o
  CC [M]  /tmp/modconfig-RUdJu9/vmnet-only/filter.o
  CC [M]  /tmp/modconfig-RUdJu9/vmnet-only/procfs.o
  CC [M]  /tmp/modconfig-RUdJu9/vmnet-only/smac_compat.o
  CC [M]  /tmp/modconfig-RUdJu9/vmnet-only/vnetEvent.o
  CC [M]  /tmp/modconfig-RUdJu9/vmnet-only/smac.o
  CC [M]  /tmp/modconfig-RUdJu9/vmnet-only/vnetUserListener.o
  LD [M]  /tmp/modconfig-RUdJu9/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/modconfig-RUdJu9/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/modconfig-RUdJu9/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-39-generic'
/usr/bin/make -C $PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= postbuild
make[1]: Entering directory `/tmp/modconfig-RUdJu9/vmnet-only'
make[1]: `postbuild' is up to date.
make[1]: Leaving directory `/tmp/modconfig-RUdJu9/vmnet-only'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/modconfig-RUdJu9/vmnet-only'
make: Entering directory `/tmp/modconfig-RUdJu9/vmblock-only'
/usr/bin/make -C /lib/modules/3.5.0-39-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-39-generic'
  CC [M]  /tmp/modconfig-RUdJu9/vmblock-only/linux/block.o
  CC [M]  /tmp/modconfig-RUdJu9/vmblock-only/linux/control.o
  CC [M]  /tmp/modconfig-RUdJu9/vmblock-only/linux/dentry.o
  CC [M]  /tmp/modconfig-RUdJu9/vmblock-only/linux/file.o
  CC [M]  /tmp/modconfig-RUdJu9/vmblock-only/linux/filesystem.o
  CC [M]  /tmp/modconfig-RUdJu9/vmblock-only/linux/inode.o
  CC [M]  /tmp/modconfig-RUdJu9/vmblock-only/linux/module.o
  CC [M]  /tmp/modconfig-RUdJu9/vmblock-only/linux/stubs.o
  CC [M]  /tmp/modconfig-RUdJu9/vmblock-only/linux/super.o
  LD [M]  /tmp/modconfig-RUdJu9/vmblock-only/vmblock.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/modconfig-RUdJu9/vmblock-only/vmblock.mod.o
  LD [M]  /tmp/modconfig-RUdJu9/vmblock-only/vmblock.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-39-generic'
/usr/bin/make -C $PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= postbuild
make[1]: Entering directory `/tmp/modconfig-RUdJu9/vmblock-only'
make[1]: `postbuild' is up to date.
make[1]: Leaving directory `/tmp/modconfig-RUdJu9/vmblock-only'
cp -f vmblock.ko ./../vmblock.o
make: Leaving directory `/tmp/modconfig-RUdJu9/vmblock-only'
make: Entering directory `/tmp/modconfig-RUdJu9/vmci-only'
/usr/bin/make -C /lib/modules/3.5.0-39-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-39-generic'
  CC [M]  /tmp/modconfig-RUdJu9/vmci-only/linux/driver.o
  CC [M]  /tmp/modconfig-RUdJu9/vmci-only/linux/vmciKernelIf.o
  CC [M]  /tmp/modconfig-RUdJu9/vmci-only/common/vmciContext.o
  CC [M]  /tmp/modconfig-RUdJu9/vmci-only/common/vmciDatagram.o
  CC [M]  /tmp/modconfig-RUdJu9/vmci-only/common/vmciDoorbell.o
  CC [M]  /tmp/modconfig-RUdJu9/vmci-only/common/vmciDriver.o
  CC [M]  /tmp/modconfig-RUdJu9/vmci-only/common/vmciEvent.o
  CC [M]  /tmp/modconfig-RUdJu9/vmci-only/common/vmciHashtable.o
  CC [M]  /tmp/modconfig-RUdJu9/vmci-only/common/vmciQPair.o
  CC [M]  /tmp/modconfig-RUdJu9/vmci-only/common/vmciQueuePair.o
  CC [M]  /tmp/modconfig-RUdJu9/vmci-only/common/vmciResource.o
  CC [M]  /tmp/modconfig-RUdJu9/vmci-only/common/vmciRoute.o
  CC [M]  /tmp/modconfig-RUdJu9/vmci-only/driverLog.o
  LD [M]  /tmp/modconfig-RUdJu9/vmci-only/vmci.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/modconfig-RUdJu9/vmci-only/vmci.mod.o
  LD [M]  /tmp/modconfig-RUdJu9/vmci-only/vmci.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-39-generic'
/usr/bin/make -C $PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= postbuild
make[1]: Entering directory `/tmp/modconfig-RUdJu9/vmci-only'
make[1]: `postbuild' is up to date.
make[1]: Leaving directory `/tmp/modconfig-RUdJu9/vmci-only'
cp -f vmci.ko ./../vmci.o
make: Leaving directory `/tmp/modconfig-RUdJu9/vmci-only'
make: Entering directory `/tmp/modconfig-RUdJu9/vsock-only'
/usr/bin/make -C /lib/modules/3.5.0-39-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-39-generic'
  CC [M]  /tmp/modconfig-RUdJu9/vsock-only/linux/af_vsock.o
  CC [M]  /tmp/modconfig-RUdJu9/vsock-only/linux/notifyQState.o
  CC [M]  /tmp/modconfig-RUdJu9/vsock-only/linux/stats.o
  CC [M]  /tmp/modconfig-RUdJu9/vsock-only/linux/notify.o
  CC [M]  /tmp/modconfig-RUdJu9/vsock-only/linux/util.o
  CC [M]  /tmp/modconfig-RUdJu9/vsock-only/linux/vsockAddr.o
  CC [M]  /tmp/modconfig-RUdJu9/vsock-only/driverLog.o
  LD [M]  /tmp/modconfig-RUdJu9/vsock-only/vsock.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/modconfig-RUdJu9/vsock-only/vsock.mod.o
  LD [M]  /tmp/modconfig-RUdJu9/vsock-only/vsock.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-39-generic'
/usr/bin/make -C $PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= postbuild
make[1]: Entering directory `/tmp/modconfig-RUdJu9/vsock-only'
make[1]: `postbuild' is up to date.
make[1]: Leaving directory `/tmp/modconfig-RUdJu9/vsock-only'
cp -f vsock.ko ./../vsock.o
make: Leaving directory `/tmp/modconfig-RUdJu9/vsock-only'
Starting VMware services:
   Virtual machine monitor[71G done
   Virtual machine communication interface[71G done
   VM communication interface socket family[71G done
   Blocking file system[71G done
   Virtual ethernet[71G done
   VMware Authentication Daemon[71G done
   Shared Memory Available[71G done

[2013-09-05 22:05:03,668] Using 2.6.x kernel build system.
Using 2.6.x kernel build system.
Using 2.6.x kernel build system.
Using 2.6.x kernel build system.
Using 2.6.x kernel build system.

[2013-09-05 22:05:03,670] Successfully installed kernel modules
[2013-09-05 22:05:06,248] Unknown option --version

[2013-09-05 22:05:26,250] Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'

[2013-09-05 22:05:33,643]  System start/stop links for /etc/init.d/vmware-USBArbitrator already exist.

[2013-09-05 22:05:33,649] Installed Service: vmware-USBArbitrator
[2013-09-05 22:05:33,718] 

[2013-09-05 22:05:33,725] Unable to stop current USB Arbitrator service.  Not fatal.
[2013-09-05 22:05:33,799] 

[2013-09-05 22:05:36,394] Attempting to change symlink /usr/lib/vmware/bin/thnuclnt to permission 493. Operation is not allowed, skipping.
[2013-09-05 22:05:36,395] Attempting to change symlink /usr/lib/vmware/bin/vmplayer to permission 493. Operation is not allowed, skipping.
[2013-09-05 22:05:36,395] Attempting to change symlink /usr/lib/vmware/bin/vmware-unity-helper to permission 493. Operation is not allowed, skipping.
[2013-09-05 22:05:36,395] Attempting to change symlink /usr/lib/vmware/bin/vmware-fuseUI to permission 493. Operation is not allowed, skipping.
[2013-09-05 22:05:36,395] Attempting to change symlink /usr/lib/vmware/bin/vmware-app-control to permission 493. Operation is not allowed, skipping.
[2013-09-05 22:05:36,395] Attempting to change symlink /usr/lib/vmware/bin/vmware-zenity to permission 493. Operation is not allowed, skipping.
[2013-09-05 22:05:39,933] Unknown option --version

[2013-09-05 22:05:41,386] Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'

[2013-09-05 22:05:46,972] Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service cups restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop cups ; start cups. The restart(8) utility is also available.
cups stop/waiting
cups start/running, process 28008

[2013-09-05 22:05:48,611] Stopping VMware services:
   VMware Authentication Daemon[71G done
   VM communication interface socket family[71G done
   Virtual machine communication interface[71G done
   Virtual machine monitor[71G done
   Blocking file system[71G done

[2013-09-05 22:05:50,332] Starting VMware services:
   Virtual machine monitor[71G done
   Virtual machine communication interface[71G done
   VM communication interface socket family[71G done
   Blocking file system[71G done
   Virtual ethernet[71G done
   VMware Authentication Daemon[71G done
   Shared Memory Available[71G done

[2013-09-05 22:05:53,585]  Adding system startup for /etc/init.d/vmware-workstation-server ...
   /etc/rc0.d/K06vmware-workstation-server -> ../init.d/vmware-workstation-server
   /etc/rc6.d/K06vmware-workstation-server -> ../init.d/vmware-workstation-server
   /etc/rc2.d/S55vmware-workstation-server -> ../init.d/vmware-workstation-server
   /etc/rc3.d/S55vmware-workstation-server -> ../init.d/vmware-workstation-server
   /etc/rc4.d/S55vmware-workstation-server -> ../init.d/vmware-workstation-server

[2013-09-05 22:05:53,589] Installed Service: vmware-workstation-server
[2013-09-05 22:05:55,004]    Starting Workstation Server:[71G done

[2013-09-05 22:06:07,008] Attempting to change symlink /usr/lib/vmware/bin/vmware to permission 493. Operation is not allowed, skipping.
[2013-09-05 22:06:07,008] Attempting to change symlink /usr/lib/vmware/bin/vmware-tray to permission 493. Operation is not allowed, skipping.
[2013-09-05 22:06:07,008] Attempting to change symlink /usr/lib/vmware/bin/vmware-enter-serial to permission 493. Operation is not allowed, skipping.
[2013-09-05 22:06:08,403] Unknown option --version

[2013-09-05 22:06:09,680] Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'

[2013-09-05 22:06:10,378] Stopping VMware services:
   VMware Authentication Daemon[71G done
   VMware Authentication Daemon[71G done

[2013-09-05 22:06:10,378] At least one instance of VMware VMX is still running.
Please stop all running instances of VMware VMX first.
 

[2013-09-05 22:06:11,113] Starting VMware services:
   Virtual machine monitor[71G done
   Virtual machine communication interface[71G done
   VM communication interface socket family[71G done
   Blocking file system[71G done
   Virtual ethernet[71G done
   VMware Authentication Daemon[71G done
   Shared Memory Available[71G done


```

---

### Post by adityagagat93 on 2014-01-06
I know it's 4 months old, but i got the same problem.
 is there any solution for this? :(

---

