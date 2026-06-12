---
title: "53C896 problem"
date: 2008-08-12
forum: Server Platforms
---

### Post by sewalk on 2008-08-12
I have encountered several problems trying to install Ubuntu on this old server but I think I've worked around all but one:  Only drives on the primary channel of the wide scsi controller (onboard 53c896) show up in /dev.  I can see the other drives from the Symbios BIOS and have verified each one, so I know that termination and cabling are at least sufficient for the drives to at least be configured in an OS.  The CD-ROM drive on the narrow controller (on board 53c810) also shows up and works.  I can also see both channels of the 53c896 with lspci but only sda through sdg were created in /dev upon installation.

Do I need to create the dev nodes for these devices by hand?  If so, what is the proper Ubuntu way to do so?  Using the MAKEDEV script in /dev didn't work because of udev.

---

### Post by sewalk on 2008-08-12
Running lsscsi only shows that only the 53c810 (01:03.0)and the first channel of the 53c896 (00:08.0) are active.  How do I get the 53c8xx driver to also activate the 2nd channel (00:08.1) on the 53c896?

Note that this motherboard has dual concurrent PCI busses.

---

