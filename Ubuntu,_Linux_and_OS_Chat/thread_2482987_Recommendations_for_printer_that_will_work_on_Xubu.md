---
title: "Recommendations for printer that will work on Xubuntu"
date: 2023-01-16
forum: Ubuntu, Linux and OS Chat
---

### Post by Ralph L on 2023-01-16
My HP printer recently failed, so I am looking for a new one. I have always used HP printers, because the HP supplied software (HPLIP) seemed to work. However, recently HP has been requiring their printers to have Internet access. I understand that any HP printer that ends in "e" requires Internet access to run, for example HP OfficeJet Pro 8035e (correct me if I am wrong). For a variety of reasons I would rather it not have access to Internet required. So I am looking for a printer that doesn't require Internet access. I don't do much printing, probably 100 to 150 pages per year. I would like a printer that uses little electricity when idle, and that starts up fast when I need to print a page and the printer has been idling for a week. I need the function: print, scan, copy. I can take or leave faxing. I use Simple Scan for scanning so I would like the printer to be compatible with that. To avoid HP's move to require all HP printers to have Internet access, I am probably looking for a non-HP printer.

Any recommendations for a (non-HP) printer that is easy to install in Xubuntu, is fairly cheap, and meets most of the above requirements. Any help appreciated.

Thanks,
Ralph

---

### Post by gezzer2 on 2023-01-17
i have a brother MFC-L3710CW colour laser multi-function printer. Xubuntu found it on installing the OS and everything just works without any input from me ...

---

### Post by dragonfly41 on 2023-01-17
I have used an HP LaserJet  2100 M for decades. No Internet access.
Black and white only. Toner Cartridge.

---

### Post by slickymaster on 2023-01-17
Not a support question

*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by Ralph L on 2023-01-17
Slickymaster

Where should I post a request for help to find printers that work under xubuntu. I would like to hear from people that have actually gotten specific non-HP printers to work. I don't want to buy a printer that is very difficult to get working (printing and scanning).

I AM asking for support. Where do I post???

Ralph

---

### Post by QIII on 2023-01-17
Hello, RalphL.

This sub-forum is the correct place for your query.  You are asking for purchase recommendations, not technical help with the OS.  All answers will be opinion -- and everyone has one of those..

---

### Post by zebra2 on 2023-01-18
A Brother anything should work fine.  I use a Brother Laser Jet. No drivers required.  I also have a very old Canon printer/scanner that has never had a ink cartridge installed.  I have used it for scanning only.  No driver required.  

I agree with the internet thing  and Internet.  The company I recently retired from bought a Cheap HP printer for a office job.  We could not access or install drivers without internet.  It went in the trash because we didn't want to take responsibility for giving access to the company Intranet. 

When I say "no driver required" in this post it goes with a Ubuntu 22.04 system. I don't know anything about Xubuntu.

---

### Post by oldfred on 2023-01-18
I have a brother with my Kubuntu 22.04 install:
lsusb shows:
[FONT=monospace][COLOR=#000000]Bus 001 Device 002: ID 04f9:0428 Brother Industries, Ltd HL-L2390DW[/COLOR]
It also has Internet.

I think with 20.04, scanning did not work until I added Internet connection.
[/FONT]

---

### Post by Ralph L on 2023-01-25
Although I received an email containing the following post by bellasmith9044, it did not get added to this thread. So I am adding it.
```
There are several non-HP printers that are compatible with Xubuntu and can be easily installed without requiring Internet access. Some options to consider include:
* Brother HL-L2350DW: This laser printer is a great option for low-volume printing and is compatible with Simple Scan. It's fast and energy efficient, and it's easy to install on Xubuntu using the Brother Linux drivers.
* Canon PIXMA TR4520: This all-in-one inkjet printer is compatible with Simple Scan, and it can print, scan, copy and fax. It's easy to install on Xubuntu using the Canon Printer driver.
* Epson WorkForce WF-2760: This all-in-one inkjet printer is compatible with Simple Scan and it can print, scan, copy and fax. It's easy to install on Xubuntu using the Epson Printer driver.
* Samsung Xpress M2020w: This laser printer is a great option for low-volume printing and is compatible with Simple Scan. It's fast and energy efficient, and it's easy to install on Xubuntu using the Samsung Linux drivers.


It's recommended to check if the printer you are looking for is compatible with the version of the linux you are using and also to read customer reviews before making a purchase to ensure that it meets your specific needs and that it's easy to install.
```

---

### Post by kurt18947 on 2023-01-27
I'll also recommend Brother. If you go Brother, when you first get it, don't install any drivers or software. Just connect the cables and try to print & scan. That worked for me with a MFC-J 4535DW Inkjet multifunction. There is one thing to be aware of with Brother or I suspect any inkjet - you need to print something once a week or so. If I don't, I need to run a cleaning cycle on the black ink. The colors don't seem to require cleaning as frequently. The black cartridge is original, installed in October 2021 and apparently ink does age, becoming more prone to ink nozzle clogging. Lasers don't have these problems but if you need color multifunction lasers can be $$$ and lasers don't work well for photo printing.

I'm not sure this is exclusive to Brother but from what I've read,HP takes it to extremes. Do some research on HP inkjets and printing with ink cartridges older than about 6 months. If for some reason I couldn't get a Brother printer I'd probably go Canon. Canon does offer linux drivers for many of their printers. Again, drivers may not need to be installed, check first before installing anything.

---

### Post by Ralph L on 2023-01-27
Thank you to everyone who replied to this. I really appreciate it!! I did buy a Brother MFCJ805DW. As several people predicted the drivers were already in Xubuntu 22.04 and mostly worked without any changes. All I had to do was find the right spot in the printer screen menu and select my local area network and the printer showed up in the "printers" menu on Xubuntu. I brought up a Writer document, selected print, and it printed. I then put a page in the scanner feed, brought up Simple Scan, and it scanned it. 

I did have a problem with the Preferences menu in Simple Scan. I brought it up and it froze Simple Scan and displayed only part of the window header, where the "x" for closing it should be. Hence, I couldn't close it and had to kill it with Alt-F2 and xkill. If anyone knows how to fix that please respond.

---

### Post by mIk3_08 on 2023-02-01
> **weltzumerr22 said:**
> Thanks for the tip on Brother printers! It's always helpful to hear from someone who has firsthand experience with a product. Good to know that all you need to do is connect the cables and go for it.

Mine using Brother printer/scanner, I installed it via wireless network and it works smoothly using driverless. My scanner  works great with document scanner and xsane image scanning application. Regards and cheers.

---

### Post by kurt18947 on 2023-02-01
I'll make a couple other suggestions. If your distro doesn't have it by default (many do) install "system-config-printer" Summon it either from the command box (alt-F2) or a terminal. It gives you a little more control over your printer. For scanning my default is gscan2pdf. It has a couple neat tricks and saves anything scanned to .pdf by default but can save in other formats.

---

