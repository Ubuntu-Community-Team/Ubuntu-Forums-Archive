---
title: "No screen brightness gui or otherwise"
date: 2013-11-28
forum: Ubuntu Studio
---

### Post by Halpm on 2013-11-28
Hi, I'm new to ubuntu studio - fresh install of 13.10 the day before yesterday. I'm just realised I can't seem to find anyway of adjusting the brightness of my laptop screen. Nothing in the various menus, hotkeys don't work, terminal commands don't help. This all worked fine in 13.04 vanilla ubuntu before I changed over. So is this a 13.10 thing, a design feature of ubuntu studio, or just me that can't find my way around xfce?
Certainly seems there is some package or other that I'm missing...

---

### Post by Toz on 2013-11-28
If would be helpful if you could provide more information about your laptop, especially the make and model.

Also helpful would be information about your video card and backlight interfaces. To do this, open a terminal window, copy/paste in the following commands, and post back the results:
```
lspci -k | grep -iA2 VGA
```
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```
```
cat /proc/cmdline
```

---

### Post by Halpm on 2013-11-28
1:
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
	Subsystem: CLEVO/KAPOK Computer Device 1500
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
--
01:00.0 VGA compatible controller: NVIDIA Corporation GF106M [GeForce GT 555M] (rev ff)
03:00.0 USB controller: Texas Instruments TUSB73x0 SuperSpeed USB 3.0 xHCI Host Controller (rev 02)
	Subsystem: CLEVO/KAPOK Computer Device 1500

2:
s; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory

3:
BOOT_IMAGE=/vmlinuz-3.11.0-13-lowlatency root=/dev/mapper/ubuntu--studio--vg-root ro acpi_backlight=vendor quiet splash nomodeset video=uvesafb:mode_option=1920x1080-24,mtrr=3,scroll=ywrap vt.handoff=7


As for the make and model, it's made by a local company called MM-vision, and it's model number is W150HR

---

### Post by Halpm on 2013-11-29
Do you think I'd have more luck with this posting in the xubuntu forums?

---

### Post by Toz on 2013-11-29
> **Halpm said:**
> 1:
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
	Subsystem: CLEVO/KAPOK Computer Device 1500
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
--
01:00.0 VGA compatible controller: NVIDIA Corporation GF106M [GeForce GT 555M] (rev ff)
03:00.0 USB controller: Texas Instruments TUSB73x0 SuperSpeed USB 3.0 xHCI Host Controller (rev 02)
	Subsystem: CLEVO/KAPOK Computer Device 1500
Can you try again with this command instead?
```
lspci -k | grep -iA2 VGA
```

> 2:
s; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory
It look like you missed a part of the command, can you try again:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

---

### Post by Toz on 2013-11-29
> **Halpm said:**
> Do you think I'd have more luck with this posting in the xubuntu forums?
This is the forums for Xubuntu as well, so no need to repost. However, I don't think this an issue related to Xubuntu - its related to the interaction between the kernel and the video driver for your specific brand of laptop.

Lets see if the results of those commands can shed some light.

---

### Post by Halpm on 2013-11-30
Ok!
hal@hal-W150HRM:~$ lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
	Subsystem: CLEVO/KAPOK Computer Device 1500
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
--
01:00.0 VGA compatible controller: NVIDIA Corporation GF106M [GeForce GT 555M] (rev ff)
03:00.0 USB controller: Texas Instruments TUSB73x0 SuperSpeed USB 3.0 xHCI Host Controller (rev 02)
	Subsystem: CLEVO/KAPOK Computer Device 1500

2:
hal@hal-W150HRM:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory

---

### Post by Toz on 2013-11-30
Interesting, you have no backlight interfaces, which explains why things aren't working. You seem to have 2 video cards, an intel and an nvidia, but neither are using the proper drivers. Your kernel boot line is:
> BOOT_IMAGE=/vmlinuz-3.11.0-13-lowlatency root=/dev/mapper/ubuntu--studio--vg-root ro acpi_backlight=vendor quiet splash nomodeset video=uvesafb:mode_option=1920x1080-24,mtrr=3,scroll=ywrap vt.handoff=7
Can you shed some light as to why you set it up as such? 

What happens if you boot _without_ the **acpi_backlight=vendor** parameter, do you get a directory under /sys/class/backlight? And if so, does brightness work?

What happens if you boot _without_ the **acpi_backlight=vendor nomodeset video=uvesafb:mode_option=1920x1080-24,mtrr=3,scroll=ywrap** parameters?

---

### Post by Halpm on 2013-11-30
Aha! The **acpi_backlight_vendor** parameter was leftover from some experimenting, but I had forgotten to update-initramfs after removing it. The other parameters were from this how-to on how to stop Plymouth from crashing: [http://byobu.info/article/Changing_Plymouth_Resolution_in_Ubuntu/](http://byobu.info/article/Changing_Plymouth_Resolution_in_Ubuntu/)  But it seems to work without the extra parameters, and removing them fixes the brightness problem :) Thank you!

---

