---
title: "Printer on wireless netowrk"
date: 2007-06-01
forum: System76 Support
---

### Post by MarkID on 2007-06-01
This question may seem basic, but how do I set up my printer on my wifi so I can print from my Darter (or other printer, for that matter) wirelessly?

---

### Post by thomasaaron on 2007-06-01
What kind of printer are you using?
What kind of print server are you using?

---

### Post by MarkID on 2007-06-01
> **thomasaaron said:**
> What kind of printer are you using?
What kind of print server are you using? is currently not 

The printer in question is currently an HP 6840, which had always been connected directly to the computer, and configured in CUPS.  It is currently not connected to any computer (problem with other computer).  Is there a way to connect the printer to my wifi router (via an ethernet  cable, for example), and printer wirelessly from my Darter?  Thanks.

---

### Post by IgnacioMiller on 2007-06-01
Can you connect to your network normally? If you can, then configuring the printer via CUPS should be easy! See this episode of Linux Reality: [http://media.libsyn.com/media/linuxreality/linuxreality029.ogg](http://media.libsyn.com/media/linuxreality/linuxreality029.ogg)

---

### Post by thomasaaron on 2007-06-01
OK, here's the scoop...

I looked up the specs on your printer. It has an integrated print server and a networking (CAT5) port.

Just hook the printer to your wireless router with a CAT5 wire.

Then configure your printer via the utility located at:
System > Administration > Printers

You will print to your printers IP address.

Here is a tutorial on setting up the printer:
[http://www.freesoftwaremagazine.com/articles/printing_ubuntu](http://www.freesoftwaremagazine.com/articles/printing_ubuntu)

The main difference is you will use the 'Network Printer' option and the 'CUPS' setting.

Let me know if you have more questions

---

### Post by MarkID on 2007-06-01
> **thomasaaron said:**
> OK, here's the scoop...

I looked up the specs on your printer. It has an integrated print server and a networking (CAT5) port.

Just hook the printer to your wireless router with a CAT5 wire.

Then configure your printer via the utility located at:
System > Administration > Printers

You will print to your printers IP address.

Here is a tutorial on setting up the printer:
[http://www.freesoftwaremagazine.com/articles/printing_ubuntu](http://www.freesoftwaremagazine.com/articles/printing_ubuntu)

The main difference is you will use the 'Network Printer' option and the 'CUPS' setting.

Let me know if you have more questions

Thank you!  That was just way too easy!

---

