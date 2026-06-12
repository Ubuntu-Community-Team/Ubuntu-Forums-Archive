---
title: "ftp://servername to http://ftp.servername"
date: 2011-02-26
forum: Server Platforms
---

### Post by joshruehlig on 2011-02-26
I noticed some ftp directories are located at [http://ftp.servername](http://ftp.servername) domains instead of [ftp://servername](ftp://servername) domains. I am currently running vsftp and have a [ftp://servername](ftp://servername) type website but would like to make [http://ftp.server](http://ftp.server) name available so clients using browsers without ftp:// capabilities (such as those on android) can view my ftp without downloading an application.

Thanks

---

### Post by SeijiSensei on 2011-02-26
Usually an [http://ftp.example.com/](http://ftp.example.com/) URL simply means there's a web server running on the same machine and offering the same files via HTTP.  Just install a webserver like Apache and point it at the same directory as the one containing your FTP files.

---

### Post by joshruehlig on 2011-04-29
> **SeijiSensei said:**
> Usually an [http://ftp.example.com/](http://ftp.example.com/) URL simply means there's a web server running on the same machine and offering the same files via HTTP.  Just install a webserver like Apache and point it at the same directory as the one containing your FTP files.

Perfect thanks! didn't know apache just showed your files if you don't have a index.html/php

I just move my ftp anon root over to a directory in my /var/www, it works well for everyone including mobile browsers =]

---

### Post by SlugSlug on 2011-05-10
you don't need to move ftp folder you can sym link
 
sudo ln -s /path/to/ftp /var/www

---

### Post by Lars Noodén on 2011-05-10
> **joshruehlig said:**
> Perfect thanks! didn't know apache just showed your files if you don't have a index.html/php



You can set the [Options Indexes](http://httpd.apache.org/docs/current/mod/core.html#options) directive to have Apache show the listing of the directory.

---

### Post by SeijiSensei on 2011-05-11
Apache also offers a variety of [options]("http://httpd.apache.org/docs/current/mod/mod_autoindex.html") that control how directory indexes are displayed.

---

