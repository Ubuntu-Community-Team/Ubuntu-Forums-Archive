---
title: "IBM Thinkpad T61p wireless problems"
date: 2012-04-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by wwyvern on 2012-04-20
I upgraded from 11.10 a few days ago and didn't have any problems with my wifi at that time, but somehow the last daily update (4/20) has broken my wifi-it will connect to my unsecured cell phone just fine, but will not connect to my home wifi (WPA2) anymore. I installed the wireless-compat package, but it didn't seem to help.
 Here is basic info
  03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Subsystem: Intel Corporation Lenovo ThinkPad T51
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 50
	Region 0: Memory at d7dfe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwl4965
	Kernel modules: iwl4965

 Is this a known bug? It's also kind of weird that it thinks the computer is a T51...it's a T61p.
  If there are any logs I can pull that would help, please let me know and I'll get them.
 Heres what I got with modinfo iwl4965

filename:       /lib/modules/3.2.0-23-generic/updates/cw-3.3/iwl4965.ko
firmware:       iwlwifi-4965-2.ucode
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi 4965 driver for Linux
srcversion:     8A2AECA700F560BA7CE73B4
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlegacy,cfg80211,mac80211
vermagic:       3.2.0-23-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)

---

