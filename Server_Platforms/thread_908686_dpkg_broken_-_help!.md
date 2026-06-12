---
title: "dpkg broken - help!"
date: 2008-09-02
forum: Server Platforms
---

### Post by Thought1 on 2008-09-02
I have 6.06LTS server install (no GUI) that's been running fine for me for a couple of years now.  However, I just recently went to do the standard update routine (sudo apt-get update / sudo apt-get dist-upgrade) and it downloaded the packages, but then it said:

```
 Preconfiguring packages ...
 (Reading database ... E: Sub-process /usr/bin/dpkg received a segmentation fault.
```

I've tried rebooting, running ```
sudo dpkg --configure -a
```, running ```
sudo apt-get clean
```, and everything else I can think of or find on the web, but dpkg is still giving a seg fault.  I'm a bit loathe to do a complete reinstall, as this is my main DHCP/email/web server, so any in situ help would be greatly appreciated.

Thanks!

---

### Post by oilchangeguy on 2008-09-02
type, sudo dpkg --configure -a then press enter.

---

### Post by Thought1 on 2008-09-03
Already did that, and I still have the problem.  Sorry I wasn't more clear, but I sudo everything so sometimes I forget to mention it.

Any other ideas?

---

### Post by Sef on 2008-09-03
moved to server platforms.

---

### Post by Thought1 on 2008-09-03
Thanks!   I'm not sure that the problem is specific to the server versions, though.

---

### Post by windependence on 2008-09-04
Have you tried fsck'ing your drives? You may have some corrupted files. Also, bad memory will do this as well as other bad hardware. Judging from the length of time you have had the machine, this is entirely possible. Also, look for a bad CPU fan or blocked ventilation in the case. Heat is another thing that may cause hardware to fail and initiate seg faults.

-Tim

---

### Post by Thought1 on 2008-09-04
Yes, I've fsck'd my drives.  I actually have it set up to run on all mount points on boot (I like having my servers as self-maintaining as possible), so it's been done several times since I started receiving the error a few days ago.  Bad memory/hardware and heat issues wouldn't be consistently reproduceable, nor would they be confined to a single program.  Additionally, the room is kept at 63 degrees F, the server in question has 2 case fans and 2 power supply fans, and on reboot the BIOS heat monitor shows both the CPU and motherboard chips at well below their heat thresholds.

Any other ideas?

---

### Post by konsole on 2008-09-05
Run dpkg through strace or valgrind and try to determine what's occuring just prior to the segfault.

---

### Post by Thought1 on 2008-09-05
Wow, that's interesting!!!  It was crashing reading in big blocks of nulls from one of the package files.  I went to the package directory and looked at the file...and it was listed as being 128petabytes in size.  Uh-huh.  Looks like there's a few other files in this directory that have the same issue.  So my question is: why wouldn't fsck see this and fix it?

In any case, deleting those files and re-runing sudo apt-get update a couple of times resolved the issue.

Thanks!

---

