---
title: "FieldPiece HVAC Guide"
date: 2011-03-13
forum: The Cafe
---

### Post by cheesekiller on 2011-03-13
I wasn't sure where to post this so I started here because this is probably as off-topic as you can get.


recently I purchased a Fieldpiece HVAC Guide 
[http://www.amazon.com/Fieldpiece-Guide-System-Analyzer-Check/dp/B0039USD1G](http://www.amazon.com/Fieldpiece-Guide-System-Analyzer-Check/dp/B0039USD1G)

It isn't designed for linux and knowing it probably wouldn't work i tried it with wine (it didn't work). Well heres the fun part I tried it with my windows seven computer and what do ya know it wont work here either.... hell they even spelled technician wrong on their own software. First I had the same problem I did with wine (it wouldn't find the device and just kept giving me errors when scanning ports). Now it finds the device and connects to it but when it goes to transfer the files (they appear to be nothing more then excel files [spreadsheets]from what I can see in the manual)my CPU hits 100% for like 45 seconds and then when i go to the directory it is supposed to be saving it in THERES NOTHING!

I was wondering if sense it is probably just like a storage and the files are already made on the device (I'm assuming like an idiot here) if there might be a way to possibly mount the damn thing as a drive and just drag and drop the files.   However i did notice the USB cable has 2 LEDs at the end of it instead of any kind of connector so I'm assuming it uses optics to transfer the files(this probably makes what I'm asking impossible). Anyway its worth me asking because if it lets me use it with Ubuntu and keeps me away from that windows seven beast I'd be twice as happy as just being able to use it.

---

### Post by wirepuller134 on 2011-03-13
Can't help on the Liux part, but here is the manufacturer product page. It says it is compatible with Windows 7 Vista and XP.  [http://www.fieldpiece.com/hvac-guide-system-analyzer/hg2](http://www.fieldpiece.com/hvac-guide-system-analyzer/hg2)

---

### Post by oldfred on 2011-03-13
USB is supposed to be a standard.

In terminal after you plug it in what does this say:

lsusb 

I would think their software is just reading & converting a text file or csv file to a spreadsheet.

---

### Post by mips on 2011-03-13
> **cheesekiller said:**
> However i did notice the USB cable has 2 LEDs at the end of it instead of any kind of connector so I'm assuming it uses optics to transfer the files(this probably makes what I'm asking impossible).

Uses IR2 (Infra Red) interface via USB but the USB standards still aplly.

Did you upgrade the firmware of the device?
[http://www.fieldpiece.com/support/downloads#Download](http://www.fieldpiece.com/support/downloads#Download) a Test from your HVAC Guide to Your PC

I'm pretty sure that there must be a way to get the data downloaded to Linux as it probably uses a simple serial protocol of sorts. Once you have it working in windows 7 mabye you can analyse the USB port it's connected to in order to see what's going on.

---

### Post by cheesekiller on 2011-03-13
well as I stated I am using it with windows 7 and it doesn't work it lets me get connected and then pretends to transfer the file but doesn't. As of today I have booted up an old windows xp computer and it gets just as far and doesn't transfer the files.

As for the terminal command you want me to plug it in and then type that in correct?  I will go attempt that now and edit this with what comes back.
                  Thanks all.:)

the results of the command are as follows:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 

The only things I have plugged in are the HVAC GUIDE and my bluetooth dongle.
As to reply to mips I cant really connect even with windows (and yes i've tryed to upgrade)....    Though I would much rather use linux. My company mainly uses linux on our computers anyway :)

---

### Post by oldfred on 2011-03-13
It is showing two devices. 

Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Microdia Sonix USB 2.0 Camera

Do you have a camera plugged in also?

---

### Post by cheesekiller on 2011-03-13
I believe that is my netbooks camera. I had just plugged the HVAC Guide into my netbook cause I had it close by.   Its an acer aspire one running ubuntu 10.10 if that helps any.  I mostly use the netbook at work so if I can make it work with my netbook thats a definate plus! :)

---

### Post by cheesekiller on 2011-03-19
poke?

---

### Post by oldfred on 2011-03-20
Is the Technology Devices International your link to your device? Does it show as a data device from places? My camera flash mounted as a USB flash device just appears as another device & I can scroll thru all the data.

---

### Post by cheesekiller on 2011-03-20
yes that is my device because it doesn't show up if i unplug it. No it doesn't show up in places.  Also I still can't get it to work WITH ITS PROGRAM in windows. I have contacted the manufacturer and haven't gotten a reply.

---

### Post by tgalati4 on 2011-03-20
A couple of $3 instant thermometers and a wet paper towel will give you the performance of an AC unit.  You just need a decent psychometric chart.  Cross platform too.

---

### Post by cheesekiller on 2011-03-21
very funny but that won't calculate superheat.  Also I work on ice machines, coolers, freezers, ice block coolers.... etc

---

