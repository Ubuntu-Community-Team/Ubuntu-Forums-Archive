---
title: "Ubuntu Core 22 64 bit - Raspberry Pi 4 - SSD boot loop (full Ubuntu boots fine)"
date: 2023-05-06
forum: Server Platforms
---

### Post by rvf148 on 2023-05-06
Hi,

I'm using Raspberry Pi imager to write the provided images to SDCard/HD/SSD
Raspberry Pi 4 eeprom is upgraded to the latest version, and no sdcard is present during the issue. 

Booting Ubnt Core 22 from SDCARD and USB HD are no issue, but when I use an USB SSD drive, a boot loop occurs.
**Booting the _full_ Ubuntu 22 image from the same USB SSD drives works fine.**

How can I troubleshoot the Core boot ?
The only thing that is displayed is the color chart at boot, and a blinking cursor, after a while it just reboots, and starts this sequence all over.
I never get to the Core initial setup, also I don't see the splash screen (could be fast)

Already tried using the raspberry pi provided image, and the custom image downloaded from ubuntu download site.

Please advice on how to get the Core version to boot from my USB SSD, any help will be appreciated

Thanks,
Raf

---

### Post by LHammonds on 2023-05-08
Did you follow these instructions?

[https://ubuntu.com/download/raspberry-pi-core](https://ubuntu.com/download/raspberry-pi-core)

LHammonds

---

### Post by MAFoElffen on 2023-05-09
Those instructions are for the MicroSD card, which the OP says works, but he cannot boot from USB attached SSD...

I looked into that yesterday. Seems that 'no one" has successfully booted a Raspberry Pi on Ubuntu Core, from an SSD. I found 4 support threads, that are still unresolved on this issue. ...At least for Ubuntu Core.

I what think that it might be possible. I mean I boot Ubuntu Server from SSD on my Rasp Pi4. I did it manually. I would think that it might be possible to do it the same way. I have to set it up on MicroSD first, update the firmware to support booting from a USB storage drive, then manually transfer the OS to the SSD. But I, myself, have not done this with Ubuntu "Core".

---

