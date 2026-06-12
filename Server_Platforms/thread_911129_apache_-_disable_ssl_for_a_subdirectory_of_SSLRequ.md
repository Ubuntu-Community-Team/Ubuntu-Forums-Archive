---
title: "apache - disable ssl for a subdirectory of SSLRequireSSL"
date: 2008-09-05
forum: Server Platforms
---

### Post by tr333 on 2008-09-05
I am using SSLRequireSSL in a <Directory> directive to force SSL in a directory, and all of its subdirectories.  How can I disable the SSL requirement for one of the subdirectories?

---

### Post by father time on 2008-09-07
Message Deleted.

---

### Post by moonspa on 2009-02-12
Hello,

Thanks for your post "tr333", because I tried to find out how usage of SSL could be forced ;). Anyway I looked into the apache manual, here's snapshot of the page:

> 
SSLRequireSSL
Syntax: SSLRequireSSL
Context: server config, virtual host, .htaccess, directory
Override: FileInfo
Status: Extension
Module: Apache-SSL
Compatibility: ??

Require SSL. This can be used in sections (and elsewhere) to protect against inadvertantly disabling SSL. If SSL is not in use when this directive applies, access will be refused. This is a useful belt-and-braces measure for critical information. Conversely, deny SSL connections with **[COLOR="Red"][SIZE="6"]SSLDenySSL[/SIZE][/COLOR]**.

Example:

    <Directory /some/where/important>
      SSLRequireSSL
    </Directory>


I would say that "SSLDenySSL" is exactly what you looking for, isn't?



mOOnSPa.

---

### Post by jimsmithkka on 2009-02-17
i am having a similar issue/want.  SSLDenySSL does not work for apache2.  I don't have much to say to help though, sorry

---

