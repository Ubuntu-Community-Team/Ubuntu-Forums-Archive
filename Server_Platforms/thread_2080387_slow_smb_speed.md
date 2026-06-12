---
title: "slow smb speed"
date: 2012-11-03
forum: Server Platforms
---

### Post by sbjaved on 2012-11-03
I'm running a 12.04 file server configured with samba in my home network. I'm getting 4MB/s file transfer speeds over wireless-n router (dlink-dir 655) from ubuntu clients. I've tried some socket optimizations in the smb.conf but nothing works.
Here is the output of testparm:

```
[global]
	workgroup = JAVED-HOME
	server string = Home-Server
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	socket options = TCP_NODELAY SO_RCVBUF=262144 SO_SNDBUF=262144 IPTOS_LOWDELAY SO_KEEPALIVE
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb
	aio read size = 64360
	aio write size = 64360
	aio write behind = true

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	guest ok = Yes
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[data]
	comment = Central Storage Area
	path = /data
	read only = No
	guest ok = Yes

[saad]
	comment = Saad's Personal Storage
	path = /home/saad
	valid users = saad
	read only = No

[TOSHIBA]
	path = /media/TOSHIBA
	force user = saad
	read only = No
	guest ok = Yes

```

My windows client seems to get slightly better speed (around 4.5-5MB/s even touches 6MB/s occasionally) which I obviously don't like :) Ubuntu should do better than Windows

---

### Post by Linuxisfast on 2012-11-04
In my experience smb speeds depend on the hardware used, if I am directly connected via LAN, speeds are quite high in the range of 25mbps+ but using wireless, it slows down to a measly 1.6mbps average.

---

### Post by sbjaved on 2012-11-04
The server is connected to the router via LAN cable. Also wireless-n in 40MHz band should support theoretical transfers of around 16MBps. The same server also runs ftp where I get speeds of 11MBps. I understand samba can't match ftp because it creates a full filesystem but around 8MBps should be doable. I'm no samba expert though.

---

### Post by Linuxisfast on 2012-11-04
> **sbjaved said:**
> The server is connected to the router via LAN cable. Also wireless-n in 40MHz band should support theoretical transfers of around 16MBps. The same server also runs ftp where I get speeds of 11MBps. I understand samba can't match ftp because it creates a full filesystem but around 8MBps should be doable. I'm no samba expert though.

Try updating router firmware to latest in case you haven't done and see if this issue gets better.

---

### Post by sbjaved on 2012-11-04
> **Linuxisfast said:**
> Try updating router firmware to latest in case you haven't done and see if this issue gets better.
Already have the latest firmware running.

---

### Post by Linuxisfast on 2012-11-04
> **sbjaved said:**
> Already have the latest firmware running.

Can you try with a ethernet cable and see if it improves.

---

### Post by sbjaved on 2012-11-04
Sure. I've run into a strange thing. I just set up my brothers laptop with ubuntu. I installed samba and shared his Public folder in his /home by right click -> Share this folder. I put in the correct workgroup in Samba. The computer is able to access the server but when I tried to access his Public folder from the server...it gives an error "Failed to mount: Unable to get share list from the server".

Here is the output of smbtree on brothers laptop:
```
JAVED-HOME
	\\HOME-SERVER    		Home-Server
		\\HOME-SERVER\ML-2160-Series 	Samsung ML-2160 Series
		\\HOME-SERVER\IPC$           	IPC Service (Home-Server)
		\\HOME-SERVER\TOSHIBA        	
		\\HOME-SERVER\saad           	Saad's Personal Storage
		\\HOME-SERVER\data           	Central Storage Area
		\\HOME-SERVER\dvd-rw         	Home-Server Asus DVD-RW
		\\HOME-SERVER\print$         	Printer Drivers
	\\DELL-XPS-L502X 		Saad's Laptop
		\\DELL-XPS-L502X\Public         	
		\\DELL-XPS-L502X\samsung-ml-2165-laserjet	Samsung ML-2165 Laserjet (hplj-pcl5e)
		\\DELL-XPS-L502X\IPC$           	IPC Service (Saad's Laptop)
		\\DELL-XPS-L502X\print$         	Printer Drivers

```

Here is the output of testparm:

```
[global]
	workgroup = JAVED-HOME
	server string = Saad's Laptop
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	socket options = TCP_NODELAY SO_RCVBUF=262144 SO_SNDBUF=262144 IPTOS_LOWDELAY SO_KEEPALIVE
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

```

---

### Post by sbjaved on 2012-11-04
nmblookup and smbclient from the server:

```
saad@Home-Server:~$ nmblookup -B 192.168.0.104 __SAMBA__
querying __SAMBA__ on 192.168.0.104
name_query failed to find name __SAMBA__
saad@Home-Server:~$ smbclient -L //192.168.0.104 -U saad
Enter saad's password: 
Connection to 192.168.0.104 failed (Error NT_STATUS_UNSUCCESSFUL)

```

---

### Post by Linuxisfast on 2012-11-04
> **sbjaved said:**
> Sure. I've run into a strange thing. I just set up my brothers laptop with ubuntu. I installed samba and shared his Public folder in his /home by right click -> Share this folder. I put in the correct workgroup in Samba. The computer is able to access the server but when I tried to access his Public folder from the server...it gives an error "Failed to mount: Unable to get share list from the server".

Here is the output of smbtree on brothers laptop:
```
JAVED-HOME
	\\HOME-SERVER    		Home-Server
		\\HOME-SERVER\ML-2160-Series 	Samsung ML-2160 Series
		\\HOME-SERVER\IPC$           	IPC Service (Home-Server)
		\\HOME-SERVER\TOSHIBA        	
		\\HOME-SERVER\saad           	Saad's Personal Storage
		\\HOME-SERVER\data           	Central Storage Area
		\\HOME-SERVER\dvd-rw         	Home-Server Asus DVD-RW
		\\HOME-SERVER\print$         	Printer Drivers
	\\DELL-XPS-L502X 		Saad's Laptop
		\\DELL-XPS-L502X\Public         	
		\\DELL-XPS-L502X\samsung-ml-2165-laserjet	Samsung ML-2165 Laserjet (hplj-pcl5e)
		\\DELL-XPS-L502X\IPC$           	IPC Service (Saad's Laptop)
		\\DELL-XPS-L502X\print$         	Printer Drivers

```

Here is the output of testparm:

```
[global]
	workgroup = JAVED-HOME
	server string = Saad's Laptop
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	socket options = TCP_NODELAY SO_RCVBUF=262144 SO_SNDBUF=262144 IPTOS_LOWDELAY SO_KEEPALIVE
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

```


Check if the firewall is turned on, I am sharing with three machines at my house, one desktop and two laptops plus two android phones and all work here, the desktop and one laptop is 12.04, the other one is 12.10

---

### Post by sbjaved on 2012-11-04
Yep it turned out to be the firewall. One "sudo ufw disable" later everything started working smoothly. Many, many thanks to you Linuxisfast! :D You are a saviour.

---

