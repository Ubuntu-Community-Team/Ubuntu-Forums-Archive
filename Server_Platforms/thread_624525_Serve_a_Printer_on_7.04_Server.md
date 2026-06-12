---
title: "Serve a Printer on 7.04 Server"
date: 2007-11-27
forum: Server Platforms
---

### Post by petersfreeman on 2007-11-27
I have set up 7.04 Server and have it serving a file share to my Windows XP machines on my LAN.  Now I have connected an Epson Stylus 600 Colour to the parallel port and want to serve this printer to my Windows XP machines on my LAN.

How do I go about it?

Thank you,

Peter

---

### Post by petersfreeman on 2007-11-27
I have moved a little forward in that I just installed CUPS by typing:

    sudo apt-get install cupsys

It installed fine and then I had a look at the /etc/cups/cupsd.conf file.

I believe I need to modify the file somehow to describe the printer attached to the parallel port, and indicate the port.

Can anyone point me in the right direction?  In the menatime, I'll continue hunting around....


Thanks,

Peter

---

### Post by petersfreeman on 2007-11-27
Moving right along...

I read that I need a printers.conf file to list the printers attached to the server.  Cutting, pasting and editing the infomration from someone else's printers.conf, I get:

[FONT="Courier New"]Info Epson Stylus 600 Colour
Location home
DeviceURI usb:/dev/unlpt0
State Idle
StateTime 1152564753
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
AllowUser webdude
OpPolicy default
ErrorPolicy stop-printer[/FONT]

Will this work?

Thanks,

Peter

---

### Post by petersfreeman on 2007-11-27
Looks like my printers.conf setup did not work.  I notice that there is an "interfaces" directory.  perhaps this is where I identify the ports and lpt0?

---

### Post by sciurus on 2007-11-29
This will be much easier if you use the CUPS web interface on port 631. You may need to alter your cups configuration; i think by default the web interface can only be reached from localhost.

Once you get the printer set up in CUPS, you can add it to Windows using the ipp:// url or make it browseable through SAMBA.

---

