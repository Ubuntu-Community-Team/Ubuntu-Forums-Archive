---
title: "How can I tell which PORTS I need to have Open?"
date: 2010-07-22
forum: Security
---

### Post by Ichido on 2010-07-22
How can I know which "Ports" on my laptop need to be Opened and all others Closed?

```
$ sudo lsof -i -n -P
COMMAND    PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
avahi-dae  939    avahi   13u  IPv4   6566      0t0  UDP *:5353 
avahi-dae  939    avahi   14u  IPv4   6567      0t0  UDP *:36703 
cupsd     1381     root    6u  IPv6   8786      0t0  TCP [::1]:631 (LISTEN)
cupsd     1381     root    7u  IPv4   8787      0t0  TCP 127.0.0.1:631 (LISTEN)
apache2   1430     root    4u  IPv6   8848      0t0  TCP *:80 (LISTEN)
apache2   1434 www-data    4u  IPv6   8848      0t0  TCP *:80 (LISTEN)
apache2   1435 www-data    4u  IPv6   8848      0t0  TCP *:80 (LISTEN)
dhclient  2961     root    5w  IPv4  27504      0t0  UDP *:68 
firefox-b 3104     dave   90u  IPv4  56792      0t0  TCP 192.168.2.101:54638->66.220.145.37:80 (ESTABLISHED)
plugin-co 3154     dave   16u  IPv4  32645      0t0  TCP 192.168.2.101:43300->67.195.186.116:5050 (ESTABLISHED)

```
I an using UFW (Ubuntu FireWall)and Removed Firestarter.

How can I "Control" and/or Monitor UFW?

---

### Post by bodhi.zazen on 2010-07-22
> **Ichido said:**
> How can I know which "Ports" on my laptop need to be Opened and all others Closed?

If you want to run a server, Apache for example, and you want others to connect to it, you need to open the port / allow the traffic through your firewall.

> I an using UFW (Ubuntu FireWall)and Removed Firestarter.

How can I "Control" and/or Monitor UFW?

What do you want to "Control" ? What do you want to "Monitor" ?

I suggest you look at these pages :

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

Monitoring can be anything from auditing the logs to wireshark to snort. IMO, most people use snort as it filters through the traffic and alerts you to only that which may require attention.

---

### Post by Ichido on 2010-07-23
Thank You very much for the links :D

---

### Post by bodhi.zazen on 2010-07-24
Glad they helped. If you still have or run across additional questions, post 'em here =)

---

