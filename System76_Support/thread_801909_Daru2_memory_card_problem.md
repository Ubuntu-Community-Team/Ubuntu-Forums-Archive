---
title: "Daru2 memory card problem"
date: 2008-05-21
forum: System76 Support
---

### Post by Peneus on 2008-05-21
Hello,

I am using an up to date Hardy with drivers version 2.2.1 on a Daru2 machine.
For some reason when put a memory card into the card reader nothing happens. 
I cannot see the cards. Any help will be greatly appreciated.

---

### Post by jdb on 2008-05-21
I just tried a memory card in my Daru2 running Hardy with the latest updates & it works fine.
I'm running 32 bit & xubuntu so that could make a difference.
Also the card was formated to ext3, I don't have a vfat card.
I do have a usb fob formated to vfat & it works.

jdb

---

### Post by thomasaaron on 2008-05-21
What was the card originally used in. Some formats (including those used by Palm devices and some cameras) may not be recognized.

Open a terminal and enter this command:
tail -f /var/log/syslog

Then insert a card and see if you get any output. Let us know what you see.

---

### Post by Peneus on 2008-05-21
I forgot to mention that i use 64-bit Ubuntu. Here is the output:

$ tail -f /var/log/syslog
May 21 16:11:03 peneusl kernel: [ 1139.761288] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._BST] (Node ffff81007d72be00), AE_TIME
May 21 16:11:03 peneusl kernel: [ 1139.761366] ACPI Exception (battery-0356): AE_TIME, Evaluating _BST [20070126]
May 21 16:13:03 peneusl kernel: [ 1226.352342] ACPI: EC: acpi_ec_wait timeout, status = 0, expect_event = 1
May 21 16:13:03 peneusl kernel: [ 1226.352353] ACPI: EC: read timeout, command = 128
May 21 16:13:03 peneusl kernel: [ 1226.352362] ACPI Exception (evregion-0420): AE_TIME, Returned by Handler for [EmbeddedControl] [20070126]
May 21 16:13:03 peneusl kernel: [ 1226.352379] ACPI Exception (dswexec-0462): AE_TIME, While resolving operands for [OpcodeName unavailable] [20070126]
May 21 16:13:03 peneusl kernel: [ 1226.352395] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1.UPBS] (Node ffff81007d72be80), AE_TIME
May 21 16:13:03 peneusl kernel: [ 1226.352487] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._BST] (Node ffff81007d72be00), AE_TIME
May 21 16:13:03 peneusl kernel: [ 1226.352564] ACPI Exception (battery-0356): AE_TIME, Evaluating _BST [20070126]
May 21 16:17:01 peneusl /USR/SBIN/CRON[8526]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 21 16:18:55 peneusl kernel: [ 1458.941003] mmc1: unrecognised SCR structure version 1
May 21 16:18:55 peneusl kernel: [ 1458.941030] mmc1: error -22 whilst initialising SD card

---

### Post by Peneus on 2008-05-21
I again forgot to mention that the card is being used in a Vivitar ViviCam6300
digital camera.

Thanks

---

### Post by thomasaaron on 2008-05-21
OK. So your card reader is working fine. It just can't work with that particular card. Possible causes include:

1. Broken card
2. Unrecognizable file system.

If the card still works in your vivitar, then the filesystem is just not compatible. If you want to use it in your computer, you might try reformatting it as fat16 or ext3 using Partition Editor:

sudo apt-get install gparted
System > Admin > Partition Editor

...but then it might not work in the vivitar. :lolflag:

Might want to just buy a new card.

---

### Post by saxamo on 2008-05-21
Also: You know how when you insert an SD card, you push it in deep, and then it comes out a little and locks in? Try holding the SD card in all the way and keep the pressure there and see if it shows up on the desktop. This is what I have to do with my SD card to get it to be read correctly.

---

### Post by manchicken on 2008-06-04
Naw, I've tried this with a memory car I know has worked (with its current filesystem) on the daru2 memory card reader, and it's getting this same error message.

Any help would be greatly appreciated.

---

### Post by theologian aaron on 2008-06-05
It appears I have the same problem.  I've tried two cards, both of which work in windows and on other ubuntu machines.  I've tried using gparted, but it does not even list the cards as being available.

This is almost frustrating.  Does anyone have any solutions?

---

### Post by thomasaaron on 2008-06-06
I'm imaging a darter now for testing...
Standby...

---

### Post by thomasaaron on 2008-06-06
Manchicken and Theologian Aaron,

I just imaged and tested a DarU2 with an SD card. It recognized the card both before and after updates.

Could both of you please post the exact output you get in /var/log/syslog when you insert the card?

Are both of you using Kubuntu? (Sorry, I have to ask.)

---

### Post by theologian aaron on 2008-06-06
I'm using a fairly vanilla install of ubuntu.

When I insert the card, I get the same message that Peneus got (-22 error).

Curiously, I just tried two different cards (one of which formatted on my camera, the other on my windows desktop) in my vista dual-boot.  It was not recognized either.  Perhaps there is a hardware issue?  I can't tell when this started as I hadn't used it in awhile anyway, but it did work before I upgraded (via a fresh install).

---

### Post by thomasaaron on 2008-06-06
Please post the error so I can research it. I can't reproduce it in the shop.

---

### Post by walkeraj on 2008-07-05
I am receiving this same error on a perfectly good memory card.

```

Jul  5 13:17:33 vanguard kernel: [14078.663086] mmc1: unrecognised SCR structure version 1
Jul  5 13:17:33 vanguard kernel: [14078.663099] mmc1: error -22 whilst initialising SD card

```

When I insert the card using a usb card reader, it works fine:

```

Jul  5 13:20:07 vanguard kernel: [14133.975431] usb 6-1: new high speed USB device using ehci_hcd and address 7
Jul  5 13:20:07 vanguard kernel: [14134.123780] usb 6-1: configuration #1 chosen from 1 choice
Jul  5 13:20:07 vanguard kernel: [14134.124462] scsi8 : SCSI emulation for USB Mass Storage devices
Jul  5 13:20:07 vanguard kernel: [14134.124653] usb-storage: device found at 7
Jul  5 13:20:07 vanguard kernel: [14134.124655] usb-storage: waiting for device to settle before scanning
Jul  5 13:20:07 vanguard NetworkManager: <debug> [1215278407.686433] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_b013_0000162915'). 
Jul  5 13:20:07 vanguard NetworkManager: <debug> [1215278407.729054] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_b013_0000162915_if0'). 
Jul  5 13:20:12 vanguard kernel: [14136.085456] usb-storage: device scan complete
Jul  5 13:20:12 vanguard kernel: [14136.086394] scsi 8:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0125 PQ: 0 ANSI: 0
Jul  5 13:20:12 vanguard NetworkManager: <debug> [1215278412.738207] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_b013_0000162915_if0_scsi_host'). 
Jul  5 13:20:12 vanguard NetworkManager: <debug> [1215278412.738902] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_b013_0000162915_if0_scsi_host_scsi_device_lun0'). 
Jul  5 13:20:12 vanguard kernel: [14136.269356] sd 8:0:0:0: [sdb] 2012160 512-byte hardware sectors (1030 MB)
Jul  5 13:20:12 vanguard kernel: [14136.270874] sd 8:0:0:0: [sdb] Write Protect is off
Jul  5 13:20:12 vanguard kernel: [14136.270879] sd 8:0:0:0: [sdb] Mode Sense: 02 00 00 00
Jul  5 13:20:12 vanguard kernel: [14136.270882] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Jul  5 13:20:12 vanguard kernel: [14136.273627] sd 8:0:0:0: [sdb] 2012160 512-byte hardware sectors (1030 MB)
Jul  5 13:20:12 vanguard kernel: [14136.275001] sd 8:0:0:0: [sdb] Write Protect is off
Jul  5 13:20:12 vanguard kernel: [14136.275006] sd 8:0:0:0: [sdb] Mode Sense: 02 00 00 00
Jul  5 13:20:12 vanguard kernel: [14136.275009] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Jul  5 13:20:12 vanguard kernel: [14136.275015]  sdb: sdb1
Jul  5 13:20:12 vanguard kernel: [14136.277064] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Jul  5 13:20:12 vanguard kernel: [14136.277127] sd 8:0:0:0: Attached scsi generic sg2 type 0
Jul  5 13:20:12 vanguard NetworkManager: <debug> [1215278412.964069] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_b013_0000162915_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jul  5 13:20:13 vanguard NetworkManager: <debug> [1215278413.411152] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_STORAGE_DEVICE_0000162915_0_0'). 
Jul  5 13:20:13 vanguard NetworkManager: <debug> [1215278413.493900] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_486F_AC62'). 
Jul  5 13:20:13 vanguard hald: mounted /dev/sdb1 on behalf of uid 1000


```

Please advise.

---

### Post by thomasaaron on 2008-07-08
walkeraj,

The good news is your card reader is *seeing* the card, so it's unlikely that you have a hardware problem.

However, it isn't able to initialize the card. I'm having great difficulty figuring out what error 22 is, but it probably has something to do either with a filesystem that Ubuntu doesn't like, or maybe a hosed filesystem on the card. 

Try reformatting it with System > Admin > Partition Editor. If it's not there, you can install it with...

```
sudo apt-get install gparted
```

---

