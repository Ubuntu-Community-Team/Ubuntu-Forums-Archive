---
title: "Problems with DNS."
date: 2010-09-09
forum: Server Platforms
---

### Post by goregeous on 2010-09-09
Hello all,

I'm pretty newb to ubuntu/linux in general, so I need a bit of help.

Installed Server 10.04, and everything went smoothly. Now, after I have tried to set up DNS' to get access to internet, I fail every time.

Edited resolv.conf file, added > nameserver primary/secondary DNS of my ISP ( I am running it on a company's network, getting out via gateway, which I have added to eth0 settings).

I have tried to install bind9 ( as I understood, it maintain the DNS ), and dnstools, but always get info: 

> E: Couldn't find package bind9/dnstools 

depending on which one I am trying to install. I am pretty much stuck in this, and trying to resolve this for two days, but didn't get anywhere. I have tried with googling for help, and saw several topics on this theme, and that lead me to register here.


Thank you in advance.

---

### Post by philinux on 2010-09-09
Please start your own threads using the New Thread button.

---

### Post by CharlesA on 2010-09-09
Please post the output of these commands:

```
ifconfig
```

```
cat /etc/resolv.conf
```

```
ping -c 4 74.125.95.103
```

```
ping -c 4 google.com
```

---

### Post by NotFromBrooklyn on 2010-09-10
I have a bit different, but similar, problem.

                     p { margin-bottom: 0.21cm; }  nslookup for localhost, localdomain, localhost.localdomain
 Server:        192.168.0.1  
 Address:    192.168.0.1#53  
 

 ** server can't find localhost.localdomain.: NXDOMAIN
 
ping for localhost, my LAN IP, google.com, 74.125.95.103 OK

ping for my WAN IP 100% packet loss

I installed LAMP, but I can't acces my web server from Internet, what should I do?

--

I reached the solution myself.

---

