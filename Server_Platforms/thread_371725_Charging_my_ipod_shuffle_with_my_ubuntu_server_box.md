---
title: "Charging my ipod shuffle with my ubuntu server box"
date: 2007-02-27
forum: Server Platforms
---

### Post by fizgig on 2007-02-27
Weird topic to be in the server section I know...

I have an ubuntu server running downstairs and it would be ideal as a charging station for my ipod shuffle (2nd generation).  I plug the charger dock into the server and the shuffle into the charger station and the status light blinks orange.  

Blinking orange means that it is in hard-drive mode and that you shouldn't disconnect it.  I'd rather just have it in charging mode where the status light should stay on constantly where the color of the light would be the charged level.  When it's blinking orange I'm unable to know if it's fully charged yet.

Question is, how do I get it out of this hard drive mode?  Ubuntu doesn't mount it anywhere.  When I plug it into my xp machine, Itunes shows harddrive mode as disabled.  Dmesg does see something though:

> [43508511.840000] usb 3-2: configuration #1 chosen from 2 choices
[43508511.840000] scsi3 : SCSI emulation for USB Mass Storage devices
[43508511.840000] usb-storage: device found at 3
[43508511.840000] usb-storage: waiting for device to settle before scanning
[43508516.840000] usb-storage: device scan complete
[43508516.840000]   Vendor: Apple     Model: iPod              Rev: 2.70
[43508516.840000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[43508516.850000] SCSI device sdc: 495616 2048-byte hdwr sectors (1015 MB)
[43508516.850000] sdc: Write Protect is off
[43508516.850000] sdc: Mode Sense: 64 00 00 08
[43508516.850000] sdc: assuming drive cache: write through
[43508516.850000] SCSI device sdc: 495616 2048-byte hdwr sectors (1015 MB)
[43508516.850000] sdc: Write Protect is off
[43508516.850000] sdc: Mode Sense: 64 00 00 08
[43508516.850000] sdc: assuming drive cache: write through
[43508516.850000]  sdc: unknown partition table
[43508516.870000] sd 3:0:0:0: Attached scsi removable disk sdc
[43508516.870000] sd 3:0:0:0: Attached scsi generic sg2 type 0

---

### Post by fizgig on 2007-02-27
Update:

When I type **sudo eject /dev/sdc**, the charging light goes to the desired state (solid green, no more blinking orange).

So now I need to figure out what eject is turning off and see if I can get my server to not turn "it" on in the first place.

---

