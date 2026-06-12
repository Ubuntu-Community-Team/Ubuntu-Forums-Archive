---
title: "LAMP stack and Domain"
date: 2017-04-10
forum: Server Platforms
---

### Post by jmoya4 on 2017-04-10
Hi,

I just installed my first LAMP stack. Now, I'm trying to connect my domain to my computers public IP. It's propagated...[https://www.whatsmydns.net/#A/ifyouonlyknew.site...and](https://www.whatsmydns.net/#A/ifyouonlyknew.site...and) it's connected to third party nameservers 'ns1.dreamhost.com' etc.... I'm not sure what to do from here. Any documentation you have, that you can share, would be greatly appreciated...Thanks!

---

### Post by deadflowr on 2017-04-10
Moved to *Server Platforms*

---

### Post by SeijiSensei on 2017-04-10
If you want the server to reply to requests for "www.example.com", then you need to add an "A" (address) record to your nameserver that points the www hostname to the server's public IP address:
```
www     IN     A     10.10.10.10
```
replacing 10.10.10.10 with your server's IP.  Usually there's a way to do this with the web-based tools at your domain registrar.

You should also set the machine's own hostname to "www" to match:
```
sudo hostname www
```

If you prefer that the server have a different name, say "myserver.example.com", you can use a "CNAME" record to make "www" an alias for "myserver":
```
myserver     IN     A         10.10.10.10
www          IN     CNAME     myserver
```

---

