---
title: "web server width ...?"
date: 2009-04-24
forum: Server Platforms
---

### Post by sartic on 2009-04-24
Looking for web server which I can apply to low bandwidth (upload is only 256Kb). I want to have:
1. compression for html and similar files
2. balance in sending packets to all IP clients connected
3. maximum connections per minute (4 users max, 5th will have page width message that he is in quee)
On this web server will be served only html, java script and some flash (no php, asp and similar) 
Any idea?

---

### Post by mrsteveman1 on 2009-04-24
Most of them support gzip compression so that isn't a problem. Load balancing is more of a network thing (QoS), but its possible some httpd has the ability to do this, maybe an apache module. I'm not aware of any built in capability for the httpds i work with though.

Most web servers also do limiting by simultaneous connections and not connections per minute, in apache you can set the maxclients directive to 4 and that will limit total connections to 4 at a time, putting others in a queue. However they will not be shown any sort of queue page, it will just pause the browser as if the site was overloaded (technically  it is since you set only 4 connections).

As for showing someone a queue page, thats probably something to be done in javascript or php on the backend, somewhat like how rapidshare etc work.

---

### Post by sartic on 2009-04-24
I found some small httpd in repos and i will try busybox.

---

