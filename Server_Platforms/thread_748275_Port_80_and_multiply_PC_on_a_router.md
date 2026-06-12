---
title: "Port 80 and multiply PC on a router"
date: 2008-04-07
forum: Server Platforms
---

### Post by ianb72 on 2008-04-07
Hi
I am trying to set up a LAMP server, I've installed the LAMP Server and WebMin and I am going through the guide at:
[LAMP for noobs]("http://www.cjfay.com/lamp.html")

I have given my server a static IP address with my router as per the guide and then did a port scan from [Security Port Scan]("http://www.whatsmyip.org/ports/security/")
which tells me that port 80 is open

My ISP says that they don't block port 80 so I put in my IP Address into firefox it comes up with 
[HTML]The connection was reset[/HTML]

Even when I tried to re-route it to port 8080 on my router I still had no luck :confused:

Could this be that I have 2 other PC's on my router? If so how can I over come this or can't I??

Many Thanks
Ian

---

### Post by Dr Small on 2008-04-07
Did you forward port 80 on your router to the IP address where the LAMP server is? Also, if a port would be closed, it would give a Connection Refused, error.

Another thing, how are you attempting to access this? From within the local network, or outside ?

Dr Small

---

### Post by pseudo-random on 2008-04-07
Go google a free web proxy. Then put your IP in that...
If you do it locally its local, not remote and will give different results.

---

### Post by Dr Small on 2008-04-07
> **pseudo-random said:**
> Go google a free web proxy. Then put your IP in that...
If you do it locally its local, not remote and will give different results.
Or.... you could ask one of us good member's here to test for ya :)

---

### Post by ianb72 on 2008-04-07
Hi
I am trying to access the server locally, with my IP address.

On my Router I have Virtual Servers for which I have set up the External start and end port as 80 and the internal start and end port as 80 and assigned it my servers static IP address which I gave 192.168.2.99.

I tried to use a free web proxy and it seemed to works :confused:

At this present time my IP Address is [HTML]79.65.222.215 [/HTML]

So if anyone would look for me and tell me if everything if ok I would be very grateful

Many Thanks
Ian

---

### Post by pseudo-random on 2008-04-07
Apache works. Don't think much to your website (yet)  though ;)
Use this command to see everyone who just accessed your webserver:
```

cat /var/log/apache2/access.log
```

---

### Post by Dr Small on 2008-04-07
I connected just fine.

---

### Post by ianb72 on 2008-04-07
Thanks for that, I haven't got round to putting a index page up yet, as you can see :)

I just wanted to make sure everything was working fine before I started that and then tried to learn how to assign a Domain name to my server using dynamic DNS.

Thanks for all your help guys

Ian

---

