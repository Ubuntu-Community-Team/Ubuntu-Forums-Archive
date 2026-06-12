---
title: "XP - Hard Drives Not Spinning Down Properly"
date: 2008-01-31
forum: Windows
---

### Post by Vince4Amy on 2008-01-31
The hard drives on this machine do not appear to be spinning down correctly. When the machine is being shut down a loud click can be heard from the Hard Drives when the power has been cut. On my other Windows machines the hard drives can clearly be heard spinning down properly. I have listened to the machine very carefully on shut down and I can confirm that the drives are indeed just switching off with the power and performing an emergency park rather than spinning the drive down properly. This can shorten the life of the Hard Drives. The configuration is as follows:2x SATA Drives, 160GB, Maxtor & Western Digital (They both make the click when shutting down)VIA k8m800 NorthbridgeVIA vt8237r plus SouthbridgeI am using the Drivers which were supplied with the motherboard (I believe Hyperion Version 5.00), I would update to the latest version, but last time I did such a thing it rendered the graphics card almost useless. Is there any way I can delay the shut down time and allow XP to spin down my drives properly?

---

### Post by frankos44 on 2008-03-05
> **Vince4Amy said:**
> The hard drives on this machine do not appear to be spinning down correctly. When the machine is being shut down a loud click can be heard from the Hard Drives when the power has been cut. On my other Windows machines the hard drives can clearly be heard spinning down properly. I have listened to the machine very carefully on shut down and I can confirm that the drives are indeed just switching off with the power and performing an emergency park rather than spinning the drive down properly. This can shorten the life of the Hard Drives. The configuration is as follows:2x SATA Drives, 160GB, Maxtor & Western Digital (They both make the click when shutting down)VIA k8m800 NorthbridgeVIA vt8237r plus SouthbridgeI am using the Drivers which were supplied with the motherboard (I believe Hyperion Version 5.00), I would update to the latest version, but last time I did such a thing it rendered the graphics card almost useless. Is there any way I can delay the shut down time and allow XP to spin down my drives properly?

It sounds like a power driver problem or compatibility, Ive seen this happen on windows too. Take a look in your BIOS and play around with power and standby settings ACPI.

---

