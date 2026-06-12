---
title: "DNS Wildcard Bind9"
date: 2008-04-24
forum: Server Platforms
---

### Post by Dr Small on 2008-04-24
I am trying to setup a wildcard for my domain mycroft.org with bind9, but really don't know where to begin.

Any suggestions?

---

### Post by terazen on 2008-04-24
Hey I think this is what you are asking.  If you are referring to hosts wildcards you can enter something like this in your bind files.

*.testbox           IN      A       1.2.3.4

Then anything.testbox.mycroft.org would resolve to 1.2.3.4.

For PTR you only need testbox.

4                   IN      PTR     testbox.mycroft.org.

Also CNAMEs would be the same I think.

*.testbox           IN      CNAME   anotherbox

---

### Post by Dr Small on 2008-04-25
Thanks, that worked.
I used:
```
*.mycroft.org     IN      CNAME     mycroft.org.
```

Dr Small

---

