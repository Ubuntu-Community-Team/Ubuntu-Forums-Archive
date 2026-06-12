---
title: "Samba remote access problems"
date: 2008-05-07
forum: Server Platforms
---

### Post by lacusmons on 2008-05-07
Hi all!

Dont know if this is the right place to post but here goes. I have been using Ubuntu server 7.10 for 6 months and really loving it. Upgraded to version 8.04 yesterday and everything is working as it should.

The problem that im having is with Samba server. My local LAN can access the shares no problem but accessing it remotely is more problematic. I can access other server services without a problem like Teamspeak, SSH, game server apps, Apache2, FTP and so on. Im behind a Dlink DGL-4300 gaming router.

I have been reading on the forum here and got a small picture that the problem is very complicated to say the least to solve. Many posts is saying to open port 137-139 and 445 in the router and that i have done but no success. When i connect from the remote machine (which is running Windows) it tries to connect if i do it from cmd prompt with net use command. It lets me enter my username and password but after i have put that in it says error 53. So i thought i can get passed that by installing hamachi on the Ubuntu server. I have installed it and enabled it at startup but same thing. I can use Apache, teamspeak etc etc but not Samba shares.

Many other posts saying that you can get passed this problem with iptables. By making a portforwarding request in the iptables so it direct the right traffic to the samba server and whatnot. I have tried many iptables configs over the last months but no avail so im turning to you gurus on this forum. I ran a Slackware server almost 6 or 7 years ago and back then i had to configure it from scratch and that was fun and learned alot. Never had this problem on that Linux box but back then the Samba worked a little different compared what it does today. That Slackware box was a experiment and a learning experience.

I have inlcuded my SMB.CONF file and sorry for the long post. I like to write.


```
[global]
;	General server settings
	netbios name = SERVER
	server string = %h server (Samba, Ubuntu 8.04)
	workgroup = HEMMA
	announce version = 5.0
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	passdb backend = tdbsam
	security = user
	null passwords = true
	username map = /etc/samba/smbusers
	invalid users = root
	name resolve order = hosts wins bcast
	interfaces = lo, eth0
	bind interfaces only = true
	
	wins support = yes

	load printers = no
;	printing = CUPS
;	printcap name = CUPS

	syslog = 1
	syslog only = yes
	
[homes]
	valid users = %S
	create mode = 0700
	directory mode = 0700
	browsable = no
	read only = no
	veto files = /*.{*}/.*/mail/bin/

; [printers]
;	comment = All Printers 
;	path = /var/spool/samba/
;	printer admin = root
;	guest ok = Yes 
;	printable = Yes 
;	use client driver = Yes 
;	browseable = yes 

[public]
	path = /server/Public/
	browseable = yes
	read only = no
	guest ok = no
;	public = yes

[ms_install]
	path = /server/MS_Install/
	browseable = yes
	read only = yes
	guest ok = no
	directory mask = 0755

```

---

### Post by HermanAB on 2008-05-07
No, Samba should not be made accessible over the internet.  It is insecure and is not designed for use on a hostile net.  Use a VPN or SSH.

Cheers,

Herman

---

### Post by lacusmons on 2008-05-07
> **HermanAB said:**
> No, Samba should not be made accessible over the internet.  It is insecure and is not designed for use on a hostile net.  Use a VPN or SSH.

Cheers,

Herman

He he oki, not so much helpful there but thanks for the advice ;)
Normally i would agree with you Herman but i have confed a dummy box server that i use to test stuff with and when i have solved the problem and it works i have applied the solution to my main server machine which is behind a firewall (router, ufw and hamachi VPN) which is working very nicely and very very secure. But i think i have solved it. in my smb.conf file in the interfaes line i have added the ham0 after my other interfaces and after that i could connect through hamachi but just need to test it from a remote machine.

```
interfaces = lo, eth0, ham0
```

EDIT: Yup, that solved the problem. Sorry to bother you all but thanks for reading :)

---

### Post by HermanAB on 2008-05-07
Firewall or no - you should not expose ports 135, 138, 139 or 445 to the internet.  The SMB protocol is not secure and the machine will get hacked.  Running it over a VPN or SSH is good.

---

