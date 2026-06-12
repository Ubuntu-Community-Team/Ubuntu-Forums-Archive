---
title: "Apache2 random HTTPS drops"
date: 2011-09-01
forum: Server Platforms
---

### Post by YorickErnst on 2011-09-01
I installed Ubuntu 10.04.03 with apache2.2.14 for use as a reverse proxy.

Everything works ok except for the https connections. Most of the time it is ok, but sometimes he just stops loading the page at random. So some text and images are loaded but the rest of the page doesn't appear.

The virtualhost configuration is the same as I have on an other ubuntu machine (8.04 i believe with apache2.2.11)
The certificates are the same, ...

in the apache log all I can find is the following:

[Thu Sep 01 16:15:22 2011] [debug] ssl_engine_io.c(1920): OpenSSL: I/O error, 5 bytes expected to read on BIO#7f38f320c700 [mem: 7f38f32156e0]
[Thu Sep 01 16:15:22 2011] [debug] ssl_engine_io.c(1920): OpenSSL: I/O error, 5 bytes expected to read on BIO#7f38f320c700 [mem: 7f38f32156e0]
[Thu Sep 01 16:15:22 2011] [debug] ssl_engine_io.c(1920): OpenSSL: I/O error, 5 bytes expected to read on BIO#7f38f320c700 [mem: 7f38f32156e0]
[Thu Sep 01 16:15:23 2011] [debug] ssl_engine_io.c(1920): OpenSSL: I/O error, 5 bytes expected to read on BIO#7f38f320c700 [mem: 7f38f32156e0]
[Thu Sep 01 16:15:23 2011] [debug] ssl_engine_io.c(1920): OpenSSL: I/O error, 5 bytes expected to read on BIO#7f38f320c700 [mem: 7f38f32156e0]
[Thu Sep 01 16:15:23 2011] [error] [client 10.0.0.88] (20014)Internal error: proxy: error reading response
[Thu Sep 01 16:15:23 2011] [debug] ssl_engine_io.c(1920): OpenSSL: I/O error, 5 bytes expected to read on BIO#7f38f320b090 [mem: 7f38f3212f10]


only this line stops the page from loading:
[Thu Sep 01 16:15:23 2011] [error] [client 10.0.0.88] (20014)Internal error: proxy: error reading response

The other errors don't really seem to do anything.

What could cause this? I've been searching for 3 days.

---

