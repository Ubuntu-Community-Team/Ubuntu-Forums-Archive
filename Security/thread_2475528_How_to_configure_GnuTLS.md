---
title: "How to configure GnuTLS?"
date: 2022-05-30
forum: Security
---

### Post by porton2 on 2022-05-30
My self-compiled program that uses GnuTLS outputs

./httpfs2-ssl: main: connecting to conference.portonvictor.org port 443.
gnutls[3]: ASSERT: ../../../lib/x509/dn.c[_gnutls_x509_compare_raw_dn]:1025
./httpfs2-ssl: SSL init: loaded 127 CA certificate(s).
./httpfs2-ssl: main: initializing SSL socket.
./httpfs2-ssl: conference.portonvictor.org:443 - ./httpfs2-ssl: main: SSL connection failed: -8 A packet with illegal or unsupported version was received..

Apparently the server conference.portonvictor.org that I used for testing does not support some feature of httpfs2-ssl.

So, for it to work, I need to reconfigure GnuTLS.

But I found no any configuration of GnuTLS in Ubuntu!

Please give me an example "sane" (not too loose, not to secure trading off important features and compatibility) GnuTLS config (and where to put it in /etc).

---

### Post by TheFu on 2022-05-31
I thought gnutls was a library, not a program. [https://www.gnutls.org/manual/html_node/How-to-use-GnuTLS-in-applications.html](https://www.gnutls.org/manual/html_node/How-to-use-GnuTLS-in-applications.html) That means the configuration would be handled by your program with the options passed into the library calls as needed. gnutls_init() The program dev should handle that.  Obviously, the client and server need to know which options work for this connection. 

> GnuTLS is a secure communications _**library**_ implementing the SSL, TLS and DTLS protocols and technologies around them. It provides a simple C language application programming interface (API) to access the secure communications protocols as well as APIs to parse and write X.509, PKCS #12, and other required structures.

There isn't going to be anything Ubuntu specific.   [https://help.ubuntu.com/community/GnuTLS](https://help.ubuntu.com/community/GnuTLS)  Nothing specific to Ubuntu in there.

---

