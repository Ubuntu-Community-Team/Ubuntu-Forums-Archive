---
title: "Ubunty Core Snappy boot problem on Artik 10 V 0.5"
date: 2016-05-23
forum: Ubuntu Development Version
---

### Post by rbitter on 2016-05-23
[COLOR=#525E68][FONT=Source Sans Pro]I installed Ubuntu Core on an SD card (actually tested with two different card to rule out hardware defect), and tried to boot up on Ver 0.5 / 2016.02.12 Artik 10. With both SD cards I ran into the same boot problem. Used the Ubuntu Core image artik10-snappy-20160317.img.tar.xz.[/FONT][/COLOR]
[COLOR=#525E68][FONT=Source Sans Pro]I'm tracking the boot progress with minicom and serial USB debug port. Here is the error message I'm seeing:

```
[ 15.902332] [c6] Dongle Host Driver, version 1.141.64.12 (r)
[ 15.902332] Compiled in drivers/net/wireless/bcmdhd on Feb 5 2016 at 00:31:54
[ 15.915702] [c6] Register interface [wlan0] MAC: 00:e2:26
[ 15.915702] 
[ 15.921348] [c6] dhd_prot_ioctl : bus is down. we have nothing to do
[ 15.927681] [c6] dhd_wl_ioctl: WLC_IOCTL: cmd: 3, ret = -1
[ 15.933473] [c6] wifi_platform_set_power = 0
[ 15.937388] [c6] ------------------------------------------------
[ 15.943337] ------------------------------------------------
[ 15.949099] [c6] dhd_wlan_power Enter: power off
[ 16.056375] [c7] ALSA device list:
[ 16.058292] [c7] #0: artik-ak4953
[ 16.062837] [c7] Freeing unused kernel memory: 500K (c09a9000 - c0a26000)
Loading, please wait...
starting version 219
[ 16.314536] [c0] dwmmc_exynos 12220000.dwmmc2: Start bit error (status=00002000)
[ 16.320617] [c2] mmcblk1: error -5 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 16.330333] [c6] mmcblk1: retrying using single block read
[ 16.337825] [c0] dwmmc_exynos 12220000.dwmmc2: data CRC error READ
[ 16.342736] [c6] mmcblk1: error -84 transferring data, sector 1, nr 7, cmd response 0x900, card status 0x0
[ 16.352943] [c0] dwmmc_exynos 12220000.dwmmc2: data CRC error READ
[ 16.358563] [c6] mmcblk1: error -84 transferring data, sector 2, nr 6, cmd response 0x900, card status 0x0
[ 16.368581] [c0] dwmmc_exynos 12220000.dwmmc2: data CRC error READ
[ 16.374333] [c6] mmcblk1: error -84 transferring data, sector 3, nr 5, cmd response 0x900, card status 0x0
[ 16.384428] [c0] dwmmc_exynos 12220000.dwmmc2: data CRC error READ
[ 16.390065] [c6] mmcblk1: error -84 transferring data, sector 4, nr 4, cmd response 0x900, card status 0x0
[ 16.400145] [c0] dwmmc_exynos 12220000.dwmmc2: data CRC error READ
[ 16.405828] [c6] mmcblk1: error -84 transferring data, sector 5, nr 3, cmd response 0x900, card status 0x0
[ 16.415940] [c0] dwmmc_exynos 12220000.dwmmc2: data CRC error READ
[ 16.421771] [c6] mmcblk1: error -84 transferring data, sector 6, nr 2, cmd response 0x900, card status 0x0
[ 16.431798] [c0] dwmmc_exynos 12220000.dwmmc2: data CRC error READ
[ 16.437661] [c4] mmcblk1: error -84 transferring data, sector 7, nr 1, cmd response 0x900, card status 0x0
[ 16.447310] [c4] Buffer I/O error on device mmcblk1, logical block 0
[ 16.453887] [c0] dwmmc_exynos 12220000.dwmmc2: Start bit error (status=00002000)
[ 16.461197] [c4] mmcblk1: error -5 transferring data, sector 0, nr 8, cmd response 0x900, card status 0xb00
[ 16.470453] [c4] mmcblk1: retrying using single block read
[ 16.477028] [c0] dwmmc_exynos 12220000.dwmmc2: data CRC error READ
[ 16.484348] [c4] mmcblk1: error -84 transferring data, sector 1, nr 7, cmd response 0x900, card status 0x0
[ 16.493249] [c0] dwmmc_exynos 12220000.dwmmc2: data CRC error READ
[ 16.498926] [c4] mmcblk1: error -84 transferring data, sector 2, nr 6, cmd response 0x900, card status 0x0
[ 16.508920] [c0] dwmmc_exynos 12220000.dwmmc2: data CRC error READ
[ 16.514647] [c4] mmcblk1: error -84 transferring data, sector 3, nr 5, cmd response 0x900, card status 0x0
[ 16.524752] [c0] dwmmc_exynos 12220000.dwmmc2: Start bit error (status=00002000)
[ 16.532030] [c4] mmcblk1: error -5 transferring data, sector 4, nr 4, cmd response 0x900, card status 0x0
[ 16.541706] [c0] dwmmc_exynos 12220000.dwmmc2: data CRC error READ
[ 16.547357] [c4] mmcblk1: error -84 transferring data, sector 5, nr 3, cmd response 0x900, card status 0x0
[ 16.557404] [c0] dwmmc_exynos 12220000.dwmmc2: data CRC error READ
[ 16.563364] [c4] mmcblk1: error -84 transferring data, sector 6, nr 2, cmd response 0x900, card status 0x0
[ 16.573363] [c0] dwmmc_exynos 12220000.dwmmc2: data CRC error READ
[ 16.579167] [c4] mmcblk1: error -84 transferring data, sector 7, nr 1, cmd response 0x900, card status 0x0
[ 16.588473] [c4] Buffer I/O error on device mmcblk1, logical block 0
Begin: Loading essential drivers ... done.
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ...
```
[/FONT][/COLOR][COLOR=#525E68][FONT=Source Sans Pro]
At this point the Artik just freezes. Is the Ubuntu version not compatible with the Artik 10 V 0.5 board?

Thanks, Raju[/FONT][/COLOR]

---

