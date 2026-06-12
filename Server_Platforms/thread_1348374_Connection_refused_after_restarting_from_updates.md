---
title: "Connection refused after restarting from updates"
date: 2009-12-07
forum: Server Platforms
---

### Post by cheadle on 2009-12-07
Hi,
 
I posted this elsewhere, however seems to be that this looks the best place to get support on this issue. We have been running 9.10 as a webserver for the last month without any problems, however after being asked to restart the computer after installing the standard updates the webserver part of the computer isnt working.
 
When you go to the domain it returns the following error;
 
*   (111) Connection refused*
 
Now im sure (hoping) this is something simple to solve - however as im a newbie in terms of Ubuntu it would be great to get any help on how this issue could be solved.

---

### Post by cdenley on 2009-12-07
Did you restart it locally, or remotely? Are you using SSL? Are you required to enter a passphrase to decrypt your SSL key before apache can start?
```

sudo netstat -tlnp
sudo ps -ef|grep apache

```

---

