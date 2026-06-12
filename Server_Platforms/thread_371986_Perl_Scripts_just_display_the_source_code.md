---
title: "Perl Scripts just display the source code"
date: 2007-02-27
forum: Server Platforms
---

### Post by rocktorrentz on 2007-02-27
I am trying to install cgiproxy on my Ubuntu 6.10 LAMP Server. However even after making a symbolic link to /usr/lib/cgi-bin called cgi-bin in /var/www and giving both the folder and the nph-cgiproxy.cgi 755 permissions, I still only get the source code. Is there something else I need to install for this to work?

Thanks
rocktorrentz

edit: I also changed the first line of the script to #!/usr/bin/perl

---

### Post by SuSUntu on 2007-02-27
Sounds like you don't have your httpd.conf file set up properly to handle 'cgi' or 'pl' files, thus instead of executing the files, the server is simply displaying them as text files.

What comes to mind first then is that httpd.conf is missing:

AddHandler cgi-script cgi pl

However, because the httpd.conf may need this as well as a few other tweaks to get it working, check out:

[http://httpd.apache.org/docs/1.3/howto/cgi.html.en](http://httpd.apache.org/docs/1.3/howto/cgi.html.en)

If you are using a later version of Apache than 1.3 (likely), the same docs are available for each version. You can substitute the version directly in the URL above or go here to choose the appropriate docs:

[http://httpd.apache.org/docs/](http://httpd.apache.org/docs/)

---

