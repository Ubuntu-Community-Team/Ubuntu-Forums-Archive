---
title: "Suggested methods for setting up Print Server for 2 Vista x64 and 3 XP x86 machines"
date: 2009-07-14
forum: Server Platforms
---

### Post by nerr on 2009-07-14
Hey everybody, as the title implies, I'm going to be setting up a print server soon with an HP Deskjet 5650 printer (confirmed to work perfectly in Linux) to print to five machines throughout the house.  Obviously it's a pretty mixed bag, with both of my machines running Windows Vista x64 (Home Premium and Ultimate if it matters), and three Windows XP x86 machines that belong to the rest of the family.

Ideally I would like to be able to print from all five machines to this single printer, no sweat, no issues.  It's currently attached to my Windows Vista Ultimate x64 desktop, and can be easily shared with my Vista Home Premium x64 laptop, but the XP machines are a nightmare to try and configure with this current setup, due to them being x86.  Damn you processor architectures.

Is there a recommended method for sharing a printer with machines of varying architectures and operating systems in one, unified Ubuntu Server environment?  Will I want to share the printer via CUPS and HTTP, or perhaps Samba with SMB?  Any advice I can get is greatly appreciated, since I've been unable to find any threads with advice on how to deal with such a mixed bag of machines.   I only pray that it isn't as difficult to figure out on Linux as it has been on Windows.  Thank you for your help!

---

### Post by irv on 2009-07-14
This is how I have my printer setup to print from any pc in my home. (Actually any one I let on my network can print to my printer).
Buy a inexpensive print server off of ebay. You can buy a wireless one for under $20. Hook it up to your printer and give it a static ip address. Then just set up your pc's to print to a network printer using this ip address and setup the driver for each OS. It just that simple. I have never had a problem doing it this way.

---

### Post by ibutho on 2009-07-14
Our Windows and Linux computers share one printer (an HP Officejet J4580). It wasn't very difficult to setup. Make sure that your CUPS server is configured to accept printing from any hosts on the local network. For the Windows clients, make sure that you have the right drivers installed and configure the clients to print via http e.g. your printers url maybe something like [http://192.168.1.120:631/printers/officejetj4580](http://192.168.1.120:631/printers/officejetj4580). You also need to do something similar on your Linux clients. We didn't need to use SAMBA.

---

