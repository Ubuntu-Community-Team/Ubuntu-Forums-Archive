---
title: "Large amount of open ports"
date: 2007-06-06
forum: Server Platforms
---

### Post by elektronisch on 2007-06-06
Hello,

I'm not sure why I have so many open ports running after I installed ubuntu.  Most of them immediately close when I telnet into them.  Can anyone help me?

PORT      STATE SERVICE
1/tcp     open  tcpmux
11/tcp    open  systat
15/tcp    open  netstat
26/tcp    open  unknown
53/tcp    open  domain
79/tcp    open  finger
111/tcp   open  rpcbind
119/tcp   open  nntp
139/tcp   open  netbios-ssn
143/tcp   open  imap
445/tcp   open  microsoft-ds
540/tcp   open  uucp
635/tcp   open  unknown
953/tcp   open  rndc
1080/tcp  open  socks
1524/tcp  open  ingreslock
2000/tcp  open  callbook
5900/tcp  open  vnc
6667/tcp  open  irc
12345/tcp open  NetBus
12346/tcp open  NetBus
27665/tcp open  Trinoo_Master
31337/tcp open  Elite
32771/tcp open  sometimes-rpc5
32772/tcp open  sometimes-rpc7
32773/tcp open  sometimes-rpc9
32774/tcp open  sometimes-rpc11
54320/tcp open  bo2k

---

### Post by Mr. C. on 2007-06-06
The lower numbered ports (<1024) are well known services (eg. DNS, rpcbind (aka portmap), imap).  Your system is configured with many servers, so those ports will be opened when the service starts.

Start from the top, and learn what each service is.  


The other ports you will have to hunt down individually, if they are not commonly used.  For example, VNC (virtual desktop/remote desktop) uses 5900 by default.  But 32774 is a free port, currently used by some program.  To determine which, use the command:

lsof -i

will give you the command using the port and its basic network connection information.

MrC

---

### Post by nixfaced on 2007-06-06
Are you portscanning from somewhere outside your network?  I've only seen output like that in 2 cases:  router / access points with port-triggering enabled, and some IDSs.

---

