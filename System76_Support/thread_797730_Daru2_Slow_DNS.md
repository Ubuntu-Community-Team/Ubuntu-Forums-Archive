---
title: "Daru2: Slow DNS"
date: 2008-05-17
forum: System76 Support
---

### Post by williumbillium on 2008-05-17
First of all, perhaps it would be more appropriate for this post to be in the Networking forum, if so, please move it.  I posted here since it's regarding a System76 laptop.

I am experiencing slow DNS lookups.  Usually browsing is fine for a few minutes or, sometimes, even hours but then, every time I lookup a domain I see "Looking up www.domain.com" in Firefox's status bar for about 10 seconds before the page begins to load.  Issuing ping commands is similar, there is a 10 second lag before anything happens, but the time for each ping is normal.

Basically, general download speed is fine but the initial lookup is very slow.

My Setup:

Daru2/Ubuntu Gutsy/wrt54gl router (happens when connected wired or wireless)

There is also a wired desktop on the same network running kubuntu gutsy that has no network issues.

Interestingly enough, when I connect to another wireless router I don't have this problem.

What I've tried:

Disable ipv6 in Firefox

Delete all reference to ipv6 in /etc/hosts, added "blacklist ipv6" to /etc/modprobe.d/blacklist

Use OpenDNS servers for DNS on Daru2 and router (208.67.222.222, 208.67.220.220)

None of this helped.

As a last resort I even tried local DNS caching (following this guide: [http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/) ).  That improved the speed of lookups using dig or nslookup, but web browsing and pings still get the painful initial lag.  And there is still a lag for the subsequent lookups of the same domain.

At this point I'm at a loss.  I'm hoping the fact that dig/nslookup is fast vs ping being slow might mean something to someone.

Thanks for any help.

---

### Post by ctsdownloads on 2008-05-18
> **williumbillium said:**
> First of all, perhaps it would be more appropriate for this post to be in the Networking forum, if so, please move it.  I posted here since it's regarding a System76 laptop.

I am experiencing slow DNS lookups.  Usually browsing is fine for a few minutes or, sometimes, even hours but then, every time I lookup a domain I see "Looking up www.domain.com" in Firefox's status bar for about 10 seconds before the page begins to load.  Issuing ping commands is similar, there is a 10 second lag before anything happens, but the time for each ping is normal.

Basically, general download speed is fine but the initial lookup is very slow.

My Setup:

Daru2/Ubuntu Gutsy/wrt54gl router (happens when connected wired or wireless)

There is also a wired desktop on the same network running kubuntu gutsy that has no network issues.

Interestingly enough, when I connect to another wireless router I don't have this problem.

What I've tried:

Disable ipv6 in Firefox

Delete all reference to ipv6 in /etc/hosts, added "blacklist ipv6" to /etc/modprobe.d/blacklist

Use OpenDNS servers for DNS on Daru2 and router (208.67.222.222, 208.67.220.220)

None of this helped.

As a last resort I even tried local DNS caching (following this guide: [http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/) ).  That improved the speed of lookups using dig or nslookup, but web browsing and pings still get the painful initial lag.  And there is still a lag for the subsequent lookups of the same domain.

At this point I'm at a loss.  I'm hoping the fact that dig/nslookup is fast vs ping being slow might mean something to someone.

Thanks for any help.

What are your ping times when pinging something like Yahoo.com from a terminal?

At any rate, this might be of some help:
[http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)

---

### Post by laserline on 2008-05-18
I'm having the same problem.

Turning off wireless and turning it back on (using the network applet) resolves this issue.

I thought I was alone with this...

Idan.

---

### Post by gaussian on 2008-05-18
I had this as well. 

Problem:
Ubuntu tried to use when connecting to wireless via DHCP local (wireless router, DSL modem) DNS servers instead of ISP's DNS servers.

Symptoms:
Really slow DNS resolution

Solution:
Check you /etc/resolv.conf file. If it has something like
```

nameserver 192.168.1.1
nameserver 192.168.2.1

```
then you are probably have the same problem as I had. Easy fix: put 
```

prepend domain-name-servers  YOURISPSDNS;

```
where YOURISPSDNS is your DNS-server to
/etc/dhcp3/dhclient.conf

---

### Post by laserline on 2008-05-19
Hi Gaussian,

Doing that will cause problems when roaming to other wireless networks, wouldn't it ?

Thanks,

Idan.

---

### Post by gaussian on 2008-05-19
> **laserline said:**
> Hi Gaussian,

Doing that will cause problems when roaming to other wireless networks, wouldn't it ?

Thanks,

Idan.

Unfortunately, yes in theory. In practice, I haven't had any problems, my ISP's DNS has been quickly reachable from almost everywhere I go. The only time I have noticed any performance problems was when I was abroad using a WIFI at hotel abroad (Germany). But my ISP's nameserver was fine in other locations on that trip. If you run into problems, you can always manually comment out the nameserver lines for your ISP in /etc/resolv.conf.

I am not really a computer guy, just a hobbyist, but my understanding is that at least my problem here was due to idiotic configuration (that I could not find an easy way to change) of my Belkin wireless router. It was the modem that was forcing the slow DNS servers.

---

### Post by freduardo on 2008-05-19
I had somewhat the same issue (with an MSI PR200, so a daru2).

I have been doing the same thing Gaussian suggested but with OpenDNS's servers (208.67.222.222 and 208.67.220.220).

So far so good. Works both at home, at my school and at my sister's. Although I haven't been abroad with it yet.

---

### Post by gaussian on 2008-05-19
Maybe it is worthwhile to mention that in my household this problem affected my Mac Powerbook and my Mandriva Desktop too. So it really was a problem with router+modem settings that needed a workaround in all the computers regardless of their OS.

---

### Post by williumbillium on 2008-05-19
Thanks for all the replies :)

> **ctsdownloads said:**
> What are your ping times when pinging something like Yahoo.com from a terminal?

At any rate, this might be of some help:
[http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)

Ping times are pretty normal.  In the region of 80ms for something like yahoo.com.

I had already tried local DNS caching, see my original post.  To be honest I don't think that's much of a fix, more of a work around to make the underlying problem more bearable...

> **gaussian said:**
> I had this as well. 

Problem:
Ubuntu tried to use when connecting to wireless via DHCP local (wireless router, DSL modem) DNS servers instead of ISP's DNS servers.

Symptoms:
Really slow DNS resolution

Solution:
Check you /etc/resolv.conf file. If it has something like
```

nameserver 192.168.1.1
nameserver 192.168.2.1

```
...

I changed my resolv.conf pretty early on to the opendns ips.  It didn't help but thanks for the suggestion.

At this point, things have actually been working well for several hours.  I rebooted after making my original post and one of the last changes I made must have come into effect.  I think, and I'm not sure, that changing the hosts line in /etc/nsswitch.conf from:

```
hosts:          files wins dns
```

to:

```
hosts:          files dns wins 
```

is what fixed it.  But at this point, I'm not sure.  Hopefully things stay as they are now!

For anyone else reading this looking for answers, from my research on the forums, it seems like there are a lot of ways dns lookups can be slow! Here are some similar threads with solutions I tried first:

[http://ubuntuforums.org/showthread.php?t=791470&highlight=slow+dns](http://ubuntuforums.org/showthread.php?t=791470&highlight=slow+dns)
[http://ubuntuforums.org/showthread.php?t=785653&highlight=slow+dns](http://ubuntuforums.org/showthread.php?t=785653&highlight=slow+dns)
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/134660)
[http://ubuntuforums.org/showthread.php?t=718709&highlight=lynx+firefox&page=2](http://ubuntuforums.org/showthread.php?t=718709&highlight=lynx+firefox&page=2)

---

