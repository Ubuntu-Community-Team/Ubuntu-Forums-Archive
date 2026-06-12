---
title: "Odd package upgrade issue."
date: 2005-04-25
forum: Repositories &amp; Backports
---

### Post by chapterthree on 2005-04-25
Hey All,

Please note I am not running ubuntu on my remote server, just regular debian, but hopefully somebody can help.  I use Ubuntu on my desktop systems though :)

I've had an odd package upgrade issue for a while now (couple of months maybe).  I am using Apache 2.x, and do not have Apache 1.x installed.

```
root@girls [~]# apt-get upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
The following packages have been kept back:
   libapache2-mod-php4 (4.3.10-2 => 4.3.10-12)
   php4 (4.3.10-2 => 4.3.10-12)
   php4-common (4.3.10-2 => 4.3.10-12)
   php4-mysql (4.3.10-2 => 4.3.10-12)
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```
```
root@girls [~]# apt-get dist-upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
Calculating Upgrade... Done
The following NEW packages will be installed:
   apache-common (1.3.33-4)
   libapache-mod-php4 (4.3.10-12)
   libkrb53 (1.3.6-2)
   libzzip-0-12 (0.12.83-4)
The following packages will be upgraded:
   libapache2-mod-php4 (4.3.10-2 => 4.3.10-12)
   php4 (4.3.10-2 => 4.3.10-12)
   php4-common (4.3.10-2 => 4.3.10-12)
   php4-mysql (4.3.10-2 => 4.3.10-12)
4 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 4637kB of archives.
After unpacking 7082kB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```

For reference, I have included what apache and php packages I have installed:
```
root@girls [~]# dpkg -l \*apache\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                       Version                    Description
+++-==========================-==========================-====================================================================
un  apache                     <none>                     (no description available)
un  apache-common              <none>                     (no description available)
un  apache-perl                <none>                     (no description available)
un  apache-ssl                 <none>                     (no description available)
un  apache-utils               <none>                     (no description available)
ii  apache2                    2.0.53-5                   next generation, scalable, extendable web server
ii  apache2-common             2.0.53-5                   next generation, scalable, extendable web server
un  apache2-doc                <none>                     (no description available)
un  apache2-modules            <none>                     (no description available)
un  apache2-mpm-perchild       <none>                     (no description available)
ii  apache2-mpm-prefork        2.0.53-5                   traditional model for Apache2
un  apache2-mpm-threadpool     <none>                     (no description available)
pn  apache2-mpm-worker         <none>                     (no description available)
ii  apache2-utils              2.0.53-5                   utility programs for webservers
un  libapache-mod-php4         <none>                     (no description available)
ii  libapache2-mod-php4        4.3.10-2                   server-side, HTML-embedded scripting language (apache 2.0 module)

root@girls [~]# dpkg -l \*php\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  caudium-php4   <none>         (no description available)
un  libapache-mod- <none>         (no description available)
ii  libapache2-mod 4.3.10-2       server-side, HTML-embedded scripting languag
ii  php4           4.3.10-2       server-side, HTML-embedded scripting languag
un  php4-cgi       <none>         (no description available)
un  php4-cgi-mysql <none>         (no description available)
ii  php4-common    4.3.10-2       Common files for packages built from the php
un  php4-gd        <none>         (no description available)
ii  php4-mysql     4.3.10-2       MySQL module for php4
un  php4-pear      <none>         (no description available)
un  php5           <none>         (no description available)
un  php5-cgi       <none>         (no description available)
un  php5-fcgi      <none>         (no description available)
un  php5-gd        <none>         (no description available)
un  php5-mysql     <none>         (no description available)
un  php5-mysqli    <none>         (no description available)
un  phpapi-2002091 <none>         (no description available)
un  phpdoc         <none>         (no description available)
ii  phpmyadmin     2.6.2-rc1-1    set of PHP-scripts to administrate MySQL ove


```

Any idea why it will not update the PHP packages on a regular upgrade, and why it wants to install apache 1.x if I try to do a dist-upgrade?  I'm baffled, and it's been like this for a while now.

---

### Post by chapterthree on 2005-04-26
Well, I managed to resolve this issue, although I'm still not sure what the underlying issue was.  I solved this by re-installing php4-common.

```
root@girls [/home/kev]# apt-get --reinstall install php4-common
Reading Package Lists... Done
Building Dependency Tree... Done
The following extra packages will be installed:
   libapache2-mod-php4 (4.3.10-12)
   libkrb53 (1.3.6-2)
   libzzip-0-12 (0.12.83-4)
   php4-mysql (4.3.10-12)
Suggested packages:
   php4-pear (4.3.10-12)
   phpdoc ()
   krb5-doc (1.3.6-2)
   krb5-user (1.3.6-2)
The following NEW packages will be installed:
   libkrb53 (1.3.6-2)
   libzzip-0-12 (0.12.83-4)
The following packages will be upgraded:
   libapache2-mod-php4 (4.3.10-2 => 4.3.10-12)
   php4-common (4.3.10-2 => 4.3.10-12)
   php4-mysql (4.3.10-2 => 4.3.10-12)
3 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.

```

Then I was able to upgrade php4:

```
root@girls [/home/kev]# apt-get upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
The following packages will be upgraded:
   php4 (4.3.10-2 => 4.3.10-12)
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

