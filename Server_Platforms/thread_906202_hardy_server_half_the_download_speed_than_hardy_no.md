---
title: "hardy server half the download speed than hardy non-server??"
date: 2008-08-31
forum: Server Platforms
---

### Post by Jean__ on 2008-08-31
Since I installed hardy on my server in stead of xp it's download speed is about half from what it used to be.

My desktop running kubuntu downloads at about 1 mbit/s. 
When xp was on the server, it used to download at the same speed, now it's averaging at around 500 kbit/s and less.
There are often gaps, where speed falls near to zero and it seems to be worse when downloading from newsgroups with ntp.

So I was thinking it might be some settings that hardy server has and hardy non-server hasn't.

What could cause this?

Idea's welcome..

---

### Post by schettj on 2008-08-31
> **Jean__ said:**
> So I was thinking it might be some settings that hardy server has and hardy non-server hasn't.

What could cause this?
I'm not seeing that. Off the top of my head, I would start looking at - ipv6 (disable?) and possibly dns issues... also, what services are you enabling? Turning on servers (ssh, http, smtp) means the usual security issues/endless script driven probes that can cause various issues...

But I'd start with ipv6/dns...

---

### Post by Jean__ on 2008-08-31
Yes besides the lamp there is ssh, a media server mostly idle, x11vncserver...
Just now I was having download speed of 600 when I got a messsage telling me the download speed was too fast for the disk.
That's another issue. I don't recall having troubles with that on xp. And vnc was much faster on xp, but that's maybe just the issue of x being somewhat slower.
Anyway I'm thinkg hard about putting xp back on, despite all the work that's gonna be. :(

---

### Post by Jean__ on 2008-08-31
Anybody knows something I could do to invest that slow harddisk issue? The machine is an older pentium 2, bios before 2000.

And does anybody know how to disable ipv6?

I' gonna try to get at least the download speed on that machine on par, if I don't succeed, xp goes back on it.

---

### Post by HermanAB on 2008-08-31
There are various reasons why a server may perform slow.  The most common are:
a. Bad DNS settings - make /etc/resolv.conf same as DNS in XP
b. If it is a Samba or NFS server, make the buffers larger
c. Bad ethernet configuration/bad driver

You just have to start at one end work your way through the options.  Use tcpdump, to get an idea of where the delays are.

---

### Post by Jean__ on 2008-09-01
I noticed my /etc/resolve.conf only has this:

```

nameserver 192.168.1.1
nameserver 0.0.0.0

```

I am behind a NAT modem/firewall, and my provider has a dns server, shouldn't that in be in there too?
Could that be a reason for slow connections?

---

