---
title: "Proftp and NAT networking porblem (have read all posts about it, I think)"
date: 2006-11-22
forum: Server Platforms
---

### Post by baldercm on 2006-11-22
Hi!
I've setup my ftp server and everything works ok... but only in mi local LAN.
I've dynamic IP address, and I've got a dyndns domain with ddclient, so ddclient it's configured to get the IP from [http://checkip.dyndns.org/](http://checkip.dyndns.org/). I think it's working fine.
My ftp port(2000) and passive ports(60000-60100) are open in my router's (Comtrend CT536+) virtual servers configuration, and I added
```
MasqueradeAddress mydomain.serveftp.org
PassivePorts 60000 60100
```
to the proftpd.conf file.
When I start proftp I get
```
balder@PortatilBalder:~$ sudo /etc/init.d/proftpd restart
 * Stopping ftp server proftpd [ ok ]
 * Starting ftp server proftpd
- IPv6 getaddrinfo 'PortatilBalder' error: Name or service not known
PortatilBalder - 127.0.1.1:2000 masquerading as 88.10.240.228 [ ok ]
```
Is that an error or it's ok?
My ftp site can't be accessed from outside my NAT right now and I really need it to work as soon as possible.
I've read some howtos talking about proftp and NAT ([like this one]("http://www.proftpd.org/localsite/Userguide/linked/config-nat.html")), but it uses ipchains and ipmasqadm, and I use iptables, but don't know how to manage it to achieve the same result.
Thanks

---

### Post by tturrisi on 2006-11-22
Just curiosu, does dynns redirect www and ftp, and must you do any configs at dyndns to route ftp?

---

### Post by rickyjones on 2006-11-22
When you forwarded the ports from your router, you did set your server to a static IP and you forward those ports to that IP, correct?

---

### Post by baldercm on 2006-11-23
Thank you for the answers

> tturrisi 
Just curiosu, does dynns redirect www and ftp, and must you do any configs at dyndns to route ftp?
I think dynds redirects wahtever you want, since it redirects an IP (without a port). You can later connect to your dyndns domain using any port, so you can use web, ftp... I think, I'm not sure.

> rickyjones 
When you forwarded the ports from your router, you did set your server to a static IP and you forward those ports to that IP, correct?
Yes, I use static IPs for all my LAN and forwarded ports to my IP.

Wow, I've just read my email, and my job partners said it seems my ftp is accessible from the internet!! It seems I can't connect to my domain from my computer, though I don't mind because it's mine :D.

Now I've set up a virtual host in proftp so it also serves to my LAN IP: I wanted to see my site to check out permissions and so on.
Anyone knows why can't I connect to my domain name but can do it to my local virtual site???

Thanks again

---

### Post by baldercm on 2006-11-23
It seems it works ok, but not perfect: I'm having problems with mi dynamic IP refresh at dyndns.org using ddclient. Anyone have any experience with that? I show you my ddclient.conf file:

```
daemon=300                               # check every 300 seconds
syslog=yes                              # log update msgs to syslog
#mail=root                              # mail all msgs to root
#mail-failure=root                      # mail failed update msgs to root
pid=/var/run/ddclient.pid               # record PID in file.

## via our CheckIP server
use=web, web=checkip.dyndns.org/, web-skip='Current IP Address: '
login=mylogin
password=mypswd
protocol=dyndns2
server=members.dyndns.org
wildcard=YES
mydomain.serveftp.org
```

Thanks

---

### Post by kelbizzle on 2006-11-25
I'm having the same issue. I believe I have stumbled across some sort of answer that lies within [this thread]("http://forums.proftpd.org/phpBB2/viewtopic.php?t=1350&highlight=ipv6"). 

It seems as though proftpd is precompiled with ipv6 support enabled. I think you have to download it and then You will have to remove the "--enable-ipv6" from the configure options before compiling it. Thats what I got from reading the thread. I'm just too lazy to get off my laptop to go upstairs and try it.


edit: check line 1065

---

### Post by houstonbofh on 2006-11-25
> **baldercm said:**
> It seems it works ok, but not perfect: I'm having problems with mi dynamic IP refresh at dyndns.org using ddclient. Anyone have any experience with that?
You will get much better performance if you do the dyndns.org update from the router.  Many support it now.  If yours doesn't I would consider buying one that does.  For example the Linksys wrt54gl or perhaps m0n0wall.  I have m0n0wall with dyndns.org on over 40 locations, and it updates instantly.

---

