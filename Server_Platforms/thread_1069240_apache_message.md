---
title: "apache message"
date: 2009-02-13
forum: Server Platforms
---

### Post by mistypotato on 2009-02-13
Anyone have any idea what this is and how to resolve it ?

 * Restarting web server apache2                                                (13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]

---

### Post by conjur3r on 2009-02-13
Apache or some other service is already running and listening on port 80.  Check out what that is with:

# sudo netstat -anp | grep 80

---

### Post by spiderbatdad on 2009-02-14
Looks like a simple permissions problem. It doesnt say socket already in use, it says permission denied. No listening sockets "avaialable" because you dont have permission. Put sudo in front of your restart command:
sudo /etc/init.d/apache2 start

---

### Post by mistypotato on 2009-02-15
thx.

Restarting the server seemed to help also :lolflag:

---

