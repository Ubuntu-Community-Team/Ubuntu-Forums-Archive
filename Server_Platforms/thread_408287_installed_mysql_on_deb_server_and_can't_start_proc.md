---
title: "installed mysql on deb server and can't start process"
date: 2007-04-13
forum: Server Platforms
---

### Post by royaltrj on 2007-04-13
Hello All,

I have a web server I'm setting up on vpslink.com (actually a lamp server).  I'm running PuTTY on a windows based machine, but the server is debian.  I'm trying to finish the initial set up, but mysql is giving me the following error below.  

[IMG]http://i64.photobucket.com/albums/h178/royaltrj/sqlerror.jpg[/IMG]

I need help getting mysql to run through the correct port or just simply run in the background.  I have already checked all my processes under 'top' to verify that it isn't running.

Thanks

---

### Post by eklapothik on 2007-04-27
try the following command:

```
/etc/bin/mysql restart
```

---

