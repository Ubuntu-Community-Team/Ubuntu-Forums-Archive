---
title: "Ubuntu Desktop access to Ubuntu Server"
date: 2009-01-18
forum: Server Platforms
---

### Post by adlabens on 2009-01-18
SETUP:

[INDENT]I've got a box running nothing but Ubuntu Server 8.10 (Intrepid Ibex), including Samba 3.2.3. It works fine. I've got 2 more boxes running nothing but WinXP Pro, and they have access to the server. I just built my daughter a box with Ubuntu 8.10 Desktop. ALL the boxes have access to the Internet. The XP boxes have access to the server, and to each other. It is a Windows Worgroup, not a domain. I have two logins on the new Ibex box, one for my daughter, who does not have any UID or PW on the Linux server or the Samba server (both in the same box, Samba running as part of Linux on the box). But, my login is as an admin on both boxes (& I can root, also). My server is running headless, and I'm using only the CLI. The data drive on the server is in ext3 format.[/INDENT]

DESIRED RESULT:

[INDENT]I would like to get the Ubuntu Desktop box to have access to the server, too, when I login as me, but not my daughter. Currently neither of us can see the server. I just want my login to be able to see it. [/INDENT]

SUSPECTED ISSUE:

[INDENT]I believe that I need to share the folder not only in Samba, but also in NFS, but I'm not sure. I'm not even sure if it IS shared yet in NFS.[/INDENT] 

I would have posted this in a Newbie forum, or in the Desktop forum, but I suspect the issue is with the Server setup instead of the Desktop. I think that if the Server is setup correctly, I should be able to see the folder in the File Browser (on the Ubuntu Desktop box), but it's not there, and it's not in the "Network places" although "Windows Network" is, and the RCH-WORKGROUP (workgroup) is. However, there is nothing in the workgroup. I have not shared anything on the WinXP boxes, so I wouldn't expect to see anything there.

Any suggestions will be GREATLY appreciated!!!

Thanks,
David

---

### Post by cmnorton on 2009-01-18
When you say access, what do you mean? From your post, it seems like you want mounted share access. At first, I thought you wanted X access, but as you know by default you would have to install Gnome or KDE on the server.

I'm not sure why you have to share the SAMBA share by NFS as well? I don't think you have to. I suggest playing around with smbclient at the command line of your Ubuntu desktop system to see what's needed to log in. Offhand, it sounds like you need to tweak your SAMBA parameters, or, do you have a firewall running on the Ubuntu server system?

---

### Post by cariboo on 2009-01-18
You should need anything extra to connect from an Ubuntu Desktop to a server running Samba. I suggest typing in a terminal:

```
smbclient -L <servername> -U%
```

This should output something like this:

```
smbclient -L willy -U%
Domain=[APLUS] OS=[Unix] Server=[Samba 3.2.3]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (willy server (Samba, Ubuntu))
	images          Disk      iso images
	updates         Disk      Project Dakota
	data            Disk      Data directory
	music           Disk      Music library
	movies          Disk      TV Shows and Movies
	print$          Disk      Printer Drivers
Domain=[APLUS] OS=[Unix] Server=[Samba 3.2.3]

	Server               Comment
	---------            -------
	RISKY                Windows computer
	WILLY                willy server (Samba, Ubuntu)
	WINMCLEESE           

	Workgroup            Master
	---------            -------
	APLUS                WILLY
```

Make sure that all of the systems are in the same workgroup.

You can change the workgorup name on the Ubuntu Desktop by pressing Alt-F2 and typing:

```
gksu gconf-editor
```

Once you have the editor open go to system-->smb and add the workgroup.

Jim

---

### Post by adlabens on 2009-01-19
Ok, no firewall is setup.  This is our home network, and it's still under development, so it's wide open.  As soon as I've got everything working, I'll start locking it down.  But for now, the firewall is turned off.

By "access" I mean that I want to be able to use the Desktop Ubuntu box to access shared files & folders on the Ubuntu Server box.  The server itself is never to be used for anything other than admin tasks such as setup, maintaining users, and locking it down to be a hardened server (eventually, but not till the entire network is working).

As for NFS versus Samba, it was my understanding that Ubuntu Desktop doesn't need Samba to access a Linux server.  As we migrate away from WinXP Pro on our desktops, I would like to get rid of Samba, too - run the server lean and not anything extra.  But, I thought I had to have NFS for my Linux desktops to access the shared files on the Linux server.  When I installed Ubuntu, I only installed Samba, Cups, & SSH.  I THINK it had an option for "file server" but am not sure if I ever got an option to install NFS.  My reading on NFS says I should have a file named /etc/exports - but the file doesn't exist.  It (my reading) says that there needs to be some entries for file sharing to work via NFS, but the file doesn't even exist on the server.  I may have to do a complete reinstall just to see if I missed something in my short-sightedness.

I ran "smbclient -L RCH-SERVER -U%" and it returned nothing but the "help" response for smbclient.  

I have never set the "workgroup" on the Ubuntu desktop because the "workgroup" is a function of Windows and I'm not sharing Windows folders (folders on a WinXP box), but am only sharing Linux folders (folders on the Ubuntu Server that are on a drive that's ext3 format).

So, I tried "gksu gconf-editor" and got to the Workgroup parameter, which I gave the value of "RCH-WORKGROUP" and then closed the window.  I logged out & logged back in, and then went browsing the file system, network, workgroup, and it's only trying to let me see "Windows shares on RCH-WORKGROUP"  I've not created the folder and tried to mount the shared folder, but doubt that would work, considering all the other issues I appear to be facing.

Oh, and I am logging into the Ubuntu Desktop with the same UID & PW that I use (as a test, only) in Linux on the server, and in Win'XP from my desktop (& consequently Samba).

I do have two separate 80 GB SATA3 hard drives, and both of them have fully functioning installations of Ubuntu Server 8.10, and both of them are 100% dedicated to the server OS and have nothing else on them (the swap file, of course, but it's all OS stuff, no data).  I can swap them out and never miss a beat.  I'll probably do a reinstall on the one that's currently installed, just to see if I've missed something.  The data is on a RAID5 array, using four 250 GB SATA3 drives, and they have none of the server OS on them at all.

I hope this info helps.  Maybe something I've said here will trigger a response with some more good info.  THANK YOU!!!

-> David

---

### Post by capscrew on 2009-01-19
> **adlabens said:**
> Ok, no firewall is setup.  This is our home network, and it's still under development, so it's wide open.  As soon as I've got everything working, I'll start locking it down.  But for now, the firewall is turned off.

By "access" I mean that I want to be able to use the Desktop Ubuntu box to access shared files & folders on the Ubuntu Server box.  The server itself is never to be used for anything other than admin tasks such as setup, maintaining users, and locking it down to be a hardened server (eventually, but not till the entire network is working).

As for NFS versus Samba, it was my understanding that Ubuntu Desktop doesn't need Samba to access a Linux server.

Your Ubuntu desktop needs either Samba or NFS to access the shares.  NFS is needs to be installed and configured if you are going to use the protocol for sharing Linux to Linux> 

As we migrate away from WinXP Pro on our desktops, I would like to get rid of Samba, too - run the server lean and not anything extra.  But, I thought I had to have NFS for my Linux desktops to access the shared files on the Linux server.  When I installed Ubuntu, I only installed Samba, Cups, & SSH.  I THINK it had an option for "file server" but am not sure if I ever got an option to install NFS.  My reading on NFS says I should have a file named /etc/exports - but the file doesn't exist.  It (my reading) says that there needs to be some entries for file sharing to work via NFS, but the file doesn't even exist on the server.  I may have to do a complete reinstall just to see if I missed something in my short-sightedness. You can add the pertinent NFS libs via the command line. The command from the CLI is:```
sudo apt-get install nfs-kernel-server
``` There is no need to reinstall.  You will have to configure a bunch of things thought.  NFS was designed for domain networks and normally uses NIS or LDAP for user management.  There are tricks to avoid non matching UID's if you are using it in a small LAN environment.> 

I ran "smbclient -L RCH-SERVER -U%" and it returned nothing but the "help" response for smbclient. 
Do you have a naming service set up?  That would be DNS or Netbios.>  

I have never set the "workgroup" on the Ubuntu desktop because the "workgroup" is a function of Windows and I'm not sharing Windows folders (folders on a WinXP box), but am only sharing Linux folders (folders on the Ubuntu Server that are on a drive that's ext3 format). 

Workgroups are a function of the SMB protocol.  Samba uses workgroups as well as Windows.  The FS format (ext3 or NTFS) is not relevant.  There is no "Linux shares" as you describe.  It's either SMB (now called CIFS) or NFS (Network FIle Service) shares. > 

So, I tried "gksu gconf-editor" and got to the Workgroup parameter, which I gave the value of "RCH-WORKGROUP" and then closed the window.  I logged out & logged back in, and then went browsing the file system, network, workgroup, and it's only trying to let me see "Windows shares on RCH-WORKGROUP"  I've not created the folder and tried to mount the shared folder, but doubt that would work, considering all the other issues I appear to be facing.

Oh, and I am logging into the Ubuntu Desktop with the same UIDI believe you mean user login rather than UID.  UID is the users ID number in Linux.  I'm not trying to be picky, but you will get confused if you read and misinterpret what others are saying.>  & PW that I use (as a test, only) in Linux on the server, and in Win'XP from my desktop (& consequently Samba).
to use samba correctly you should have your users in the smbpasswd database.  Have you done that?[/QUOTE]

I think you will find configuring Samba will be your easiest bet at this time.  I would suggest that you read the [**[COLOR="Blue"]Samba documentation  [/COLOR]**]("http://www.samba.org/samba/docs/") and in particular the excellent  [**[COLOR="Green"]Samba Howto Collection[/COLOR]**]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/") before going much further.  Yes it is dry but most of your questions would be answered there.
> 
I do have two separate 80 GB SATA3 hard drives, and both of them have fully functioning installations of Ubuntu Server 8.10, and both of them are 100% dedicated to the server OS and have nothing else on them (the swap file, of course, but it's all OS stuff, no data).  I can swap them out and never miss a beat.  I'll probably do a reinstall on the one that's currently installed, just to see if I've missed something.  The data is on a RAID5 array, using four 250 GB SATA3 drives, and they have none of the server OS on them at all.

I hope this info helps.  Maybe something I've said here will trigger a response with some more good info.  THANK YOU!!!

-> David

---

