---
title: "Webmin wont work"
date: 2009-04-10
forum: Server Platforms
---

### Post by shootdamonkey on 2009-04-10
Installed ubuntu server in vmware, install went fine no problems. Then installed webmin using a tutorial and seemed to have no problems.

Now in the host computer (vista), UBUNTUSERVER appeared in the network browser, all good so far. But i cannot access webmin.

I tried [http://ubuntuserver:10000/](http://ubuntuserver:10000/) and [http://192.168.1.2:10000/](http://192.168.1.2:10000/) which webmin recommended when i installed it. But firefox just takes a while then says network timeout.

Help!

---

### Post by volkswagner on 2009-04-10
Generally Webmin listens on https not http.

Try [https://192.168.1.2:10000/](https://192.168.1.2:10000/)

---

### Post by juancarlospaco on 2009-04-10
Http**s**

---

