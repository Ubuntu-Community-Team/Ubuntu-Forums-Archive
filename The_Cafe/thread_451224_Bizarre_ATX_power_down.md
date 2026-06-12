---
title: "Bizarre ATX power down"
date: 2007-05-22
forum: The Cafe
---

### Post by voided3 on 2007-05-22
Hello, I have two computers that have trouble shutting down. One is an HP Pavilion desktop with a 2.5ghz P4; when going through a standard shutdown procedure, it restarts the computer once the OS has finished shutting down, leaving the only way to shut it off is to hold the power button down once it starts to restart. The other is on a custom built computer with an AMD Athlon t-bird @ 1.43ghz on an IWILL KK266R mobo; it also doesn't shutdown completely exactly as the HP did, but starts to restart, then after 1 second, re-restarts and does this a few times, leaving me to once again have to shut it down by holding the power button. Both systems restart normally and function as they should otherwise and I believe wake-on-LAN is disabled on both in BIOS. Any ideas as what would cause this or a possible remedy? Thanks!

---

### Post by dmizer on 2007-05-22
i'm actually having a problem with the shutdown routine on my server but it's a different problem.  not too sure how to tell you what you need to do to REALLY fix this problem, but when the machine reboots, hit <esc> to get into the grub menu.  select the letter 'c' to get to the command line.  you should see something like this:
```
grub>
```
just type:
halt

hit <enter> and the machine should turn off.

again, this isn't a fix, but it should prevent you from having to hold the power button in order to shutdown the machine.

edit:
just happened to think ... does the machine actually turn off (rather than reboot) if you enter this command in the terminal?
```
sudo halt
```

---

### Post by voided3 on 2007-05-22
Well the thing is it isn't a software based issue; both systems' operating systems shutdown normally, but the hardware does not power off afterwards. I have both Windows and Xubuntu on the Athlon computer and both OSes do the same thing, as do any live CDs.

---

