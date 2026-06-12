---
title: "Disable TLS1.0 / apache / LTS14.04"
date: 2015-07-23
forum: Server Platforms
---

### Post by m0rph3us0306 on 2015-07-23
We had a scan done (routine) and getting a message saying that TLS1.0 is still supported on the server and must be disabled for PCI complaince.  I have tried numerous the latest being;

```
SSLProtocol -all -SSLv2 -SSLv3 -TLSv1 +TLSv1.1 +TLSv1.2
SSLHonorCipherOrder on
SSLCompression Off
SSLCipherSuite ALL:!ADH:RC4+RSA:+HIGH:+MEDIUM:-LOW:-SSLv2:-SSLv3:-EXP:!kEDH

```

Now before I ask them to rscan, I am testing using *openssl s_client -connect secure.mydomain.com:443 -tls1* and getting the response;
CONNECTED(00000003)

So before I have them re-scan, to me that it still is accepting.  I have read so much my eyes hurt, but wondering am I missing something else?
Thanks for all read/posts back.

---

### Post by TheFu on 2015-07-24
Is the system completely patched and current?
[https://askubuntu.com/questions/477260/ubuntu-server-14-04-apache-2-4-tlsv1-2-tlsv1-1-support](https://askubuntu.com/questions/477260/ubuntu-server-14-04-apache-2-4-tlsv1-2-tlsv1-1-support) says old versions of openssl were not compiled with the correct settings.

Lacking that, [https://httpd.apache.org/docs/2.4/mod/mod_ssl.html](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html) has all the options. Saw some with "Cmd" in the name that might help if the normal options aren't working.

---

