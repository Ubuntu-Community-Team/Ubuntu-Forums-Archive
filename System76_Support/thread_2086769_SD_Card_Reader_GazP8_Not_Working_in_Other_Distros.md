---
title: "SD Card Reader GazP8 Not Working in Other Distros"
date: 2012-11-21
forum: System76 Support
---

### Post by IntoFlow on 2012-11-21
In Ubuntu 12.10 with the latest driver from System76, the SD reader of the Gazelle Pro 8 works perfectly fine.

However when I try to install another distro (dual-boot with Ubuntu), the SD card reader simply does not function. It seems that the only way to have an SD card working properly is with the System76 driver, which I'm not able to install on another distro.

What can I do to be able to have a functioning SD card reader on another distro (Mint 14)? Is it possible to just download a driver on that distro somehow from somewhere?

This is a picture of the SD Reader appearing as normal in Ubuntu. But this is absent in other distros. How can it be that a computer with hardware that is guaranteed to work with Linux has these issues? The hardware of my old Sony worked with all distros I tried.

I do a lot of work with photography and the only way I can transfer files from my camera to the laptop is via the SD card.

Thanks all

---

### Post by IntoFlow on 2012-11-24
Hey all just an update..

Tried different distros and the SD Reader simply doesn't work. As of now I still don't know of any way to make this thing work *without* the System76 Driver in Ubuntu.

Ideas ?

---

### Post by Carborundum on 2012-11-25
The System76 driver is GPLed, so if you have some programming experience you should be able to extract the relevant code from it and build it for any distro.

---

### Post by dogweather on 2013-01-03
> **IntoFlow said:**
> ...How can it be that a computer with hardware that is guaranteed to work with Linux has these issues? 

This is the thing that concerns me about System 76 - their choice to use hardware which doesn't have Linux drivers. And so you're locked in to Ubuntu, and dependent on System 76 staying around and providing updates to match new Ubuntu versions.

I don't understand why they do this. Za Reason chooses compatible hardware; their laptops run most distributions.

---

### Post by lolwtfhax on 2013-02-15
The drivers are open source so it should work fine on other distros.
Try inserting an sdcard and run "sudo fdisk -l" in a terminal and see if it shows up.

---

### Post by isantop on 2013-02-18
> **dogweather said:**
> I don't understand why they do this. Za Reason chooses compatible hardware; their laptops run most distributions.

We do it because the hardware we choose offers better performance and higher quality. We do submit driver changes upstream so that they can be included in other distros as well.

---

### Post by rodney.jacobson on 2013-03-03
I got my SD Card Reader to work in Mint 14.

lspci shows:
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)

grab and build the driver:
wget [https://bugs.launchpad.net/bugs/971876/+attachment/2991730/+files/rts_bpp.tar.bz2](https://bugs.launchpad.net/bugs/971876/+attachment/2991730/+files/rts_bpp.tar.bz2)
tar jxf rts_bpp.tar.bz2
cd rts_bpp
make

Then with root/sudo from the same directory:
make install
depmod -a
modprobe rts_bpp

---

### Post by freechelmi on 2013-03-06
Hi , Do you confirm that you get a kernel crash when using a memory stick from sony on this reader ? I mailed realtek but no answer.

---

