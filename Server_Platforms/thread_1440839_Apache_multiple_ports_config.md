---
title: "Apache multiple ports config"
date: 2010-03-28
forum: Server Platforms
---

### Post by Rulesy on 2010-03-28
I have several sites running on a local server. Currently, they're all running on port 80. I need one particular site (and ONLY that site) to also accept connections on port 81.

If I browse to the server IP x.x.x.x:80 directly, Apache's behaviour of showing the default site should work as usual. But, if I browse to IP x.x.x.x:81, it should show a different site (the one that should be accepting both :80 and :81). This part is very important.

I was hoping something like the following would work, but it didn't :( Currently x.x.x.x:81 still shows what I've called myport80defaultsite.com below. Any ideas?

```

Listen 80
Listen 81

<VirtualHost *:80>
ServerName myport80defaultsite.com
</VirtualHost>

<VirtualHost *>
ServerName myport81defaultsite.com
</VirtualHost>

<VirtualHost *:80>
ServerName someotherport80site.com
</VirtualHost>

...
more port 80 sites
...

```

---

### Post by Ryan Dwyer on 2010-03-28
You need to specify *:81 instead of just * in your VirtualHost container.

BTW, when I restart my Apache service with <VirtualHost *> it tells me the hosts overlap and the first (port 80) has preference. I'm not sure why you didn't get the same error.

---

