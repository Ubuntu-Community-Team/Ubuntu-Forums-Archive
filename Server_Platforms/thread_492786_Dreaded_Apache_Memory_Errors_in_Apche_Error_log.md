---
title: "Dreaded Apache Memory Errors in Apche Error log"
date: 2007-07-05
forum: Server Platforms
---

### Post by yellowtip on 2007-07-05
Hi everyone, 

Just in case you didn't read my previous post, we're having some load issues with a major software implementation (mysql5/php5/Apache2).

In the apache error log, we see the following errors:
Allowed memory size of 67108864 bytes exhausted (tried to allocate 128 bytes)

We don't see them too much, but still...I don't like seeing these kind of things.

I'm assuming this is not normal for Apaches operations?

I can increase the allowed memory per script from 64MB to 128MB, but would that help, or would that simply make the problem worse?

Should I be worried about these problems? Are they related to the php code, or are they relasted to something else?

Anybody? :confused:

---

### Post by yellowtip on 2007-07-05
Anybody at all?

---

### Post by nocturn on 2007-07-05
I'm not sure, but I think it's a PHP limit.  You need to set it in the PHP configuration file.

---

### Post by bmathis on 2007-07-06
i just had the same problem. In /etc/php5/apache2/php.ini make sure the value for max_memory is 64M and not 64MB (or whatever memory size youi need). That fixed the problem for me.

---

