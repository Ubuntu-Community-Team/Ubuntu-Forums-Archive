---
title: "Samba: Is there a way to &quot;check out&quot; files"
date: 2009-02-17
forum: Server Platforms
---

### Post by 47_MasoN_47 on 2009-02-17
Hello,

At my place of employment I am running a file server on Ubuntu 8.04 using Samba.  Most of us work from inside our LAN but there is one user that works from home (he is several hours away) via VPN.  Our Internet connection sucks so he downloads the files from the server in the morning and uploads them later when he's through working.  Is there some way that he could "check out" the file, like when you check out a book from the library, so that when another user opens it it will be read only or locked somehow so that they can't edit it until the offsite user is through?  Today we had a conflict because our offsite user overwrote the data that one of the inside users had worked on when he synced.

Thanks

---

### Post by Titan8990 on 2009-02-17
It sounds like what you need is a WebDAV server. It functions in the ways that you mention. You can download/upload files but if a user currently has the file open another user will not be able to modify it until it is unlocked.

[http://www.digital-arcanist.com/sanctum/article.php?story=20070427101250622](http://www.digital-arcanist.com/sanctum/article.php?story=20070427101250622)


You can even mount WebDAV network places in Windows. In addition to this, transfering files over HTTP is much faster than SMB/CIFS.

---

### Post by 47_MasoN_47 on 2009-02-17
Thanks for the suggestion!  I'll definitely check that out.  It'll probably take a few days to a week of testing and whatnot before I can post back again with results, but who knows maybe things will slow down a bit and I'll get to play with it sooner than I think.

---

### Post by HermanAB on 2009-02-17
Maybe you need to look at a document management system such as OpenDocMan:
[http://www.opendocman.com/](http://www.opendocman.com/)

Cheers,

Herman

---

