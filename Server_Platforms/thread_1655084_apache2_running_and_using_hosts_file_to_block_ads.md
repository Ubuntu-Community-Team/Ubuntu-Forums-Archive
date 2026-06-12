---
title: "apache2 running and using hosts file to block ads"
date: 2010-12-29
forum: Server Platforms
---

### Post by tynin on 2010-12-29
I have apache2 running on and by default it is answering requests on both the IP address I have bound to eth0 as well as anything it considers a loopback (127.0.0.1, 0.0.0.0). I also have in my /etc/hosts file a huge list of ad servers that I redirect to my loopback to avoid ever having to waste my bandwidth fetching them.

My issue is that I would like to have apache2 never answer anything if it is coming from a loopback address. 

I've already setup an .htaccess to deny traffic from my loopback, however that still involves apache2 having to process the request even though it is just a deny (which causes my error_log to file up quick as well as spike my cpu usage much more so then without having the huge hosts file). How can I configure apache2 to not bind to the loopback so it never gets these requests?

---

