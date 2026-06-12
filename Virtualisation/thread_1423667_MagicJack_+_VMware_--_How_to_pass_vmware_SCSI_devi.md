---
title: "MagicJack + VMware -- How to pass vmware SCSI devices?"
date: 2010-03-06
forum: Virtualisation
---

### Post by fermulator on 2010-03-06
I'm trying to get the "MagicJack" USB dongle to work in a WinXP guest OS using VMware server 2.

**_My Setup / Configuration:_**
 * VMware Server 2.0.0 (Build 122589)
 * Host OS: Ubuntu 8.04 LTS - (Linux fermmy-server 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux)
 * Guest OS: WinXP SP3 (Fresh Installation)

**_High Level Problem:_**

I followed the supposedly simple procedure here: [http://osdir.com/ml/ubuntu-users/2009-05/msg01554.html](http://osdir.com/ml/ubuntu-users/2009-05/msg01554.html)

 1. Boot WinXP VM.
 2. Plug in MagicJack
 3. In VM console, I see the following new device on the host: "TigerJet Network, Inc. USB Internet Phone by TigerJet"
 4. Click the "check box" next to this device to pass it through to the magic jack winxp vm.
 5. WinXP notices a few new devices in device manager, but no drivers for auto installation.

[IMG]http://img291.imageshack.us/img291/793/devicemanagermagicjack.jpg[/IMG]

After some reading, it appears that there's SUPPOSED to be a CD-ROM mounted (for drivers/installation?) and a virtual disk (~20MB) for (temp files?).

 ... on to the troubleshooting ...

**_Details & Troubleshooting:_**

The author of the above link (and several others in forums) report success with Ubuntu + VMware (XP guest OS) + MagicJack.  In fact, they all claimed that it was very easy ... there goes that (at least from my experience so far)

I modified the vmx file as per instructions:
> $ cat magic_jack.vmx | grep usb
usb.present = "TRUE"
usb.generic.skipsetconfig = "TRUE"
usb.pciSlotNumber = "32"
usb:0.present = "TRUE"
usb:1.present = "TRUE"
usb:1.deviceType = "hub"
usb:0.deviceType = "mouse"
usb.autoConnect.device0 = "path:4/0 autoclean:1"


When I plug in the MagicJack USB dongle, here's the dmesg output:

> [606282.296142] usb 4-1: USB disconnect, address 3
[606291.092042] usb 4-1: new full speed USB device using uhci_hcd and address 4
[606291.411266] usb 4-1: configuration #1 chosen from 1 choice
[606291.420179] scsi35 : SCSI emulation for USB Mass Storage devices
[606291.420535] usb-storage: device found at 4
[606291.420537] usb-storage: waiting for device to settle before scanning
[606291.471229] hiddev97hidraw1: USB HID v1.00 Device [TigerJet Network, Inc. USB Internet Phone by TigerJet] on usb-0000:00:1d.0-1
[606296.421943] usb-storage: device scan complete
[606296.424889] scsi 35:0:0:0: Direct-Access     TigerJet HardDisk         v2.0 PQ: 0 ANSI: 2
[606296.427875] scsi 35:0:0:1: CD-ROM            TigerJet CD-ROM           v2.0 PQ: 0 ANSI: 2
[606296.432841] sd 35:0:0:0: [sdn] 36352 512-byte hardware sectors (19 MB)
[606296.435874] sd 35:0:0:0: [sdn] Write Protect is off
[606296.435888] sd 35:0:0:0: [sdn] Mode Sense: 03 00 00 00
[606296.435891] sd 35:0:0:0: [sdn] Assuming drive cache: write through
[606296.445860] sd 35:0:0:0: [sdn] 36352 512-byte hardware sectors (19 MB)
[606296.448856] sd 35:0:0:0: [sdn] Write Protect is off
[606296.448867] sd 35:0:0:0: [sdn] Mode Sense: 03 00 00 00
[606296.448869] sd 35:0:0:0: [sdn] Assuming drive cache: write through
[606296.449437]  sdn: unknown partition table
[606296.658988] sd 35:0:0:0: [sdn] Attached SCSI removable disk
[606296.659325] sd 35:0:0:0: Attached scsi generic sg14 type 0
[606296.682841] sr1: scsi3-mmc drive: 0x/0x caddy
[606296.684170] sr 35:0:0:1: Attached scsi CD-ROM sr1
[606296.685356] sr 35:0:0:1: Attached scsi generic sg15 type 5

Here comes the interesting part, and the point of my post.  As we can see from dmesg, there are indeed two missing things from the vmware: /dev/sg14, and /dev/sg15.  Our mystery HDD and CD-ROM.

OK, so the first thing I tried was shutting down the WinXP VM, and adding these as SCSI passthrough devices.

Started up the vm again, but .. weird .. vmware issued some sort of "rescan" and caused the devices to become sg16 and sg17.  No matter what I've tried so far, if I configure pass-through in vmware console, after starting the WinXP VM, the SCSI IDs change for these two mystery HDD & CD-ROM.

In VMware console, if I try to "disconnect" and "reconnect" the MagicJack device, I get some warnidge in dmesg:

> [606687.540273] usb 4-1: usbfs: process 26168 (vmware-vmx) did not claim interface 2 before use
[606687.542567] usb 4-1: usbfs: process 26168 (vmware-vmx) did not claim interface 3 before use
[606687.562308] usb 4-1: usbfs: process 26168 (vmware-vmx) did not claim interface 2 before use
[606687.564870] usb 4-1: usbfs: process 26168 (vmware-vmx) did not claim interface 3 before use
[606687.572257] usb 4-1: usbfs: process 26168 (vmware-vmx) did not claim interface 1 before use
[606687.580304] usb 4-1: usbfs: process 26168 (vmware-vmx) did not claim interface 1 before use
[606687.592188] usb 4-1: usbfs: process 26168 (vmware-vmx) did not claim interface 4 before use
[606687.600423] usb 4-1: usbfs: process 26168 (vmware-vmx) did not claim interface 4 before use

**_The Question:_**
 * How to make vmware server 2 actually work with SCSI devices?

---

### Post by dcstar on 2010-03-08
> **fermulator said:**
> I'm trying to get the "MagicJack" USB dongle to work in a WinXP guest OS using VMware server 2.

**_My Setup / Configuration:_**
 * VMware Server 2.0.0 (Build 122589)
 * Host OS: Ubuntu 8.04 LTS - (Linux fermmy-server 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux)
 * Guest OS: WinXP SP3 (Fresh Installation)

**_High Level Problem:_**

I followed the supposedly simple procedure here: [http://osdir.com/ml/ubuntu-users/2009-05/msg01554.html](http://osdir.com/ml/ubuntu-users/2009-05/msg01554.html)

 1. Boot WinXP VM.
 2. Plug in MagicJack
 3. In VM console, I see the following new device on the host: "TigerJet Network, Inc. USB Internet Phone by TigerJet"
 4. Click the "check box" next to this device to pass it through to the magic jack winxp vm.
 5. WinXP notices a few new devices in device manager, but no drivers for auto installation.


After some reading, it appears that there's **SUPPOSED** to be a CD-ROM mounted (for drivers/installation?) and a virtual disk (~20MB) for (temp files?).
.........

"Supposed"?, like any Windows hardware installation **you** are supposed to put the driver CD in so the OS can detect it, have you done this and made the CD-ROM available to the VM?

---

### Post by fermulator on 2010-03-08
> **dcstar said:**
> "Supposed"?, like any Windows hardware installation **you** are supposed to put the driver CD in so the OS can detect it, have you done this and made the CD-ROM available to the VM?

It doesn't come with a "driver CD".  As I explained in my initial post, the USB dongle has a "SCSI" device (CD ROM & HDD) of which it uses to install Windows drivers.  As such, my primary question still holds :-)  -- how to make VMware forward those SCSI nodes into Windows....

---

### Post by dcstar on 2010-03-08
> **fermulator said:**
> It doesn't come with a "driver CD".  As I explained in my initial post, the USB dongle has a "SCSI" device (CD ROM & HDD) of which it uses to install Windows drivers.  As such, my primary question still holds :-)  -- how to make VMware forward those SCSI nodes into Windows....

If it is a USB device then I assume you should do the same as all VMware USB devices, either that or manually copy the files off that USB device on another Windows machine to something you can transfer to the VM.

If some hardware vendor makes some tricky new bit of equipment that doesn't conform to previous devices but is obviously tailored towards Windows, don't expect the Linux kernel to have support for it.

---

### Post by fermulator on 2010-03-08
> **dcstar said:**
> If it is a USB device then I assume you should do the same as all VMware USB devices, either that or manually copy the files off that USB device on another Windows machine to something you can transfer to the VM.

If some hardware vendor makes some tricky new bit of equipment that doesn't conform to previous devices but is obviously tailored towards Windows, don't expect the Linux kernel to have support for it.

OK, I don't want to come across as rude here, not trying to be, but I will be blunt.

Can you please actually read my post before replying?  You're comments seem to indicate that you have not fully read the details in the post :-(  I'm sorry if you did already read the post ... just getting the impression that you missed the point.

---

### Post by dcstar on 2010-03-08
> **fermulator said:**
> OK, I don't want to come across as rude here, not trying to be, but I will be blunt.

Can you please actually read my post before replying?  You're comments seem to indicate that you have not fully read the details in the post :-(  I'm sorry if you did already read the post ... just getting the impression that you missed the point.

[LIST=1]
[*]You have a multi-use USB device - one that does multiple functions - how many listings for it do you see on the VMware console?
[*]Have you previously successfully used USB drives in your VMs?
[/LIST]

---

### Post by fermulator on 2010-03-08
1. Yes it would seem that the USB device here has multiple functions to it.  However, in the vmware console, it detects only one functionality of the USB device ... as far as I can tell, it only detects the "actual device" as a USB device.  The other two (CD-ROM and HDD) are not detected in vmware as a USB device.  Ubuntu detects these two other devices (CD-ROM and HDD) as SCSI devices /dev/sg##.  The problem is that I can't get vmware to passthrough these SCSI devices to the guest OS.

 2. I've never tried to get a standalone external USB drive to work in VM ware.  I could try to plug one in later to see if it comes up as a "USB device" that VMware recognizes, or if it's a SCSI device.  This will be interesting information to know, but I guess it doesn't really help with the SCSI passthrough problem.

---

### Post by dcstar on 2010-03-08
> **fermulator said:**
> 1. Yes it would seem that the USB device here has multiple functions to it.  However, in the vmware console, it detects only one functionality of the USB device ... as far as I can tell, it only detects the "actual device" as a USB device.  The other two (CD-ROM and HDD) are not detected in vmware as a USB device.  Ubuntu detects these two other devices (CD-ROM and HDD) as SCSI devices /dev/sg##.  The problem is that I can't get vmware to passthrough these SCSI devices to the guest OS.

 2. I've never tried to get a standalone external USB drive to work in VM ware.  I could try to plug one in later to see if it comes up as a "USB device" that VMware recognizes, or if it's a SCSI device.  This will be interesting information to know, but I guess it doesn't really help with the SCSI passthrough problem.

There are specific things that have to be done to the host Ubuntu system to get USB drives to work in VMware Server, I have been assuming that you already have a fully working VMware Server setup and all these things already work with "normal" USB drives.

If this is not the case then it is no wonder these issues have arisen.

---

### Post by tester321 on 2010-09-04
@fermulator: I am not sure if you still need a solution to this ... I happened upon this thread while browsing for other stuff.

[This post]("http://www.widwad.com/content/running-magicjack-from-a-windows-xp-guest-on-vmware-on-linux-how-i-did-it") might help you -- it outlines how to get magicjack to work on a Windows XP Guest on vmware on Ubuntu.  Note that it is vmware server 1; not sure about vmware server 2 as I have opted to remain on server 1 on purpose.

Successfully used this setup since 2008.

Hope it helps!

---

### Post by lbrty on 2010-09-08
My setup is below. I have been using this for the past two weeks and it works perfectly.

Ubuntu 10.04 LTS Lucid Lynx
VMWare Player
Install Windows operating system within VMWare Player (in my case Windows XP)
Plugin in your magicJack and your ready to make calls!

---

