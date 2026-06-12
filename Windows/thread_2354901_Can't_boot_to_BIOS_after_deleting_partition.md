---
title: "Can't boot to BIOS after deleting partition"
date: 2017-03-07
forum: Windows
---

### Post by ramr2 on 2017-03-07
Hi, I was uninstalling Ubuntu to install Windows and was following the steps from this [thread]("http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on"),when I got to the part to repair the computer my cd said it was incompatible, so I went to install Windows, and it asked me to choose what partition I would like to install, and I chose the largest, but it was greyed out, so I tried to delete it , and it prompted a warning, saying that if I chose to erase it, it might erase system files, I chose to ignore it, and now I can't even boot to BIOS. It's not a big deal, but I would like some help please.

Rui

---

### Post by oldfred on 2017-03-07
Moved to Windows sub-forum, since not Ubuntu.

UEFI or BIOS system.
Was Ubuntu then installed in UEFI or BIOS boot mode?
Do you want Windows in UEFI or BIOS boot?

Did you want to totally erase hard drive? If so just boot installer in boot mode you want either BIOS or UEFI.
If drive was gpt, Windows booted in BIOS will complain as it only installs to MBR(msdos). And Windows 7 default install is BIOS only, but can be converted to UEFI install.

---

### Post by ramr2 on 2017-03-07
Hi, the laptop only has BIOS, so I assume that both were installed BIOS. I would like windows to be in BIOS. But the thing is when I turn on the pc and click F2 nothing happens, I notice that the screen lights up a bit, but I can't access the BIOS menu.

---

### Post by oldfred on 2017-03-07
If f2 is correct key, then that is a hardware issue.

Some newer systems require cold boot, or from full power down. And if laptop you may have to remove battery.
And hold power switch with no power in, to drain all power & in effect remove any saved settings.
Then try boot.

What brand/model system?

---

### Post by ramr2 on 2017-03-08
I removed the battery and held the power button down, then switched it on and still the same thing happened.

The laptop is an Asus X55U

---

### Post by oldfred on 2017-03-08
Do not know specific issues, but found this in my notes on UEFI installs.
 Asus x55u UEFI change to BIOS discuses boot keys esp & f2
[http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html](http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html)

---

### Post by ramr2 on 2017-03-08
Thank you, I solved it, I installed the latest distro of Ubuntu to solve it, but now I feel the need to change to Windows. Again thank you very much :)

---

