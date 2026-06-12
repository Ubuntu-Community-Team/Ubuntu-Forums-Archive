---
title: "Recommended way to compile php extension like pdo_oci.so"
date: 2016-05-11
forum: Server Platforms
---

### Post by Dieter_Springer on 2016-05-11
Hi

I need to install pdo_oci extension in php7 on a new Ubuntu 16.04 server.
I search the net and found a couple of tutorials . Most weren´t related to ubuntu, but i succsessfully compiled a working pdo_oci.so from the vanilla php-7.0.4 sources.

But now a colleague needs this module on a couple of servers too. So now i am asking me, what is the recommended way to compile and package this php module as a .deb in 16.04? 
Older tutorials i found so far wont work, as there is no dh-make-php or something ( see: [https://www.dotdeb.org/2008/09/25/how-to-package-php-extensions-by-yourself/](https://www.dotdeb.org/2008/09/25/how-to-package-php-extensions-by-yourself/)). I know i could write a whole new package description with rules, control, compat and others. But i am not sure if this will create problems with future updates.
I want to do it "the right way".

Any Ideas?

---

