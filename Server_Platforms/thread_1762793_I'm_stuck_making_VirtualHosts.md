---
title: "I'm stuck making VirtualHosts"
date: 2011-05-19
forum: Server Platforms
---

### Post by tapi0n on 2011-05-19
Trying so set up a **www1.sub.domain.tld **next to a **sub.domain.tld** _****_
My http.conf looks like this:

```
<VirtualHost *:80>
ServerName www.sub.domain.tld
ServerAlias www.sub.domain.tld
DocumentRoot /var/www/www
</VirtualHost>

<VirtualHost *:80>
ServerName www.sub.domain.tld
ServerAlias www1.sub.domain.tld
DocumentRoot /var/www/www1
</VirtualHost>
```My bind is configured like this:

```
ns        IN    A    xxx.xxx.xxx.xxx
www        IN    CNAME    ns
www1        IN    CNAME     ns
test        IN     A    xxx.xxx.xxx.xxx

```the ip of **test** is not the same as the one in **ns**. When browsing *test.sub.domain.tld*. that does get resolved to the right place.

also, when just going to *sub.domain .tld *I do get to the right place.

I'm not getting much love from the apache docs nor from the logs.

Anyone who can spot what I'm doing wrong? 

Cheers,

---

### Post by volkswagner on 2011-05-19
I do not see where you specify the problem or symptom.

What happens when you enter www1.sub.domain.tld in a browser?

---

### Post by tapi0n on 2011-05-20
I get a server not found message.

Also, when going to sub.domain.tld I get the index.html I'm supposed to get on www1.sub.domain.tld.

my var/www looks like this:

var/www/www/index.html
var/www/www1/index.html

---

### Post by volkswagner on 2011-05-20
> **tapi0n said:**
> I get a server not found message.

Also, when going to sub.domain.tld I get the index.html I'm supposed to get on www1.sub.domain.tld.


Which domain gets the server not found message?

---

### Post by tapi0n on 2011-05-20
the www1 domain

---

