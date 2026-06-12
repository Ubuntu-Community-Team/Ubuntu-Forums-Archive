---
title: "Unable to find a medium containing a live file system"
date: 2013-01-14
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2013-01-14
Since the early days of Rairing I have been unable to run a Raring live session or install. Every daily image I try dumps me at a Busybox (initramfs) command line with the message: "Unable to find a medium with a live file system."

This has happened on Raring images for Ubuntu amd64 (last tried 20130112), amd64+mac (20130112), i386 (20130113) and Kubuntu (20130114).

Other images work fine. Such as 12.04.1; Ubuntu Gnome Remix (12.10); Ubuntu Secure Remix (12.10).

The motherboard is 5 years old with a boring, standard BIOS. Removing 'quiet splash' shows the loading stopping at Initializing Nouveau. Adding 'debug' to the boot parameters confirms that it is in a panic because it cannot find a live file system. It then runs scripts to set up the Busybox console.

Anybody else getting this?

I found this old bug

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/817145]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/817145")

And added my comments to it. Error messages are there. I am at the bottom. I also reported it on QA testing tracker.

Regards.

---

### Post by dino99 on 2013-01-14
are the working images using the same device (hdd) than those not working ?

because the bug owner said:

**** Modifying BIOS settings to use AHCI instead of IDE for sata related stuff fixed the issue. ****

---

### Post by grahammechanical on 2013-01-14
> **dino99 said:**
> are the working images using the same device (hdd) than those not working ?

because the bug owner said:

**** Modifying BIOS settings to use AHCI instead of IDE for sata related stuff fixed the issue. ****

I went through the BIOS about 2 hours ago. I am sure that the SATA drive is not set to work as IDE. I remember looking at those settings. I have not tried an image since then. Been doing other work. I will double check. I only have one drive and it is SATA.

And I am trying different images on different disks. On disks I know work.

But why would 12.04 and 12.10 images work but not Raring images? As a Vulcan once said: "It is not logical. Jim."

Thanks for thinking about this.

---

### Post by ventrical on 2013-01-14
I am interested in your  lspci  output please.

---

### Post by ventrical on 2013-01-14
This is not quite the same problem but I just updated my Intel BIOS. I had been having some problems with the BIOS recognizing the PCI-e 3.0 USB card. In the BIOS it refers to then as 'bootable cards'. When I go to BIOS I can't move the up/down priority. It osrt of gets locked up. Even after the update, now the USB boot default is gone. I had been having a similar problem with my SATA drive and  USB. I would have to shut down  and switch the SATA drive to a different socket and then reboot and the USB option would return.

  Currently I am on IDE Enabled and that is the only way the SATA (or CD/DVD for that matter ) will work. I also had to remove the 80 line UDMA cable to the DVD drive(used 40 line cable) and that restored it somewhat also. I am about to stick the USB PCI-e  3.0 card back in and see what happens.

  My apologies if this is off topic.

 And now I find that it is almost impossible to find a Pentium D 3.4 GHz processor for this machine.

Oh the joy. :)

---

### Post by grahammechanical on 2013-01-14
An update.

SATA was set to Enhanced with another setting - Configure SATA set to IDE. The other two options are RAID and AHCI. So, I changed it to AHCI. Does not resolve the problem of Raring ISO images unable to find a medium with a live file system but the machine does seem to boot faster.

> graham@Seven-Raring:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation GT216 [GeForce GT 220] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
04:00.0 Multimedia video controller: Micronas Semiconductor Holding AG nGene PCI-Express Multimedia Controller
06:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
06:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)

As requested. I will come back to this issue tomorrow. Time for evening meal.

P.S. Regarding the off topic subject. In  my BIOS if I have legacy floppy set then I lose USB options including boot order options. I found this out last year when I installed Ubuntu on a USB stick. A little later I hit the Power button just after I pressed it to power on - stopped it booting and I had to use the previous boot profile to boot. Phew! But I lost the ability to boot from USB because I had reverted back to legacy floppy being set.

Regards.

---

### Post by ventrical on 2013-01-14
> **grahammechanical said:**
> An update.

SATA was set to Enhanced with another setting - Configure SATA set to IDE. The other two options are RAID and AHCI. So, I changed it to AHCI. Does not resolve the problem of Raring ISO images unable to find a medium with a live file system but the machine does seem to boot faster.



As requested. I will come back to this issue tomorrow. Time for evening meal.

P.S. Regarding the off topic subject. In  my BIOS if I have legacy floppy set then I lose USB options including boot order options. I found this out last year when I installed Ubuntu on a USB stick. A little later I hit the Power button just after I pressed it to power on - stopped it booting and I had to use the previous boot profile to boot. Phew! But I lost the ability to boot from USB because I had reverted back to legacy floppy being set.

Regards.

  I had the exact same thing happen here except I had to enable "Plug-n-Pray' in the BIOS to get the Floppy working so I could burn in the updated BIOS. All went well but now I can't find the enable/disable Plug n' Play and I too now cannot boot from the USB without the PLOP bootloader (err mabey even thats broke now too.

---

### Post by ventrical on 2013-01-14
Looks like you have 2 SATA controllers.

---

### Post by george83 on 2013-01-15
I had the same prob. Press F6 in the purple screen before the dots, F6 again for "Other Options" check the 2 first "acpi=off" and "noapic" then try Ubuntu without instaling. That worked for me.

---

### Post by grahammechanical on 2013-01-16
Sorry people, I have been 'unavailable for comment' during Tuesday = shopping.

Yes I do have two SATA controllers. One gives 6 x SATA drives and the other gives 1 x UltraDMA for 2 x PATA devices, 1 x internal SATA port and 1 x external SATA port (SATA-On-the Go). I have over capacity on my motherboard for what I use this machine for.

Situations where the Raring image dumps me at a Busybox prompt

1) All F6 options when used on their own.
2) noapic + nolapic.
3) acpi=off + edd=on.

Situations where I get a live session.

1) acpi=off + noapic > slow, slow, very slow loading + blackscreen = slow, slow, very slow live session. Both CPUs running at 30%. It is as if 1GB is not enough memory to run the session. Do not hold breath waiting for things to happen.

2) acpi=off + nolapic > slow, slow loading + blackscreen  = slow but usable live session. Take a deep breath before running a task. System monitor only shows one CPU on this dual core CPU and it is running at 100%.

In the meantime my beard has grown an inch. Testing finished for today. Will try an install tomorrow.

Remember, If you can't take a joke, then you shouldn't have joined. My testing motto.

_Update: 17/01/2013_

I just put in an install using acpi=off + nolapic. It is not what I would call a satisfactory user experience when I have to spend so long looking at "Check askubuntu.com for all your Ubuntu questions" :) as the install process is very slow.

_Update 19/01/2013_

I can get a reasonable live session from using F6 option acpi=off and adding irqpoll to the boot parameters. The session loads as fast as it should and runs as fast as usual. I have never needed these options before.

Regards.

---

