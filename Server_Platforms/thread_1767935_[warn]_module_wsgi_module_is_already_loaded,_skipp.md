---
title: "[warn] module wsgi_module is already loaded, skipping"
date: 2011-05-26
forum: Server Platforms
---

### Post by vandorjw on 2011-05-26
Hey everyone,
When I run this:

```
$ sudo apachectl -t
```

I get this as output.

```
[Thu May 26 10:33:20 2011] [warn] module wsgi_module is already loaded, skipping
```

I have gone through my configuration file a couple times now, but I cannot figure out why it is being loaded twice.

I have attached my config file to this post. Hopefully someone can point out my mistake.

Cheers - CC7

---

### Post by sanguinoso on 2011-05-26
Check in your conf.d directory as well. If something in there is loading wsgi_module again that's probably the reason for the error.

---

### Post by vandorjw on 2011-05-26
Thanks for the reminder.
I'll make a check and report back.

cheers - cc7

---

