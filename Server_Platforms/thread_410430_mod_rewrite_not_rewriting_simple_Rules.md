---
title: "mod_rewrite not rewriting simple Rules"
date: 2007-04-15
forum: Server Platforms
---

### Post by Boffbowsh on 2007-04-15
I have enabled the rewrite module using sudo a2enmod.

I have, in my 000-default file, the following rule simply as a test:
```
RewriteRule ^/somepath(.*) otherpath$1
```
This is as a precursor to some obviously more complex rules.

If i go to [http://hostname/somepath/anotherpath](http://hostname/somepath/anotherpath), I get a 404, but the debug log of apache says that /var/www/somepath doesn't exist. It's not getting rewritten to otherpath. I copied this example from a website. It's very very basic and should in fact work. I have RewriteEngine On elsewhere in the config too.

Anyone got any ideas?

---

### Post by SishGupta on 2007-04-15
> **Boffbowsh said:**
> I have enabled the rewrite module using sudo a2enmod.

I have, in my 000-default file, the following rule simply as a test:
```
RewriteRule ^/somepath(.*) otherpath$1
```This is as a precursor to some obviously more complex rules.

If i go to [http://hostname/somepath/anotherpath](http://hostname/somepath/anotherpath), I get a 404, but the debug log of apache says that /var/www/somepath doesn't exist. It's not getting rewritten to otherpath. I copied this example from a website. It's very very basic and should in fact work. I have RewriteEngine On elsewhere in the config too.

Anyone got any ideas?
I have never used a2enmod so I am not sure what methods it uses to enable mods. I always just do it manually.

But I usually forget to restart the server after enabling a mod. Did you? I also don't use modrewrite so I am not sure of any other obvious errors.

---

### Post by MJN on 2007-04-16
Put a leading slash before otherpath$1 i.e.

```
RewriteRule ^/somepath(.*) /otherpath$1
```

Mathew

---

