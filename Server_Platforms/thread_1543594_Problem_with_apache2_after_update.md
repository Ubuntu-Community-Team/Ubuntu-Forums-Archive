---
title: "Problem with apache2 after update"
date: 2010-08-01
forum: Server Platforms
---

### Post by cazz on 2010-08-01
Hi
I have problem with my apache2 server after I have update my server

I have problem to make apache to find some file and directory.

Some directory is ok but some I have problem with connect with my web browser. I get a "500 Internal Server Error" and in the log I can see

```
[Sun Aug 01 16:12:45 2010] [error] [client x.x.x.x] script '/media/raid/user/testing/listan.php' not found or unable to stat, referer: http://server.se/testing/
```


But the file is there and it have right to use it

and in the httpd.conf look ok, I mean the other site work nice

```
alias /testing /media/raid/user/testing
<Directory "/media/raid/user/testing">
       Options Indexes FollowSymLinks MultiViews ExecCGI
       AllowOverride All
       Order allow,deny
       Allow from all
       IndexOptions +FancyIndexing +FoldersFirst
</Directory>
```

---

### Post by ruffEdgz on 2010-08-02
Because I don't know your setup, my questions might sound a bit weird but bare with me.

So the actual location for the file 'listan.php' is under /media/raid/user/testing? Are there any other files under the directory that you can get to? You say 'the file is there and it have right to use it' so the owner and group are www-data or something else? Just curious but what does this show:
```

updatedb
locate listan.php

```

Just want to get a good idea of what your setup is. Thanks for answering my questions.

---

