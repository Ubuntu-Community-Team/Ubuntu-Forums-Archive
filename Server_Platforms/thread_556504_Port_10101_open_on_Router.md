---
title: "Port 10101 open on Router?"
date: 2007-09-21
forum: Server Platforms
---

### Post by rbmorse on 2007-09-21
I was playing with some of the bright shiny in Gutsy today and opened system > administration > network tools for the first time.  One of the tabs is labeled "port scan" so I pointed it at my Belkin N1 Wireless A/P router (192.168.2.1).   NAT is enabled. The scan reported that port 80 is open, which I anticipated, but also that port 10101 was open as well, which I did not anticipate. 

I will profess ignorance here, but a Google indicated that port 10101 is associated with a trojan BrainSpy that contains a key logger, among other things.  I'm not particularly concerned as I don't see any evidence that BrainSpy is a Linux vulnerability.  There is a residual XP installation on the network, but it isn't used very often and I have to check that box for infections, but I am a bit confused why a port scan of a bleeping router would show that port open with only a Linux box active on the LAN side of the net?

Can someone help me understand this?

---

### Post by James79 on 2007-09-22
Having your router reporting that 10101 is open does not mean that a client behind its firewall is actually listening on that port, nor does it mean that this port is forwarded (from the internet to an internal server).

The fact that it reported 10101 which is used by some obscure virus is probably just a coencidence.

One useful tool in this situation is actually telnet. Using it you can connect to a server on any port and it'll dump the server's response to your screen. Often that'll give you some clues.

```
telnet 192.168.2.1 10101
```

What does that give you?

---

### Post by rbmorse on 2007-09-23
It reports "Connection Refused" and in very short, order, too. 

Thanks for the info about telnet.

---

### Post by netlogic on 2007-09-24
look into a program called, netcat. it is part of a default installation.

a port number is a port number. just like i can run my torrents on port 10101 if i wanted to. some ports are static to certain client applications, that's all that means.

---

### Post by James79 on 2007-09-24
> **rbmorse said:**
> It reports "Connection Refused" and in very short, order, too. 

Excellent. That means that nothing is actually listening :)

---

### Post by andymcc on 2008-04-08
nmap uncovered the same on my router (was expecting a port to be open but didn't know what it would be).
In my case it was Mediatomb, a uPNP mediaserver that had opened the port.  Killing the process closed the port.

---

### Post by mechgt on 2008-04-12
I just scanned my Belkin F5D7231-4 v1213 wireless router, and port 10101 reported open here too.  I'm able to telnet to the switch as below

```
user@puter:~$ telnet 192.168.2.1 10101
Trying 192.168.2.1...
Connected to 192.168.2.1.
Escape character is '^]'.
```

and just sits there.

If I escape out (Ctrl+], then ENTER) and type 'status', it says that I'm connected, but anytime I enter anything, it quickly closes the connection.  I want to put DD-WRT on this router, but not sure if I can or not (post on [DD-WRT and similar Belkin router]("http://www.dd-wrt.com/phpBB2/viewtopic.php?t=11631")).

---

