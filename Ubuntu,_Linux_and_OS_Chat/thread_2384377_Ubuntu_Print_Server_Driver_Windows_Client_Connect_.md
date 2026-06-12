---
title: "Ubuntu Print Server Driver Windows Client Connect unable"
date: 2018-02-06
forum: Ubuntu, Linux and OS Chat
---

### Post by efeliz on 2018-02-06
I would like to ask about an issue I've been facing:
I had a windows print server, while having less than a hundred printers  it was working as expected, but now I have more than two hundred  printers and the spool service stops on the *Windows Server*. 
  So I've decided to install an Ubuntu server and configure all  printers there (CUPS), the operation was successful, but while trying to  connect windows clients, I have noticed  that it's required to install  the selected printer driver manually, so, a limited AD users account  can't connect to any printer in my Ubuntu CUPS server, I'm interested in  making this Ubuntu print server windows like on auto-installing  printers drivers on windows client  from the source Ubuntu print server.


Actual smb.conf 

[Drivers]
    comment = Drivers Printer
    path = /home/printserver/Drivers
    read only = yes
    guest ok = yes

[printers]
    comment = All Printers
    browseable = yes
    path = /var/spool/samba
    printable = yes
    guest ok = yes
    read only = yes
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    public = yes
    browseable = yes
    comment = Printer Drivers
    path = /var/lib/samba/printers
    #path = /usr/share/cups/drivers
[prnproc$]
    comment = Printer Drivers
    path = /home/printserver/prtprocs
    browseable = yes
    read only = yes
    guest ok = yes

# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

---

### Post by TheFu on 2018-02-06
I suppose you've already found these?
* [https://wiki.samba.org/index.php/Setting_up_Automatic_Printer_Driver_Downloads_for_Windows_Clients](https://wiki.samba.org/index.php/Setting_up_Automatic_Printer_Driver_Downloads_for_Windows_Clients)
* [https://wiki.samba.org/index.php/Setting_up_Samba_as_a_Print_Server](https://wiki.samba.org/index.php/Setting_up_Samba_as_a_Print_Server)

---

### Post by efeliz on 2018-02-08
Yes, i'd tried those recommendations, and didn't work, thanks for replying.

---

