---
title: "Must manually push power button to turn off"
date: 2011-09-01
forum: Server Platforms
---

### Post by devin0 on 2011-09-01
I have recently acquired a IBM Netfinity 5600 Server. It had an old version on windows 2000 on it so I upgraded it to ubuntu server 10.04. The system does not appear to be capable of powering itself off for some odd reason. When i issue the shutdown command it says that the system is halted on screen, but i must manually push the button to turn it off. Is there a way i can fix this or is it an annoyance im just going to have to live with.

---

### Post by disabledaccount on 2011-09-02
Add acpi=force to kernel boot options.

---

### Post by smile-on on 2011-09-17
A note for clarification. I personally have been in same problem with Linux on some old PCs. It turns out that ACPI support in kernel 2.6 requires a BIOS upgrade to bring ACPI from version 1.02 (1.0b) to 1.10 or later. First check if there a specific Linux upgrade for your BIOS on HW manufacture support site, that may fix the issue.

A sad note, it seams windows completely ignored acpi issues as M$ is a one of main founders  of ACPI ([http://www.acpi.info/](http://www.acpi.info/)) and they have private implementation of acpi in kernel that works like a reference implementation. 
ACPI support in Linux kernel comes from a Intel sponsored team ([http://lesswatts.org/projects/acpi/](http://lesswatts.org/projects/acpi/)). Unfortunately ACPI "standard" is not exact. Just check AML/ASL compilers ([http://www.acpi.info/toolkit.htm](http://www.acpi.info/toolkit.htm)) you could see when one get a DSDT (main table) compiled another reports problems.):PSo HW guys definitely have to comply with M$ :wink: and Intel team tries to bring some support in Linux kernel. Well, the key word here is "some". Old story... 

BTW, can some one bring clarity on those magic parameters reboot=bios, acpi=force etc.

---

