---
title: "other comps can't access samba shares"
date: 2010-04-25
forum: Security
---

### Post by Roclemir on 2010-04-25
it's driving me nuts. Done a few things now, including this last: 
[http://www.debuntu.org/guest-file-sharing-with-samba](http://www.debuntu.org/guest-file-sharing-with-samba)
and that didn't work. All the other comps in the house are windows 7, and I want this box to be my file server, with two 1 TB HDD plugged into it via USB, but I can't get the damn samba to allow access to everyone. Here's the path in the config file:

[data]
    comment = Test sharing
    path = /media/Shared
        browseable = yes
        read only = yes
        guest ok = yes

I don't know if it matters, but when I do testparm, i get:

Unknown parameter encountered: "SO_RCVBUF"
Ignoring unknown parameter "SO_RCVBUF"

Not sure what it means.

---

### Post by cariboo on 2010-04-26
The error your getting, shouldn't have anything to do with file sharing, to be on the safe side just comment the lines out in /etc/samba/smb.conf.

Open a terminal and type:

```
smbtree
```

do your shares show up in the output?

The output should look similar to this:

```
smbtree
Enter my password: 
APLUS
	\\WILLY          		willy server (Samba, Ubuntu)
		\\WILLY\print$         	Printer Drivers
		\\WILLY\Movies         	Movies & TV Shows
		\\WILLY\Music          	Music
		\\WILLY\Documents      	Documents
		\\WILLY\Stuff          	Everything Else
		\\WILLY\Iso            	Mounted iso's
		\\WILLY\Images         	iso images
		\\WILLY\IPC$           	IPC Service (willy server (Samba, Ubuntu))
	\\RISKY          		XP Computer
		\\RISKY\C$             	Default share
		\\RISKY\ADMIN$         	Remote Admin
		\\RISKY\EPSONSty       	EPSON Stylus Photo R340 Series
		\\RISKY\All Users      	
		\\RISKY\SharedDocs     	
		\\RISKY\print$         	Printer Drivers
		\\RISKY\IPC$           	Remote IPC
```

willy is my server, risky is a computer running XP, the computer I'm using at the moment isn't set up to do any sharing. I connect to the server using nfs on this system.

---

### Post by Roclemir on 2010-04-26
ryan@FileServer:~$ smbtree
Unknown parameter encountered: "SO_RCVBUF"
Ignoring unknown parameter "SO_RCVBUF"
Enter ryan's password: 
Server requested plaintext password but 'client plaintext auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
Server requested plaintext password but 'client plaintext auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
ryan@FileServer:~$ ^C
ryan@FileServer:~$

---

### Post by Roclemir on 2010-04-26
and what does the above mean exactly?

---

### Post by cariboo on 2010-04-26
Did you create a samba password? You can do so by entering the following:

```
sudo smpasswd -L -a <user>
```

to enable the user:

```
sudo smbpasswd -L -e <user>
```

---

### Post by Roclemir on 2010-04-26
ryan@FileServer:~$ sudo smpasswd -L -a Ryan
sudo: smpasswd: command not found
ryan@FileServer:~$ sudo smpasswd -L -e Ryan
sudo: smpasswd: command not found
ryan@FileServer:~$ 


Is this suppose to be creating a new user or modifying an existing one?

---

### Post by CharlesA on 2010-04-26
It should be this to add the user:

```
smbpasswd -L -a ryan
```

This to enabled the user:

```
smbpasswd -L -e ryan
```

After that is done, try running testparm.

---

