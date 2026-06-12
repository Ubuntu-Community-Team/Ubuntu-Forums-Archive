---
title: "apahce vhost"
date: 2011-10-24
forum: Server Platforms
---

### Post by lolium on 2011-10-24
hey gus, 

Probably an easy one for the most of you

Ive got a web application installed on my server which runs on port :4040, is it possible to point my subdomain to that port? or tell that subdomain to pull the files from the location of those files

What would be the best way to go about this?

Thanks

---

### Post by volkswagner on 2011-10-24
I think you'll want to setup a vhost with reverse proxy.

Like:

```
<VirtualHost *>
	ServerAdmin root@localhost
	ServerName sub.domain.com

 <location />
          allow from all
     </location>
     ProxyPass / http://127.0.0.1:4040/
     ProxyPassReverse / http://127.0.0.1:4040/

```

You can change the first few lines to match your needs.

---

### Post by lolium on 2011-10-24
Your a god, Thank you

---

