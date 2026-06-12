---
title: "Slow printers?"
date: 2007-12-17
forum: Server Platforms
---

### Post by fizgig on 2007-12-17
I have two printers installed on my feisty server.  They are both hp printers and I am able to print to them from xp.

The trouble is that whenever I select either of the two printers in my printer selection box in xp, there is a 30 second delay before I get my options.

Anyone have any ideas?

printers.conf
```
root@Massive:/etc/cups# vi printers.conf
# Printer configuration file for CUPS v1.2.4
# Written by cupsd on 2007-12-03 08:19
<Printer HP-PSC-1610>
Info HP PSC 1600 series
Location Local Printer
DeviceURI hp:/usb/PSC_1600_series?serial=HU53ODR0CBL0
State Idle
StateTime 1191446840
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
<Printer HP_DeskJet_1220C_USB_SG08A130H9OK_HPLIP>
Info HP DeskJet 1220C
Location Local Printer
DeviceURI hp:/usb/DeskJet_1220C?serial=SG08A130H9OK
State Idle
StateTime 1196698790
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

```
smb.conf section
```
[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
   writable = yes
   create mode = 0700

```

---

### Post by tgilber1 on 2007-12-21
Take a look at the /var/log/cups/*.log files for some indication.  If do not understand the log files, then post a small excerpt of the failed part of the log.  Additionally, the cups.conf, mime.conv, & mime.types files will be helpful to help.

Rather then use samba, if your window boxes are XP, try using IPP protocol.  When you set up Windows, choose network and populate something like the following

http://<IPaddress>:631/printers/<name of CUPS printer>

Note 1:  The name of the printer is displayed when you type lpq on the terminal command line (similar to the DOS prompt in Windows) but much better.  To access terminal, from the GUI, select Applications#Accessories#Terminal

Note 2:  The "printers" part of the destination is required, since it is the locations of all the printers in CUPS.  You can omit the name of CUPS printer name, which will cause CUPS to choose the default printer.  If a default printer is not selected, you will not be able to print.  I have had some problems with getting this to work.  Hence, I always populate the actual printer name.

Below is an example of what you would type for CUPS printer  destination in Windows IP

[http://192.168.1.2:631/printers/myprinter](http://192.168.1.2:631/printers/myprinter)

---

