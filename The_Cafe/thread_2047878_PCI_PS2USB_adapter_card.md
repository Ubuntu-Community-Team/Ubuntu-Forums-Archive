---
title: "PCI PS2/USB adapter card"
date: 2012-08-25
forum: The Cafe
---

### Post by kurt18947 on 2012-08-25
I'm going to post this as a heads-up for those who might be seeking to add a PS2 port(s) or replace a PS2 port on a MoBo that is malfunctioning.  I need to use a PS2 mouse on a boot manager that I use,  on one machine the boot manager does not recognize a USB mouse.  On another machine a USB mouse is recognized by the boot manager so it's probably a MoBo chipset issue.  Anyway I wanted to plug 2 PS2 devices in and use them in this boot manager.  I found a Syba branded PCI card that has 2 PS2 ports and 2 USB ports.  It uses  a NEC chipset so figured I'd give it a go.

It works with Linux and Windows but not like I had hoped.  The PS2 port on the MoBo is recognized and functions without any sort of device driver loaded.  That is what I wanted.  This PCI add-on card requires a device driver/O.S. loaded so it is not exactly what I wanted.  I'm able to make it work because the boot manager recognizes a USB keyboard but not a USB mouse.  I can plug a USB keyboard in when editing boot manager settings.  <lspci> in a terminal shows only two additional USB entries, nothing about any other (PS2) device.  I suspect there's a PS2/USB 'translator' and the PS2 ports are seen as USB devices hence the need for a driver.  Anyway I hope this adds to the forum's "general fund of knowledge".  I do have 'regard USB as legacy devices' - or however it's phrased - in the BIOS but that's no help.

---

