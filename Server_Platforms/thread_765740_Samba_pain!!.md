---
title: "Samba pain!!"
date: 2008-04-24
forum: Server Platforms
---

### Post by upforthedownstroke on 2008-04-24
So I went through the Samba Fast Start guide on samba.org, and set up a file and print server according the the "Secure Office Server" section. Everything works just as the guide says it should until I attempt to log in with smbclient. this is what I get:

```
will@mothership:~$ sudo smbclient //MOTHERSHIP/student -Ustudent%*******
session setup failed: NT_STATUS_LOGON_FAILURE

```

here's my testparm. Help!
```

Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[public]"
Processing section "[printers]"
WARNING: The "printer admin" option is deprecated
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = MSHOME
        printcap name = cups
        disable spoolss = Yes
        show add printer wizard = No
        printing = cups
        print command = 
        lpq command = %p
        lprm command = 

[homes]
        comment = Home Directories
        valid users = @users
        read only = No
        browseable = No

[public]
        comment = Data
        path = "/media/MUSIC ETC"
        valid users = @users
        read only = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        printer admin = root, student
        create mask = 0600
        guest ok = Yes
        printable = Yes
        use client driver = Yes
        browseable = No

```

---

### Post by Iowan on 2008-04-24
I haven't gone through that guide (yet) - forgive me if I ask something the guide covered...
You did create a Samba user and password with **smbpasswd**?

---

### Post by upforthedownstroke on 2008-04-25
Yes, I've got my users and passwords set up in smbpasswd.

---

### Post by upforthedownstroke on 2008-05-01
Update:

Okay, so I got the CUPS aspect of my Samba setup working just fine. I was able to just type \\servername\printer in the windows network printer config screen and get it to connect just fine using the smbpasswd users I'd created. I don't have the fileserver system working quite yet, but it shouldn't be long.

---

### Post by HermanAB on 2008-05-01
Use smbclient to debug Samba.

$ man smbclient

Cheers,

H.

---

