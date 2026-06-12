---
title: "&quot;Add a New Printer&quot; in System Settings / Printers fails"
date: 2012-03-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by w-sky on 2012-03-30
Hello,

the "Add a New Printer" dialog in System Settings fails when I try to add a network printer.

I do select "Network", then enter the IP address of the printer, mark "search by address" and a few seconds later the printer is found:

"Lexmark-International--Inc-85-33mr2-44H0021"

Though the printer is selected, and when I click "Add" nothing happens.

---

### Post by dino99 on 2012-03-30
Do you get errors logged in xsession-errors or /var/log/dmesg about this issue?

---

### Post by w-sky on 2012-03-30
> **dino99 said:**
> Do you get errors logged in xsession-errors or /var/log/dmesg about this issue?

I do not see anything in Xorg.0.log in the log viewer, but I found this in dmesg, these are the only lines that have anything to do with printing, though I don't know when this happened and what it means:

> [  127.813140] type=1400 audit(1332951764.927:31): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1644 comm="apparmor_parser"

[  127.814966] type=1400 audit(1332951764.927:33): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1644 comm="apparmor_parser"

---

