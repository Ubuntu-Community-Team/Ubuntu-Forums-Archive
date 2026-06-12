---
title: "Apache2 Heap Error"
date: 2011-12-15
forum: Server Platforms
---

### Post by soyer38301 on 2011-12-15
Good day,

I have an 8.04 server install (32 bit) with the following apache and php installed:

Apache/2.2.8 (Ubuntu)
PHP 5.2.4-2ubuntu5.17 with Suhosin-Patch 0.9.6.2 (cli) (built: May  4 2011 09:46:14) 
Copyright (c) 1997-2007 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies

Starting on the 9th of this month I started seeing this error in the apache2 error.log

[error] [client {ip of my load balancer}] ALERT - linked list corrupt on efree() - heap corruption detected (attacker '{ip of my load balancer}', file '/home/www/{folder}/{folder}/{folder}/php/save.php'), referer: http://{host.domain.com/{folder}/com/{folder}/core/{folder}/stable.swf

No updates or changes have been made to any software for the last 3 weeks or so.

Any google searches I have done for this issue point to APC - which is not installed on this machine.

Any guidance would be appreciated.
Thanks.
Scott

---

