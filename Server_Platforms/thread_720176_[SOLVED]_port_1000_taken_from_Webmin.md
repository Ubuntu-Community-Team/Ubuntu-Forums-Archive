---
title: "[SOLVED] port 1000 taken from Webmin"
date: 2008-03-10
forum: Server Platforms
---

### Post by dynamethod on 2008-03-10
Hey there ive tried to reinstall WebMin on my LAMP gutsy box, (I locked myself out first time), but im getting this error: [http://paste.ubuntu-nl.org/59109/](http://paste.ubuntu-nl.org/59109/) how do i correct this?

---

### Post by SpaceTeddy on 2008-03-10
mhm - this looks like your old webmin is still running. you can figure that out with 

```
sudo netstat -lnp
```

and then see if there is anything listening on the port 10000 - if so, kill it. also, make sure that you do a purge of the webmin package , otherwise your configuration files will be kept, and your reset does not work :)

---

### Post by dynamethod on 2008-03-10
yup it was exactly that, thanks dude :)

---

