---
title: "Where do I set &quot;DocumentRoot&quot; in apache2 on 11.10?"
date: 2012-02-05
forum: Server Platforms
---

### Post by nikonian on 2012-02-05
Hi guys. 
I am struggling to set my "DocumentRoot" on my apache2 server, running atop 11.10 x64. Would someone show me the syntax, and what file I need to edit, as Google just throws up more results than my brain can handle, and they ALL conflict.

Thanks.


{{EDIT}}

It's okay; I worked it out. You do:

```

sudo gedit /etc/apache2/sites-available/default

```And change it there. Boy, they keep shuffling things around! lol ^_^

---

### Post by richardjh on 2012-02-06
You get a lot of different answers because apache2 can be configured in so many ways. The default file on Debian based systems has been /etc/apache2/site-available/default for a long time though.

---

