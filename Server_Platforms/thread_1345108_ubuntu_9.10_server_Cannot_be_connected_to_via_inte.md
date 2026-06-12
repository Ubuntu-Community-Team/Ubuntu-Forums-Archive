---
title: "ubuntu 9.10 server Cannot be connected to via internet"
date: 2009-12-03
forum: Server Platforms
---

### Post by yewbie on 2009-12-03
First all ports on my lan to this server are working properly.
Secondly I have a old version of whitebox linux running with a similar configuration that is working properly.

Here is what I am doing, I am running postfix with spamassassin and clamav and amavis, all this is working properly, I can telnet in from anywhere in my lan and send emails, it gets relayed to my exchange server.. everything works great...

Now when I change my Router which I have setup with NAT to port 25, when I change the IP address from my old machine (whitebox linux with same configuration) to the IP of my new machine I cannot connect at all through the NAT over the internet...

Now this has to be some strange configuration I have disabled the firewall on the machine, yet its still not working... I don't really think this is a postfix problem so much since I tried doing the same thing give port 110 (POP3) and it also was not working..

It makes me believe that there is something not correct with my networking setup... I have looked through all the config files and nothing seems to stick out at me, as im not sure what configs people will want to see I will post a few random ones and hope someone steers  me to the correct config file.


```

#/etc/networks/interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address = 10.0.0.245
gateway = 10.0.0.56
netmask = 255.255.255.0

```Thank you in advance, I will post posfix config files also on request (I do not believe that is the problem though)



Edit: Running netstat shows:
***tcp 0 0 *:smtp *:* LISTEN ***

---

### Post by munky99999 on 2009-12-03
> Here is what I am doing, I am running postfix with spamassassin and clamav and amavis, all this is working properly, I can telnet in from anywhere in my lan and send emails, it gets relayed to my exchange server.. everything works great...
the exchange server is on the lan also?

> It makes me believe that there is something not correct with my networking setup... I have looked through all the config files and nothing seems to stick out at me, as im not sure what configs people will want to see I will post a few random ones and hope someone steers me to the correct config file.
Sounds like something to do with this specifically.

> Now when I change my Router which I have setup with NAT to port 25, when I change the IP address from my old machine (whitebox linux with same configuration) to the IP of my new machine I cannot connect at all through the NAT over the internet...
You make this change up. It causes problems.

If the exchange server is on the lan. You have no connectivity originally through the internet. I would look more at the ISP. ISPs very commonly block port 25 so you can host your own mail servers.

---

### Post by yewbie on 2009-12-04
> **munky99999 said:**
> 
You make this change up. It causes problems.

If the exchange server is on the lan. You have no connectivity originally through the internet. I would look more at the ISP. ISPs very commonly block port 25 so you can host your own mail servers.


Sorry my wording was a bit bad on that, The original configuration pointing to the whitebox linux server still works through the NAT on port 25 as intended.
We have a dedicated t1 with no ports blocked.

Yes my exchange server is also on the lan.

Also some more information I can connect out to the internet from the new ubuntu box.

Could this be some strange dns or domain problem?

To specify when I do the NAT change im just changing the points to address from 10.0.0.243(old whitebox) to 10.0.0.245(new ubuntu)

---

### Post by yewbie on 2009-12-04
Im sorry this problem is resolved, there was a filter set on my router that I neglected to check that was specifically blocking port 25 to any other IP, why this was there I have no idea but I fixed it, thanks for everyone who tried to help!

---

