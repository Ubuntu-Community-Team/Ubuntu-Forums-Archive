---
title: "Suspend broken on SERP3 + 10.04 Lucid"
date: 2010-05-07
forum: System76 Support
---

### Post by haydnv on 2010-05-07
Lucid (fresh install) breaks suspend on my SERP3 - here's (I think) the relevant kern.log:

> main kernel: [99371.053066] PM: Preparing system for mem sleep
main kernel: [99371.053072] Freezing user space processes ... (elapsed 0.00 seconds) done.
main kernel: [99371.053881] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
main kernel: [99371.053924] PM: Entering mem sleep
main kernel: [99371.053934] Suspending console(s) (use no_console_suspend to debug)
main kernel: [99371.100112] sd 2:0:0:0: [sda] Synchronizing SCSI cache
main kernel: [99371.100350] sd 2:0:0:0: [sda] Stopping disk
main kernel: [99371.602174] PM: suspend of drv:sd dev:2:0:0:0 complete after 502.062 msecs
main kernel: [99372.021281] PM: suspend of drvsmouse dev:serio1 complete after 405.057 msecs
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

### Post by thomasaaron on 2010-05-10
Not exactly sure. Please post the output of...

lspci

...and...

lsusb

Also, go to System > Admin > Hardware Drivers and make sure your nVidia driver is enabled. Then reboot (after enabling it, if it wasn't enabled to begin with ).

---

### Post by haydnv on 2010-05-16
NVidia driver is enabled.

Here's lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
0e:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0e:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0e:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0e:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev ff)

```

and lsusb:
```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b018 Chicony Electronics Co., Ltd 2M UVC Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by catalyst294 on 2010-05-17
I have the same problem. I get this error when trying to suspend or hibernate and it sends me back to the unlock screen. I have a SERP4 though, if that makes a difference. Also my lsusb and lspci outputs are the same as haydnv's output.

---

### Post by isantop on 2010-05-17
Please contact me via email at support...at...system76...dot...com. We'll get this problem fixed up quickly.

---

### Post by Vadi on 2010-05-19
Same issue on same hardware

> vadi@vadi-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
0e:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0e:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0e:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0e:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev ff)
vadi@vadi-laptop:~$ 


> vadi@vadi-laptop:~$ lsusb
Bus 007 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 047f:d955 Plantronics, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b018 Chicony Electronics Co., Ltd 2M UVC Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
vadi@vadi-laptop:~$ 


---

### Post by Vadi on 2010-05-23
Are there any news on this by chance?

---

### Post by isantop on 2010-05-24
We are working on it over here, but this is a strange one. We'll keep you guys updated on the status of this.

---

### Post by isantop on 2010-05-25
Today I finished getting a test system set up, and updated. 

I got no problems with suspend and resume. Maybe try making sure you have the latest System76 Driver installed, then try installing drivers from there.

It may be nothing related, but this is on a fresh install. I wouldn't try that yet though, unless you're really desperate.

Try this:
Reboot your system. Take note of the time on the clock, then try and suspend it. If it fails, goto System > Administration > System76 Driver, click on the support tab, then click create. This will create a log archive in your home folder. Send us that file as an attachment to support...at...system76...dot...com and we'll have a look.

---

### Post by Sean-Michael on 2010-05-25
I had a problem with one of our computers, it would suspend where it used to activate the screen saver... when I tried to bring it back out of suspend it seemed to freez but actually the screen froze, I entered my password and the computer came back.

I ended up changing the preferences to not suspend and all well with that one now.

Hope that helps.

---

### Post by haydnv on 2010-05-27
Installed the system76 driver - tells me all dependencies are satisfied by Ubuntu.

---

### Post by compholio on 2010-06-02
I haven't visited the forum in a while and I decided to pop on by.  Hopefully, this visit will be helpful for tracking down your problem as I have a SERP3 where suspend works on 10.04.  It appears that I have different wireless card than you folks:
```
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

The rest of my lspci matches up, as does my lsusb.

---

### Post by catalyst294 on 2010-06-15
So the latest round of updates fix the problem for me!

Hooray!

---

### Post by Vadi on 2010-06-22
Not for me. Laptop still can't suspend.

---

### Post by isantop on 2010-06-23
> **Vadi said:**
> Not for me. Laptop still can't suspend.

Make sure you have proposed and backports enabled. The cause for this bug is specifically a bug in the 2.6.32 kernel that comes with Lucid. This all works great in Maverick, so they should backport it to Lucid.

---

### Post by Vadi on 2010-06-28
Thanks, got it working.

---

