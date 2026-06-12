---
title: "Proxy Server cannot caching youtube, why? :("
date: 2013-04-08
forum: Server Platforms
---

### Post by fendie pablo on 2013-04-08
since March 2013, my Proxy Server cannot caching videos from youtube anymore, I used Lusca as Proxy Server in Ubuntu Server 12.04
is there something wrong with my squid and storeurl? anyone can help me? I'm new in Ubuntu.. please help..
thankyou verymuch

---

### Post by woxuxow on 2013-04-08
Probably it is because of youtube technology not your squid setting
Preventing video from downloading

---

### Post by fendie pablo on 2013-04-08
yes..
but sometimes youtube video player also displays unwanted video ..
is there any enlightenment?

---

### Post by cerealcable on 2013-04-10
Caching youtube video is tricky at best since so much comes from multiple servers.  It isn't as simple as we'd hope.  I know I haven't had a chance to see it working yet, there are many older posts on this topic but they look quite outdated at this point and probably don't work.

You would probably require to record the http sessions that occur and see what is actually happening and build a config to save those objects.  I've tried to caches files from multiple domains but never seemed to figure it out on squid.  I've heard better things about nginx to do this, but I haven't looked into it.

---

