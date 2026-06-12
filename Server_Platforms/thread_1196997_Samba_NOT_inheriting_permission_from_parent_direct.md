---
title: "Samba NOT inheriting permission from parent directory"
date: 2009-06-25
forum: Server Platforms
---

### Post by wheniwork on 2009-06-25
I hope someone can please help me out here. I have been struggling with this for over a year.

When a new folder of file is made through a samba share the new file/folder is not getting the permissions of the parent folder.

What I want is all folders/files created to get the permissions 775.

See an example of what just happend here:
```
# ls -al
total 10
drwxrwsr-x  8 thisclicks staff    304 2009-06-25 14:40 .
drwxrwsr-x 55 thisclicks staff   1960 2009-05-29 13:48 ..
drwxr-xr-x  2 chad       staff     48 2009-06-25 14:40 asdsad
-rwxrw-r--  1 chad       staff   6148 2008-11-20 12:26 .DS_Store
drwxrws--x  2 chad       clients   48 2008-09-12 10:28 ftp
drwxrwsr-x  5 thisclicks staff    128 2008-08-01 00:31 LAT000 (Description)
drwxrwxr-x  5 chad       staff    128 2008-08-01 00:31 LAT100 (test)
drwxrwxr-x  3 chad       staff     72 2009-06-25 14:32 LAT102 (test2)
drwxrwsr-x  3 thisclicks staff     80 2008-08-01 00:31 SiteDefs

```

Using samba, the folder I made called "asdsad" does not have write permissions for the group. IT SHOULD. I want it to sooo bad. 

here is my global settings in my smb.conf

```

#======================= Global Settings =======================

[global]
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	write list = @staff
	force group = +staff
	passwd program = /usr/bin/passwd %u
	dns proxy = no
	netbios name = chernobyl
	invalid users = root
	hide files = /._*/.DS_Store/._.*/DesktopFolderDB/Network Trash Folder/resource.frk/TheFindByContentFolder/TheVolumeSettingsFolder/
	block size = 4096
	os level = 20
	security = user
	usershare allow guests = yes
	max log size = 1000
	log file = /var/log/samba/log.%m
	socket options = TCP_NODELAY
	map to guest = bad user
	hide dot files = yes
	encrypt passwords = true
	passdb backend = tdbsam
	server string = %h server (Samba, Ubuntu)
	unix password sync = yes
	valid users = @staff
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	pam password change = yes
        force create mode = 0775
        force directory mode = 0775
```

Please help.

---

### Post by Lucky. on 2009-06-25
I ran this same gauntlet last year.  Inheritance, Samba, etc.

Could the UMask be interfering with the Samba permissions?

Check the following file:

/etc/profile

Look at the bottom line.  By default the UMask is 022, which would block any permissions down to 755 on newly created files.  Changing the UMask to 002 would get the trick done if indeed this is the problem.

The sticky bit will help newly created files inherit the same group as the parent directory, but not its permission bits (in case you already didn't know).

Better inheritance can be achieved by using Access Control Lists, but I'm not sure if SAMBA would override the permissions based on the mask in its configuration.  I've never tried it before.

```

force directory mode = 0775

```

I **think** (not sure) that this might keep newly created subdirectories from gaining the sticky bit and propagating group inheritance...so inheritance would work at the top level, but not deeper down.  Perhaps 2775 or simply 775 would work?  I'm just throwing this out there...not 100% sure.

---

### Post by wheniwork on 2009-06-26
Neither of those options worked. Samba is still setting permissions to 755 when new files and directories are made. 

I need to get samba to create folders and files as 775.

Thanks in advanced.

---

### Post by Lucky. on 2009-06-26
If I get some time tonight, I'll give this a shot on my virtual machine and see if I can help out some more.

---

### Post by Lucky. on 2009-07-01
Well man, doesn't look like I can solve the problem.  I tried my best to duplicate the issue, but to no avail.

I don't know if it will help, but here's my configuration that works well and inherits permissions appropriately.  It doesn't have any of the other features that yours has though, but maybe it could be a starting point to troubleshooting?

```


[global]
security = user

[web]
path = /srv/stufftoshare
writeable = yes
create mask = 775
directory mask = 775
valid users = mydude


```

Sorry I couldn't help more.  Good luck.

---

### Post by sbleono on 2009-07-30
Here's the permissions-related section of the config for my share from smb.conf:

        create mask = 664
        force create mode = 664
        security mask = 664
        force security mode = 664

        directory mask = 2775
        force directory mode = 2775
        directory security mask = 2775
        force directory security mode = 2775

I'm using OS X clients, and they tend to set their own permissions on the files unless you set it up this to force exact permissions for all new files and directories. I also found that using "inherit permissions" and "inherit acls" don't work very well and interfere with these settings, so I took them out.

I've finally got this working after years of putting up with having to manually adjust the permissions on new folders!

Note that I'm using 2775 instead of 0775. The 2 in front is for the setGID bit, which causes new dirs to inherit the parent's group. You should be able to change it to 0775 with no trouble.

---

