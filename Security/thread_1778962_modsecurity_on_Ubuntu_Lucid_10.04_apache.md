---
title: "modsecurity on Ubuntu Lucid 10.04 apache"
date: 2011-06-09
forum: Security
---

### Post by oregonbob on 2011-06-09
I am trying to get modsecurity running with some basic rules on 10.04. I have tried a couple of how-to's but they all cover different versions of Ubuntu and apparently don't work on 10.04.

I used Synaptic to install modsecurity-common and libmod_security.

If I make a folder /etc/apache2/conf.d/modsecurity and place example rules in it, I get this error when starting apache:

> apache2: Syntax error on line 234 of /etc/apache2/apache2.conf: Syntax error on line 132 of /etc/apache2/conf.d/modsecurity/base_rules/modsecurity_40_generic_attacks.data: /etc/apache2/conf.d/modsecurity/base_rules/modsecurity_40_generic_attacks.data:170: <input> was not closed.\n/etc/apache2/conf.d/modsecurity/base_rules/modsecurity_40_generic_attacks.data:132: <![cdata[> was not closed.
     
For every how-to I find they have a different directory structure and directives, nothing is standardized making it difficult to install.

Anyone running modsecurity on 10.04 care to share?

---

### Post by desire.linux on 2011-06-09
When you set the rules folder in your apache2 config, remeber to add *.conf.

Like this:
```

/etc/apache2/conf.d/modsecurity/*.conf

```Try that.

---

