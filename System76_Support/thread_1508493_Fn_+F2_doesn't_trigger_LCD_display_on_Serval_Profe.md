---
title: "Fn +F2 doesn't trigger LCD display on Serval Professional"
date: 2010-06-13
forum: System76 Support
---

### Post by Dan Hinojosa on 2010-06-13
Hey there, 

I am so stoked about my Serval Professional! I got it yesterday and  everything works fantastically except for one thing - the Fn + F2 key does not trigger the external monitor. I have tried DVI -> VGA and DVI -> DVI. DVI -> VGA doesn't show up on the external monitor. I researched this and found a post that indicated some monitors do not work this this type of adapter. So, I tried a DVI -> DVI, but nvidia-xconfig and nvidia-settings configure the alternate monitor with a very small resolution, not using Fn+F2 but by restarting the computer with the DVI -> DVI plugged in. I have used nvidia-settings before with great success on some older laptops so do have experience setting up monitors in Ubuntu. The Serval Pro hasn't been as easy as with previous laptops. Am I missing something?  Did I screw something up? Let me know.

Some technical info:
I have run the System 76 drivers. I am using version 173 of the NVIDIA driver.

*Operating System : Ubuntu 10.04 (Lucid Lynx) 64 Bit Linux
*Display Resolution : 15.6" Full HD LED Display with Super Glossy Surface (1920 x 1080)
*Graphics : Nvidia GeForce GTX 285M Graphics with 1GB GDDR3 Video Memory
*Processor : Core i7-920XM Processor Extreme Edition ( 45nm, 8MB L3 Cache, 2.0GHz )
*Memory : 8 GB - DDR3 1333 MHz - 2 DIMMs This upgrade option only available with Intel Core i7-720QM or Core i7-820QM CPU
*Hard Drive : 640 GB 5400 RPM SATA II
*Optical Drive : CD-RW / DVD-RW
*Wireless : Intel Centrino Ultimate-N 6300 - 802.11A/B/G/N Wireless LAN Module
*Bluetooth : Bluetooth

---

### Post by isantop on 2010-06-14
I believe that Fn+F2 turns off the LCD Backlight. Fn+F7 should switch between built-in and external monitors.

---

### Post by aranaea on 2011-05-01
I have a serval pro running 11.04 and I can't seem to get Fn+F7 to switch between monitors.  I have to open the nvidia X Server Settings and enable/disable the monitor there.  Is there some setup that I need to do?

---

### Post by isantop on 2011-05-02
Fn+F7 seems to have issues on recent versions of Ubuntu with Nvidia graphics. We're looking into the issue, but I suspect it has to do with the Nvidia driver.

---

