---
title: "Proftpd upgrade to proftpd-1.3.2rc2"
date: 2008-10-10
forum: Server Platforms
---

### Post by Fish3rm4n on 2008-10-10
Hi there!
I want to upgrade my proftpd server so it can handle ssl/tls connections the way filezilla 3.0.2 (something) wants.
Following this guide [http://www.proftpd.org/docs/howto/Upgrade.html](http://www.proftpd.org/docs/howto/Upgrade.html) gets me into problems at the line:"./configure ..". I haven't done much cli ./configure->make->make install installations but I suspect that the '..' means that I should choose my previous installation adding modules with the "--with-modules=...". Now my problem is that I don't know what modules I should use. I tried including all modules displayed from "proftpd - l". But it complains that "duplicate build request for xxx".
I tried to remove modules one by one but then got into another problem during the make.
How should I proceed?
Thanks in advance.

---

### Post by burgundy on 2008-12-05
I too would like to know more about how to upgrade the current proftpd package for 8.10 with what is now proftpd 1.3.2rc3. The broken Filezilla compatibility is quite annoying.

Who maintains the current proftpd package?

It would be nice if all we had to do was compile some source code and overwrite a few files in specific places.

Any chance there is a new ubuntu proftpd package that is listed on an 'unstable' branch somewhere?

The problem is I don't know where to look...

---

### Post by etamax on 2008-12-31
If you use the
```
proftpd -V
```
command, you can see the configure options

Mine are:
>   Version: 1.3.1
  Platform: LINUX
  Built With:
    configure --prefix=/usr --with-includes=/usr/include/postgresql:/usr/include/mysql --mandir=/usr/share/man --sysconfdir=/etc/proftpd --localstatedir=/var/run --libexecdir=/usr/lib/proftpd --enable-sendfile --enable-facl --enable-dso --enable-autoshadow --enable-ctrls --with-modules=mod_readme --enable-ipv6 --build i486-linux-gnu --with-shared=mod_site_misc:mod_load:mod_ban:mod_quotatab:mod_sql:mod_sql_mysql:mod_sql_postgres:mod_dynmasq:mod_quotatab_sql:mod_ldap:mod_quotatab_ldap:mod_ratio:mod_tls:mod_rewrite:mod_radius:mod_wrap:mod_wrap2:mod_wrap2_file:mod_wrap2_sql:mod_quotatab_file:mod_quotatab_radius:mod_facl:mod_ctrls_admin:mod_ifsession


I suggest you backup your /etc/proftpd folder and remove any previuos installation of proftpd with
```
sudo apt-get remove --purge proftpd proftpd-basic
```
Then download the latest release from the [ProFTPd site](http://www.proftpd.org/) and install it.

I haven't done it before because I'm looking for security problems that I may encounter from installing a different package that it's not provided by Ubuntu...

---

### Post by DantePasquale on 2009-01-15
I'm having some similar problems, but my issue is I can't get the latest rc to build -- I think it has something to do with gcc  having 'Werror' set for warn_unused_results. I searched around and don't see how to fix this. I followed instructions on proftp website and also on [https://launchpad.net/ubuntu/intrepid/+source/proftpd-dfsg]("https://launchpad.net/ubuntu/intrepid/+source/proftpd-dfsg"). I installed all the dependencies listed on that page, downloaded the source from that page as well as proftp's website and I get the same problem:

./configure runs properly but

make pukes:
```
make[1]: Entering directory `/home/e0081963/Work/ProFTP/proftpd-dfsg-1.3.1/src'
gcc -DHAVE_CONFIG_H  -DLINUX  -I.. -I../include  -O2 -Wall -Wno-long-double -c main.c
gcc -DHAVE_CONFIG_H  -DLINUX  -I.. -I../include  -O2 -Wall -Wno-long-double -c timers.c
gcc -DHAVE_CONFIG_H  -DLINUX  -I.. -I../include  -O2 -Wall -Wno-long-double -c sets.c
gcc -DHAVE_CONFIG_H  -DLINUX  -I.. -I../include  -O2 -Wall -Wno-long-double -c pool.c
gcc -DHAVE_CONFIG_H  -DLINUX  -I.. -I../include  -O2 -Wall -Wno-long-double -c table.c
gcc -DHAVE_CONFIG_H  -DLINUX  -I.. -I../include  -O2 -Wall -Wno-long-double -c regexp.c
gcc -DHAVE_CONFIG_H  -DLINUX  -I.. -I../include  -O2 -Wall -Wno-long-double -c dirtree.c
gcc -DHAVE_CONFIG_H  -DLINUX  -I.. -I../include  -O2 -Wall -Wno-long-double -c support.c
gcc -DHAVE_CONFIG_H  -DLINUX  -I.. -I../include  -O2 -Wall -Wno-long-double -c netaddr.c
gcc -DHAVE_CONFIG_H  -DLINUX  -I.. -I../include  -O2 -Wall -Wno-long-double -c inet.c
gcc -DHAVE_CONFIG_H  -DLINUX  -I.. -I../include  -O2 -Wall -Wno-long-double -c child.c
gcc -DHAVE_CONFIG_H  -DLINUX  -I.. -I../include  -O2 -Wall -Wno-long-double -c parser.c
gcc -DHAVE_CONFIG_H  -DLINUX  -I.. -I../include  -O2 -Wall -Wno-long-double -c log.c
log.c: In function ‘log_wtmp’:
log.c:173: warning: ignoring return value of ‘ftruncate’, declared with attribute warn_unused_result
At top level:
cc1: error: unrecognized command line option "-Wno-long-double"
make[1]: *** [log.o] Error 1
make[1]: Leaving directory `/home/e0081963/Work/ProFTP/proftpd-dfsg-1.3.1/src'
make: *** [src] Error 2
```

I tested by commenting out the offending call in log.c, but get the exact same failure on another module. 

How do you turn off Werror in GCC? Do I need to rebuild that in order to get proftp to build????

Thanks a bunch,
Danté

---

### Post by DantePasquale on 2009-01-20
Per instructions from Proftp forums, proftpd-1.3.2.**rc3** was created to get around this problem. 

So if anyone else is trying to compile proftpd-1.3.2rc2 on Ubuntu 8.10, try using proftpd-1.3.2rc3 instead.

---

### Post by burgundy on 2009-02-05
I just wanted to bump this thread out there... [http://www.proftpd.org/](http://www.proftpd.org/) says that 1.3.2 final has been released.

When/Where do we go to see this as an official Ubuntu 8.10 package?

Will we have to wait for 9.04?  Who makes this decision?

---

