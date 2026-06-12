---
title: "Cannot Use Htaccess/HtPasswd Protection?"
date: 2009-05-03
forum: Server Platforms
---

### Post by GCoffee on 2009-05-03
PROBLEM SOLVED.

SEE BELOW

Hi,


Ive got ubuntu server running on a old pc we have, all is going fine, until i try to enable .htaccess protection on a web directory, so first i tried the webmin module, it didnt work so i thought, these things happen, i will just have to do it manually, so i went off and found a .htaccess generator on the web, filled it in, copied and pasted into the files, saved the files to the server, alas, no luck. so i used the default htpasswd program that comes with apache, this didnt work either.

I've checked that the htaccess file is pointing to the right .htpasswd file, ive checked everything writable, ive even reinstalled apache with no luck..

I cant figure out why it wont work.

Can anyone shed some light on the issue?

Thanks,
GC.

---

### Post by spiderbatdad on 2009-05-03
.htaccess files are really not intended for this purpose. I know that doesn't answer your question, but it is hard to answer w/out seeing your configuration file.
Access should be controlled in the configuration file on a per directory basis, using basic authentication for example.
[http://httpd.apache.org/docs/1.3/howto/auth.html](http://httpd.apache.org/docs/1.3/howto/auth.html)

---

### Post by GCoffee on 2009-05-03
Ok I solved it,

AllowOverideAll directive wasnt set right. I was looking in the wrong config file for it.

Thanks.

---

