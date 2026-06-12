---
title: "Apache - ServerAlias exception"
date: 2010-01-20
forum: Server Platforms
---

### Post by StrangeWill on 2010-01-20
So lets say I have two sites:
domain.com ([www.domain.com](www.domain.com))
www2.domain.com

I want all aliases to point to domain.com ex:
```
ServerAlias *.domain.com
```
which means [www.domain.com](www.domain.com) -> domain.com, somesite.domain.com -> domain.com. Great.


Except, www2.domain.com -> domain.com.... www2.domain.com is another site, is there a way to use wildcard exceptions? Every other combination OTHER THAN www2.domain.com will go to domain.com?

I've started listing:
```

ServerAlias site1.domain.com
ServerAlias *.site1.domain.com
ServerAlias site2.domain.com
ServerAlias *.site2.domain.com
ServerAlias site3.domain.com
ServerAlias *.site3.domain.com
ServerAlias site4.domain.com
ServerAlias *.site4.domain.com

```

but this requires a restart every time a new site is added, and is going to become a mess very quickly.

Thanks. :)

---

### Post by a9k3d on 2010-01-21
You want to use <**VirtualHost _default_>** in your **/etc/apache2/sites-available/default**
and then use
[B]<VirtualHost *>
ServerName www2.domain.com[/B]
...
for the **www2** site
Make sure **/etc/apache2/ports.conf** has **NameVirtualHost *** in it.

ServerAlias is used for another name of the site it's configuring. Example:
[B]ServerName [www.fish.com](www.fish.com)
ServerAlias fish.com
[/B]

---

### Post by StrangeWill on 2010-01-24
> **a9k3d said:**
> You want to use <**VirtualHost _default_>** in your **/etc/apache2/sites-available/default**
and then use
[B]<VirtualHost *>
ServerName www2.domain.com[/B]
...
for the **www2** site
Make sure **/etc/apache2/ports.conf** has **NameVirtualHost *** in it.

ServerAlias is used for another name of the site it's configuring. Example:
[B]ServerName [www.fish.com](www.fish.com)
ServerAlias fish.com
[/B]

So I'm assuming I need www2.domain.com to come first as a virtual host, and then just use *.domain.com on the 2nd virtual host, correct?

I'm not 100% sure how this will work, plesk may throw up, but I'll investigate ASAP.

---

### Post by ICEB3AR on 2010-01-24
You could use:

#Default-Directory which is used, if the subdomain/domain is not found
DocumentRoot "/<path to your [www.domain.de](www.domain.de) directory>"
 
#define your subdomain www2.domain.com
<VirtualHost *:80>
...
</VirtualHost>

THis should work.

---

