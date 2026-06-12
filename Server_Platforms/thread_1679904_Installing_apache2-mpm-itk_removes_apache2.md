---
title: "Installing apache2-mpm-itk removes apache2?"
date: 2011-02-01
forum: Server Platforms
---

### Post by Bouke on 2011-02-01
As to increase security on my shared server, I would like to install apache2-mpm-itk. I'm on Ubuntu 8.04 with the following apache-related package versions:

```
ii  apache2                                2.2.8-1ubuntu0.19                    Next generation, scalable, extendable web se
ii  apache2-mpm-prefork                    2.2.9-10+lenny9                      Apache HTTP Server - traditional non-threade
ii  apache2-threaded-dev                   2.2.9-10+lenny9                      Apache development headers - threaded MPM
ii  apache2-utils                          2.2.8-1ubuntu0.19                    utility programs for webservers
ii  apache2.2-common                       2.2.9-10+lenny9                      Apache HTTP Server common files
ii  libapache2-mod-php5                    5.2.4-2ubuntu5.14                    server-side, HTML-embedded scripting languag
ii  webmin-apache                          1.490-turnkey+1+ga06198f             Webmin module - Apache Webserver
```

So, I command apt-get to install the requested package:
```
apt-get -s install apache2-mpm-itk
(...)
The following packages have unmet dependencies:
  apache2-mpm-itk: Depends: apache2.2-common (= 2.2.8-1ubuntu0.19) but 2.2.9-10+lenny9 is to be installed
```

Ok, so let me downgrade apache2.2-common to 2.2.8:
```
apt-get -s install apache2-mpm-itk apache2.2-common=2.2.8-1ubuntu0.19
(...)
The following packages were automatically installed and are no longer required:
  comerr-dev libpcre3-dev libdb4.6-dev libsqlite3-dev libkrb5-dev libapr1-dev libldap2-dev libpcrecpp0 uuid-dev libpq-dev libkadm55 libexpat1-dev libaprutil1-dev
Use 'apt-get autoremove' to remove them.
Suggested packages:
  apache2-doc www-browser
The following packages will be REMOVED:
  apache2 apache2-mpm-prefork apache2-threaded-dev
The following NEW packages will be installed:
  apache2-mpm-itk
The following packages will be DOWNGRADED:
  apache2.2-common
0 upgraded, 1 newly installed, 1 downgraded, 3 to remove and 5 not upgraded.
Remv apache2 [2.2.8-1ubuntu0.19]
Remv apache2-mpm-prefork [2.2.9-10+lenny9] [libapache2-mod-php5 ]
Remv apache2-threaded-dev [2.2.9-10+lenny9] [libapache2-mod-php5 ]
Inst apache2.2-common [2.2.9-10+lenny9] (2.2.8-1ubuntu0.19 Ubuntu:8.04/hardy-security) [libapache2-mod-php5 ]
Inst apache2-mpm-itk (2.2.6-01-1build3.11 Ubuntu:8.04/hardy-security)
Conf apache2.2-common (2.2.8-1ubuntu0.19 Ubuntu:8.04/hardy-security)
Conf apache2-mpm-itk (2.2.6-01-1build3.11 Ubuntu:8.04/hardy-security)
```

So, I also include apache2 as 'to be installed':
```
apt-get -s install apache2-mpm-itk apache2.2-common=2.2.8-1ubuntu0.19 apache2
(...)
apache2 is already the newest version.
(...)
The following packages have unmet dependencies:
  apache2: Depends: apache2-mpm-worker (>= 2.2.8-1ubuntu0.19) but it is not going to be installed or
                    apache2-mpm-prefork (>= 2.2.8-1ubuntu0.19) but it is not going to be installed or
                    apache2-mpm-event (>= 2.2.8-1ubuntu0.19) but it is not going to be installed
E: Broken packages
```

Okey, so let me install mpm-prefork:
```
apt-get -s install apache2-mpm-itk apache2.2-common=2.2.8-1ubuntu0.19 apache2 apache2-mpm-prefork=2.2.8-1ubuntu0.19
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  apache2-mpm-itk: Conflicts: apache2-mpm
  apache2-mpm-prefork: Conflicts: apache2-mpm
E: Broken packages
```

This is the point where I don't know where to go next.

---

