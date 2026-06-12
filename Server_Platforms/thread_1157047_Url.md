---
title: "Url"
date: 2009-05-12
forum: Server Platforms
---

### Post by k33bz on 2009-05-12
I have my web server setup. I have my domain name registered and have it pointing to my server. The problem I am having though, is that after I type my page in,corpus-christi-fun.info, it goes there, and then re-directs it to my wordpress at corpus-christi-fun.info/wordpress. Everything up to that point works great. However if I click on one of the links in my wordpress, whether it is History, or Home, instead of it showing my domain name in the browser it switches to showing my server's IP address. What am I doing wrong, or what am I not doing?

---

### Post by cdenley on 2009-05-12
> **k33bz said:**
> I have my web server setup. I have my domain name registered and have it pointing to my server. The problem I am having though, is that after I type my page in,corpus-christi-fun.info, it goes there, and then re-directs it to my wordpress at corpus-christi-fun.info/wordpress. Everything up to that point works great. However if I click on one of the links in my wordpress, whether it is History, or Home, instead of it showing my domain name in the browser it switches to showing my server's IP address. What am I doing wrong, or what am I not doing?

You probably entered your IP address for a configuration option where you should have entered your domain name. I've never used worpress, so I can't tell you where that option may be, but perhaps this command will fix it.
```

sudo dpkg-reconfigure wordpress

```

Also, I would suggest more descriptive thread titles in the future, such as "wordpress links with IP".

---

### Post by k33bz on 2009-05-12
I have it fixed, thanks cdenley

---

