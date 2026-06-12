---
title: "BIND9 question..."
date: 2008-08-22
forum: Server Platforms
---

### Post by hockey97 on 2008-08-22
HI I have a router currently. My problem is that if I only have an A record for the domain to point to my external ip  and have people at my house to take a look at my website ect I get my routers config page instead of my website.

I currently makde 2 A records each one for the [www.mydomain.com](www.mydomain.com) and other mydomain.com ect..  I made 2 copies one is pointed towards my external ip and the other record is pointed to my internal ip.


I notice that when this happens my website would sometimes work and somtimes bring up my routers config page.


How can I solve this problem??

---

### Post by windependence on 2008-08-23
This is because the router will not route traffic outside your network just to com back in again.

You need to put and entry into each of your home LAN computers host files for the server to create an alias for it.

Put something like this in your /etc/hosts on Linux or your %SystemRoot%\system32\drivers\etc\hosts file on Windows.

```
xxx.xxx.xxx.xxx  yourservername.tld   yourservername
```

Where xxx.xxx.xxx.xxx is your server's IP on the LAN.

This will tell each machine how to resolve the server name when on your local network.

-Tim

---

### Post by hockey97 on 2008-08-23
ok, I see. So should I delete all domain records where I refer/point the domain name to my internal ip address of my server??

Since I was told that if I made 2 same A records and the only difference is the ip one is internal the other is external.

Someone told me that my external traffic would work 50% of the time and the 50% will not work because the dns server would rotate them causing my external traffic not able to get to my website.

so should I just delete all A records I made using my internal ip?

---

### Post by windependence on 2008-08-23
If you are running a DNS server on your LAN, you don't have to be. You should point your domain at your external address using your domain registrar's DNS control panel. That is much cleaner.

-Tim

---

