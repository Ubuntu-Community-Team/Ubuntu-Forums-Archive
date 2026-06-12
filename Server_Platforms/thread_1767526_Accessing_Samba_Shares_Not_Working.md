---
title: "Accessing Samba Shares Not Working"
date: 2011-05-25
forum: Server Platforms
---

### Post by 451422 on 2011-05-25
I have a couple of workstations that are having trouble connecting to a workgroup share that is used by about eight computers.  I redirected the user's files (my documents, favorits, etc) to a profile directory on the workgroup share by going into the properties of each item and redirecting the location to the mapped drive letter pointing to the share.

The server is on a desktop grade computer running Ubuntu 9.04.  The OS is current with the most recent updates available on live update agent.  I do realize it is 9.04 and Ubuntu has released version 10.xx, but don't feel it is necessary to upgrade to the latest version to share data files. 

All assistance or suggestions is very much appreciated.  Thanks.

I am receiving errors as follows: 
-------------------server log file and errors--------------------------------
Log.smbd > 2011/05/25 14:14:38, 0] param/loadparm.c:lp_do_parameter(7258) Global parameter smb ports found in service section!
 
- Syslog > May 25 13:52:23 bob kernel: [4080379.259028] [drm:drm_wait_vblank] *ERROR* failed to acquire vblank counter, -22

- "[Samba] getpeername failed. Error was Transport endpoint is not connected"
-------------------------------------------------------------------------------------

----------------computer errors when accessing or running programs-------------------------------
Explorer.exe process produces ans error "Server Execution Error"

"Net View" is unable to obtain a list of servers from the command prompt.
---------------------------------------------------------------------------------------------------------------------------
[SIZE="2"]
---------------------- smb.conf ----------------------------------------

#======================= Global Settings =======================

[global]
 log file = /var/log/samba/log.%m
 passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
 obey pam restrictions = yes
 logon drive = H:
 domain master = auto
 map to guest = bad user
 encrypt passwords = true
 logon home = \\%N\%U
 passwd program = /usr/bin/passwd %u
 passdb backend = tdbsam
 wins support = true
 dns proxy = no
 browseable = no
 writable = yes
 server string = %h server
 unix password sync = yes
 workgroup = obrien
 os level = 20
 comment = Home Directories
 security = user
 syslog = 0
 usershare allow guests = yes
 panic action = /usr/share/samba/panic-action %d
 max log size = 1000
 domain logons = yes
 pam password change = yes

[ScannedData]
 delete readonly = yes
 path = /home/sambauser/ScannedData
 write list = sambauser,@everyone
 force directory mode = 755
 force create mode = 755
 comment = Scanned Documents
 guest ok = yes
 ; browseable = yes
 writeable = yes

smb ports = 139

[workgroup]
 browseable = Yes
 read only = No
 delete readonly = Yes
 path = /home/sambauser
 force directory mode = 755
 force create mode = 755
 comment = Company Data Store
 public = yes
---------------------------End smb.conf-------------------------------------------[/SIZE]

---

### Post by capscrew on 2011-05-25
> **451422 said:**
> I have a couple of workstations that are having trouble connecting to a workgroup share that is used by about eight computers.  I redirected the user's files (my documents, favorits, etc) to a profile directory on the workgroup share by going into the properties of each item and redirecting the location to the mapped drive letter pointing to the share.

The server is on a desktop grade computer running Ubuntu 9.04.  The OS is current with the most recent updates available on live update agent.  I do realize it is 9.04 and Ubuntu has released version 10.xx, but don't feel it is necessary to upgrade to the latest version to share data files. 

All assistance or suggestions is very much appreciated.  Thanks.

[COLOR="Blue"]How about a better description of system.
[LIST]
[*]How did you generate the /etc/samba/smb.conf file?
[*]What are the client OS's?
[*]Is everything on the same subnet?
[*]How do you provide nameservices (DNS) for the LAN?
[*]Are all users also Samba users? 
[/LIST]

I will comment on the few obvious things below. [/COLOR]

> 

I am receiving errors as follows: 
-------------------server log file and errors--------------------------------
Log.smbd > 2011/05/25 14:14:38, 0] param/loadparm.c:lp_do_parameter(7258) Global parameter smb ports found in service section!
[COLOR="Blue"]This is because you have the parameter below in the wrong place in the smb.conf file```
smb ports = 139
```
But more importantly: Why do you have it at all?  This is defiantly not needed in Samba 3 with Windows client later than Win2k.[/COLOR]> 
 
- Syslog > May 25 13:52:23 bob kernel: [4080379.259028] [drm:drm_wait_vblank] *ERROR* failed to acquire vblank counter, -22
[COLOR="Blue"]This has nothing to do with Samba.  This is an Xserver error.  All Samba errors will be in the *smbd and nmbd *logs.[/COLOR]> 
- "[Samba] getpeername failed. Error was Transport endpoint is not connected"
[COLOR="Blue"]This is probably your fatal error.  This says that the SMB resource (//COMPUTERNAME/share) could not be found to connect to.[/COLOR]> 
-------------------------------------------------------------------------------------

----------------computer errors when accessing or running programs-------------------------------
Explorer.exe process produces ans error "Server Execution Error"

"Net View" is unable to obtain a list of servers from the command prompt.
[COLOR="Blue"]Sorry, I'm no help with Windows.[/COLOR] :-(> 
---------------------------------------------------------------------------------------------------------------------------
[SIZE="2"]
---------------------- smb.conf ----------------------------------------

#======================= Global Settings =======================

[global]
 log file = /var/log/samba/log.%m
 passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
 obey pam restrictions = yes
 logon drive = H:
 domain master = auto
 map to guest = bad user
 encrypt passwords = true
 logon home = \\%N\%U
 passwd program = /usr/bin/passwd %u
 passdb backend = tdbsam
 wins support = true
 dns proxy = no
 browseable = no
 writable = yes
 server string = %h server
 unix password sync = yes
 workgroup = obrien
 os level = 20
 comment = Home Directories
 security = user
 syslog = 0
 usershare allow guests = yes [COLOR="Blue"]Are you using GUI created shares?[/COLOR]> 
 panic action = /usr/share/samba/panic-action %d
 max log size = 1000
 domain logons = yes [COLOR="Blue"]Why this?[/COLOR]> 
 pam password change = yes

[ScannedData]
 delete readonly = yes 
 path = /home/sambauser/ScannedData
 write list = sambauser,@everyone
 force directory mode = 755
 force create mode = 755
 comment = Scanned Documents
 guest ok = yes
 ; browseable = yes [COLOR="Blue"]How does the user find the share?[/COLOR]> 
 writeable = yes

smb ports = 139 [COLOR="Blue"]This prevents Samba from using TCP port 445.  The default is *smb ports = 445*[/COLOR]> 

[workgroup]
 browseable = Yes
 read only = No
 delete readonly = Yes
 path = /home/sambauser [COLOR="Blue"]I would do this a little different.  I would put the Public share outside of any users /home directory.  This is what /srv is for.  I would use at least /srv/Public.[/COLOR]> 
 force directory mode = 755
 force create mode = 755
 comment = Company Data Store
 public = yes
---------------------------End smb.conf-------------------------------------------[/SIZE]

[COLOR="Blue"]Everyone has the own style (reasons) for doing things, but I would start with as many defaults in place as possible.  I have a mixed network of Debian, Ubuntu, XP and Vista.  They all share with no problems.[/COLOR]

---

### Post by 451422 on 2011-05-25
> How about a better description of system.
The system is an Acer Intel dual-core with 4gb of ram.  Configured with one workgroup share that contains shared data and desktop files in separate directories.

> How did you generate the /etc/samba/smb.conf file?
Created by Webmin and manually modified per some research.

> What are the client OS's?
All clients are Windows 7 and two Windows XP

> Is everything on the same subnet?
Same subnet 

> How do you provide nameservices (DNS) for the LAN?
DNS is provided by the router.  The Samba server is supposed to be a WINS server.

> Are all users also Samba users?
Yes all the users are on Samba

> smb ports = 139
But more importantly: Why do you have it at all? This is defiantly not needed in Samba 3 with Windows client later than Win2k.  This prevents Samba from using TCP port 445. The default is smb ports = 445
I put it in there in a desperate attempt to fix the problem.

---

### Post by capscrew on 2011-05-26
> **451422 said:**
> The system is an Acer Intel dual-core with 4gb of ram.  Configured with one workgroup share that contains shared data and desktop files in separate directories.

Created by Webmin and manually modified per some research.

Boo!  Do you have a copy of the original smb.conf file?> 
...
DNS is provided by the router.  The Samba server is supposed to be a WINS server.

DNS for the LAN, not the Internet.  We don't need to a WINS server for a simple LAN situation.  The only time you need a WINS server is if there are multiple subnets in your network.  Samba can convert local DNS listings to NetBIOS names (COMPUTER NAMES) via the daemon nmbd.  **Can you ping all the hosts on the network by hostname?** >  

Yes all the users are on Samba
What do you mean *on Samba*?  Are they in the smbpasswd database?  Is each Windows user also a Ubuntu user as well as a Samba user?  Do their login/pass match?> 

I put it in there in a desperate attempt to fix the problem.

Take it out.

My suggestion would be to start over with Samba.  This is not as hard as you would think.  Samba completely reconfigures itself everytime you reload the smbd daemon (restarting Samba).

If you don't have a copy of the original smb.conf file there is one at
```
/usr/share/samba/smb.conf
```

Save your share definitions (or at least the basic info) and we can recreate them in the new smb.conf file.  If you use Webmin again I can't help you.  You will be suprised how easy it is to set this up via a simple text editor.

Essentially we are going to do what is mentioned in post #6 of [**_[COLOR="Blue"]this[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1749823").  Follow the link to [**_[COLOR="Blue"]this[/COLOR]_**]("http://www.jonathanmoeller.com/screed/?p=1590") also.  This guide works for any Samba install from 8.04 on.

---

