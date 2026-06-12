---
title: "malicious root certificates?"
date: 2016-01-24
forum: Security
---

### Post by haplorrhine on 2016-01-24
[https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL) > One of the drawbacks of using self-signed certificates, however, is that  warnings will typically be issued by a user's Web browser, and other  applications, upon accessing an SSL-secured server that uses a  self-signed certificate.  By default, client applications (e.g., Firefox) will suppress such warnings for certificates that are signed using only a globally-recognized and trusted Certificate Authority,  but warnings may also be squelched by importing a server's root  certificate into client applications; a relevant demonstration is shown  later in this guide.

It seems like importing root certificates could be of interest to blackhats imitating websites.  Could they import a root certificate and spoof the certificate's checksums with only a browser exploit, without ever accessing the system files?  How would one catch such an exploit?  One of my modems started giving a "Connect" page that I'm not sure it should give that never provides a certificate on a user's first viewing.  There's no hard reset.  I would also like to know how to check the certificate checksums without relying on the browser.


I wanted to do tags, but it's saying they're too long.
certificate, certificate authority, browser exploit,

---

### Post by Habitual on 2016-01-25
> **haplorrhine said:**
> I would also like to know how to check the certificate checksums without relying on the browser.

I use this on occasion:
```
echo | openssl s_client -connect host:<ssl_port> -CApath /etc/ssl/certs/
```
output should show you some decent info.

---

### Post by haplorrhine on 2016-02-10
I looked at some certs in the /etc/ssl/certs folder, but couldn't find the certificate I wanted, which is probably elsewhere.  [https://ubuntuforums.org/showthread.php?t=1093952](https://ubuntuforums.org/showthread.php?t=1093952)

visitor@junk:~$ echo | openssl s_client -connect junk:443 -CApath /etc/ssl/certs/UbuntuOne-Go_Daddy_CA.pem
connect: Connection refused
connect:errno=111

I don't see why I should need to connect since the certificate should already be stored. I'm wondering whether I could just hash the file, but perhaps not good for comparing certs between devices with different private keys, correct?

---

