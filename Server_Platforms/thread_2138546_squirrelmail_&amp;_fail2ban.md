---
title: "squirrelmail &amp; fail2ban"
date: 2013-04-24
forum: Server Platforms
---

### Post by SlugSlug on 2013-04-24
Can someone help with expressions?

I get this in syslog

```
Apr 24 15:40:48 servername squirrelmail: Failed webmail login: by N/A (domain.com) at 86.0.0.0 on 04/24/2013 14:40:48: Unknown user or password incorrect.
```


It looks like the docs are outdated as it says filter should look like

```
failregex = \[webmail\].*at <HOST>: Unknown user or password incorrect
```

But that does nothing

---

### Post by SlugSlug on 2013-04-25
for anyone else that needs it it's


```
failregex = squirrelmail: Failed webmail login: by .* \(.*\) at <HOST> on .* Unknown user or password incorrect.$
```

---

