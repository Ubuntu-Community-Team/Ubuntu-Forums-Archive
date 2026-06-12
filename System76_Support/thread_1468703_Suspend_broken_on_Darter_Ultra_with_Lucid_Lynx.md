---
title: "Suspend broken on Darter Ultra with Lucid Lynx"
date: 2010-05-01
forum: System76 Support
---

### Post by peterih on 2010-05-01
After upgrading my Darter Ultra to Lucid Lynx Suspend does not kick in when I closed the lid. I get no errors and the system just continues when opening again.

First I upgradede via update manager, and later I did a clean install from CD, installed the system76 drivers and did a "Restore system".

---

### Post by haydnv on 2010-05-02
FWIW, Lucid also breaks suspend on my SERP3 - here's (I think) the relevant kern.log:

> 
main kernel: [99371.053066] PM: Preparing system for mem sleep
main kernel: [99371.053072] Freezing user space processes ... (elapsed 0.00 seconds) done.
main kernel: [99371.053881] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
main kernel: [99371.053924] PM: Entering mem sleep
main kernel: [99371.053934] Suspending console(s) (use no_console_suspend to debug)
main kernel: [99371.100112] sd 2:0:0:0: [sda] Synchronizing SCSI cache
main kernel: [99371.100350] sd 2:0:0:0: [sda] Stopping disk
main kernel: [99371.602174] PM: suspend of drv:sd dev:2:0:0:0 complete after 502.062 msecs
main kernel: [99372.021281] PM: suspend of drv:psmouse dev:serio1 complete after 405.057 msecs
main kernel: [99372.124086] PM: suspend of drv:atkbd dev:serio0 complete after 102.797 msecs
main kernel: [99372.128392] tpm_inf_pnp 00:08: saving TPM state
main kernel: [99372.147493] tpm_inf_pnp 00:08: Timeout while clearing FIFO
main kernel: [99372.147495] tpm_inf_pnp 00:08: error while saving TPM state
main kernel: [99372.147501] device_suspend(): pnp_bus_suspend+0x0/0x70 returns -5
main kernel: [99372.147506] PM: Device 00:08 failed to suspend: error -5
main kernel: [99372.147507] PM: Some devices failed to suspend
main kernel: [99372.322675] sd 2:0:0:0: [sda] Starting disk
main kernel: [99373.349872] PM: resume of drv:sd dev:2:0:0:0 complete after 1027.196 msecs
main kernel: [99373.484421] PM: resume of devices complete after 1336.904 msecs
main kernel: [99373.484569] PM: resume devices took 1.340 seconds
main kernel: [99373.484583] PM: Finishing wakeup.
main kernel: [99373.484584] Restarting tasks ... done.


Does anyone know how I can figure out what device 00:08 is?

---

### Post by thomasaaron on 2010-05-03
haydnv, you really should start a separate post on that. The SerP3 is quite a bit different than the Darter Ultra series, and it's not likely the fixes will be the same.

peterih, If you have a Darter Ultra 3, please go to System > Administration > Software Sources and click the Updates tab. Then, enable the repos that say "proposed" and "backports". Then run updates and reboot.

---

### Post by peterih on 2010-05-03
This seems to work. Thanks! Will I have to continue using backports and proposed? It changes a lot of other stuff which I'm not sure I like.

---

### Post by isantop on 2010-05-04
Once you donwload and install any updates from proposed and Backports, you should be able to disable them and keep any updates without continuing to recieve updates from those repos. Thanks to apt-get's versioning system, the only packages which get installed have a higher version than the existing one, which will be true for backports and proposed 99% of the time.

---

### Post by yavoh on 2010-06-17
Updating while allowing backports and proposed updates fixed the problem for a while, but now it's back.  I tried looking in `lspci` but it's not listed there.  Any other ideas?

---

### Post by isantop on 2010-06-17
Does it ever fail on the first suspend after a reboot? Or is it only after multiple consecutive Suspend/Resume Cycles?

---

### Post by yavoh on 2010-06-17
The first suspend after a reboot does not fail; all subsequent suspends/hibernates fail.

---

### Post by isantop on 2010-06-17
Please open up a terminal (Applications > Accessories > Terminal) and run:

tail -f /var/log/syslog

Please take note of the last line to be output there.

Then, try and suspend your system. Make sure it fails. Post the output from that command here.

---

### Post by yavoh on 2010-06-17
```
Jun 17 22:27:11 anish-desktop-ubuntu NetworkManager: <info>  Sleeping...
Jun 17 22:27:11 anish-desktop-ubuntu NetworkManager: <info>  (eth0): now unmanaged
Jun 17 22:27:11 anish-desktop-ubuntu NetworkManager: <info>  (eth0): device state change: 8 -> 1 (reason 37)
Jun 17 22:27:11 anish-desktop-ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 37).
Jun 17 22:27:12 anish-desktop-ubuntu NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 22111
Jun 17 22:27:12 anish-desktop-ubuntu NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Jun 17 22:27:12 anish-desktop-ubuntu avahi-daemon[987]: Withdrawing address record for 192.168.10.199 on eth0.
Jun 17 22:27:12 anish-desktop-ubuntu avahi-daemon[987]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.10.199.
Jun 17 22:27:12 anish-desktop-ubuntu avahi-daemon[987]: Interface eth0.IPv4 no longer relevant for mDNS.
Jun 17 22:27:12 anish-desktop-ubuntu NetworkManager: <info>  (eth0): cleaning up...
Jun 17 22:27:12 anish-desktop-ubuntu NetworkManager: <info>  (eth0): taking down device.
Jun 17 22:27:12 anish-desktop-ubuntu vmnetBridge: Removing interface eth0 index:2
Jun 17 22:27:12 anish-desktop-ubuntu avahi-daemon[987]: Withdrawing address record for fe80::21f:d0ff:fe81:6a49 on eth0.
Jun 17 22:27:12 anish-desktop-ubuntu kernel: [ 8907.875167] bridge-eth0: disabling the bridge on dev down
Jun 17 22:27:12 anish-desktop-ubuntu vmnetBridge: Stopped bridge eth0 to virtual network 0.
Jun 17 22:27:12 anish-desktop-ubuntu NetworkManager: <info>  (eth0): carrier now OFF (device state 1)
Jun 17 22:27:12 anish-desktop-ubuntu kernel: [ 8907.951276] bridge-eth0: down
Jun 17 22:27:12 anish-desktop-ubuntu kernel: [ 8907.951300] bridge-eth0: detached
Jun 17 22:27:12 anish-desktop-ubuntu postfix/master[1689]: reload -- version 2.7.0, configuration /etc/postfix
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8912.761426] PM: Syncing filesystems ... done.
Jun 17 22:27:38 anish-desktop-ubuntu rtkit-daemon[1447]: The canary thread is apparently starving. Taking action.
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8913.091266] PM: Preparing system for mem sleep
Jun 17 22:27:38 anish-desktop-ubuntu rtkit-daemon[1447]: Demoting known real-time threads.
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8913.091270] Freezing user space processes ... (elapsed 0.00 seconds) done.
Jun 17 22:27:38 anish-desktop-ubuntu rtkit-daemon[1447]: Successfully demoted thread 2142 of process 2109 (n/a).
Jun 17 22:27:38 anish-desktop-ubuntu rtkit-daemon[1447]: Successfully demoted thread 2141 of process 2109 (n/a).
Jun 17 22:27:38 anish-desktop-ubuntu rtkit-daemon[1447]: Successfully demoted thread 2109 of process 2109 (n/a).
Jun 17 22:27:38 anish-desktop-ubuntu rtkit-daemon[1447]: Demoted 3 threads.
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8913.092236] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8913.092286] PM: Entering mem sleep
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8913.092295] Suspending console(s) (use no_console_suspend to debug)
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8913.092681] sd 4:0:0:0: [sdd] Synchronizing SCSI cache
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8913.092830] sd 4:0:0:0: [sdd] Stopping disk
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8913.589775] PM: suspend of drv:sd dev:4:0:0:0 complete after 497.092 msecs
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8913.610061] sd 3:0:0:0: [sdc] Synchronizing SCSI cache
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8913.610777] sd 3:0:0:0: [sdc] Stopping disk
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8913.773572] PM: suspend of drv:sd dev:3:0:0:0 complete after 163.512 msecs
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8913.773587] sd 1:0:1:0: [sdb] Synchronizing SCSI cache
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8913.773776] sd 1:0:1:0: [sdb] Stopping disk
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8914.288761] PM: suspend of drv:sd dev:1:0:1:0 complete after 515.175 msecs
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8914.288775] sd 0:0:1:0: [sda] Synchronizing SCSI cache
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8914.288914] sd 0:0:1:0: [sda] Stopping disk
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8914.820817] PM: suspend of drv:sd dev:0:0:1:0 complete after 532.043 msecs
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8914.840376] ACPI handle has no context!
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8914.840381] tpm_inf_pnp 00:09: saving TPM state
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8914.853925] tpm_inf_pnp 00:09: Timeout while clearing FIFO
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8914.853926] tpm_inf_pnp 00:09: error while saving TPM state
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8914.853932] device_suspend(): pnp_bus_suspend+0x0/0x90 returns -5
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8914.853934] PM: Device 00:09 failed to suspend: error -5
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8914.853935] PM: Some devices failed to suspend
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8915.126039] sd 0:0:1:0: [sda] Starting disk
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8917.417646] PM: resume of drv:sd dev:0:0:1:0 complete after 2291.607 msecs
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8917.417656] sd 1:0:1:0: [sdb] Starting disk
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8922.138782] PM: resume of drv:sd dev:1:0:1:0 complete after 4721.125 msecs
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8922.138792] sd 3:0:0:0: [sdc] Starting disk
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8927.070328] PM: resume of drv:sd dev:3:0:0:0 complete after 4931.534 msecs
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8927.136209] input input4: event field not found
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8927.136211] input input4: event field not found
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8927.136213] input input4: event field not found
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8927.136214] input input4: event field not found
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8927.136216] input input4: event field not found
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8927.136217] input input4: event field not found
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8927.136219] input input4: event field not found
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8927.136231] sd 4:0:0:0: [sdd] Starting disk
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551020] PM: resume of drv:sd dev:4:0:0:0 complete after 7414.788 msecs
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551141] PM: resume of devices complete after 19697.198 msecs
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551337] PM: resume devices took 19.700 seconds
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551338] ------------[ cut here ]------------
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551342] WARNING: at /build/buildd/linux-2.6.32/kernel/power/suspend_test.c:53 suspend_test_finish+0x88/0x90()
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551344] Hardware name: EP45-UD3P
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551345] Component: resume devices, time: 19700
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551346] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat usb_storage xt_multiport iptable_filter ip_tables x_tables binfmt_misc vmnet vmblock vsock vmci vmmon quota_v2 quota_tree snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd ppdev psmouse soundcore fbcon tileblit font bitblit softcursor parport_pc tpm_infineon tpm snd_page_alloc tpm_bios serio_raw nvidia(P) vga16fb vgastate coretemp intel_agp it87 hwmon_vid lp parport ohci1394 r8169 usbhid ieee1394 mii hid pata_jmicron ahci
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551377] Pid: 22581, comm: pm-suspend Tainted: P        W  2.6.32-22-generic #36-Ubuntu
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551378] Call Trace:
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551382]  [<ffffffff81066d0b>] warn_slowpath_common+0x7b/0xc0
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551384]  [<ffffffff81066db1>] warn_slowpath_fmt+0x41/0x50
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551387]  [<ffffffff810a3238>] suspend_test_finish+0x88/0x90
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551389]  [<ffffffff810a2fe1>] suspend_devices_and_enter+0xb1/0xe0
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551391]  [<ffffffff810a30e8>] enter_state+0xd8/0x110
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551394]  [<ffffffff810a268a>] state_store+0x9a/0x100
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551396]  [<ffffffff812b32b7>] kobj_attr_store+0x17/0x20
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551400]  [<ffffffff811ace45>] sysfs_write_file+0xe5/0x170
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551402]  [<ffffffff81142a08>] vfs_write+0xb8/0x1a0
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551405]  [<ffffffff81543898>] ? do_page_fault+0x158/0x3b0
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551408]  [<ffffffff811432a1>] sys_write+0x51/0x80
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551411]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551412] ---[ end trace 2d2c0baadf273191 ]---
Jun 17 22:27:38 anish-desktop-ubuntu kernel: [ 8934.551431] PM: Finishing wakeup.

```

---

