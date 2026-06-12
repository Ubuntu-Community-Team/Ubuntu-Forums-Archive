---
title: "CUPS, Samba and pushing Windows drivers"
date: 2012-05-02
forum: Server Platforms
---

### Post by SkateboarderM15F17 on 2012-05-02
Hi All,

This is my first time posting on the Ubuntu forums after years of  lurking and always finding a thread with answers to my problems. 

I'm working on a print server to replace our unreliable Windows server that keeps crashing and causing us all sorts of headaches.

I'm using CUPS and SAMBA on Ubuntu 10.04. So far I've successfully added all of our printers to CUPS, got them working with the correct drivers then shared them with SAMBA. I've also managed (after much confusion and frustration) to have SAMBA automatically push out Windows drivers for each printer and so that they can be automatically installed on each Windows client that adds the printer. So far so good. All of the features of our printers are working just as they would on our Windows print server.

I added each printer with CUPS Postscript drivers then used "Printer Properties > Change Driver" method in Windows to upload the correct drivers for each printer. This worked for every printer.

The Dymo driver for CUPS installed easily for each different model of the Dymo Labelwriters. I could print from CUPS just fine with each model.  

The trouble started with adding the Windows Dymo drivers to the Samba print$ share. I followed the same "Printer Properties > Change Driver" method that worked for the other printers. The driver for the first Dymo uploaded just fine (Dymo Labelwriter 400). When I attempted to change the driver for another Dymo ( Lable Writer 450, different model) I could only see the drivers for the Dymo Labelwriter 400 as being available on the server. So I attempted to upload the drivers for the 450 and selected the same Dymo driver INI file (then picked the 450 model instead of 400). 

I receive an error when Windows attempts to copy the driver to the server. I suspect this is because all of the Dymo drivers use the same INI file and it cannot be uploaded to the print$ share more than once. Is there a way around this that will allow me to upload more than one driver from the Dymo INI? (instead of just the 400 model).

I apologize if I haven't explained this very clearly. Thank you in advance for any help.

---

### Post by LHammonds on 2012-05-03
Sounds like you are a much more advanced user than me (meaning everything below may be completely irrelevant to you) but when I started setting up my Zentyal print server, I did some research to find out what drivers come with the basic OS for WinXP and Win7.  I then figured out which drivers were close enough to the physical printers I had and still allowed control of features such as selecting which print tray to use.

After figuring out which drivers that come with the client OS works with the print queue, I then setup my logon script to automatically add the print queue using the driver that is already on the client PC (that works).

This way, I avoided the problem of specific drivers needing to be installed...since we have many users that go from PC to PC and need different printers all the time.

Here is an example of what I'm talking about:

Real Printer --> Brother HL-5250DN

Windows XP has "Brother HL-2460"
Windows 7 has "Brother HL-5250DN series"

Real Printer --> HP LaserJet P4014N

Windows XP has "HP LaserJet 4000 Series PCL6"
Windows 7 has "HP LaserJet P4014/P4015 PCL6"

Real Printer --> Toshiba e-STUDIO 255SE

Windows XP has jack squat for Toshiba so we will use "HP LaserJet 4"
Windows 7 has "TOSHIBA e-STUDIO282 PS3"

To add the above 3 printers above to a Windows XP machine, I run the following commands:
```

rundll32 printui.dll,PrintUIEntry /b "CITY1-BUILDING1-OFFICE1-FRONTDESK" /x /n "required but unused" /if /f %windir%\inf\ntprint.inf /r "http://192.168.107.22:631/printers/CITY1-BUILDING1-OFFICE1-FRONTDESK" /m "Brother HL-2460"
rundll32 printui.dll,PrintUIEntry /b "CITY1-BUILDING1-OFFICE2-RECEPT" /x /n "required but unused" /if /f %windir%\inf\ntprint.inf /r "http://192.168.107.22:631/printers/CITY1-BUILDING1-OFFICE2-RECEPT" /m "HP LaserJet 4000 Series PCL6"
rundll32 printui.dll,PrintUIEntry /b "CITY1-BUILDING2-OFFICE2-MAILROOM" /x /n "required but unused" /if /f %windir%\inf\ntprint.inf /r "http://192.168.107.22:631/printers/CITY1-BUILDING2-OFFICE2-MAILROOM" /m "HP LaserJet 4"

```
To add the above 3 printers above to a Windows 7 machine, I run the following commands:
```

rundll32 printui.dll,PrintUIEntry /b "CITY1-BUILDING1-OFFICE1-FRONTDESK" /x /n "required but unused" /if /f %windir%\inf\ntprint.inf /r "http://192.168.107.22:631/printers/CITY1-BUILDING1-OFFICE1-FRONTDESK" /m "Brother HL-5250DN series"
rundll32 printui.dll,PrintUIEntry /b "CITY1-BUILDING1-OFFICE2-RECEPT" /x /n "required but unused" /if /f %windir%\inf\ntprint.inf /r "http://192.168.107.22:631/printers/CITY1-BUILDING1-OFFICE2-RECEPT" /m "HP LaserJet P4014/P4015 PCL6"
rundll32 printui.dll,PrintUIEntry /b "CITY1-BUILDING2-OFFICE2-MAILROOM" /x /n "required but unused" /if /f %windir%\inf\ntprint.inf /r "http://192.168.107.22:631/printers/CITY1-BUILDING2-OFFICE2-MAILROOM" /m "TOSHIBA e-STUDIO282 PS3"

```

Is it possible that you can use the same (or similar) Dymo print drivers on the client and work just fine for different Dymo printers?

LHammonds

---

