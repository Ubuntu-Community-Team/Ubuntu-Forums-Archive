---
title: "make the folder public"
date: 2010-04-23
forum: Server Platforms
---

### Post by Vi-Maker on 2010-04-23
Hi, i installed ubuntu on my computer and im testing it.. so i have a problem =/

So im wondering how can i make the folder /var/www/ public for all users? so thay can write/read?

Thanks! :D:guitar:

---

### Post by cdenley on 2010-04-23
You usually shouldn't do this, since this means any process on your system can modify the contents of /var/www. If an attacker ever gained local access, they could delete or maliciously alter your web content.
```

sudo chmod -R a+rwX /var/www

```

---

### Post by arrrghhh on 2010-04-23
I'm going to echo what cdenley said... You shouldn't open up any folder, especially the root of your webserver, to everyone... I mean if you create a special folder for them to interact with that's one thing, but your entire webserver is now open...

---

