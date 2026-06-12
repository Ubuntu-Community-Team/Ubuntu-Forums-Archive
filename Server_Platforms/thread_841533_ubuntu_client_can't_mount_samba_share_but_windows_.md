---
title: "ubuntu client can't mount samba share but windows clients can"
date: 2008-06-26
forum: Server Platforms
---

### Post by stevepowell99 on 2008-06-26
hi forum members
I have a debian box which serves as a file server and the other windows clients in the network (via a router) can mount the shares on it. But my new ubuntu hardy installation on my laptop can't. I can browse the network using nautilus (but not with dolphin or konqueror) but can't mount the shares. So smb://promentedebian/promenteprojects works in nautilus but not anywhere else.
If I use the gui via places/connect to server I can make a bookmark which works in nautilus but not from applications, e.g. to save a file on the network.
I have tried for example 
```
sudo mount //promentedebian/pdhome /mnt/pp -o username=HP,password=xxx 
 
```
but I get 

```
mount error 111 = Connection refused
```.

other variants of mount and smbmount get the same result. 
this is obviously a real drag because I can't e.g use unison to sync my laptop with the network

any ideas?
thanks
Steve Powell

---

### Post by MJN on 2008-06-26
Check to see if if your Ubuntu client can see the share okay - try the following command (and post the output):

```
smbclient -L promentedebian -N
```It may also be worth forcing cifs or smbfs (rather than leaving it to self-detection) using the -t cifs (or smbfs) switch on your mount command.

Mathew

---

### Post by stevepowell99 on 2008-06-27
thanks mjn. already tried cifs and smbfs with same result. 
i did the smbclient command with following result: 

```
steve@steve-ubuntu:/etc$ smbclient -L promentedebian -N
Anonymous login successful
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.24]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (promentedebian server)
	to              Disk      
	usbdisk         Disk      
	pdhome          Disk      
	proMENTEprojects Disk      
	print$          Disk      Printer Drivers
Anonymous login successful
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.24]

	Server               Comment
	---------            -------
	PROMENTEDEBIAN       promentedebian server

	Workgroup            Master
	---------            -------
	MSHOME               PROMENTEDEBIAN
```

---

### Post by stevepowell99 on 2008-06-27
hi, I fixed it, it was really simple. I had entered the wrong ip address of the server in my hosts file. With the correct ip address instead of promentedebian, the server name, it works fine now. thanks!

---

### Post by MJN on 2008-06-27
...but your smbclient output worked okay..?

---

