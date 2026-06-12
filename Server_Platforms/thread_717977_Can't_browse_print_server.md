---
title: "Can't browse print server"
date: 2008-03-07
forum: Server Platforms
---

### Post by protellect on 2008-03-07
Howdy.

I'm trying to set up a print server for my small business, and have had some success with it. However some change I made caused it so that I can't browse it.

I've had pretty poor luck going through the smb.conf man pages..... maybe I'm not looking in the right place, dunno. 

I'd just like to get the network browse working. I'd like to then be able to let any computer on our internal network print to it without bothering with any type of authentication.

 Sadly, I'm not very good at this yet. But I'm trying. If anyone can tell me what the error message means, that would be great.. Google hasn't turned up anything that has fixed it yet. 

Just to clarify, remote SSH, Cups web admin, SWAT web admin, apache/http all work. I was sort of curious if it was a port blocked thing, but I'm not sure. 

This is on Dapper 6.06LTS, if it makes a difference.

```
@hermes:/etc/samba$ testparm smb.conf 

Load smb config files from smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

/etc/samba$ testparm smb.conf 
[global]
        workgroup = workgroup
        server string = Ubuntu Print Server
        security = SHARE
        obey pam restrictions = Yes
        passdb backend = tdbsam
        guest account = ftp
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        log file = /var/log/samba/log.%m
        max log size = 1000
        printcap name = cups
        panic action = /usr/share/samba/panic-action %d
        invalid users = root
        printing = cups
        print command = 
        lpq command = %p
        lprm command = 

[printers]
        comment = All Printers
        path = /var/spool/samba
        guest ok = Yes
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
```

---

### Post by SavageHcky7 on 2008-03-08
I would try setting "browseable=yes".  Not sure if that will work for printers or not.

---

### Post by pogztimz on 2008-03-10
> **SavageHcky7 said:**
> I would try setting "browseable=yes".  Not sure if that will work for printers or not.

i am having a similar problem. though i tried to follow ur suggestion but to no avail. i still can't browse printers that are shared by other computers...

---

