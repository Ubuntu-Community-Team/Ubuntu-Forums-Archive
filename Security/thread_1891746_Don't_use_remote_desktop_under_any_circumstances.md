---
title: "Don't use remote desktop under any circumstances"
date: 2011-12-06
forum: Security
---

### Post by TGIF Tony on 2011-12-06
Running Ubuntu 10.04 2.6.32-36-generic-pae

I've seen a few threads on this forum warning people not to use Remote Desktop and I would just like to add weight to this advice.

I had installed some time ago the Remote Desktop application that is available in the Ubuntu Software Centre and was today, for the first time, trying to get a work XP laptop to control my Ubuntu laptop's desktop.

The Wireshark trace I was taking purely out of interest showed something very interesting, and worrying.

Upon firing up Remote Desktop, the first thing it does is a DNS query to find the IP of one "blog.jorgepereira.com.br". The returned IP is 189.38.80.51

There then follows a 3-way TCP handshake SYN, SYN ACK, ACK followed by some HTTP and a smidgen of HTTP/XML (POST /jorg/org.gnome.vino.service.php).

There is some more HTTP then the usual FIN, FIN ACK TCP tear-down.

Jorge is probably sunning himself somewhere on a delightful beach in Brazil (and I know there are many coz I've spent many years there doing the same) pondering in his next nefarious activity.

But Jorge, if you ever get to read this, get the heck out of my machine you tit. Remote Desktop is now un-installed and iptables will block the aforementioned IP from getting anywhere near it.

---

### Post by CharlesA on 2011-12-07
Check this [bug report]("https://bugs.launchpad.net/ubuntu/+source/vino/+bug/608701") as to why vino is "phoning home."

In any case, I wouldn't expose VNC to the internet unless it was tunneled over SSH and if I have SSH access, there are better ways to do a remote GUI then VNC.

---

### Post by Lars Noodén on 2011-12-07
> **CharlesA said:**
> In any case, I wouldn't expose VNC to the internet unless it was tunneled over SSH and if I have SSH access, there are better ways to do a remote GUI then VNC.

Which ways do you recommend?

---

### Post by CharlesA on 2011-12-07
> **Lars Noodén said:**
> Which ways do you recommend?
I either forward X over SSH or use FreeNX/NoMachine's NX server.

---

### Post by emiller12345 on 2011-12-07
> **CharlesA said:**
> I either forward X over SSH or use FreeNX/NoMachine's NX server.
I don't know if this is still relevant, but you may be careful about X11 forwarding over ssh.
[http://www.hackinglinuxexposed.com/articles/20040705.html](http://www.hackinglinuxexposed.com/articles/20040705.html)
The article sounds a little confusing, but it seems like you have to be careful.

---

### Post by CharlesA on 2011-12-07
> **emiller12345 said:**
> I don't know if this is still relevant, but you may be careful about X11 forwarding over ssh.
[http://www.hackinglinuxexposed.com/articles/20040705.html](http://www.hackinglinuxexposed.com/articles/20040705.html)
The article sounds a little confusing, but it seems like you have to be careful.
Thanks for the link. The article makes it sound like someone needs to have access to the server itself in order to sniff the Magic cookie and access a running X session.

Not sure tho.

---

### Post by matt_symes on 2011-12-07
Thanks for your link in post #2 CharlesA. Very informative.

---

### Post by CharlesA on 2011-12-07
> **matt_symes said:**
> Thanks for your link in post #2 CharlesA. Very informative.
No problem.

Google is my friend. ;)

---

### Post by Jive Turkey on 2011-12-07
> **CharlesA said:**
> Thanks for the link. The article makes it sound like someone needs to have access to the server itself in order to sniff the Magic cookie and access a running X session.

Not sure tho.

That's the impression I got too.  The take home lesson is that you may not want to use X11 forwarding in situations where you don't trust the admins of the server.  I can't really appreciate that it's that big of a distinction for using an untrusted host in general, where admins could abuse your account with or without a gui.

---

### Post by c.cobb on 2011-12-07
> **CharlesA said:**
> I either forward X over SSH or use FreeNX/NoMachine's NX server.

CharlesA, what is your take on [TeamViewer]("http://www.teamviewer.com/en/index.aspx")?
Thanks,

---

### Post by CharlesA on 2011-12-07
> **Jive Turkey said:**
> That's the impression I got too.  The take home lesson is that you may not want to use X11 forwarding in situations where you don't trust the admins of the server.  I can't really appreciate that it's that big of a distinction for using an untrusted host in general, where admins could abuse your account with or without a gui.

Aye. I have only used it with my home server. I have SSH access to my webhost, but I set it up so that I have a key that I use to connect and initiate the connection from my machine to their server in order to do backups so I don't have a passphraseless key to access my home server on an untrusted server.

That makes sense right? :D

> **c.cobb said:**
> CharlesA, what is your take on [TeamViewer]("http://www.teamviewer.com/en/index.aspx")?
Thanks,

I've used it before, but only for remote support. I don't think I've used it to access a GUI on my own machine tho.

---

### Post by TGIF Tony on 2011-12-08
Thanks, Charles for Post #2, and to others for suggesting alternatives to RDP, VNC etc.

OK, here's my take on this. Yes, there are many ways of skinning a cat but for a quick and simple solution to, for example, carrying out a presentation one someone else's machine whilst yours is in another location in the same office, VNC seemed like a quick and easy way to go.

What I hadn't anticipated (I was running Wireshark for an entirely uconnected reason and saw this quite by accident) was to see an application that I had opened going outside of the company LAN and contacting a device on another continent. This is unacceptable. Although my machine is behind a firewall and I have UFW running, the machine opens up an outbound HTTP flow allowing anything to come back via the same flow.

I don't buy the reasoning that it is necessary for the applicatiopn to "phone home" (using HTTP) to check anything that is application related. This is extremely naughty. The session I was trying to establish was on a private LAN between to peer machines on the same subnet.

These days, with the number of commercial transactions that are carried out from our machines, not to mention accessing internet banking sites, credit card web sites etc. alarm bells started to ring immediately. Anything could be posted back onto my machine.

Anyway, I will certainly be using one of the other methods going forward to establish secure connections between machines.

Cheers, Tony

---

### Post by CharlesA on 2011-12-08
I agree with you there. I would have thought there would be easier ways to tell if you have internet access or not. That being said, I don't know jack about programing so something that seems simple to me, might be quite complicated.

---

