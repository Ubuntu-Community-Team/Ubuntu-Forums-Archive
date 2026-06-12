---
title: "Help configuring squid ACL rules"
date: 2010-03-14
forum: Security
---

### Post by karthick87 on 2010-03-14
Only i want to allow few sites,and i want to restrict all other sites..For example i want to allow gmail,rediff and yahoo and i want to restrtict all other sites... So how to write ACL for this?

---

### Post by cariboo on 2010-03-14
A bump for the move.

---

### Post by karthick87 on 2010-03-15
Is this correct..?

```
acl workingURL url_regex "/etc/squid/opensites"
http_access allow workingURL
http_access deny all
```


**opensites** file contains the following

```

yahoo
gmail
rediff
```

---

### Post by koenn on 2010-03-15
I'm not familiar wuth the workingURL and url_regex directives, but if they exist, that looks like a squid config that would work.

an other way of doing it is going by domain name - something like this :

squid conf:
```

acl whitelist dstdomain "/etc/squid/whitelist"
http_access allow whitelist
http_access deny all

```

/etc/squid/whitelist
```

yahoo.com
google.com

```
this goes by domain name, so all urls in the given domains will be allowed. IIRC, ou can include subdomains by prepending a  .  to the domain names, eg
```

.google.com

```
This is probably documented in the squid.conf comments.

---

### Post by karthick87 on 2010-06-24
Thank you :)

---

### Post by anomie on 2010-06-24
> **getyourkarthick said:**
> Is this correct..?

```
acl workingURL url_regex "/etc/squid/opensites"
http_access allow workingURL
http_access deny all
```


**opensites** file contains the following

```

yahoo
gmail
rediff
```

Using url_regex is probably not what you want in this case. While not super likely, it's possible you could match "rediff" in *any* part (the domain or the path) of an otherwise undesirable URL. For example: http.//badguys.com/rediff/ would match. 

I recommend instead: 
```
acl workingURL **dstdomain** "/etc/squid/opensites"
http_access allow workingURL
http_access deny all
```

And the opensites file could contain: 
```
.yahoo.com
.gmail.com
.rediff.com
```

... or whatever. You'll need to do a fair amount of testing to confirm you're getting the behavior you expect. 

-------

BTW, there is good documentation on the 'net that you should read through: 
[list]
[*] [http://wiki.squid-cache.org/SquidFaq/SquidAcl](http://wiki.squid-cache.org/SquidFaq/SquidAcl)
[*] [http://www.visolve.com/squid/squid24s1/access_controls.php](http://www.visolve.com/squid/squid24s1/access_controls.php)
[/list]

---

### Post by karthick87 on 2010-06-25
Thanks to koenn and anomie,that did the trick...

---

