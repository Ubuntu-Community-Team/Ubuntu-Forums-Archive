---
title: "Samba trouble - failed to retrive share list"
date: 2020-05-10
forum: Server Platforms
---

### Post by OiPenguin on 2020-05-10
I have set up two servers. One spare to experiment and test before implementing on my main server for my house. It's different hardware, but apart from that they are similar with Ubuntu server running, raid 1, the same folder structure etc. 

I've tried to replicate what I did with the spare one (*.1.11) on the main server (*.1.12), however I'm able access the spare server, but not the main server through nautilus. The shares name is M and not listed below for either servers, however it is accessible on .1.11 but not on .1.12. From what I can tell fstab are similar so I wonder where I've done wrong. I've followed this guide: [https://linuxize.com/post/how-to-install-and-configure-samba-on-ubuntu-18-04/](https://linuxize.com/post/how-to-install-and-configure-samba-on-ubuntu-18-04/)

In Nautilus the servers are visible, but only server *spare* is accessible. *spare* has *(file sharing)* trailing in Nautilus, but server does not. They ar listed like this:
*Server spare (file sharing)*
*Windows network*
*Server*
*Server spare (file sharing)*

Any help to trouble shoot this would be greatly appreciated.

```
user@laptop:~/$ smbclient -L 192.168.1.11
Enter WORKGROUP\users's password: 

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	users           Disk      
	IPC$            IPC       IPC Service (e12b server (Samba, Ubuntu))
SMB1 disabled -- no workgroup available

```

```
user@laptop:~/$ smbclient -L 192.168.1.12
Enter WORKGROUP\users's password: 

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	users           Disk      
	IPC$            IPC       IPC Service (e12b-reserve server (Samba, Ubuntu))
SMB1 disabled -- no workgroup available
```

---

### Post by Morbius1 on 2020-05-10
That HowTo is unnecessarily complicated for a home server.

In any event there is not enough information to answer your question:

** Are you using Ubuntu Server or Ubuntu Desktop?

** What versions of Ubuntu are you using 18, 19, 20?

** How is samba configured on the server you cannot access?
```
testparm -s
```

If you want a guess without knowing facts I would look at this symptom:
> In Nautilus the servers are visible, but only server *spare* is accessible. *spare* has *(file sharing)* trailing in Nautilus, but server does not.
It sounds like server "server" either does not have avahi installed:
```
sudo apt install avahi-daemon
```
Or it is not running:
```
sudo service avahi-daemon status
```
If it's not running start it:
```
sudo service avahi-daemon restart
```

---

### Post by OiPenguin on 2020-05-10
Both machines use ubuntu server, 18.04 and 20.04 respectively

```

lars@e12b-reserve:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.4 LTS
Release:	18.04
Codename:	bionic

```

The inaccessible one:
```
lars@e12b:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04 LTS
Release:	20.04
Codename:	focal

```

```

lars@e12b:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
	log file = /var/log/samba/log.%m
	logging = file
	map to guest = Bad User
	max log size = 1000
	obey pam restrictions = Yes
	pam password change = Yes
	panic action = /usr/share/samba/panic-action %d
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	passwd program = /usr/bin/passwd %u
	server role = standalone server
	server string = %h server (Samba, Ubuntu)
	unix password sync = Yes
	usershare allow guests = Yes
	idmap config * : backend = tdb


[printers]
	browseable = No
	comment = All Printers
	create mask = 0700
	path = /var/spool/samba
	printable = Yes


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


[users]
	force create mode = 0660
	force directory mode = 02770
	path = /home/m
	read only = No
	valid users = @sambashare @sadmin @lars @ingrid


[ingrid]
	browseable = No
	force create mode = 0660
	force directory mode = 02770
	path = /home/ingrid
	read only = No
	valid users = ingrid @sadmin


[lars]
	browseable = No
	force create mode = 0660
	force directory mode = 02770
	path = /home/lars
	read only = No
	valid users = lars @sadmin


```

> It sounds like server "server" either does not have avahi installed:
You were right. I've now installed Avahi-daemon. I've also restarted these services:
```

lars@e12b:~$ sudo service avahi-daemon restart
lars@e12b:~$ sudo systemctl restart smbd
lars@e12b:~$ sudo systemctl restart nmbd

```

The server is still not accessible: *"Failed to retrive share list from server: invalid argument"*
however (**file sharing**) is now displayed after the server name so I get this list in Nautilus:

Server spare (file sharing)
Server (file sharing)
Windows network
Server (file sharing)
Server spare (file sharing)

---

### Post by Morbius1 on 2020-05-10
> *"Failed to retrive share list from server: invalid argument"*
The invalid argument it is refering to is SMB1 ( what Samba calls NT1 ). It's because of a bug in a gvfs component ( gvfsd-smb-browse ) on the client system that forces access to servers using SMB1 but the version of the samba server in 20.04 turns it off.

You have three choices depending on how you feel about SMB1:

[B][1] You could re-enable SMB1 on the server:

[/B]Edit /etc/samba/smb.conf and under the workgroup = WORKGROUP line add this one:

  ```
server min protocol = NT1 
```  Then restart smbd:```

sudo service smbd restart 
```

**[2] Or, You can leave smb.conf as it is and make the client access the share the way the Mac did in your HowTo.**

By accessing the server AND the share explicitly with a [highlight]smb://e12b.local/users[/highlight] in the Location bar in Nautilus or Connect to Server.

This will bypass gvfsd-smb-browse and the client will access the server using SMB3.

**[3] Or with a cifs mount which by default will access the samba server using SMB3.**

CIFS does not reference smb.conf or gvfs but instead uses the Linux kernel where things are more ... um ... coherent.

---

### Post by OiPenguin on 2020-05-10
> **Morbius1 said:**
> The invalid argument it is refering to is SMB1 ( what Samba calls NT1 ). It's because of a bug in a gvfs component ( gvfsd-smb-browse ) on the client system that forces access to servers using SMB1 but the version of the samba server in 20.04 turns it off.

You have three choices depending on how you feel about SMB1:

[B][1] You could re-enable SMB1 on the server:

[/B]Edit /etc/samba/smb.conf and under the workgroup = WORKGROUP line add this one:

  ```
server min protocol = NT1 
```  Then restart smbd:```

sudo service smbd restart 
```


Excellent. I have no knowledge about SMB1, but have read about a bug related to this. Solution 1 appears to do the trick. This is in my opinion the far easiest solution since we won't have to do anything out of the ordinary on the client side in the future. Thanks a lot!

---

