---
title: "Apache Issues"
date: 2008-03-28
forum: Server Platforms
---

### Post by damonjablons on 2008-03-28
Hey,

I'm running apache2, and it has been running fine, until I attempted to edit the port it listens for.  I'm changing the port because my ISP blocks port 80.

I attempted to change to the listening port by editing the ports.conf file as root.  When I try to restart the apache server, it gives me the error message: 
```
httpd (no pid file) not running
```

I appreciate the help, thank you.

---

### Post by Poleh on 2008-03-29
This just means when u restarted the server it wasn't found to be running. What command did you use to restart the server?

You should only need to issue /etc/init.d/apache2 restart 

after you configure the port change.

---

