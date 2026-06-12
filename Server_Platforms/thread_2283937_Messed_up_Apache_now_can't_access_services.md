---
title: "Messed up Apache now can't access services"
date: 2015-06-25
forum: Server Platforms
---

### Post by roadwarrior2 on 2015-06-25
So I was trying to use SSL on ownCloud on my personal server. I had the server running smoothly with CouchPotato, Sick Beard, Plex, Museek, and lots more. While trying to the the virtual host going for owncloud I did something wrong and now I can access some services and others I can't. I can't access Webmin, CouchPotato and others but some other services I can access fine. They all have different Ports. I don't understand what I did that would make some work and others not. I removed and  reinstalled Webmin and apache and I still have the same issue. I am running Ning Ubuntu Server 14.04

---

### Post by TheFu on 2015-06-26
Would posting the different apache config files so someone can help be possible?

I would just restore from a backup from before I started mucking around.  With a complex setup like on the system there, I'd want really great, automatic, daily, backups.

Instead of using SSL, have you considered openvpn?

---

