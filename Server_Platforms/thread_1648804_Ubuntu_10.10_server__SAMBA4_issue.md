---
title: "Ubuntu 10.10 server / SAMBA4 issue"
date: 2010-12-19
forum: Server Platforms
---

### Post by efurlan on 2010-12-19
Coming from a Windows environment (SERVER 2k3) to linux for server needs has been very rewarding, however am trying to get SAMBA 4 Alpha to work correctly since... well... it would give me an excuse to say bye bye to Windows server completely (more or less)
 
I have used ubuntu server 10.04 with webmin as a successful file server, however it feels so limited when compared to AD windows for XP / 7 machines. 
 
After reading about Samba4 I really want to get it to work (I am not wonderful with linux... somewhat of a newbie, but am really trying to learn!) I currently installed 10.10 server with xfce for GUI when working with multiple directories, and have successfully got the latest alpha of Samba4 to install... I can even do a -V check etc and it works fine
 
However, when i follow the general tutorial [http://blog.mycroes.nl/2010/09/installing-samba-4-on-ubuntu-maverick.html](http://blog.mycroes.nl/2010/09/installing-samba-4-on-ubuntu-maverick.html) I get stuck around the the point where I attempt to see if the server shares are up. I am able to bind dnsupdate and spnupdate to the local samba file with the correct information.
 
However, when I attempt to see shared through smbclient -UAdministrator I get the following error: ncacn_np:localhost - NT-STATUS_CONNECTION_REFUSED List servers not implemented.
 
I checked out etc/samba and the configuration file does not exist but there is an old one (From the initial samba3 install) I know I'm probably just missing something idiotic, or not realizing something, and if so would someone be able to point me in the right direction? (Even if it is another forum post or howto) thanks! This is installed on a secondary hard drive as a test and not always connected to the net... however localhost access shouldn't be affected then (right?)... so I will attempt any suggestion that seems reasonable.

---

### Post by windependence on 2010-12-19
Some troubleshooting in this thread: [http://ubuntuforums.org/showthread.php?t=1646851&page=2](http://ubuntuforums.org/showthread.php?t=1646851&page=2)
 
You were supposed to save the old SAMBA config file and create a new one, but I notice in the tutorial the section on creating the new one is blank:
 
>  
Create a samba 4 config and provision the database

 
Did you miss that step? I'm not a SAMBA expert so I'm not sure what he wants there but it looks like you might have skipped it since he forgot to include it in the tutorial.
 
-Tim

---

