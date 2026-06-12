---
title: "upgrade kills kernel"
date: 2012-10-30
forum: Server Platforms
---

### Post by kouakou on 2012-10-30
I am at a loss as to what is going on with my ubuntu server install. The server was running Ubuntu 11.10 Server and was working fine. I upgrraded to 12.04 and that hosed the Kernel, to get it to boot I had to delete the new kernel and revert to 2.6.32-42-server which worked for a few days till I had to upgrade again. 
After the upgrade the machine would not boot. 
I reverted to 2.6.32-41 and it also worked for a few days and I got another message to upgrade which I did and now the server is dead again ... I iam able to boot if I chose 2.6.32-40, but it is getting tiring to have to do this every few days... I am witts end, what to do what to do?? 

Thanks in advance for the help

---

### Post by chadk5utc on 2012-10-31
I believe this will get you going
In a terminal, run sudo update-grub
Then, type grep menuentry /boot/grub2/grub.cfg
Counting from 0, find the number of the line containing the 2.6 entry you want.
Set that as default in /etc/default/grub and run sudo update-grub again.

---

### Post by 2F4U on 2012-10-31
> After the upgrade the machine would not boot.

There is not enough information in this. How far does it get in the boot process? Did you look into the log files? What are your hardware specs?

---

### Post by kouakou on 2012-10-31
> **2F4U said:**
> There is not enough information in this. How far does it get in the boot process? Did you look into the log files? What are your hardware specs?

The machiine boots and stops at intramfs__ with a blinking cursor. all I can o at that point is type reboot and go back to the begining. 
Below are the servers specs. I have looked at the server logs but they dont tell me anything. 

CPU Supported CPU Type Intel 1.6GHz Atom processor on board
FSB 533MHz
Chipset:North Bridge Intel 945GC
        South Bridge ICH7
Memory Supported:Memory slot 1 x 200Pin
Memory Type Supported DDR2 400/533
       Memory installed 2GB
Expansion Slots: Other 1 x CF card slot
Storage: Serial ATA 2 x SATAII 300
Storage Installed: 2 x 1TB WD HDD
Graphics:Onboard Video Intel GMA 950
Audio:Onboard Audio Realtek ALC858
Channel 8-CH
Communications
First LAN Realtek 8111C(10/100/1000Mbps)
Max LAN Speed 10/100/1000Mbps
Extension Bays
3.5" Internal bays 1
5.25" External bays 1
Front Panel Ports:Front USB 2
Front Audio Ports 2 jacks
Card Reader SD/MMC/MS/XD 4-in-1 Card Reader
Back Panel Ports
VGA 1 x D-Sub
Rear USB 4
RJ45 1
Rear Audio Ports 6 jacks
Power Supply:Power Supply External 65W Power Adapter with Active PFC
Physical SPEC:Dimensions 11.8" x 9.5" x 2.6"

---

