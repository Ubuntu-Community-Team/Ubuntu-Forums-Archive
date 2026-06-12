---
title: "&quot;Airplane mode&quot; button on gazp9"
date: 2014-08-11
forum: System76 Support
---

### Post by sappj on 2014-08-11
I've compiled my own kernel for a Gazelle Professional (gazp9), but the  "Airplane mode" (Fn-F11) button doesn't work with it.  It works with the  stock kernel.  I have multiple RFKILL modules compiled, but none of  them seem to work.  Any suggestions on the kernel options I need to make  it work?

---

### Post by gjhein on 2014-08-13
It does nothing on the 17" Sys76-Kudo running X-Ubuntu.  I do not have this key on Gazelle purchased in 2012.

---

### Post by sappj on 2014-08-13
The one I have was purchased in the last few months.

---

### Post by tbh2 on 2014-09-03
I have a gazpro9 purchased in late 2013. It has an airplane mode icon on F11. That key used to work but no longer works. Other (blue) function keys still work. I am using Ubuntu as shipped + online updates! nothing special. Also, wireless does not work. Still under warranty but I can't figure out how to get help, so far.

---

### Post by sappj on 2014-09-03
Sounds like the same issue I'm having with the "airplane mode" key, but the wireless issue is for a different thread (try `[FONT=courier new]rfkill list[/FONT]`).  My wireless works just fine.

---

### Post by sappj on 2014-09-06
From what I've determined so far, it needs the following symbols in the kernel: ACPI_EC_DEBUGFS DMIID RFKILL
Then, the code can be obtained [https://code.launchpad.net/~system76-dev/system76-driver/trunk](https://code.launchpad.net/~system76-dev/system76-driver/trunk), then make sure the `system76-daemon` python script is running.  It now works for me on my new kernel.
It looks like the script identifies the model using the DMI sysfs entry, monitors the ACPI EC sysfs interface, and uses RFKILL to kill wifi and bluetooth.

---

