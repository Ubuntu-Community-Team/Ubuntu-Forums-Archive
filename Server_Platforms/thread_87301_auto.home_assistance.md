---
title: "auto.home assistance"
date: 2005-11-07
forum: Server Platforms
---

### Post by ejkeebler on 2005-11-07
ell read the threads still confused.

I have on server.domain.com autofs, NIS, portmapper and NFS running. I can login to any client as the NIS users, but of course no home drive. I am trying to get the home drive from the server.domain.com

auto.master on server.domain.com
/home /etc/auto.home

auto.home on server.domain.com and on client.domain.com
* -defaults,nousid server.domain.com:/home/&

what else do i need to do here? and does anyone know a good howto or walkthrough for autofs? I searched the web on autofs, auto.master, auto.home and really didnt find any that talked about the whole user (&) variable???

---

