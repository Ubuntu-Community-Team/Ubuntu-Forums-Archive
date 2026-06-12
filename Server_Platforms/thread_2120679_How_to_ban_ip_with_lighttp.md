---
title: "How to ban ip with lighttp ?"
date: 2013-02-27
forum: Server Platforms
---

### Post by jaho22 on 2013-02-27
I have Ubuntu 10.04 with lighttp, i now want to ban an ip that is loading my site image folder, about 5 times in one minute, it is searching one of site images that dont exist anymore.

How can i give a ban to an ip with lighttpd on ubuntu 10.04 ?

---

### Post by The Cog on 2013-02-27
I'm not sure you can. You should be able to ban it using iptables like this (change the IP address to suit):
```
sudo iptables -A INPUT -s 1.2.3.4 -j DROP
```

---

### Post by Drenriza on 2013-02-27
> **jaho22 said:**
> I have Ubuntu 10.04 with lighttp, i now want to ban an ip that is loading my site image folder, about 5 times in one minute, it is searching one of site images that dont exist anymore.

How can i give a ban to an ip with lighttpd on ubuntu 10.04 ?

To ban someone is not a light decision.
I don't know what site you have, but ISP's from time to time dynamically change their customers public ip address, unless they have purchased a static one.

Also this user could come from a tor network and you might end up banning him forever on one ip address, and then he just comes back on another.
But you have then banned the next user who gets the banned ip.

Or it can be a big firm with 1.000 employers, where 1 of them searches your site from their public IP. And you ban the 999 rest.

If you ban an ip address, you should consider un-banning it again at a specific time.
Like 10 hours, 2 days, 1 week, 1 month or something else.

---

### Post by The Cog on 2013-02-27
Drenriza has a good point.

I know that many ISPs allocate IP addresses dynamically - all their user's addresses are liable to change every few days or weeks. And some ISPs are starting to use NAT bacause of the shortage of IP addresses. In the case of an ISP using carrier-grade-NAT, your server would simply seem to become intermittently unresponsive to every user on that ISP.

---

### Post by TheFu on 2013-02-27
> **Drenriza said:**
> To ban someone is not a light decision.
I don't know what site you have, but ISP's from time to time dynamically change their customers public ip address, unless they have purchased a static one.

Also this user could come from a tor network and you might end up banning him forever on one ip address, and then he just comes back on another.
But you have then banned the next user who gets the banned ip.

Or it can be a big firm with 1.000 employers, where 1 of them searches your site from their public IP. And you ban the 999 rest.

If you ban an ip address, you should consider un-banning it again at a specific time.
Like 10 hours, 2 days, 1 week, 1 month or something else.

I ban IPs all the time, but usually not individual IPs, rather entire subnets. These are my resources.  With each ban, I consider the likely purpose for the subnet.

For example, I ban Baidu Search engine completely. They were ignoring the robots.txt.  In a single month, their indexing my sites incesently - abusively - eating 5x more bandwidth than google ate, only 1 referral came back.
Banned.

On my blog, I was getting lots-o-blog spam from non-English speaking counties.  I ended up finding subnet lists by country and just started banning entire blocks inside a few different countries. These blocks are huge - /8 is common from China.  Oh well.  Much of Russia, Ukraine and Romania are blocked as well.  Too much blog spam.  Either the source addresses are hacked or they are pushing huge amounts of blog spam. Either way, blocked.

These are my servers.  Just like any restaurant can refuse service to anyone for almost any reason, I can refuse access to my servers and content similarly.

I used to feel bad about blocking anyone, but as blog spam increased, I started carrying less and less.  A few rotten apples ruin the entire bushel.
After a few weeks of 100+ blog spams daily, I implemented a Captcha - it reduced the blog spam to zero for about a week.  Slowly it has increased a little, but never more than 10 spam posts a day. I can deal with that.

I use nginx as a reverse proxy and load balancer.  nginx has methods to redirect based on all sorts of information - IP, user agent, etc.

These are my servers.

I will consider unblocking a few subnets to see if it impacts the amount of blog spam. I do not have much hope that this will work out well. Places hacked once are likely to be hacked again and again, IME.

---

### Post by jaho22 on 2013-02-27
I found an answer to my problem, the following lines are very helpfull to me -

ban one ip -
$HTTP["remoteip"] =~ "1.2.3.4" {
url.access-deny = ( "" )
}

Ban many ips
$HTTP["remoteip"] =~ "1.2.3.4|2.3.4.5|3.4.5.6" {
url.access-deny = ( "" )
}

---

### Post by TheFu on 2013-02-27
[QUOTE=jaho22;12533318]I found an answer to my problem, the following lines are very helpfull to me -

You probably want to ban a subnet, if that is supported, something like this:
```
1.2.3.0/24

```or 
```
1.2.3.0/255.255.255.0
```
is what you want.  Much more efficient from a network perspective.

---

