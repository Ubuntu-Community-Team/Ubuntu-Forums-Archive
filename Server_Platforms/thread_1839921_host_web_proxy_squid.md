---
title: "host web proxy squid"
date: 2011-09-06
forum: Server Platforms
---

### Post by chaosdesigner on 2011-09-06
hey guys,

so you all know those popular webproxies like hidemyass or proxify, I want to host something familiar on my ubuntu server, with the only difference being that its only specialized on one certain website. So user A visits my website and gets to see site B exactly how it is, only with a filter for maybe adblocking running over it.

Is something like this possible with squid? Or would I need some other kind of proxy software? Has anyone has experience with something like this?

I apologizes if this might be a foolish question to ask, I'm fairly new to server administration. 

Thank you in advance!

---

### Post by SlugSlug on 2011-09-07
Yer I've done this with squid (not the adblock bit tho)

found it better using a ssh tunnel though if thats the kinda thing your after 
[http://ubuntuforums.org/showthread.php?t=723025](http://ubuntuforums.org/showthread.php?t=723025)

---

### Post by SeijiSensei on 2011-09-07
Using [Apache as a proxy]("http://httpd.apache.org/docs/2.2/mod/mod_proxy.html") might be easier to configure.  squid.conf can be pretty hairy.

---

### Post by rubylaser on 2011-09-07
EDIT: I just re-read your post. Shame on me for skimming, what SeijiSensei gave you is the way to go.

---

### Post by chaosdesigner on 2011-09-07
Thank you for your quick replies. I will defiantly look into using apache as a proxy. Going to try to update this thread for further source of information.

**EDIT:** I've been looking into Apache Proxy, and it seems quite easy to set up and configure. I think the reverse proxy would be the way to go for me, since I want to use it as some kind of webproxy. The only set back I am having right now is that I can't find any mod for the apache proxy that lets me tamper with the data that is being channeled. As I said in the OP, I want to be able to block certain ads and even maybe add some code in some places (keep in mind that I only want to focus on one website, so the same patterns could be reused). 

After some googleing I only found some good tutorials on adblocking with squid, but how would I do it with the apache proxy? Could I maybe configure the mod_cache in certain ways so it can filter out code I want to be hidden from the client?

---

