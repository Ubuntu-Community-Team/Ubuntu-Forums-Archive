---
title: "How to disable or change the console on Ubuntu 20.04?"
date: 2020-09-28
forum: Server Platforms
---

### Post by jrushford2 on 2020-09-28
Greetings,

I don't know how to disable the use of a serial console on Ubuntu 20.04 running on a raspberry pi model 4.
The reason that I wish to disable the console is because I have an Adafruit GPS module wired to the serial UART
on the raspberry pi and the GPS module seems to interrupt the boot process with the module wired to the UART.  If
I connect the the GPS module after the pi boots, I can see that the module is working correctly as I can see GPS data on
/dev/ttyS0.

I have disabled the getty's from running with systemctl but, the kernel boots with this command line (Note: console=ttyS0,115200)

Kernel command line:  coherent_pool=1M 8250.nr_uarts=1 snd_bcm2835.enable_compat_alsa=0 snd_bcm2835.enable_hdmi=1 snd_bcm2835.enable_headphones=1 bcm2708_fb.fbwidth=0 bcm2708_fb.fbheight=0 bcm2708_fb.fbswap=1 smsc95xx.macaddr=DC:A6:32:B8:A0:20 vc_mem.mem_base=0x3ec00000 vc_mem.mem_size=0x40000000  net.ifnames=0 dwc_otg.lpm_enable=0 console=ttyS0,115200 console=tty1 root=LABEL=writable rootfstype=ext4 elevator=deadline rootwait fixrtc quiet splash

It definitely appears that because the kernel is using ttyS0 that the data coming in from the GPS module is causing the boot process to be interrupted.
I'm looking for a way to prevent the boot from being interrupted and I think I need to disable the use of the console to accomplish this.

thanks for your help
John Rushford

---

### Post by jrushford2 on 2020-09-30
I did find boot/firmware/cmdline.txt and fiddled with it.  I changed the settings to use a different tty and I also tried removing "serial0,115200 console=tty1" but nothing helped.  With the GPS module TXD connected to the UART RXD lead, ubuntu fails to boot.  On the monitor I see 'Hit any key to interrupt the boot" followed by a boot prompt.

I was hoping to use Ubuntu but I don't see how to fix this.  Other people are successfully using Raspian with this GPS module so, I think I'll switch.

---

### Post by jrushford2 on 2020-09-30
Yup, I tried Raspian 10 (buster) and it does not have the issue that Ubuntu 20.04 has.  Raspian boots up fine with the GPS module installed and the module has locked on to the GPS satellites.  To bad I couldn't solve the issue on Ubuntu server 20.04.

---

