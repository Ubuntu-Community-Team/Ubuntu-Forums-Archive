---
title: "Squid cache questions"
date: 2007-11-16
forum: Server Platforms
---

### Post by seanlivo on 2007-11-16
Hi guys, I have setup squid to try and cut back on some bandwidth. Squid seems to be caching the files but don't for long (not more then a day anyway), I'm not sure what and where the default setting is for how long squid keeps files in cahce but I cannot find anything in the conf file.

Also I have told squid to 1000mb ram and 40000mb but I have never seen it use more the  280mb ram and 3.4gb HD space

I was going to post my conf file but it seems to big with all the extra info that is # out and I think there is way to extract the real lines isn't there?

Thanks in advance

---

### Post by HermanAB on 2007-11-17
Hmm, I have used squid in the past and it was very reliable.  I think you need to visit the project web site and read some and join their mailing list [http://www.squid-cache.org/](http://www.squid-cache.org/)

---

### Post by pete.dawgg on 2007-11-19
> cut back on some bandwidth.
for bandwidth-regulation you can use delaypools in squid. (I'm not sure if that's what u really want)

> Squid seems to be caching the files but don't for long (not more then a day anyway), I'm not sure what and where the default setting is for how long squid keeps files in cahce but I cannot find anything in the conf file.

more than squid itself the website-devs control how long stuff is being cached. you can force stale content to be kept in the cache with a couple of paramters (eg reload_into_ims), but some of that might violate the http-standard (can be fun, though ;)  )

> I have told squid to 1000mb ram and 40000mb but I have never seen it use more the 280mb ram and 3.4gb HD space
maybe it just doesn't need any more? how many users do you serve and how necessary is it to keep (stale) content inside the cache?

you may want to write the config from scratch so squid will do EXACTLY what u want it to, there's an excellent guide on their website ([www.squid-cache.org](www.squid-cache.org))

> I was going to post my conf file but it seems to big with all the extra info that is # out and I think there is way to extract the real lines isn't there?

sth. like ```
sed '/^#/d' /etc/squid/squid.conf 
``` might work.

---

