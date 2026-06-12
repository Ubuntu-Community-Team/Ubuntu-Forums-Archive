---
title: "ddclient.conf config for virtual hosts on zoneedit"
date: 2008-06-27
forum: Server Platforms
---

### Post by skunkbad on 2008-06-27
I tried to get a new IP by turning off the network for a while, but no luck. I've got 2 websites that need to have their zoneedit zones updated if the WAN IP changes. I'm hoping I configured ddclient.conf correctly, and hoping for a check:

```
pid=/var/run/ddclient.pid
protocol=zoneedit1
use=web
server=www.zoneedit.com
login=MrSkunk
password='password123'
wildcard=yes
site1.com
site2.com
```

---

### Post by sxxxe83 on 2008-10-14
> **skunkbad said:**
> I tried to get a new IP by turning off the network for a while, but no luck. I've got 2 websites that need to have their zoneedit zones updated if the WAN IP changes. I'm hoping I configured ddclient.conf correctly, and hoping for a check:

```
pid=/var/run/ddclient.pid
protocol=zoneedit1
use=web
server=www.zoneedit.com
login=MrSkunk
password='password123'
wildcard=yes
site1.com
site2.com
```

As far as I know zoneedit.com uses the address: dynamic.zoneedit.com not the [www.zoneedit.com](www.zoneedit.com) if you want to update it like this.

---

### Post by johnnybirdman on 2008-10-17
Did you get this working?  I'm trying to configure ddclient.conf for a zoneedit update also and can't find any definitive answers on what is the proper code.  Been trying for a while and still seeing errors in syslog.

---

### Post by MJN on 2008-10-17
Whilst I'm sure you can get ddclient to work (I haven't used it so cannot help specifically) have you considered using [Zoneclient](http://zoneclient.sourceforge.net/)?

I've used it for several years now and can highly recommend it.

Mathew

---

### Post by johnnybirdman on 2008-10-17
> **MJN said:**
> Whilst I'm sure you can get ddclient to work (I haven't used it so cannot help specifically) have you considered using [Zoneclient](http://zoneclient.sourceforge.net/)?

I've used it for several years now and can highly recommend it.

Mathew

Thanks for the tip Mathew, I may look into using it.

I learned that is helps in the ddclient.conf to have the correct password....](*,) 

For the OP and everyone else I have basically the same .conf working with some minor revisions:
```
pid=/var/run/ddclient.pid
protocol=zoneedit1
use=web,web=dnspark
server=www.zoneedit.com
login=username
password='password123'
site1.com,site2.com
```
thanks to this post here [http://boardgamemadness.blogspot.com/2008/06/easy-fixes-how-to-fix-ddclient-for.html](http://boardgamemadness.blogspot.com/2008/06/easy-fixes-how-to-fix-ddclient-for.html)

---

### Post by johnnybirdman on 2009-05-05
As an update to this, I had to change the server line to

```
server=dynamic.zoneedit.com
```

to make this work properly.

---

