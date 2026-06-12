---
title: "Print server addition"
date: 2010-02-26
forum: Server Platforms
---

### Post by vader95 on 2010-02-26
Hi,

I have a samba file server already setup and running.  I would like to add printing capabilities onto the server.  Does anyone know how to or a tutorial i could follow to allow this. I Google searched it and had a hard time finding one. I am using 9.10. 


Thanks,
vader95

---

### Post by johnson.d on 2010-03-05
In ubuntu Samba shares all the printers by default. The Ubuntu machine which has Samba running can connect between the Samba client and the printer.You can directly print from the client using Samba.

Samba can be used for printing using the following steps:

1) Configuration on Ubuntu side:

i) Edit the /etc/samba/smb.conf file and see if these lines are uncommented,add these lines if not present

[ printers]

comment = All Printers
path = /var/spool/samba
browseable = no
printable = yes

iii) restart the samba service using the command "/etc/init.d/samba restart"

If using a windows client:

i) Start menu-> Printers and faxes -> Add a printer
ii) A window will open click next
iii) Select "A network printer, or a printer attached to another computer" and click next
iv) Select "Connect to this printer (or to browse for a printer, select this option and click next)" 
Enter \\< ip-address >\<printer name as in ubuntu> and click next
v) It will connect to the printer and may say that the driver is not installed (if driver is present in Windows xp it will proceed without driver installation)
vi) Install the drivers
vii) It will prompt "Do you want to this printer as the default printer?". Select your choice an click next
viii) Click finish

If using a Ubuntu Client:

1) Go to Gnome menu-> System-> Administration-> Printing.
2) A window will open, Click new.
3) Another Window will open. At devices, drop down Network printer, Click Windows Printer via Samba.
4) At the right hand side, There will be a box with 'smb://'. Here enter the ip-address and the printer name as follows:
smb://<ip-address>/<shared-name of the printer>
5) Choose the driver and finish the installation.
6) Now try printing from the Ubuntu System.

If you want to setup print server, you can use CUPS. You can access the CUPS configuration page from a browser using the URL [http://localhost:631](http://localhost:631). In this page you can find the documentation as well.

---

### Post by vader95 on 2010-03-05
ok, thank you.

i just need to finish getting my printer installed now.

Thanks,
vader95

---

