---
title: "Apache SSL setup"
date: 2010-12-07
forum: Security
---

### Post by eriksays on 2010-12-07
I'm having issues geting SSL running with apache2.

I've gone through a number of helpful articles:

[https://help.ubuntu.com/8.04/serverguide/C/httpd.html]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html")
[https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html]("https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html")

[LIST]
[*]enabled ssl (sudo a2ensmod ssl)
[*]generated ssl certs
[*]generated a self-signed certificate (this is for testing)
[*]setup my default-ssl conf file
[/LIST]

```

NameVirtualHost my.i.p.address 
<VirtualHost my.i.p.address:443>
 DocumentRoot /var/www
 SSLEngine on
 #SSLOptions +StrictRequire
 SSLCertificateFile /etc/ssl/certs/server.crt
 SSLCertificateKeyFile /etc/ssl/private/server.key
 ServerAdmin you@example.com
 ErrorLog /var/log/ssl_error_log
 TransferLog /var/log/ssl_access_log

</VirtualHost>

```

I generated a symbolic link in sites-enabled (000-default-ssl) to my default-ssl conf file in sites-available

I'm getting the following error in Firefox: ssl_error_rx_record_too_long
My apache error log has a line: Invalid method in request \x16\x03

port 443 is open and listening because I can hit [http://my.IP.Address:443](http://my.IP.Address:443) without errors.

So it looks like my server is listening to port 443, but it's serving up content unsecured (HTTP). 

Any suggestions on where to look next?

---

### Post by bodhi.zazen on 2010-12-07
[http://ubuntuforums.org/showthread.php?t=806884](http://ubuntuforums.org/showthread.php?t=806884)

[http://www.noah.org/wiki/Apache2_Invalid_method_in_request_%5Cx16%5Cx03%5Cx01](http://www.noah.org/wiki/Apache2_Invalid_method_in_request_%5Cx16%5Cx03%5Cx01)

---

