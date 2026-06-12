---
title: "how to download directly to folder in server"
date: 2009-01-10
forum: Server Platforms
---

### Post by Heeter on 2009-01-10
Hi all,

what command line do I use to download a file directly to a folder in my server.

I am thinking:
```

wget http://downloadsite.com/downloadfile.tar.gz > /srv/folder

```

Would that work?

Thanks

Heeter

---

### Post by HermanAB on 2009-01-10
Probably.

I simply do something like this:
cd /wherever; wget whatever

Cheers,

Herman

---

### Post by Heeter on 2009-01-10
great, never even thought of going that way.

thanks

Heeter

---

### Post by lswb on 2009-01-10
wget "http://source" -P /path/to/download/directory

---

### Post by Heeter on 2009-01-10
awesome, thanks

Heeter

---

