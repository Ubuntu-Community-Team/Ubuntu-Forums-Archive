---
title: "Webserver and fileserver?"
date: 2008-06-11
forum: Security
---

### Post by borahshadow on 2008-06-11
Hello,
I have an older computer currently running ubuntu 6.06 server RAID'ed and samba. It is just currently just local with no ports forwarded to it. I have not been overly concerned about security because it is not accessible from the internet. Don't get me wrong I have not disregarded security I have done the updates and etc.
I have a website I have been developing and now am looking to host it. I would ideally host it somewhere else but that costs money. I realized I have a server running 24/7 but what are the security risks? Could somebody get into my files that are on my samba drive and not in my webserver directory? I am actually just the server admin but the actual owner of the server is worried about security issues.

---

### Post by cdenley on 2008-06-11
A samba server would be more secure if it weren't also running as a public web server, but I wouldn't be too concerned if it were configured properly. Since it sounds like you're using a router, it shouldn't allow any net access to samba if you only forward port 80. However, just in case, you should add a line like this to the global section of your smb.conf file.
```

hosts allow = 192.168.0.0/255.255.255.0

```

---

### Post by borahshadow on 2008-06-11
wow thanks for the fast reply.
Will that allow any computer on the LAN to still access samba? How great are the risks of apache (actually LAMP) somehow allowing someone file system access or some way to just corrupt data on the file system?

---

### Post by cdenley on 2008-06-11
> **borahshadow said:**
> wow thanks for the fast reply.
Will that allow any computer on the LAN to still access samba? How great are the risks of apache (actually LAMP) somehow allowing someone file system access or some way to just corrupt data on the file system?

Yes, just allow the correct address for your network.

Running a web server isn't really risky if you set it up right. However, if the site you developed uses server-side scripting, be careful your code can't be exploited. As long as you install security updates as they are released, apache should be safe. There is always a possibility someone finds a vulnerability before it is fixed, though. In that unlikely scenario, they would probably still need to penetrate another layer of security to corrupt your filesystem, but it's not impossible.

If you want to protect certain files that aren't web-accessible, make sure the user www-data doesn't have read or write permission. Don't allow any web-accessible directory/files to be written to by www-data. Restrict file permissions on your samba shares as much as you can.

---

### Post by borahshadow on 2008-06-11
> **cdenley said:**
> Yes, just allow the correct address for your network
I don't quite understand. The computers on my network are all 192.168.0.* so shouldn't there be an asterisk in the line you gave me?

For the samba do I need to make a separate user or is the user made during during the install good enough? It seems like making another user for samba is just another user that could be hacked. Samba is the only thing that needs to access those files (besides me logged in through ssh if command line access is necessary) what permissions do I need? 750, 755, other?

---

### Post by cdenley on 2008-06-11
> **borahshadow said:**
> I don't quite understand. The computers on my network are all 192.168.0.* so shouldn't there be an asterisk in the line you gave me?

For the samba do I need to make a separate user or is the user made during during the install good enough? It seems like making another user for samba is just another user that could be hacked. Samba is the only thing that needs to access those files (besides me logged in through ssh if command line access is necessary) what permissions do I need? 750, 755, other?
If your IP's are 192.168.0.*, then the line I gave you is correct. That's what the netmask of 255.255.255.0 is for.

Every samba user has to have a local unix account to grant filesystem permissions. If you want to prevent that account from getting hacked, set it's shell to be /bin/false and/or disable it
```

sudo usermod -s /bin/false smbuser
sudo passwd -l smbuser

```
Replace "smbuser" in that command with whatever users you created to login to samba. If a samba user called smbuser is the only one who needs access to a directory, and needs write permissions
```

sudo chown -R smbuser /path/to/dir
sudo chmod -R 700 /path/to/dir

```
Then you would have to edit your smb.conf file if you want to change permissions on new file or directories created using samba.
```

create mask = 0600
directory mask = 0700

```

---

### Post by borahshadow on 2008-06-11
Ok thanks I forgot to mention one thing. My samba setup is pretty simple. everybody uses one user so I can just have that user be my account right.


EDIT:
Here is my current smb.conf any thing I should change except maybe the create masks. if I chmod everything in My path to 700 can root access it? I will be able to access it always right? 
```
[global]
	netbios name = SERVER-HOME
	load printers = yes
	name resolve order = hosts wins bcast
	server string = 
	announce version = 5.0
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	workgroup = WORKGROUP
	syslog only = yes
	username map = /etc/samba/smbusers
	null passwords = true
	printcap name = CUPS
	syslog = 1
	security = share
	passdb backend = tdbsam
	wins support = no
        unix extensions = no
    ; General server settings

[shared]
	writeable = yes
	path = My Path
	force group = My user
	force user = My user
	create mask = 0644
	public = yes
	directory mask = 0755
	browseable = yes
	guest ok = yes
```

---

### Post by cdenley on 2008-06-11
> **borahshadow said:**
> Ok thanks I forgot to mention one thing. My samba setup is pretty simple. everybody uses one user so I can just have that user be my account right.

Yeah, except if only one user is used, I would change the permissions.
```

[shared]
	writeable = yes
	path = /data/shared
	force group = myuser
	force user = myuser
	**create mask = 0600**
	public = yes
	**directory mask = 0700**
	browseable = yes
	guest ok = yes

```
```

sudo chown -R myuser /data/shared
sudo chmod -R 700 /data/shared

```
and add that "hosts allow" line.

---

### Post by borahshadow on 2008-06-11
K thanks

---

