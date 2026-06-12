---
title: "apache shtml problem"
date: 2007-04-06
forum: Server Platforms
---

### Post by computx on 2007-04-06
I am converting from a Gentoo LAMP server to an Ubuntu one.

I have  Apache, PHP and Mysql installed fine but I am running into a problems with server side includes.

I use an index.shtml file and not an index.html due to use of includes.

Apache will not display index.shtml as the default webpage and when I load it explicitly The includes are not working.   
In /etc/apache2/apache2.conf I have this 
# To use server-parsed HTML files
#
<FilesMatch "\.shtml(\..+)?$">
    SetOutputFilter INCLUDES
</FilesMatch>

and /etc/apache2/mods-enabled has include.load

What am I missing here? Gentoo's apache configuration is much different from the ubuntu one so I am like a newbie again. any help appreciated.

---

### Post by MJN on 2007-04-06
A couple of things:

1) Make sure **index.shtml** is listed in the **DirectoryIndex** directive in /etc/apache2/apache2.conf (note the order is important).

2) In the relevent **<Directory> **directive in /etc/apache2/sites-available/default covering your web root makes sure **Includes** is specified in **Options**.

If you want it in more detail just shout.

Mathew

---

