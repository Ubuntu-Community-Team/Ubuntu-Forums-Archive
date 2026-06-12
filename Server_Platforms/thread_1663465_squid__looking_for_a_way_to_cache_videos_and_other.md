---
title: "squid | looking for a way to cache videos and other stuff"
date: 2011-01-09
forum: Server Platforms
---

### Post by elico on 2011-01-09
im using SQUID 2.7 on my LAN cause most of the sites that we are using are the same.
so.. i want to cache as much as i can.
CSS for sure.. pictures..
and also videos from  some sites.
in any case
I need help settings up squid for the mission.
i have some things in mind.

as for maximum objec size...
overiding the leas time for the cache.

i also built a nice script to precache sites using wget and recrusinve download.

so i will be verry happy to hear some recommendations.
also if you are working in an ISP and you now some inside about software they use to cache youtube videos and other stuff i will be more then happy to hear it.

---

### Post by liverpoolatnight on 2011-01-10
Hello :) 

set it to something like:
**cache_dir** ufs c:/squid/var/cache [COLOR="Red"]1024[/COLOR] 16 256
([COLOR="Red"]1024 = 1GB[/COLOR] max swap) and [COLOR="Blue"]2048[/COLOR] = 2GB

and you might also want to change maximum_object_size to make sure big-ish stuff gets cached with Dynamic sites:

[COLOR="Sienna"]**acl dynamic_sites dstdomain .youtube.com**[/COLOR]
acl dynamic_sites dstdomain .facebook.com
acl dynamic_sites dstdomain .google.co.uk
acl dynamic_sites dstdomain .twitter.com
acl dynamic_sites dstdomain .bbc.co.uk
acl dynamic_sites dstdomain .imgur.com

cache allow dynamic_sites
Heres my list i will share just copy and paste this text file. [http://pastebin.com/4DL2z7eX](http://pastebin.com/4DL2z7eX)

I put that before hierarchy_stoplist cgi-bin ? in the config file. Getting a lot more cache hits now.

About 20%-25% of hits to sites like Google and Facebook, etc now use the cache. I think by default Squid won't cache any dynamic site stuff at all (not even the static images and stuff on dynamic sites).

:P hope this helps.

---

### Post by elico on 2011-01-10
well i did some other stuff that works already for these sites.
my problem is with the videos themsef.

but whatever.

i did some reaserch about it.
there is a software that does that and i need to do some work in order to make it really work.

i need to now the stuff about how it works inside squid..

---

