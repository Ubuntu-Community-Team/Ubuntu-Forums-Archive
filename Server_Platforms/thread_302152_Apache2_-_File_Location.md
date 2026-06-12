---
title: "Apache2 - File Location"
date: 2006-11-18
forum: Server Platforms
---

### Post by gRoberts on 2006-11-18
Hi all,

I'm trying to setup my edgy release so I can continue to create and test web applications.

I downloaded Apache2 2.2.3 and installed to /usr/local/apache2

after running

```
sudo /usr/local/apache2/bin/apachectl start
```

It reported that it was listening to 127.0.1.1:80 rather then 127.0.0.1:80.

So I went to both addresses and I got the It Works! text that Apache put in.

I then went to /usr/local/apache2/htdocs and changed index.html and only 127.0.1.1 showed the change.

This lead me to believe there is more then one installation on the system.

So I searched the computer for anything with apache in, and nothing apart from the known files that I created when installing Apache.

search results:
```

gavin@EYCD:~$ sudo find / -name "*apache*"
/home/gavin/Desktop/httpd-2.2.3/support/win32/apache_header.bmp
/home/gavin/Desktop/httpd-2.2.3/support/apachectl.in
/home/gavin/Desktop/httpd-2.2.3/support/apachectl
/home/gavin/Desktop/httpd-2.2.3/docs/man/apachectl.8
/home/gavin/Desktop/httpd-2.2.3/docs/icons/apache_pb2.png
/home/gavin/Desktop/httpd-2.2.3/docs/icons/apache_pb.gif
/home/gavin/Desktop/httpd-2.2.3/docs/icons/apache_pb2.gif
/home/gavin/Desktop/httpd-2.2.3/docs/icons/apache_pb.png
/home/gavin/Desktop/httpd-2.2.3/docs/icons/apache_pb2_ani.gif
/home/gavin/Desktop/httpd-2.2.3/docs/manual/images/apache_header.gif
/home/gavin/Desktop/httpd-2.2.3/docs/manual/programs/apachectl.html.ko.euc-kr
/home/gavin/Desktop/httpd-2.2.3/docs/manual/programs/apachectl.html.en
/home/gavin/Desktop/httpd-2.2.3/docs/manual/programs/apachectl.html
/home/gavin/Desktop/httpd-2.2.3/docs/docroot/apache_pb22_ani.gif
/home/gavin/Desktop/httpd-2.2.3/docs/docroot/apache_pb.gif
/home/gavin/Desktop/httpd-2.2.3/docs/docroot/apache_pb.png
/home/gavin/Desktop/httpd-2.2.3/docs/docroot/apache_pb22.gif
/home/gavin/Desktop/httpd-2.2.3/docs/docroot/apache_pb22.png
/home/gavin/Desktop/httpd-2.2.3/build/win32/apache.ico
/home/gavin/Desktop/httpd-2.2.3/apachenw.mcp.zip
/home/gavin/Desktop/httpd-2.2.3/os/netware/apache.xdc
/usr/local/apache2
/usr/local/apache2/bin/apachectl
/usr/local/apache2/htdocs/apache_pb22_ani.gif
/usr/local/apache2/htdocs/apache_pb.gif
/usr/local/apache2/htdocs/apache_pb.png
/usr/local/apache2/htdocs/apache_pb22.gif
/usr/local/apache2/htdocs/apache_pb22.png
/usr/local/apache2/icons/apache_pb2_ani.gif
/usr/local/apache2/icons/apache_pb2.gif
/usr/local/apache2/icons/apache_pb2.png
/usr/local/apache2/icons/apache_pb.gif
/usr/local/apache2/icons/apache_pb.png
/usr/local/apache2/man/man8/apachectl.8
/usr/local/apache2/manual/images/apache_header.gif
/usr/local/apache2/manual/programs/apachectl.html.ko.euc-kr
/usr/local/apache2/manual/programs/apachectl.html
/usr/local/apache2/manual/programs/apachectl.html.en
/usr/share/gnome/help/desktopguide/sample/ports.conf_changeportnumberapache
/usr/share/gnome/help/desktopguide/sample/testphp.php_installphpapache
/usr/share/icons/gnome/24x24/apps/apacheconf.png
/usr/share/icons/gnome/48x48/apps/apacheconf.png
/usr/share/vim/vim70/syntax/apachestyle.vim
/usr/share/vim/vim70/syntax/apache.vim

```

Can anyone see why this is doing this and where the hell it could be coming from as I have no idea where to store my files.

I'd also prefere that I only had one instance of Apache running, unless some how the other IP is on the same instance and is looking at a cached file?!

Thanks in advance.

Gavin

---

### Post by PilotJLR on 2006-11-18
How did you install apache??

If you use apt-get (a very good idea), then the only default location for html files would be /var/www/

If you did install two instances (from a tarball or something else), then make sure only 1 apache2 init script is placed in /etc/init.d/, so that the computer doesn't run 2 instances at boot.

---

### Post by garybrlow on 2006-11-18
well (XK)ubuntu has two local loopback ip addresses built in namely the standard 127.0.0.1 that resolves to localhost and 127.0.1.1 that resolves to the distro name (xk)ubuntu(whatever you're using) by default. Both ip addresses should serve the same index page for the default site, they coexist.

Apache 2.2.3 is not an offical package of debian and ubuntu yet. The Apache version in the repositories is still 2.0.x and configuration files and directory structure  are very much different from the standard apache installation downloaded for the offical site [http://httpd.apache.org](http://httpd.apache.org). Even if you install both, both Apaches can not run together unless you specifially set the other Apache to listen on another port aside from 80 since they can not use the same port together. Also default index html for the 1.3.x and 2.0.x series sports a default message and the Apache logo while the 2.2.x series only has "It works!!!" displayed.

Unless you had vitrual host on and other module issues not included during compilation. 127.0.0.1, 127.0.1.1, and your own ip should show the same index page. 

Here are a few things you should check:
1) Check if your browser is a proxy server, if it is make sure 127.0.0.1, 127.0.1.1, and your ip addresss are set to use direct connection and not the proxy.

2) Check if you installed Apache from the repositories before you installed the compiled version. I you did, uninstall it using synaptic and choose complete removal and restart linux to make sure it is removed from memory. Since you're 2.2.3 the older version should be removed. Note: Since you are compiling make sure to inlcude all neede modules upon compiling you can not use the apache modules in repositories (refer to the installation and compiling section in apache manual and the php install text for dynamic so modules)

3) You can start and stop apache and see if it makes a difference.


Alhough your locate results do not show another installation of Apache just double check anyways.

:)

---

