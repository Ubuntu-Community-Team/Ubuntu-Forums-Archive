---
title: "Help using SquidGuard time Constraints"
date: 2007-10-24
forum: Server Platforms
---

### Post by mymate on 2007-10-24
Im having problems using the time contraints in squidguard 1.2.0

When i add them to my squidguard.conf and restart squid it says "The proxy is refusing connections"

When i am simply just filtering webpages my conf works fine, anyone with some experience with squidguard be able to help me?

Any help would be greatly appreciated

I've included my squidguard.conf

> 
#
# CONFIG FILE FOR SQUIDGUARD
#

dbhome /var/lib/squidguard/db
logdir /var/log/squid

time workhours {
	weekly mtwhf 08:40 - 12:00
	weekly mtwhf 14:00 - 16:50
}
dest ads {
        domainlist	ads/domains
	urllist		ads/urls
}
dest aggressive {
        domainlist	aggressive/domains
	urllist		aggressive/urls
}
dest audio-video {
        domainlist	audio-video/domains
	urllist		audio-video/urls
}
dest gambling {
        domainlist	gambling/domains
	urllist		gambling/urls
}
dest hacking {
        domainlist	hacking/domains
	urllist		hacking/urls
}
dest porn {
        domainlist	porn/domains
	urllist		porn/urls
}
dest proxy {
        domainlist	proxy/domains
	urllist		proxy/urls
}
dest redirector {
        domainlist	redirector/domains
	urllist		redirector/urls
}
dest spyware {
        domainlist	spyware/domains
	urllist		spyware/urls
}
dest suspect {
        domainlist	suspect/domains
	urllist		suspect/urls
}
dest violence {
        domainlist	violence/domains
	urllist		violence/urls
}
dest time-wasting {
        domainlist	time-wasting/domains
}
acl {
        all outside workhours {
                pass all
        }
        else {
                pass  !ads !aggressive !audio-video !gambling !hacking !porn !proxy !redirector !spyware !suspect !violence !time-wasting all
        }
        default {
                pass    none
                redirect [http://localhost/block.html](http://localhost/block.html)
                }
}

---

### Post by HermanAB on 2007-10-24
Have a look at this guide: [http://www.aeronetworks.ca/squidguard-howto.html](http://www.aeronetworks.ca/squidguard-howto.html)

Cheers,

Herman

---

### Post by mymate on 2007-10-24
that website contains a very good sample and managed to get my conf working 100% now, thanks for your help!

---

