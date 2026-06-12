---
title: "Forward *@mydomain.com -&gt; another@domain.com with Postfix"
date: 2010-11-15
forum: Server Platforms
---

### Post by molgan on 2010-11-15
Is there a way to implement a catch-all address without having to deal with virtual aliases in postfix? (ubuntu 10)

In other words: I would like *@mydomain.com to be forwarded to [EMAIL="another@domian.com"]another@domian.com[/EMAIL] the easiest way possible.

---

### Post by James78 on 2010-11-15
An alias like so, will provide a catch all for example.com and forward it to local user jim. You were pretty close.
```
 /etc/postfix/virtual:
     postmaster@example.com postmaster
     info@example.com       joe
     sales@example.com      jane
     # Uncomment entry below to implement a catch-all address
     # @example.com         jim
     ...virtual aliases for more domains...

```

Unfortunately I haven't been able to find a way to do this without using Virtual Aliases, maybe someone else will know hopefully...

Why do you need to do this without Virtual Aliases? It's so easy to do it with them.

---

### Post by molgan on 2010-11-22
Since no one purposed a way of doing this without virtual aliases, I guess that's the way to go.


I'm going to set up postfix with two virtual alias domains.
So I will execute:
```

sudo postconf -e "virtual_alias_domains = mydomain1.com mydomain2.com"
sudo postconf -e "virtual_alias_maps = hash:/etc/postfix/virtual"
echo '@mydomain1.com another@domain.com' >> /etc/postfix/virtual
echo '@mydomain2.com another@domain.com' >> /etc/postfix/virtual
sudo postmap /etc/postfix/virtual
sudo postfix reload
```Can I remove the value mydomain.com that I find in:

/etc/postfix/main.cf => myhostname
/etc/postfix/main.cf => mydestination
/etc/mailname

Or what should they be set to?


> NEVER list a [virtual alias domain]("http://www.postfix.org/ADDRESS_CLASS_README.html#virtual_alias_class") name as a [mydestination]("http://www.postfix.org/postconf.5.html#mydestination") domain!        (from [http://www.postfix.org/VIRTUAL_README.html](http://www.postfix.org/VIRTUAL_README.html))

---

### Post by James78 on 2010-11-22
Ya, it's safe to keep mydomain.com out of those 2 variables. I use Virtual Alias domains, and my 2 variables are set to:
```
myorigin: $myhostname
mydestination: $myhostname, localhost.$mydomain 
```
And my system receives mail and whatnot for all my domains perfectly fine. In fact, if you DO put mydomain.com in any of those, you'll receive a warning/error in your logs like "warning: do not list domain example.com in BOTH mydestination and virtual_alias_domains"

So ya, setting it to what I have works, using Virtual Aliases works perfect, and no errors like the example I gave.

Note: localhost.$mydomain means localhost.example.com, which means you need a DNS entry that says "localhost.example.com" which points to 127.0.0.1, just FYI, you can probably/may have to omit that entry. Or you may completely need that entry, testing that out should show you if you need it.

Edit: As for the myhostname, you can just leave it where it's at.

---

