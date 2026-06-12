---
title: "Apache &lt;Directory /&gt; vs &lt;Directory /var/www/mystie&gt;"
date: 2012-04-11
forum: Server Platforms
---

### Post by kkruecke on 2012-04-11
What is the difference between the

```
<Directory /> 
```

directive and the

```
<Directory /var/www/mysite>
```

**<Directory /var/www/mysite>** seems obvious. But is <Directory /> really even needed for a virtual host? I based my site's virtual host setup file off of the **default**, which has both directives.

---

