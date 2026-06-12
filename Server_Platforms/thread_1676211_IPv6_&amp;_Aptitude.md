---
title: "IPv6 &amp; Aptitude"
date: 2011-01-26
forum: Server Platforms
---

### Post by ctimko on 2011-01-26
Hello Community!

I was wondering how I go about doing updates when my system is purely IPv6? (If this already works, then my issue probably lies in the fact that I am having issues communicating with any of the Root servers, yet I can ping the servers...and I verified them against what IANA and ICANN has).

Thanks,

Charles Timko

---

### Post by kevinthecomputerguy on 2011-01-26
I have Charter as my ISP, pure IPv6, no apt issues.
 
Hope this helps.
 
can you ping [www.google.com]("http://www.google.com") ?
 
-Kev

---

### Post by lemming465 on 2011-01-27
I've seen ubuntu providing IPv6 torrents, but I'm not aware that the mirrors distributing repository updates are dual-stacked yet.  I think you need to be dual-stacked with IPv4 + IPv6 for at least the next two or three years.

Congratulations on having native IPv6, if that's what your ISP is offering.

---

### Post by ctimko on 2011-01-27
Does anyone have any public IPv6 nameservers I could use?  Because apparently I can't resolve!

Also, it's my server..it's on a pure IPv6 network (according the trace-route anyway)

---

### Post by kevinthecomputerguy on 2011-01-27
Try these.
 
ns1.everydns.net, ns2.everydns.net, ns3.everydns.net, ns4.everydns.net
 
or these
 
resolver1.dyndnsinternetguide.com, resolver2.dyndnsinternetguide.com

---

### Post by ctimko on 2011-01-28
Alright, thanks, I will give those a try.

---

### Post by ctimko on 2011-01-28
Those are all IPv4 DNS resolvers!

I found a good public dns: 2001:470:20::2, however Security.ubuntu.com does not have an IPv6 address...that said, anyone have any luck using Apt-get on a machine that only has IPv6 and not an ounce of IPv4 (no IPv4 tunneling or dual-stacking)

---

### Post by ctimko on 2011-01-31
bump...someone has to know something...

---

