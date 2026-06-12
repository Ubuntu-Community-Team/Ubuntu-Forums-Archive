---
title: "openssl connexion problem"
date: 2011-08-02
forum: Server Platforms
---

### Post by tompasto on 2011-08-02
__Hello,

I change my server and get the new version of Ubuntu server 11.04
Since then i can reach a server i use to, with an ssl connexion (it still working on my old server).

I did an openssl commande to check what's wrong:
Here the result


CONNECTED(00000003)
turning on non blocking io
SSL_connect:before/connect initialization
SSL_connect:SSLv2/v3 write client hello A
SSL_connect:error in SSLv2/v3 read server hello A
write R BLOCK
SSL_connect:SSLv3 read server hello A
depth=1 /C=US/O=VeriSign, Inc./OU=VeriSign Trust Network/OU=Terms of use at [https://www.verisign.com/rpa](https://www.verisign.com/rpa) (c)10/CN=VeriSign Class 3 International Server CA - G3
verify error:num=20:unable to get local issuer certificate
verify return:0
SSL_connect:SSLv3 read server certificate A
SSL_connect:SSLv3 read server done A
SSL_connect:SSLv3 write client key exchange A
SSL_connect:SSLv3 write change cipher spec A
SSL_connect:SSLv3 write finished A
SSL_connect:SSLv3 flush data
SSL3 alert read:fatal:handshake failure
SSL_connect:failed in SSLv3 read finished A
24322:error:14094410:SSL routines:SSL3_READ_BYTES:sslv3 alert handshake failure:s3_pkt.c:1102:SSL alert number 40
24322:error:140780E5:SSL routines:SSL23_READ:ssl handshake failure:s23_lib.c:142:

Any idea what's wrong ?

---

### Post by tompasto on 2011-08-02
I can get a certificate if i add -ssl3 to the openssl command.
My problem is that it will not work with some php http request.

Any idea ?

---

