---
title: "DSL and Cable on Same Server"
date: 2007-11-23
forum: Server Platforms
---

### Post by mlapaglia on 2007-11-23
Hello everyone, I've got a few n00b questions if you could take a minutes to flame.. so pull out your :popcorn: and get ready to :lolflag: at me.



I am currently living in an apartment with 3 other roomates. two of us have different ISP connections, i have cable, and my roomate has dsl. I am looking for a way to combine the both of these connections the same way something like [http://shopping.redorbit.com/product.php?productid=8139606&MMCF_froogle_feed&utm_id=1&utm_source=froogle&utm_medium=feed&utm_campaign=Froogle+Feed](http://shopping.redorbit.com/product.php?productid=8139606&MMCF_froogle_feed&utm_id=1&utm_source=froogle&utm_medium=feed&utm_campaign=Froogle+Feed)
would do, only without the expensive price tag.

I've heard load balancing is a capability of an ubuntu server.

Is there a way to plug two different ISP's into a server, and have it "merge" the internet connection, theoretically doubling bandwith?

any help is appreciated. I hope i could give you a good laugh.

---

### Post by HermanAB on 2007-11-23
See the Advanced Routing Howto at tldp.org

Cheers,

Herman

---

### Post by mlapaglia on 2007-11-24
i looked at that site, and i was discouraged not seeing any ubuntu related solutions to my problem.

then i got "segwayed" into ebox, and i noticed the server version of ubuntu comes with this installed...

ebox has the ability to combine two nics into one per say, now i need to find a n00b guide ;)

---

### Post by herbie_popnecker on 2007-11-24
I was trying to do the same thing for years, it was too beyond my skill level.
Then I found this dual gateway router for $100 and installed it. It seemed to work great for a few hours, then it would switch from one to the other supposedly balancing and stop traffic... if you ping it you'd see about 2 minutes of steady pings, miss 4 then 2 more minutes steady over and over. Just enough to make everyone wireless have to reconnect...
I eventually gave up and shelled out a heap of dough for a faster connection....

---

### Post by koenn on 2007-11-24
> **mlapaglia said:**
> i looked at that site, and i was discouraged not seeing any ubuntu related solutions to my problem.
)
What you're asking has to do with routing and the sollution is to be found in the routing functions of the kernel; the tcp/ip stack and tools such as ip-route and netfilter/iptables. These are common to all Linux,   it really doesn't matter what distro you're using at this level. 
However, some distros specialize in routing and may offer features to make such a setup easier. Ubuntu is not one of them : Ubuntu specializes in desktop use, not routing / advanced networking.

---

