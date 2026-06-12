---
title: "Help setting openssh for remote client access to samba shares."
date: 2009-10-24
forum: Server Platforms
---

### Post by photoman355 on 2009-10-24
Hi

I'm building by first linux server and am in need of some help setting up remote client access to my samba shares.

Build so far is:

Ubuntu Server 8.04LTS
Webmin
Samba
OpenSSH

The client machines I want to connect are both windows and mac.  I've configured samba and that's working fine in a wired network.  I can connect to the server using putty but I needed something simpler for the remote users (I need a GUI tomake it easy for them to use for sharing files over the internet) so I decided on Winscp for the PC's and I'll possibly use fung or cyberduck for the mac.

My problem is that when I setup Winscp and added my host/username in both ssh tunnel and session I get an error which prevents me from connecting = (ESshFatal) Network error: Connection refused.  I figured this is because openssh needs some configuration work to setup the sftp side of things but I don't know enough about what I need to do to get things working and can't find any good tutorials.  I also disabled my firewall just incase it was causing a problem but seems not to be that and port 22 is open as putty can connect using it.

Below is a log of the winscp response I got:

. 2009-10-24 21:51:41.265 --------------------------------------------------------------------------
. 2009-10-24 21:51:41.281 WinSCP Version 4.1.9 (Build 416) (OS 5.1.2600 Service Pack 2)
. 2009-10-24 21:51:41.281 Login time: 24 October 2009 21:51:41
. 2009-10-24 21:51:41.281 --------------------------------------------------------------------------
. 2009-10-24 21:51:41.281 Session name: [EMAIL="xxxx@xxx.xxx.xxx.xxx"]xxxx@xxx.xxx.xxx.xxx[/EMAIL]
. 2009-10-24 21:51:41.281 Host name: xxx.xxx.xxx.xxx (Port: 22)
. 2009-10-24 21:51:41.281 User name: xxxx (Password: No, Key file: No)
. 2009-10-24 21:51:41.281 Tunnel: Yes
. 2009-10-24 21:51:41.281 Tunnel: Host name: xxx.xxx.xxx.xxx (Port: 22)
. 2009-10-24 21:51:41.281 Tunnel: User name: xxxx (Password: No, Key file: No)
. 2009-10-24 21:51:41.281 Tunnel: Local port number: 0
. 2009-10-24 21:51:41.281 Transfer Protocol: SFTP (SCP)
. 2009-10-24 21:51:41.281 Ping type: -, Ping interval: 30 sec; Timeout: 15 sec
. 2009-10-24 21:51:41.281 Proxy: none
. 2009-10-24 21:51:41.281 SSH protocol version: 2; Compression: No
. 2009-10-24 21:51:41.281 Bypass authentication: No
. 2009-10-24 21:51:41.281 Try agent: Yes; Agent forwarding: No; TIS/CryptoCard: No; KI: Yes; 

GSSAPI: No
. 2009-10-24 21:51:41.281 Ciphers: aes,blowfish,3des,WARN,arcfour,des; Ssh2DES: No
. 2009-10-24 21:51:41.281 SSH Bugs: -,-,-,-,-,-,-,-
. 2009-10-24 21:51:41.281 SFTP Bugs: -,-
. 2009-10-24 21:51:41.281 Return code variable: Autodetect; Lookup user groups: Yes
. 2009-10-24 21:51:41.281 Shell: default, EOL: 0
. 2009-10-24 21:51:41.281 Clear aliases: Yes, Unset nat.vars: Yes, Resolve symlinks: Yes
. 2009-10-24 21:51:41.281 LS: ls -la, Ign LS warn: Yes, Scp1 Comp: No
. 2009-10-24 21:51:41.281 Local directory: default, Remote directory: home, Update: No, Cache: 

Yes
. 2009-10-24 21:51:41.281 Cache directory changes: Yes, Permanent: Yes
. 2009-10-24 21:51:41.281 DST mode: 1
. 2009-10-24 21:51:41.281 --------------------------------------------------------------------------
. 2009-10-24 21:51:41.421 Opening tunnel.
. 2009-10-24 21:51:41.468 Autoselected tunnel local port number 50000
. 2009-10-24 21:51:41.500 [Tunnel] Looking up host "xxx.xxx.xxx.xxx"
. 2009-10-24 21:51:41.500 [Tunnel] Connecting to xxx.xxx.xxx.xxx port 22
. 2009-10-24 21:51:43.031 [Tunnel] Failed to connect to xxx.xxx.xxx.xxx: Network error: 

Connection refused
* 2009-10-24 21:51:43.078 (ESshFatal) Network error: Connection refused.

Can anyone help me out?

---

### Post by photoman355 on 2009-10-25
Solved.

It turns out that even after opening ports in my firewall (Comodo), it was restricting access separately to the winscp program even though I had responded to the firewalls allow permissions.  I had tried disabling the firewall also before but comodo has a process that seems to run in the background even when its not being used.  

To fix changed winscp rules to allow all traffic in/out and that allowed me to login.

On another note just incase anyone else has this problem:  When I switched to login as a different user it suddenly stopped working again.  This was an issue with shell permissions as ssh needs certain commands to be run in order to login.  I had changed these to bin/false for all users other than the administratior thinking that they would not need to run shell commands.  Changed back over to bin/bash to fix.

---

