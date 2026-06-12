---
title: "Server - Setting up a printer"
date: 2005-05-17
forum: Server Platforms
---

### Post by relaxinbob on 2005-05-17
I'm sure somebody had done this on a server...  Here's the scoop:

I have two Ubuntu boxes.  One is a desktop, the other a server.  On the desktop, I can use the usual graphical tools to create and print to a printer.  On the server, however, I can't get anything out of the same printer (and yes, I've moved the USB cable between the two systems  :???: )  

I uncommented the access settings in cupsd.conf and can access and manipulate CUPS through the web interface on the server ([http://litterbox:631)](http://litterbox:631)).  I can create/delete printers, send print jobs, watch them go to the completed list, etc.  I installed lprng as well, and can "lpr somefile", again with no output.  (I figure lprng isn't set up properly, but that's probably a whole different issue...)

I tried queue names of ml-1210 and lp0 - same result.

Thanks,
Bob

---

### Post by Xerampelinae on 2005-05-17
I think you're making it harder than it is.

You just need cups on both machines.  Set up cups on the machine with the printer, so that it can print.  Enable browsing on the machine with the printer--this can be done in /etc/cups/cupsd.conf or by using the /usr/share/cups/enable_browsing script provided with ubuntu (debian?).

If you have your network set up correctly, the other machine should automatically pick up the printer.  If not, you can always add an ipp printer on the other machine, and point the address to the machine with the printer.

---

### Post by relaxinbob on 2005-05-17
The printer is attached to the server.  That's what's not working.  On a system configured as a server, and actually headless/keyboardless, how does one set up a printer?  My only choices are to ssh into the box, or access it by the web interface.

I did an apt-get of
- cupsys
- foomatic-filters-pdds
- lprng

then went into cupsd.conf and commented the lines requiring authentication to administer cups by the web interface.  I also added the Port 631 to allow any machine to access it by the web.  At this point, the admin functions appear to work properly.  I just don't get any activity on the printer when I try to send a test page.

---

