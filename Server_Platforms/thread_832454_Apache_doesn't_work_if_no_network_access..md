---
title: "Apache doesn't work if no network access."
date: 2008-06-17
forum: Server Platforms
---

### Post by SpankinPartier on 2008-06-17
I've turned my laptop into a LAMP server to do some PHP development.  Apache works well whenever I have either a wireless network or a wired network access.  But whenever I don't have network access I can't access my Apache server using [http://localhost](http://localhost) or [http://127.0.0.1](http://127.0.0.1).  

Any ideas?

---

### Post by windependence on 2008-06-18
Can you ping 127.0.0.1?

Have you checked the Apache access log in /var/log?

-Tim

---

### Post by zccpop on 2008-09-20
> **windependence said:**
> Can you ping 127.0.0.1?

Have you checked the Apache access log in /var/log?

-Tim

Could you talk more detailly?

I met the same question.

---

### Post by windependence on 2008-09-20
From the command line on your server do this:

```
ping 127.0.0.1
```

To check the access log:

```
cat /var/log/apache2/access.log 
```

and

```
cat /var/log/apache2/error.log 
```

You can post the results here if your not sure of the errors.

-Tim

---

### Post by zccpop on 2008-09-20
> **windependence said:**
> From the command line on your server do this:

```
ping 127.0.0.1
```

To check the access log:

```
cat /var/log/apache2/access.log 
```

and

```
cat /var/log/apache2/error.log 
```

You can post the results here if your not sure of the errors.

-Tim


The access.log:
```

127.0.0.1 - - [19/Sep/2008:15:54:42 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:15:54:42 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:15:54:42 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:15:54:42 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:15:54:42 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:15:56:01 +0800] "GET / HTTP/1.1" 200 45 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:15:56:01 +0800] "GET /favicon.ico HTTP/1.1" 404 283 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:15:56:04 +0800] "GET /favicon.ico HTTP/1.1" 404 283 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:15:59:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:15:59:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:15:59:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:15:59:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:15:59:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:15:59:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:00:00 +0800] "GET /wiki HTTP/1.1" 301 344 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:00 +0800] "GET /wiki/ HTTP/1.1" 302 - "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:01 +0800] "GET /wiki/lib/exe/js.php?edit=0&write=0 HTTP/1.1" 200 23951 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:01 +0800] "GET /wiki/lib/exe/css.php?s=all&t=dokubook HTTP/1.1" 200 3212 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:00 +0800] "GET /wiki/doku.php HTTP/1.1" 200 8683 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:01 +0800] "GET /wiki/lib/exe/css.php?s=print&t=dokubook HTTP/1.1" 200 5890 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:01 +0800] "GET /wiki/lib/exe/css.php?t=dokubook HTTP/1.1" 200 33721 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/tpl/dokubook/images/favicon.ico HTTP/1.1" 200 7406 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/tpl/dokubook/images/dwbg.jpg HTTP/1.1" 200 1060 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/tpl/dokubook/images/dokuwiki-128.png HTTP/1.1" 200 10248 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/tpl/dokubook/images/button-chimeric-de.png HTTP/1.1" 200 296 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/tpl/dokubook/images/button-cc.gif HTTP/1.1" 200 1231 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/tpl/dokubook/images/button-css.png HTTP/1.1" 200 299 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/tpl/dokubook/images/button-dw.png HTTP/1.1" 200 427 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/tpl/dokubook/images/button-firefox.png HTTP/1.1" 200 1063 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/tpl/dokubook/images/button-rss.png HTTP/1.1" 200 280 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/tpl/dokubook/images/button-xhtml.png HTTP/1.1" 200 321 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/tpl/dokubook/images/closed.gif HTTP/1.1" 200 54 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/tpl/dokubook/images/inputshadow.png HTTP/1.1" 200 155 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/tpl/dokubook/images/tool-index.png HTTP/1.1" 200 935 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/tpl/dokubook/images/tool-recent.png HTTP/1.1" 200 464 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/tpl/dokubook/images/tool-backlink.png HTTP/1.1" 200 540 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/images/error.png HTTP/1.1" 200 706 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/tpl/dokubook/images/tool-source.png HTTP/1.1" 200 617 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/tpl/dokubook/images/tool-revisions.png HTTP/1.1" 200 603 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/tpl/dokubook/images/tool-login.png HTTP/1.1" 200 650 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:02 +0800] "GET /wiki/lib/exe/indexer.php?id=home&1221811202 HTTP/1.1" 200 42 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:03 +0800] "GET /wiki/ HTTP/1.1" 302 - "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:03 +0800] "GET /wiki/doku.php HTTP/1.1" 200 8683 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:03 +0800] "GET /wiki/lib/exe/indexer.php?id=home&1221811203 HTTP/1.1" 200 42 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:10 +0800] "GET /vote HTTP/1.1" 301 344 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:10 +0800] "GET /vote/ HTTP/1.1" 200 1286 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:10 +0800] "GET /icons/blank.gif HTTP/1.1" 200 148 "http://localhost/vote/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:10 +0800] "GET /icons/back.gif HTTP/1.1" 200 216 "http://localhost/vote/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:10 +0800] "GET /icons/unknown.gif HTTP/1.1" 200 245 "http://localhost/vote/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:10 +0800] "GET /icons/folder.gif HTTP/1.1" 200 225 "http://localhost/vote/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:10 +0800] "GET /favicon.ico HTTP/1.1" 404 323 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:13 +0800] "GET /vote/test.php HTTP/1.1" 200 19 "http://localhost/vote/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:14 +0800] "GET /favicon.ico HTTP/1.1" 404 323 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:14 +0800] "GET /favicon.ico HTTP/1.1" 404 323 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:16 +0800] "GET /vote/config.inc.php HTTP/1.1" 200 3 "http://localhost/vote/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:00:31 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:00:33 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:05:08 +0800] "GET /phpmyadmin HTTP/1.1" 404 322 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:08:46 +0800] "GET /phpmyadmin HTTP/1.1" 404 322 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:10:14 +0800] "GET /PHPMyAdmin HTTP/1.1" 404 322 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:10:52 +0800] "GET /phpmyadmin HTTP/1.1" 404 322 "http://ubuntuforums.org/showthread.php?t=841173&highlight=phpMyAdmin+setup&page=2" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:12:49 +0800] "GET /phpmyadmin HTTP/1.1" 403 326 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:12:52 +0800] "GET /phpmyadmin HTTP/1.1" 403 326 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:20:49 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:20:49 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:20:49 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:20:49 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:20:49 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:20:49 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:20:49 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:20:49 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:20:49 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:20:49 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:20:49 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:20:49 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:21:03 +0800] "GET /phpmyadmin HTTP/1.1" 301 350 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:03 +0800] "GET /phpmyadmin/ HTTP/1.1" 200 8136 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:04 +0800] "GET /phpmyadmin/favicon.ico HTTP/1.1" 200 18902 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:04 +0800] "GET /phpmyadmin/print.css HTTP/1.1" 200 1063 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:04 +0800] "GET /phpmyadmin/phpmyadmin.css.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=right&nocache=3615148564 HTTP/1.1" 200 20584 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:04 +0800] "GET /phpmyadmin/themes/original/img/logo_right.png HTTP/1.1" 200 5658 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:04 +0800] "GET /phpmyadmin/themes/original/img/b_help.png HTTP/1.1" 200 229 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:04 +0800] "GET /phpmyadmin/themes/original/img/s_notice.png HTTP/1.1" 200 247 "http://localhost/phpmyadmin/phpmyadmin.css.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:04 +0800] "GET /phpmyadmin/themes/original/img/b_info.png HTTP/1.1" 200 234 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "POST /phpmyadmin/index.php HTTP/1.1" 302 - "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/index.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8 HTTP/1.1" 200 2482 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/js/querywindow.js HTTP/1.1" 200 11069 "http://localhost/phpmyadmin/index.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/main.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8 HTTP/1.1" 200 7085 "http://localhost/phpmyadmin/index.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/navigation.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8 HTTP/1.1" 200 1097 "http://localhost/phpmyadmin/index.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/js/navigation.js HTTP/1.1" 200 3916 "http://localhost/phpmyadmin/navigation.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/phpmyadmin.css.php?token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=left&nocache=3615148564 HTTP/1.1" 200 4100 "http://localhost/phpmyadmin/navigation.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/js/functions.js HTTP/1.1" 200 40801 "http://localhost/phpmyadmin/navigation.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/b_home.png HTTP/1.1" 200 370 "http://localhost/phpmyadmin/navigation.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/s_loggoff.png HTTP/1.1" 200 262 "http://localhost/phpmyadmin/navigation.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/b_selboard.png HTTP/1.1" 200 274 "http://localhost/phpmyadmin/navigation.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/b_docs.png HTTP/1.1" 200 292 "http://localhost/phpmyadmin/navigation.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/phpmyadmin.css.php?token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=right&nocache=3615148564 HTTP/1.1" 200 20584 "http://localhost/phpmyadmin/main.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/b_sqlhelp.png HTTP/1.1" 200 287 "http://localhost/phpmyadmin/navigation.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/js/tooltip.js HTTP/1.1" 200 5228 "http://localhost/phpmyadmin/main.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/window-new.png HTTP/1.1" 200 583 "http://localhost/phpmyadmin/main.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/s_host.png HTTP/1.1" 200 316 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/item_ltr.png HTTP/1.1" 200 173 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/s_asci.png HTTP/1.1" 200 254 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/logo_left.png HTTP/1.1" 200 6854 "http://localhost/phpmyadmin/navigation.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/b_newdb.png HTTP/1.1" 200 408 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/s_status.png HTTP/1.1" 200 313 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/s_vars.png HTTP/1.1" 200 306 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/s_process.png HTTP/1.1" 200 362 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/b_engine.png HTTP/1.1" 200 362 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/s_reload.png HTTP/1.1" 200 245 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/s_rights.png HTTP/1.1" 200 512 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/s_db.png HTTP/1.1" 200 285 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/b_export.png HTTP/1.1" 200 313 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/b_import.png HTTP/1.1" 200 310 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/s_lang.png HTTP/1.1" 200 422 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:09 +0800] "GET /phpmyadmin/themes/original/img/s_theme.png HTTP/1.1" 200 737 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:14 +0800] "GET /phpmyadmin/index.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8 HTTP/1.1" 200 2275 "http://localhost/phpmyadmin/navigation.php?lang=en-utf-8&convcharset=iso-8859-1&collation_connection=utf8_unicode_ci&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:14 +0800] "GET /phpmyadmin/navigation.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8 HTTP/1.1" 200 2107 "http://localhost/phpmyadmin/index.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:14 +0800] "GET /phpmyadmin/db_structure.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8 HTTP/1.1" 200 4811 "http://localhost/phpmyadmin/index.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:15 +0800] "GET /phpmyadmin/themes/original/img/b_sbrowse.png HTTP/1.1" 200 197 "http://localhost/phpmyadmin/navigation.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:16 +0800] "GET /phpmyadmin/themes/original/img/b_props.png HTTP/1.1" 200 294 "http://localhost/phpmyadmin/db_structure.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:16 +0800] "GET /phpmyadmin/themes/original/img/b_sql.png HTTP/1.1" 200 322 "http://localhost/phpmyadmin/db_structure.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:16 +0800] "GET /phpmyadmin/themes/original/img/b_search.png HTTP/1.1" 200 605 "http://localhost/phpmyadmin/db_structure.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:16 +0800] "GET /phpmyadmin/themes/original/img/b_tblops.png HTTP/1.1" 200 345 "http://localhost/phpmyadmin/db_structure.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:16 +0800] "GET /phpmyadmin/themes/original/img/b_deltbl.png HTTP/1.1" 200 364 "http://localhost/phpmyadmin/db_structure.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:16 +0800] "GET /phpmyadmin/themes/original/img/b_tipp.png HTTP/1.1" 200 308 "http://localhost/phpmyadmin/db_structure.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:16 +0800] "GET /phpmyadmin/themes/original/img/bd_browse.png HTTP/1.1" 200 265 "http://localhost/phpmyadmin/db_structure.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:16 +0800] "GET /phpmyadmin/themes/original/img/bd_select.png HTTP/1.1" 200 524 "http://localhost/phpmyadmin/db_structure.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:16 +0800] "GET /phpmyadmin/themes/original/img/b_insrow.png HTTP/1.1" 200 283 "http://localhost/phpmyadmin/db_structure.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:16 +0800] "GET /phpmyadmin/themes/original/img/bd_empty.png HTTP/1.1" 200 298 "http://localhost/phpmyadmin/db_structure.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:16 +0800] "GET /phpmyadmin/themes/original/img/b_drop.png HTTP/1.1" 200 311 "http://localhost/phpmyadmin/db_structure.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:16 +0800] "GET /phpmyadmin/themes/original/img/b_browse.png HTTP/1.1" 200 265 "http://localhost/phpmyadmin/db_structure.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:16 +0800] "GET /phpmyadmin/themes/original/img/b_select.png HTTP/1.1" 200 540 "http://localhost/phpmyadmin/db_structure.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:16 +0800] "GET /phpmyadmin/themes/original/img/b_empty.png HTTP/1.1" 200 298 "http://localhost/phpmyadmin/db_structure.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:16 +0800] "GET /phpmyadmin/themes/original/img/arrow_ltr.png HTTP/1.1" 200 277 "http://localhost/phpmyadmin/db_structure.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:16 +0800] "GET /phpmyadmin/themes/original/img/b_print.png HTTP/1.1" 200 574 "http://localhost/phpmyadmin/db_structure.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:16 +0800] "GET /phpmyadmin/themes/original/img/b_tblanalyse.png HTTP/1.1" 200 296 "http://localhost/phpmyadmin/db_structure.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:16 +0800] "GET /phpmyadmin/themes/original/img/b_newtbl.png HTTP/1.1" 200 409 "http://localhost/phpmyadmin/db_structure.php?db=mysql&token=501290f0ccd9f3c1fb94ec759c9d1ec8" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:21:16 +0800] "GET /phpmyadmin/themes/original/img/error.ico HTTP/1.1" 200 318 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=501290f0ccd9f3c1fb94ec759c9d1ec8&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:16:50:00 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:50:00 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:50:00 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:50:00 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:50:00 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:50:00 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:50:00 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:50:00 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:16:50:00 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:18:28:12 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:18:28:12 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:18:28:12 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:18:28:12 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:18:28:12 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:19:25:18 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:19:25:18 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:19:25:18 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:19:25:18 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:19:25:18 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:19:29:59 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:19:29:59 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:19:29:59 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:19:29:59 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:19:29:59 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:21:55:13 +0800] "GET /phpmyadmin/ HTTP/1.1" 200 7987 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:21:55:14 +0800] "GET /phpmyadmin/favicon.ico HTTP/1.1" 200 18902 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:21:55:14 +0800] "GET /phpmyadmin/print.css HTTP/1.1" 200 1063 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:21:55:14 +0800] "GET /phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564 HTTP/1.1" 200 20584 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:21:55:14 +0800] "GET /phpmyadmin/themes/original/img/logo_right.png HTTP/1.1" 200 5658 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:21:55:14 +0800] "GET /phpmyadmin/themes/original/img/b_info.png HTTP/1.1" 200 234 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:21:55:14 +0800] "GET /phpmyadmin/themes/original/img/b_help.png HTTP/1.1" 200 229 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:11 +0800] "GET /wiki HTTP/1.1" 301 344 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:11 +0800] "GET /wiki/ HTTP/1.1" 302 - "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:11 +0800] "GET /wiki/doku.php HTTP/1.1" 200 8683 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:11 +0800] "GET /wiki/lib/exe/css.php?t=dokubook HTTP/1.1" 200 33721 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:11 +0800] "GET /wiki/lib/exe/css.php?s=print&t=dokubook HTTP/1.1" 200 5890 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:11 +0800] "GET /wiki/lib/exe/js.php?edit=0&write=0 HTTP/1.1" 200 23951 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:11 +0800] "GET /wiki/lib/exe/css.php?s=all&t=dokubook HTTP/1.1" 200 3212 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/tpl/dokubook/images/favicon.ico HTTP/1.1" 200 7406 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/tpl/dokubook/images/dwbg.jpg HTTP/1.1" 200 1060 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/tpl/dokubook/images/dokuwiki-128.png HTTP/1.1" 200 10248 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/tpl/dokubook/images/button-chimeric-de.png HTTP/1.1" 200 296 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/tpl/dokubook/images/button-cc.gif HTTP/1.1" 200 1231 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/tpl/dokubook/images/button-css.png HTTP/1.1" 200 299 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/tpl/dokubook/images/button-dw.png HTTP/1.1" 200 427 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/tpl/dokubook/images/button-firefox.png HTTP/1.1" 200 1063 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/tpl/dokubook/images/button-rss.png HTTP/1.1" 200 280 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/tpl/dokubook/images/button-xhtml.png HTTP/1.1" 200 321 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/images/error.png HTTP/1.1" 200 706 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/tpl/dokubook/images/closed.gif HTTP/1.1" 200 54 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/tpl/dokubook/images/inputshadow.png HTTP/1.1" 200 155 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/tpl/dokubook/images/tool-index.png HTTP/1.1" 200 935 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/tpl/dokubook/images/tool-recent.png HTTP/1.1" 200 464 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/tpl/dokubook/images/tool-backlink.png HTTP/1.1" 200 540 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/tpl/dokubook/images/tool-login.png HTTP/1.1" 200 650 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/tpl/dokubook/images/tool-source.png HTTP/1.1" 200 617 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/tpl/dokubook/images/tool-revisions.png HTTP/1.1" 200 603 "http://localhost/wiki/lib/exe/css.php?t=dokubook" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:06:12 +0800] "GET /wiki/lib/exe/indexer.php?id=home&1221833172 HTTP/1.1" 200 42 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:01 +0800] "GET /phpmyadmin HTTP/1.1" 301 350 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:01 +0800] "GET /phpmyadmin/ HTTP/1.1" 200 7987 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:01 +0800] "GET /phpmyadmin/print.css HTTP/1.1" 304 - "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:01 +0800] "GET /phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564 HTTP/1.1" 200 20584 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:01 +0800] "GET /phpmyadmin/themes/original/img/logo_right.png HTTP/1.1" 304 - "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:01 +0800] "GET /phpmyadmin/themes/original/img/b_info.png HTTP/1.1" 304 - "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:01 +0800] "GET /phpmyadmin/themes/original/img/b_help.png HTTP/1.1" 304 - "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:04 +0800] "POST /phpmyadmin/index.php HTTP/1.1" 302 - "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:04 +0800] "GET /phpmyadmin/index.php?lang=en-utf-8&token=a1de95438eb9b623db620ffff6423621 HTTP/1.1" 200 2272 "http://localhost/phpmyadmin/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/js/querywindow.js HTTP/1.1" 200 11069 "http://localhost/phpmyadmin/index.php?lang=en-utf-8&token=a1de95438eb9b623db620ffff6423621" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/main.php?lang=en-utf-8&token=a1de95438eb9b623db620ffff6423621 HTTP/1.1" 200 7083 "http://localhost/phpmyadmin/index.php?lang=en-utf-8&token=a1de95438eb9b623db620ffff6423621" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/js/tooltip.js HTTP/1.1" 200 5228 "http://localhost/phpmyadmin/main.php?lang=en-utf-8&token=a1de95438eb9b623db620ffff6423621" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/navigation.php?lang=en-utf-8&token=a1de95438eb9b623db620ffff6423621 HTTP/1.1" 200 1108 "http://localhost/phpmyadmin/index.php?lang=en-utf-8&token=a1de95438eb9b623db620ffff6423621" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/themes/original/img/window-new.png HTTP/1.1" 200 583 "http://localhost/phpmyadmin/main.php?lang=en-utf-8&token=a1de95438eb9b623db620ffff6423621" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/themes/original/img/s_host.png HTTP/1.1" 200 316 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/themes/original/img/item_ltr.png HTTP/1.1" 200 173 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/themes/original/img/s_status.png HTTP/1.1" 200 313 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/themes/original/img/b_engine.png HTTP/1.1" 200 362 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/themes/original/img/s_theme.png HTTP/1.1" 200 737 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/js/navigation.js HTTP/1.1" 200 3916 "http://localhost/phpmyadmin/navigation.php?lang=en-utf-8&token=a1de95438eb9b623db620ffff6423621" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/themes/original/img/b_docs.png HTTP/1.1" 200 292 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/themes/original/img/b_home.png HTTP/1.1" 200 370 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/themes/original/img/b_newdb.png HTTP/1.1" 200 408 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/themes/original/img/s_asci.png HTTP/1.1" 200 254 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=left&nocache=3615148564 HTTP/1.1" 200 4100 "http://localhost/phpmyadmin/navigation.php?lang=en-utf-8&token=a1de95438eb9b623db620ffff6423621" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/themes/original/img/s_vars.png HTTP/1.1" 200 306 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/themes/original/img/s_process.png HTTP/1.1" 200 362 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/themes/original/img/s_reload.png HTTP/1.1" 200 245 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:05 +0800] "GET /phpmyadmin/themes/original/img/s_rights.png HTTP/1.1" 200 512 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:06 +0800] "GET /phpmyadmin/themes/original/img/s_db.png HTTP/1.1" 200 285 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:06 +0800] "GET /phpmyadmin/themes/original/img/b_export.png HTTP/1.1" 200 313 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:07 +0800] "GET /phpmyadmin/js/functions.js HTTP/1.1" 200 40801 "http://localhost/phpmyadmin/navigation.php?lang=en-utf-8&token=a1de95438eb9b623db620ffff6423621" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:07 +0800] "GET /phpmyadmin/themes/original/img/logo_left.png HTTP/1.1" 200 6854 "http://localhost/phpmyadmin/navigation.php?lang=en-utf-8&token=a1de95438eb9b623db620ffff6423621" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:07 +0800] "GET /phpmyadmin/themes/original/img/b_selboard.png HTTP/1.1" 200 274 "http://localhost/phpmyadmin/navigation.php?lang=en-utf-8&token=a1de95438eb9b623db620ffff6423621" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:07 +0800] "GET /phpmyadmin/themes/original/img/b_sqlhelp.png HTTP/1.1" 200 287 "http://localhost/phpmyadmin/navigation.php?lang=en-utf-8&token=a1de95438eb9b623db620ffff6423621" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:07 +0800] "GET /phpmyadmin/themes/original/img/b_import.png HTTP/1.1" 200 310 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:07 +0800] "GET /phpmyadmin/themes/original/img/s_loggoff.png HTTP/1.1" 200 262 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:07 +0800] "GET /phpmyadmin/themes/original/img/s_lang.png HTTP/1.1" 200 422 "http://localhost/phpmyadmin/phpmyadmin.css.php?token=a1de95438eb9b623db620ffff6423621&js_frame=right&nocache=3615148564" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:18 +0800] "GET /wiki HTTP/1.1" 301 344 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:18 +0800] "GET /wiki/ HTTP/1.1" 302 - "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:18 +0800] "GET /wiki/doku.php HTTP/1.1" 200 8683 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:18 +0800] "GET /wiki/lib/exe/indexer.php?id=home&1221833238 HTTP/1.1" 200 42 "http://localhost/wiki/doku.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:22 +0800] "GET /link HTTP/1.1" 404 316 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
::1 - - [19/Sep/2008:22:07:22 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:22:07:23 +0800] "GET /favicon.ico HTTP/1.1" 404 323 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
::1 - - [19/Sep/2008:22:07:23 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:07:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:22:07:25 +0800] "GET /links HTTP/1.1" 301 345 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:25 +0800] "GET /links/ HTTP/1.1" 200 9484 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:25 +0800] "GET /links/style.css HTTP/1.1" 200 2817 "http://localhost/links/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:25 +0800] "GET /links/images/headerleft.gif HTTP/1.1" 200 2494 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:25 +0800] "GET /links/images/rss.gif HTTP/1.1" 200 1387 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:25 +0800] "GET /links/images/ds_bg.gif HTTP/1.1" 404 334 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:25 +0800] "GET /links/images/link-l.gif HTTP/1.1" 200 272 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:25 +0800] "GET /links/images/nav.gif HTTP/1.1" 200 2291 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:25 +0800] "GET /links/images/c_bg.gif HTTP/1.1" 200 66 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:25 +0800] "GET /links/images/link-r.gif HTTP/1.1" 200 987 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
::1 - - [19/Sep/2008:22:07:25 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:22:07:26 +0800] "GET /favicon.ico HTTP/1.1" 404 323 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:22:07:26 +0800] "GET /favicon.ico HTTP/1.1" 404 323 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
::1 - - [19/Sep/2008:22:07:26 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:07:27 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:07:28 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:07:29 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:07:42 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:07:43 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:07:44 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:07:45 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:07:46 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:07:47 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [19/Sep/2008:22:10:41 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [19/Sep/2008:23:11:19 +0800] "GET /links HTTP/1.1" 301 345 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:11:19 +0800] "GET /links/ HTTP/1.1" 200 9484 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:11:19 +0800] "GET /links/style.css HTTP/1.1" 200 2817 "http://localhost/links/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:11:19 +0800] "GET /links/images/headerleft.gif HTTP/1.1" 200 2494 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:11:19 +0800] "GET /links/images/rss.gif HTTP/1.1" 200 1387 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:11:19 +0800] "GET /links/images/c_bg.gif HTTP/1.1" 200 66 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:11:19 +0800] "GET /links/images/ds_bg.gif HTTP/1.1" 404 334 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:11:19 +0800] "GET /links/images/link-l.gif HTTP/1.1" 200 272 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:11:19 +0800] "GET /links/images/link-r.gif HTTP/1.1" 200 987 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:11:19 +0800] "GET /links/images/nav.gif HTTP/1.1" 200 2291 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:11:19 +0800] "GET /favicon.ico HTTP/1.1" 404 323 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:11:22 +0800] "GET /favicon.ico HTTP/1.1" 404 323 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:14:30 +0800] "GET / HTTP/1.1" 200 4380 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:14:32 +0800] "GET / HTTP/1.1" 200 4380 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:14:32 +0800] "GET /favicon.ico HTTP/1.1" 404 323 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:14:32 +0800] "GET /favicon.ico HTTP/1.1" 404 323 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:14:39 +0800] "GET / HTTP/1.1" 200 4380 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:14:40 +0800] "GET / HTTP/1.1" 200 4380 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:14:42 +0800] "GET /links HTTP/1.1" 301 345 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:14:42 +0800] "GET /links/images/ds_bg.gif HTTP/1.1" 404 334 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:15:31 +0800] "GET /links/ HTTP/1.1" 304 - "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:15:31 +0800] "GET /links/style.css HTTP/1.1" 304 - "http://localhost/links/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:15:31 +0800] "GET /links/images/headerleft.gif HTTP/1.1" 304 - "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:15:31 +0800] "GET /links/images/rss.gif HTTP/1.1" 304 - "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:15:31 +0800] "GET /links/images/c_bg.gif HTTP/1.1" 304 - "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:15:31 +0800] "GET /links/images/ds_bg.gif HTTP/1.1" 404 334 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:15:31 +0800] "GET /links/images/link-l.gif HTTP/1.1" 304 - "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:15:31 +0800] "GET /links/images/link-r.gif HTTP/1.1" 304 - "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [19/Sep/2008:23:15:31 +0800] "GET /links/images/nav.gif HTTP/1.1" 304 - "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:00:15:20 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [20/Sep/2008:00:15:20 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [20/Sep/2008:00:15:20 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [20/Sep/2008:00:15:20 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [20/Sep/2008:00:15:20 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [20/Sep/2008:00:15:20 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [20/Sep/2008:13:00:12 +0800] "GET /links HTTP/1.1" 301 345 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:13:00:12 +0800] "GET /links/ HTTP/1.1" 200 9484 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:13:00:12 +0800] "GET /links/style.css HTTP/1.1" 200 2817 "http://localhost/links/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:13:00:12 +0800] "GET /links/images/ds_bg.gif HTTP/1.1" 404 334 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:13:00:12 +0800] "GET /links/images/rss.gif HTTP/1.1" 200 1387 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:13:00:12 +0800] "GET /links/images/headerleft.gif HTTP/1.1" 200 2494 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:13:00:12 +0800] "GET /links/images/c_bg.gif HTTP/1.1" 200 66 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:13:00:12 +0800] "GET /links/images/link-l.gif HTTP/1.1" 200 272 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:13:00:12 +0800] "GET /links/images/link-r.gif HTTP/1.1" 200 987 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:13:00:12 +0800] "GET /links/images/nav.gif HTTP/1.1" 200 2291 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:13:00:13 +0800] "GET /favicon.ico HTTP/1.1" 404 323 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:13:00:13 +0800] "GET /links/images/link-r-o.gif HTTP/1.1" 200 997 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:13:00:16 +0800] "GET /favicon.ico HTTP/1.1" 404 323 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:13:00:18 +0800] "GET /links/images/rss_o.gif HTTP/1.1" 200 1387 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
::1 - - [20/Sep/2008:13:00:31 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:13:00:34 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:13:00:35 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:13:06:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:13:06:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:13:06:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:13:06:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:13:06:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:13:06:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:13:06:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:13:06:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:13:06:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:13:06:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:13:06:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:13:06:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:13:06:24 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [20/Sep/2008:16:13:12 +0800] "telnet " 200 4380 "-" "-"
127.0.0.1 - - [20/Sep/2008:16:13:31 +0800] "^]" 200 4380 "-" "-"
127.0.0.1 - - [20/Sep/2008:16:14:18 +0800] "GET / HTTP/1.0\r" 200 4380 "-" "-"
127.0.0.1 - - [20/Sep/2008:16:17:35 +0800] "GET / HTTP/1.1" 200 4380 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:16:23:44 +0800] "GET /links/index.html HTTP/1.1" 200 9484 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:16:23:44 +0800] "GET /links/style.css HTTP/1.1" 304 - "http://localhost/links/index.html" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:16:23:44 +0800] "GET /links/images/rss.gif HTTP/1.1" 304 - "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:16:23:44 +0800] "GET /links/images/c_bg.gif HTTP/1.1" 304 - "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:16:23:44 +0800] "GET /links/images/ds_bg.gif HTTP/1.1" 404 334 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:16:23:44 +0800] "GET /links/images/link-l.gif HTTP/1.1" 304 - "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:16:23:44 +0800] "GET /links/images/headerleft.gif HTTP/1.1" 304 - "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:16:23:44 +0800] "GET /links/images/link-r.gif HTTP/1.1" 304 - "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:16:23:44 +0800] "GET /links/images/nav.gif HTTP/1.1" 304 - "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
::1 - - [20/Sep/2008:16:26:06 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:16:26:06 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:16:26:06 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:16:26:06 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:16:26:06 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:16:26:06 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:16:26:06 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [20/Sep/2008:17:23:35 +0800] "GET / HTTP/1.1" 200 4380 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:17:23:38 +0800] "GET /links HTTP/1.1" 301 345 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:17:23:38 +0800] "GET /favicon.ico HTTP/1.1" 404 323 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:17:23:38 +0800] "GET /links/images/ds_bg.gif HTTP/1.1" 404 334 "http://localhost/links/style.css" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [20/Sep/2008:18:53:39 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [20/Sep/2008:18:53:39 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [20/Sep/2008:18:53:39 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [20/Sep/2008:18:53:39 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [20/Sep/2008:18:53:39 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [20/Sep/2008:18:53:39 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:20:35:25 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:20:35:25 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:20:35:25 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:20:35:25 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
::1 - - [20/Sep/2008:20:35:25 +0800] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"

```

---

### Post by zccpop on 2008-09-20
The error.log

```


[Fri Sep 19 15:54:41 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Fri Sep 19 15:54:42 2008] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Sep 19 15:54:42 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Fri Sep 19 15:56:01 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Sep 19 15:56:04 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Sep 19 15:59:24 2008] [notice] caught SIGWINCH, shutting down gracefully
[Fri Sep 19 15:59:34 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Fri Sep 19 16:00:10 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/favicon.ico
[Fri Sep 19 16:00:14 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/favicon.ico
[Fri Sep 19 16:00:14 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/favicon.ico
[Fri Sep 19 16:05:08 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/phpmyadmin
[Fri Sep 19 16:08:46 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/phpmyadmin
[Fri Sep 19 16:10:14 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/PHPMyAdmin
[Fri Sep 19 16:10:52 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/phpmyadmin, referer: http://ubuntuforums.org/showthread.php?t=841173&highlight=phpMyAdmin+setup&page=2
[Fri Sep 19 16:12:49 2008] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /home/zcc/WWW/phpmyadmin
[Fri Sep 19 16:12:52 2008] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /home/zcc/WWW/phpmyadmin
[Fri Sep 19 16:20:49 2008] [notice] caught SIGWINCH, shutting down gracefully
[Fri Sep 19 16:20:59 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Fri Sep 19 16:50:00 2008] [notice] caught SIGWINCH, shutting down gracefully
[Fri Sep 19 18:18:04 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Fri Sep 19 18:28:12 2008] [notice] caught SIGWINCH, shutting down gracefully
[Fri Sep 19 18:28:22 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Fri Sep 19 19:25:18 2008] [notice] caught SIGWINCH, shutting down gracefully
[Fri Sep 19 19:25:26 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Fri Sep 19 19:29:59 2008] [notice] caught SIGWINCH, shutting down gracefully
[Fri Sep 19 21:53:37 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Fri Sep 19 22:07:22 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/link
[Fri Sep 19 22:07:23 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/favicon.ico
[Fri Sep 19 22:07:25 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/links/images/ds_bg.gif, referer: http://localhost/links/style.css
[Fri Sep 19 22:07:26 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/favicon.ico
[Fri Sep 19 22:07:26 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/favicon.ico
[Fri Sep 19 22:10:41 2008] [notice] caught SIGWINCH, shutting down gracefully
[Fri Sep 19 22:11:38 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Fri Sep 19 23:11:19 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/links/images/ds_bg.gif, referer: http://localhost/links/style.css
[Fri Sep 19 23:11:19 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/favicon.ico
[Fri Sep 19 23:11:22 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/favicon.ico
[Fri Sep 19 23:14:32 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/favicon.ico
[Fri Sep 19 23:14:32 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/favicon.ico
[Fri Sep 19 23:14:42 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/links/images/ds_bg.gif, referer: http://localhost/links/style.css
[Fri Sep 19 23:15:31 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/links/images/ds_bg.gif, referer: http://localhost/links/style.css
[Sat Sep 20 00:15:20 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Sep 20 10:57:40 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Sep 20 13:00:12 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/links/images/ds_bg.gif, referer: http://localhost/links/style.css
[Sat Sep 20 13:00:13 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/favicon.ico
[Sat Sep 20 13:00:16 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/favicon.ico
[Sat Sep 20 13:06:24 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Sep 20 16:03:45 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Sep 20 16:23:44 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/links/images/ds_bg.gif, referer: http://localhost/links/style.css
[Sat Sep 20 16:26:06 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Sep 20 16:26:16 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Sep 20 17:23:38 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/favicon.ico
[Sat Sep 20 17:23:38 2008] [error] [client 127.0.0.1] File does not exist: /home/zcc/WWW/links/images/ds_bg.gif, referer: http://localhost/links/style.css
[Sat Sep 20 18:53:39 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Sep 20 20:25:12 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Sep 20 20:35:25 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Sep 20 20:36:22 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations

```

---

### Post by windependence on 2008-09-20
Well, it's pretty obvious what the problem is:

```
File does not exist: /home/zcc/WWW/various_files
```

Why is your document root set to /home/zcc/WWW? Or is this a symbolic link? I can never understand why people do this. 

It looks like the files you are trying to serve are actually not located at /home/zcc/WWW but somewhere else.

What is the output of :

```
ls -la /home/zcc/WWW
```


-Tim

---

### Post by zccpop on 2008-09-20
> **windependence said:**
> Well, it's pretty obvious what the problem is:

```
File does not exist: /home/zcc/WWW/various_files
```

Why is your document root set to /home/zcc/WWW? Or is this a symbolic link? I can never understand why people do this. 

It looks like the files you are trying to serve are actually not located at /home/zcc/WWW but somewhere else.

What is the output of :

```
ls -la /home/zcc/WWW
```


-Tim

```

drwxrwxrwx  6 zcc zcc 4096 2008-09-19 16:22 .
drwxr-xr-x 53 zcc zcc 4096 2008-09-21 09:22 ..
-rwxrwxrwx  1 zcc zcc 6919 2008-02-13 05:22 index.php
drwxrwxrwx  3 zcc zcc 4096 2008-09-16 08:36 links
drwxrwxrwx  3 zcc zcc 4096 2008-09-16 08:36 PHP Beautifier
-rwxrwxrwx  1 zcc zcc   17 2008-07-28 15:44 phpinfo.php
drwxrwxrwx  3 zcc zcc 4096 2008-09-19 19:29 vote
drwxrwxrwx  6 zcc zcc 4096 2008-09-16 08:37 wiki

```

I think the reason that some people like me set the dir is:

We only need to study the program language, not the server tech.

I followed the wiki, and what dir change to home looks suit me.

We cannot use linux good enough, and we didn't use the commands like 
"cat"&#12289;"ls" and so on often . We only operate like windows. I knew it's not a good habit but as a beginner the habit isn't fixed easily.

---

### Post by zccpop on 2008-09-20
> **windependence said:**
> Well, it's pretty obvious what the problem is:

```
File does not exist: /home/zcc/WWW/various_files
```

Why is your document root set to /home/zcc/WWW? Or is this a symbolic link? I can never understand why people do this. 

It looks like the files you are trying to serve are actually not located at /home/zcc/WWW but somewhere else.

What is the output of :

```
ls -la /home/zcc/WWW
```


-Tim



I have reinstalled the lamp server. And the default dir is also var/www

But the problem is also exit.

---

### Post by SpankinPartier on 2008-09-22
Sorry I never got back here.  When I posted I had to go out to get a internet connection (was on holidays).

I did figure out what was my problem.  The first issue was an issue with Firefox 3.  Since I had no internet access FF3 would switch to off line mode.  So even even attempt to access the server.  I had to click on **File --> Work Offline** menu items to correct that.

But Konqueror wouldn't work either.  So I would have to turn off KNetworkManage from the 'system tray' and then things would work (I'm running Ubuntu with KDE - not full blown Kubuntu).

---

