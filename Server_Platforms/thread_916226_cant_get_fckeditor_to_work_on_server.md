---
title: "cant get fckeditor to work on server"
date: 2008-09-10
forum: Server Platforms
---

### Post by kustomjs on 2008-09-10
hey guys
I just got done installing fckeditor and its not working what else do I need to do to get it working?

---

### Post by cariboo on 2008-09-11
Check out /usr/share/doc/fckeditor/README.Debian

Jim

---

### Post by kustomjs on 2008-09-11
ok where do I put this at?

fckeditor for Debian
------------------------

The package installs all the files needed by tinymce under
`/usr/share/fckeditor'.

It's pretty easy to use fckeditor within your webapp, you just have alias that
directory to "fckeditor":

    Alias /fckeditor/ /usr/share/fckeditor/
    <Directory "/usr/share/fckeditor/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order allow,deny
    </Directory>

 -- Frank Habermann <lordlamer@lordlamer.de>  Fri, 02 Nov 2007 21:30:01 +0200

---

### Post by kustomjs on 2008-09-11
anybody?

---

