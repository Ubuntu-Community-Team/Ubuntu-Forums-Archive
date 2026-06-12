---
title: "Slow DNS update"
date: 2017-08-22
forum: Server Platforms
---

### Post by boffen1 on 2017-08-22
Hi,
I got some delay/issue with my DNS server and hope someone can explain why.
I have installed my own dns server for my own domain, with Ubuntu/Bind.
Two days ago I updated a few ip adresses pointing to my domain and some people still have problem to access my site from Internet. I can verify the update with two public dns servers, 8.8.8.8 and 4.2.2.1, and they respond with the correct updated ip addresses.
But there are serveral users using other dns servers that still not have got the updated values.

This is my settings in Bind for my zones.
$TTL 604800
3600 Refresh
600 Retry
1209600 Expire
3600 negative Cache TTL

Shouldn't other dns servers update their info every 3600 seconds?
Is there any "best practise" values to use for faster "updates" on Internet?
My domain is small so their are not many records or requests to my dns server.

Thanks for any inputs!

---

### Post by TheFu on 2017-08-27
No. The 3600 doesn't force updates, it forces a check of the cache.  Every DNS record has a number that must be incremented with every change. It just needs to be larger than the last time it was seen. [https://serverfault.com/questions/345331/dns-records-serial-number](https://serverfault.com/questions/345331/dns-records-serial-number)

I haven't dealt with DNS on my own since being hacked through it in 2002.  Please be certain you keep bind patched, running inside a chroot, and running on a properly secured box. Your primary/master BIND server shouldn't be on the internet at all. 

[https://insights.sei.cmu.edu/sei_blog/2017/02/six-best-practices-for-securing-a-robust-domain-name-system-dns-infrastructure.html](https://insights.sei.cmu.edu/sei_blog/2017/02/six-best-practices-for-securing-a-robust-domain-name-system-dns-infrastructure.html)

Also, did you see that all DNS keys were being replaced?  I don't remember if that happened this week or when it was planned to occur.  You'll want to know.

---

