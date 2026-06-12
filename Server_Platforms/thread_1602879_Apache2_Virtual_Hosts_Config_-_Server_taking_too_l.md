---
title: "Apache2 Virtual Hosts Config - Server taking too long to respond error"
date: 2010-10-22
forum: Server Platforms
---

### Post by johnrusso on 2010-10-22
I have configured apache2 on Ubuntu for NameVirtual hosts.  

The default server works fine - [couch.klouddb.com]("http://www.klouddb.com").

The second virtual host does not - [www.taintedtitle.com]("http://www.taintedtitle.com").

DNS works for both and they both point to the same IP address.

I can get the index.html file for the virtual host by using the default address as follows:

            [http://couch.klouddb.com/taintedtitle/index.html]("http://www.klouddb.com/taintedtitle/index.html")

When I use [www.taintedtitle.com]("http://www.taintedtitle.com"), the browser times out and there are no entries in the error or access logs specific to that virtual host - it is empty.

I am stumped.  Ideas?

John

---

### Post by Barriehie on 2010-10-22
This [url](http://httpd.apache.org/docs/2.0/urlmapping.html#redirect) might prove useful in your situation.

HTH

---

### Post by johnrusso on 2010-10-22
Not sure that solves the problem, as that would presume the server is answering and could then redirect.

There is no entry in either the access or error log, so I can only assume that the server never sees nor handles the request - thus would not be able to redirect.

John

---

### Post by johnrusso on 2010-10-22
I have added only one file to the default Apache2 installation, "/etc/apache2/sites-available/taintedtitle.com" and ran "a2ensite taintedtitle.com" and checked that the link is there.

Contents of "taintedtitle.com"

-------------------------------------------------------
ServerName [www.taintedtitle.com](www.taintedtitle.com)
ServerAlias taintedtitle.com *.taintedtitle.com

DocumentRoot /var/www/taintedtitle

<Directory /var/www/taintedtitle/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride all
        Order allow,deny
        allow from all
</Directory>

CustomLog /var/log/apache2/taintedtitle.com-access.log combined
ErrorLog /var/log/apache2/taintedtitle.com-error.log
LogLevel debug
</VirtualHost>
------------------------------------------------------------


Output from  "apache2ctl -S"

-------------------------------------------------------------
VirtualHost configuration:
wildcard NameVirtualHosts and _default_ servers:
*:80                   is a NameVirtualHost
         default server couchdb.klouddb.com (/etc/apache2/sites-enabled/000-default:1)
         port 80 namevhost couchdb.klouddb.com (/etc/apache2/sites-enabled/000-default:1)
         port 80 namevhost [www.taintedtitle.com](www.taintedtitle.com) (/etc/apache2/sites-enabled/taintedtitle.com:1)
Syntax OK
--------------------------------------------------------------

Log files:

-------------------------------------------------------------
drwxr-x---  2 root adm  4096 2010-10-21 16:58 .
drwxr-xr-x 12 root root 4096 2010-10-22 06:26 ..
-rw-r-----  1 root adm  2440 2010-10-22 09:47 access.log
-rw-r-----  1 root adm  1465 2010-10-22 10:08 error.log
-rw-r--r--  1 root root    0 2010-10-21 16:02 other_vhosts_access.log
-rw-r--r--  1 root root    0 2010-10-21 16:58 taintedtitle.com-access.log
-rw-r--r--  1 root root    0 2010-10-21 16:58 taintedtitle.com-error.log
-------------------------------------------------------------

John

----------------------------------------------------------------

---

### Post by johnrusso on 2010-10-22
PROBLEM SOLVED!  I had mistyped the DNS address in the Nameserver.

But I learned to use nc to troubleshoot and here are a few sample commands that were helpful.

1st, Test the virtualhost on the local machine using the loopback address.  Test all the virtual hosts by changing the "Host: " parameter.

Type:
nc 127.0.0.1 80
GET /index.html HTTP/1.1
Host: [www.xyz.com](www.xyz.com)

Hit return at the blank line and you should get something like this with the contents of your index.html file at the end.

-----------------------------------
HTTP/1.1 200 OK
Date: Fri, 22 Oct 2010 23:40:00 GMT
Server: Apache/2.2.12 (Ubuntu)
Last-Modified: Thu, 21 Oct 2010 23:59:47 GMT
ETag: "1a026c-c4-4932952240e03"
Accept-Ranges: bytes
Content-Length: 196
Vary: Accept-Encoding
Content-Type: text/html
X-Pad: avoid browser bug

<html><body><h1>It works!</h1>
<p>This is the default web page for this server - www.xyz.com.</p>
<p>The web server software is running but no content has been added, yet.</p>
</body></html>
--------------------------------------

Next use the IP address, then the FQDN, and you should get the same results.

nc 216.38.135.101 80

then 

nc [www.xyz.com](www.xyz.com) 80

Good luck.

John

---

