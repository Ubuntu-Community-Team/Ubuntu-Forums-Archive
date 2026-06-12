---
title: "Rndc key error"
date: 2006-09-20
forum: Server Platforms
---

### Post by Gustav Nilsson on 2006-09-20
Hi!

I have newly changed distro on a server from Crux to Ubuntu. Everthing worked well except the DNS server. I tried to configure bind like the old configuration files, but when I restarted the server I got an error like:
```

rndc: connection to remote host closed
This may indicate that the remote server is using an older version of
the command protocol, this host is not authorized to connect,
or the key is invalid.

```

I'm pretty sure that the key and so is correct. I heard of a /scripts/fixndc script. But I can't find it, anyone who knows where it's placed or has other suggestions for sloving this problem?

---

### Post by Divan Santana on 2008-06-27
reboot worked for me! :)

---

