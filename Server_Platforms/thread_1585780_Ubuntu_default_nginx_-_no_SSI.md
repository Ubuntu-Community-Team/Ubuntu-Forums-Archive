---
title: "Ubuntu default nginx - no SSI?"
date: 2010-10-01
forum: Server Platforms
---

### Post by Kurtosis on 2010-10-01
I'm using Ubuntu 10.04 along with nginx 0.8.52 from the [Nginx PPA]("http://ppa.launchpad.net/nginx/stable/ubuntu").  Server Side Includes like below aren't working.  

The output from 'nginx -V' appears to show it was compiled without the SSI module:

> kurtosis@kurtosis-desktop:~/bin/nginx$ nginx -V >> test.txt
nginx version: nginx/0.8.52
TLS SNI support enabled
configure arguments: --conf-path=/etc/nginx/nginx.conf --error-log-path=/var/log/nginx/error.log --http-client-body-temp-path=/var/lib/nginx/body --http-fastcgi-temp-path=/var/lib/nginx/fastcgi --http-log-path=/var/log/nginx/access.log --http-proxy-temp-path=/var/lib/nginx/proxy --http-scgi-temp-path=/var/lib/nginx/scgi --http-uwsgi-temp-path=/var/lib/nginx/uwsgi --lock-path=/var/lock/nginx.lock --pid-path=/var/run/nginx.pid --with-debug --with-http_dav_module --with-http_flv_module --with-http_geoip_module --with-http_gzip_static_module --with-http_image_filter_module --with-http_realip_module --with-http_stub_status_module --with-http_ssl_module --with-http_sub_module --with-http_xslt_module --with-ipv6 --with-sha1=/usr/include/openssl --with-md5=/usr/include/openssl --with-mail --with-mail_ssl_module --add-module=/build/buildd/nginx-0.8.52/modules/nginx-upstream-fair


 but I just want to confirm before I go about removing it and compiling my own.  Anyone know for sure?  (also that IO redirect apparently doesn't work in this case...)

The SSI line I've tried to use is a basic include footer (only html files involved, no scripting languages or web frameworks of any kind):

```
<!--#include virtual="footer.html" -->
```

---

### Post by a9k3d on 2010-10-02
I think you'll have to compile with that feature on. 

It's been a long time since I've needed a SSI with all the templating add-ons out there for php, rails etc. I suspect SSI considered old-school in the age of AJAX and Web 2.0.

---

### Post by Kurtosis on 2010-10-02
It is, I just need it to rearrange some static HTML pages into headers and footers and the like, as a stopgap until I can port the site over to a cms.

After a little digging, it seems nginx includes SSI by default, unless you compile with the [--without-http_ssi_module]("http://wiki.nginx.org/NginxInstallOptions") directive.

But it's not working for me, even with ['ssi on;']("http://wiki.nginx.org/HttpSsiModule") added to nginx.conf.  Any suggestions appreciated.

---

### Post by openfly on 2011-11-02
I am seeing this behavior as well.

SSI does appear to be broken on oneiric nginx packages.

Tried with nginx-full and nginx-extras.

Not sure what the issue is.

---

### Post by cc young on 2012-08-26
My experience as well.  Will report as bug.

---

