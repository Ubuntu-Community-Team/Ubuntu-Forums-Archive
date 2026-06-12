---
title: "installation of both php5-xcache and php-apc fails (php5enmod: not found)"
date: 2012-11-03
forum: Server Platforms
---

### Post by oli_ on 2012-11-03
After successfully installing php5-fpm and several php modules I wanted to add some opcode caching. My first choice was xcache because I used it before, however the installation failed:

```
# apt-get install php5-xcache
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  php5-xcache
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/100 kB of archives.
After this operation, 306 kB of additional disk space will be used.
Selecting previously unselected package php5-xcache.
(Reading database ... 46718 files and directories currently installed.)
Unpacking php5-xcache (from .../php5-xcache_2.0.0-1_amd64.deb) ...
Setting up php5-xcache (2.0.0-1) ...
/var/lib/dpkg/info/php5-xcache.postinst: 6: /var/lib/dpkg/info/php5-xcache.postinst: php5enmod: not found
dpkg: error processing php5-xcache (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 php5-xcache
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've never encountered a problem like this before.
Since apparently the difference between xcache and apc is rather minimal I tried to install apc instead, but it fails for the same reason.

Any idea how to fix the php5enmod issue?


About the system:
Ubuntu Server 12.10
```
# uname -a
Linux mongolia 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

```
# dpkg -l php5*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                        Version                    Architecture               Description
+++-===========================================-==========================-==========================-============================================================================================
ii  php5-cli                                    5.3.10-1ubuntu4            amd64                      command-line interpreter for the php5 scripting language
ii  php5-common                                 5.3.10-1ubuntu4            amd64                      Common files for packages built from the php5 source
ii  php5-curl                                   5.3.10-1ubuntu4            amd64                      CURL module for php5
ii  php5-fpm                                    5.3.10-1ubuntu4            amd64                      server-side, HTML-embedded scripting language (FPM-CGI binary)
ii  php5-gd                                     5.3.10-1ubuntu4            amd64                      GD module for php5
un  php5-idn                                    <none>                                                (no description available)
ii  php5-intl                                   5.3.10-1ubuntu4            amd64                      internationalisation module for php5
un  php5-json                                   <none>                                                (no description available)
ii  php5-mcrypt                                 5.3.5-0ubuntu1             amd64                      MCrypt module for php5
un  php5-mhash                                  <none>                                                (no description available)
ii  php5-mysql                                  5.3.10-1ubuntu4            amd64                      MySQL module for php5
un  php5-mysqli                                 <none>                                                (no description available)
un  php5-mysqlnd                                <none>                                                (no description available)
un  php5-suhosin                                <none>                                                (no description available)
rc  php5-xcache                                 2.0.0-1                    amd64                      Fast, stable PHP opcode cacher
ii  php5-xmlrpc                                 5.3.10-1ubuntu4            amd64                      XML-RPC module for php5

```

---

