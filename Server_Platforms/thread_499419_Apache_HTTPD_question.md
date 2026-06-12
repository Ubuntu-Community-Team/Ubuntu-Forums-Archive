---
title: "Apache HTTPD question"
date: 2007-07-12
forum: Server Platforms
---

### Post by ratbastard on 2007-07-12
Why is there 6 instances of httpd running? 

Should this be the case ? 

When I run TOP I am seeing 6 of em..

---

### Post by Footballkid4 on 2007-07-12
I'm believe (correct me if I'm wrong) a new child process is created for each connected client, and then closed when the connection to the client is closed.

---

### Post by ratbastard on 2007-07-12
It is always that way -- I am pretty sure there is no one connecting --
Also IF i kill one I kill em all --

---

### Post by jtc on 2007-07-12
Yes, there are usually a minimum amount of "children" spawned.

You can find those settings in your apache2.conf

---

### Post by ratbastard on 2007-07-12
So I am guessing I can tone it down to one or 2 ? 

Via the CONF?

---

### Post by jtc on 2007-07-12
Yes you could, but I'm not sure you want to. When it comes the the spawning rules it is generally a good idea to leave the apache defaults, unless you really know what you are doing.

---

