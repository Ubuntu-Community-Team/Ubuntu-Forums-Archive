---
title: "General Home File/Print Server Dilemma"
date: 2008-12-20
forum: Server Platforms
---

### Post by bluesy321 on 2008-12-20
I've been playing around with/testing a home file server setup lately with an older PC that I retired from being my primary desktop.  Its an older AthlonXP 2600+ with 1.5GB of RAM.  OS is installed on a 250 GB drive at the moment, but that may change as the drive is total overkill for a server install.  I plan on adding 2-4 1TB hard drives in a mirrored setup for both pairs and striping the second two drives if/when I get them.  The RAID will be controlled by a hardware SATA RAID card is supposed to be supported for Linux or Windows.  I'm also looking to upgrade the NIC to 1gbps at some point, but I'm really not sure if that will be necessary.  The file server will be used for sharing media files on my LAN - XBMC, couple WinXP PCs.  I'd also like to share my HP 5610 AOI from the file server as it doesn't have a built-in print server.  I realize there will be virtually no way to have all the same features available over the network as I do when the device is connected directly to a PC, but that is OK.  The printer will still be close enough to one of the WinXP PCs that I can connect it directly if need be.  However, my wife has to be able to print from her laptop without a lot of complication; in other words, she has to be able to click print and then OK without any problems.  I typically setup her printing prefs to be B&W with draft prints unless she changes it.

So far I've done testing between Ubuntu Server (8.04) with Webmin and Windows 2003.  The system works perfectly in Ubuntu Server, but I have a dilemma with the Print Server portion.  I can't seem to setup the Print Server portion the way I'd like to.  I think I may have to go back to the dark side of Windows unfortunately.

The CUPS system is great for what it does, but it doesn't offer me options of fast/draft printing through Windows which will be the primary client PCs.  Sure I can edit the quality, but whats the point if its still printing just as slow as a good quality print.  I have to wonder if its also using as much ink as a normal print even though the print quality is reduced.  I'm not sure if anyone has any recommendations for a better way to do this, but the only alternatives I see are setting up the server in Windows or purchasing a hardware print server.  With Windows Server, I can load the standard XP driver on my desktop and laptop which allows for the normal print options.  When I configured the printer via CUPS in Ubuntu Server, I had to install a 'CUPS for Windows' print driver that limited the print options I have.  I had to edit the CUPS driver just to enable color printing and I still can't get it to use a fast/draft mode.  When I tried installing the normal WindowsXP print driver on the client and sent a print job to the printer configured via CUPS, the print job would just hang in the queue - Checked the CUPS web interface which didn't even see the job.  The security should have been setup properly though, as I made no changes to the printer configuration and after installing the CUPS for Windows driver on the client the printer worked just fine.  I feel like I must be missing something though; I'd imagine there is a way to setup the print server as almost like a pass-through so it can use the normal Windows driver or something close to it.

I really hadn't had it in my budget or plan for the server setup to get a hardware print server, but I just don't see a way around that other than using Windows for the time being.  It is a shame though; I'd really prefer to use linux for the file server end since I'm really looking for reliability out of the system and Windoze doesn't seem to do as well on that front.  Please tell me I'm missing something...

---

### Post by cariboo on 2008-12-20
Have tried going into Printers-->set printer options and setting draft and grey-scale printing? Check the attached screenshot.


Edit: I just tried changing the printer settings on my Epson R340 to fast economy printing. It worked!

Jim

---

### Post by bluesy321 on 2008-12-20
I have not tried that, but would that allow me to change those options on the client PC or only from the CUPS interface?  It looks as though it would just set the parameters for CUPS which would limit what I can do from the client PC even further.  Its really a necessity that I be able to select those options on the client PC when printing.  Eg, I'd like to be able to set the laptops printing prefs to B&W/Draft as default and be able to go to the properties screen from the print dialog to change the options if needed.

The other thing I didn't explicitly state in my previous post - I'm not married to either Ubuntu Server or Windows Server.  If there is something else out there that will satisfy my requirements, that would be fine.  Those are just the two systems I've tried so far.  I will be receiving some of the additional hardware for Christmas so I'd like to make a decision in order to get this up and running shortly.

---

### Post by bluesy321 on 2008-12-29
Does anyone have any other ideas??

I really just need to be able to change print settings "on-the-fly" from the client PCs.  My wife can't remember to change the "properties" right from the print dialog half the time; I can't really expect her to go to the CUPS interface before she prints anything to change the settings and then change them back afterward.

I've got the two hard drives I need to setup my RAID, and I'm waiting on the controller to arrive.  So I'd like to be done with testing different OSes as soon as possible.  Perhaps this isn't possible since my client PCs are Windows, but I'd at least like confirmation of that before I make a final decision.

---

