---
title: "apache2 random folder access"
date: 2010-12-17
forum: Security
---

### Post by Kruum on 2010-12-17
My apache server have gotten a few requests to access some very strange directories that don't exist in my system.

From the access.log
```

- - [15/Dec/2010:19:08:00 +0200] "j\xd4F:\xbc\x0f\x12\xe0Y\x1d\xef]\x1c\x83\xe7\xef[\x06\xc6\xd8\x8a\x0f\x07\x90\x92\x88|\xbf\x9d\xbb^" 200 1318 "-" "-"

- - [15/Dec/2010:22:18:45 +0200] "\xbaj" 200 1341 "-" "-"

```

And few others.  A few days earlier similar requests got rejected with the status code 400.  Since then, I haven't made any changes.  Anyone knows what that means?

---

### Post by TSJason on 2010-12-17
I commonly see this on managed hosting servers where a bot or virus is scanning for vulnerabilities on webservers. If you're sufficiently secured and up-to-date then there's not much to worry about. 

You may want to look into mod_security ([http://modsecurity.org/](http://modsecurity.org/)) if you are unsure of the secureness of sites you host on this machine as it is helpful in shoring up many vulnerabilities.

---

