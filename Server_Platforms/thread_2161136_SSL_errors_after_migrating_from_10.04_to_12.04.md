---
title: "SSL errors after migrating from 10.04 to 12.04"
date: 2013-07-09
forum: Server Platforms
---

### Post by kevpatts on 2013-07-09
Hello,

I've upgraded my web server from Ubuntu 10.04 to 12.04 recently and have no problems for 99.9% or sites connecting in. However there is one merchant who is now getting timeouts when truing to connect to us. They are using a .NET framework 4 environment in IIS7 on Windows Server 2008.

The can connect to our 10.04 config but just timeout when we switch to the equivelant 12.04 config.

I've enabled debug logging for one of their incoming requests and we see a timeout mid SSL handshake.
```
[Tue Jul 09 16:13:53 2013] [info] [client 184.73.155.83] Connection to child 66 established (server testpayments.XXXXXX.com:443)
[Tue Jul 09 16:13:53 2013] [info] Seeding PRNG with 656 bytes of entropy
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_kernel.c(1866): OpenSSL: Handshake: start
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_kernel.c(1874): OpenSSL: Loop: before/accept initialization
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_io.c(1897): OpenSSL: read 11/11 bytes from BIO#7fad7c000da0 [mem: 7fad80016720] (BIO dump follows)
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_io.c(1830): +-------------------------------------------------------------------------+
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_io.c(1869): | 0000: 16 03 01 00 7f 01 00 00-7b 03 01                 ........{..      |
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_io.c(1875): +-------------------------------------------------------------------------+
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_io.c(1897): OpenSSL: read 121/121 bytes from BIO#7fad7c000da0 [mem: 7fad8001672e] (BIO dump follows)
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_io.c(1830): +-------------------------------------------------------------------------+
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_io.c(1869): | 0000: 51 dc 28 9f 00 98 ff c7-3e 1e 07 9a ae 23 71 2e  Q.(.....>....#q. |
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_io.c(1869): | 0010: 88 bf 8f 89 75 d6 b8 33-13 6d c5 17 b4 45 c9 64  ....u..3.m...E.d |
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_io.c(1869): | 0020: 00 00 18 00 2f 00 35 00-05 00 0a c0 09 c0 0a c0  ..../.5......... |
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_io.c(1869): | 0030: 13 c0 14 00 32 00 38 00-13 00 04 01 00 00 3a 00  ....2.8.......:. |
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_io.c(1869): | 0040: 00 00 24 00 22 00 00 1f-74 65 73 74 70 61 79 6d  ..$."...testpaym |
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_io.c(1869): | 0050: 65 6e 74 73 2e 70 61 67-6f 74 65 63 68 6e 6f 6c  ents.YYYYYYYYYYY |
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_io.c(1869): | 0060: 6f 67 79 2e 63 6f 6d 00-0a 00 08 00 06 00 17 00  YYY.com......... |
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_io.c(1869): | 0070: 18 00 19 00 0b 00 02 01-                         ........         |
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_io.c(1873): | 0121 - <SPACES/NULS>
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_io.c(1875): +-------------------------------------------------------------------------+
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_kernel.c(1993): [client 184.73.155.83] No matching SSL virtual host for servername testpayments.YYYYYY.com found (using default/first virtual host)
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_kernel.c(1884): OpenSSL: Write: SSLv3 read client hello C
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_kernel.c(1874): OpenSSL: Loop: SSLv3 read client hello A
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_kernel.c(1874): OpenSSL: Loop: SSLv3 write server hello A
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_kernel.c(1874): OpenSSL: Loop: SSLv3 write certificate A
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_kernel.c(1874): OpenSSL: Loop: SSLv3 write server done A
[Tue Jul 09 16:13:53 2013] [debug] ssl_engine_kernel.c(1874): OpenSSL: Loop: SSLv3 flush data
[Tue Jul 09 16:14:14 2013] [info] [client 184.73.155.83] Request header read timeout
[Tue Jul 09 16:14:14 2013] [debug] ssl_engine_io.c(1908): OpenSSL: I/O error, 5 bytes expected to read on BIO#7fad7c000da0 [mem: 7fad80016723]
[Tue Jul 09 16:14:14 2013] [debug] ssl_engine_kernel.c(1903): OpenSSL: Exit: error in SSLv3 read client certificate A
[Tue Jul 09 16:14:14 2013] [debug] ssl_engine_kernel.c(1903): OpenSSL: Exit: error in SSLv3 read client certificate A
[Tue Jul 09 16:14:14 2013] [info] [client 184.73.155.83] (70007)The timeout specified has expired: SSL handshake interrupted by system [Hint: Stop button pressed in browser?!]
[Tue Jul 09 16:14:14 2013] [info] [client 184.73.155.83] Connection closed to child 66 with abortive shutdown (server testpayments.XXXXX.com:443)

```

I initially thought that this was caused by TLS fallback but enabling SSLInsecureRenegotiation in ssl.conf had no effect.

Any ideas?

---

