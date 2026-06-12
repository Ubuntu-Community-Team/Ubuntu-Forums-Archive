---
title: "Problems Adding New User in Samba"
date: 2007-08-22
forum: Server Platforms
---

### Post by i.wanna.corndog on 2007-08-22
Hey everybody,

I am working on setting up a file server under Ubuntu Server (Feisty). I have installed Samba and gotten all of my shares working and everything.

I am trying to add a new user to Samba, but I'm having some difficulty.

My user account (let's call it user1) works fine for logging in from Windows at this point in time.

Here's what I've done thus far:

```
sudo adduser user2
Adding user `user2' ...
Adding new group `user2' (1001) ...
Adding new user `user2' (1001) with group `user2' ...
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
Changing the user information for derektrout
Enter the new value, or press ENTER for the default
        Full Name []: user2
        Room Number []:
        Work Phone []:
        Home Phone []:
        Other []:
Is the information correct? [y/N] y
sudo smbpasswd -a user2
New SMB password:
Retype new SMB password:
Added user user2.
```

And just for good measure:
```
sudo smbpasswd -e user2
```

Here's my smb.conf file:
```
# Samba config file created using SWAT
# from 192.168.1.7 (192.168.1.7)
# Date: 2007/08/22 14:57:46

[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spa$
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[User Backup]
        path = share/backup
        valid users = user1, user2
```

I try to access the "User Backup" folder with user2, but I get this error message: (See attachment). (As a side note, this exact message comes up when i just enter random stuff for username and password, so I believe Samba isn't recognizing user2 as a valid user.)

I have no trouble accessing the folder with user1.

Also, I did restart both smbd and nmbd throught SWAT.

---

### Post by i.wanna.corndog on 2007-08-22
Well...all that work making a nice post and I figured out the problem. :) It would appear that Windows had cached the credentials for user1 and thus wouldn't let me log in as user2. I figured this out by using another machine.

On a side note: is there any way to clear the cached credentials in Windows so that I can test multiple Samba users?

---

### Post by James79 on 2007-08-22
You can get to your stored credentials by:

Start>Run>control userpasswords2>Advanced>Manage Passwords

---

