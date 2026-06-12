---
title: "secure and encrypted http file browser?"
date: 2007-07-04
forum: Server Platforms
---

### Post by kudeta on 2007-07-04
Heya everybody.

I'm going to university in september and unfourtunately i've heard that they block most ports except 80 and occasionally block access to websites. I have a need to access files that are stored on a remote server i use to host files (for other people too) so that means i can't put an ftp server on that port right? i will try a portscan when i get to uni too see if i can put a secure ftpd somewhere.

Meanwhile, what i need is a way of securely (passwords) and with encryption, browsing through files stored on my server and being able to download them, sort of a web based file browser that supports encryption. 

Alternatively is it possible to just encrypt everything that apache shows on the net?. I have seen several web based file browsers but i can't work out how i would encrypt the transfers. Either way it needs to be able to stop the university admins seeing the files i am downloading. In case your wondering its nothing too exciting, just some of my mums work that i often help with on a technical side. It contains HIGHLY sensitive information about peoples personal lives and so i don't really want to take any chances.

Thanks for you thoughts,

KuDeTa

---

### Post by johannes on 2007-07-04
Perhaps you could create a ssh server and make it use some port accessible at the university? A quick google search for "java ssh client" turned up a couple of browser based clients. Ssh encrypts everything.

Just an idea though. I haven't attempted such a procedure myself.

---

### Post by darkog on 2007-07-04
why not just [http over ssl]("http://httpd.apache.org/docs/2.2/ssl/") on port 443?

---

### Post by kudeta on 2007-07-04
thanks, i just tried to do that following this guide:

[https://help.ubuntu.com/community/forum/server/apache2/SSL?highlight=%28ssl%29%7C%28apache%29](https://help.ubuntu.com/community/forum/server/apache2/SSL?highlight=%28ssl%29%7C%28apache%29)

Doesn't seem to work though, i restarted apache then went to  https:// on my server, it won't connect.


any ideas?

Edit: actually my mozilla says 
The connection was interrupted        

The connection to my.ip.ad.dy was interrupted while the page was loading.


whe i create the ssl certificate, i have to add a hostname right? well the hostname i use in there blagh.blagh.blam isn't active on the Net, in otherwords i can't access the site with that hostname as its still unaviable. Am i right in thinking that would stop SSL from working?

---

### Post by kudeta on 2007-07-04
these are the errors iam getting in error.log of apache:


```
[Thu Jul 05 01:44:13 2007] [info] Seeding PRNG with 136 bytes of entropy
[Thu Jul 05 01:44:13 2007] [info] SSL handshake failed: HTTP spoken on HTTPS port; trying to send HTML error page
[Thu Jul 05 01:44:13 2007] [info] SSL Library Error: 336027804 error:1407609C:SSL routines:func(118):reason(156)
[Thu Jul 05 01:44:13 2007] [info] Connection to child 6 established (server kudeta.vectoral.info:433, client 82.108.13.42)
[Thu Jul 05 01:44:13 2007] [info] Seeding PRNG with 136 bytes of entropy
[Thu Jul 05 01:44:13 2007] [info] SSL handshake failed: HTTP spoken on HTTPS port; trying to send HTML error page
[Thu Jul 05 01:44:13 2007] [info] SSL Library Error: 336027804 error:1407609C:SSL routines:func(118):reason(156)
[Thu Jul 05 01:44:46 2007] [info] Connection to child 2 established (server kudeta.vectoral.info:433, client 82.108.13.42)
[Thu Jul 05 01:44:46 2007] [info] Seeding PRNG with 136 bytes of entropy
[Thu Jul 05 01:44:46 2007] [info] SSL handshake failed: HTTP spoken on HTTPS port; trying to send HTML error page
[Thu Jul 05 01:44:46 2007] [info] SSL Library Error: 336027804 error:1407609C:SSL routines:func(118):reason(156)
[Thu Jul 05 01:45:13 2007] [info] Connection to child 3 established (server kudeta.vectoral.info:433, client 82.108.13.42)
[Thu Jul 05 01:45:13 2007] [info] Seeding PRNG with 136 bytes of entropy
[Thu Jul 05 01:45:13 2007] [info] SSL handshake failed: HTTP spoken on HTTPS port; trying to send HTML error page
[Thu Jul 05 01:45:13 2007] [info] SSL Library Error: 336027804 error:1407609C:SSL routines:func(118):reason(156)
[Thu Jul 05 01:49:12 2007] [notice] Graceful restart requested, doing restart
[Thu Jul 05 01:49:12 2007] [info] Connection to child 4 established (server kudeta.vectoral.info:433, client ::1)
[Thu Jul 05 01:49:12 2007] [info] Seeding PRNG with 136 bytes of entropy
[Thu Jul 05 01:49:12 2007] [info] (70014)End of file found: SSL handshake interrupted by system [Hint: Stop button pressed in browser?!]
[Thu Jul 05 01:49:12 2007] [info] Connection to child 4 closed with abortive shutdown(server kudeta.vectoral.info:433, client ::1)
[Thu Jul 05 01:49:12 2007] [info] Connection to child 5 established (server kudeta.vectoral.info:433, client ::1)
[Thu Jul 05 01:49:12 2007] [info] Seeding PRNG with 136 bytes of entropy
[Thu Jul 05 01:49:12 2007] [info] (70014)End of file found: SSL handshake interrupted by system [Hint: Stop button pressed in browser?!]
[Thu Jul 05 01:49:12 2007] [info] Connection to child 5 closed with abortive shutdown(server kudeta.vectoral.info:433, client ::1)
[Thu Jul 05 01:49:12 2007] [info] Connection to child 6 established (server kudeta.vectoral.info:433, client ::1)
[Thu Jul 05 01:49:12 2007] [info] Seeding PRNG with 136 bytes of entropy
[Thu Jul 05 01:49:12 2007] [info] (70014)End of file found: SSL handshake interrupted by system [Hint: Stop button pressed in browser?!]
[Thu Jul 05 01:49:12 2007] [info] Connection to child 6 closed with abortive shutdown(server kudeta.vectoral.info:433, client ::1)
[Thu Jul 05 01:49:13 2007] [info] Init: Initializing OpenSSL library
[Thu Jul 05 01:49:13 2007] [info] Init: Seeding PRNG with 136 bytes of entropy
[Thu Jul 05 01:49:13 2007] [info] Loading certificate & private key of SSL-aware server
[Thu Jul 05 01:49:13 2007] [info] Init: Generating temporary RSA private keys (512/1024 bits)
[Thu Jul 05 01:49:13 2007] [info] Init: Generating temporary DH parameters (512/1024 bits)
[Thu Jul 05 01:49:13 2007] [info] Init: Initializing (virtual) servers for SSL
[Thu Jul 05 01:49:13 2007] [info] Configuring server for SSL protocol
[Thu Jul 05 01:49:13 2007] [info] Server: Apache/2.0.55, Interface: mod_ssl/2.0.55, Library: OpenSSL/0.9.8a
[Thu Jul 05 01:49:13 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a configured -- resuming normal operations
[Thu Jul 05 01:49:13 2007] [info] Server built: Jul 26 2006 17:59:52
[Thu Jul 05 01:50:02 2007] [error] [client 82.108.13.42] Invalid method in request \x80g\x01\x03\x01
[Thu Jul 05 01:50:02 2007] [error] [client 82.108.13.42] Invalid method in request \x80g\x01\x03
[Thu Jul 05 01:50:07 2007] [error] [client 82.108.13.42] Invalid method in request \x80g\x01\x03
[Thu Jul 05 01:50:32 2007] [error] [client 82.108.13.42] Invalid method in request \x80g\x01\x03
[Thu Jul 05 01:50:42 2007] [error] [client 82.108.13.42] Invalid method in request \x80g\x01\x03
[Thu Jul 05 01:50:42 2007] [error] [client 82.108.13.42] Invalid method in request \x80g\x01\x03
[Thu Jul 05 01:51:20 2007] [info] removed PID file /var/run/apache2.pid (pid=20812)
[Thu Jul 05 01:51:20 2007] [notice] caught SIGTERM, shutting down
[Thu Jul 05 01:51:24 2007] [info] Init: Initializing OpenSSL library
[Thu Jul 05 01:51:24 2007] [info] Init: Seeding PRNG with 136 bytes of entropy
[Thu Jul 05 01:51:24 2007] [info] Loading certificate & private key of SSL-aware server
[Thu Jul 05 01:51:24 2007] [info] Init: Generating temporary RSA private keys (512/1024 bits)
[Thu Jul 05 01:51:24 2007] [info] Init: Generating temporary DH parameters (512/1024 bits)
[Thu Jul 05 01:51:24 2007] [info] Init: Initializing (virtual) servers for SSL
[Thu Jul 05 01:51:24 2007] [info] Configuring server for SSL protocol
[Thu Jul 05 01:51:24 2007] [info] Server: Apache/2.0.55, Interface: mod_ssl/2.0.55, Library: OpenSSL/0.9.8a
[Thu Jul 05 01:51:24 2007] [info] Init: Initializing OpenSSL library
[Thu Jul 05 01:51:24 2007] [info] Init: Seeding PRNG with 136 bytes of entropy
[Thu Jul 05 01:51:24 2007] [info] Loading certificate & private key of SSL-aware server
[Thu Jul 05 01:51:24 2007] [info] Init: Generating temporary RSA private keys (512/1024 bits)
[Thu Jul 05 01:51:24 2007] [info] Init: Generating temporary DH parameters (512/1024 bits)
[Thu Jul 05 01:51:24 2007] [info] Init: Initializing (virtual) servers for SSL
[Thu Jul 05 01:51:24 2007] [info] Configuring server for SSL protocol
[Thu Jul 05 01:51:24 2007] [info] Server: Apache/2.0.55, Interface: mod_ssl/2.0.55, Library: OpenSSL/0.9.8a
[Thu Jul 05 01:51:25 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a configured -- resuming normal operations
[Thu Jul 05 01:51:25 2007] [info] Server built: Jul 26 2006 17:59:52
[Thu Jul 05 01:51:33 2007] [error] [client 82.108.13.42] Invalid method in request \x80g\x01\x03
[Thu Jul 05 01:52:37 2007] [info] removed PID file /var/run/apache2.pid (pid=11647)
[Thu Jul 05 01:52:37 2007] [notice] caught SIGTERM, shutting down
[Thu Jul 05 01:52:38 2007] [info] Init: Initializing OpenSSL library
[Thu Jul 05 01:52:38 2007] [info] Init: Seeding PRNG with 136 bytes of entropy
[Thu Jul 05 01:52:38 2007] [info] Loading certificate & private key of SSL-aware server
[Thu Jul 05 01:52:38 2007] [info] Init: Generating temporary RSA private keys (512/1024 bits)
[Thu Jul 05 01:52:38 2007] [info] Init: Generating temporary DH parameters (512/1024 bits)
[Thu Jul 05 01:52:38 2007] [info] Init: Initializing (virtual) servers for SSL
[Thu Jul 05 01:52:38 2007] [info] Configuring server for SSL protocol
[Thu Jul 05 01:52:38 2007] [info] Server: Apache/2.0.55, Interface: mod_ssl/2.0.55, Library: OpenSSL/0.9.8a
[Thu Jul 05 01:52:38 2007] [info] Init: Initializing OpenSSL library
[Thu Jul 05 01:52:38 2007] [info] Init: Seeding PRNG with 136 bytes of entropy
[Thu Jul 05 01:52:38 2007] [info] Loading certificate & private key of SSL-aware server
[Thu Jul 05 01:52:38 2007] [info] Init: Generating temporary RSA private keys (512/1024 bits)
[Thu Jul 05 01:52:38 2007] [info] Init: Generating temporary DH parameters (512/1024 bits)
[Thu Jul 05 01:52:38 2007] [info] Init: Initializing (virtual) servers for SSL
[Thu Jul 05 01:52:38 2007] [info] Configuring server for SSL protocol
[Thu Jul 05 01:52:38 2007] [info] Server: Apache/2.0.55, Interface: mod_ssl/2.0.55, Library: OpenSSL/0.9.8a
[Thu Jul 05 01:52:38 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a configured -- resuming normal operations
[Thu Jul 05 01:52:38 2007] [info] Server built: Jul 26 2006 17:59:52
[Thu Jul 05 01:52:44 2007] [error] [client 82.108.13.42] Invalid method in request \x80g\x01\x03
[Thu Jul 05 02:10:56 2007] [error] [client 82.108.13.42] Invalid method in request \x80g\x01\x03
[Thu Jul 05 02:10:59 2007] [error] [client 82.108.13.42] Invalid method in request \x80g\x01\x03
[Thu Jul 05 02:12:16 2007] [error] [client 82.108.13.42] Invalid method in request \x80g\x01\x03
[Thu Jul 05 02:30:30 2007] [error] [client 82.108.13.42] Invalid method in request \x80g\x01\x03
[Thu Jul 05 02:39:59 2007] [notice] Graceful restart requested, doing restart
[Thu Jul 05 02:40:00 2007] [info] Init: Initializing OpenSSL library
[Thu Jul 05 02:40:00 2007] [info] Init: Seeding PRNG with 136 bytes of entropy
[Thu Jul 05 02:40:00 2007] [info] Loading certificate & private key of SSL-aware server
[Thu Jul 05 02:40:00 2007] [info] Init: Generating temporary RSA private keys (512/1024 bits)
[Thu Jul 05 02:40:00 2007] [info] Init: Generating temporary DH parameters (512/1024 bits)
[Thu Jul 05 02:40:00 2007] [info] Init: Initializing (virtual) servers for SSL
[Thu Jul 05 02:40:00 2007] [info] Configuring server for SSL protocol
[Thu Jul 05 02:40:00 2007] [info] Server: Apache/2.0.55, Interface: mod_ssl/2.0.55, Library: OpenSSL/0.9.8a
[Thu Jul 05 02:40:00 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a configured -- resuming normal operations
[Thu Jul 05 02:40:00 2007] [info] Server built: Jul 26 2006 17:59:52
[Thu Jul 05 02:40:29 2007] [error] [client 82.108.13.42] Invalid method in request \x80g\x01\x03
[Thu Jul 05 02:40:41 2007] [error] [client 82.108.13.42] Invalid method in request \x80g\x01\x03
[Thu Jul 05 02:41:15 2007] [error] [client 82.108.13.42] Invalid method in request \x80L\x01\x03
```

---

