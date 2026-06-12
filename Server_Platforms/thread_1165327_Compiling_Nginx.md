---
title: "Compiling Nginx"
date: 2009-05-20
forum: Server Platforms
---

### Post by CP1256 on 2009-05-20
Hello everyone,

I've been trying to compile the latest version of Nginx, but everytime I fail.
These are the compile options I use:

> 
NO_WARNING_CHECKS=yes ./configure --conf-path=/etc/nginx/nginx.conf --error-log-path=/var/log/nginx/error.log --pid-path=/var/run/nginx.pid --lock-path=/var/lock/nginx.lock --http-log-path=/var/log/nginx/access.log --with-http_dav_module --http-client-body-temp-path=/var/lib/nginx/body --with-http_ssl_module --http-proxy-temp-path=/var/lib/nginx/proxy --with-http_stub_status_module --http-fastcgi-temp-path=/var/lib/nginx/fastcgi --with-debug --with-http_flv_module 


I get no .deb package, also I get no errors when running make, although I do get errors when trying to compile it on Debian Lenny, then I get 'Wno-unused-parameter -Wno-unused-function -Wunused-variable -Wunused-value -Werror -gWno-unused-parameter -Wno-unused-function -Wunused-variable -Wunused-value -Werror -g'.

Does anyone know how to solve this? I've already tried [this]("http://ubuntuforums.org/showthread.php?t=986408&highlight=compile+nginx"), but with no success.

---

### Post by CP1256 on 2009-05-20
Nevermind, I solved it. Use checkinstall.

---

### Post by mothes on 2009-06-29
You can find article how to install and compile nginx here 
[http://www.linuxspace.org/archives/1576]("http://www.linuxspace.org/archives/1576")

---

