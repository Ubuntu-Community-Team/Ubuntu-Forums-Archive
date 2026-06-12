---
title: "Open ports - step by step best practice...?"
date: 2015-10-02
forum: Security
---

### Post by x-michael-h on 2015-10-02
Hello all, still quite new to Ubuntu Server. So your valuable insight is welcomed and needed. I have tried to complete the following request from a developer with no luck.
> [INDENT]Can you please open these ports for both inband/output?
 
TCP 80
TCP 443
TCP 49152-65535     (range)
UDP 49152-65535     (range)
 
I'm currently using "no-auth" because turnserver was showing "unauthorized" even I was passing valid credentials. 
 
BTW, our main issue currently is to make sure it works with "--no-auth".[/INDENT]


I thought the default best way to do this from what I read was to do the following:

sudo ufw enable
sudo ufw allow (port#)

However Ranges and UDP it is asking for from & to if I remember correctly. But I need it completely open per the developer.

How can I accomplish this?

---

### Post by TheFu on 2015-10-02
Before we start....
Is ufw the normal interface for the firewall on this system? Are there any iptables settings outside ufw?  Pick 1 interface for the kernel firewall and use that.  

Check it by running **sudo iptables -L**.

Oh-  and this should help [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
There is almost always a guide for the major tools at help.ubuntu.com. There is also the "ubuntu server guide" which covers many common tasks.

---

### Post by CharlesA on 2015-10-02
I would recommend just sticking to plain iptables for those types of rules.

I looked thru the docs for ufw and didn't find anything that mentioned ranges of ports.

Iptables can do that just fine, so I don't know why I didn't see it for ufw.

FWIW: I use iptables via [ConfigServerFirewall]("http://configserver.com/cp/csf.html")

---

