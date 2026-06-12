---
title: "Setting up Portsentry"
date: 2008-03-30
forum: Security Discussions
---

### Post by apokkalyps on 2008-03-30
I'll soon be running some servers off of my Ubuntu-Desktop and I'm trying to put some security in place in advance.  I discovered portsentry and installed it through synaptic (didn't build).

At first I flipped out because installing portsentry changed my "nmap localhost" from this:

> 
$ nmap localhost

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-03-29 09:13 CDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1687 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
2049/tcp open  nfs
3306/tcp open  mysql
6881/tcp open  bittorent-tracker

Nmap finished: 1 IP address (1 host up) scanned in 0.202 seconds

to this:

> $ nmap localhost

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-03-30 17:25 CDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1666 closed ports
PORT      STATE SERVICE
1/tcp     open  tcpmux
11/tcp    open  systat
15/tcp    open  netstat
22/tcp    open  ssh
25/tcp    open  smtp
79/tcp    open  finger
80/tcp    open  http
111/tcp   open  rpcbind
119/tcp   open  nntp
139/tcp   open  netbios-ssn
143/tcp   open  imap
445/tcp   open  microsoft-ds
540/tcp   open  uucp
631/tcp   open  ipp
635/tcp   open  unknown
1080/tcp  open  socks
1524/tcp  open  ingreslock
2000/tcp  open  callbook
2049/tcp  open  nfs
3306/tcp  open  mysql
6667/tcp  open  irc
6881/tcp  open  bittorent-tracker
12345/tcp open  NetBus
12346/tcp open  NetBus
27665/tcp open  Trinoo_Master
31337/tcp open  Elite
32771/tcp open  sometimes-rpc5
32772/tcp open  sometimes-rpc7
32773/tcp open  sometimes-rpc9
32774/tcp open  sometimes-rpc11
54320/tcp open  bo2k

Nmap finished: 1 IP address (1 host up) scanned in 0.228 seconds


Installing portsentry added tons of open suspicous ports, but I think that is mostly sorted out.  At first I thought I was totally comprimised, and I was flipping out about it.  It was discussed in this thread.
**[http://ubuntuforums.org/showthread.php?p=4613165#post4613165]("http://ubuntuforums.org/showthread.php?p=4613165#post4613165")**
I think those are just opened to intercept attacks.

A few things still arent adding up, and maybe someone smarter than me can explain why:)


[COLOR="Red"]Why does it matter if I nmap localhost or nmap my external IP address?[/COLOR]  Unless there is some firewall in the way or something?  Doesnt the external IP get resolved back to the same place through routing?

When I nmap my external IP it gives nothing.  The host looks invisible to nmap unless I use the -P0 option and then it just thinks all the ports are closed.

> $ nmap [external IP address]

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-03-30 17:25 CDT
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0
Nmap finished: 1 IP address (0 hosts up) scanned in 4.009 seconds


> $ nmap [external IP address] -P0

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-03-30 17:25 CDT
All 1697 scanned ports on 66-169-217-150.dhcp.dntn.tx.charter.com (66.169.217.150) are closed

Nmap finished: 1 IP address (1 host up) scanned in 51.435 seconds



Yet when I "nmap localhost", I get the list of open suspicious ports (in the second quote from the top).  [COLOR="Red"]Is this lenghty output from "nmap localhost" because 127.0.0.1 is in my portsentry.ignore?  [/COLOR]

Even though blocking scans is the point of portsentry, I notice my configureation file currently has the settings:
> # 0 = Do not block UDP/TCP scans.
# 1 = Block UDP/TCP scans.
# 2 = Run external command only (KILL_RUN_CMD)

BLOCK_UDP="0"
BLOCK_TCP="0"
[COLOR="Red"]
Blocking is off by defualt, so why is it blocking the nmap of the external IP at the moment?  Shouldnt I have to set those to 1 for that?[/COLOR]

I don't understand why I'm getting nothing on an external IP portscan with the current configuration, and I also dont understand why I'm getting contrarily something on an internal portscan.....


[COLOR="Red"]How can I restart portsentry it if I update my config file?[/COLOR]


Also I can't find where the stuff is logged to.  I have been through multiple guides and tutorials and maybe I'm missing somethnig but they always go like this:
> 
*from: [http://www.securityfocus.com/infocus/1586](http://www.securityfocus.com/infocus/1586)*

Once PortSentry has been started, the next step is to test the install. This can best be achieved by logging into another host and connecting to one of PortSentry's monitored ports. A properly installed and operating PortSentry should log a message similar to the one below:

May 26 22:54:50 rashi portsentry[3111]: attackalert: Host 10.16.17.1 has been 
blocked via wrappers with string: "ALL: 10.16.17.1"
May 26 22:54:50 rashi portsentry[3111]:

 attackalert: TCP SYN scan from host 
10.16.17.1/10.16.17.1 to TCP port: 2000 from TCP port: 4427


They always say "after this happens youll get logs like this" but I can't find a single guide that doesn't happen to omit the detail of where that logfile is saved.  [COLOR="Red"]Can anyone tell me where the logfile is?[/COLOR]

Also, that particular quote implys portsentry reacts to individual connection attempts on the trap-ports, as well as scans.  [COLOR="Red"]Is that true that it reacts to scans AND single connections?[/COLOR]

As always thanks for your help everyone.

---

### Post by pseudo-random on 2008-03-30
Your logs should be with all the other logs in /var/log
As for the ports/interfaces. Everything seems ok from what I can see.
localhost is just a loopback and is trusted as such so thats why you can see dozens of open ports. The fact that your external ports are stealthed is good. Unless of course you're trying to open HTTP, FTP etc for external access.

I recall a thread on another forum once where a kid was port scanning a server called localhost. He was pleased to note it was running the same OS and services as himself...

---

### Post by apokkalyps on 2008-03-30
haha :lolflag:

I guess I'm not sure exactly what is implied by the concept of "loopback" other than it points back to the local machine....but it's still a tcp/ip connection, why would an application react differently to it?  

Also, I do intend to open HTTP, SFTP, and SSH etc for external access.  I expected I would be able to connect to them still, but not come up in a scan, but as of right now portsentry is blocking them.  Even though I read in the documentation that it is supposed to ignore ports that are actually running services.  This raises another question:[COLOR="Red"]  Why is it blocking my legitmate external ports?[/COLOR]

---

