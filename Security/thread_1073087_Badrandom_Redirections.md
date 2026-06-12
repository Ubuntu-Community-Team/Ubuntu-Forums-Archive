---
title: "Bad/random Redirections?"
date: 2009-02-17
forum: Security
---

### Post by redxine on 2009-02-17
I was going through my apache logs just now and found a rather interesting entry:

79.134.33.115 - - [17/Feb/2009:16:21:51 -0700] "GET [http://www.yahoo.com/](http://www.yahoo.com/) HTTP/1.1" 200 138 "-" "Mozilla/4.0 (compatible; MSIE 4.01; Windows 95)"

Yahoo.com? Last I checked, that was nowhere close to my domain name. It appears again here:

222.187.221.88 - - [17/Feb/2009:17:42:09 -0700] "GET [http://sevy.eu.org/azenv.php](http://sevy.eu.org/azenv.php) HTTP/1.1" 404 325 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"

Is this from bad DNS redirections or what? Anyone have any ideas?

---

### Post by cdenley on 2009-02-18
Somebody, or more likely something, was trying to use your web server as a proxy, and apparently failed. By default, apache uses the request URI (/azenv.php), and ignores the rest ([http://sevy.eu.org](http://sevy.eu.org)). Since that request returned a 404, the URI "/azenv.php" was not found on your server. These attempts are very common.

---

### Post by Dr Small on 2009-02-18
You will see from my thread, that I had a very similar thing happening to me:
[http://ubuntuforums.org/showthread.php?t=1005848](http://ubuntuforums.org/showthread.php?t=1005848)

---

