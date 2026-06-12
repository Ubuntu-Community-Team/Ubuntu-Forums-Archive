---
title: "Where are samba passwords located in 10.10?"
date: 2011-04-10
forum: Server Platforms
---

### Post by roadrawts on 2011-04-10
Although my smb.conf file cites /etc/samba/smbpasswd as the password file, I see that it is not in some database file.  Since smb.conf doesn't seem to look anywhere else but /etc/samba/smbpasswd, how can I direct it to the new password scheme.  At least this is what I find when using SWAT to display the smb.conf file contents.

This seems to be preventing my windows client having access to shared printers, but yet, not shared files.  Strange????

---

### Post by falko on 2011-04-11
Have you thought about using the smbpasswd command (see ```
man smbpasswd
```) as an interface to your password file? By using this command, you don't have to know where the file is located.

---

### Post by roadrawts on 2011-04-12
man smbpasswd is instructions on the program, not the location of the file.  The issue is that in 10.10 the whole concept has changed to use some sort of database.  But in the smb.conf file according to SWAT, the password "file" should be located at /etc/samba/smbpasswd.  However, it doesn't exit there.  Consequently, I'm having trouble with authentication and access from Windows platform.    I guess I'm looking for tdbsam, but I'm not sure.

---

### Post by jordg on 2011-12-28
Asking people to rtfm is totally ignorant.
May I say for example 'man at' It says TIMESPEC but does not define what the hell TIMESPEC is or where to find it. The manuals are terse and lacking examples.  If you don't know then don't say rtfm. If you do then give a decent answer.

Anyway look in /var/lib/samba

Incidentally if I install a new OS on my system and want to configure samba again without asking my users to enter a new smbpasswd maybe I can 
> mv /var/lib/samba /var/lib/samba.fcs; cp -a /old/var/lib/samba /var/lib/ Seems to work for me.

---

### Post by redmk2 on 2011-12-28
> **jordg said:**
> Asking people to rtfm is totally ignorant.
Why would you say that?  Ignorance is not knowing what you are looking at.  The information is in there.  from the smbpasswd man pages...
```
Note that the password is stored in the secrets.tdb
```

The file is located at ```
/var/lib/samba/secrets.tdb
```

The file can be read using pdbedit.  The incantation to list the samba users is ```
sudo pdbedit -L
```

Of course, you can read all about it with ```
man pdbedit
```

---

