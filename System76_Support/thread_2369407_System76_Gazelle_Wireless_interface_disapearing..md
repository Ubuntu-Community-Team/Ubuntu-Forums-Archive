---
title: "System76 Gazelle Wireless interface disapearing."
date: 2017-08-22
forum: System76 Support
---

### Post by mattyshires on 2017-08-22
I'm having an issue where my wireless interface keeps disappearing at random, when this happens it no longer shows up in "ifconfig -a":

```
matty@Gazelle:~$ ifconfig -a
enp2s0f1  Link encap:Ethernet  HWaddr 80:fa:5b:32:ae:c1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4900 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4900 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:501300 (501.3 KB)  TX bytes:501300 (501.3 KB)
```

It only reappears when I run "sudo modprobe -r iwlwifi ; sudo modprobe iwlwifi"

```
matty@Gazelle:~$ ifconfig -a
enp2s0f1  Link encap:Ethernet  HWaddr 80:fa:5b:32:ae:c1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:17157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1197465 (1.1 MB)  TX bytes:1197465 (1.1 MB)

wlp3s0    Link encap:Ethernet  HWaddr ac:2b:6e:07:15:b6  
          inet addr:192.168.0.113  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::18e:1283:f85:ab5b/64 Scope:Link
          inet6 addr: fe80::77d:56ea:3802:c296/64 Scope:Link
          inet6 addr: fe80::40c2:799d:b888:f83e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:342043 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66896 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:495391918 (495.3 MB)  TX bytes:7801554 (7.8 MB)


```

lspci:
```
00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Skylake Integrated Graphics (rev 06)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Sunrise Point-H SATA Controller [AHCI mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #1 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #5 (rev f1)
00:1c.6 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #7 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5287 (rev 01)
02:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
03:00.0 Network controller: Intel Corporation Wireless 3165 (rev 81)
```

This error appeared in dmesg:
```
[  345.929204] WARNING: CPU: 2 PID: 465 at /build/linux-hVVhWi/linux-4.4.0/net/mac80211/driver-ops.c:39 drv_stop+0xfe/0x110 [mac80211]()
[  345.929206] Modules linked in: rfcomm cmac pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) ctr ccm snd_hrtimer ec_sys bnep binfmt_misc uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common videodev media arc4 iwlmvm mac80211 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic btusb btrtl tpm_crb snd_hda_intel intel_rapl snd_hda_codec snd_hda_core snd_hwdep wl(POE) x86_pkg_temp_thermal snd_pcm intel_powerclamp snd_seq_midi snd_seq_midi_event coretemp iwlwifi snd_rawmidi snd_seq snd_seq_device kvm_intel snd_timer snd soundcore kvm cfg80211 mei_me mei hci_uart joydev input_leds serio_raw rtsx_pci_ms irqbypass btbcm memstick btqca btintel shpchp bluetooth intel_lpss_acpi acpi_pad intel_lpss mac_hid parport_pc ppdev lp parport autofs4 drbg ansi_cprng
[  345.929253]  algif_skcipher af_alg dm_crypt hid_generic usbhid rtsx_pci_sdmmc crct10dif_pclmul crc32_pclmul ghash_clmulni_intel i915_bpo aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd intel_ips i2c_algo_bit drm_kms_helper syscopyarea psmouse sysfillrect sysimgblt fb_sys_fops r8169 drm ahci rtsx_pci mii libahci wmi pinctrl_sunrisepoint i2c_hid video pinctrl_intel hid fjes
[  345.929280] CPU: 2 PID: 465 Comm: kworker/2:2 Tainted: P        W  OE   4.4.0-92-generic #115-Ubuntu
[  345.929281] Hardware name: System76, Inc. Gazelle/Gazelle, BIOS 1.05.08 03/31/2016
[  345.929297] Workqueue: events_freezable ieee80211_restart_work [mac80211]
[  345.929301]  0000000000000286 37706384c3ea418c ffff880266ccbb78 ffffffff813f9c83
[  345.929304]  0000000000000000 ffffffffc0e1a500 ffff880266ccbbb0 ffffffff81081312
[  345.929307]  ffff880265588700 ffff880265588700 0000000000000000 ffff880265588e90
[  345.929311] Call Trace:
[  345.929314]  [<ffffffff813f9c83>] dump_stack+0x63/0x90
[  345.929318]  [<ffffffff81081312>] warn_slowpath_common+0x82/0xc0
[  345.929321]  [<ffffffff8108145a>] warn_slowpath_null+0x1a/0x20
[  345.929337]  [<ffffffffc0da799e>] drv_stop+0xfe/0x110 [mac80211]
[  345.929356]  [<ffffffffc0dd8ab3>] ieee80211_stop_device+0x43/0x50 [mac80211]
[  345.929375]  [<ffffffffc0dbbf2f>] ieee80211_do_stop+0x4cf/0x810 [mac80211]
[  345.929379]  [<ffffffff81841b2e>] ? _raw_spin_unlock_bh+0x1e/0x20
[  345.929383]  [<ffffffff8175e7ba>] ? dev_deactivate_many+0x20a/0x240
[  345.929402]  [<ffffffffc0dbc28a>] ieee80211_stop+0x1a/0x20 [mac80211]
[  345.929407]  [<ffffffff817309c9>] __dev_close_many+0x99/0x100
[  345.929410]  [<ffffffff81730ac1>] dev_close_many+0x91/0x140
[  345.929414]  [<ffffffff81732d6a>] dev_close.part.78+0x4a/0x70
[  345.929418]  [<ffffffff81732daa>] dev_close+0x1a/0x20
[  345.929452]  [<ffffffffc04efac1>] cfg80211_shutdown_all_interfaces+0x41/0xa0 [cfg80211]
[  345.929475]  [<ffffffffc0dd6438>] ieee80211_handle_reconfig_failure+0x98/0xb0 [mac80211]
[  345.929506]  [<ffffffffc0dd8ca8>] ieee80211_reconfig+0x1e8/0xf80 [mac80211]
[  345.929510]  [<ffffffff8183fe32>] ? mutex_lock+0x12/0x30
[  345.929525]  [<ffffffffc0da41eb>] ieee80211_restart_work+0x6b/0xa0 [mac80211]
[  345.929529]  [<ffffffff8109a625>] process_one_work+0x165/0x480
[  345.929532]  [<ffffffff8109a98b>] worker_thread+0x4b/0x4c0
[  345.929536]  [<ffffffff8109a940>] ? process_one_work+0x480/0x480
[  345.929538]  [<ffffffff810a0cc5>] kthread+0xe5/0x100
[  345.929541]  [<ffffffff810a0be0>] ? kthread_create_on_node+0x1e0/0x1e0
[  345.929545]  [<ffffffff8184238f>] ret_from_fork+0x3f/0x70
[  345.929548]  [<ffffffff810a0be0>] ? kthread_create_on_node+0x1e0/0x1e0
[  345.929569] ---[ end trace ec414bb43e6cf972 ]---
[  346.017675] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  346.024179] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-19.ucode failed with error -2
[  346.024208] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-18.ucode failed with error -2
[  346.025794] iwlwifi 0000:03:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
[  346.025839] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[  346.025921] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  346.026102] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  346.250936] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x2000000.
[  346.250941] iwlwifi 0000:03:00.0: CSR values:
[  346.250943] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[  346.250957] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c89200
[  346.250971] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[  346.250982] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[  346.250993] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[  346.251003] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[  346.251014] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[  346.251024] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[  346.251035] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[  346.251046] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X00000210
[  346.251057] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0Xd55555d5
[  346.251067] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X00000000
[  346.251078] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0Xd55555d5
[  346.251089] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080042
[  346.251099] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[  346.251110] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[  346.251121] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[  346.251131] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[  346.251142] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[  346.251152] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X880351ae
[  346.251163] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[  346.251174] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[  346.251184] iwlwifi 0000:03:00.0:      CSR_MONITOR_STATUS_REG: 0Xd3b7ff57
[  346.251195] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[  346.251205] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[  346.251207] iwlwifi 0000:03:00.0: FH register values:
[  346.251228] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X265d7d00
[  346.251240] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0265cbf0
[  346.251252] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000010
[  346.251263] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00801114
[  346.251275] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[  346.251287] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X03030000
[  346.251299] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[  346.251310] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[  346.251322] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[  346.251428] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[  346.251430] iwlwifi 0000:03:00.0: Status: 0x00000000, count: 6
[  346.251432] iwlwifi 0000:03:00.0: Loaded firmware version: 17.352738.0
[  346.251434] iwlwifi 0000:03:00.0: 0x00000034 | NMI_INTERRUPT_WDG           
[  346.251436] iwlwifi 0000:03:00.0: 0x000002F0 | uPc
[  346.251438] iwlwifi 0000:03:00.0: 0x00000000 | branchlink1
[  346.251439] iwlwifi 0000:03:00.0: 0x00040312 | branchlink2
[  346.251441] iwlwifi 0000:03:00.0: 0x00040BEC | interruptlink1
[  346.251442] iwlwifi 0000:03:00.0: 0x0000572A | interruptlink2
[  346.251444] iwlwifi 0000:03:00.0: 0x00000000 | data1
[  346.251445] iwlwifi 0000:03:00.0: 0x00000002 | data2
[  346.251447] iwlwifi 0000:03:00.0: 0x07030000 | data3
[  346.251449] iwlwifi 0000:03:00.0: 0x003CADA9 | beacon time
[  346.251450] iwlwifi 0000:03:00.0: 0x00035255 | tsf low
[  346.251452] iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
[  346.251453] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[  346.251455] iwlwifi 0000:03:00.0: 0x00035256 | time gp2
[  346.251457] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[  346.251458] iwlwifi 0000:03:00.0: 0x00000011 | uCode version major
[  346.251460] iwlwifi 0000:03:00.0: 0x000561E2 | uCode version minor
[  346.251461] iwlwifi 0000:03:00.0: 0x00000210 | hw version
[  346.251463] iwlwifi 0000:03:00.0: 0x00C89200 | board version
[  346.251464] iwlwifi 0000:03:00.0: 0x0912006A | hcmd
[  346.251466] iwlwifi 0000:03:00.0: 0x00023080 | isr0
[  346.251468] iwlwifi 0000:03:00.0: 0x00000000 | isr1
[  346.251469] iwlwifi 0000:03:00.0: 0x00000002 | isr2
[  346.251471] iwlwifi 0000:03:00.0: 0x404000C0 | isr3
[  346.251472] iwlwifi 0000:03:00.0: 0x00000080 | isr4
[  346.251474] iwlwifi 0000:03:00.0: 0x01800112 | isr_pref
[  346.251475] iwlwifi 0000:03:00.0: 0x00000000 | wait_event
[  346.251477] iwlwifi 0000:03:00.0: 0x00004288 | l2p_control
[  346.251478] iwlwifi 0000:03:00.0: 0x00000000 | l2p_duration
[  346.251480] iwlwifi 0000:03:00.0: 0x00000000 | l2p_mhvalid
[  346.251481] iwlwifi 0000:03:00.0: 0x00000000 | l2p_addr_match
[  346.251483] iwlwifi 0000:03:00.0: 0x00000007 | lmpm_pmg_sel
[  346.251484] iwlwifi 0000:03:00.0: 0x15061440 | timestamp
[  346.251486] iwlwifi 0000:03:00.0: 0x00341020 | flow_handler
[  346.251658] iwlwifi 0000:03:00.0: Failed to run INIT ucode: -5
[  346.251695] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled

```

---

### Post by april-system76 on 2017-08-23
It looks like the hardware itself has failed. We've set up a replacement ticket for you, check your email!

---

