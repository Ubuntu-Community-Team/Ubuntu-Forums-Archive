---
title: "Apache2 Aliases"
date: 2018-06-12
forum: Server Platforms
---

### Post by warmango on 2018-06-12
So im working on recreating my webserver inside a VM on my PC, I have Uby16.04-32bit server installed along with Apache2, Im trying to have a redirect from **MyDomain.com:8040 **to [B]MyDomain.com/page

[/B]Its rather annoying and I cant seem to find anything to solve this issue.

---

### Post by howefield on 2018-06-12
Thread moved to the "*Server Platforms*" forum.

---

### Post by LHammonds on 2018-06-12
> **warmango said:**
> So im working on recreating my webserver inside a VM on my PC, I have Uby16.04-32bit server installed along with Apache2, Im trying to have a redirect from **MyDomain.com:8040 **to [B]MyDomain.com/page

[/B]Its rather annoying and I cant seem to find anything to solve this issue.
So you are taking visitors hitting your domain on port 8040 and re-directing to port 80 and then to a specific page?
Have two site config, one listening on port 8040 with a single index page that re-directs to the desired URL.  The other config would be listening on port 80.

LHammonds

---

### Post by warmango on 2018-06-12
> **LHammonds said:**
> So you are taking visitors hitting your domain on port 8040 and re-directing to port 80 and then to a specific page?
Have two site config, one listening on port 8040 with a single index page that re-directs to the desired URL.  The other config would be listening on port 80.

LHammonds
Sorta but not exactly, I have a program (ShellInaBox) that runs off a specific port, in my case i have it set to 8040, What i want to have, is instead of going to "mydomain.com:8040", i want to beable to got to "mydomain.com/shell" 

Ive done it before, but that was on a Server my Teacher let me tinkerwith, and i nolonger have access to pull the Config File,

It used a proxy config inside the /etc/apache2/apache2.conf file at the bottom

---

### Post by volkswagner on 2018-06-13
What you're looking for is reverse proxy.

See if [this how to]("http://ubuntuforums.org/showthread.php?t=1920715") helps.
It's written for two servers, but you can substitute localhost or the same server's ip for the remote server ip.

You'll need to modify the config file for port number and folder location.

---

