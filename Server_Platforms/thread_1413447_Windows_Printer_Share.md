---
title: "Windows Printer Share"
date: 2010-02-22
forum: Server Platforms
---

### Post by petersenmde on 2010-02-22
Hi,

I'm having some problems with a windows printer I am trying to share.

I have a Dymo thermal label printer connected via serial to a Windows XP Pro work station. The printer is shared on the Windows box. On a second Windows XP Pro work station I have the printer driver installed and connecting via a local port to the printer (//sambaserver/Dymo).

When I set this up over a year ago, I remember having difficulty connecting to windows shared printers anonymously. On the server, I had installed the gnome desktop, so I used the printer tool under System/Administration to add a user name and password to connect to shared windows printers. The printer is setup as a raw printer (on the server) and the Windows XP workstations have the driver installed on them.

The problem I am encountering is changing the printer local port settings on the one Windows XP work station also changes the settings on the other Windows XP work station. The workstation with the serial connection works fine until I go to the second workstation and change the port setting from serial to //sambaserver/dymo. Then the port settings get changed from serial to //sambaserver/dymo on the work station with the printer connected via serial.

I have 2 other network printers that work fine printing from both windows and debian work station.

Current Setup:

Samba Domain
Ubuntu 8.04 LTS 64 bit
Samba 3.0.28a
CUPS 1.3.7

Relevant smb.conf

[global]
printing = cups
print cap = cups

[printers]
comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
guest ok = yes
create mask = 0600
use client driver = yes

Anyone have a tried and true way of sharing a windows printer?
Thanks for any assistance

Mark

---

### Post by Vegan on 2010-02-22
So called Win Printers do not have a proper print engine, but rather use Windows to do the work and then a simple raster is sent to the printer. Makes its useless for other platforms.

For that reason I do not buy Windows specific printers.

---

