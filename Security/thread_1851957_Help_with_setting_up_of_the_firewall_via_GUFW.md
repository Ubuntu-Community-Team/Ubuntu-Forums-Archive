---
title: "Help with setting up of the firewall via GUFW"
date: 2011-09-29
forum: Security
---

### Post by PeteAsdf on 2011-09-29
Hi guys,

Relatively new to Ubuntu. 
I wanted to set the iptables rules via GUFW on my PC (a typical host PC at home)- basically ensure the maximum security and only allow the basic ports:

HTTP, HTTPS, DNS, FSTP, SSH (do I need this one for FSTP?) and ports for Skype, KTorrent and a PS3 server (5001). Can you have a look at the attached configuration and let me know if I'm doing this all wrong? (Hope not!)

Thx

---

### Post by dino99 on 2011-09-29
there are nice tools to do that smootly without headache

- set ufw as default and activate it at startup
- install these packages with synaptic: pgld, pglcmd, pgl-gui
from this ppa to add to synaptic:
[https://launchpad.net/~jre-phoenix/+archive/ppa](https://launchpad.net/~jre-phoenix/+archive/ppa)
( the default settings are good enough here too, set it to start at logon)

---

### Post by oldos2er on 2011-09-29
Thread moved to Security Discussions.

---

### Post by jre on 2011-09-29
err, I don't think PeteAsdf really asked for pgl, which is a tool to block traffic based on huge IP blocklists. Allowing ports in pgl is possible but normally just adds an iptables rule with target "RETURN" - thus traffic gets ignored by pgl, and the system's other iptables rules apply.

---

### Post by collisionystm on 2011-09-29
> **PeteAsdf said:**
> Hi guys,

Relatively new to Ubuntu. 
I wanted to set the iptables rules via GUFW on my PC (a typical host PC at home)- basically ensure the maximum security and only allow the basic ports:

HTTP, HTTPS, DNS, FSTP, SSH (do I need this one for FSTP?) and ports for Skype, KTorrent and a PS3 server (5001). Can you have a look at the attached configuration and let me know if I'm doing this all wrong? (Hope not!)

Thx


Unless you plan on RECIEVING http, https, dns, fstp, or ssh traffic from another machine, you do not need to open these ports. It sounds like you only need to open the port for your PS3. Your firewall will automatically open ports for services that your computer initiates as an outbound connection...aka torrent, http, https...etc. Do you follow?

---

### Post by collisionystm on 2011-09-29
Just saw your screen shot, YOU DO NOT WANT TO ALLOW THAT TRAFFIC IN. Like I said, Only your PS3. You are opening holes in your firewall to the outside world. If you want to make sure that your computer will only communicate on the ports that you specify, you need to edit your Outbound policies, NOT inbound.

---

### Post by PeteAsdf on 2011-09-29
Thanks a lot collisionystm!!
You probably saved my system from being hacked. [-o<

---

### Post by collisionystm on 2011-09-29
> **PeteAsdf said:**
> Thanks a lot collisionystm!!
You probably saved my system from being hacked. [-o<

I try :)

---

