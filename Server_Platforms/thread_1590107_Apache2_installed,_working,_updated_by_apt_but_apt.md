---
title: "Apache2 installed, working, updated by apt but apt reports it as not installed..."
date: 2010-10-07
forum: Server Platforms
---

### Post by mansonthomas on 2010-10-07
Hi,

  I've apache2 installed on my machine, which is unwanted as I'm using lighttpd.

  I've run an updatitude update; aptitude full-upgrade and i've seen apache2 being updated : 
[PHP]
Setting up apache2.2-bin (2.2.14-5ubuntu8.2) ...
Setting up apache2-utils (2.2.14-5ubuntu8.2) ...
Setting up apache2.2-common (2.2.14-5ubuntu8.2) ...

Setting up apache2-mpm-prefork (2.2.14-5ubuntu8.2) ...
 * Starting web server apache2
   ...done.[/PHP]But aptitude reports it as 'not installed'

thomas@sd1:~$ sudo aptitude show apache2
[PHP][sudo] password for thomas:
Package: apache2
State: not installed
Version: 2.2.14-5ubuntu8.2
Priority: optional
Section: httpd
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 36.9k
[/PHP]Any idea on how to clean this mess and remove apache2? 




[COLOR=Blue]Erf... I didn't notice the name of the package which was apache2.2-bin and not apache2 so :[/COLOR]
[PHP]sudo aptitude  remove apache2.2-bin apache2-mpm-prefork apache2.2-common apache2-utils libapache2-mod-php5[/PHP][COLOR=Blue]Solve the issue...[/COLOR]









Regards,
Thomas

---

