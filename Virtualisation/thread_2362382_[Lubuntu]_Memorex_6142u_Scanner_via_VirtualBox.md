---
title: "[Lubuntu] Memorex 6142u Scanner via VirtualBox"
date: 2017-05-27
forum: Virtualisation
---

### Post by gaurav20 on 2017-05-27
Hi,

I am trying to configure my memorex 6142u flatbed scanner on lubuntu. According to this post, [https://ubuntuforums.org/showthread.php?t=924173](https://ubuntuforums.org/showthread.php?t=924173). The user was able to use virtualbox and acsess the scanner to scan with a Windows 2000 Guest OS.

I have a virtual machine with Windows 2000. (Which is supported) How would I access the scanner?

---

### Post by efflandt on 2017-05-28
You would need a proper twain driver or scanning software that works in Windows 2000.

I have a somewhat similar issue with a Lexmark X204n network printer/scanner. The 64-bit sane driver works in Ubuntu 14.04 (as host or vbox guest) and their 32-bit sane driver works in 32-bit 16.04 in virtualbox (which I was using for 32-bit only WebEx). But the 64-bit sane driver does not seem to work on 64-bit 16.04 or 16.10 host. But printing is no problem because it does postscript (and HP PCL). You just need a proper driver or software with the driver for the OS you are trying to scan from.

---

### Post by gaurav20 on 2017-05-29
I installed the drivers in Windows 2000. And I checked if the scanner is supported by SANE. (It isn't). However I found it.

sudo sane-find-scanner
[sudo] password for gaurav: 


  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x0461 [Primax], product=0x0347 [USB Scanner]) at libusb:005:004

Now the only issue I am encountering, is how to get virtualbox to find the scanner.

---

### Post by Bucky Ball on 2017-05-29
If it is USB, you will need the Extensions Pack as far as I know. The Extension Pack needs to be the same version number as the Virtualbox version you have installed.

efflandt may be able to confirm as they may be using a USB printer themselves, but I will say this. You would do well to get this going in Ubuntu first. If Ubuntu doesn't see it, unsure your virtual machine will.

---

### Post by gaurav20 on 2017-05-29
I just used the lsusb command and I found it there too. So, I think it really is a problem with vbox seeing the scanner at this point.

---

### Post by Bucky Ball on 2017-05-29
As I say, if it's USB, you'll probably need to install the same Virtualbox Extensions Pack version as your Virtualbox for Virtualbox to use anything USB, printer or otherwise. Guest Additions will not give USB, unless something has changed. Been a couple of months since I used VBox, but that's exactly what I did.

Good luck with it. ;)

---

### Post by howefield on 2017-05-29
Thread moved to the "*Virtualisation*" forum.

---

### Post by coolgauru on 2017-05-30
I got the extension pack, but for some reason, the scanner still does not show up.

---

### Post by efflandt on 2017-05-31
I am a little confused between Extension Pack and Guest Additions. And I have not done anything directly on USB from a guest (my scanner is network scanner). But did you install the Guest Additions by doing Devices > "Insert Guest Additions CD Image" from virtualbox menus on host while the guest is running, and then running the Guest Additions on the guest from that virtual CD if that does not autorun?

---

