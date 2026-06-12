---
title: "Samba, cups and printerdrivers for Windows"
date: 2013-12-04
forum: Server Platforms
---

### Post by huehnerhose on 2013-12-04
Hi!

I'm pretty new to this forum, but I'm really desperated. My goal is to deploy printers to Windows Clients inside a windows domain, using a GPO. For various reasons I want to use cups as print server. The easiest way I see to deploy printers using a GPO is to deploy shared printers - here samba comes into play. 

At the moment I have a perfectly working cups, talking to all my printers, a samba sharing the printers perfectly - as long as I install the printer driver manually. All I now need is to deploy the printer drivers with samba. 

I read various tutorials on that subject and the most convenient way is to use the Windows-Printer-Wizard-Thing. Here my troouble starts. Everytime I add a driver nothing happens. The button for "Additional Drivers" is grey, also the dropdown menu for selecting the driver. I think my samba user doesn't have the rights to administrate the printers. All I read on this subject says "grant SePrintOperatorPrivilege" to that user by using net rpc. But my samba hasn't join the domain and on domain level I'm no admin - so I can't grant these privileges. 

Is there anyway to get theses privileges outside a domain? How can I add my user to the BUILTIN\Administrators (if this even helps)? Or do you have any other ideas how I get this problem solved?

Thanks!
huehnerhose

> [global]
   workgroup = PARETO
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   security = user

   printing = cups
   printcap name = cups

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
admin users = @lpadmin, user1, user2

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
   write list = @lpadmin, root
admin users = @lpadmin, user1, user2

---

### Post by volkswagner on 2013-12-04
I recall having similar trouble.  I don't have the best notes, but I may add some help.

I used this info [http://wiki.samba.org/index.php/Samba_as_a_print_server](http://wiki.samba.org/index.php/Samba_as_a_print_server)

Here are my notes... indicate needing to use Linux to set the drivers with the following 'rpcclient' command 
```
****** Jun 8 2013 ***
Seemed to still have issues with adding drivers for SAMBA printers:

Had to set driver from linux side as it would fail on windows.

#Find the driver name
sudo rpcclient localhost -U eric -c 'enumdrivers'

#the above returns
[Windows NT x86]
Printer Driver Info 1:
	Driver Name: [Brother HL-2240D series]


#set the driver
rpcclient localhost -U eric -c 'setdriver "laser" "Brother HL-2240D series"'

## following this how to for samba print server may be better with the above as well.
	http://wiki.samba.org/index.php/Samba_as_a_print_server

### simple way to reload samba after config file changes!
sudo smbcontrol all reload-config


******* although Windows 7 complains that adding the driver has failed, this does not
seem to be true.  After adding the drivers via Windows GUI, I get failed message, yet the driver is in fact added!
```

---

### Post by huehnerhose on 2013-12-05
Thanks for that answer and input!

I finally figured it out... 

My problem was a problem with user rights. That part about adding the smb-user to administrator group was everything I had to figure out. In the end it was only that little line:
```
[global]
admin users = root, @adm, user1
```
After adding this to the smb.conf I was able to grant the user that SePrintOperatorPrivilege via:
```
net rpc rights grant user1 SePrintOperatorPrivilege -U user1
```
Now with authenticate with that user in Windows i was able to add drivers via the Windows-Printer-Wizard. After that I ran into the same problem as volkswagner. Via the windows dialog I wasn't able to associate the driver with the printer. This is where your two commands help.

```
rpcclient localhost -U user1 -c 'enumdrivers'
```
from that listing you have to copy the exact name between the [] and associate the printer with the driver. The printer names can be listed via:

```
net rpc printer
```

```
rpcclient localhost -U user1 -c 'setdriver "printername" "DriverName"'
```

---

