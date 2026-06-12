---
title: "Please help me to setup SSL on my Ubuntu"
date: 2011-05-03
forum: Server Platforms
---

### Post by s.a.patil on 2011-05-03
Hi community members, I'm running Ubuntu 10.4.2 and I have setup SSL on my computer by following this guide, now I have this problem.

When I issue this command: sudo /etc/init.d/apache2 restart

I get this error

 * Restarting web server apache2
( 98 )Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

But some time Apache successfully restart.

Please help, as I have wasted lot of time Googleing, thanks a lot in advance

The guide I followed:

Setting up SSL on Ubuntu

At first enable SSL: sudo a2enmod ssl

Now force-reload Apache: sudo /etc/init.d/apache2 force-reload

Now, to encrypt your site, create the server encryption keys:

cd /etc/apache2

sudo openssl genrsa -des3 -out server.key 1024

Now use this set of keys to create a certificate request:

sudo openssl req -new -key server.key -out server.csr

When asked to input data, use your imagination to create something appropriate.  Be sure to write down your passphrase.

Use this request to create your self-signed certificate:

sudo openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt

Install the key and certificate:

sudo cp server.crt /etc/ssl/certs/

sudo cp server.key /etc/ssl/private/

Open the &#8220;defaults&#8221; file for editing:

cd /etc/apache2/sites-available
gksudo gedit default-ssl

This file is basically set up but you will want to uncomment  the SSLOptions line and also change the SSLCertificate lines to reflect the location and name of your new information.

SSLEngine on
SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
SSLCertificateFile /etc/ssl/certs/server.crt
SSLCertificateKeyFile /etc/ssl/private/server.key

The port 443 is enabled when you use SSL so that is ready to go.

Enable the default SSL site:

sudo a2ensite default-ssl

If you do not enable the default-ssl you will get this error:
&#8220;ssl_error_rx_record_too_long apache&#8221;

Restart Apache.

sudo /etc/init.d/apache2 restart

That should do it.

---

### Post by s.a.patil on 2011-05-04
Hi members, since I found nobody to help I have decided to take this approach, to drop Ubuntu 10.4.2 altogether and adopt Ubuntu 11.04, will get back to this thread when I'm done.

---

