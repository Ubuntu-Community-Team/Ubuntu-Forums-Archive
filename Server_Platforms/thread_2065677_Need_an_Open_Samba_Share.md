---
title: "Need an Open Samba Share"
date: 2012-10-02
forum: Server Platforms
---

### Post by CarlosinFL on 2012-10-02
I'm trying to set up an open Samba share on Ubuntu Linux (No GUI) and for some reason I'm having problems with the 'open' part. I have a folder in Linux called /share that's owned by root:users and has 777 permissions:

```
drwxrwsrwx   2 root users  4096 Oct  2 12:19 share
```

Now my Samba configuration is as shown below:

```
fs3:/etc/samba# cat smb.conf
[global]
	workgroup = workgroup
	server string = Share
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	security = share

[share]
	path = /share
	comment = Test Share
	writable = yes
	browsable = yes
	read only = no

```

Now when I try to browse to the share from any Windows machine, I'm prompted with a login box that doesn't allow me to change the username field. It's like grayed out or not editable for some reason. I just have an option for a password but since I have no idea what credentials it's asking for, I don't know how to fix this. Users just want an 'un-secure' share to dump files and folders in. Seems fairly simple but I've not used Samba in some time and have no idea what I'm doing...

---

### Post by hasan.akgoz on 2012-10-02
samba user and password should be the same as the windows user and password.Can you check it username and password ?

Example confguration

[share]
comment = Share for Office
path = /office
valid users = user1 user2 ( user1 and user2 must be windows local account )
public = no
writable = yes
create mask = 0770

also if you have any problem Can you give me samba log file ? (/var/log/samba )

---

### Post by volkswagner on 2012-10-02
> **CarlosinFL said:**
> 
Now when I try to browse to the share from any Windows machine, I'm prompted with a login box that doesn't allow me to change the username field. It's like grayed out or not editable for some reason. I just have an option for a password but since I have no idea what credentials it's asking for, I don't know how to fix this. Users just want an 'un-secure' share to dump files and folders in. Seems fairly simple but I've not used Samba in some time and have no idea what I'm doing...


I think The user is grayed out because you have selected "security = share".  With this model, I believe you need credential requirements per share, which you have none.

To create a share without requiring a login, you will want to access via guest.

I would make the following changes.

```
security = user

[share]
	path = /share
	comment = Test Share
	writable = yes
	browsable = yes
	read only = no
        guest ok = yes
	create mask = 0775
        directory mask = 0775
 

```

This should allow any user to connect regardless if they have a samba account.  The create mask and directory mask force the permissions when files and folders are created.  When users create files and folders they will be set to group = nobody.

Obviously this give no control over user1 overwriting user2's files.

---

### Post by Morbius1 on 2012-10-02
**First**, you did not create a Public or guest accessible share. By default the one you created will require credentials. You can fix that by adding one line to your share definition:
> [share]
path = /share     
comment = Test Share     
writable = yes     
browsable = yes
 read only = no
[COLOR=Blue]**guest ok = yes**[/COLOR]**Second**, you don't need any username and password matching. In fact you don't need any usernames or passwords at all.

**Third**, I'll admit I don't remember exactly how share level security works ( I contend that no one living remembers how share level security works ) so it may work without this step.  I would make the following change to your [global] section to bring it back to the modern default:

Change this:
> security = shareTo this:
> security = user
map to guest = Bad User

****** When you are all don editing smb.conf restart samba:
```
sudo service smbd restart
```

---

