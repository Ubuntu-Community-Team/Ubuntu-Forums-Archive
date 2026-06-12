---
title: "Printing Problems"
date: 2007-06-14
forum: The Cafe
---

### Post by tardis on 2007-06-14
After printing a doc once and then trying to print another the second will not print, what could be the problem?  Using Ubuntu 7.04 Feisty Fawn with an epson 600q.  I don't remember have this problem with Ubuntu 6.10, can anyone help?

---

### Post by trinaryouroboros on 2007-06-20
This could be a variety of things. 

I have a more recent Epson Photo printer that I also had a similar problem with, but, it just required a reboot of the client, host, and printer itself to get things back together. Sometimes that stuff happens.

For one: Is this printer hooked up via parallel cable Straight to your Ubuntu desktop, or is it going through another computer on the network?

If it's going through another computer on the network, what operating system is that one using?

If it's not going through another computer on the network, is it going through something else, like a network print server?

In the meantime, if this printer Is hooked up straight to your Ubuntu desktop, you can try to unplug the power off the back of the printer for 30-seconds (count it out!) then reboot Ubuntu and see if that helps.

If you continue to get the same problem, you could also take things a step further by hooking it up to another PC and seeing if that prints or has similar issues (if it Does have issues even on another PC, then you definitely know it's the Epson printer that you need to troubleshoot foremost, be prepared for anything!)

To give other ideas, there could be something as simple as a bad port setting in Ubuntu for the parallel port, or something similar to the way the spooler is set up...

---

### Post by trinaryouroboros on 2007-06-20
My apologies, you said this problem occurred after upgrading to 7.04 from 6.10?

---

### Post by trinaryouroboros on 2007-06-20
You may want to refer to this thread for more information:

[http://ubuntuforums.org/showthread.php?p=2521992](http://ubuntuforums.org/showthread.php?p=2521992)

---

### Post by DoctorMO on 2007-06-20
i've seen a number of epson usb devices refuse to respond after a number of commands. something in the epson driver is keeping the printers/scanners alive but we don't know what.

---

