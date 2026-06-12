---
title: "Apache SSL Virtual host issues"
date: 2010-06-22
forum: Server Platforms
---

### Post by penguintiz on 2010-06-22
Hi,

I have a server using 2 IP based virtual hosts on Ubuntu 9.10 with a LAMP setup. I am trying to move one of the virtual hosts to https from http.
The host works fine using http but does not using https. I am using self signed certificates at the moment. I have gone to the simplest configuration and I get nothing in a browser.
In chrome I get this:
This webpage is not available.
Error 102 (net::ERR_CONNECTION_REFUSED): Unknown error.
Here is the virtual host config:

<VirtualHost 192.168.169.8:443>
ServerAdmin somebody@somewhere (valid email removed)
DocumentRoot /var/www/OpenZIS/OpenZIS/ZIT_SERVER
ServerName SomeServer (FQD removed)
<Directory /var/www/OpenZIS/OpenZIS/ZIT_SERVER>
Options Indexes FollowSymlinks
AllowOverride All
Order deny,allow
</Directory>
SSLEngine on
#SSLOptions  +ExportCertData  +StrictRequire
SSLCertificateFile /etc/ssl/certs/server.crt
SSLCertificateKeyFile /etc/ssl/private/server.key
</VirtualHost>

I have changed the apache error log to debug level but it isn't giving me any more helpful information.
This is the error log on startup
[Tue Jun 22 17:51:07 2010] [info] Init: Seeding PRNG with 656 bytes of entropy
[Tue Jun 22 17:51:07 2010] [info] Loading certificate & private key of SSL-aware server
[Tue Jun 22 17:51:07 2010] [debug] ssl_engine_pphrase.c(469): unencrypted RSA private key - pass phrase not required
[Tue Jun 22 17:51:07 2010] [info] Init: Generating temporary RSA private keys (512/1024 bits)
[Tue Jun 22 17:51:07 2010] [info] Init: Generating temporary DH parameters (512/1024 bits)
[Tue Jun 22 17:51:07 2010] [info] Init: Initializing (virtual) servers for SSL
[Tue Jun 22 17:51:07 2010] [info] Configuring server for SSL protocol
[Tue Jun 22 17:51:07 2010] [debug] ssl_engine_init.c(414): Creating new SSL context (protocols: SSLv3, TLSv1)
[Tue Jun 22 17:51:07 2010] [debug] ssl_engine_init.c(607): Configuring permitted SSL ciphers [HIGH:MEDIUM:!ADH]
[Tue Jun 22 17:51:07 2010] [debug] ssl_engine_init.c(370): Configuring TLS extension handling
[Tue Jun 22 17:51:07 2010] [debug] ssl_engine_init.c(738): Configuring RSA server certificate
[Tue Jun 22 17:51:07 2010] [debug] ssl_engine_init.c(777): Configuring RSA server private key
[Tue Jun 22 17:51:07 2010] [info] mod_ssl/2.2.12 compiled against Server: Apache/2.2.12, Library: OpenSSL/0.9.8g
PHP Warning:  Module 'PDO' already loaded in Unknown on line 0
PHP Warning:  Module 'pdo_mysql' already loaded in Unknown on line 0
[Tue Jun 22 17:51:07 2010] [info] Init: Seeding PRNG with 656 bytes of entropy
[Tue Jun 22 17:51:07 2010] [info] Loading certificate & private key of SSL-aware server
[Tue Jun 22 17:51:07 2010] [debug] ssl_engine_pphrase.c(469): unencrypted RSA private key - pass phrase not required
[Tue Jun 22 17:51:07 2010] [info] Init: Generating temporary RSA private keys (512/1024 bits)
[Tue Jun 22 17:51:07 2010] [info] Init: Generating temporary DH parameters (512/1024 bits)
[Tue Jun 22 17:51:07 2010] [debug] ssl_scache_shmcb.c(253): shmcb_init allocated 512000 bytes of shared memory
[Tue Jun 22 17:51:07 2010] [debug] ssl_scache_shmcb.c(272): for 511920 bytes (512000 including header), recommending 32 subcaches, 133 indexes each
[Tue Jun 22 17:51:07 2010] [debug] ssl_scache_shmcb.c(306): shmcb_init_memory choices follow
[Tue Jun 22 17:51:07 2010] [debug] ssl_scache_shmcb.c(308): subcache_num = 32
[Tue Jun 22 17:51:07 2010] [debug] ssl_scache_shmcb.c(310): subcache_size = 15992
[Tue Jun 22 17:51:07 2010] [debug] ssl_scache_shmcb.c(312): subcache_data_offset = 3208
[Tue Jun 22 17:51:07 2010] [debug] ssl_scache_shmcb.c(314): subcache_data_size = 12784
[Tue Jun 22 17:51:07 2010] [debug] ssl_scache_shmcb.c(316): index_num = 133
[Tue Jun 22 17:51:07 2010] [info] Shared memory session cache initialised
[Tue Jun 22 17:51:07 2010] [info] Init: Initializing (virtual) servers for SSL
[Tue Jun 22 17:51:07 2010] [info] Configuring server for SSL protocol
[Tue Jun 22 17:51:07 2010] [debug] ssl_engine_init.c(414): Creating new SSL context (protocols: SSLv3, TLSv1)
[Tue Jun 22 17:51:07 2010] [debug] ssl_engine_init.c(607): Configuring permitted SSL ciphers [HIGH:MEDIUM:!ADH]
[Tue Jun 22 17:51:07 2010] [debug] ssl_engine_init.c(370): Configuring TLS extension handling
[Tue Jun 22 17:51:07 2010] [debug] ssl_engine_init.c(738): Configuring RSA server certificate
[Tue Jun 22 17:51:07 2010] [debug] ssl_engine_init.c(777): Configuring RSA server private key
[Tue Jun 22 17:51:07 2010] [info] mod_ssl/2.2.12 compiled against Server: Apache/2.2.12, Library: OpenSSL/0.9.8g
[Tue Jun 22 17:51:07 2010] [notice] Apache/2.2.12 (Ubuntu) PHP/5.2.10-2ubuntu6.4 with Suhosin-Patch mod_ssl/2.2.12 OpenSSL/0.9.8g configured -- resuming normal operations
[Tue Jun 22 17:51:07 2010] [info] Server built: Mar  9 2010 22:11:44
[Tue Jun 22 17:51:07 2010] [debug] prefork.c(1013): AcceptMutex: sysvsem (default: sysvsem)

Does anyone have any ideas?
Thanks.

Dave

---

### Post by Ryan Dwyer on 2010-06-22
Is your server listening on port 443?

Also, you should change your IP address in your <VirtualHost> tag to *. For example, <VirtualHost *:443>.

---

### Post by penguintiz on 2010-06-22
Yes I am listening on port 443
This is the ports.conf file

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>

It is my understanding that the ip address needs to be in the VirtualHost directive since I am using IP based virtual hosts
<VirtualHost 192.168.169.8:443>
Is this incorrect? It works when I doing http but not doing https

Thaks.

Dave

---

### Post by Ryan Dwyer on 2010-06-22
You might be right with the IP thing.

I don't know what the cause of the problem is. In a few hours I'll have time to play around with SSL, so I'll get back to you then if no one else does.

---

### Post by penguintiz on 2010-06-23
Thanks. Appreciate it.

---

### Post by penguintiz on 2010-06-23
I forgot to open the port in the firewall.
I may need more help. I need to get two way certificate authentication working. Basic https is functional.

---

### Post by Ryan Dwyer on 2010-06-24
According to Wikipedia ([http://en.wikipedia.org/wiki/Transport_Layer_Security#How_it_works](http://en.wikipedia.org/wiki/Transport_Layer_Security#How_it_works)), "both parties generate key material for encryption and decryption." So if you have SSL working properly all information travelling both ways should be encrypted. Unless I've misunderstood your request about two way certificate authentication.

I also found this to be an excellent resource: [https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html](https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html)

---

