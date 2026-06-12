---
title: "[SOLVED] Apache2 Undefined Symbol"
date: 2008-07-01
forum: Server Platforms
---

### Post by paulpc on 2008-07-01
I installed the library package 'libapreq2' using 'aptitude', and tried dereferencing the 'Apache2::Request' module in a mod_perl script,  but it crashed with '/usr/sbin/apache2: symbol lookup error: /usr/lib/perl5/auto/APR/Request/Apache2\
/Apache2.so: undefined symbol: apreq_handle_apache2'. I ran 'nm' on libapreq2.so.3and it returned "nm: /usr/lib/libapreq2.so.3: no symbols".

Can anyone help with this?

Thanks,

---

### Post by paulpc on 2008-07-07
I just found the problem.

The 'aptitude' package manager installed the libapreq2 package but unfortunately, it didn't create the symbolic link that's required in the apache2/mods-enabled directory pointing to apache2/mods-available/apreq.load. So, when the server started, it didn't load the mod_apreq2.so module. That meant that none of the symbols in mod_apreq2.so were loaded at startup which caused any reference to Apache2::Request to fail.

This is a trap for newbies.

Regards,

---

### Post by sneils on 2012-05-29
Sorry for the topic necromancy, but just ran into the same error and wanted to share a quick fix:

```
% sudo a2enmod apreq
```

---

