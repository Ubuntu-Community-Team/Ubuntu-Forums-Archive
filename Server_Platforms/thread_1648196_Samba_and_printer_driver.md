---
title: "Samba and printer driver"
date: 2010-12-18
forum: Server Platforms
---

### Post by GabriRuflex on 2010-12-18
Hey guys!
I've a little problem with Samba.

I've installed and configured Samba and all of that but I still have a little problem: I need to upload the printer driver to the samba server. I tried with cupsaddsmb but there were too much problems so I used the "Windows add driver wizard" (right click on the network printer -> properties -> advanced -> new driver...) and all the x86 PCs are ok. I still need to upload the driver for x64 machines but now the advanced dialog is greyed!!

Do you know where I was wrong?
Thank you guys :)

Here my smb.conf:
```
#======================= Global Settings =======================
[global]
   workgroup = WORKGROUP
   netbios name = bertoni.local
   hosts allow = 127.0.0.0/8 10.0.0.0/8 172.16.0.0/12 192.168.0.0/16
   guest ok = yes
   security = share
   #usershare allow guests = yes
   server string = Server-Bertoni
   #name resolve order = wins lmhost bcast host
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
########## Printing ##########
   load printers = yes
   printing = cups
   printcap name = cups

#======================= Share Definitions =======================
[www]
   comment = Apache Service
   path = /var/www

[documenti]
   comment = Documenti condivisi
   path = /home/ospite
   writeable = yes

[HP_LaserJet_1160]
   comment = HP LaserJet 1160
   path = /var/spool/samba
   browseable = yes
   guest ok = yes


[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   guest ok = yes
   read only = yes
   write list = root

```

I think that there could be a permission problem but I don't know where.
In x86 PCs I can install the printer and print without any problems.

---

### Post by HermanAB on 2010-12-19
Howdy,

Note that CUPS makes all printers look like Postscript printers.  So you can hook any Windows system up to a CUPS server by selecting a ***mon postscript driver, like Apple Laser Writer II (top of the list) and then the printer will essentially work.  The fancy features will not (selecting trays etc) but it will print.

BTW, what is up with the stupid forum turning c o m into *** all of a sudden?

---

### Post by GabriRuflex on 2010-12-19
I need that samba automatically provides the windows driver when a windows client connects to the samba shared printer.

---

### Post by HermanAB on 2010-12-19
Yes, I gathered that - except that most users don't need it - as explained above.

You need to go to the Samba project web site and read the manual.

---

### Post by GabriRuflex on 2010-12-19
Ok, but I'd like to implement it.
Can someone help me?

---

### Post by elico on 2010-12-25
so you just need samba to install automatic the drivers for the printer?
so i assume the printer is working..

ok i will look up for it.

small google found this nice thing :)
[http://lists.samba.org/archive/samba/2007-March/129995.html](http://lists.samba.org/archive/samba/2007-March/129995.html)
and this
[http://www.linuxquestions.org/questions/linux-enterprise-47/samba-cups-windows-automatic-driver-install-385822/](http://www.linuxquestions.org/questions/linux-enterprise-47/samba-cups-windows-automatic-driver-install-385822/)

---

