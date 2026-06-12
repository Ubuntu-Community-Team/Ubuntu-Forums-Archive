---
title: "Samba / Printer Server"
date: 2006-06-01
forum: Server Platforms
---

### Post by diablo668 on 2006-06-01
Hi, I'm sorry if this has been asked before, but couldn't find a real anwser to the problem, I'm pretty new to the linux scene, but trying to learn

I'm trying to create a samba file server with a printer server

The problem I'm encountering is that the printer doesn't do a thing when trying to print a testpage with hplip

Ubuntu 5.10 server install (no X server,all updates, latest kernel,...)
cupsys is installed and up and running
hplip 0.9.11 installed an configured using the guide on the off. site
the printer is a hp officejet 4212 (supported by hplip)

```
root@Diablo668:/hplip-0.9.11# hp-setup -a

HP Linux Imaging and Printing System (ver. 0.9.11)
Printer/Fax Setup Utility ver. 2.0

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Using device: hp:/usb/officejet_4200_series?serial=XXXXXXXXXX

Setting up device: hp:/usb/officejet_4200_series?serial=XXXXXXXXXX



PRINT QUEUE SETUP
Using queue name: officejet_4200

Found a possible PPD file: /usr/share/ppd/HP/HP-OfficeJet_4200-hpijs.ppd.gz

Adding print queue to CUPS:
Device URI: hp:/usb/officejet_4200_series?serial=XXXXXXXXXX
Queue name: officejet_4200
PPD file: /usr/share/ppd/HP/HP-OfficeJet_4200-hpijs.ppd.gz
Location:
Information: Automatically setup by HPLIP
Printing test page...
lpr: officejet_4200: unknown printer
Test page has been sent to printer. Waiting for printout to complete...


FAX QUEUE SETUP
Using queue name: officejet_4200_fax

Adding fax queue to CUPS:
Device URI: hpfax:/usb/officejet_4200_series?serial=XXXXXXXXXX
Queue name: officejet_4200_fax
PPD file: /usr/share/ppd/HP/fax/HP-Fax-hplip.ppd.gz
Location:
Information: Automatically setup by HPLIP

Done.

```

```
root@Diablo668:/hplip-0.9.11# hp-testpage

HP Linux Imaging and Printing System (ver. 0.9.11)
Testpage Print Utility ver. 4.0

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Using device: hp:/usb/officejet_4200_series?serial=XXXXXXXXXX

Printing test page to printer officejet_4200...
lpr: officejet_4200: unknown printer
Test page has been sent to printer. Waiting for printout to complete...

If an error occured, or the test page failed to print, refer to the HPLIP website
at: http://hplip.sourceforge.net for troubleshooting and support.

Done.


```

```
root@Diablo668:/hplip-0.9.11# tail -f /var/log/cups/error_log
I [02/Jun/2006:01:54:36 +0200] Setting officejet_4200 printer-is-accepting-jobs to 1 (was 0.)
I [02/Jun/2006:01:54:36 +0200] Setting officejet_4200 printer-state to 3 (was 5.)
E [02/Jun/2006:01:54:36 +0200] Unable to backup printers.conf - No such file or directory
I [02/Jun/2006:01:54:36 +0200] Saving printers.conf...
I [02/Jun/2006:01:54:36 +0200] New printer 'officejet_4200' added by 'root'.
I [02/Jun/2006:01:54:47 +0200] Setting officejet_4200_fax device-uri to "hpfax:/usb/officejet_4200_series?serial=XXXXXXXXXX" (was "file:/dev/null".)
I [02/Jun/2006:01:54:47 +0200] Setting officejet_4200_fax printer-is-accepting-jobs to 1 (was 0.)
I [02/Jun/2006:01:54:47 +0200] Setting officejet_4200_fax printer-state to 3 (was 5.)
I [02/Jun/2006:01:54:47 +0200] Saving printers.conf...
I [02/Jun/2006:01:54:47 +0200] New printer 'officejet_4200_fax' added by 'root'.
```

the printer is connected

```
root@Diablo668:/hplip-0.9.11# /usr/lib/cups/backend/hp
direct hp:/usb/officejet_4200_series?serial=XXXXXXXXX "HP officejet_4200_series" "hp:/usb/officejet_4200_series?serial=XXXXXXXXX" "MFG:hp;MDL:officejet 4200 series;CMD:LDL,MLC,PML,DYN;CLS:PRINTER;1284.4DL:4d,4e,1;SN:XXXXXXXXX;S:0380008000020020002c1480022c2500046;Z:007;"

```


cups debug log
```

I [02/Jun/2006:02:34:21 +0200] Listening to 7f000001:631
I [02/Jun/2006:02:34:21 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
I [02/Jun/2006:02:34:21 +0200] Configured for up to 100 clients.
I [02/Jun/2006:02:34:21 +0200] Allowing up to 100 client connections per host.
I [02/Jun/2006:02:34:21 +0200] Full reload is required.
E [02/Jun/2006:02:34:21 +0200] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [02/Jun/2006:02:34:21 +0200] LoadPPDs: Read "/etc/cups/ppds.dat", 479 PPDs...
I [02/Jun/2006:02:34:22 +0200] LoadPPDs: No new or changed PPDs...
I [02/Jun/2006:02:34:22 +0200] Full reload complete.
I [02/Jun/2006:02:35:50 +0200] Scheduler shutting down normally.
I [02/Jun/2006:02:35:50 +0200] Listening to 7f000001:631
D [02/Jun/2006:02:35:50 +0200] AddLocation: added location '/'
D [02/Jun/2006:02:35:50 +0200] DenyIP: / deny 00000000/00000000
D [02/Jun/2006:02:35:50 +0200] AllowIP: / allow 7f000001/ffffffff
D [02/Jun/2006:02:35:50 +0200] AddLocation: added location '/jobs'
D [02/Jun/2006:02:35:50 +0200] AddLocation: added location '/admin'
D [02/Jun/2006:02:35:50 +0200] DenyIP: /admin deny 00000000/00000000
D [02/Jun/2006:02:35:50 +0200] AllowIP: /admin allow 7f000001/ffffffff
I [02/Jun/2006:02:35:50 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
I [02/Jun/2006:02:35:50 +0200] Configured for up to 100 clients.
I [02/Jun/2006:02:35:50 +0200] Allowing up to 100 client connections per host.
I [02/Jun/2006:02:35:50 +0200] Full reload is required.
D [02/Jun/2006:02:35:50 +0200] LoadAllPrinters: Loading printer officejet_4200...
D [02/Jun/2006:02:35:50 +0200] LoadAllPrinters: Loading printer officejet_4200_fax...
E [02/Jun/2006:02:35:50 +0200] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
D [02/Jun/2006:02:35:50 +0200] LoadDevices: Added device "ipp"...
D [02/Jun/2006:02:35:50 +0200] LoadDevices: Added device "http"...
D [02/Jun/2006:02:35:50 +0200] LoadDevices: Added device "lpd"...
D [02/Jun/2006:02:35:50 +0200] LoadDevices: Added device "socket"...

```

---

### Post by Iowan on 2006-06-02
I read another thread around here somewhere that suggested CUPS and HPLIP don't get along well together.

---

