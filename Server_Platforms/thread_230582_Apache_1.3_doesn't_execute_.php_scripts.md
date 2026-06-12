---
title: "Apache 1.3 doesn't execute .php scripts"
date: 2006-08-06
forum: Server Platforms
---

### Post by Ramses de Norre on 2006-08-06
I'm running apache 1.3 and I have a problem with php files, firefox asks to download them instead of executing them.
I know this is a common problem but all solutions are for apache2 and I just can't get it to work (I'm pretty new in this things).

I installed libapache-mod-php4 and php4-common and restarted apache but it wont work..

The file is /var/www/status/index.php and I made it executable.

I hope someone knows how to solve it =)

---

### Post by anthonysales on 2006-08-06
go check your httpd.conf and see if your php modules are loaded. Look for the line that says:

LoadModule php5_module libexec/libphp5.so

If its not there, search for the LoadModule section and add it there.
also check if your apache is parsing the .php extesions as PHP. look for these lines: 

AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

if they're not there, just add them. if it still doesn't work, just compile apache from source. hehehe...pm me if you have any trouble compiling through source. i'll be glad to help! :D

---

### Post by anthonysales on 2006-08-06
oops...my bad! didn't notice that you were using php4. just change
LoadModule php5_module libexec/libphp5.so to 
LoadModule php4_module libexec/libphp4.so

---

### Post by Kurt` on 2006-08-06
My friend had a similar problem on one of his machines.

I installed [LiveHTTPHeaders](http://livehttpheaders.mozdev.org/) in firefox, and checked the actual raw request. It was sending the .php file as text/plain (he forgot to /etc/init.d/apache reload :p).

For some reason, we also had to clear his browser cache.

---

### Post by jms1989 on 2006-08-07
My system has those codes already inserted, but nutin'

Even when I try to restart Apache2, it fails. Any advice, I'm using the lated version.

---

### Post by Ramses de Norre on 2006-08-07
That worked =)
I inserted those three lines and now the script works (after configuring it a bit).

And to jms1989: this is all for apache 1.3, I think apache2 uses another config file and not httpd.conf.

---

