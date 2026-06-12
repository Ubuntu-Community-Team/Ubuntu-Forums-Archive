---
title: "OVMF, Virtio SCSI Controller, SCSI CD ROM...wont boot .iso?"
date: 2015-07-15
forum: Virtualisation
---

### Post by KillerKelvUK on 2015-07-15
What am I doing wrong here...

Using Gerd's latest OVMF pure builds, doing nothing fancy with the guest config...using the same iso under an IDE CDROM then boot goes fine.  Change the CDROM to us SCSI and change the SCSI Controller to use Virtio SCSI instead of 'default' and I fail to boot the same iso...EFI Shell reports a blk device mapping to FS0 which looks like the CDROM drive...I type FS0: [enter] and then ls [enter] and I get "file not found"?

Google tells me OVMF supports virtio scsi and the .iso is proven intact.  Help?

---

