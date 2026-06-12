---
title: "multiple apache threads"
date: 2009-07-27
forum: Server Platforms
---

### Post by abarth on 2009-07-27
Hi all,
I have an apache server on a 8-core machine with 16 GB of memory. 
I create dynamical content (images) in Python integrated in apache with mod_python. When I run the apache benchmark (ab) on a URL

ab -n 100 -c 20 'http://localhost/path/to/python/script?somevars'

top reports only 3 apache processes running at 100% CPU utilization. Why is apache not using all 8 cores to improve performance?

I think I use the MPM worker threading model:

```

dpkg -l | grep apache2
ii  apache2                               2.2.8-1ubuntu0.10                         Next generation, scalable, extendable web se
ii  apache2-mpm-worker                    2.2.8-1ubuntu0.10                         High speed threaded model for Apache HTTPD
ii  apache2-utils                         2.2.8-1ubuntu0.10                         utility programs for webservers
ii  apache2.2-common                      2.2.8-1ubuntu0.10                         Next generation, scalable, extendable web se
ii  libapache2-mod-python                 3.3.1-2build1                             Apache 2 module that embeds Python within th

```

I increased the StartServers variable to 8 in /etc/apache2.conf, but without the expected result.

```
<IfModule mpm_worker_module>
    StartServers          8
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

```

I'm using Ubuntu 8.04 64-bit with 2 quad-core Xeon E5420.

Any help would be greatly appreciated! 
Thanks
Alex

---

### Post by dragos2 on 2009-07-27
> **abarth said:**
> Hi all,

```

dpkg -l | grep apache2
ii  apache2                               2.2.8-1ubuntu0.10                         Next generation, scalable, extendable web se
ii  apache2-mpm-worker                    2.2.8-1ubuntu0.10                         High speed threaded model for Apache HTTPD
ii  apache2-utils                         2.2.8-1ubuntu0.10                         utility programs for webservers
ii  apache2.2-common                      2.2.8-1ubuntu0.10                         Next generation, scalable, extendable web se
ii  libapache2-mod-python                 3.3.1-2build1                             Apache 2 module that embeds Python within th

```
Alex

Hmm I see there both apache2 and apache-mpm-worker. Uninstall the apache2 and keep
only the apache-worker.

---

### Post by abarth on 2009-07-27
> **dragos2 said:**
> Hmm I see there both apache2 and apache-mpm-worker. Uninstall the apache2 and keep
only the apache-worker.

Are you sure? It seems to me that apache2 is just a dummy package that depends on the apache version compiled with different threading models.

```
$ aptitude show apache2
...
Depends: apache2-mpm-worker (>= 2.2.8-1ubuntu0.10) | apache2-mpm-prefork (>= 2.2.8-1ubuntu0.10) | apache2-mpm-event (>= 2.2.8-1ubuntu0.10)
Provided by: apache2-mpm-event, apache2-mpm-itk, apache2-mpm-prefork, apache2-mpm-worker
...

```

On my system the apache2 package only contains:

```
$ dpkg -L apache2
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/apache2
/usr/share/doc/apache2/copyright
/usr/share/doc/apache2/NEWS.Debian.gz
/usr/share/doc/apache2/changelog.Debian.gz
/usr/share/bug
/usr/share/bug/apache2
/usr/share/doc/apache2/README.Debian.gz
/usr/share/bug/apache2/script

```

---

