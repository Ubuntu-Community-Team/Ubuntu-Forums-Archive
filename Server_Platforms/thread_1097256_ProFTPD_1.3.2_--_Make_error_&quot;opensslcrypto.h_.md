---
title: "ProFTPD 1.3.2 -- Make error: &quot;openssl/crypto.h: No such file or directory&quot;"
date: 2009-03-15
forum: Server Platforms
---

### Post by heffalump on 2009-03-15
***Update:** Turned out to be a stupid mistake.  The contents of "openssl-0.9.8j/include/openssl" were symbolic links, not actual files.  The links were relative.  Moving them out of that directory and into the ProFTPD directory invalidated the links.  I kept them were they were and added changed the includes parameter to "--with-includes=/usr/include/postgresql:/usr/include/mysql:/home/user/openssl-0.9.8j/include"  It worked like a charm!*

I'm trying to compile/install the newest ProFTPD version.

I've downloaded and configured the build.  I've used the following configuration options:

> --prefix=/usr --with-includes=/usr/include/postgresql:/usr/include/mysql:/usr/include/openssl --mandir=/usr/share/man --sysconfdir=/etc/proftpd --localstatedir=/var/run --libexecdir=/usr/lib/proftpd --enable-sendfile --enable-facl --enable-dso --enable-autoshadow --enable-ctrls --with-modules=mod_readme --enable-ipv6 --build i486-linux-gnu --with-shared=mod_site_misc:mod_load:mod_ban:mod_quotatab:mod_sql:mod_sql_mysql:mod_sql_postgres:mod_dynmasq:mod_quotatab_sql:mod_ldap:mod_quotatab_ldap:mod_ratio:mod_tls:mod_rewrite:mod_radius:mod_wrap:mod_wrap2:mod_wrap2_file:mod_wrap2_sql:mod_quotatab_file:mod_quotatab_radius:mod_facl:mod_ctrls_admin:mod_ifsession

Upon running the make command, I receive this error:

> support.c:50:29: error: openssl/crypto.h: No such file or directory

I figured it was just that I didn't have the OpenSSL include files in the directory that I was compiling ProFTPD from.  I moved the "openssl-0.9.8j/include/openssl" dir to my ProFTPD build directory.  The same error persists.

Anyone know where I should put the includes?  Am I even on the right track?

---

