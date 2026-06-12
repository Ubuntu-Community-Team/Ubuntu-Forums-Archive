---
title: "Server doesn't boot properly"
date: 2015-05-08
forum: Server Platforms
---

### Post by tajscat on 2015-05-08
Hey guys,
recently I've installed a ubuntu server on my old x86 pc.
Now every time I reboot the server it gets stuck on this page while booting:
[http://www.directupload.net/file/d/3981/wdhmfeo9_jpg.htm](http://www.directupload.net/file/d/3981/wdhmfeo9_jpg.htm)
The only way for me to bypass this error is to restart the pc while it's stuck.
I already tried re installing the server software and plugging off the usb devices from the motherboard.
I can't figure out how to solve this problem. :(

Maybe one of you can help me?

---

### Post by tgalati4 on 2015-05-08
Welcome to the forums.  How old is the computer?  Perhaps the power supply is weak.  Check the voltages with a meter.

---

### Post by tajscat on 2015-05-08
My pc is quite old. I think its from 2006. The power supply is working properly.

---

### Post by tgalati4 on 2015-05-08
A double boot could be a weak capacitor on the motherboard or in the power supply.  Look for leaking or bulging capacitors on the motherboard.

One way to isolate a weak power supply is to remove all accessories and excess RAM and the video card (use on-board video) and try to boot with a minimum configuration.  If it boots in a stable fashion, then start adding stuff back in.  Otherwise, if the motherboard is failing, try declocking the CPU in BIOS.

If you think it is a software problem, post any errors in /var/log/syslog.  You don't need to post the entire log, just errors.

---

### Post by tajscat on 2015-05-09
Even in minimal configuration it wont boot properly. (mainboard, harddrive and RAM modules)
I couldn't find any defect capacitors either. 
Maybe the problem is linked to the fact that when i reboot the pc manually while running i get to the boot menu?

There is only one error that i found in my syslog.
```

May  9 15:03:57 Server-T kernel: [    1.328045] usb 2-6: device descriptor read/64, error -62

May  8 22:45:15 Server-T kernel: [    3.380022] usb 2-6: device not accepting address 4, error -62
May  8 22:45:15 Server-T kernel: [    3.964041] usb 2-6: device not accepting address 5, error -62


```

btw thanks for your help!

---

### Post by cariboo on 2015-05-09
What usb devices have you got plugged in, and does unplugging them allow the system to boot properly?

---

### Post by tajscat on 2015-05-10
There are no usb devices connected to the pc. Neither to the mainboard nor to the ports on the outside.
Maybe the pc setup will help..

Amd Athlon 64 3800+ (2,4GHz)
Hitachi 250gb hard drive
2x 1gb RAM modules
ASRock AM2NF6G-VISTA mainboard
Jersey CP4-420WS ATX 420W power supply

---

