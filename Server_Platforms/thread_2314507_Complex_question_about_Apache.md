---
title: "Complex question about Apache"
date: 2016-02-21
forum: Server Platforms
---

### Post by isaac17 on 2016-02-21
HI ubuntu community,
I have this situation and I'm not sure if it's possible but I'll explain it ..
So I an apache server behind a router, lets call it apache1
I have another apache server(apache2) and I want to get the content from apache1
Apache2 is publically open for everyone, but the content that I want to show from apache1 in apache2 is viewable?
The idea here is to leave router untouched and show apache1's content on apache2's server.
Is this possible? Do i need to make a tunnel between apache1 to apache2?
I've been searching forever and I don't where to start. 
I know there's this iframe but the client is requesting directly from apache1
Thank you for reading and helping

---

### Post by darkod on 2016-02-21
I don't understand... Do you need a constant sync? Will the content on apache1 change so often that you need a constant sync to apache2?

Otherwise you can simply upload content manually...

For constant sync you would have to do scheduled rsync from apache1 to apache2 which is very easy too. You simply sync the folder(s) you want to, and that's it. If apache2 has a static public IP that makes it even more easier...

---

### Post by isaac17 on 2016-02-21
Ok then, apache1 is 192.168.0.5:8000 and i want to show it through another server. Maybe it doesnt need to be an apache but something that can show. Virtualy displaying apache1 on another server

---

### Post by darkod on 2016-02-21
That still doesn't answer whether you need a constant sync between the content on both servers. If the content on apache1 changes once a month, simply create apache2, set up the same sites, and upload the same content. No constant sync between them.

Then each time you make significant changes in the content on apache1, you simply upload the same modification to apache2.

On the other hand, if the content on apache1 changes every day and you want the same to reflect on apache2, you will need a cron job to do rsync of the folders...

---

### Post by isaac17 on 2016-02-21
ok ty

---

### Post by darkod on 2016-02-21
No problem. To add something more, you mentioned only apache but if you have mysql DBs used by the sites for example, you will need them in constant sync too, which makes it much more complex. So it all depends what you actually need...
An identical copy of the server with DBs is more complex than simply files sync.

---

### Post by volkswagner on 2016-02-22
I think you want a reverse proxy where Apache1 will have a vhost config which proxies to Apache2. I made a quick tutorial http://ubuntuforums.org/showthread.php?t=1920715

---

