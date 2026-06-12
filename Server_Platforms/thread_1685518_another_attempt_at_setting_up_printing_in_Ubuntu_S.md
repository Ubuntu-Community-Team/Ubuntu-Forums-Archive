---
title: "another attempt at setting up printing in Ubuntu Server"
date: 2011-02-10
forum: Server Platforms
---

### Post by rogdawg on 2011-02-10
I have posted a question about this in the past, here:

[http://ubuntuforums.org/showthread.php?p=10280662](http://ubuntuforums.org/showthread.php?p=10280662)

I never received an answer.

I am making another stab at this. Today, I have installed Ubuntu Server 10.10 on a machine in my home. I have set the server up as a development server, and I can connect to it from my Macbook, via our wireless router [the Ubuntu Server is connected to the router by cable]. I can view web pages and php pages stored in /var/www on the Ubuntu Server using the browser on my Macbook. I also have gotten the file sharing to work [I created a file an placed it in the shared directory on Ubuntu Server]. So, Apache is working, PHP, MySQL, and SAMBA file sharing all seem to be working just fine. But, I am having a difficult time getting printing to work. 

I have installed cups, following the instructions found here:
[https://help.ubuntu.com/10.10/serverguide/C/cups.html](https://help.ubuntu.com/10.10/serverguide/C/cups.html)

in my /etc/cups/cupsd.conf file, I have this relevant information:
Listen localhost:631
Listen /var/run/cups/cups.sock
Port 631

I have edited the samba config file per the instructions on this page:
[https://help.ubuntu.com/10.10/serverguide/C/samba-printserver.html](https://help.ubuntu.com/10.10/serverguide/C/samba-printserver.html)

The relevant information from the samba config file is:
workgroup = WORKGROUP     << This is something I am not sure is correct
security = user

in the ####### Printing ############ section:
load printers = yes
printing = cups
printcap name = cups

[printers]
comment = All Printers
browseable = yes
path = /var/spool/samba
printable = yes
guest ok = yes
read only = yes
create mask = 0700
use client driver = yes

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
browseable = yes
read only = yes
guest ok = no

I have a photosmart C4200 printer connected to my Ubuntu Server via a USB cable. 
If I run the command:
```
lpinfo -v
```
I see the printer in the results. It is listed like this:
direct usb://HP/Photosmart%20C4200%20series?serial=CN7BCRD0Q304VP

If I run the command:
```
lpstat -a
```

I get this result:
lpstat: No destinations added.

I can see the printer and select it from my MacBook, and it has the following url listed:
smb://ubuntu/HP_Photosmart_C4200_series

If I try to print to that printer from my Macbook, via the ubuntu server, I don't receive an error but, nothing happens. 

If I try to print to the printer from Ubuntu server, using something like:
lp myFile.txt
I get an error: 
lp: Error - no default destination available

If I try to print a document from vim using :hardcopy, I get the error E365: Failed to print PostScript file. 

Does anyone have any suggestion as to how I can correct this. I must be getting close but, I am stumped. I am not sure about the "workgroup" bit in the config file, I don't know how to set the photosmart printer as the default printer on ubuntu (every combination of the printer name that I have tried has caused an error like "Unknown printer or class"), and I am not sure what I need to do to finish setting the printer up so I can print to it from my Macbook.

Thanks in advance for ANY help you can provide.

---

