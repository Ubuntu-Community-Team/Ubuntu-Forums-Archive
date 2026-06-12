---
title: "Help regarding ICMP and Ping"
date: 2008-09-15
forum: Security
---

### Post by Danilux on 2008-09-15
I was taking a security test at [https://www.grc.com](https://www.grc.com) and all my ports were shown as stealth and ubuntu default config passed the test on pretty much everything, but one didn't pass:

Ping Reply: RECEIVED (FAILED) — Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation.


Is there a way to configure the firewall not to reply or ignore ping request in iptables?
I'm a begginer in linux i know about firewall in windows so please anyone could help me configure this on ubuntu, thanks sorry for english.

---

### Post by cariboo on 2008-09-15
You can use a gui for the default firewall that is installed by default on Ubuntu, such as firestarter, guidedog or fwbuilder to add the following rule:

```
iptables -A INPUT -p icmp --icmp-type echo-request -j DROP to block incomming pings

```

to stop a ping

Jim

---

### Post by brian_p on 2008-09-15
> **Danilux said:**
> 

Is there a way to configure the firewall not to reply or ignore ping request in iptables?

Is your computer connected to a router?

---

### Post by Danilux on 2008-09-15
cariboo907@
I tried installing Firestarter a few days ago and it freezes, i couldn't even configure it. Can i do that command manually?

I'm gonna give guidedog and fwbuilder a try though.




brian_p
Yes brian i'm connected to a router, there's a windows machine connected too but we don't share anything, but yes we are both connected to a router.

---

### Post by kevdog on 2008-09-15
Your router then has to block the ping requests as the reply is coming from the router rather than your individual computer behind the router since a NAT translation is going on through the router.  Most modern routers have capabilities to block the ping requests through their web interface.

Just my 2 cents -- if you are running any type of server to the outside world -- such as an ssh, ftp, http, openvpn, etc.  I actually want my network to be seen by the outside world and reply to a ping requests -- helps in troubleshooting when the client is not connecting to the server.  Again my 2 cents, however just because your network router replies to a ping request, I in no way see how this makes your network more vulnerable, particularly if you are not running any servers visible to the outside world, or in the face of a properly configured server/firewall if you are running a server visible to the outside world.

Sorry to go off topic.

For your own computer, you can block ping requests by typing:
sudo iptables -A INPUT -p icmp --icmp-type echo-request -j DROP

at the command line to add blocking of ping requests.  Most routers run linux, so even through the web interface, this type of command is being issued in the background.

---

### Post by iponeverything on 2008-09-15
goodness. if all box does is respond to pings you have nothing to worry about. 

I would not worry about any of gui's 

if you don't want send an echo reply just run the iptables command from the command line as root and add it to /etc/rc.local so that its there the next time you boot.

---

### Post by kamaji792 on 2008-09-15
As IPTables commands are being banded about can I recommend the excellent [IPTables HowTo](https://help.ubuntu.com/community/IptablesHowTo)

All the best

---

