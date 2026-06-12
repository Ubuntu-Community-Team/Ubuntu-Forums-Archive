---
title: "Lighty and file upload"
date: 2008-01-29
forum: Server Platforms
---

### Post by _sami_ on 2008-01-29
Hi 

I have a native installation of lighttpd (1.4.18 ) on ubuntu 7.10 and runing php5 through cgi. But i have trouble uploading files through forms. I have tryed to increase the limit for post-data in the configuration file, and also to specify the upload-path to /var/tmp.

Still not working and dont know what to do. Any ideas? :)

---

### Post by tlcoffee on 2008-01-30
try adding one of the following to your lighttpd.conf for lighttpd 1.4.x

server.network-backend = "write"

I can verify that the follow works for 1.5.x

server.network-backend = "writev"
server.network-backend = "linux-sendfile"

---

