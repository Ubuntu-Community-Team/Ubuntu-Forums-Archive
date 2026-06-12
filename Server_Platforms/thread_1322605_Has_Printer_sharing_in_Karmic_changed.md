---
title: "Has Printer sharing in Karmic changed?"
date: 2009-11-11
forum: Server Platforms
---

### Post by RichardCL on 2009-11-11
Hi Forum,

I'm trying to setup a simple print-share.

My HP CP1215 is connected to USB
```
richard@ceaelserver:~$ lpinfo -v
```
> network beh
network ipp
network http
serial serial:/dev/ttyS0?baud=115200
direct scsi
network lpd
network socket
direct usb://HP/Color%20LaserJet%20CP1215
direct hp:/usb/HP_Color_LaserJet_CP1215?serial=LJ041MJ
direct hpfax
richard@ceaelserver:~$

I've tried to follow [this]("http://ubuntuforums.org/showthread.php?p=1831119")

Ubuntu's [configuration page]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu") isn't too helpful because the server is headless and I'm using puTTy so I need commandline.

Cupsys is not found

```
richard@ceaelserver:~$ sudo /etc/init.d/cupsys restart
```
> sudo: /etc/init.d/cupsys: command not found

When I search for a printer in the GUI on the client 192.168.178.25:631 I get a message that no printer is connected?

Any ideas?


Rich

---

### Post by MockY on 2009-11-11
I'm baffled as well.
I installed my printer on my main Karmic machine. Adding that shared printer is easy in Intrepid since all I have to do is enter the ip of the main machine and hit find. On a second Karmic machine, the find button is removed from the IPP menu so now I need to know the exact address to it. Just entering the IP and then hit Verify does not yield a successful result.

I figured things like this would be easier with newer releases, but apparently not.

---

### Post by RichardCL on 2009-11-12
I've just tried Webmin. Also no success. Should be simple to share a printer between systems.

---

### Post by davidjxyz on 2009-11-21
I noticed that /etc/cups/cupsd.conf changed one line when upgrading from Intrepid to Karmic.

Browsing On

was changed to:

Browsing Off

I edited this line back to Browsing On ($ sudo nano /etc/cups/cupsd.conf) then went to Printing setup (System -> Administration -> Printing) and added my network printer back again (New -> Printer -> Network Printer -> Find Network Printer -> enter your printer host name and hit Find).

---

### Post by DarkKitsune on 2009-11-22
How do I find my printer's host name? oo;

---

