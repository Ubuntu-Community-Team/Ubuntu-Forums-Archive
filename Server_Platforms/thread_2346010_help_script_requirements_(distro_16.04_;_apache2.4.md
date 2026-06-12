---
title: "help script requirements (distro 16.04 ; apache2.4) : JS, CSS3, HTML5"
date: 2016-12-10
forum: Server Platforms
---

### Post by keoz2 on 2016-12-10
Hello,

This is my first post ! [IMG]https://ubuntuforums.org/images/icons/icon7.png[/IMG]
Should this section or this forum not be appropriated enough for VPS/apache issues, redirect me !
My VPS (freshly installed) is running distro Ubuntu 16.04 LTS, and my Control panel is ISP Config3
 
I wish now to install a script that ask for minimum requirements (list below) some of them are unusual to me... !
How can I verify if JS, CSS3, and HTLM5 are available on my apache2.4 server ?
How can I verify if JS, CSS3, and HTML5 are or are not enabled on my apche2.4 server ?

*** List of requirements 

    PHP 5.3 or higher
[LIST]
[*]        PHP Mail or SMTP 
[*]        PHP Sessions in working order 
[/LIST]
    1 MySQL Database (can be shared, database prefix)
    HTML5
    CSS3
    JavaScript enabled (standard)
    
Awaiting for some help and guidance,

Cordially

---

### Post by Graham_Willis on 2016-12-11
Just install the script and check if it works properly. The requirements of "JS, CSS3, HTML5" looks more like requirements for a browser than a server. Normally, from the server's point of view, all of them are static files (it's possible to execute JavaScript server-side, but I doubt that it's what's meant here). If something doesn't work, write back.

---

### Post by keoz2 on 2016-12-26
Thanks !

---

