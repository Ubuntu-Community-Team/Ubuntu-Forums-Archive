---
title: "[SOLVED] gzip support with php"
date: 2008-04-05
forum: Server Platforms
---

### Post by xyrer on 2008-04-05
Hi, I installed joomla on my lamp ubuntu server, but there's something that would make my life much easier and can't find any info on google, it's about gzip support with php, to let php uncompress files, anyone knows what should I look for at least?
thanks

---

### Post by conjur3r on 2008-04-07
On Ubuntu, zlib un/compress for PHP should be available by default.  You may have it disabled in your php.ini file.  Which version of Ubuntu are you running?

More info: [http://au.php.net/zlib](http://au.php.net/zlib)

---

### Post by xyrer on 2008-04-07
I'm using 7.10 server

---

### Post by xyrer on 2008-04-07
That was it, thank you very much, that website you gave me cleared everything, zlib was disabled by default, I enabled it and everything is working like a charm.
Thanks.

---

