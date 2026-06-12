---
title: "Too much for one server?"
date: 2010-01-03
forum: Server Platforms
---

### Post by sparkerjc on 2010-01-03
Can I do all of this on the same server?

1. Name Server to point to my website
2. Host said website with apache
3. run a mail server for addresses @mywebsite.com

I have seen that I can do each individually but I want to know if one machine can do all of these.

The biggest one that confuses me is how to host my own DNS so that anyone can go to mywebsite.com and it points to my ip. Any good how-to's for that?

Thanks in advance.

---

### Post by J V on 2010-01-03
Yes you can, I don't know...

---

### Post by ian dobson on 2010-01-03
Hi,

The DNS server that points at your IP needs to be "known/trusted" by other DNS servers. The best thing to do is register your domain and use zoneedit.org to point your domains at your IP address. zoneedit is free for "small" users.

Regards
Ian Dobson

---

### Post by arvevans on 2010-01-03
DNS servers only use resources when asked to resolve a URL to IP address.  Set up your DNS server so that it uses something like 8.8.8.8 as primary DNS source and maybe 8.8.4.4 as the secondary.  Turn on DNS caching and it will remember DNS resolves that it does, so it doesn't have to look them up again.  Set the cache timeout so that it does recheck URLs at some reasonable interval.  Then point your downstream computers at your DNS server as their DNS host.  You can place hard-coded DNS resolve information in the DNS config files so that they will remain there and will always point to your mail server URL or IP.

Apache is one of the larger and more robust web servers.  You might want to look into one of the smaller, and faster, ones for use on a busy machine.  Try Comanche or Hiawatha for more minimalist servers.  There are some network issues with personal web servers...if you are connected to the Internet via DSL or something similar your bandwidth may be asynchronous, such that you have much higher download speed from the Internet than upload speed to the Internet.  If true this will impact user's ability to browse your web from outside your own LAN.  Put some large images up on your web server and test the access times to see if you have a problem.

Running an email server from your own computer is more a matter of traffic load than anything else.  Text emails do not take much bandwidth, but emails with large amounts of imagery could use significant bandwidth.

As you install and activate all these services you might want to use one of the CPU and Memory bandwidth monitors ("top" from the command line) to see just how much resources each is using in idle mode, and then the same while doing DNS dips, Web page serving, and email handling.

Older  PC's running stripped down versions of Linux (i.e. no X-windows or other GUI software) can make very efficient services servers.
_._

---

### Post by BkkBonanza on 2010-01-03
You can run all those on one machine no problem. It depends mostly on how busy they are as to whether you will get good speed. If you're just starting out and don't have lots of web traffic then you'll have no problems.

Regarding DNS: I recommend you don't bother running you own DNS servers. Just use the ones at your registrar or if not free then use zoneedit as suggested above. DNS servers should be on reliable connections and should be redundant - ie. multiple nodes present 24/7. When DNS is down everything else you have will be down but even worse your name will appear not to exist. If you don't have complex needs then there is no  reason to run them yourself. At least when they are served independently from your web/email server the name will work even when your server is down.

The comment above about using google's at 8.8.8.8/8.8.4.4 is only for DNS caching/recursive DNS and is irrelevant as far as pointing your own IP to your web server and for email. You need to add an A record for the webserver, a CNAME for aliases for the web server, and an MX record for your email server.

---

### Post by sparkerjc on 2010-01-03
Thanks for the replies. It looks like zoneedit.com is the perfect solution for what I need as far as DNS goes, so now I just need to set the server up as a mail server and web host.

You guys rock!

---

### Post by munky99999 on 2010-01-03
There are only 2 reasons for something to be "too much for 1 server"

1. Security: In computing there are some things you want apart. Generally speaking it's security based things. Network authentication shouldnt be on the same machine as a webserver

2. Resources: IF your server is running full blast constantly. Adding new roles like a distributed compiler or something. Or if your hd space is almost all full and you have no space for expansion; probably not the best choice for a file server.

As for LAMP + Mail + Dns. Should work fine assuming you have the resources for your traffic.

---

### Post by ian dobson on 2010-01-04
Hi,

My backend server runs the following and doesn't even break out in a sweat:-

1) Apache web server with 4 domains defined (2 PHP/SQL based)
2) Email server with spamassassin spam filter
3) Mysql Server with several DB's (600Mb data in total)
4) MythTV video server with 2 DVB tuners
5) 9Tb disk space (6Tb RAID5 array + 3Tb backup)
6) Local DNS cache server

The CPU load from all what is usually <10% on a Q9660 with 8Gb ram.

Regards
Ian Dobson

---

### Post by HighCommander540 on 2010-01-04
> **arvevans said:**
> Apache is one of the larger and more robust web servers.  You might want to look into one of the smaller, and faster, ones for use on a busy machine.  Try Comanche or Hiawatha for more minimalist servers.  There are some network issues with personal web servers...if you are connected to the Internet via DSL or something similar your bandwidth may be asynchronous, such that you have much higher download speed from the Internet than upload speed to the Internet.  If true this will impact user's ability to browse your web from outside your own LAN.  Put some large images up on your web server and test the access times to see if you have a problem.

_._

I would recommend doing this. There are a lot of other great web server's out there that are much better (and faster) for small users. In reality unless you need something that Apache specifically does. I would never use it myself. It is old and slow and a resource hog. It use to be the best, but it hasn't been really looked at and made better in a long while.

Here is a topic that talks about this problem and better solutions:

[http://ubuntuforums.org/showthread.php?t=1366564]("http://ubuntuforums.org/showthread.php?t=1366564")

---

### Post by i.r.id10t on 2010-01-04
Yeah you can do all that with one box, but you'll need 2 IPs to do your own DNS totally....

---

### Post by K.J. on 2010-01-04
It also depends on your PC specs. A more modern PC can handle the load no problem. On the other hand, my current server is only running a P3 and maxes out CPU load on SSL connections at a mere 300 kbps. Hopefully, I'll be replacing it soon with something that can at least saturate my uplink.

---

### Post by HighCommander540 on 2010-01-04
> **K.J. said:**
> It also depends on your PC specs. A more modern PC can handle the load no problem. On the other hand, my current server is only running a P3 and maxes out CPU load on SSL connections at a mere 300 kbps. Hopefully, I'll be replacing it soon with something that can at least saturate my uplink.

Yeah, but the point is. Why would you use something that does this even on a bad machine. When you could use something that is just pure faster?

Unless you are using something that only Apache has. Which for the most part from what I here people say about what they use apache for...They are never doing something that the other's can't do/better.

---

### Post by kevin11951 on 2010-01-04
as others have said, don't use Apache...  I personally think you should use lighttpd.

---

### Post by doas777 on 2010-01-04
> **sparkerjc said:**
> 
The biggest one that confuses me is how to host my own DNS so that anyone can go to mywebsite.com and it points to my ip. Any good how-to's for that?

Thanks in advance.

in terms of your services, all of them are light, unless you are dealing with a lot of traffic, so you are probably good.

as for the DNS listing, you do need to register a domain publicly. nothing will get around that. you cannot just put up your own server and have remote clients resolve to you.
Look up dns registrars, and if you have a dynamic IP from your ISP, look at dydns and noip specifically, as they are geared to your scenario.

---

