---
title: "Ubuntu 10.04 server edition booting problem in HP z800 workstation"
date: 2011-01-13
forum: Server Platforms
---

### Post by deep07004 on 2011-01-13
I have just installed  Ubuntu 10.04 Server on my HP z800 workstation with intel Xeon processor.
Installation is fine but monitor goes to sleep mode on boot up.


Does anybody have any idea?????


Thanks in advance.

---

### Post by chrislynch8 on 2011-01-13
Command Line server, no GUI?

When you power it up do you have anything at all on the screen before the monitor goes to sleep?

Rgds
Chris

---

### Post by deep07004 on 2011-01-13
Yea. No gui.

Few seconds of blinking ... nothing else


regards
dipankar

---

### Post by chrislynch8 on 2011-01-13
I've seen this happen with HP alot. 

Power Down completely, check all RAM is set in Motherboard correctly. Remove all RAM, power on Server with one RAM module at a time and see if any are faulty.

---

### Post by deep07004 on 2011-01-13
Checked. Everything seems fine.

Ubuntu server 9.10 is booting properly.
Problem is only with 10.04 and 10.10.


thanking .......
DIpankar

---

### Post by chrislynch8 on 2011-01-13
Ok. This I haven't seen before if the same PC is dual booting 9.10 is booting and 10.04 and 10.10 is not maybe graphics card drivers are incorrect.

Can you boot into the 9.10 install and access the partition with 10.04 or 10.10 and see if there are anything in the log files?

---

### Post by deep07004 on 2011-01-13
No it's not dual boot.
When 10.10 and 10.04 didn't work I just tried 9.10 and that's work.
But I don't want to stick to 9.10 as it's life span is going to end by April 2011. 
It has a Nvidia graphics card ........ it may cause the problem .



Dipankar

---

### Post by chrislynch8 on 2011-01-13
Ok, so have I the following correct.

Fresh Install of 10.04 -> Nothing 
Fresh Install of 10.10 -> Nothing 
Fresh Install of 9.10  -> That works

Is that Graphic card built into the motherboard or is it a seperate PCI card? If seperate do you have one on the Motherboard you can try using.

---

### Post by disabledaccount on 2011-01-13
> **deep07004 said:**
> No gui.
Few seconds of blinking ... nothing elseI suppose there are two possible reasons:
- wrong resoulution/refresh rate setting
- bug in gfx driver
Simplest (temporary) solution is to force gfx mode in kernel boot options (during bootup in grub or by editing grub.cfg from live cd). Possible options are -xforcevesa (vesa mode), vga=<vga_mode_nr>, nomodeset for nv and modeset=0/1 for intel gfx

You should check Xorg.0.log or >lspci -v output to determine what is the type of gfx adapter (revision).

---

### Post by deep07004 on 2011-01-13
Graphics card is built in the motherboard

---

### Post by chrislynch8 on 2011-01-14
Can you do BIOS update? or Even reset the BIOS?

---

