---
title: "share printer"
date: 2008-09-03
forum: Server Platforms
---

### Post by nargesi on 2008-09-03
hi every body
i want to share a printer(hp color lasarjet 1600) in network . i instal its driver and print with it in my local computer . now i want to share it for other system (linux and windows). i know i must do it with samba . i share with samba  folder but i cant share printer . is any body share printer in network ? how? please tell me your configuration in  smb.conf  and other configuration .
tanks in advance

---

### Post by hyper_ch on 2008-09-03
a quick google search with "samba share printer" returned as first result: [http://tldp.org/HOWTO/Debian-and-Windows-Shared-Printing/sharing_with_windows.html](http://tldp.org/HOWTO/Debian-and-Windows-Shared-Printing/sharing_with_windows.html)
second result: [http://tldp.org/HOWTO/SMB-HOWTO-9.html](http://tldp.org/HOWTO/SMB-HOWTO-9.html)

Modifying the query by adding "ubuntu hardy" returns as first result:
[http://www.jonathanmoeller.com/screed/?p=224](http://www.jonathanmoeller.com/screed/?p=224)
then we also get this: [http://www.jonathanmoeller.com/screed/?p=181](http://www.jonathanmoeller.com/screed/?p=181)

---

### Post by nargesi on 2008-09-03
i try 
> 
[global]
  printcap name = cups  
  printing = cups   
  security = share   
[printers]   
  browseable = yes   
  printable = yes   
  public = yes   
  create mode = 777   
  guest only = yes   
  use client driver = yes
  guest account = smbprint   
  path = /home/smbprint   


i omit "use client driver = yes" and " guest account = smbprint " and also set "path=/var/spool/samba" . but i dont know the path for my printer  what is it? what should i set for path ? 
thanks in advance

---

### Post by nargesi on 2008-09-05
no one know about path ? 
what's path for printer?

---

### Post by bullgr on 2008-09-05
to share a printer thru samba in the network open smb.conf:
```
sudo nano /etc/samba/smb.conf
```
in the end of the [global] section add the line (if not already there):
```
wins support = yesload printers = yes
```
and in the [printers] section delete the content and add these lines:
```

printing = cups
printcap name = cups

```

---

### Post by windependence on 2008-09-05
It's not necessary to use samba at all to share a printer. Just make sure cups is running and you can either put it on the network or attach it to a server and share it there.

Save yourself some headaches (assuming this is a private network), edit the Listen directives in the following file:
(Dapper: /etc/cups/cups.d/ports.conf; Edgy: /etc/cups/cupsd.conf)

```
#Listen localhost:631
Listen *:631
Listen /var/run/cups/cups.sock
```

Restart the cups daemon:

```
sudo /etc/init.d/cupsys restart
```


**On the Windows box:**

Start the Add Printer wizard 
Click Next 
Select A network printer, or a printer attached to another computer 
Select Connect to a printer on the Internet or on a home or office network 
Type [http://server_name:631/printers/printer_name](http://server_name:631/printers/printer_name) in the URL box, where server_name is the hostname or ip address for the ubuntu machine, and printer_name is... the printer name. Don't forget the port number! 
Click Next and run through the driver installation to complete 

Since root isn't enabled you will have to follow the steps here to use the cups web interface:

[https://help.ubuntu.com/community/PrintingCupsWebInterface](https://help.ubuntu.com/community/PrintingCupsWebInterface)

Should work just fine.

-Tim

---

