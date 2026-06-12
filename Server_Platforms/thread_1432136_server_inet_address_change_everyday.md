---
title: "server inet address change everyday"
date: 2010-03-17
forum: Server Platforms
---

### Post by iroy2000 on 2010-03-17
Hi all,

I'm using comcast, and I setup my server, everything works fine.

But later I found out that the server inet address is changing everyday, and it makes my server almost not accessible.

Is there anyway to fix that problem??

Thanks

---

### Post by jrssystemsnet on 2010-03-17
Dynamic DNS.  There are lots of providers for this; try [http://dyndns.org](http://dyndns.org).

---

### Post by KB1JWQ on 2010-03-17
This is why I pay for a static IP-- I THINK running a server is against the ToS for some residential ISPs-- you might want to check this.

---

### Post by Iowan on 2010-03-17
[http://www.no-ip.com/]("http://www.no-ip.com/") is a similar service.

---

### Post by iroy2000 on 2010-03-18
Yes, I'm using dyndns.org. Maybe I haven't make my question clear above.

My inet address for my server was when I do ifconfig
192.168.1.4

today it is 
192.168.1.6

So I'm using netgear, so I redirect all incoming traffic to 192.168.1.4.

But the inet address change, so the incoming traffic can't find the server.

I'm still have no idea how to make my server always has the same inet address.

---

### Post by jrssystemsnet on 2010-03-18
> **iroy2000 said:**
> Yes, I'm using dyndns.org. Maybe I haven't make my question clear above.

My inet address for my server was when I do ifconfig
192.168.1.4

today it is 
192.168.1.6

That's not an internet address, that's a private address.  Either stop using DHCP from your router and start using static addressing in /etc/network/interfaces, or tell your router to always issue the same IP to your server's MAC address.

See [http://ubuntuwiki.net/index.php/Network_interfaces,_configuring](http://ubuntuwiki.net/index.php/Network_interfaces,_configuring) for a cheat sheet on the formatting for /etc/network/interfaces.

---

