---
title: "smbpasswd password file is not updated"
date: 2014-08-16
forum: Server Platforms
---

### Post by hextra on 2014-08-16
I have Samba set up and working with all the shares open. I now decided to switch to a more secure set up that includes specific user rights.

I've installed libpam-smbpass and configured samba to be a domain controller. However, it seems that I am not able to add users. I get all the correct responses from smbpasswd as if everything is working fine but the new user is not added to the smbpasswd user repository.

Configuration:
>   security = user
  encrypt passwords = yes
  smb passwd file = /etc/samba/smbpasswd



> master@Luna:~$ grep test /etc/passwd
test123:x:1003:1004:Test 123,,,:/home/test123:/bin/bash
master@Luna:~$ sudo smbpasswd -a test123
New SMB password:
Retype new SMB password:
Added user test123.
master@Luna:~$ cat /etc/samba/smbpasswd
master@Luna:~$

Any idea whats going on?

---

### Post by bab1 on 2014-08-16
> **hextra said:**
> I have Samba set up and working with all the shares open. I now decided to switch to a more secure set up that includes specific user rights.

I've installed libpam-smbpass and configured samba to be a domain controller. However, it seems that I am not able to add users. I get all the correct responses from smbpasswd as if everything is working fine but the new user is not added to the smbpasswd user repository.

Configuration:




Any idea whats going on?
The samba user database is located at /var/lib/samba/passdb.tdb.  You can read it using the tool *pdbedit*.  To list all the Samba user you can use this incantation```
sudo pdbedit -L
```

You do not need to make Samba a domain controller to add Samba users (sudo smbpasswd -a).  The domain controller is for user security domains.  The smbpasswd command is to add Samba users to the local host's Samba user database.

---

### Post by hextra on 2014-08-16
Thank you BAB1.

For some reason all samba documentation point to the [COLOR=#000000]*smb passwd file. *[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo pdbedit -L [/FONT][/COLOR][COLOR=#000000][I]worked great.

How can Windows users authenticate as [/I][/COLOR]Samba users, if Samba &#8203;is not also a domain controller?[COLOR=#000000][I]

[/I][/COLOR]

---

### Post by bab1 on 2014-08-16
> **hextra said:**
> Thank you BAB1.

For some reason all samba documentation point to the smb passwd file.  [The tool] ** sudo pdbedit -L**  worked great.

The actual file name is as I said.  It is referred to as the smbpasswd file.  The tool *pdbedit* is used to manipulate the binary database.  
> 

How can Windows users authenticate as Samba users, if Samba &#8203;is not also a domain controller?


The Samba server (by that I mean the daemon *smbd*) compares the login and password provided by the client to ***authenticate*** the user (who are you) and allows the share directory to be mounted to the clients file system.  The underlaying file system permissions provide AUTHORIZATION (you can do that).

The smbpasswd file holds *only the authentication *for Samba.  There must ALSO  be a Linux user for the AUTHORIZATION.  You need to add that user to either the local user database (/etc/passwd) or some centralized user database (AD or LDAP or NIS).  For my standalone Samba servers (workgroup only) I just use the local host's /etc/passwd file via the tool *adduser* .  This is the Ubuntu/Debian preferred method for adding users/groups to the local host's user database.

---

### Post by hextra on 2014-08-19
> **bab1 said:**
> 
The Samba server (by that I mean the daemon *smbd*) compares the login and password provided by the client to ***authenticate*** the user (who are you) and allows the share directory to be mounted to the clients file system.  The underlaying file system permissions provide AUTHORIZATION (you can do that).

The smbpasswd file holds *only the authentication *for Samba.  There must ALSO  be a Linux user for the AUTHORIZATION.  You need to add that user to either the local user database (/etc/passwd) or some centralized user database (AD or LDAP or NIS).  For my standalone Samba servers (workgroup only) I just use the local host's /etc/passwd file via the tool *adduser* .  This is the Ubuntu/Debian preferred method for adding users/groups to the local host's user database.

This is how I started. Had a user both in Linux and added through smbpasswd, but every attempt to authenticate from Windows 8.1 failed. My assumption was that this occurs due to Windows sending the user as a domain user so authentication doesn't work.

---

### Post by bab1 on 2014-08-20
> **hextra said:**
> This is how I started. Had a user both in Linux and added through smbpasswd, but every attempt to authenticate from Windows 8.1 failed. My assumption was that this occurs due to Windows sending the user as a domain user so authentication doesn't work.

Window does send the logged in user name by default, but you can override that.  The Samba daemon (smbd) uses it's database to authenticate the user, for Samba user.  If you are using a stand alone server (workgroup) and you have setup on that server both a Linux user (/etc/passwd) and a Samba user (smbpasswd -a) and still can't authenticate the user then the client is at fault not the server.

My suggestion still stands -- g back to the default smb.conf file and **only add one share**.  Then have a user try and authenticate.  I don't use Windows 8.1 so I can't tell you exactly what to do to diagnose that problem.  I can tell you how to check to see if authentication works using an Ubuntu client.  From any Ubuntu client in the LAN (including the Samba server itself) you can test using this command```
smbtree -d3
```

Post that data back here.  PLEASE WRAP THE TEXT IN CODE BLOCKS ( [CODE][/BLOCK] ).  You can do that by clicking on the [SIZE=5]**#**[/SIZE] icon at the top of the advanced editor.

---

