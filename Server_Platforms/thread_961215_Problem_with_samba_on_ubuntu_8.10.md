---
title: "Problem with samba on ubuntu 8.10"
date: 2008-10-28
forum: Server Platforms
---

### Post by _tomcio on 2008-10-28
Hello!

I'm trying to set up samba server on my pc. Server will work in local secured wifi network. I want to share two folders with other users, who have windows xp. I also want to copy files between my laptop and desktop, that's why i decided to use samba.
```

here's configuration file:
[global]
netbiosname = goofy-desktop
server string = Samba %v na (%L)
workgroup = jebudu

valid users = goofy
security = user
encrypt passwords = true
unix password sync = yes
smb passwd file = /etc/samba/smbpasswd
passwd program = /usr/bin/passwd %u

[homes]
browsable = yes
writable = yes
```

this is output of 'smbtree':
```
WORKGROUP
JEBUDU
	\\GOOFY-DESKTOP  		Samba 3.2.3 w serwerze (goofy-desktop)
		\\GOOFY-DESKTOP\goofy          	Home directory of goofy
		\\GOOFY-DESKTOP\homes          	
		\\GOOFY-DESKTOP\IPC$           	IPC Service (Samba 3.2.3 w serwerze (goofy-desktop))
```

Now the problem. When I browse local network using explorer on windows and nautilus on ubuntu I don't see 'jebudu' working group. I don't have any idea, why it doesn't work properly.

---

### Post by underdog512 on 2009-01-14
I am having the same exact problem.  Does anyone know how to get this working?

---

### Post by Iowan on 2009-01-14
Somewhere inside [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To is information on making shares visible (has to do with Winbind and/or WINS).  As an aside... **valid users = goofy** in the [global] section means only that user will be able to use Samba... was that the intent?

---

### Post by albinootje on 2009-01-14
> **_tomcio said:**
> I'm trying to set up samba server on my pc. Server will work in local secured wifi network. I want to share two folders with other users, who have windows xp. 

Do you already have anything working in the setup ? 
Can those machines ping each other ? 
Are you using the same workgroup ?
Did you set up samba users on your Ubuntu box ?

Is your Samba setup working locally on your Ubuntu box ?
Please test that with the smbclient command.
For more info see here : 
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
--> Samba Client Manual Configuration

---

### Post by alex.burlacu on 2009-01-29
You have to pay some attention to the firewall settings as well.
Your config looks ok but you have to check if you have UDP ports 137 and 138
and TCP ports 139 and 44 open in your server.

---

