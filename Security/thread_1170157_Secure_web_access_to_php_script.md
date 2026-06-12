---
title: "Secure web access to php script"
date: 2009-05-26
forum: Security
---

### Post by Eviltechie on 2009-05-26
I'm writing a program in php that will bring together a bunch of webui's from other programs. To keep everything standard and such, I was going to use apache to reverse proxy the programs to virtual hosts (like localhost:8112 to /deluge) and allow access through my php app. Unfortunately, my friend pointed out that this would only move the problem, not fix it. So how would I only allow access to those virtual hosts though my php app?

---

### Post by cdenley on 2009-05-26
Are you trying to restrict access to [http://localhost:8112/](http://localhost:8112/) or [http://localhost/deluge/](http://localhost/deluge/)?
[http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html#allow](http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html#allow)

---

### Post by Eviltechie on 2009-05-26
Both. I want the :8112 completely firewalled off, and /deluge only available through the php app.

---

### Post by cdenley on 2009-05-26
I'm not sure how deluge works, but you should be able to make it bind to 127.0.0.1 so it cannot be connected to remotely. You could also use UFW to firewall it.
```

netstat -tln

```
What do you mean "/deluge only available through the php app"? How does the "php app" connect/redirect to /deluge? You could have apache also bind to 127.0.0.1, or configure apache to only allow certain IP's as shown in the link I posted. As always, you can always firewall it as well.

---

### Post by Eviltechie on 2009-05-26
I was going to reverse proxy localhost:8112 to /deluge. But I don't want any old person to be able to goto mywebsite.com/deluge and mess with my torrents. I want to have a login through a php application that will allow access to /deluge.

---

