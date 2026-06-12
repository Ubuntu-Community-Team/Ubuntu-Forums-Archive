---
title: "Various Ports are Closed"
date: 2013-01-15
forum: Server Platforms
---

### Post by donniezazen on 2013-01-15
Hello,

Some of my ports that used to work fine are now not open anymore. I am not sure why. These ports are added to port forwarding section of my router. How can I open these ports? I am using a 12.04 Ubuntu Server.

```

4040 Subsonic
443
80
8080 XBMC
9777 XBMC
10,000 Webmin

```

Thanks.

---

### Post by Mopar1973Man on 2013-01-15
I'm going to take a crack at it. I'm rather a noob to the linux server stuff. But from what I normal try to do is test and be sure the port responds locally first on the actual machine. 

So can you localhost these ports?

---

### Post by d4rk0wl on 2013-01-15
That is a good starting point, also do you have any local firewall running (besides the one on your router), i.e. smoothwall.

Regards,
- D4rk0wl

---

### Post by donniezazen on 2013-01-15
> **Mopar1973Man said:**
> I'm going to take a crack at it. I'm rather a noob to the linux server stuff. But from what I normal try to do is test and be sure the port responds locally first on the actual machine. 

So can you localhost these ports?

I can access these ports on my laptop but not over internet. They also keep changing like 10,000 no works over internet.

> **d4rk0wl said:**
> That is a good starting point, also do you have any local firewall running (besides the one on your router), i.e. smoothwall.

Regards,
- D4rk0wl

It's just the stock Ubuntu server with a few software installed. I haven't done any modification related to firewall. I got myself a new router and I am not sure if it is related to my new router.

---

### Post by d4rk0wl on 2013-01-16
So just to clarify, you are able to access the services from your LAN but not over the WAN correct?

Sounds like something is going on with your new router/firewall. What is the make/model of the router?
Also, did you enable both TCP/UDP connections on the ports in question?
You also might want to use a tool such as nmap to see if the ports are indeed closed from the WAN just to verify.

Regards,
- D4rk0wl

---

### Post by cariboo on 2013-01-17
[http://www.canyouseeme.org/](http://www.canyouseeme.org/), is a great tool for checking to see if the ports you specified are open to the rest of the world.

---

### Post by donniezazen on 2013-01-17
> **d4rk0wl said:**
> So just to clarify, you are able to access the services from your LAN but not over the WAN correct?

Sounds like something is going on with your new router/firewall. What is the make/model of the router?
Also, did you enable both TCP/UDP connections on the ports in question?
You also might want to use a tool such as nmap to see if the ports are indeed closed from the WAN just to verify.

Regards,
- D4rk0wl

Yes, that's correct. I am unable resolve these ports over WAN/Internet.

I have a [MediaLink MWN-WAPR150N]("http://www.amazon.com/Medialink-Wireless-Broadband-802-11n-Internal/dp/B0044YU60M/ref=sr_1_1?ie=UTF8&qid=1358402712&sr=8-1&keywords=medialink+wireless+n+router&tag=thelinactsho-20"). I have tried disabling default router firewall but it didn't do anything. Most ports on the list are open for both TCP/UDP except 8080(TCP) and 9777(UDP) as required by XBMC Remote.

Here is a quick nmap summary.
```
nmap -sT presynapse.dyndns.org

Starting Nmap 6.25 ( http://nmap.org ) at 2013-01-16 23:22 MST
Nmap scan report for presynapse.dyndns.org (98.202.218.108)
Host is up (0.038s latency).
rDNS record for 98.202.218.108: c-98-202-218-108.hsd1.ut.comcast.net
Not shown: 996 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
631/tcp   open  ipp
9091/tcp  open  xmltec-xmlmail
10000/tcp open  snet-sensor-mgmt

Nmap done: 1 IP address (1 host up) scanned in 0.64 seconds
```

Thanks.

---

### Post by donniezazen on 2013-01-17
> **cariboo907 said:**
> [http://www.canyouseeme.org/](http://www.canyouseeme.org/), is a great tool for checking to see if the ports you specified are open to the rest of the world.

That's what I used to check aforementioned ports.

---

### Post by d4rk0wl on 2013-01-17
It seems that these services are bottlenecking at your router/firewall.

You may want to attempt to enable a DMZ style configuration on your router, forwared to your server.

Best of luck!
- D4rk0wl

---

### Post by d4m1r on 2013-01-17
What kind of router is it? Has it recently been restarted or lost power? Could it be your ISP blocking those ports now and not your router?

---

### Post by donniezazen on 2013-01-19
> **d4rk0wl said:**
> It seems that these services are bottlenecking at your router/firewall.

You may want to attempt to enable a DMZ style configuration on your router, forwared to your server.

Best of luck!
- D4rk0wl

I have enabled DMZ and disabled router firewall. Still no luck.

> **d4m1r said:**
> What kind of router is it? Has it recently been restarted or lost power? Could it be your ISP blocking those ports now and not your router?

As mentioned about it's a Medialink Wireless N Broadband Router model number MWN-WAPR150N. Yep it has been restarted many times. I am not sure what you mean by lost power. It does seem like my ISP might be blocking it. How do I get it to unblock? Do I have to call them and ask them to unblock these ports?

---

