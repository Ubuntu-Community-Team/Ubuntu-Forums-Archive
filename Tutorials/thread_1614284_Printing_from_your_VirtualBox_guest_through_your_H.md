---
title: "Printing from your VirtualBox guest through your Host's printer"
date: 2010-11-05
forum: Tutorials
---

### Post by amateur_mav on 2010-11-05
The instructions for enabling access to a Linux host's printer
from a Windows VirtualBox client goes like this:

Linux:
1. Install your printer driver. Get your printer working.
2. Add your printer to CUPS at [http://localhost:631/admin](http://localhost:631/admin)
If CUPS is not installed in your computer, go to the [official CUPS website]("http://www.cups.org/") to download it.
You may also want to read the Ubuntu [Official Documentation]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/cups.html") here. 

3. Set your virtual machine's Network to Bridged Adapter (eth0) in Settings and connect the cable (Advanced menu).
4. Start your VirtualBox machine.
5. Enter "ifconfig" at a terminal prompt to list your current network settings
and copy down your host's (eth0) address. You can also access this address using Network Tools.

Windows:
1. Add a new Network printer in "Printers and Faxes" from the Control Panel
2. Enter the URL address of your host's printer.
For example: [http://192.168.0.2:631/printers/Your_printer's_name]("http://192.168.0.2:631/printers/Your_printer%27s_name")

You need the :631 after your host's address as this is the port
that CUPS listens to. Your_printer's_name is the name of the printer you added to CUPS.

If no connection is made, check your firewall settings.


If you want a Linux VirtualBox client to access a Window's host's printer, you're going the wrong direction!
:)

---

### Post by terdon on 2010-11-18
Hi, thanks for the tip! Isn't it also possible to directly install the printer through the usb connection? I cannot get my guest XP to see the printer. Although it comes up under the shared devices in the virtual box menu, its name is greyed out...

Any ideas?

---

### Post by b&amp;m on 2010-11-24
> **amateur_mav said:**
> The instructions for enabling access to a Linux host's printer
from a Windows VirtualBox client goes like this:

Linux:
1. Install your printer driver. Get your printer working.
2. Add your printer to CUPS at [http://localhost:631/admin](http://localhost:631/admin)
If CUPS is not installed in your computer, go to the [official CUPS website]("http://www.cups.org/") to download it.
You may also want to read the Ubuntu [Official Documentation]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/cups.html") here. 

3. Set your virtual machine's Network to Bridged Adapter (eth0) in Settings and connect the cable (Advanced menu).
4. Start your VirtualBox machine.
5. Enter "ifconfig" at a terminal prompt to list your current network settings
and copy down your host's (eth0) address. You can also access this address using Network Tools.

Windows:
1. Add a new Network printer in "Printers and Faxes" from the Control Panel
2. Enter the URL address of your host's printer.
For example: [http://192.168.0.2:631/printers/Your_printer's_name]("http://192.168.0.2:631/printers/Your_printer%27s_name")

You need the :631 after your host's address as this is the port
that CUPS listens to. Your_printer's_name is the name of the printer you added to CUPS.

If no connection is made, check your firewall settings.


If you want a Linux VirtualBox client to access a Window's host's printer, you're going the wrong direction!
:)

Very useful, thanks a lot.

Let me just add one bit more of information: on the Linux side in  System/Administration/Printing/Server/Setting be sure that the flag  "Allow printing from the Internet" is set.
:)

---

### Post by Birdman2010 on 2012-04-17
> **amateur_mav said:**
> The instructions for enabling access to a Linux host's printer
from a Windows VirtualBox client goes like this:

Linux:
1. Install your printer driver. Get your printer working.
2. Add your printer to CUPS at [http://localhost:631/admin](http://localhost:631/admin)
If CUPS is not installed in your computer, go to the [official CUPS website]("http://www.cups.org/") to download it.
You may also want to read the Ubuntu [Official Documentation]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/cups.html") here. 

3. Set your virtual machine's Network to Bridged Adapter (eth0) in Settings and connect the cable (Advanced menu).
4. Start your VirtualBox machine.
5. Enter "ifconfig" at a terminal prompt to list your current network settings
and copy down your host's (eth0) address. You can also access this address using Network Tools.

Windows:
1. Add a new Network printer in "Printers and Faxes" from the Control Panel
2. Enter the URL address of your host's printer.
For example: [http://192.168.0.2:631/printers/Your_printer's_name]("http://192.168.0.2:631/printers/Your_printer%27s_name")

You need the :631 after your host's address as this is the port
that CUPS listens to. Your_printer's_name is the name of the printer you added to CUPS.

If no connection is made, check your firewall settings.


If you want a Linux VirtualBox client to access a Window's host's printer, you're going the wrong direction!
:)

I am learning a lot about Mint (ubuntu flavor), but I'm not ready to commit. So, for now, how do I go the "wrong direction"?  I cannot get it to hit my Windows 7 printer (Epson Artisan 725).

Thanks!

---

### Post by Elfy on 2012-04-17
Old thread closed.

If you need help then please start a new thread - if it's for Mint - try the Mint forums, if you need to post here about Mint then please use the Other O/s Forum - [http://ubuntuforums.org/forumdisplay.php?f=401](http://ubuntuforums.org/forumdisplay.php?f=401)

---

