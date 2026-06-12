---
title: "Darter USB drive troubles"
date: 2007-05-06
forum: System76 Support
---

### Post by zaroff on 2007-05-06
Under Feisty, I've been having some big troubles with USB drives on my Darter.  I've tried 3 different USB sticks and a USB hard drive with the same results.  I plug in the drive and nothing happens.  No window displaying the drive contents, no automounting.  I decided to dig a little deeper.  Here's the output of /var/log/messages when plugging in a typical drive:

May  6 21:05:36 lappy76 kernel: [  358.092000] usb 1-3: new high speed USB device using ehci_hcd and address 3
May  6 21:05:36 lappy76 kernel: [  358.232000] usb 1-3: configuration #1 chosen from 1 choice
May  6 21:05:36 lappy76 kernel: [  358.352000] usbcore: registered new interface driver libusual
May  6 21:05:36 lappy76 kernel: [  358.360000] Initializing USB Mass Storage driver...
May  6 21:05:36 lappy76 kernel: [  358.360000] scsi0 : SCSI emulation for USB Mass Storage devices
May  6 21:05:36 lappy76 kernel: [  358.364000] usbcore: registered new interface driver usb-storage
May  6 21:05:36 lappy76 kernel: [  358.364000] USB Mass Storage support registered.
May  6 21:05:41 lappy76 kernel: [  363.368000] scsi 0:0:0:0: Direct-Access     Imation   USB Flash Drive 2.00 PQ: 0 ANSI: 2
May  6 21:05:43 lappy76 kernel: [  365.432000] ready
May  6 21:05:43 lappy76 kernel: [  365.432000] SCSI device sda: 2037760 512-byte hdwr sectors (1043 MB)
May  6 21:05:43 lappy76 kernel: [  365.436000] sda: Write Protect is off
May  6 21:05:43 lappy76 kernel: [  365.436000] SCSI device sda: 2037760 512-byte hdwr sectors (1043 MB)
May  6 21:05:43 lappy76 kernel: [  365.436000] sda: Write Protect is off
May  6 21:05:43 lappy76 kernel: [  365.440000]  sda: sda1
May  6 21:05:43 lappy76 kernel: [  365.440000] sd 0:0:0:0: Attached scsi removable disk sda
May  6 21:05:43 lappy76 kernel: [  365.456000] sd 0:0:0:0: Attached scsi generic sg0 type 0

Now my root partition is detected (or at least mounted) as sda1 in Feisty and what's happening here is that the USB drive is also being detected as sda.  Now I can manually mount this "new" sda1 from the command line:

sudo mount /dev/sda1 mnt

I can then browse the contents.  Next I unmount the drive:

sudo umount mnt

No problems yet.  Now I unplug the drive and the real trouble begins.  The system monitor applet on the panel crashes.  It asks if I want to reload, so I click 'Reload'.  Both panels (top and bottom) freak out and disappear.  My desktop is left but useless.  Ctrl+Alt+Backspace gets me out of X and back to the console but X doesn't respawn.  Ctrl+Alt+Del reboots and is the only way to get things back to normal.

So it looks like this meltdown is a result of the system getting the hard drive and USB drive confused since both are being detected as sda1.

Has anyone else had this problem?  Any thoughts?

---

### Post by zaroff on 2007-05-07
I just discovered that the cause of this problem is that after install changed my fstab from UUIDs to devices.  Changing back to UUIDs seems to have eliminated the problem entirely.

---

