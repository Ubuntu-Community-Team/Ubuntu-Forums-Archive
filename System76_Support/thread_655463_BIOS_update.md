---
title: "BIOS update"
date: 2008-01-01
forum: System76 Support
---

### Post by steveneddy on 2008-01-01
Is there a BIOS update for my Serval Performance Type 1 laptop?

I was wanting to upgrade to 4 Gig of RAM and I understand that i can't do that without a BIOS update.

---

### Post by thomasaaron on 2008-01-02
You didn't say what BIOS version you currently have, so I'm not sure if there are updates from that version.

However, there have been some updates for the EL80 BIOS over time. I looked through the change reports for the bios updates and didn't see anything indicating they would support 4GB of RAM, though.

Where did you see that the EL80 can support 4GB with a BIOS update? (That would assist me in investigating further.)

---

### Post by mawalters1 on 2008-01-05
I had a similar question on upgrading BIOS, to try to see if they provide booting from USB.
Current BIOS details: 
[INDENT]SMBIOS 2.4 present.
24 structures occupying 1067 bytes.
Table at 0x000DC010.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
        Vendor: COMPAL
        Version: 1.12
        Release Date: 08/29/2007
        BIOS Revision: 49.49
        Firmware Revision: 49.49[/INDENT]
System76 info: Serval serp3
Ubuntu 7.10, 
If there is a link or other resource to search or review for bios or Firmware updates I haven't figure it out yet.
Thanks,

---

### Post by thomasaaron on 2008-01-07
mawalters1,

Yes, it will boot from USB. Most all modern computers will.

Just a note:
We don't recommend updating your BIOS unless you have a specific need that the BIOS update meets. It seems to me that BIOS updates almost NEVER do anything for Ubuntu. They seem to generally offer functionality specific to MS Windows.

Just another note:
If you update your BIOS and toast your computer, and it is not an update that System 76 recommended, we probably will not cover it under warranty. It is an inherently risky procedure.

---

