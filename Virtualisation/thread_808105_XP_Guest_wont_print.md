---
title: "XP Guest wont print"
date: 2008-05-26
forum: Virtualisation
---

### Post by BobLand on 2008-05-26
Host is Gutsy.  Have USB recognized by vbox and xp.  Printer is Epson Photo Stylus 2200.  The usb filter is set by vbox to this specific printer.  XP sees the printer.  When I try to print a doc, xp throws this error
```
Check all connections and make sure all devices are on. 
If the power was turned off during printing, cancel the print job. 
If the error does not clear, see your printer documentation.
```

The printer prints normally in Gutsy so all communication lines are intact.

Any ideas?

bobland

---

### Post by fjgaude on 2008-05-26
Did you load the driver while in XP for the printer?

---

### Post by BobLand on 2008-05-26
Yes.  In fact, everytime I go into XP I see 2 instances of the printer.  If I delete the copy, it comes back regardless of what state I save.

bobland

---

### Post by fjgaude on 2008-05-26
Maybe it would solve the problem if you delete the printer and started over, re-loaded the driver. Then see if it worked correctly.

---

### Post by BobLand on 2008-05-26
Did all of that multiple times.  Logging out, rebooting, reloading drivers.  Same result.

Funny thing is, XP loads the driver correctly, lets me configure it all over the place except running an ink check.  Then I get the same error as trying to print.  In other words, XP thinks everything is OK but when it comes time to talk to the printer, no one is home.

bobland

---

### Post by fjgaude on 2008-05-26
If it doesn't let you run an ink check it likely doesn't see the printer. Can you see the USB Device in the LM menu?

---

