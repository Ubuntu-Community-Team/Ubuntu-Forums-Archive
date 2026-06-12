---
title: "[cups] How to Add a Printer to a Server Machine (no GUI)"
date: 2008-06-14
forum: Server Platforms
---

### Post by GenuineXP on 2008-06-14
I've been struggling for quite some time to simply add a printer connected to my server to CUPS, but nothing seems to work.

I've opened up just about every hole and using the web interface fails for some reason. Everything works fine until I choose the driver and click the "Add Printer" button. The page just continues to load indefinitely (and, of course, the printer is never added).

I'm perplexed as to how a printer is added from the terminal. You would think it was simpler (i.e., some kind of cups-add-printer command)! In fact, I was able to install xinetd and write a custom service to share the printer's *scanner* in about ten minutes. I've been without a printer for three weeks!

Any ideas? Thanks.

---

### Post by GenuineXP on 2008-06-15
Bump.

---

### Post by GenuineXP on 2008-06-16
Bump.

---

### Post by iskatyel on 2008-06-17
Personally, I have used the http on port 631 and had no trouble, but if you need to use the command-line, try these from a quick google for cups cli printer add:
[http://www.togaware.com/linux/survivor/CUPS_Command.html](http://www.togaware.com/linux/survivor/CUPS_Command.html)
[http://www.cups.org/documentation.php/man-lpadmin.html](http://www.cups.org/documentation.php/man-lpadmin.html)

In Ubuntu I believe the cli commands will be absent unless you install the cupsys-bsd package.

---

### Post by mlapaglia on 2008-06-17
I just finished setting up CUPS on a 8.04 Server. Install all the required cups programs, plug in all the printers, edit the configuration file to allow remote access (it doesn't by default), get to a computer on the network that *does* have a GUI, and go to [http://ipaddressofserver:631](http://ipaddressofserver:631) from there the configuration of the printers is extremely easy, it took me only a few minutes.

---

### Post by jakonj on 2008-06-17
Long time ago on xubuntu (with gui) i tried to set up printer from console. Since that time that command is still here but im not sure that it will work. Try it:

```
sudo lpadmin -p LaserJet -E -v parallel:/dev/lp0 -m ljet4.ppd
```

LaserJet- name of printer
parallel:/dev/lp0 - port where is printer attached (this is default for mine (HP LaserJet 6l))
ljet4.ppd - driver that is used for your printer

Something like this will work :D

---

### Post by GenuineXP on 2008-06-18
Great, I used lpadmin to simply add the printer (the configuration was completely incorrect) and then used the GUI tools from another box to connect to the server and perform the configuration that way (first I tried this via the web interface, but once again the page just never loaded... bug?).

Thanks for the help!

---

