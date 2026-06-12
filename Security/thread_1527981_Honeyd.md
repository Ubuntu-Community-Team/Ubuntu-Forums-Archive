---
title: "Honeyd"
date: 2010-07-10
forum: Security
---

### Post by iamgeniusrnti on 2010-07-10
OK, something seems terribly wrong here... here is my config file: 


create default 
set default personality "Microsoft Windows XP Home Edition" 
set default default tcp action reset 
set default default udp action reset 
set default default icmp action open 
add default tcp port 80 "/usr/share/honeyd/honeyd_kit-1.0c-a/scripts/win32/iis-0.95/iisemul8.pl" 
add default tcp port 139 open 
add default tcp port 137 open 
add default udp port 137 open 
add default udp port 135 open 
bind 192.168.1.200 default 
### Cisco router 
create router 
set router personality "Cisco IOS 11.3 - 12.0(11)" 
set router default tcp action reset 
set router default udp action reset 
add router tcp port 23 "/usr/share/honeyd/honeyd_kit-1.0c-a/scripts/router/cisco/router-telnet.pl" 
set router uid 32767 gid 32767 
set router uptime 1327650 
bind 192.168.1.201 router 
## Ftp
create template
set template personality "Linux kernel 2.4.19 (X86)"
set template uptime 0428938
add template tcp port 21 "/usr/share/honeyd/ftp.sh"
set template default tcp action block
set template default udp action block
bind 192.168.1.202 template

 
 
 
 
Here is how it starts: 
 
 
 
 
genius@ubuntu-server:/usr/share/honeyd$ sudo ./start-honeyd.sh  
+ honeyd -p nmap.prints -f honeyd.conf -x xprobe2.conf -a nmap.assoc -l /var/log/honeyd -d -i eth0 192.168.1.200-192.168.1.201 
Honeyd V1.5c Copyright (c) 2002-2007 Niels Provos 
honeyd[9723]: started with -p nmap.prints -f honeyd.conf -x xprobe2.conf -a nmap.assoc -l /var/log/honeyd -d -i eth0 192.168.1.200-192.168.1.201 
honeyd[9723]: listening promiscuously on eth0: (arp or ip proto 47 or (udp and src port 67 and dst port 6[IMG]http://www.honeyd.org/phpBB2/images/smiles/icon_cool.gif[/IMG] or (ip and (dst net 192.168.1.200/31))) and not ether src 00:b0:d0:b0:60:53 
honeyd[9723]: Running with root privileges. 
 
 
 
 
But whenever I try to get in, it simply kills the connection... aren't honeypots supposed to entertain people for a while?!? 
 
 
 
 
 
honeyd[9784]: Connection request: tcp (192.168.1.111:43715 - 192.168.1.201:23) 
honeyd[9784]: Killing attempted connection: tcp (192.168.1.111:51874 - 192.168.1.200:23) 
honeyd[9784]: Killing unknown connection: tcp (192.168.1.111:59443 - 192.168.1.200:80) 
honeyd[9784]: Killing unknown connection: tcp (192.168.1.111:59443 - 192.168.1.200:80) 
honeyd[9784]: Killing unknown connection: tcp (192.168.1.111:59443 - 192.168.1.200:80) 
honeyd[9784]: Killing unknown connection: tcp (192.168.1.111:59443 - 192.168.1.200:80) 
honeyd[9784]: Killing unknown connection: tcp (192.168.1.111:59443 - 192.168.1.200:80) 
 honeyd[13512]: Connection request: tcp (192.168.1.1:56678 - 192.168.1.201:23)
honeyd[13512]: Connection established: tcp (192.168.1.1:56678 - 192.168.1.201:23) <-> /usr/share/honeyd/honeyd_kit-1.0c-a/scripts/router/cisco/router-telnet.pl
honeyd[13512]: Connection dropped by reset: tcp (192.168.1.1:56678 - 192.168.1.201:23)
honeyd[13512]: Connection request: tcp (192.168.1.1:56679 - 192.168.1.201:23)
honeyd[13512]: Connection dropped by reset: tcp (192.168.1.1:56676 - 192.168.1.201:23)
honeyd[13512]: Connection dropped by reset: tcp (192.168.1.1:56679 - 192.168.1.201
 

 Am I missing something here?

---

### Post by wacky_sung on 2010-07-10
Check this out for honeypot as below.If you do not set it proper and your whole system can also be compromised.

[http://en.wikipedia.org/wiki/Honeypot_(computing](http://en.wikipedia.org/wiki/Honeypot_(computing))

---

### Post by iamgeniusrnti on 2010-07-10
> **wacky_sung said:**
> Check this out for honeypot as below.If you do not set it proper and your whole system can also be compromised.

[http://en.wikipedia.org/wiki/Honeypot_(computing]("http://en.wikipedia.org/wiki/Honeypot_%28computing"))

All that told me was general knowledge about honeypots... I need to know why mine isn't interacting with wouldbe attackers.  I really don't care if they compromise the system, it's a lonely isolated PE server.

---

### Post by Kinstonian on 2010-07-10
It's been a while since I've used honeyd, but are you using a port scanner to connect or using telnet?  Have you tried to connect to other services?

---

### Post by iamgeniusrnti on 2010-07-10
> **Kinstonian said:**
> It's been a while since I've used honeyd, but are you using a port scanner to connect or using telnet?  Have you tried to connect to other services?

OK got it--phew!  To answer your question I simply used telnet and FTP commands.

Turns out I had several syntax command errors.  If you want to bind a script trouble a port, you have to say "sh /full/path.sh" or "/usr/bin/perl /full/path.pl".  Also, every script, log file and lib must be chown'd to nobody:nobody.  Lastly, when you fired up the honeydews, it's better to specify the full path of each library you want to invoke.

It now answers to telnet, telnet smtp and FTP.  Solved.

---

### Post by tanveer on 2010-12-04
Hi there,

can you please tell me what command u used to connect to sample ftp.sh in honeyd?
Because I think there is a problem with the default script. Whenever I am giving the command
$ftp ipaddr 21
 It just asks for username and after giving username it says this username requires password and gives the ftp> prompt.
 Did u changed those sample scripts to make them work?

 thank you.

---

### Post by iamgeniusrnti on 2010-12-04
> **tanveer said:**
> Hi there,

can you please tell me what command u used to connect to sample ftp.sh in honeyd?
Because I think there is a problem with the default script. Whenever I am giving the command
$ftp ipaddr 21
 It just asks for username and after giving username it says this username requires password and gives the ftp> prompt.
 Did u changed those sample scripts to make them work?

 thank you.

LOL!  That's what it's supposed to do!

---

