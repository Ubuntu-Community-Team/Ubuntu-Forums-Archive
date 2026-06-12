---
title: "linux-abi on 8.04 gives segfault"
date: 2008-05-01
forum: Server Platforms
---

### Post by lanhelp on 2008-05-01
Hello, im having problems installing linux-abi from [www.sf.net/projects/linux-abi](www.sf.net/projects/linux-abi)

The modules loads ok, but got a segfault when execute some sco binaries, look at dmesd:

```

[ 1225.628597] cobrun[7691]: segfault at 000000d4 eip 000000d4 esp bfffe6bc error 4
[ 1225.629307] ------------[ cut here ]------------
[ 1225.629313] kernel BUG at /build/buildd/linux-2.6.24/mm/mmap.c:2054!
[ 1225.629317] invalid opcode: 0000 [#3] SMP 
[ 1225.629322] Modules linked in: abi_wyse abi_uw7 abi_solaris abi_isc abi_ibcs abi_sco abi_cxenix abi_svr4 binfmt_xout binfmt_coff abi_lcall abi_util i915 drm rfcomm l2cap bluetooth ppdev acpi_cpufreq cpufreq_ondemand cpufreq_stats cpufreq_userspace cpufreq_conservative freq_table cpufreq_powersave container sbs sbshc video output dock battery iptable_filter ip_tables x_tables ac ipv6 lp evdev serio_raw parport_pc parport psmouse pcspkr snd_hda_intel snd_pcm_oss snd_mixer_oss atl2 snd_pcm snd_page_alloc snd_hwdep snd_seq_dummy iTCO_wdt iTCO_vendor_support snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event button snd_seq shpchp intel_agp snd_timer snd_seq_device pci_hotplug agpgart snd soundcore ext3 jbd mbcache sg sr_mod sd_mod cdrom ata_generic ata_piix pata_acpi floppy libata ehci_hcd scsi_mod uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[ 1225.629409] 
[ 1225.629413] Pid: 7691, comm: cobrun Tainted: G      D (2.6.24-16-generic #1)
[ 1225.629417] EIP: 0060:[<c017b04c>] EFLAGS: 00010202 CPU: 1
[ 1225.629425] EIP is at exit_mmap+0xec/0xf0
[ 1225.629428] EAX: 00000000 EBX: c18012a0 ECX: 00000019 EDX: c1802cb4
[ 1225.629431] ESI: 00000000 EDI: 00000001 EBP: dc99bf10 ESP: dc99be3c
[ 1225.629435]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[ 1225.629438] Process cobrun (pid: 7691, ti=dc99a000 task=dc847680 task.ti=dc99a000)
[ 1225.629441] Stack: 00000000 dc99be48 00000000 00000000 c18012a0 dc9a1c40 dc847680 0000000b 
[ 1225.629451]        c012a223 00000001 c012fa35 dc847b34 00000000 00000000 0000000a dc847680 
[ 1225.629459]        dc847b14 0000000b 00000000 00000001 dc99be8c eb8f3400 0000000b dc847680 
[ 1225.629468] Call Trace:
[ 1225.629481]  [<c012a223>] mmput+0x23/0x80
[ 1225.629490]  [<c012fa35>] do_exit+0x165/0x850
[ 1225.629505]  [<c0130146>] do_group_exit+0x26/0x80
[ 1225.629512]  [<c0138e97>] get_signal_to_deliver+0x2b7/0x4a0
[ 1225.629526]  [<c0103903>] do_notify_resume+0x93/0x750
[ 1225.629544]  [<c0122696>] __update_rq_clock+0x26/0x170
[ 1225.629552]  [<c010336e>] __switch_to+0x9e/0x150
[ 1225.629562]  [<c0315b5a>] schedule+0x20a/0x600
[ 1225.629568]  [<c03193c4>] do_page_fault+0x2d4/0x730
[ 1225.629580]  [<c0102afc>] sys_execve+0x3c/0x80
[ 1225.629590]  [<c03190f0>] do_page_fault+0x0/0x730
[ 1225.629597]  [<c010451e>] work_notifysig+0x13/0x25
[ 1225.629614]  =======================
[ 1225.629616] Code: 5b 5e 5f c3 8b 03 c7 43 08 00 00 00 00 e8 2d b2 f9 ff 8b 53 04 83 fa ff 74 c6 8d 43 10 e8 ad 56 00 00 c7 43 04 00 00 00 00 eb b5 <0f> 0b eb fe 83 ec 18 89 74 24 0c 89 ce 89 7c 24 10 89 c7 89 6c 
[ 1225.629663] EIP: [<c017b04c>] exit_mmap+0xec/0xf0 SS:ESP 0068:dc99be3c
[ 1225.629673] ---[ end trace 7927f755df2674ec ]---
[ 1225.629676] Fixing recursive fault but reboot is needed!


```


linux-abi version is 3.5

thanks!

---

### Post by bbauman on 2008-07-10
I am having exactly the same problem with a slightly older kernel. Has anyone figured this out?

Thanks.

---

### Post by Rovani on 2008-07-13
I have the same problem too. I don't know it is helped but I discovered that in root works very well but in common user not.

---

### Post by Rovani on 2008-07-13
If somebody has or to find a solution, puts there.

---

### Post by Hotei on 2008-09-30
BUMP!! Anyone come back on this.

I have compiled a vanilla 2.6.23.17 and applied the following patch:

[http://sourceforge.net/tracker/index.php?func=detail&aid=1888895&group_id=13130&atid=313130](http://sourceforge.net/tracker/index.php?func=detail&aid=1888895&group_id=13130&atid=313130)

I can get the modules to load but when I attempt to run the binary...


```

Sep 30 13:15:04 db01 kernel: [ 1667.022461] _proutil[5677]: segfault at 000000d4 eip 000000d4 esp bfffe438 error 4
Sep 30 13:15:04 db01 kernel: [ 1667.022502] ------------[ cut here ]------------
Sep 30 13:15:04 db01 kernel: [ 1667.022538] kernel BUG at mm/mmap.c:2056!
Sep 30 13:15:04 db01 kernel: [ 1667.022568] invalid opcode: 0000 [#1]
Sep 30 13:15:04 db01 kernel: [ 1667.022595] SMP 
Sep 30 13:15:04 db01 kernel: [ 1667.022624] Modules linked in: binfmt_coff abi_sco abi_cxenix abi_svr4 abi_lcall abi_util iptable_filter ip_tables x_tables parport_pc lp parport loop ipv6 cfi_probe gen_probe scb2_flash mtd chipreg psmouse map_funcs button serio_raw shpchp pci_hotplug evdev i2c_piix4 i2c_core sworks_agp agpgart pcspkr ext3 jbd mbcache sd_mod sg sr_mod cdrom ata_generic pata_serverworks qla1280 aic7xxx libata megaraid_mbox scsi_transport_spi megaraid_mm floppy tg3 scsi_mod ohci_hcd usbcore thermal processor fan fuse
Sep 30 13:15:04 db01 kernel: [ 1667.022998] CPU:    0
Sep 30 13:15:04 db01 kernel: [ 1667.022999] EIP:    0060:[exit_mmap+0xe6/0xf0]    Not tainted VLI
Sep 30 13:15:04 db01 kernel: [ 1667.023000] EFLAGS: 00010202   (2.6.23.17-abi #1)
Sep 30 13:15:04 db01 kernel: [ 1667.023099] EIP is at exit_mmap+0xe6/0xf0
Sep 30 13:15:04 db01 kernel: [ 1667.023132] eax: 00000000   ebx: c5013240   ecx: 00000019   edx: c5014300
Sep 30 13:15:04 db01 kernel: [ 1667.023171] esi: 00000000   edi: 00000001   ebp: df017f10   esp: df017e3c
Sep 30 13:15:04 db01 kernel: [ 1667.023208] ds: 007b   es: 007b   fs: 00d8  gs: 0000  ss: 0068
Sep 30 13:15:04 db01 kernel: [ 1667.023247] Process _proutil (pid: 5677, ti=df016000 task=df560b60 task.ti=df016000)
Sep 30 13:15:04 db01 kernel: [ 1667.023287] Stack: 00000000 df017e48 00000000 00000000 c5013240 f7dda380 df560b60 00000001 
Sep 30 13:15:04 db01 kernel: [ 1667.023376]        c012485e 0000000b c0129e54 dd903750 df017f10 00000000 df560b60 df561004 
Sep 30 13:15:04 db01 kernel: [ 1667.023459]        0000000b df017f10 c01309eb 00000000 00000001 ddb20e00 0000000b df560b60 
Sep 30 13:15:04 db01 kernel: [ 1667.023546] Call Trace:
Sep 30 13:15:04 db01 kernel: [ 1667.023604]  [mmput+0x1e/0x80] mmput+0x1e/0x80
Sep 30 13:15:04 db01 kernel: [ 1667.023656]  [do_exit+0x144/0x840] do_exit+0x144/0x840
Sep 30 13:15:04 db01 kernel: [ 1667.023713]  [recalc_sigpending+0xb/0x20] recalc_sigpending+0xb/0x20
Sep 30 13:15:04 db01 kernel: [ 1667.023767]  [do_group_exit+0x26/0x70] do_group_exit+0x26/0x70
Sep 30 13:15:04 db01 kernel: [ 1667.023825]  [get_signal_to_deliver+0x29a/0x470] get_signal_to_deliver+0x29a/0x470
Sep 30 13:15:04 db01 kernel: [ 1667.023898]  [do_notify_resume+0x93/0x720] do_notify_resume+0x93/0x720
Sep 30 13:15:04 db01 kernel: [ 1667.023989]  [sg:printk+0x1b/0x100] printk+0x1b/0x20
Sep 30 13:15:04 db01 kernel: [ 1667.024032]  [do_page_fault+0x119/0x810] do_page_fault+0x119/0x810
Sep 30 13:15:04 db01 kernel: [ 1667.024124]  [do_page_fault+0x0/0x810] do_page_fault+0x0/0x810
Sep 30 13:15:04 db01 kernel: [ 1667.024172]  [work_notifysig+0x13/0x19] work_notifysig+0x13/0x19
Sep 30 13:15:04 db01 kernel: [ 1667.024244]  =======================
Sep 30 13:15:04 db01 kernel: [ 1667.024275] Code: 5b 5e 5f c3 8b 03 c7 43 08 00 00 00 00 e8 63 23 fa ff 8b 53 04 83 fa ff 74 c6 8d 43 10 e8 f3 58 00 00 c7 43 04 00 00 00 00 eb b5 <0f> 0b eb fe 8d b6 00 00 00 00 83 ec 18 89 74 24 0c 89 ce 89 7c 
Sep 30 13:15:04 db01 kernel: [ 1667.024624] EIP: [exit_mmap+0xe6/0xf0] exit_mmap+0xe6/0xf0 SS:ESP 0068:df017e3c
Sep 30 13:15:04 db01 kernel: [ 1667.025118] Fixing recursive fault but reboot is needed!

```

I have it running successfully in 6.06.2 using the linux-source package for 2.6.15.7.

I would really like to get this running on 8.04.

Assistance is appreciated.

---

