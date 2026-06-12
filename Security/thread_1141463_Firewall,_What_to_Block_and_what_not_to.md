---
title: "Firewall, What to Block and what not to?"
date: 2009-04-28
forum: Security
---

### Post by Shady3D on 2009-04-28
hi all, i am confused right now with firewall configuration, i understand IP-tables, and know how to use Firestarter, but i don't know what to block and what not to.

i use Internet for browsing, samba sharing, chatting (irc, and other voIP nad regular IM), download (browser download, APT-GET or torrents), and other applications like drop-box.
[U]
my configurations[/U]
 
**Inbound: **
*from host:* allow from 192.168.1.3
*from service:* bit-torrent (6881-6889), smb (137-139 455), http (80), pop3 (110), https (443)

**Outbound: **
*mode:* Blacklist

Firestarter notify me when a service is blocked, and i don't know if its blocking something important or not, and if it slowing down my connection.

i would like to know if my configuration is good or not, and if there anything that i can add to this configuration or remove, also if any body got an article where i can learn more about this, i would like to read it too.

also i want to know about, how to check if i am secure, or in other way how to know that i am protected, is there a way do do this.

---

### Post by dragos_iliescu_2005 on 2009-04-28
Hello there,
generally speaking a firewall is set up like all to outbound and filtered to inbound.
If correct setup is applied, no slowing is to be involved. If not correct setup applied, some "strange" connection it will be accepted by your system.
You said you understand IP tables. If so, I recommend you Shorewall.
Refer to this link for start [http://www.shorewall.net/]("http://www.shorewall.net/")

---

### Post by Shady3D on 2009-04-28
so what is the difference, i still don't know what to block and what not to, shorewall is just a tool, but any way thx for ur reply

---

### Post by dragos_iliescu_2005 on 2009-04-28
You right. Just follow the link. You will find there about how to setup your firewall. Is a good how-to in there.

By the way. I think you must understand about networking, services, IPs and so on. After that you can can start to build your firewall. But first question is how much you need it?

---

### Post by Shady3D on 2009-04-28
actually i went to the website and downloaded the firewall, but i a agree with u about learning more about the hole thing, but i don't have a good recourse to learn from, so if have any place to get me started that will be great

---

### Post by dragos_iliescu_2005 on 2009-04-28
In my case, Firestarter was the first. Depending on your needs, this could be the right solution for you or not.
I start to learn how-to about Firestarter - don't remember exactly location on the internet - but now I'm using Shorewall. Is more "accurate". In my case I discover that I was allow with Firestarter some ports, connections that normally shouldn't. But this is called learning. About Shorewall, I just sent you the link to the how-to with firewall. It was what I used to learned about. Other how-to you can found on internet, wiki generally.

Rule of thumb, your log file (/var/log/kern.log) will tell you how to configure the firewall depending on how many unwanted connections you actually have.

---

### Post by lovinglinux on 2009-04-28
> **Shady3D said:**
> hi all, i am confused right now with firewall configuration, i understand IP-tables, and know how to use Firestarter, but i don't know what to block and what not to.

i use Internet for browsing, samba sharing, chatting (irc, and other voIP nad regular IM), download (browser download, APT-GET or torrents), and other applications like drop-box.
[U]
my configurations[/U]
 
**Inbound: **
*from host:* allow from 192.168.1.3
*from service:* bit-torrent (6881-6889), smb (137-139 455), http (80), pop3 (110), https (443)

**Outbound: **
*mode:* Blacklist

Unlike Windows, you shouldn't be much worried about outgoing connections, unless you are a paranoid like me and want full control of your system. 

It seems that you have covered all the ports you need to allow incoming traffic, but you don't need to allow http, pop3 and https for incoming connections, unless you are running a web and a mail servers. Allowing outgoing connections is all you need to access the web and send e-mails. The torrent configuration is correct, since you will need to accept incoming connections from other peers. You might want to use another port range, between 49152 and 65535, because some ISP's throttle the connection on common torrent ports (6881-6889). You might also want to install [moblock](http://moblock-deb.sourceforge.net/) (mobloquer gui) to block ips from blocklists while torrenting. The samba  ports don't need to be open to everyone if you do not access your computer files from outside your LAN. If you only use samba between computers on your home, then you could allow the IP of the machines on your network instead of opening the port. Is less risky this way.

You might also want to block incoming icmp packets, which are essentially a probing connection, to check if you are connected or not. REJECTing icmp packets will return a message to the sender telling that you do not accept this type of packets, but if you want to be "stealth" then you should DROP incoming icmp packets. 

> **Shady3D said:**
> Firestarter notify me when a service is blocked, and i don't know if its blocking something important or not, and if it slowing down my connection.

You shouldn't be using Firestarter to monitor connections, because it requires root permission and there are some threads here that discuss flaws in Firestarter that would allow an attacker to take control of your machine. I'm not sure if this is just paranoia, but Firestarter is kind of old and not recommended anymore. There are other tools for monitoring connections and the recommended firewall manger now is ufw, which is installed by default. You can add the gui to control it, using the Add/Remove manager. Whichever you choose, you should use it just to setup the firewall rules, the close it. Iptables will do the work on the background.

For monitoring connections visit these: 

[http://ubuntuforums.org/showpost.php?p=7166253&postcount=26](http://ubuntuforums.org/showpost.php?p=7166253&postcount=26)
[http://ubuntuforums.org/showpost.php?p=7156014&postcount=13](http://ubuntuforums.org/showpost.php?p=7156014&postcount=13)

> **Shady3D said:**
> also i want to know about, how to check if i am secure, or in other way how to know that i am protected, is there a way do do this.

Use these:

[http://www.pcflank.com/scanner1.htm](http://www.pcflank.com/scanner1.htm)
[http://nmap-online.com/](http://nmap-online.com/)

If you are behind a router, then you probably don't need a firewall. I have a router with firewall, but I also like to add extra protection, specially while a port is open for p2p. I don't use any firewall manager, just moblock and my personal iptables rules.

To learn about iptables visit:

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)
[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

I also recommend reading the Ubuntu Security tutorial

[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

You can alos read Firestarter manual, which has some information about network and stuff:

[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)
[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

Good luck.

---

### Post by Shady3D on 2009-04-28
WOW thats amazing, and the funny thing the i was just switching from gufw to firestater to see the blocked traffic, and thx alot for ur help that was really helpful 

and i think the second link is broken

---

### Post by Shady3D on 2009-04-28
so how to make this thead solved

---

### Post by lovinglinux on 2009-04-28
> **Shady3D said:**
> and i think the second link is broken

Fixed.

---

### Post by brian_p on 2009-04-28
> **lovinglinux said:**
> 

You might also want to block incoming icmp packets, which are essentially a probing connection, to check if you are connected or not. REJECTing icmp packets will return a message to the sender telling that you do not accept this type of packets, but if you want to be "stealth" then you should DROP incoming icmp packets.

It is worth noting that DROPing packets allows someone to deduce a machine is connected to the net.

---

### Post by lovinglinux on 2009-04-28
> **brian_p said:**
> It is worth noting that DROPing packets allows someone to deduce a machine is connected to the net.

Yes, I know. Because of the delay. But the OP is probably a former Windows user, so I bet he would feel more safe when the port scanning services shows all ports as "stealth" instead of "closed".

---

### Post by brian_p on 2009-04-28
> **lovinglinux said:**
> Yes, I know. Because of the delay. But the OP is probably a former Windows user, so I bet he would feel more safe when the port scanning services shows all ports as "stealth" instead of "closed".

You could be right; but I would rather credit him with wanting to **be** safe (and know why) rather than **feel** safe.

---

### Post by lovinglinux on 2009-04-28
> **brian_p said:**
> You could be right; but I would rather credit him with wanting to **be** safe (and know why) rather than **feel** safe.

I agree, but I thought it was enough to get things working properly first. I didn't want to add this kind of info, to avoid confusion. Anyways, he probably know by now what we are talking about  :)

---

