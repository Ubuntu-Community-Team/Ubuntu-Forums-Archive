---
title: "Simple Samba setup"
date: 2008-09-29
forum: Server Platforms
---

### Post by moonshinerat on 2008-09-29
Hi guys,

I've just built a home office server with Ubuntu Server 8.04.1, Samba and RAID1. My client machines are two XP systems and an Ubuntu Laptop. I have tried reading through the Samba setup howto's without too much success as my own circumstances differ from the standard installation and I'm unsure how to proceed.

Firstly, I have a huge partition (dev/md2) on my server which I want to use as a central "home" partition. It is mounted under /data. This means I want all three clients to store their normal data in this partition.

Secondly, I have been able to ping each of the clients from the server without a problem. Ubuntu just found the server in Remote Places and connects on it's own (but doesn't yet store it's info here). However, I don't know how to get the Windows machines to access the server.

There is no print sharing, I just need to use the server as a central file storage area. Please can someone help me setup up the rest of this system? Thanks all.

---

### Post by lykwydchykyn on 2008-09-29
Well if you know the IP of your server (and you should), just open start=>run and enter:
```

\\ip_of_my_server

```
See if that gets you to the server.  If you want to you can map a drive there.

Samba is pretty much samba on any distro.  IMHO the biggest gotcha for people is the fact that both Samba permissions and local user permissions apply, so you've got to set up both for the access you need (FWIW, this confuses people setting up shares on Windows as well, it's no different--both local file permissions and share permissions apply, and the most restrictive wins out).

---

### Post by cariboo on 2008-09-29
On your laptop in a terminal try:

```
smbclient -L <server> -U%
```

This will output something like this:

```
smbclient -L willy -U%
Domain=[APLUS] OS=[Unix] Server=[Samba 3.0.28a]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (Willy server (Samba, Ubuntu))
	win_updates     Disk      Project Dakota
	data            Disk      data storage
	images          Disk      iso images
	music           Disk      Music directory
	Movies          Disk      Tv and Movies
	print$          Disk      Printer Drivers
	HP-Laserjet     Printer   Laser Printer
Domain=[APLUS] OS=[Unix] Server=[Samba 3.0.28a]

	Server               Comment
	---------            -------
	INTREPID             intrepid server (Samba, Ubuntu)
	WILLY                Willy server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	APLUS                WILLY
```

This shows all the shares and printer that are available on my server. If you get an output similar to above then you should be able to connect to the server from your xp computers.

Jim

---

### Post by moonshinerat on 2008-10-01
Hi guys,

thanks for the answers. I can actually see what I think is the directories on Samba. However all I have at the moment is printers/faxes.

Folks keep saying that you need to setup every user on the samba system and that each has it's own directory. What I want is a universal directory for anyone who connects to my router. So, that's just one directory between 3 possible users so all of their information goes into the same place.

I think I've already worked out how to change the samba share directory in Windows to the default 'home' location so I just need to let my users save their data (in the same directory, not seperate user directories) on the samba server. Where do I go from here?

Please remember that I have Ubuntu Server and there is no gui, just command line.

Thank you again for the other answers.

---

### Post by moonshinerat on 2008-10-06
Hi guys.

Okay, I now have proper acces to the Samba server and I can add and remove files/folders etc in my own home directory on the server.

I have a directory called /data. Everytime I try to access this folder Samba asks for a username and password. I provide it with the only one that I have setup on this server and it won't access.

I have two machines, both XP. I can map to my own home directory on the Samaba server but I need to access /data with both XP machines. How do I do this now?

Thanks all.

---

### Post by Iowan on 2008-10-06
> **moonshinerat said:**
> Folks keep saying that you need to setup every user on the samba system and that each has it's own directory. What I want is a universal directory for anyone who connects to my router. So, that's just one directory between 3 possible users so all of their information goes into the same place.You can do either - or both.  Each user *should* be set up, and *can* have a private share - the sample **/etc/samba/smb.conf** has one such share.  But you can also build "common" shares. If security is no concern (it *should* be), you can set up **security=share** or use **force user=** and **force group=**.

BTW, have you seen these links?
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

---

### Post by bunnynuts on 2008-10-07
I agree with Iowan, it seems that what you want is the default for the sample smb.conf file. If you post your config file it might be a bit easier to offer some help. For security you have many options not the least of which is limiting access by IP if that is an option.

---

### Post by lykwydchykyn on 2008-10-07
You may need to set the password for the samba account -- by default it is NOT synchronized with your system account password.  On the server, execute:
```

smbpasswd -a myuser

```
And type in the password.  See if that will allow you to connect to /data.  Also check the file permissions on /data -- can your user read these files?

---

### Post by PhaseTwenty on 2008-10-07
I too am trying to work out a simple Samba configuration for a file server on my LAN, but I can't seem to get the configuration right.

What I'm trying to do is the following:
[LIST]
[*]Make available each UNIX account's home directory via Samba.
[*]Each directory has 0744 permissions set on it, new files and directories get 0744 as well.
[*]Anonymous access is disabled; each user must supply their UNIX credentials for access.
[*]If possible, members of the *administrators* group (right?  whoever the sudoers are) have write access on directories they don't own.
[/LIST]

Anything you could do would be appreciated.

---

### Post by erwall on 2008-10-07
> **moonshinerat said:**
> Hi guys.

Okay, I now have proper access to the Samba server and I can add and remove files/folders etc in my own home directory on the server.

I have a directory called /data. Everytime I try to access this folder Samba asks for a username and password. I provide it with the only one that I have setup on this server and it won't access.

I have two machines, both XP. I can map to my own home directory on the Samaba server but I need to access /data with both XP machines. How do I do this now?

Thanks all.

If you just want a wide open share, try setting the following in your smb.conf:

```
security = share
```

and

```
[data]
   comment = Data Share
   read only = no
   path = /data
   guest ok = yes
```

---

### Post by Iowan on 2008-10-07
> **PhaseTwenty said:**
> I too am trying to work out a simple Samba configuration for a file server on my LAN.A couple of links to check:
[http://https://help.ubuntu.com/community/SettingUpSamba]("http://https://help.ubuntu.com/community/SettingUpSamba")
[http://http://ubuntuforums.org/showthread.php?t=202605]("http://http://ubuntuforums.org/showthread.php?t=202605")
    * Make available each UNIX account's home directory via Samba. 
*(Sample in /etc/samba/smb.conf - valid users=%S)*
    * Each directory has 0744 permissions set on it, new files and directories get 0744 as well.[i]
(Create mask=0744 and directory mask=0744)[/i]
    * Anonymous access is disabled; each user must supply their UNIX credentials for access.
*(security=user and guestOK=no)*
    * If possible, members of the administrators group (right? whoever the sudoers are) have write access on directories they don't own.
*(write list=@administrators - you'll need to verify groupname)*

---

