---
title: "Installing Open VPN"
date: 2006-03-14
forum: Server Platforms
---

### Post by rock freak on 2006-03-14
It gets to this stage as spits this out at me and i have installed open ssl any ideas at all????


configure: checking for OpenSSL Crypto Library and Header files...
checking openssl/evp.h usability... no
checking openssl/evp.h presence... no
checking for openssl/evp.h... no
configure: error: OpenSSL Crypto headers not found.

So I did a "find /usr -name evp.h" and got:
/usr/local/ssl/include/openssl/evp.h

---

### Post by drakkan on 2006-03-14
why not

```

apt-get install openvpn

```

??? :D

---

### Post by rock freak on 2006-03-14
i didnt think open vpn was on there thts why !!!!!:D


i shall give it a go and let you know

---

### Post by Darkriser on 2006-03-14
[QUOTE=drakkan]why not

```

apt-get install openvpn

```

??? :D[/QUOTE]

that's really easy :) 

on the other side, repositories don't always offer latest releases (and not all apps are back ported). currently, openvpn latest stable release is 2.0.5, using apt-get you'll probably install "only" version 2.0.2.

---

### Post by rock freak on 2006-03-14
coool all install but hwo do i start it and configure it.  i want any vpn ips to start at 192.168.1.200

any help/ideas????


cheers

---

### Post by Darkriser on 2006-03-15
go to [http://openvpn.net/](http://openvpn.net/) and read the documentation + HowTo's, there's really lot of useful reading explaining configuration of openvpn in details.

---

### Post by usacomp2k3 on 2006-05-17
Does anyone have a how-to that is specific to Ubuntu/debian? I seemed to have gotten lost trying the how-to on the openvpn website.

---

### Post by gunnor on 2006-07-01
Me too! 
For example, I don't know where to put the files (openvpn.conf and static.key).
I read [http://openvpn.net/howto.html](http://openvpn.net/howto.html) and [http://kerneltrap.org/node/5018](http://kerneltrap.org/node/5018) but I am stuck now :(

---

### Post by gunnor on 2006-07-01
sorry for double posting...

---

### Post by nzgreen on 2006-07-03
[QUOTE=gunnor]Me too! 
For example, I don't know where to put the files (openvpn.conf and static.key).
I read [http://openvpn.net/howto.html](http://openvpn.net/howto.html) and [http://kerneltrap.org/node/5018](http://kerneltrap.org/node/5018) but I am stuck now :([/QUOTE]

The configuration files go in /etc/openvpn if you want to use the init script.  You will need to edit /etc/default/openvpn to tell the init script which vpns to start.  Probably easiest to use "all" and then any files in /etc/openvpn ending with .conf are assumed to be openvpn config files and a corresponding vpn will be started.

Otherwise, the config files can go anywhere and you can start the vpn manually and  specify the config file to use like so:
```
~$ sudo openvpn --config /home/scott/openvpn/tohome.conf
```

---

### Post by gunnor on 2006-07-06
nzgreen,

thanks for the answer.
I still have problems understanding the VPN-configuration of OpenVPN.
I want to enable friends (and of course me) to access my server via VPN with Windows XP, but this seems to be impossible because everyone needs certificates.
Is that right or am I wrong?

PS: This is my openvpn.conf:
```
dev tun
ifconfig 10.0.0.254 192.168.10.195
secret static.key

daemon
user nobody
group nobody

## Set the appropriate level of log
## file verbosity.
##
## 0 is silent, except for fatal errors
## 4 is reasonable for general usage
## 5 and 6 can help to debug connection problems
## 9 is extremely verbose
log /var/log/openvpn/openvpn.log
verb 6 
```

---

### Post by nzgreen on 2006-07-06
You will need to give your friends a copy of static.key.  They should then be able to access your server.  This is much less secure than using certificates, but is a lot easier to setup and still way more secure than a PPTP connection (IMO).

If you fall out with one of your friends and want to deny them access then you will have to create a new key and re-distribute to those who should have access.  With certificates you could just revoke the certificate for that particular friend.

---

### Post by gunnor on 2006-07-06
All right, I'll try that :)
Many thanks for the info!

---

### Post by Jonix on 2006-07-24
If you can't find the file evp.h while you do a manually search you do not have the OpenSSL development files installed. Install it with the command 'sudo apt-get install libssl-dev'.

---

### Post by paul.maddox on 2006-07-24
Sorry to threadjack, but does OpenVPN require a Windows client or can you connect via the VPN client build into WinXP?

I've tried using poptop as a VPN server in the past but it was a pain because the kernel needed patching for MPPE encryption (WinXP default) and setting up clients without MPPE requires more steps for the end user.

Thanks

---

### Post by NewPenguin on 2008-01-03
> **Jonix said:**
> If you can't find the file evp.h while you do a manually search you do not have the OpenSSL development files installed. Install it with the command 'sudo apt-get install libssl-dev'.

I realize this is a Ubunto specific forum, but perhaps someone can help regardless.  I found this thread as I am having the same problem installing OpenVPN.  I have also installed OpenSSL.

How do I install libssl-dev with CentOS.  I cannot use the apt-get command.  

I appreciate your help!  Thank you!

---

### Post by NewPenguin on 2008-01-03
Problem solved, found solution at [http://www.webhostingtalk.com/showthread.php?t=595436](http://www.webhostingtalk.com/showthread.php?t=595436)

Thanks anyway!

---

