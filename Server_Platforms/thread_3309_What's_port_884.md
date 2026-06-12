---
title: "What's port 884?"
date: 2004-11-05
forum: Server Platforms
---

### Post by HungSquirrel on 2004-11-05
What's Ubuntu using it for, and can I safely close it?

```
$ sudo nmap -sV localhost

Starting nmap 3.50 ( http://www.insecure.org/nmap/ ) at 2004-11-05 00:37 CST
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1655 ports scanned but not shown below are in state: closed)
PORT    STATE SERVICE VERSION
22/tcp  open  ssh     OpenSSH 3.8.1p1 (protocol 2.0)
111/tcp open  rpcbind 2 (rpc #100000)
631/tcp open  ipp     CUPS 1.1
884/tcp open  unknown

Nmap run completed -- 1 IP address (1 host up) scanned in 6.468 seconds
```

---

### Post by jdodson on 2004-11-05
it looks like it is an undefined port number.  i wouldnt worry too much about closing it, unless you break something then :grin:

[info here](http://www.grc.com/port_884.htm)

---

### Post by mr_ed on 2004-11-05
Funny... I have 22, 25, 111, 139, 445, 631, and 650 open.

The 650 is unknown.

How come there's so many services running?  Good thing I'm behind a hardware firewall.  Is there a GUI way to shut all this stuff off, or do I need to go into /etc/init.d and remove a few symlinks?

---

### Post by jdodson on 2004-11-05
[QUOTE=mr_ed]How come there's so many services running?  Good thing I'm behind a hardware firewall.  Is there a GUI way to shut all this stuff off, or do I need to go into /etc/init.d and remove a few symlinks?[/QUOTE]

no gui way to do it in the native ubuntu install, you 
[can do this though.](http://www.ubuntuforums.org/showthread.php?t=2728) strange that you have so many ports open, ubuntu by default should have no ports open. :?:

---

### Post by khc on 2004-11-06
[QUOTE=HungSquirrel]What's Ubuntu using it for, and can I safely close it?

```
$ sudo nmap -sV localhost

Starting nmap 3.50 ( http://www.insecure.org/nmap/ ) at 2004-11-05 00:37 CST
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1655 ports scanned but not shown below are in state: closed)
PORT    STATE SERVICE VERSION
22/tcp  open  ssh     OpenSSH 3.8.1p1 (protocol 2.0)
111/tcp open  rpcbind 2 (rpc #100000)
631/tcp open  ipp     CUPS 1.1
884/tcp open  unknown

Nmap run completed -- 1 IP address (1 host up) scanned in 6.468 seconds
```[/QUOTE]

nmap'ing localhost won't show you anything useful. Ubuntu by default has no open port _to_the_outside_world_. The results you get are ports that you can connect to from your own machine. In order to get the real result, you need to nmap your machine from some place else on the network.

---

### Post by HungSquirrel on 2004-11-06
I know.  I just want to know what service the port is for, and if I need the service running.

---

### Post by khc on 2004-11-06
[QUOTE=HungSquirrel]I know.  I just want to know what service the port is for, and if I need the service running.[/QUOTE]
 sudo netstat -l -p --numeric-ports -tcp

---

### Post by HungSquirrel on 2004-11-06
I just rebooted, and now the unknown port I have open is 664, which doesn't show up in the output of *netstat -l -p --numeric-ports -tcp*.

---

### Post by WW on 2004-11-07
I don't understand the technical details, but I bet the unknown port is connected to famd.  Try this sequence of commands:
```
sudo nmap -sS 127.0.0.1
pmap_dump
```
The first will probably show an open port whose "SERVICE" is "unknown".  In the output of the second, you will see that this port is associated with something called sgi_fam.  sgi_fam is connected to famd... somehow.   So this "unknown" port is normal.  Perhaps an expert could fill in the details...?

---

### Post by HungSquirrel on 2004-11-07
You were quite right.

---

### Post by mr_ed on 2004-11-11
[QUOTE=jdodson]no gui way to do it in the native ubuntu install[/QUOTE]

That's what I wanted to know.  Thanks.  :)
I have a Samba server running
The way to shut that off through the GUI is 
System Configuration - > Networking
enter sudo password
click the General tab
Uncheck "Enable Windows Networking"

That network tool is very neat.  I've been using Linux for at least a year, and I discovered it after installing Ubuntu.  I love the layout.  It all makes sense.

Perhaps ssh server should be added here as well?

[QUOTE=jdodson]strange that you have so many ports open, ubuntu by default should have no ports open. :?:[/QUOTE]

I also have an SSH server running, in addition to Samba (which opens 2 ports)... :)
CUPS is also installed.

Why Postfix is installed, I have no idea. :?
rpcbind?  (is that also needed by the Samba server?
The only one unaccounted for is the "unknown" one which is probably famd.

---

