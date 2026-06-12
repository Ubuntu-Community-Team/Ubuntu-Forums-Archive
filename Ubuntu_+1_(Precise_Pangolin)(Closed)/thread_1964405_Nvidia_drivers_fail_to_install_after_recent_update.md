---
title: "Nvidia drivers fail to install after recent update"
date: 2012-04-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Russty of Oz on 2012-04-23
Since an update a couple of weeks back I haven't been able to activate the Nvidia drivers.  They used to work but now they don't and when I try to activate them it tries to download and install but I get an error message saying the install failed.  It say to check the log file but this makes no sense to me, can anyone suggest what is wrong?  

Russty

(I tried to copy and paste the log file which is quite long but I was then told I had 84 images in my message.):confused:

---

### Post by Harry33 on 2012-04-24
> **Russty of Oz said:**
> Since an update a couple of weeks back I haven't been able to activate the Nvidia drivers.  They used to work but now they don't and when I try to activate them it tries to download and install but I get an error message saying the install failed.  It say to check the log file but this makes no sense to me, can anyone suggest what is wrong?  

Russty

(I tried to copy and paste the log file which is quite long but I was then told I had 84 images in my message.):confused:

Could you please give us some more info.
Which troublesome update are you talking about (which packages)?
Are you using any extra PPA's or only official Precise ones?
What Nvidia driver are you using?

Have you tried to purge (completely remove) nvidia drivers first, then install it again?

---

### Post by Russty of Oz on 2012-04-24
I am not sure which update it was, all I can remember is that there were a lot of updates that day and it required a restart.

The only PPA I can find is for Launchpad.net/elementaryart/.....

Yes, I have removed the Nvidia driver and tried again but with no success. 

Is there some way I can post the log file?

---

### Post by arpanaut on 2012-04-24
> Is there some way I can post the log file?
Did you try to post the contents of the log file within code tags or just attach as a text file?
You would need to go to the Advanced Editor mode to accomplish that.

---

### Post by Russty of Oz on 2012-04-24
Ok, I will try posting the log file this way:
[HTML]2012-04-23 16:14:24,794 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c>
2012-04-23 16:14:26,160 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic-pae/modules.alias
2012-04-23 16:14:26,239 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-23 16:14:26,239 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-23 16:14:26,274 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-23 16:14:26,288 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-23 16:14:26,297 DEBUG: Software modem not available
2012-04-23 16:14:26,297 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-23 16:14:26,302 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-23 16:14:26,322 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-23 16:14:26,322 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-23 16:14:26,322 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-23 16:14:26,329 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-23 16:14:26,330 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-23 16:14:26,347 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-23 16:14:26,348 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-23 16:14:26,353 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-23 16:14:26,354 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-23 16:14:26,354 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-23 16:14:26,354 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-23 16:14:26,377 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-23 16:14:26,378 DEBUG: Firmware for DVB cards not available
2012-04-23 16:14:26,378 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-23 16:14:26,386 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-23 16:14:26,391 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-23 16:14:26,393 DEBUG: nvidia.available: falling back to default
2012-04-23 16:14:26,452 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-23 16:14:26,452 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-23 16:14:26,455 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-23 16:14:26,458 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-23 16:14:26,459 DEBUG: nvidia.available: falling back to default
2012-04-23 16:14:26,493 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-23 16:14:26,497 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-23 16:14:26,502 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-23 16:14:26,503 DEBUG: nvidia.available: falling back to default
2012-04-23 16:14:26,539 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-23 16:14:26,544 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-23 16:14:26,549 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-23 16:14:26,550 DEBUG: nvidia.available: falling back to default
2012-04-23 16:14:26,569 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-23 16:14:26,569 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-23 16:14:26,573 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-23 16:14:26,578 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-23 16:14:26,579 DEBUG: nvidia.available: falling back to default
2012-04-23 16:14:26,597 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-23 16:14:26,597 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-23 16:14:26,601 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-23 16:14:26,606 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-23 16:14:26,607 DEBUG: nvidia.available: falling back to default
2012-04-23 16:14:26,625 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-23 16:14:26,625 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-23 16:14:26,625 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-23 16:14:26,631 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-04-23 16:14:26,636 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-23 16:14:26,637 DEBUG: fglrx.available: falling back to default
2012-04-23 16:14:26,673 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-23 16:14:26,677 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-23 16:14:26,682 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-23 16:14:26,682 DEBUG: fglrx.available: falling back to default
2012-04-23 16:14:26,718 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-23 16:14:26,719 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-04-23 16:14:26,725 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-04-23 16:14:26,730 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-04-23 16:14:26,764 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-04-23 16:14:26,764 DEBUG: all custom handlers loaded
2012-04-23 16:14:26,764 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'pci:v00008086d000027D8sv00001043sd00008415bc04sc03i00')
2012-04-23 16:14:26,989 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-23 16:14:27,049 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,049 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-23 16:14:27,049 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,049 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-04-23 16:14:27,053 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-23 16:14:27,053 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,053 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-23 16:14:27,053 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-23 16:14:27,053 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd000083A3bc02sc00i00')
2012-04-23 16:14:27,060 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-04-23 16:14:27,060 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2012-04-23 16:14:27,060 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-23 16:14:27,060 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,060 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-23 16:14:27,060 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'platform:pcspkr')
2012-04-23 16:14:27,061 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-23 16:14:27,061 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,061 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-23 16:14:27,061 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,061 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-23 16:14:27,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-23 16:14:27,072 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-23 16:14:27,072 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,072 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-23 16:14:27,072 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-23 16:14:27,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'platform:eisa')
2012-04-23 16:14:27,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'pci:v000014F1d00008800sv0000107Dsd0000665Fbc04sc00i00')
2012-04-23 16:14:27,075 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'cx8800'}
2012-04-23 16:14:27,075 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'cx8800', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-23 16:14:27,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'pci:v000010DEd00000A20sv00001462sd00008051bc03sc00i00')
2012-04-23 16:14:27,262 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2012-04-23 16:14:27,272 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:14:27,272 DEBUG: KMH enabled: False
2012-04-23 16:14:27,263 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-04-23 16:14:27,275 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-23 16:14:27,279 DEBUG: nvidia.available: falling back to default
2012-04-23 16:14:27,307 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:14:27,307 DEBUG: KMH enabled: False
2012-04-23 16:14:27,292 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-04-23 16:14:27,307 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2012-04-23 16:14:27,323 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:14:27,323 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-23 16:14:27,307 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-04-23 16:14:27,328 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-23 16:14:27,334 DEBUG: nvidia.available: falling back to default
2012-04-23 16:14:27,369 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:14:27,369 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-23 16:14:27,353 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-04-23 16:14:27,369 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2012-04-23 16:14:27,369 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,369 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2012-04-23 16:14:27,370 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,370 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-23 16:14:27,370 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-23 16:14:27,370 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'pci:v00008086d00002E30sv00001043sd0000836Dbc06sc00i00')
2012-04-23 16:14:27,375 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'acpi:PNP0401:')
2012-04-23 16:14:27,375 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'pci:v00008086d000027C9sv00001043sd00008179bc0Csc03i00')
2012-04-23 16:14:27,379 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-23 16:14:27,379 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-23 16:14:27,379 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-23 16:14:27,380 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'pci:v00008086d000027CBsv00001043sd00008179bc0Csc03i00')
2012-04-23 16:14:27,383 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-04-23 16:14:27,390 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-23 16:14:27,390 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,390 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'pci:v00008086d000027C0sv00001043sd00008179bc01sc01i8f')
2012-04-23 16:14:27,392 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-23 16:14:27,392 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-23 16:14:27,392 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,392 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,l0,1,2,3,4,sfw')
2012-04-23 16:14:27,393 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-23 16:14:27,393 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,393 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-23 16:14:27,393 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,393 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-23 16:14:27,393 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,393 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-04-23 16:14:27,393 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-23 16:14:27,393 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,393 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'pci:v00008086d000027CAsv00001043sd00008179bc0Csc03i00')
2012-04-23 16:14:27,396 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0402:bd01/21/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5G41C-MLX:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-04-23 16:14:27,407 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-23 16:14:27,407 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-23 16:14:27,407 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-23 16:14:27,408 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,408 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2012-04-23 16:14:27,428 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-04-23 16:14:27,428 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,428 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-04-23 16:14:27,428 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,428 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2012-04-23 16:14:27,428 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-04-23 16:14:27,428 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,428 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-04-23 16:14:27,429 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,429 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-23 16:14:27,429 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'acpi:PNP0501:')
2012-04-23 16:14:27,429 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'pci:v00008086d000027DFsv00001043sd00008179bc01sc01i8a')
2012-04-23 16:14:27,431 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'pci:v00008086d000027C8sv00001043sd00008179bc0Csc03i00')
2012-04-23 16:14:27,433 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'pci:v00008086d000027B8sv00001043sd00008179bc06sc01i00')
2012-04-23 16:14:27,435 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng'}
2012-04-23 16:14:27,435 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,436 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-04-23 16:14:27,436 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,436 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'leds_ss4200'}
2012-04-23 16:14:27,436 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'leds_ss4200', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,436 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'pci:v00008086d000027CCsv00001043sd00008179bc0Csc03i20')
2012-04-23 16:14:27,438 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'pci:v000010DEd00000BE2sv00001462sd00008051bc04sc03i00')
2012-04-23 16:14:27,440 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-23 16:14:27,440 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-23 16:14:27,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2012-04-23 16:14:27,441 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-04-23 16:14:27,441 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,441 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd00008179bc06sc04i01')
2012-04-23 16:14:27,443 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-23 16:14:27,443 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-23 16:14:27,444 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,444 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-23 16:14:27,444 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,444 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'pci:v000014F1d00008802sv0000107Dsd0000665Fbc04sc80i00')
2012-04-23 16:14:27,444 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'cx8802'}
2012-04-23 16:14:27,444 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'cx8802', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,444 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-04-23 16:14:27,444 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-23 16:14:27,444 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,444 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'input:b0001v107Dp665Fe0001-e0,1,4,14,k71,72,73,80,8B,8E,A4,A7,A8,D0,D4,DF,163,164,166,167,16B,170,172,174,175,179,17A,181,182,184,185,188,189,18E,18F,190,191,192,193,195,197,19C,ram4,lsfw')
2012-04-23 16:14:27,444 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-23 16:14:27,445 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,445 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-23 16:14:27,445 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-23 16:14:27,445 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7246d0c> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-23 16:14:27,445 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'pci:v00008086d000027D8sv00001043sd00008415bc04sc03i00')
2012-04-23 16:14:27,445 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-04-23 16:14:27,445 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-23 16:14:27,445 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-23 16:14:27,445 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd000083A3bc02sc00i00')
2012-04-23 16:14:27,445 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2012-04-23 16:14:27,445 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'platform:pcspkr')
2012-04-23 16:14:27,445 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-23 16:14:27,445 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-23 16:14:27,445 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-23 16:14:27,445 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'platform:eisa')
2012-04-23 16:14:27,445 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'pci:v000014F1d00008800sv0000107Dsd0000665Fbc04sc00i00')
2012-04-23 16:14:27,445 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-23 16:14:27,446 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'pci:v000010DEd00000A20sv00001462sd00008051bc03sc00i00')
2012-04-23 16:14:27,446 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-23 16:14:27,446 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-23 16:14:27,446 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'pci:v00008086d00002E30sv00001043sd0000836Dbc06sc00i00')
2012-04-23 16:14:27,446 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'acpi:PNP0401:')
2012-04-23 16:14:27,446 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'pci:v00008086d000027C9sv00001043sd00008179bc0Csc03i00')
2012-04-23 16:14:27,446 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-23 16:14:27,446 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-23 16:14:27,446 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-23 16:14:27,446 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'pci:v00008086d000027CBsv00001043sd00008179bc0Csc03i00')
2012-04-23 16:14:27,446 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-04-23 16:14:27,446 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'pci:v00008086d000027C0sv00001043sd00008179bc01sc01i8f')
2012-04-23 16:14:27,446 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-23 16:14:27,446 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,l0,1,2,3,4,sfw')
2012-04-23 16:14:27,446 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-04-23 16:14:27,446 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'pci:v00008086d000027CAsv00001043sd00008179bc0Csc03i00')
2012-04-23 16:14:27,446 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0402:bd01/21/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5G41C-MLX:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-04-23 16:14:27,446 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-23 16:14:27,447 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-23 16:14:27,447 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2012-04-23 16:14:27,447 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2012-04-23 16:14:27,447 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-23 16:14:27,447 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'acpi:PNP0501:')
2012-04-23 16:14:27,447 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'pci:v00008086d000027DFsv00001043sd00008179bc01sc01i8a')
2012-04-23 16:14:27,447 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'pci:v00008086d000027C8sv00001043sd00008179bc0Csc03i00')
2012-04-23 16:14:27,447 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'pci:v00008086d000027B8sv00001043sd00008179bc06sc01i00')
2012-04-23 16:14:27,447 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'pci:v00008086d000027CCsv00001043sd00008179bc0Csc03i20')
2012-04-23 16:14:27,447 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'pci:v000010DEd00000BE2sv00001462sd00008051bc04sc03i00')
2012-04-23 16:14:27,447 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-23 16:14:27,447 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2012-04-23 16:14:27,447 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd00008179bc06sc04i01')
2012-04-23 16:14:27,447 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-23 16:14:27,447 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'pci:v000014F1d00008802sv0000107Dsd0000665Fbc04sc80i00')
2012-04-23 16:14:27,447 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-04-23 16:14:27,447 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'input:b0001v107Dp665Fe0001-e0,1,4,14,k71,72,73,80,8B,8E,A4,A7,A8,D0,D4,DF,163,164,166,167,16B,170,172,174,175,179,17A,181,182,184,185,188,189,18E,18F,190,191,192,193,195,197,19C,ram4,lsfw')
2012-04-23 16:14:27,448 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694184c> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-23 16:14:27,502 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:14:27,503 DEBUG: KMH enabled: False
2012-04-23 16:14:28,316 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:14:28,317 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-23 16:14:29,111 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:14:29,111 DEBUG: KMH enabled: False
2012-04-23 16:14:29,149 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:14:29,150 DEBUG: KMH enabled: False
2012-04-23 16:14:29,179 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:14:29,179 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-23 16:14:34,472 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:14:34,473 DEBUG: KMH enabled: False
2012-04-23 16:14:38,893 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-23 16:14:38,894 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2012-04-23 16:14:56,831 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:14:56,831 DEBUG: KMH enabled: False
2012-04-23 16:14:56,849 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:14:56,850 DEBUG: KMH enabled: False
2012-04-23 16:15:01,688 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:15:01,688 DEBUG: KMH enabled: False
2012-04-23 16:15:01,707 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:15:01,707 DEBUG: KMH enabled: False
2012-04-23 16:15:01,739 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:15:01,739 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-23 16:15:01,778 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:15:01,778 DEBUG: KMH enabled: False
2012-04-23 16:15:01,797 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:15:01,797 DEBUG: KMH enabled: False
2012-04-23 16:15:01,844 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:15:01,844 DEBUG: KMH enabled: False
2012-04-23 16:15:01,863 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:15:01,863 DEBUG: KMH enabled: False
2012-04-23 16:15:01,893 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-23 16:15:01,893 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-23 16:15:02,798 DEBUG: Shutting down
2012-04-24 12:44:44,857 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c>
2012-04-24 12:44:46,229 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic-pae/modules.alias
2012-04-24 12:44:46,351 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-24 12:44:46,362 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-24 12:44:46,436 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-24 12:44:46,448 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-24 12:44:46,462 DEBUG: Software modem not available
2012-04-24 12:44:46,462 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-24 12:44:46,491 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-24 12:44:46,503 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-24 12:44:46,503 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-24 12:44:46,503 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-24 12:44:46,506 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-24 12:44:46,506 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-24 12:44:46,516 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-24 12:44:46,516 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-24 12:44:46,519 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-24 12:44:46,520 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-24 12:44:46,520 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-24 12:44:46,520 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-24 12:44:46,560 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-24 12:44:46,560 DEBUG: Firmware for DVB cards not available
2012-04-24 12:44:46,560 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-24 12:44:46,625 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-24 12:44:46,628 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-24 12:44:46,629 DEBUG: nvidia.available: falling back to default
2012-04-24 12:44:46,753 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-24 12:44:46,753 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-24 12:44:46,755 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-24 12:44:46,758 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-24 12:44:46,759 DEBUG: nvidia.available: falling back to default
2012-04-24 12:44:46,780 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-24 12:44:46,782 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-24 12:44:46,785 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-24 12:44:46,786 DEBUG: nvidia.available: falling back to default
2012-04-24 12:44:46,806 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-24 12:44:46,809 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-24 12:44:46,812 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-24 12:44:46,812 DEBUG: nvidia.available: falling back to default
2012-04-24 12:44:46,823 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-24 12:44:46,823 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-24 12:44:46,826 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-24 12:44:46,829 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-24 12:44:46,829 DEBUG: nvidia.available: falling back to default
2012-04-24 12:44:46,839 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-24 12:44:46,840 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-24 12:44:46,842 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-24 12:44:46,845 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-24 12:44:46,846 DEBUG: nvidia.available: falling back to default
2012-04-24 12:44:46,856 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-24 12:44:46,856 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-24 12:44:46,856 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-24 12:44:46,860 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-04-24 12:44:46,863 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-24 12:44:46,863 DEBUG: fglrx.available: falling back to default
2012-04-24 12:44:46,884 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-24 12:44:46,886 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-24 12:44:46,889 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-24 12:44:46,890 DEBUG: fglrx.available: falling back to default
2012-04-24 12:44:46,910 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-24 12:44:46,911 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-04-24 12:44:46,915 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-04-24 12:44:46,918 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-04-24 12:44:46,936 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-04-24 12:44:46,937 DEBUG: all custom handlers loaded
2012-04-24 12:44:46,937 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'pci:v00008086d000027D8sv00001043sd00008415bc04sc03i00')
2012-04-24 12:44:47,152 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-24 12:44:47,242 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,242 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-24 12:44:47,242 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,242 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-04-24 12:44:47,246 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 12:44:47,246 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,246 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-24 12:44:47,246 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-24 12:44:47,246 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd000083A3bc02sc00i00')
2012-04-24 12:44:47,253 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-04-24 12:44:47,253 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,253 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2012-04-24 12:44:47,253 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 12:44:47,253 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,253 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 12:44:47,253 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,253 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'platform:pcspkr')
2012-04-24 12:44:47,253 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-24 12:44:47,254 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,254 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-24 12:44:47,254 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,254 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 12:44:47,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-24 12:44:47,264 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 12:44:47,264 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,265 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 12:44:47,265 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-24 12:44:47,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'platform:eisa')
2012-04-24 12:44:47,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'pci:v000014F1d00008800sv0000107Dsd0000665Fbc04sc00i00')
2012-04-24 12:44:47,268 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'cx8800'}
2012-04-24 12:44:47,268 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'cx8800', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,268 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-24 12:44:47,268 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'pci:v000010DEd00000A20sv00001462sd00008051bc03sc00i00')
2012-04-24 12:44:47,453 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2012-04-24 12:44:47,525 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:44:47,525 DEBUG: KMH enabled: False
2012-04-24 12:44:47,453 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-04-24 12:44:47,527 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-24 12:44:47,531 DEBUG: nvidia.available: falling back to default
2012-04-24 12:44:47,551 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:44:47,551 DEBUG: KMH enabled: False
2012-04-24 12:44:47,542 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-04-24 12:44:47,551 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2012-04-24 12:44:47,560 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:44:47,560 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-24 12:44:47,551 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-04-24 12:44:47,563 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-24 12:44:47,566 DEBUG: nvidia.available: falling back to default
2012-04-24 12:44:47,586 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:44:47,586 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-24 12:44:47,577 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-04-24 12:44:47,586 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2012-04-24 12:44:47,586 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,586 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2012-04-24 12:44:47,586 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,586 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-24 12:44:47,586 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-24 12:44:47,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'pci:v00008086d00002E30sv00001043sd0000836Dbc06sc00i00')
2012-04-24 12:44:47,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'acpi:PNP0401:')
2012-04-24 12:44:47,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'pci:v00008086d000027C9sv00001043sd00008179bc0Csc03i00')
2012-04-24 12:44:47,591 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-24 12:44:47,591 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-24 12:44:47,592 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 12:44:47,592 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'pci:v00008086d000027CBsv00001043sd00008179bc0Csc03i00')
2012-04-24 12:44:47,594 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-04-24 12:44:47,600 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-24 12:44:47,600 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,601 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'pci:v00008086d000027C0sv00001043sd00008179bc01sc01i8f')
2012-04-24 12:44:47,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-24 12:44:47,603 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 12:44:47,603 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,l0,1,2,3,4,sfw')
2012-04-24 12:44:47,603 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 12:44:47,603 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,603 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-24 12:44:47,603 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,604 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 12:44:47,604 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,604 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-04-24 12:44:47,604 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 12:44:47,604 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,604 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'pci:v00008086d000027CAsv00001043sd00008179bc0Csc03i00')
2012-04-24 12:44:47,606 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0402:bd01/21/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5G41C-MLX:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-04-24 12:44:47,618 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-24 12:44:47,618 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-24 12:44:47,618 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 12:44:47,618 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,618 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2012-04-24 12:44:47,638 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-04-24 12:44:47,638 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,638 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-04-24 12:44:47,638 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,638 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2012-04-24 12:44:47,639 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-04-24 12:44:47,639 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,639 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-04-24 12:44:47,639 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,639 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-24 12:44:47,639 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'acpi:PNP0501:')
2012-04-24 12:44:47,639 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'pci:v00008086d000027DFsv00001043sd00008179bc01sc01i8a')
2012-04-24 12:44:47,641 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'pci:v00008086d000027C8sv00001043sd00008179bc0Csc03i00')
2012-04-24 12:44:47,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'pci:v00008086d000027B8sv00001043sd00008179bc06sc01i00')
2012-04-24 12:44:47,646 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng'}
2012-04-24 12:44:47,646 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,646 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-04-24 12:44:47,646 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,646 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'leds_ss4200'}
2012-04-24 12:44:47,646 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'leds_ss4200', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,646 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'pci:v00008086d000027CCsv00001043sd00008179bc0Csc03i20')
2012-04-24 12:44:47,648 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'pci:v000010DEd00000BE2sv00001462sd00008051bc04sc03i00')
2012-04-24 12:44:47,651 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-24 12:44:47,651 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,651 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-24 12:44:47,651 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2012-04-24 12:44:47,651 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-04-24 12:44:47,651 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,651 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd00008179bc06sc04i01')
2012-04-24 12:44:47,654 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-24 12:44:47,654 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-24 12:44:47,654 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,654 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-24 12:44:47,654 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,654 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'pci:v000014F1d00008802sv0000107Dsd0000665Fbc04sc80i00')
2012-04-24 12:44:47,654 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'cx8802'}
2012-04-24 12:44:47,654 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'cx8802', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,654 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-04-24 12:44:47,654 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 12:44:47,655 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,655 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'input:b0001v107Dp665Fe0001-e0,1,4,14,k71,72,73,80,8B,8E,A4,A7,A8,D0,D4,DF,163,164,166,167,16B,170,172,174,175,179,17A,181,182,184,185,188,189,18E,18F,190,191,192,193,195,197,19C,ram4,lsfw')
2012-04-24 12:44:47,655 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 12:44:47,655 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,655 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 12:44:47,655 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:44:47,655 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7263d0c> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-24 12:44:47,655 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'pci:v00008086d000027D8sv00001043sd00008415bc04sc03i00')
2012-04-24 12:44:47,655 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-04-24 12:44:47,655 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-24 12:44:47,655 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-24 12:44:47,655 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd000083A3bc02sc00i00')
2012-04-24 12:44:47,655 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2012-04-24 12:44:47,655 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'platform:pcspkr')
2012-04-24 12:44:47,655 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 12:44:47,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-24 12:44:47,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-24 12:44:47,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'platform:eisa')
2012-04-24 12:44:47,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'pci:v000014F1d00008800sv0000107Dsd0000665Fbc04sc00i00')
2012-04-24 12:44:47,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-24 12:44:47,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'pci:v000010DEd00000A20sv00001462sd00008051bc03sc00i00')
2012-04-24 12:44:47,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-24 12:44:47,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-24 12:44:47,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'pci:v00008086d00002E30sv00001043sd0000836Dbc06sc00i00')
2012-04-24 12:44:47,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'acpi:PNP0401:')
2012-04-24 12:44:47,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'pci:v00008086d000027C9sv00001043sd00008179bc0Csc03i00')
2012-04-24 12:44:47,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-24 12:44:47,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-24 12:44:47,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 12:44:47,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'pci:v00008086d000027CBsv00001043sd00008179bc0Csc03i00')
2012-04-24 12:44:47,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-04-24 12:44:47,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'pci:v00008086d000027C0sv00001043sd00008179bc01sc01i8f')
2012-04-24 12:44:47,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-24 12:44:47,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,l0,1,2,3,4,sfw')
2012-04-24 12:44:47,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-04-24 12:44:47,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'pci:v00008086d000027CAsv00001043sd00008179bc0Csc03i00')
2012-04-24 12:44:47,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0402:bd01/21/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5G41C-MLX:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-04-24 12:44:47,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-24 12:44:47,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-24 12:44:47,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2012-04-24 12:44:47,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2012-04-24 12:44:47,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-24 12:44:47,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'acpi:PNP0501:')
2012-04-24 12:44:47,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'pci:v00008086d000027DFsv00001043sd00008179bc01sc01i8a')
2012-04-24 12:44:47,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'pci:v00008086d000027C8sv00001043sd00008179bc0Csc03i00')
2012-04-24 12:44:47,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'pci:v00008086d000027B8sv00001043sd00008179bc06sc01i00')
2012-04-24 12:44:47,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'pci:v00008086d000027CCsv00001043sd00008179bc0Csc03i20')
2012-04-24 12:44:47,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'pci:v000010DEd00000BE2sv00001462sd00008051bc04sc03i00')
2012-04-24 12:44:47,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-24 12:44:47,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2012-04-24 12:44:47,658 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd00008179bc06sc04i01')
2012-04-24 12:44:47,658 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-24 12:44:47,658 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'pci:v000014F1d00008802sv0000107Dsd0000665Fbc04sc80i00')
2012-04-24 12:44:47,658 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-04-24 12:44:47,658 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'input:b0001v107Dp665Fe0001-e0,1,4,14,k71,72,73,80,8B,8E,A4,A7,A8,D0,D4,DF,163,164,166,167,16B,170,172,174,175,179,17A,181,182,184,185,188,189,18E,18F,190,191,192,193,195,197,19C,ram4,lsfw')
2012-04-24 12:44:47,658 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb695e84c> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-24 12:44:47,707 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:44:47,708 DEBUG: KMH enabled: False
2012-04-24 12:44:48,682 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:44:48,683 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-24 12:44:49,483 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:44:49,483 DEBUG: KMH enabled: False
2012-04-24 12:44:49,508 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:44:49,508 DEBUG: KMH enabled: False
2012-04-24 12:44:49,527 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:44:49,527 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-24 12:44:52,251 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:44:52,251 DEBUG: KMH enabled: False
2012-04-24 12:44:56,506 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-24 12:44:56,507 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2012-04-24 12:45:18,004 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:45:18,004 DEBUG: KMH enabled: False
2012-04-24 12:45:18,015 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:45:18,015 DEBUG: KMH enabled: False
2012-04-24 12:45:22,392 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:45:22,392 DEBUG: KMH enabled: False
2012-04-24 12:45:22,409 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:45:22,409 DEBUG: KMH enabled: False
2012-04-24 12:45:22,440 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:45:22,440 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-24 12:45:22,478 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:45:22,478 DEBUG: KMH enabled: False
2012-04-24 12:45:22,496 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:45:22,496 DEBUG: KMH enabled: False
2012-04-24 12:45:22,541 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:45:22,541 DEBUG: KMH enabled: False
2012-04-24 12:45:22,559 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:45:22,559 DEBUG: KMH enabled: False
2012-04-24 12:45:22,587 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:45:22,587 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-24 12:45:23,986 DEBUG: Shutting down
2012-04-24 12:50:57,837 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c>
2012-04-24 12:50:59,513 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic-pae/modules.alias
2012-04-24 12:50:59,627 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-24 12:50:59,638 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-24 12:50:59,712 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-24 12:50:59,725 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-24 12:50:59,738 DEBUG: Software modem not available
2012-04-24 12:50:59,738 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-24 12:50:59,767 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-24 12:50:59,779 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-24 12:50:59,779 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-24 12:50:59,779 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-24 12:50:59,782 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-24 12:50:59,782 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-24 12:50:59,803 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-24 12:50:59,803 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-24 12:50:59,807 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-24 12:50:59,807 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-24 12:50:59,807 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-24 12:50:59,807 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-24 12:50:59,848 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-24 12:50:59,848 DEBUG: Firmware for DVB cards not available
2012-04-24 12:50:59,848 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-24 12:50:59,913 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-24 12:50:59,916 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-24 12:50:59,917 DEBUG: nvidia.available: falling back to default
2012-04-24 12:51:00,041 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-24 12:51:00,041 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-24 12:51:00,043 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-24 12:51:00,046 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-24 12:51:00,047 DEBUG: nvidia.available: falling back to default
2012-04-24 12:51:00,068 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-24 12:51:00,070 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-24 12:51:00,073 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-24 12:51:00,074 DEBUG: nvidia.available: falling back to default
2012-04-24 12:51:00,095 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-24 12:51:00,097 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-24 12:51:00,100 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-24 12:51:00,101 DEBUG: nvidia.available: falling back to default
2012-04-24 12:51:00,111 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-24 12:51:00,111 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-24 12:51:00,113 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-24 12:51:00,117 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-24 12:51:00,117 DEBUG: nvidia.available: falling back to default
2012-04-24 12:51:00,128 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-24 12:51:00,128 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-24 12:51:00,130 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-24 12:51:00,133 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-24 12:51:00,134 DEBUG: nvidia.available: falling back to default
2012-04-24 12:51:00,144 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-24 12:51:00,144 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-24 12:51:00,144 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-24 12:51:00,148 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-04-24 12:51:00,151 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-24 12:51:00,151 DEBUG: fglrx.available: falling back to default
2012-04-24 12:51:00,172 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-24 12:51:00,174 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-24 12:51:00,177 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-24 12:51:00,178 DEBUG: fglrx.available: falling back to default
2012-04-24 12:51:00,199 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-24 12:51:00,199 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-04-24 12:51:00,203 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-04-24 12:51:00,206 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-04-24 12:51:00,225 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-04-24 12:51:00,225 DEBUG: all custom handlers loaded
2012-04-24 12:51:00,225 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'pci:v00008086d000027D8sv00001043sd00008415bc04sc03i00')
2012-04-24 12:51:00,441 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-24 12:51:00,529 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,529 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-24 12:51:00,529 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,529 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-04-24 12:51:00,533 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 12:51:00,533 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,533 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-24 12:51:00,533 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-24 12:51:00,533 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd000083A3bc02sc00i00')
2012-04-24 12:51:00,540 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-04-24 12:51:00,540 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,540 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2012-04-24 12:51:00,540 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 12:51:00,540 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,540 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 12:51:00,540 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,540 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'platform:pcspkr')
2012-04-24 12:51:00,541 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-24 12:51:00,541 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,541 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-24 12:51:00,541 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,541 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 12:51:00,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-24 12:51:00,552 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 12:51:00,552 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,552 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 12:51:00,552 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-24 12:51:00,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'platform:eisa')
2012-04-24 12:51:00,553 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'pci:v000014F1d00008800sv0000107Dsd0000665Fbc04sc00i00')
2012-04-24 12:51:00,555 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'cx8800'}
2012-04-24 12:51:00,555 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'cx8800', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-24 12:51:00,556 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'pci:v000010DEd00000A20sv00001462sd00008051bc03sc00i00')
2012-04-24 12:51:00,742 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2012-04-24 12:51:00,872 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:00,872 DEBUG: KMH enabled: False
2012-04-24 12:51:00,742 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-04-24 12:51:00,875 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-24 12:51:00,879 DEBUG: nvidia.available: falling back to default
2012-04-24 12:51:00,898 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:00,899 DEBUG: KMH enabled: False
2012-04-24 12:51:00,889 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-04-24 12:51:00,899 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2012-04-24 12:51:00,908 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:00,908 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-24 12:51:00,899 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-04-24 12:51:00,910 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-24 12:51:00,914 DEBUG: nvidia.available: falling back to default
2012-04-24 12:51:00,933 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:00,934 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-24 12:51:00,924 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-04-24 12:51:00,934 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2012-04-24 12:51:00,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,934 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2012-04-24 12:51:00,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-24 12:51:00,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-24 12:51:00,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'pci:v00008086d00002E30sv00001043sd0000836Dbc06sc00i00')
2012-04-24 12:51:00,937 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'acpi:PNP0401:')
2012-04-24 12:51:00,937 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'pci:v00008086d000027C9sv00001043sd00008179bc0Csc03i00')
2012-04-24 12:51:00,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-24 12:51:00,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-24 12:51:00,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 12:51:00,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'pci:v00008086d000027CBsv00001043sd00008179bc0Csc03i00')
2012-04-24 12:51:00,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-04-24 12:51:00,948 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-24 12:51:00,948 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,948 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'pci:v00008086d000027C0sv00001043sd00008179bc01sc01i8f')
2012-04-24 12:51:00,950 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-24 12:51:00,950 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 12:51:00,951 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,951 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,l0,1,2,3,4,sfw')
2012-04-24 12:51:00,951 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 12:51:00,951 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,951 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-24 12:51:00,951 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,951 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 12:51:00,951 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,951 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-04-24 12:51:00,951 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 12:51:00,951 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,951 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'pci:v00008086d000027CAsv00001043sd00008179bc0Csc03i00')
2012-04-24 12:51:00,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0402:bd01/21/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5G41C-MLX:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-04-24 12:51:00,965 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-24 12:51:00,965 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-24 12:51:00,966 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 12:51:00,966 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,966 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2012-04-24 12:51:00,986 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-04-24 12:51:00,986 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,986 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-04-24 12:51:00,986 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2012-04-24 12:51:00,986 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-04-24 12:51:00,986 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,987 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-04-24 12:51:00,987 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,987 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-24 12:51:00,987 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'acpi:PNP0501:')
2012-04-24 12:51:00,987 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'pci:v00008086d000027DFsv00001043sd00008179bc01sc01i8a')
2012-04-24 12:51:00,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'pci:v00008086d000027C8sv00001043sd00008179bc0Csc03i00')
2012-04-24 12:51:00,991 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'pci:v00008086d000027B8sv00001043sd00008179bc06sc01i00')
2012-04-24 12:51:00,993 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng'}
2012-04-24 12:51:00,993 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,993 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-04-24 12:51:00,993 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,994 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'leds_ss4200'}
2012-04-24 12:51:00,994 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'leds_ss4200', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,994 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'pci:v00008086d000027CCsv00001043sd00008179bc0Csc03i20')
2012-04-24 12:51:00,996 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'pci:v000010DEd00000BE2sv00001462sd00008051bc04sc03i00')
2012-04-24 12:51:00,998 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-24 12:51:00,998 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,998 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-24 12:51:00,998 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2012-04-24 12:51:00,999 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-04-24 12:51:00,999 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:00,999 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd00008179bc06sc04i01')
2012-04-24 12:51:01,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-24 12:51:01,001 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-24 12:51:01,001 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:01,001 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-24 12:51:01,002 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:01,002 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'pci:v000014F1d00008802sv0000107Dsd0000665Fbc04sc80i00')
2012-04-24 12:51:01,002 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'cx8802'}
2012-04-24 12:51:01,002 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'cx8802', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:01,002 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-04-24 12:51:01,002 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 12:51:01,002 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:01,002 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'input:b0001v107Dp665Fe0001-e0,1,4,14,k71,72,73,80,8B,8E,A4,A7,A8,D0,D4,DF,163,164,166,167,16B,170,172,174,175,179,17A,181,182,184,185,188,189,18E,18F,190,191,192,193,195,197,19C,ram4,lsfw')
2012-04-24 12:51:01,002 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 12:51:01,002 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:01,002 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 12:51:01,002 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 12:51:01,003 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7188d0c> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-24 12:51:01,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'pci:v00008086d000027D8sv00001043sd00008415bc04sc03i00')
2012-04-24 12:51:01,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-04-24 12:51:01,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-24 12:51:01,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-24 12:51:01,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd000083A3bc02sc00i00')
2012-04-24 12:51:01,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2012-04-24 12:51:01,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'platform:pcspkr')
2012-04-24 12:51:01,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 12:51:01,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-24 12:51:01,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-24 12:51:01,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'platform:eisa')
2012-04-24 12:51:01,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'pci:v000014F1d00008800sv0000107Dsd0000665Fbc04sc00i00')
2012-04-24 12:51:01,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-24 12:51:01,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'pci:v000010DEd00000A20sv00001462sd00008051bc03sc00i00')
2012-04-24 12:51:01,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-24 12:51:01,003 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-24 12:51:01,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'pci:v00008086d00002E30sv00001043sd0000836Dbc06sc00i00')
2012-04-24 12:51:01,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'acpi:PNP0401:')
2012-04-24 12:51:01,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'pci:v00008086d000027C9sv00001043sd00008179bc0Csc03i00')
2012-04-24 12:51:01,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-24 12:51:01,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-24 12:51:01,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 12:51:01,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'pci:v00008086d000027CBsv00001043sd00008179bc0Csc03i00')
2012-04-24 12:51:01,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-04-24 12:51:01,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'pci:v00008086d000027C0sv00001043sd00008179bc01sc01i8f')
2012-04-24 12:51:01,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-24 12:51:01,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,l0,1,2,3,4,sfw')
2012-04-24 12:51:01,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-04-24 12:51:01,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'pci:v00008086d000027CAsv00001043sd00008179bc0Csc03i00')
2012-04-24 12:51:01,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0402:bd01/21/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5G41C-MLX:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-04-24 12:51:01,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-24 12:51:01,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-24 12:51:01,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2012-04-24 12:51:01,004 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2012-04-24 12:51:01,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-24 12:51:01,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'acpi:PNP0501:')
2012-04-24 12:51:01,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'pci:v00008086d000027DFsv00001043sd00008179bc01sc01i8a')
2012-04-24 12:51:01,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'pci:v00008086d000027C8sv00001043sd00008179bc0Csc03i00')
2012-04-24 12:51:01,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'pci:v00008086d000027B8sv00001043sd00008179bc06sc01i00')
2012-04-24 12:51:01,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'pci:v00008086d000027CCsv00001043sd00008179bc0Csc03i20')
2012-04-24 12:51:01,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'pci:v000010DEd00000BE2sv00001462sd00008051bc04sc03i00')
2012-04-24 12:51:01,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-24 12:51:01,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2012-04-24 12:51:01,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd00008179bc06sc04i01')
2012-04-24 12:51:01,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-24 12:51:01,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'pci:v000014F1d00008802sv0000107Dsd0000665Fbc04sc80i00')
2012-04-24 12:51:01,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-04-24 12:51:01,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'input:b0001v107Dp665Fe0001-e0,1,4,14,k71,72,73,80,8B,8E,A4,A7,A8,D0,D4,DF,163,164,166,167,16B,170,172,174,175,179,17A,181,182,184,185,188,189,18E,18F,190,191,192,193,195,197,19C,ram4,lsfw')
2012-04-24 12:51:01,005 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb688384c> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-24 12:51:01,037 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:01,037 DEBUG: KMH enabled: False
2012-04-24 12:51:01,909 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:01,909 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-24 12:51:02,693 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:02,693 DEBUG: KMH enabled: False
2012-04-24 12:51:02,717 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:02,718 DEBUG: KMH enabled: False
2012-04-24 12:51:02,734 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:02,735 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-24 12:51:04,787 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:04,787 DEBUG: KMH enabled: False
2012-04-24 12:51:08,013 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-24 12:51:08,014 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2012-04-24 12:51:24,949 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:24,949 DEBUG: KMH enabled: False
2012-04-24 12:51:24,962 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:24,962 DEBUG: KMH enabled: False
2012-04-24 12:51:26,576 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:26,576 DEBUG: KMH enabled: False
2012-04-24 12:51:26,586 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:26,587 DEBUG: KMH enabled: False
2012-04-24 12:51:26,605 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:26,606 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-24 12:51:26,628 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:26,629 DEBUG: KMH enabled: False
2012-04-24 12:51:26,639 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:26,639 DEBUG: KMH enabled: False
2012-04-24 12:51:26,666 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:26,666 DEBUG: KMH enabled: False
2012-04-24 12:51:26,677 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:26,677 DEBUG: KMH enabled: False
2012-04-24 12:51:26,694 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 12:51:26,694 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-24 12:51:28,873 DEBUG: Shutting down
2012-04-24 15:28:04,216 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c>
2012-04-24 15:28:05,600 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic-pae/modules.alias
2012-04-24 15:28:05,680 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-24 15:28:05,680 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-24 15:28:05,715 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-24 15:28:05,730 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-24 15:28:05,739 DEBUG: Software modem not available
2012-04-24 15:28:05,739 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-24 15:28:05,744 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-24 15:28:05,763 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-24 15:28:05,764 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-24 15:28:05,764 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-24 15:28:05,769 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-24 15:28:05,769 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-24 15:28:05,787 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-24 15:28:05,787 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-24 15:28:05,792 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-24 15:28:05,792 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-24 15:28:05,792 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-24 15:28:05,793 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-24 15:28:05,816 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-24 15:28:05,816 DEBUG: Firmware for DVB cards not available
2012-04-24 15:28:05,816 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-24 15:28:05,824 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-24 15:28:05,829 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-24 15:28:05,831 DEBUG: nvidia.available: falling back to default
2012-04-24 15:28:05,891 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-24 15:28:05,892 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-24 15:28:05,894 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-24 15:28:05,898 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-24 15:28:05,899 DEBUG: nvidia.available: falling back to default
2012-04-24 15:28:05,926 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-24 15:28:05,930 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-24 15:28:05,934 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-24 15:28:05,935 DEBUG: nvidia.available: falling back to default
2012-04-24 15:28:05,973 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-24 15:28:05,977 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-24 15:28:05,982 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-24 15:28:05,982 DEBUG: nvidia.available: falling back to default
2012-04-24 15:28:06,000 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-24 15:28:06,001 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-24 15:28:06,004 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-24 15:28:06,009 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-24 15:28:06,010 DEBUG: nvidia.available: falling back to default
2012-04-24 15:28:06,028 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-24 15:28:06,028 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-24 15:28:06,032 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-24 15:28:06,037 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-24 15:28:06,038 DEBUG: nvidia.available: falling back to default
2012-04-24 15:28:06,055 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-24 15:28:06,056 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-24 15:28:06,056 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-24 15:28:06,062 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-04-24 15:28:06,067 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-24 15:28:06,067 DEBUG: fglrx.available: falling back to default
2012-04-24 15:28:06,103 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-24 15:28:06,107 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-24 15:28:06,111 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-24 15:28:06,112 DEBUG: fglrx.available: falling back to default
2012-04-24 15:28:06,147 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-24 15:28:06,148 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-04-24 15:28:06,154 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-04-24 15:28:06,159 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-04-24 15:28:06,191 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-04-24 15:28:06,192 DEBUG: all custom handlers loaded
2012-04-24 15:28:06,192 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'pci:v00008086d000027D8sv00001043sd00008415bc04sc03i00')
2012-04-24 15:28:06,417 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-24 15:28:06,492 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,492 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-24 15:28:06,492 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-04-24 15:28:06,496 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 15:28:06,496 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,496 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-24 15:28:06,496 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-24 15:28:06,496 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd000083A3bc02sc00i00')
2012-04-24 15:28:06,503 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-04-24 15:28:06,503 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2012-04-24 15:28:06,503 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 15:28:06,503 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,503 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 15:28:06,503 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'platform:pcspkr')
2012-04-24 15:28:06,504 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-24 15:28:06,504 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,504 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-24 15:28:06,504 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,504 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 15:28:06,515 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-24 15:28:06,515 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 15:28:06,515 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,515 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 15:28:06,515 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,515 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-24 15:28:06,515 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'platform:eisa')
2012-04-24 15:28:06,515 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'pci:v000014F1d00008800sv0000107Dsd0000665Fbc04sc00i00')
2012-04-24 15:28:06,518 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'cx8800'}
2012-04-24 15:28:06,518 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'cx8800', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,518 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-24 15:28:06,519 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'pci:v000010DEd00000A20sv00001462sd00008051bc03sc00i00')
2012-04-24 15:28:06,706 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2012-04-24 15:28:06,716 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 15:28:06,716 DEBUG: KMH enabled: False
2012-04-24 15:28:06,706 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-04-24 15:28:06,718 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-24 15:28:06,723 DEBUG: nvidia.available: falling back to default
2012-04-24 15:28:06,746 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 15:28:06,746 DEBUG: KMH enabled: False
2012-04-24 15:28:06,734 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2012-04-24 15:28:06,746 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2012-04-24 15:28:06,761 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 15:28:06,761 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-24 15:28:06,746 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-04-24 15:28:06,765 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-24 15:28:06,771 DEBUG: nvidia.available: falling back to default
2012-04-24 15:28:06,807 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 15:28:06,807 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-24 15:28:06,790 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2012-04-24 15:28:06,808 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2012-04-24 15:28:06,808 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,808 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2012-04-24 15:28:06,808 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,808 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-24 15:28:06,808 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-24 15:28:06,808 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'pci:v00008086d00002E30sv00001043sd0000836Dbc06sc00i00')
2012-04-24 15:28:06,813 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'acpi:PNP0401:')
2012-04-24 15:28:06,814 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'pci:v00008086d000027C9sv00001043sd00008179bc0Csc03i00')
2012-04-24 15:28:06,818 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-24 15:28:06,818 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-24 15:28:06,818 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 15:28:06,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'pci:v00008086d000027CBsv00001043sd00008179bc0Csc03i00')
2012-04-24 15:28:06,822 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-04-24 15:28:06,828 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-24 15:28:06,829 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,829 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'pci:v00008086d000027C0sv00001043sd00008179bc01sc01i8f')
2012-04-24 15:28:06,831 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-24 15:28:06,831 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 15:28:06,831 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,831 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,l0,1,2,3,4,sfw')
2012-04-24 15:28:06,832 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 15:28:06,832 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,832 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-24 15:28:06,832 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,832 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 15:28:06,832 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,832 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-04-24 15:28:06,832 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 15:28:06,832 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,832 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'pci:v00008086d000027CAsv00001043sd00008179bc0Csc03i00')
2012-04-24 15:28:06,835 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0402:bd01/21/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5G41C-MLX:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-04-24 15:28:06,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-24 15:28:06,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-24 15:28:06,847 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 15:28:06,847 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2012-04-24 15:28:06,867 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-04-24 15:28:06,867 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,867 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-04-24 15:28:06,868 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,868 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2012-04-24 15:28:06,868 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-04-24 15:28:06,868 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,868 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-04-24 15:28:06,868 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,868 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-24 15:28:06,868 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'acpi:PNP0501:')
2012-04-24 15:28:06,868 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'pci:v00008086d000027DFsv00001043sd00008179bc01sc01i8a')
2012-04-24 15:28:06,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'pci:v00008086d000027C8sv00001043sd00008179bc0Csc03i00')
2012-04-24 15:28:06,873 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'pci:v00008086d000027B8sv00001043sd00008179bc06sc01i00')
2012-04-24 15:28:06,876 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng'}
2012-04-24 15:28:06,876 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,876 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-04-24 15:28:06,876 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,876 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'leds_ss4200'}
2012-04-24 15:28:06,876 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'leds_ss4200', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,876 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'pci:v00008086d000027CCsv00001043sd00008179bc0Csc03i20')
2012-04-24 15:28:06,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'pci:v000010DEd00000BE2sv00001462sd00008051bc04sc03i00')
2012-04-24 15:28:06,881 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-24 15:28:06,881 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-24 15:28:06,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2012-04-24 15:28:06,882 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-04-24 15:28:06,882 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,882 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd00008179bc06sc04i01')
2012-04-24 15:28:06,884 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-24 15:28:06,884 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-24 15:28:06,885 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,885 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-24 15:28:06,885 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,885 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'pci:v000014F1d00008802sv0000107Dsd0000665Fbc04sc80i00')
2012-04-24 15:28:06,885 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'cx8802'}
2012-04-24 15:28:06,885 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'cx8802', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,885 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-04-24 15:28:06,885 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 15:28:06,885 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,885 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'input:b0001v107Dp665Fe0001-e0,1,4,14,k71,72,73,80,8B,8E,A4,A7,A8,D0,D4,DF,163,164,166,167,16B,170,172,174,175,179,17A,181,182,184,185,188,189,18E,18F,190,191,192,193,195,197,19C,ram4,lsfw')
2012-04-24 15:28:06,885 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-24 15:28:06,886 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,886 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-24 15:28:06,886 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-24 15:28:06,886 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb716dd0c> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-24 15:28:06,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'pci:v00008086d000027D8sv00001043sd00008415bc04sc03i00')
2012-04-24 15:28:06,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2012-04-24 15:28:06,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-24 15:28:06,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-24 15:28:06,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd000083A3bc02sc00i00')
2012-04-24 15:28:06,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2012-04-24 15:28:06,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'platform:pcspkr')
2012-04-24 15:28:06,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 15:28:06,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-24 15:28:06,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-24 15:28:06,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'platform:eisa')
2012-04-24 15:28:06,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'pci:v000014F1d00008800sv0000107Dsd0000665Fbc04sc00i00')
2012-04-24 15:28:06,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-24 15:28:06,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'pci:v000010DEd00000A20sv00001462sd00008051bc03sc00i00')
2012-04-24 15:28:06,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-24 15:28:06,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-24 15:28:06,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'pci:v00008086d00002E30sv00001043sd0000836Dbc06sc00i00')
2012-04-24 15:28:06,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'acpi:PNP0401:')
2012-04-24 15:28:06,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'pci:v00008086d000027C9sv00001043sd00008179bc0Csc03i00')
2012-04-24 15:28:06,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-24 15:28:06,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-24 15:28:06,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-24 15:28:06,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'pci:v00008086d000027CBsv00001043sd00008179bc0Csc03i00')
2012-04-24 15:28:06,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2012-04-24 15:28:06,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'pci:v00008086d000027C0sv00001043sd00008179bc01sc01i8f')
2012-04-24 15:28:06,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-24 15:28:06,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,l0,1,2,3,4,sfw')
2012-04-24 15:28:06,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2012-04-24 15:28:06,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'pci:v00008086d000027CAsv00001043sd00008179bc0Csc03i00')
2012-04-24 15:28:06,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0402:bd01/21/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5G41C-MLX:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2012-04-24 15:28:06,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-24 15:28:06,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-24 15:28:06,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2012-04-24 15:28:06,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2012-04-24 15:28:06,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-24 15:28:06,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'acpi:PNP0501:')
2012-04-24 15:28:06,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'pci:v00008086d000027DFsv00001043sd00008179bc01sc01i8a')
2012-04-24 15:28:06,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'pci:v00008086d000027C8sv00001043sd00008179bc0Csc03i00')
2012-04-24 15:28:06,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'pci:v00008086d000027B8sv00001043sd00008179bc06sc01i00')
2012-04-24 15:28:06,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'pci:v00008086d000027CCsv00001043sd00008179bc0Csc03i20')
2012-04-24 15:28:06,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'pci:v000010DEd00000BE2sv00001462sd00008051bc04sc03i00')
2012-04-24 15:28:06,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-24 15:28:06,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2012-04-24 15:28:06,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd00008179bc06sc04i01')
2012-04-24 15:28:06,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-24 15:28:06,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'pci:v000014F1d00008802sv0000107Dsd0000665Fbc04sc80i00')
2012-04-24 15:28:06,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-04-24 15:28:06,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'input:b0001v107Dp665Fe0001-e0,1,4,14,k71,72,73,80,8B,8E,A4,A7,A8,D0,D4,DF,163,164,166,167,16B,170,172,174,175,179,17A,181,182,184,185,188,189,18E,18F,190,191,192,193,195,197,19C,ram4,lsfw')
2012-04-24 15:28:06,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb686884c> about HardwareID('modalias', 'acpi:INT0800:')
2012-04-24 15:28:06,963 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 15:28:06,963 DEBUG: KMH enabled: False
2012-04-24 15:28:07,764 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 15:28:07,764 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-24 15:28:08,578 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 15:28:08,578 DEBUG: KMH enabled: False
2012-04-24 15:28:08,614 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 15:28:08,614 DEBUG: KMH enabled: False
2012-04-24 15:28:08,642 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 15:28:08,643 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-24 15:28:17,702 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-04-24 15:28:17,702 DEBUG: nvidia_current_updates is not the alternative in use
2012-04-24 15:28:23,982 DEBUG: Shutting down[/HTML]

---

### Post by Harry33 on 2012-04-24
This seems a bit odd.
Jockey is trying to install old nvidia-graphics-drivers (v. 96 and 173) and with wrong video abi (xorg-video-abi-10).
This is not suitable for Precise xserver. It needs the xorg-video-abi-11.

Russty of Oz, what Nvidia graphics card (model) do you have?
We need to know, which driver you need.
Then, you can manually install the correct driver.

For example:
Nvidia-current (295.40) is the latest driver now. It supports NVidia GPUs such as GeForce series 6 or newer.
For a 32-bit setup, you will find it here:
[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/295.40-0ubuntu1/+build/3401267](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/295.40-0ubuntu1/+build/3401267)

For a 64-bit setup, you will find it here:
[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/295.40-0ubuntu1/+build/3401266](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/295.40-0ubuntu1/+build/3401266)

---

### Post by Russty of Oz on 2012-04-24
Thanks Harry, 

I do have a 6 series card and so I went to the link you provided and when I tried to install the new drivers it said they were already installed, so I reinstalled and now it works beautifuly!!:D

Thanks,

Russty

> **Harry33 said:**
> This seems a bit odd.
Jockey is trying to install old nvidia-graphics-drivers (v. 96 and 173) and with wrong video abi (xorg-video-abi-10).
This is not suitable for Precise xserver. It needs the xorg-video-abi-11.

Russty of Oz, what Nvidia graphics card (model) do you have?
We need to know, which driver you need.
Then, you can manually install the correct driver.

For example:
Nvidia-current (295.40) is the latest driver now. It supports NVidia GPUs such as GeForce series 6 or newer.
For a 32-bit setup, you will find it here:
[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/295.40-0ubuntu1/+build/3401267](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/295.40-0ubuntu1/+build/3401267)

For a 64-bit setup, you will find it here:
[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/295.40-0ubuntu1/+build/3401266](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/295.40-0ubuntu1/+build/3401266)

---

### Post by VMC on 2012-04-24
Interesting. I installed that driver and I keep getting the slow *r-click* focus problem. Is their a xorg config fix for that?

---

### Post by dino99 on 2012-04-24
> **VMC said:**
> Interesting. I installed that driver and I keep getting the slow *r-click* focus problem. Is their a xorg config fix for that?

yes, either install back the 280.10 driver or wait for a new 300.xx driver fixing the borked 295.xx

---

### Post by VMC on 2012-04-24
> **dino99 said:**
> yes, either install back the 280.10 driver or wait for a new 300.xx driver fixing the borked 295.xx

Are you sure its 280.10,and not 290.10?

edit: can't be 290.10. I just installed it and it does the same thing. r-click several seconds to focus. I can't seem to find 280.10 using nvidia [**downloads**]("ftp://download.nvidia.com/XFree86/Linux-x86_64/") site.

---

