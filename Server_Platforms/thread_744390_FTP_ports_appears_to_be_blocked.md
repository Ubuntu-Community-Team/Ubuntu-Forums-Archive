---
title: "FTP ports appears to be blocked?"
date: 2008-04-03
forum: Server Platforms
---

### Post by adamitj on 2008-04-03
Hello there!

I set an old machine (Athlon XP 1800+ with 256 MB RAM and 80 GB IDE disk) as a WebServer, just to work as FTP and Apache server for internal applications be accessed over internet - usefull when we are visiting our customers.

After a extensive search over the Linux flavours, my choice was Ubuntu Server 7.10, wich shows itself as a very good performance choice and we all agreed in their use.

The FTP server still running and working on another machine, for inside (LAN) and outside (WAN). This old server runs openSUSE 10.2 and proFTPd.

Then I set the new machine (with Ubuntu Server 7.10) with vsftpd getting from official repository (apt-get install vsftpd), and made it work on LAN. Local access is fine. Everything works. But, even if I drop out the old server with openSUSE, and apply the same IP to the new server with Ubuntu, I can connect only locally.

This is gaving me nuts, once all port forward in router is ok, the old server still running, but ubuntu appears to deny any connection from the WAN.

In fact, I can connect the web *FROM* the ubuntu server, but not from outside to inside.

What could be happening? All the Ubuntu firewall and iptables are the default from installation.

---

### Post by angelmartinezn on 2008-04-03
I had the same problem, but in my case with shorewall firewall. It was solved when I opened not olny 21 tcp port on shorewall config, but besides ports 61000 to 62000 (ports configured on shorewall to be passive ports). The router only have port 21 forwarded.

Hope this will help you...

---

### Post by adamitj on 2008-04-03
Thanks angelmartinezn, but I have no other firewall installed than the default wich came with ubuntu packages, and there is no iptables entries defined...

Another suggestion?

---

### Post by Dr Small on 2008-04-03
How do you define "local" ?
Is this from the local machine, or the local network?

Also, just for assurance, let's take a look at IPtables:
```
sudo iptables -L
```

Expecially the part that says:
> Chain INBOUND 

Just to help diagnose the problem, of course.

---

### Post by angelmartinezn on 2008-04-03
One thing you can do is sniff a connection using wireshark (old ethereal), this would give you an idea of what ports and how is the connection in your local lan, and (the most important) how it differs from the connection from the wan segment.

---

### Post by Dr Small on 2008-04-03
You can also run nmap against the machine to check open ports, but don't run it on the local machine.

---

### Post by adamitj on 2008-04-04
Oh man... the server now is malfunctioning... appears to be the power supply.

I called hardware support assistance and they toke the tower for maintenance.

I'm waiting the server to return for run the iptables command, but I have done it before, and it came with no entries on INPUT or OUTPUT. It is like the defaults exactly as if I have done the Ubuntu Server installation.

---

### Post by smileypaul on 2008-04-04
Does it connect at all? 

I would run an  nmap -P0 -vvvv -p21 externalipaddress

That will tell you if the port is accessible from the outside world.

If you can connect, but cannot retrieve a LIST, its a passive problem.

---

### Post by adamitj on 2008-04-04
Ok, through LeechFTP from outside world (WAN), it says:

"Socket error: no connection".

But I'm thinking about... if it is a passive mode error, why ProFTPd in the openSuse Server is running perfectly? Passive mode uses TCP connection through port 80?

Last time I remember to change the forward ports 20 and 21 to the new server's IP, when I did the last test, but port 80 still pointing to the old server.

For knowledgement:
OLD = openSUSE Linux - ProFTPd - IP 192.168.100.250
NEW = Ubuntu Server - vsFTPd - IP 192.168.100.2

At the router, the port forward in my last un-successfull was like this (now all ports are set to OLD server):
Port 8080 --> 192.168.100.250
Port 80 --> 192.168.100.250
Port 20 --> 192.168.100.2
Port 21 --> 192.168.100.2
Port 22 --> 192.168.100.250
Port 23 --> 192.168.100.250

There could be a error on passive mode only if ProFTPd is set with passive mode OFF, but really I don't know how to identify this.

I just set vsFTPd, and I just know that it is working when accessed by local network (inside the same IP mask, that means all the PCs with IP 192.168.100.***), but over the modem ADSL do not (wich one is the router).

---

### Post by adamitj on 2008-04-14
Hello again, my dear comrades!

I would like to thank everyone who helped me to solve this problem.

After a few sets on the routers, I found the problem. Each server was deployed with two ethernet cards, one to LAN (192.168.100.xxx) and another to WAN (10.0.0.xxx).

The old model doesn't care after all now. The problem was in the connection to the main router, wich one was plugged into the LAN switch, but with the IP set to the WAN router's network.

It was a very badly projected infrastructure, made by the old IT technician.

This proofs the power of Ubuntu again. It was exceptionally perfect, but there was too many workarounds in physical model wich ones caused the socket errors.

Thanks everybody. Problem solved!

---

