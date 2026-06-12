---
title: "How secure is Ubuntu? a general question"
date: 2007-12-27
forum: Server Platforms
---

### Post by akimatsu123 on 2007-12-27
How secure is Ubuntu 7.10 (gutsy)? compared to xp?

i understand that since all programs are open source, it would be difficult to hide a spyware in a program. but how about protection against hackers? since it's an open source it worries me a little. 

is ubuntu 7.10 secure upon install? (i.e. no virus scan, firewall, extra configuration. just installed and started using)

if not, what steps should i take to secure it?

thanks in advance

---

### Post by Znort_Ubern00b on 2007-12-27
you do have a firewall installed called iptables(its command line programme)

if you install firestarter from synaptic this gives you a gui that is fairly straight forward for firewall.

linux as a whole does not require av software but you can get avg for linux as well as avast if you really want, think you can find avast in synaptic too if not there are many howtos on the forum.

---

### Post by jken146 on 2007-12-27
All ports are closed by default, so there really is no need to do anything in firestarter (unless you want to open something up).

You don't need an anti-virus program (waste of resources).

Check out the Servers & Security forum if you're interested in learning some more, in particular this: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by akimatsu123 on 2007-12-27
thanks a lot. i will check it out

---

### Post by Linuxratty on 2007-12-27
using Linux,you will find your paranoid level will drop like a rock.

---

### Post by (((X))) on 2007-12-28
Installing firefox opens port 80 in kubuntu( hackerwatch.org/probe).
Maybe firestarter will close it.I don't know..because I do not use firestarter of guarddog now..

---

### Post by bluevoodoo1 on 2007-12-28
If you're only installing applications through Synaptic, then you should be fine.

---

### Post by Steveway on 2007-12-28
> **(((X))) said:**
> Installing firefox opens port 80 in kubuntu( hackerwatch.org/probe).
Maybe firestarter will close it.I don't know..because I do not use firestarter of guarddog now..

But if you close it then Firefox wouldn't work. That is nothing to worry about.
Just go ahead and use it, no need to worry about these Windows-ways of security.

---

### Post by ingram on 2007-12-28
The biggest threat to your Ubuntu system is sitting at your computer.

Read the forum warnings about malicious code, and pay attention to commands you use and what you install. 

Also make sure to keep your system up to date. :guitar:

BTW Port 80 is the port your computer uses to listen for HTTP. So there really is no reason to worry about that port.

---

### Post by p_quarles on 2007-12-28
> **(((X))) said:**
> Installing firefox opens port 80 in kubuntu( hackerwatch.org/probe).
Maybe firestarter will close it.I don't know..because I do not use firestarter of guarddog now..
No, it doesn't. Contrary to what someone else said, it's actually the fact that *no* ports are closed by default. If you scan the ports, they will be listed as open. That in itself doesn't make the system insecure, though, because there are no services running on those ports. If a port is open, but no program has the ability to respond to a request on that port, the port is as good as closed.

> **Steveway said:**
> But if you close it then Firefox wouldn't work. That is nothing to worry about.
Just go ahead and use it, no need to worry about these Windows-ways of security.
Firefox doesn't use port 80. Currently, my version is connected via ports 33518, 33522 and 34730. Web servers use port 80.

---

### Post by K.Mandla on 2007-12-28
Moving to Servers and Security.

---

### Post by jas0 on 2007-12-28
> **akimatsu123 said:**
> How secure is Ubuntu 7.10 (gutsy)? compared to xp?

i understand that since all programs are open source, it would be difficult to hide a spyware in a program. but how about protection against hackers? since it's an open source it worries me a little. 

is ubuntu 7.10 secure upon install? (i.e. no virus scan, firewall, extra configuration. just installed and started using)

if not, what steps should i take to secure it?

thanks in advance

The bottom line is that even if Ubuntu and Windows XP/Vista were equal in every other respect, you simply do not have the user base with Ubuntu worthy of exploiting for profit. Also, it can be safely said (after looking at the OS X) that we can grow 10x times before we even have to start worrying about the garden variety of evil doers on the internet going after our machines en masse. 

I'm not saying that the former is the case (i.e. ubuntu = windows), just making the point that Ubuntu is miles ahead security-wise. There is even no need to go into the argument of why open source is better for security. All you need to do is just look at what's going on out there in the field.

Also, while Windows is completely "harden-able," most everyday users are stuck in [_this_]("http://port79.org/2007/12/02/spyware-removal/") situation.

---

### Post by aysiu on 2007-12-29
Read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by (((X))) on 2008-01-27
I just installed limewire.deb made for ubuntu, do I need a firewall now?
I scanned my computer on nmap-online.com, hackerwatch.org/probe, gcc/shieldsup and pcflank, I done all tests, no open ports were found.

I don´t find firestarter userfriendly, since linux has iptables..and I often switch between wifi an ethernet, so I had to set the right interface all the time using firestarter.

ps: I´m behind the router, and don´t have server apps installed.
Is it better if I setup firestarter, In this situation?:confused:

---

### Post by koenn on 2008-01-27
> **p_quarles said:**
>  Contrary to what someone else said, it's actually the fact that *no* ports are closed by default. If you scan the ports, they will be listed as open. 

?

I scanned an almost  default Ubunt 6.06 (added sshd) and this is what it says :
```

kdunix:~# nmap -sS -sV 192.168.1.113

Starting Nmap 4.11 ( http://www.insecure.org/nmap/ ) at 2008-01-27 18:29 CET
Interesting ports on 192.168.1.113:
Not shown:** 1679 closed ports**
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 4.2p1 Debian 7ubuntu3.2 (protocol 2.0)

Service Info: OS: Linux

Nmap finished: 1 IP address (1 host up) scanned in 4.120 seconds
kdunix:~#


```

---

### Post by erginemr on 2008-01-27
For those, who would like a secure remote scan of their posts, I would suggest Shields Up!, a well-known web service to cross-check network security of a client machine:
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

If all your ports are either closed or stealth, then you can rest assured that your system is secure. 

Having Firestarter installed as a frontend to iptables is a good thing, though.

Besides the network security, you can rest assured that native linux viruses are virtually non-existent. 

The story however is different when it comes to rootkits, advanced malicious programs, that are run as hidden from your system. To eliminate the possibility of having rootkits ins your system, you can install "chkrootkit" or "rkhunter" from Synaptic and do regular checks with these from the command line.

---

