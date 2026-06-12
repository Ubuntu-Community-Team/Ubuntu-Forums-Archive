---
title: "&quot;Filter Failed&quot;: HP Printer not Printing"
date: 2013-05-14
forum: Ubuntu Development Version
---

### Post by fantab on 2013-05-14
I am having trouble printing using my HP printer on "Saucy" (I like saying 'Saucy' :D). 
I have re-installed both 'hplip' and 'cups' but to no avail. I am using everything from official repos. I have no issues printing from other Ubuntu versions and other Distros.

Here is what /var/log/cups/errorlog says:

```
W [14/May/2013:07:13:02 +0530] AddProfile failed: org.freedesktop.DBus.Error.UnknownMethod:No such interface `org.freedesktop.ColorManager' on object at path /org/freedesktop/ColorManager/devices/cups_Deskjet_F4200
W [14/May/2013:07:13:02 +0530] AddProfile failed: org.freedesktop.DBus.Error.UnknownMethod:No such interface `org.freedesktop.ColorManager' on object at path /org/freedesktop/ColorManager/devices/cups_Deskjet_F4200
E [14/May/2013:10:32:40 +0530] [Job 28] Job aborted after 5 unsuccessful attempts.
D [14/May/2013:10:32:40 +0530] [Job 28] The following messages were recorded from 10:32:39 to 10:32:40
D [14/May/2013:10:32:40 +0530] [Job 28] Setting job-hold-until to no-hold
D [14/May/2013:10:32:40 +0530] [Job 28] Job released by user.
D [14/May/2013:10:32:40 +0530] [Job 28] time-at-processing=1368507759
D [14/May/2013:10:32:40 +0530] [Job 28] job-sheets=none,none
D [14/May/2013:10:32:40 +0530] [Job 28] argv[0]="Deskjet_F4200"
D [14/May/2013:10:32:40 +0530] [Job 28] argv[1]="28"
D [14/May/2013:10:32:40 +0530] [Job 28] argv[2]="username"
D [14/May/2013:10:32:40 +0530] [Job 28] argv[3]="Why Nokia and Linux failed, so far | Netrunner MAG"
D [14/May/2013:10:32:40 +0530] [Job 28] argv[4]="1"
D [14/May/2013:10:32:40 +0530] [Job 28] argv[5]="InputSlot=Auto Duplex=None MediaType=Automatic PageSize=A4 OutputMode=Normal ColorModel=RGB number-up=1 job-uuid=urn:uuid:bbe43df2-xxxx-3a94-yyyy-84c71a73d69b job-originating-host-name=localhost time-at-creation=1368507727 time-at-processing=1368507759"
D [14/May/2013:10:32:40 +0530] [Job 28] argv[6]="/var/spool/cups/d00028-001"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[8]="HOME=/var/spool/cups/tmp"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[10]="SERVER_ADMIN=root@Echo"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[11]="SOFTWARE=CUPS/1.6.2"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[13]="USER=root"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[14]="CUPS_MAX_MESSAGE=2047"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[17]="IPP_PORT=631"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[18]="CHARSET=utf-8"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[19]="LANG=en_IN.UTF-8"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[20]="PPD=/etc/cups/ppd/Deskjet_F4200.ppd"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[21]="RIP_MAX_CACHE=128m"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[22]="CONTENT_TYPE=application/pdf"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[23]="DEVICE_URI=hp:/usb/Deskjet_F4200_series?serial=CN95E5912M05BR"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[24]="PRINTER_INFO=Deskjet_F4200"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[25]="PRINTER_LOCATION="
D [14/May/2013:10:32:40 +0530] [Job 28] envp[26]="PRINTER=Deskjet_F4200"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[27]="PRINTER_STATE_REASONS=none"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[28]="CUPS_FILETYPE=document"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[29]="FINAL_CONTENT_TYPE=printer/Deskjet_F4200"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[30]="AUTH_I****"
D [14/May/2013:10:32:40 +0530] [Job 28] Started filter /usr/lib/cups/filter/pdftopdf (PID 3626)
D [14/May/2013:10:32:40 +0530] [Job 28] Started filter /usr/lib/cups/filter/gstoraster (PID 3627)
D [14/May/2013:10:32:40 +0530] [Job 28] Started filter /usr/lib/cups/filter/hpcups (PID 3628)
D [14/May/2013:10:32:40 +0530] [Job 28] Started backend /usr/lib/cups/backend/hp (PID 3629)
D [14/May/2013:10:32:40 +0530] [Job 28] PPD uses qualifier 'RGB.Automatic.'
D [14/May/2013:10:32:40 +0530] [Job 28] PID 3626 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [14/May/2013:10:32:40 +0530] [Job 28] Calling FindDeviceById(Deskjet_F4200)
D [14/May/2013:10:32:40 +0530] [Job 28] Failed to send: org.freedesktop.ColorManager.NotFound:device id 'Deskjet_F4200' does not exists
D [14/May/2013:10:32:40 +0530] [Job 28] Failed to get profile filename!
D [14/May/2013:10:32:40 +0530] [Job 28] no profiles specified in PPD
D [14/May/2013:10:32:40 +0530] [Job 28] Set job-printer-state-message to "no profiles specified in PPD", current level=INFO
D [14/May/2013:10:32:40 +0530] [Job 28] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -dNOINTERPOLATE -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -sMediaType=Automatic -sOutputType=0 -r600x600 -dMediaPosition=7 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=833 -dcupsMediaType=-1 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=17 -dcupsInteger0=26 -scupsPageSizeName=A4 -I/usr/share/cups/fonts -c -f -_
D [14/May/2013:10:32:40 +0530] [Job 28] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[8]="HOME=/var/spool/cups/tmp"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[10]="SERVER_ADMIN=root@Echo"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[11]="SOFTWARE=CUPS/1.6.2"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[12]="USER=root"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[13]="CUPS_MAX_MESSAGE=2047"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[16]="IPP_PORT=631"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[17]="CHARSET=utf-8"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[18]="LANG=en_IN.UTF-8"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[19]="PPD=/etc/cups/ppd/Deskjet_F4200.ppd"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[20]="RIP_MAX_CACHE=128m"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[21]="CONTENT_TYPE=application/pdf"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[22]="DEVICE_URI=hp:/usb/Deskjet_F4200_series?serial=CN95E5912M05BR"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[23]="PRINTER_INFO=Deskjet_F4200"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[24]="PRINTER_LOCATION="
D [14/May/2013:10:32:40 +0530] [Job 28] envp[25]="PRINTER=Deskjet_F4200"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[26]="PRINTER_STATE_REASONS=none"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[27]="CUPS_FILETYPE=document"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[28]="FINAL_CONTENT_TYPE=printer/Deskjet_F4200"
D [14/May/2013:10:32:40 +0530] [Job 28] envp[29]="AUTH_INFO_REQUIRED=none"
D [14/May/2013:10:32:40 +0530] [Job 28] Start rendering...
D [14/May/2013:10:32:40 +0530] [Job 28] Set job-printer-state-message to "Start rendering...", current level=INFO
D [14/May/2013:10:32:40 +0530] [Job 28] Processing page 1...
D [14/May/2013:10:32:40 +0530] [Job 28] Set job-printer-state-message to "Processing page 1...", current level=INFO
D [14/May/2013:10:32:40 +0530] [Job 28] STATE: +connecting-to-device
D [14/May/2013:10:32:40 +0530] [Job 28] PAGE: 1 1 
D [14/May/2013:10:32:40 +0530] [Job 28] prnt/backend/hp.c 745: ERROR: open device failed stat=12: hp:/usb/Deskjet_F4200_series?serial=CN95E5912M05BR
D [14/May/2013:10:32:40 +0530] [Job 28] PID 3629 (/usr/lib/cups/backend/hp) stopped with status 1.
D [14/May/2013:10:32:40 +0530] [Job 28] Hint: Try setting the LogLevel to "debug" to find out more.
D [14/May/2013:10:32:40 +0530] [Job 28] PID 3628 (/usr/lib/cups/filter/hpcups) did not catch or ignore signal 13.
D [14/May/2013:10:32:40 +0530] [Job 28] PID 3627 (/usr/lib/cups/filter/gstoraster) stopped with status 13.
D [14/May/2013:10:32:40 +0530] [Job 28] Hint: Try setting the LogLevel to "debug" to find out more.
D [14/May/2013:10:32:40 +0530] [Job 28] Backend returned status 1 (failed)
D [14/May/2013:10:32:40 +0530] [Job 28] time-at-completed=1368507760
D [14/May/2013:10:32:40 +0530] [Job 28] End of messages
D [14/May/2013:10:32:40 +0530] [Job 28] printer-state=3(idle)
D [14/May/2013:10:32:40 +0530] [Job 28] printer-state-message="Filter failed"
D [14/May/2013:10:32:40 +0530] [Job 28] printer-state-reasons=none
E [14/May/2013:10:57:54 +0530] [Job 29] Stopping unresponsive job.
```

I need help in understanding what is going on and help in resolution? Is anyone else facing this?

---

### Post by fantab on 2013-05-14
Resolved.
Since when do we need to be part of 'lpadmin' group to print? I have always just added myself to 'lp' group. Weird, unless there has been some reasonable change in 13.10.

Added my 'User' to 'lpadmin' and its printing now.

---

### Post by ajgreeny on 2013-05-14
Just for information, I am running Xubuntu 12.04 and even though I have not added myself to the lpadmin group, I am a member by default.

Have you made any manual changes or edits to your groups membership?

---

### Post by fantab on 2013-05-14
Nope... I haven't made any changes. I am sure.

---

### Post by Irihapeti on 2013-05-14
I had a similar problem. I installed CUPS and hplip and found that I wasn't a member of the lpadmin group. I had to add myself to it manually.

I'm using a system built up from a command-line install of saucy with "apt-get install xubuntu-desktop --no-install-recommends". That gives only a basic system without all the other packages that I don't want. But should that make any difference?

---

