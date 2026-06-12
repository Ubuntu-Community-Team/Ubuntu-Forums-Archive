---
title: "load Win8 as vbox guest"
date: 2013-09-02
forum: Virtualisation
---

### Post by dbclin2 on 2013-09-02
I'm running Ubuntu 12.04 and I've got a (legal) USB backup of Win8 that I'd like to run through vbox. I'm stumped right from the start because vbox doesn't recognize my USB device (nor does Ubuntu, but that's less of a surprise). Any ideas?
Thanks,

---

### Post by TheFu on 2013-09-02
Is your license for any machine or OEM locked to specific hardware?  
Is the license for virtual machines?

Running any OS on USB storage is slow.  Even USB3 has issues with queuing if more than a few requests occur concurrently. At least that has been my experience. I don't think VBox does USB3 passthru yet, does it?  Could be wrong about that.

Does the host OS see the USB device at all? What do the logs show? Check my sig for links, if you need them.

---

### Post by dbclin2 on 2013-09-02
> Is your license for any machine or OEM locked to specific hardware?
It's locked...but this is the machine I'm trying to run it on (just with Ubuntu as its host).
> Is the license for virtual machines?
I have no clue. 
> Running any OS on USB storage is slow.
The truth is that I would really like to install Win8 to vbox from the usb. That should, in theory, work better.
> Does the host OS see the USB device at all? What do the logs show? Check my sig for links, if you need them.
I'll check that. 
Thanks!

---

### Post by dbclin2 on 2013-09-02
> Does the host OS see the USB device at all? What do the logs show? Check my sig for links, if you need them.
The host certainly does see the drive. Here's the output from syslog:
> Sep  2 20:03:49 dbclinton kernel: [11765.613487] usb 6-2.2.2: new full-speed USB device number 7 using uhci_hcd
Sep  2 20:03:49 dbclinton kernel: [11765.731481] usb 6-2.2.2: not running at top speed; connect to a high speed hub
Sep  2 20:03:49 dbclinton mtp-probe: checking bus 6, device 7: "/sys/devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2.2/6-2.2.2"
Sep  2 20:03:49 dbclinton mtp-probe: bus: 6, device: 7 was not an MTP device
Sep  2 20:03:49 dbclinton kernel: [11767.002371] Initializing USB Mass Storage driver...
Sep  2 20:03:49 dbclinton kernel: [11767.002536] scsi8 : usb-storage 6-2.2.2:1.0
Sep  2 20:03:49 dbclinton kernel: [11767.002633] usbcore: registered new interface driver usb-storage
Sep  2 20:03:49 dbclinton kernel: [11767.002635] USB Mass Storage support registered.
Sep  2 20:03:50 dbclinton kernel: [11768.004582] scsi 8:0:0:0: Direct-Access     Staples  Relay UFD        1.26 PQ: 0 ANSI: 5
Sep  2 20:03:50 dbclinton kernel: [11768.005185] sd 8:0:0:0: Attached scsi generic sg2 type 0
Sep  2 20:03:50 dbclinton kernel: [11768.011014] sd 8:0:0:0: [sdb] 31266816 512-byte logical blocks: (16.0 GB/14.9 GiB)
Sep  2 20:03:50 dbclinton kernel: [11768.015568] sd 8:0:0:0: [sdb] Write Protect is off
Sep  2 20:03:50 dbclinton kernel: [11768.015571] sd 8:0:0:0: [sdb] Mode Sense: 43 00 00 00
Sep  2 20:03:50 dbclinton kernel: [11768.019570] sd 8:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Sep  2 20:03:51 dbclinton kernel: [11768.054633]  sdb: sdb1
Sep  2 20:03:51 dbclinton kernel: [11768.071578] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Thanks!

---

### Post by TheFu on 2013-09-02
Which version of virtualbox are you running?  The proprietary version is needed for USB passthru, I think.
Plus the proprietary version of the guest additions too - USB license stuff.

So, Ubuntu on the hostOS can mount the USB drive? If so, what's the issue?  I must not understand something.  Have you tried mounting /dev/sdb1, then copying the files over?  The VM doesn't need access to any USB devices if you do that.

---

### Post by dbclin2 on 2013-09-03
> Have you tried mounting /dev/sdb1, then copying the files over?
That works (now that you mention it). Although there are a definitely files that remain invisible even under ls -a. I guess I could somehow then mount the whole thing as a hard drive that the Win8 boot process under Vbox would be able to find.
Any good links for that?
Thanks so much,

---

### Post by JKyleOKC on 2013-09-03
> **dbclin2 said:**
> It's locked...but this is the machine I'm trying to run it on (just with Ubuntu as its host).I don't think it can possibly work, for several reasons.

First, while the vbox VM does live on the host machine, vbox itself totally hides the host hardware from its VMs, and instead shows its own virtual hardware. Because of this, any locked package won't run on one of the VMs. You have to have an unlocked standalone OS to be able to install it and activate the correct drivers for the virtual hardware.

Second, Win8 requires the "Secure Boot" capability in the BIOS of the machine in which it's installed, in order to boot. Since the virtual BIOS of any vbox guest machine doesn't include that capability, and isn't likely to do so any time in the future because Microsoft charges a license fee to provide it, even if by some chance you did manage to install from the backup or bought a standalone copy, it would not be able to boot and run.

Bottom line is that virtualizing a fully legal Win8 system is likely to remain impossible for the foreseeable future, although I'm certain that cracked versions will appear (if they haven't already)...

---

### Post by dbclin2 on 2013-09-03
> I don't think it can possibly work, for several reasons...
Darn. 
Thanks

---

### Post by TheFu on 2013-09-03
I agree on most things said, however, Win8 does not require secure boot. That can be disabled in the BIOS, if you like.  Secure Boot must come with Win8 Certified machines and be enabled by default. It can be turned off according the the UEFI how-to for Ubuntu. [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Now ... once Windows is installed with UEFI BIOS, it must be retained, so if VirtualBox BIOS isn't UEFI compliant, then his backup will never work. That doesn't mean he can't restore data files into a new VM or that he can't create a new install disc from the old Win8 install and elect to re-install without UEFI - there must be a legacy mode, right?  Lots of older machines have Win8 installed without UEFI.

You can definitely run Win8 inside a VM under Ubuntu, but you'll probably never be able to run "that specific backup" in that way.  I though I'd said that already?  Guess hearing it from a different person helps with clarity.

Sorry - I was confused. It must have been a different thread.

---

### Post by Jonathan Precise on 2013-09-06
Good news:

> **TheFu said:**
> Now ... once Windows is installed with UEFI BIOS, it must be retained, so if VirtualBox BIOS isn't UEFI compliant, then his backup will never work. That doesn't mean he can't restore data files into a new VM or that he can't create a new install disc from the old Win8 install and elect to re-install without UEFI - there must be a legacy mode, right?  Lots of older machines have Win8 installed without UEFI.

Virtualbox has an option for EFI support.:)
[HR][/HR]Bad news:

> You can definitely run Win8 inside a VM under Ubuntu, but you'll probably never be able to run "that specific backup" in that way.

If it is locked to your PC's hardware, then you will probably never run the backup in that way, as the Virtual Machine simulates its own hardware.:(

---

### Post by dbclin2 on 2013-09-08
Thanks for all your helpful (if depressing) responses!
I appreciate it.

---

