---
title: "Need help on server administration"
date: 2008-11-14
forum: Server Platforms
---

### Post by serverCrazy on 2008-11-14
Hi guys, i am a intermediate user of ubuntu (but i am a ubuntu lover). I have a server which i use ISPconfig for virtual hosting, however, i would like to know about server administration.

what to look for? (logs files, users files)
what to delete? (cache, tmp)

Basically, i dont know anything on administration, so if somebody could help me on that would be great. Also note that i am talking about administration of the performance of the system.

Could somebody help me with that?

---

### Post by mssever on 2008-11-15
> **serverCrazy said:**
> Hi guys, i am a intermediate user of ubuntu (but i am a ubuntu lover). I have a server which i use ISPconfig for virtual hosting, however, i would like to know about server administration.

what to look for? (logs files, users files)
what to delete? (cache, tmp)

Basically, i dont know anything on administration, so if somebody could help me on that would be great. Also note that i am talking about administration of the performance of the system.

Could somebody help me with that?
Could you be more specific? Server administration is a HUGE topic. I suggest you start by reading the documentation for whatever server(s) you're running. You implied that you're running a webserver, but you didn't say for sure (remember, there are many types of server), and you didn't say which one.

---

### Post by serverCrazy on 2008-11-16
i am looking for a performance administration guide on something like that.

I am using ubuntu 8.10.

where should i always be looking at?

---

### Post by Philio on 2008-11-16
It might help if you describe a little about what your hosting on your server, how much traffic your getting, servers specs too possibly.

---

### Post by Thirtysixway on 2008-11-16
In performance terms, I'd suggest lighttpd over apache if you're running it.  It uses less system resources, and serves pages faster

[http://blog.noobbox.com/2008/09/apache-vs-lighttpd.html](http://blog.noobbox.com/2008/09/apache-vs-lighttpd.html)

I did a small benchmark test, and it shows lighttpd serves requests faster.

---

### Post by hictio on 2008-11-16
> **serverCrazy said:**
> Hi guys, i am a intermediate user of ubuntu (but i am a ubuntu lover). I have a server which i use ISPconfig for virtual hosting, however, i would like to know about server administration.

what to look for? (logs files, users files)
what to delete? (cache, tmp)

Basically, i dont know anything on administration, so if somebody could help me on that would be great. Also note that i am talking about administration of the performance of the system.

Could somebody help me with that?

Can you spend a some money? If yes, I would suggest: [Linux System Administration](http://oreilly.com/catalog/9780596009526/#top).
After this one, read this ones:
[Linux Server Hacks](http://oreilly.com/catalog/9780596004613/?CMP=AFC-ak_book&ATT=Linux+Server+Hacks#top)
[Linux Server Hacks, Volume Two](http://oreilly.com/catalog/9780596100827/#top)

These are NOT Ubuntu specific.

---

