---
title: "Samba 3.0 + Winbind: Groups with Spaces issue"
date: 2009-06-08
forum: Server Platforms
---

### Post by rwyatt85 on 2009-06-08
Ubuntu OS: 8.04 LTS x64 Desktop
Client: Windows 7 RC & Windows XP
Samba Version: 3.0.28a-1ubuntu4.7 via apt-get.
 
I cannot get domain groups with spaces in them to translate right in my samba config. I dug around in the official documentation and random blogs enough to feel certain that this is supposed to be possible.
 
I have successfully joined my samba server to my Server 2008 Active Directory domain. Commands like wbinfo and getent are returning information correctly. Furthermore, both my home directory and an "everyone" share (config details below) are working exactly as intended. In other words, samba is working except for this one issue.
 
Here's a side by side with two shares so you can understand my testing environment.
 
[Everyone]
comment = Public Share for All Employees
path = /samba/everyone
Valid Users = @"Domain Users"
browseable = yes
read only = no
create mask = 0770
directory mask = 0770
 
[Information Tech]
comment = Department Share for Information Tech
path = /samba/informationTech
Valid Users = @"GD\information tech"
browseable = yes
read only = no
create mask = 0770
directory mask = 0770
 
The Everyone share is accessible, but the Information Tech share gives a "Permission Denied" message. I already know why, thanks to /var/log/samba/log.winbindd
 
[2009/06/08 14:48:12, 1] nsswitch/winbindd_group.c:winbindd_getgrnam(519)
group information\tech in domain GD does not exist
 
 
Ultimately I want samba to look for a group called "information tech". If i use the config file as shown, it looks for "information\tech" if i change the samba.conf file line to @"information tech" the error changes to the following:
 
[2009/06/08 14:52:39, 1] nsswitch/winbindd_group.c:winbindd_getgrnam(519)
group tech in domain GD does not exist
 
So either way, its not translating the request correctly when a space is involved. I've tried all sorts of variations with capitalization, spacing, and backslashes to no avail.
 
The rest of my config file, command outputs, etc are available by request. I dont want to dirty the post up with more command-line upchuck unless needed. Thanks for the help guys.

---

### Post by rwyatt85 on 2009-06-08
It seems in proper forum fashion that I answered my own question after i finally broke down and asked.
 
Here it is for any poor soul that finds themselves in my shoes:
 
My issue had something to do with using backslash ( \ ) as my "Windbind Separator". Change your winbind separator to "+" and go ahead and prefix it to your share permission entries even if you have "winbind use default domain = yes" set.

---

