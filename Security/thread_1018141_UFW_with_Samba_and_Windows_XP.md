---
title: "UFW with Samba and Windows XP"
date: 2008-12-21
forum: Security
---

### Post by Kissell on 2008-12-21
Okay, so I am having a firewall problem using ufw on Ubuntu.

I have no idea why, from what I know and what I've read, I have the ports open that samba and windows shares need, yet from my Ubuntu server I cannot open windows xp file shares unless I type "ufw disable"

Here is what my "ufw status" currently is (i have already tried opening ports 135 thru 139 and 445 on both UDP and TCP from anywhere, but no luck).

Firewall loaded

To                         Action  From
--                         ------  ----
445:tcp                    ALLOW   Anywhere
139:tcp                    ALLOW   Anywhere
138:udp                    ALLOW   Anywhere
137:udp                    ALLOW   Anywhere
135:tcp                    ALLOW   Anywhere

Am I missing something?  Is the computer doing exactly what I'm telling it to do, and that's not enough?  or is it buggy?  I normally don't use ufw, but thought i'd give it a shot on this box.

---

### Post by Kissell on 2008-12-21
Hmmm...  this is interesting...  I thought i can browse windows shares from ubuntu when ufw is disabled...  but can't when it's enabled...  

But that's not entirely true...  if I connect to a windows share while ufw is disabled, then ubuntu will prompt me for the password, then if I enable ufw I'll be able to use that share I've already entered my password for.

So, ufw is setup right to use windows shares, it works if the password is cached, its killing something related to passing the password...  hmm...

---

### Post by Kissell on 2008-12-21
Okay, so with the firewall disabled I run netstat on the computer I'm trying to connect to, let's say it's 192.168.1.101 (some IPs may be changed to protect the identities of the local network) anyway, it gives me a list of tcp ports in the 30000 range that it needs for this to work...  WTF!?  it's like microsoft is just randomly picking tcp high ports to serve its shares on...  why does that surprise me?  I vaguely remember this from the days I had windows servers.

netstat -an|grep 192.168.1.101

tcp        0      0 192.168.1.5:37003       192.168.1.101:445       TIME_WAIT  
tcp        0     12 192.168.1.5:139         192.168.1.101:1972      ESTABLISHED
tcp        0      0 192.168.1.5:36998       192.168.1.101:445       TIME_WAIT  
tcp        0      0 192.168.1.5:39388       192.168.1.101:445       ESTABLISHED
tcp        0      0 192.168.1.5:37002       192.168.1.101:445       ESTABLISHED
tcp        0      0 192.168.1.5:445         192.168.1.101:4055      ESTABLISHED
tcp        0      0 192.168.1.5:37001       192.168.1.101:445       TIME_WAIT  
tcp        0      0 192.168.1.5:38872       192.168.1.101:139       ESTABLISHED

---

### Post by Nepherte on 2008-12-22
The high number ports are so called dynamic ports ( > 1023) and are dynamically being used by programs that are not system services. It's perfectly normal that you have them.

You only have to open those ports when *another* pc tries to acces *your* shares: they are so called incoming connections. You don't have to open those ports when you are trying to access *another* pc's files: they are so called outgoing connections. In fact, I believe you don't even need samba to access a pc's shares, only smbclient.

You can verify all of this in the netstat output you provide. Your pc, that uses a dynamic port, tries to access the remote pc's share. The service that provides this sharing functionality listens on port 445.

On a default ubuntu installation, no outgoing connection is being blocked (something ufw can't do anyways, unless you digg into the configuration files manually). That same default ubuntu installation will accept every incoming connection but, since there are no services installed listening to incoming connections, there won't be any.

---

### Post by Kissell on 2008-12-22
I agree with what you've said.  However, I have a conundrum, based in a reproducable fact.

When I disable ufw I can browse from this ubuntu box to windows shares...  when I enable ufw I cannot (unless I've already connected to them once and entered the password while ufw was disabled)

Because of this, I am 100% positive that UFW is the problem.  It must be treating authentication communication received back from that windows PC as incoming connecitons that are denied.

---

### Post by Nepherte on 2008-12-22
Ufw probably is the problem, I agree. I just wanted to point out that you didn't have to open those ports and the problem wasn't related to ports.

[QUOTE=Kissel]When I disable ufw I can browse from this ubuntu box to windows shares... when I enable ufw I cannot (unless I've already connected to them once and entered the password while ufw was disabled)[/QUOTE]
That's because the connection has already been established. When you enable ufw afterwards, I believe it only deals with new connections, not established ones.

I believe the guilth probably lies with ufw blocking ping requests. Since security by obscurity doesn't work, you might as well enable it and see how it works out with your problem: [https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw#Enable%20PING](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw#Enable%20PING)

---

### Post by Kissell on 2008-12-22
icmp requests were already setup like that post suggested...  

i'm at a loss...

---

