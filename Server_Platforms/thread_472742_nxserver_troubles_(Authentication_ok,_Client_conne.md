---
title: "nxserver troubles (Authentication ok, Client connection NOT!)"
date: 2007-06-13
forum: Server Platforms
---

### Post by pcpete on 2007-06-13
Hello all! I have been very interested in getting NX server running for use as a remote connection into a 6.06 Ubuntu Gnome box. NX is awesome, and I'm definitely ready to get VNC to the next level. 

I have setup FreeNX using the tutorial given:[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)
refered to this thread as well: [http://ubuntuforums.org/showthread.php?t=241651&highlight=nxserver+troubles&page=2](http://ubuntuforums.org/showthread.php?t=241651&highlight=nxserver+troubles&page=2)

Quesitons:

1.) Has anyone run into a problem connecting to nxserver into a standard Gnome session? I use the NEWER client 2.0 on a Windows XP machine and I have no luck connecting to the *nix box. Here's the ouput from the NoMachine windows 2.0 client: 

NX> 203 NXSSH running with pid: 684
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 10.2.2.13 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.4.0
NX> 134 Accepted protocol: 1.4.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: ftp
NX> 102 Password: 
NX> 103 Welcome to: ftp-desktop user: ftp
NX> 105 listsession --user="ftp" --status="suspended,running" --geometry="1024x768x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'ftp' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: ftp
NX> 105 startsession  --link="adsl" --backingstore="1" --nodelay="1" --cache="8M" --images="32M" --media="0" --session="ftp" --type="unix-gnome" --cookie="******" --geometry="fullscreen" --kbtype="pc102/en_US" --screeninfo="1024x768x32+render" 

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: ftp-desktop-1000-AD721BEB0EB89D297DA28F28EE101E84
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: b86adcc47abadc81c92e58b172cfc6fc
NX> 702 Proxy IP: 10.2.15.33
NX> 706 Agent cookie: ff104b2dfab9fe8c0676587292a636d3
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 0
/usr/lib/nx/nxserver: line 891:  5394 Terminated              ( sleep $AGENT_STARTUP_TIMEOUT; exit 1 )
NX> 105 NX> 504 Session startup failed.
NX> 1004 Error: nxagent failed to start with: Unrecognized option: 1
NX> 1001 Bye.
Killed by signal 15.

(Originally I thought it was a session error, I played with the nomahine environment settings e.g. KDE, Gnome, etc... Also I logged out on the local machine as the user "ftp" I was logging into)

**Thanks for your help, I haven't really seen a great explaination...!**

---

### Post by pcpete on 2007-06-13
In the meantime I'll try a 1.5 client.... but has anyone found a preferred way to install NX? I don't mind a NoMachine/ FreeNX option..

---

### Post by pcpete on 2007-06-13
**Quick update!** A version 1.5 client is able to connect to the NXSERVER. The fact that a 2.0 client cannot connect is just a nuisance though. 

Does anyone know what settings can be changed on the server level for a fix? I was led to believe there is a fix.. just can't find it

---

