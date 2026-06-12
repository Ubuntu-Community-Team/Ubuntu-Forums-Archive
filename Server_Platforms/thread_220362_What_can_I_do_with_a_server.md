---
title: "What can I do with a server?"
date: 2006-07-21
forum: Server Platforms
---

### Post by ubuntu1 on 2006-07-21
I've been using Ubuntu since it launched. However I have absolutely no experience of setting up and running a server so I thought I should try it on a spare machine. What would you suggest I try on my new server box? any suggestions appreciated.

---

### Post by Paerez on 2006-07-21
The best thing to try first, imo, is a web server, like apache or lighttpd, because you get instant results!

And because of services like dyndns.org, you can even have your own site for free.

I run a web/torrent/music/photo/video/blog server using dyndns and linux, and the total cost was $10 a year for two domain names. And the server cost <$300. Yay linux!

---

### Post by DigitDuke on 2006-07-21
> **Paerez said:**
> I run a web/torrent/music/photo/video/blog server using dyndns and linux, and the total cost was $10 a year for two domain names.

**Off-topic:** Hmm... where would one get such a deal?

Anyways, I do agree with Paerez, starting with a web server is very easy - Ubuntu even offers a [LAMP](http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29) installation out of the box.

And if you'd like to know how to do it yourself, you can always go for [Howtoforge's step-by-step "Perfect Setup" tutorial]("http://howtoforge.org/perfect_setup_ubuntu_6.06_p3").  And if you have no use for a web server (although I highly recommend it, if not only for the experience of it), you could take an extra computer and make it your backup server.

---

### Post by Paerez on 2006-07-21
the domains were from 1and1.com, and it was actually $12 ($6 each).

---

### Post by ubuntu1 on 2006-07-21
Thanks for the advice guys. I'll try with a web server and take it from there.

---

### Post by kaptainlange on 2006-07-21
> **Paerez said:**
> the domains were from 1and1.com, and it was actually $12 ($6 each).

Are you using DynDNS's customDNS service too to point dynamic ip's to those domains, or is it static?  I'm paying 39 bucks a year for the domain and customDNS service.

---

### Post by Paerez on 2006-07-21
I use dyndns's free dns to point my server to one of their places. Lets call it "site.dyndns.org" then I paid $6 to 1and1, and set 1and not to an ip, but to a CNAME. The CNAME is set to site.dyndns.org. So you see "site.com" and "site.com/~user/index" but it really directs all the traffic behind your back to site.dyndns.org.

So i have a dynamic ip which maps to a constant url, which my url maps to

dynamic ip -> site.dyndns.org -> site.com

---

### Post by kaptainlange on 2006-07-21
> **Paerez said:**
> I use dyndns's free dns to point my server to one of their places. Lets call it "site.dyndns.org" then I paid $6 to 1and1, and set 1and not to an ip, but to a CNAME. The CNAME is set to site.dyndns.org. So you see "site.com" and "site.com/~user/index" but it really directs all the traffic behind your back to site.dyndns.org.

So i have a dynamic ip which maps to a constant url, which my url maps to

dynamic ip -> site.dyndns.org -> site.com

Darn, didn't know you could point a domain name to another domain name through that service.  Just renewed for another year last week too.  I'll keep that in mind next year, thanks for the info.

---

### Post by az on 2006-07-21
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

