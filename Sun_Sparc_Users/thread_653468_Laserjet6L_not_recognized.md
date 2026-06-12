---
title: "Laserjet6L not recognized?"
date: 2007-12-29
forum: Sun Sparc Users
---

### Post by earthforce_1 on 2007-12-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/178822](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/178822) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have installed the Ubuntu Sparc64 bit server on my Ultra 5, but CUPS does not recognize my parallel port based Laserjet6L.  I previously ran the latest stock debian on the same machine which successfully detected and configured my printer.  It is "sort of" recognized, but CUPS cannot see it.

lsmod | grep lp
lp                     14040  0 
parport                43600  3 ppdev,parport_pc,lp

 dmesg | grep par 
[    0.000000] Linux version 2.6.22-14-sparc64 (buildd@vivies) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 Tue Dec 18 04:42:46 UTC 2007 (Ubuntu 2.6.22-14.47-sparc64)
[   33.436951]  hdb: unknown partition table
[   81.233171] parport0: PC-style at 0x1fff13043bc (0x1fff13047bc), irq 8, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   81.282467] parport0: Printer, Hewlett-Packard HP LaserJet 6L
[   81.293811] lp0: using parport0 (interrupt-driven).
[   81.396871] ppdev: user-space parallel port driver
[  611.542765] ppdev0: registered pardevice
[  612.661596] ppdev0: unregistered pardevice
[  613.857305] ioctl32(parallel:4149): Unknown cmd fd(4) cmd(44005001){t:'P';sz:1024} arg(ffb26a74) on /dev/lp0
[  616.502235] ppdev0: registered pardevice
[  617.580468] ppdev0: unregistered pardevice
[ 2677.072211] ppdev0: registered pardevice
[ 2678.119897] ppdev0: unregistered pardevice
[ 2679.271605] ioctl32(parallel:4961): Unknown cmd fd(4) cmd(44005001){t:'P';sz:1024} arg(ffa96a74) on /dev/lp0
[ 2681.412970] ppdev0: registered pardevice
[ 2682.446915] ppdev0: unregistered pardevice
[ 3921.424179] ppdev0: registered pardevice
[ 3922.470363] ppdev0: unregistered pardevice
[ 3923.618071] ioctl32(parallel:5113): Unknown cmd fd(4) cmd(44005001){t:'P';sz:1024} arg(ffe3ea74) on /dev/lp0
[ 3925.764810] ppdev0: registered pardevice
[ 3926.893359] ppdev0: unregistered pardevice

 lpinfo -v
network socket
network beh
direct hpfax
direct hp
network http
network ipp
network lpd
direct parallel:/dev/lp0
direct scsi

tail -20 /var/log/cups/error_log
D [29/Dec/2007:23:25:20 -0500] CUPS-Get-Default client-error-not-found: No default printer
D [29/Dec/2007:23:25:20 -0500] cupsdProcessIPPRequest: 9 status_code=406 (client-error-not-found)
D [29/Dec/2007:23:25:20 -0500] cupsdCloseClient: 9
D [29/Dec/2007:23:26:36 -0500] cupsdAcceptClient: 9 from localhost (Domain)
D [29/Dec/2007:23:26:36 -0500] cupsdReadClient: 9 POST / HTTP/1.1
D [29/Dec/2007:23:26:36 -0500] cupsdAuthorize: No authentication data provided.
D [29/Dec/2007:23:26:36 -0500] CUPS-Get-Printers
D [29/Dec/2007:23:26:36 -0500] CUPS-Get-Printers client-error-not-found: No destinations added.
D [29/Dec/2007:23:26:36 -0500] cupsdProcessIPPRequest: 9 status_code=406 (client-error-not-found)
D [29/Dec/2007:23:26:36 -0500] cupsdReadClient: 9 POST / HTTP/1.1
D [29/Dec/2007:23:26:36 -0500] cupsdAuthorize: No authentication data provided.
D [29/Dec/2007:23:26:36 -0500] CUPS-Get-Classes
D [29/Dec/2007:23:26:36 -0500] CUPS-Get-Classes client-error-not-found: No destinations added.
D [29/Dec/2007:23:26:36 -0500] cupsdProcessIPPRequest: 9 status_code=406 (client-error-not-found)
D [29/Dec/2007:23:26:36 -0500] cupsdReadClient: 9 POST / HTTP/1.1
D [29/Dec/2007:23:26:36 -0500] cupsdAuthorize: No authentication data provided.
D [29/Dec/2007:23:26:36 -0500] CUPS-Get-Default
D [29/Dec/2007:23:26:36 -0500] CUPS-Get-Default client-error-not-found: No default printer
D [29/Dec/2007:23:26:36 -0500] cupsdProcessIPPRequest: 9 status_code=406 (client-error-not-found)
D [29/Dec/2007:23:26:36 -0500] cupsdCloseClient: 9

 tail -20 /var/log/messages
Dec 29 17:16:57 zack -- MARK --
Dec 29 17:36:57 zack -- MARK --
Dec 29 17:53:57 zack kernel: [249446.060589] UDF-fs: No VRS found
Dec 29 18:16:57 zack -- MARK --
Dec 29 18:36:57 zack -- MARK --
Dec 29 18:56:57 zack -- MARK --
Dec 29 19:16:57 zack -- MARK --
Dec 29 19:36:57 zack -- MARK --
Dec 29 19:56:57 zack -- MARK --
Dec 29 20:16:57 zack -- MARK --
Dec 29 20:36:57 zack -- MARK --
Dec 29 20:56:57 zack -- MARK --
Dec 29 21:01:33 zack kernel: [260699.546784] ioctl32(parallel:11628): Unknown cmd fd(4) cmd(44005001){t:'P';sz:1024} arg(ffb08a74) on /dev/lp0

---

