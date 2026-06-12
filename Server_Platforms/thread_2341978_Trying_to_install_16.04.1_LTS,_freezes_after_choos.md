---
title: "Trying to install 16.04.1 LTS, freezes after choosing install ubuntu"
date: 2016-11-02
forum: Server Platforms
---

### Post by cuddles2 on 2016-11-02
Hello, i am currently trying to install ubuntu server on a server i got from my school. 

The problem i am having is that my HP Proliant DL385 keeps freezing after choosing install ubuntu.
This is my first time trying to do something like this. My friend who has been working with server for a little while told me to go into the "F6" menu and mark ACPI=off, nolapic and nomodreset. 

After i had done that all i got was a system screen. (See picture "Kernel Panic") (Don't know what to call it)

Then i went on into the BIOS to disable MPS Table.

Now it freezes on the Location selections screen after i select Install Ubuntu.

Thank you for the quick response and sorry if i am and idiot when it comes to this, but it is my first time doing anything like this.

Sincerely Cuddles

---

### Post by jmgangemi on 2016-11-02
Can you please post up the hardware specifications for the server such as:


[LIST]
[*]Processor/CPU Make and Model
[*]Type and amount of RAM
[*]Disk drives and any RAID controllers that may ba installed
[*]Graphics (if any as most servers have very simple graphics adaptors)
[*]Full product model number (Usually on BIOS screen or as a sticker on the server frame)
[*]Serial number (Usually on BIOS screen or as a sticker on the server frame)
[*]BIOS/UEFI version
[/LIST]

Have you tried resetting the BIOS to the factory default settings first and see if that works?  (You may
need to change the boot order so it boots from your Ubuntu CD/USB stick.)

A step I would try is update the BIOS to the latest version that is available with a bootable
update tool (usually this is available from OEMs like HP/Compaq/Dell etc).  As some older BIOSes may have
bugs that stop Ubuntu from booting up or the Linux Kernel cannot talk to it.

If your server has a RAID controller, make sure the drives and the RAID setup you want is correctly configured.

Maybe others may have some more suggestions.

---

### Post by Speculos on 2016-11-03
Hi,

Have you try to install another distribution such as Debian or CentOS just to be sure this isn't related to Ubuntu ISO or something else !?

---

### Post by mastablasta on 2016-11-03
> **cuddles2 said:**
> 
Thank you for the quick response and sorry if i am and idiot when it comes to this, but it is my first time doing anything like this.


not knowing doesn't make you an idiot. [-X

make sure the image is good (md5sum check or torrent download): [URL="https://help.ubuntu.com/community/HowToMD5SUM"][SIZE=2]https://help.ubuntu.com/community/HowToMD5SUM
[/SIZE][/URL] 

and as mentioned try other version of Linux OS. not sure why you need the server, but if its for homeuse i suggest Openmediavault (debian based with a nice web gui) or Nethserver (centos based again with nice webgui for administering). or you can go to basics and just try debian or centos.

if other versions work nicely then try Ubuntu 14.04 LTS. 

other options include netinstall (mini.iso aka barebones), then adding services (e.g. via tasksel - tasksel is run anyway during server install towards the end of install procedure). looks kind of like this: [SIZE=2][http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
[/SIZE]
OBI install: [SIZE=2][https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

kernel panic is quite serious system error.  wiki explains it better:


> A kernel panic (sometimes abbreviated as KP[1]) is an action taken by an operating system upon detecting an internal fatal error from which it cannot safely recover.
...

A panic may occur as a result of a hardware failure or a software bug in the operating system. In many cases, the operating system is capable of continued operation after an error has occurred. However, the system is in an unstable state and rather than risking security breaches and data corruption, the operating system stops to prevent further damage and facilitate diagnosis of the error and, in usual cases, restart.[8]


[/SIZE]

---

