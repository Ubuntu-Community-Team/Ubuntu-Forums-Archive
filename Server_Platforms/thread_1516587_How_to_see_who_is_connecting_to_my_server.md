---
title: "How to see who is connecting to my server"
date: 2010-06-23
forum: Server Platforms
---

### Post by natman on 2010-06-23
Hi,
I would just like to know how many page hits i am getting and to see where the IP is. How to i go about seeing this on the server ( i dont want to add a page counter or anything all i want is to see a list of IP's times when they made the connection and what they viewed )
Is there a command to see this?

---

### Post by volkswagner on 2010-06-24
You can examine your access.log.

Use less to view the log, and search for page names.

Sorry I don't have a more elegant solution.  I am sure a more experienced user can suggest a better way.

```
less /var/log/apache2/access.log
```

---

