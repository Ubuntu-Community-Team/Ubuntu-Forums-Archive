---
title: "Remove shell from users"
date: 2008-09-06
forum: Server Platforms
---

### Post by Silent Ninja on 2008-09-06
I was checking on the /etc/passwd to remove the shell from one user, but.. I've realized that almost all pre-created users (like gnats, games, man, news).. have the /bin/sh shell access setup, but isn't it insecure if some hacker finds out the password from those users and logs to my server ?

Do they have shell access for some script/s to work out, or it's Ok if I turn all of them to /bin/false ?

---

### Post by windependence on 2008-09-06
Be careful with this. If you turn off shell access for system processes or applications that need it, you will have a mess.

I think you are being a bit paranoid here. If you are that paranoid try this:

[http://www.openbsd.org/](http://www.openbsd.org/)

The most secure OS on the planet.

-Tim

---

