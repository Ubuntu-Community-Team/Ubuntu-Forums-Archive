---
title: "Cannot see my server in My Network Places"
date: 2011-02-04
forum: Server Platforms
---

### Post by Stienz on 2011-02-04
I installed Ubuntu Server 10.10 today on an old laptop. I then used webmin to configure it and enabled windows networking, the laptop is in the same workgroup as another win7 laptop and a win xp desktop. However, I can't see the server in My network places. What am I doing wrong? 

Prolly a stupid question, but I am quite a linux noob.

---

### Post by CharlesA on 2011-02-04
Are you able to ping it by name or ip address?

---

### Post by Stienz on 2011-02-04
Yes, it responds to a ping.

---

### Post by CharlesA on 2011-02-04
Ok. Make sure that the smbd and nmbd services are running:

```
service smbd status
service nmbd status
```

---

### Post by Stienz on 2011-02-04
They aren't running, also, I cannot figure out by googling how to start them.

---

### Post by CharlesA on 2011-02-04
You can use this to start those services:

```
sudo service smbd start
sudo service nmbd start
```

---

### Post by kroon78 on 2011-02-04
Exactly what was said above me :)

---

### Post by Stienz on 2011-02-04
It's running now, still can't see the service under My Network Places, really appreciate all your posts :D

---

### Post by Morbius1 on 2011-02-04
Then it's time to go hardcore:
Please post the output of the following commands from the server:
```
testparm -s
```
```
smbtree
```

---

### Post by Stienz on 2011-02-04
**> testparm -s**
```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Public]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = STNZCLOUD
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	path = /home/public

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Public]

```

**> smbtree**
```
WORKGROUP
	\\STNZSERV       		Stnzserv server (Samba, Ubuntu)
		\\STNZSERV\IPC$           	IPC Service (Stnzserv server (Samba, Ubuntu))
		\\STNZSERV\Public         	
		\\STNZSERV\print$         	Printer Drivers
```

---

### Post by Morbius1 on 2011-02-04
Aside from one line it looks like the default smb.conf. One problem is the following line is in the wrong place:
> path = /home/publicCurrently it's in the [global] section. It needs to be in the [public] section:
> [Public]
[COLOR=Blue]path = /home/public[/COLOR]Once you move it restart samba:
```
sudo service smbd restart
```

---

### Post by Stienz on 2011-02-04
Hmm, I can see it in Win7 now, but still not in the Winxp, which is prolly something on the side of Winxp, anyone got an idea what that might be? 

When I try to copy something to the server I get Destionation Folder Acces Denied.

---

### Post by arrrghhh on 2011-02-04
> **Stienz said:**
> Hmm, I can see it in Win7 now, but still not in the Winxp, which is prolly something on the side of Winxp, anyone got an idea what that might be? 

When I try to copy something to the server I get Destionation Folder Acces Denied.

Please don't take offense to this comment but...

Did you configure samba at all, or did you just install it and expect it to work...?

---

### Post by Stienz on 2011-02-04
> **arrrghhh said:**
> Please don't take offense to this comment but...

Did you configure samba at all, or did you just install it and expect it to work...?

I don't take offensive to your comment, I configured samba, but not in a right way. I can use the share now in Win7, took me ages.  Thanks all for the helpful comments. 

Still can't see the whole server in Winxp, dunno what's wrong, gonna update the xp client now.

---

### Post by Morbius1 on 2011-02-04
> When I try to copy something to the server I get Destionation Folder Acces Denied.Your share looks like this:
> [Public]
[COLOR=Black]path = /home/public[/COLOR] This means two things:

* [1] The only remote users that can access that share have to provide authentication meaning:*

(a) You have to Create local users on the Samba server itself corresponding to those remote users.

(b) You must add those local users to the samba database, as in:
```
smbpasswd -a user-name
```*[2] Your share is defined as read only ( the default ). If you want to allow write ( i.e., copy to the share ) then you must modify the share definition to allow it:*
```
[Public]
path = /home/public
read only = no
```You must also make sure that the target and the path to the target have the corresponding linux permissions to allow someone to access the target and allow them to write. If you do an:
```
ls -al /home
```/home must have permissions of at least drwxr-xr-x
/home/Public must have permissions of drwxrwxrwx

As for Win7 can see it but not WinXP I would temporarily disable all Windows firewall just to see if it's getting in the way.

---

