---
title: "IP Not Resolving in 9.04 Server"
date: 2009-06-23
forum: Server Platforms
---

### Post by SoulMazer on 2009-06-23
Sorry for another post about getting a static IP to work, but I think I'm almost there.

So a week a ago I had DSL and had everything working with a DHCP connection. Yet I just upgraded to cable internet and now everything seems to be messed up for some reason. Now I am unable to connect to "mydomain.com".

On my box, I have a client set to update with DynDNS to a hostname every few minutes. Since this has not changed since my upgrade to cable, I know this is not my problem.

I have also forwarded port 80 to my box and by using [DynDNS's OpenPort tool]("http://www.dyndns.com/support/tools/openport.html") I am pretty sure that the port is not the problem.

Finally, here are some files that I think will help.

My /etc/network/interfaces file:
> 
# loopback
auto lo
iface lo inet loopback

# primary network
auto eth0
iface eth0 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1

My /etc/resolv.conf file: (Note, this was all pre-assigned when I opened it)
> 
domain nv.charter.com
search nv.charter.com
nameserver 24.205.192.61
nameserver 66.215.64.14
nameserver 24.205.1.14


So, what can I do to fix my problem?

Thank you very much in advance.

---

### Post by Bachstelze on 2009-06-23
I'm not sure I understand what your problem is. What do you mean, when you say you can't "connect to 'mydomain.com'"?

---

### Post by SoulMazer on 2009-06-23
Ok well let me just cut out the unnecessary parts to this equation. So basically, I have a hostname (patsserver.homelinux.com) that points to my IP address which is updated constantly. However, whenever I type "patsserver.homelinux.com" into my browser, I get a page that has a never-ending loading page.

I don't know what is causing this to happen, but I would like to know how to fix it.

Thanks again.

---

### Post by Bachstelze on 2009-06-23
Right now, the domain points to 24.205.206.93. Is that your IP? [http://whatismyip.com/](http://whatismyip.com/) if you're not sure.

---

### Post by SoulMazer on 2009-06-23
Yes, 24.205.206.93 is my current IP address.

---

### Post by Bachstelze on 2009-06-23
> **SoulMazer said:**
> Yes, 24.205.206.93 is my current IP address.

Then it's your server that's the problem, not the domain name.

---

### Post by SoulMazer on 2009-06-23
Ok yes, but how do I fix it? I have no idea what is with it.

Thanks again.

---

### Post by Bachstelze on 2009-06-23
> **SoulMazer said:**
> Ok yes, but how do I fix it? I have no idea what is with it.

Thanks again.

Well, it dependS. What do you use your server for? For starters, make sure your ISP doesn't block the relevant port(s) and that they are open/forwarded in your router/firewall. If all is good, check your logs.

---

### Post by SoulMazer on 2009-06-23
> **HymnToLife said:**
> What do you use your server for?
I use it to host my website (a few HTML pages, a few PHP pages, some CGI scripts, etc.) and this is all done via a LAMP setup.

> **HymnToLife said:**
> make sure your ISP doesn't block the relevant port(s) and that they are open/forwarded in your router/firewall.
I have already forwarded port 80 for normal HTTP use. Also, DynDNS's Open Port tool reveals that the port is not being blocked, that there is just "no service available on the port".

> **HymnToLife said:**
> If all is good, check your logs.
Sorry for all the questions, but which logs are you referring to? And where are they located?

Thanks again.

---

### Post by cariboo on 2009-06-23
All the logs are located in /var/log.

---

### Post by windependence on 2009-06-23
Are you trying to access it from inside your network or outside?

-Tim

---

### Post by SoulMazer on 2009-06-23
Thanks cariboo.

Anyways, I decided to simply do a fresh install of 9.04 Server and I found some interesting things. So, when I reinstalled, I chose to install a LAMP server and to install OpenSSH. When I try to connect to my domain from outside my network, I get an error message: "Unable to determine IP address from host name". I think I must be having a problem with Apache because when I surf _directly to my IP_ from outside my network, I get "connection refused". And according to Google, that usually means there is no service listening on that port.

Also, my error log for Apache has nothing relevant in it.

Anybody have any suggestions at all? I'm getting pretty desperate.

---

### Post by papenpj on 2009-06-23
I checked out that address and got a testpage. So is your problem resolved?

---

### Post by SoulMazer on 2009-06-24
Did you really? Well...when my friend just tried it he was unable to get either my straight IP or the domain to load.

I am pretty sure the problem is just that all connections are being refused. How can I fix this?

Thanks.

---

### Post by SoulMazer on 2009-06-24
Ok, well after I read a few other threads and other info, I somehow got it working. It seems as though the problem suddenly stopped for whatever reason...but thanks to everybody that helped.

---

