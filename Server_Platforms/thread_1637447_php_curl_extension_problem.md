---
title: "php curl extension problem"
date: 2010-12-04
forum: Server Platforms
---

### Post by Juddling on 2010-12-04
i've installed (as root)

    aptitude install curl php5-curl libcurl3 libcurl3-dev

and added extension=curl.so to my php.ini (i assumed this wasn't done automatically because i'm using Lighty and not apache)

    service lighttpd restart

But still no luck, there is nothing about cURL when I run phpinfo()

curl.so is located in /usr/lib/php5/20090626

---

