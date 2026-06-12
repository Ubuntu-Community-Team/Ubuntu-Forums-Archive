---
title: "External Firewire Drive will Not Mount"
date: 2008-11-13
forum: Server Platforms
---

### Post by paiwacket on 2008-11-13
Ubuntu Server  8.04 for intel
External Segate 250GB HD

I am a newbie w/ Ubuntu, but am learning fast.

An ext HD will not mount. HD has mounted fine on a Leopard Server. Does not show up in hardware config, even after restarting system. What else can I try?

Thanx,  -Barry

---

### Post by Philio on 2008-11-13
You shouldn't need to reboot, try unplugging/ plugging in again and see if anything is shown by the dmesg command.

---

### Post by paiwacket on 2008-11-13
No diff when viewing 'Hardware > Partitions on Local Disks'

---

### Post by Philio on 2008-11-13
If you type dmesg into the console you will see if it was recognised by the system.

This is a crap example but gives you an idea, was taken from a Xen box which I plugged and unplugged a BT dongle:

> PM: Adding info for usb:5-1
PM: Adding info for No Bus:usbdev5.2_ep00
usb 5-1: configuration #1 chosen from 1 choice
PM: Adding info for usb:5-1:1.0
hub 5-1:1.0: USB hub found
hub 5-1:1.0: 3 ports detected
PM: Adding info for No Bus:usbdev5.2_ep81
PM: Adding info for usb:5-1.2
PM: Adding info for No Bus:usbdev5.3_ep00
usb 5-1.2: configuration #1 chosen from 1 choice
PM: Adding info for usb:5-1.2:1.0
PM: Adding info for No Bus:usbdev5.3_ep81
PM: Adding info for usb:5-1.3
PM: Adding info for No Bus:usbdev5.4_ep00
usb 5-1.3: configuration #1 chosen from 1 choice
PM: Adding info for usb:5-1.3:1.0
PM: Adding info for No Bus:usbdev5.4_ep81
usbcore: registered new driver hiddev
input: Logitech Logitech BT Mini-Receiver as /class/input/input1
input: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.1-1.2
input: Logitech Logitech BT Mini-Receiver as /class/input/input2
input,hiddev96: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.1-1.3
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.6:USB HID core driver
usb 5-1: USB disconnect, address 2
usb 5-1.2: USB disconnect, address 3
PM: Removing info for No Bus:usbdev5.3_ep81
PM: Removing info for usb:5-1.2:1.0
PM: Removing info for No Bus:usbdev5.3_ep00
PM: Removing info for usb:5-1.2
usb 5-1.3: USB disconnect, address 4
PM: Removing info for No Bus:usbdev5.4_ep81
PM: Removing info for usb:5-1.3:1.0
PM: Removing info for No Bus:usbdev5.4_ep00
PM: Removing info for usb:5-1.3
PM: Removing info for No Bus:usbdev5.2_ep81
PM: Removing info for usb:5-1:1.0
PM: Removing info for No Bus:usbdev5.2_ep00
PM: Removing info for usb:5-1

But you can see that the device was registered recognised then removed, should get something similar.

---

### Post by paiwacket on 2008-11-14
I plugged the drive into a USB port (the enclosure is usb/firewire) & voila! it showed up.

Thx for the help.

---

### Post by Nausser on 2008-11-24
I have a similar issue; however I can only access my external HDD via USB. I need to use IEEE1394 to free up some USB ports. I have a 3 port pci Belkin firewire card with a TI chip.
Also, I will be needing to plug in my camcorder for DV capture as soon as I can find my 4 to 6 pin firewire adapter cable.
I am running Ubuntu Studio 8.10

The card shows up under lspci

Here is my dmesg output for plugging and unplugging the drive...

[ 5945.608141] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[ 5962.280088] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[ 5963.232261] ieee1394: Error parsing configrom for node 0-00:1023
[ 5963.232737] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[ 5971.189105] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[0090a9500000d90d]
[ 5971.189538] scsi7 : SBP-2 IEEE-1394
[ 5971.190572] ieee1394: sbp2: Workarounds for node 0-00:1023: 0x2 (firmware_revision 0x000221, vendor_id 0x0090a9, model_id 0x000000)


I hope this makes sense to someone.

---

### Post by SteveF48 on 2009-10-19
My laptop only has USB 1 ports, so Firewire should be quicker. The FireWire drive worked once, but is usually not recognised. I've tried plugging in after jaunty starts and before jaunty starts, to no avail, it's invisible.

dmesg gives:
[  338.284946] ohci1394: fw-host0: SelfID received, but NodeID invalid (probably new bus reset occurred): 0000FFC0
[  338.285089] ohci1394: fw-host0: SelfID received, but NodeID invalid (probably new bus reset occurred): 0000FFC0
[  751.116458] ohci1394: fw-host0: SelfID received, but NodeID invalid (probably new bus reset occurred): 0000FFC0
[  751.116623] ohci1394: fw-host0: SelfID received, but NodeID invalid (probably new bus reset occurred): 0000FFC0
[ 2049.522230] gtk-gnash[6198]: segfault at bf327fec ip 0809095d sp bf327ff0 error 6 in gtk-gnash[8048000+97000]

These commands worked the one time I saw the device:
sudo chmod 777 /dev/raw1394
sudo mount -a
But no longer has any effect.
Doesn't anyone know how to solve this problem?

---

