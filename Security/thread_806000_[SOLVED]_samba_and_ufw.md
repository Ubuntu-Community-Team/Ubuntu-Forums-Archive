---
title: "[SOLVED] samba and ufw"
date: 2008-05-24
forum: Security
---

### Post by kamaji792 on 2008-05-24
I have been trying to set up an ubuntu box (8.04) to provide some network storage for some windows PCs.  I am using **ufw** as a firewall and **samba** as the file server.  There is a router allowing the windows PCs to access the internet, so the idea of the firewall is to stop anyone connecting from outside the local network.  The default for ufw is to deny.

The only way I can get it to work is with ufm set up as shown by the status:
```
$ ufw status
Firewall loaded

To               Action  From
--               ------  ----
Anywhere         ALLOW   192.168.0.0/24
```

I know samba is supposed to use ports 135, 137, 138, 139 and 445.

However if I only open these ports (tcp and udp) I can't connect from the windows PCs.  Interestingly I can't see any logging of dropped packets in the syslog (yes, logging is turned on).

I have seen one comment that said you need ports 1024 to 65535 to be open as well.  However ufw does not allow you to specify a rage of ports so opening large number of ports is impractical.

Is this the best I can do or do ? :confused:

or do I need to learn IP tables :cry:

Thanks in advance

---

### Post by kamaji792 on 2008-06-05
OK the lack of response tells me I need to go iptables.

Thanks to the excellent [IPTables HowTo](https://help.ubuntu.com/community/IptablesHowTo) I have managed to get to grips with iptables.  With far better resolution on the ports I allow and block.

just one word of warning.  The howto tells you to add the following line to the /etc/network/interfaces file:
```
post-down iptables-save -c > /etc/iptables.rules
```
I had to change the line to:
```
post-down sh -c "iptables-save -c > /etc/iptables.rules"
```
to get it to work.

I still think I have a little way to go as "apt-get update" has stopped working so I will have to work out how to get that passed the firewall.

Still I am one step closer to setting up a NAS box at work.

**Edit:**Two points.

1) I have found the answer to allowing 'apt-get update' to work you need to do the following (It was actually in the IPTables HOWTO I referenced above.).
```

sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

```

2) As noted by:
> **tebbens said:**
> Using ufw, here is mine....it works great.

sudo ufw allow proto udp from 192.168.1.0/24 to any port 137
sudo ufw allow proto udp from 192.168.1.0/24 to any port 138
sudo ufw allow proto tcp from 192.168.1.0/24 to any port 139
sudo ufw allow proto tcp from 192.168.1.0/24 to any port 445
This worked when I built a new system recently and did not interfere with apt-get.  So I don't know what I was doing wrong originally.

---

### Post by tebbens on 2008-06-06
> **kamaji792 said:**
> I have been trying to set up an ubuntu box (8.04) to provide some network storage for some windows PCs.  I am using **ufw** as a firewall and **samba** as the file server.  There is a router allowing the windows PCs to access the internet, so the idea of the firewall is to stop anyone connecting from outside the local network.  The default for ufw is to deny.

The only way I can get it to work is with ufm set up as shown by the status:
```
$ ufw status
Firewall loaded

To               Action  From
--               ------  ----
Anywhere         ALLOW   192.168.0.0/24
```

I know samba is supposed to use ports 135, 137, 138, 139 and 445.

However if I only open these ports (tcp and udp) I can't connect from the windows PCs.  Interestingly I can't see any logging of dropped packets in the syslog (yes, logging is turned on).

I have seen one comment that said you need ports 1024 to 65535 to be open as well.  However ufw does not allow you to specify a rage of ports so opening large number of ports is impractical.

Is this the best I can do or do ? :confused:

or do I need to learn IP tables :cry:

Thanks in advance


Using ufw, here is mine....it works great.

sudo ufw allow proto udp from 192.168.1.0/24 to any port 137
sudo ufw allow proto udp from 192.168.1.0/24 to any port 138
sudo ufw allow proto tcp from 192.168.1.0/24 to any port 139
sudo ufw allow proto tcp from 192.168.1.0/24 to any port 445

---

### Post by sefs on 2009-03-19
For ubuntu 8.04 and 8.10

Taken from ...

[http://log.logfish.net/node/31](http://log.logfish.net/node/31) 

OR

[http://www.mypcsupport.de/net/linux/ubuntu-ufw/](http://www.mypcsupport.de/net/linux/ubuntu-ufw/)

1/

You might also want to change /etc/default/ufw and add add the netbios_ns line so you can use samba:
```

# The nf_contrack_netbios_ns has been added
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc nf_conntrack_netbios_ns"

```


2/

#Samba sharing [1]
```

sudo ufw allow proto tcp to any port 135 from 192.168.0.0/16
sudo ufw allow proto udp to any port 137 from 192.168.0.0/16
sudo ufw allow proto udp to any port 138 from 192.168.0.0/16
sudo ufw allow proto tcp to any port 139 from 192.168.0.0/16
sudo ufw allow proto tcp to any port 445 from 192.168.0.0/16

```

3/

#Allow avahi/bonjour/zeroconf [2]
```

sudo ufw allow proto udp to any port 5353 from 192.168.0.0/16

```


Additionally install:
samba-tools
system-config-samba

Access system-config-samba via  System -> Administration -> Samba  and do all you configuration there.

---

### Post by mfrederickson67 on 2010-10-14
It's really simple.  Just issue 
```
 sudo ufw allow Samba
```
This configures it for all samba ports via the app facility in ufw... man ufw for more details. This was with Ubuntu 10.4.

---

### Post by Morbius1 on 2010-10-14
mfrederickson67, That's very interesting.

So if I wanted to replicate the same samba settings that sefs did then the syntax would be this:

```
 sudo ufw allow from 192.168.0.0/16 to any app Samba
```

Is that how you understand the syntax?

---

### Post by k23 on 2010-12-08
The right rule is this: :popcorn:

```
sudo ufw allow from any app Samba to "yourlinuxboxIP"
```

---

### Post by condamine on 2010-12-15
Me thinks this is back to front (or un-documented alternative syntax)...
> **k23 said:**
> The right rule is this: :popcorn:

```
sudo ufw allow from any app Samba to "yourlinuxboxIP"
```

From the man page...
> 
  Users  can specify one of the applications names when adding rules. For
       example, when using the simple syntax, users can use:

         ufw allow <name>

       Or for the extended syntax:

         ufw allow from 192.168.0.0/16 to any app <name>

       You should not specify the protocol with either syntax,  and  with  the
       extended syntax, use app in place of the port clause.

This worked for me
```

sudo ufw allow from 192.168.1.0/24 to any app samba
sudo ufw allow from 192.168.1.0/24 to any app cups

```
So just to check...
```

sudo ufw status verbose
Status: active
Logging: off
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
137,138/udp (Samba)        ALLOW IN    192.168.1.0/24
139,445/tcp (Samba)        ALLOW IN    192.168.1.0/24
631 (CUPS)                 ALLOW IN    192.168.1.0/24

```

I'd be interested in any other comments as I have found UFW to be a little quirky, especially...

Re: the logging (rather the lack of it) mentioned by kamaji792 in the original post.
I have found a couple of **errors in the man page.**
[INDENT]log-all, mentioned briefly in the man page, does nothing[/INDENT]
[INDENT]Syntax for setting log level seems not to work, except for default level of *low*[/INDENT]

```

sudo ufw logging off

```
Again just checking
```

sudo ufw status verbose
Status: active
Logging: off
....

```
Try to turn on logging and set log level in one command
```

sudo ufw logging on high

```
Checking
```

sudo ufw status verbose
Status: active
Logging: on (low)

```
I found I could only set the log level to higher than low with 2 commands.
First turn logging on
```

sudo ufw logging on

```
Then set a higher level
```

sudo ufw logging medium

```

While I'm here I might mention the other inconsistency I came across in the use of the pre-defined application rules for SAMBA.

The SAMBA manual clearly states these ports are used by SAMBA (smbd & nmbd) as referenced by kamaji792 in this post [Firewall & ports]("http://ubuntuforums.org/showthread.php?t=1432635#2")
> 
Port 135/TCP - used by smbd
Port 137/UDP - used by nmbd
Port 138/UDP - used by nmbd
Port 139/TCP - used by smbd
Port 445/TCP - used by smbd

Yet the Samba application rule omits port 135, which BTW is Microsoft Remote Procedure Call (RPC) service. 

```

sudo ufw app info Samba
Profile: Samba
Title: LanManager-like file and printer server for Unix
Description: The Samba software suite is a collection of programs that
implements the SMB/CIFS protocol for unix systems, allowing you to serve
files and printers to Windows, NT, OS/2 and DOS clients. This protocol is
sometimes also referred to as the LanManager or NetBIOS protocol.

Ports:
  137,138/udp
  139,445/tcp

```

More info from [Gibson Research Corporation]("http://www.grc.com/port_135.htm")

> 
Name: 	dcom-scm
Purpose: 	DCOM Service Control Manager
Description: 	Microsoft's DCOM (Distributed, i.e. networked, COM) Service Control Manager (also known as the RPC Endpoint Mapper) uses this port in a manner similar to SUN's UNIX use of port 111. The SCM server running on the user's computer opens port 135 and listens for incoming requests from clients wishing to locate the ports where DCOM services can be found on that machine.


---

### Post by evilsectoid on 2011-10-15
> **tebbens said:**
> Using ufw, here is mine....it works great.

sudo ufw allow proto udp from 192.168.1.0/24 to any port 137
sudo ufw allow proto udp from 192.168.1.0/24 to any port 138
sudo ufw allow proto tcp from 192.168.1.0/24 to any port 139
sudo ufw allow proto tcp from 192.168.1.0/24 to any port 445

i like this one :D

---

