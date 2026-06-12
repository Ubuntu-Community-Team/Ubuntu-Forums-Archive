---
title: "Openssl paypal server issues"
date: 2012-07-13
forum: Server Platforms
---

### Post by bronzeblood on 2012-07-13
I cant seem to use curl to access paypals server through openssl.

curl -v -ssl [https://api-aa-3t.paypal.com](https://api-aa-3t.paypal.com)
 
gives 


* About to connect() to api-aa-3t.paypal.com port 443 (#0)
*   Trying 173.0.88.100... connected
* successfully set certificate verify locations:
*   CAfile: none
  CApath: /etc/ssl/certs
* SSLv3, TLS handshake, Client hello (1):
* Unknown SSL protocol error in connection to api-aa-3t.paypal.com:443
* Closing connection #0


However 

 curl -v -ssl [https://api-aa-3t.sandbox.paypal.com](https://api-aa-3t.sandbox.paypal.com)
 gives 

* About to connect() to api-aa-3t.sandbox.paypal.com port 443 (#0)
*   Trying 173.0.82.84... connected
* successfully set certificate verify locations:
*   CAfile: none
  CApath: /etc/ssl/certs
* SSLv3, TLS handshake, Client hello (1):
* SSLv3, TLS handshake, Server hello (2):
* SSLv3, TLS handshake, CERT (11):
* SSLv3, TLS handshake, Server key exchange (12):
* SSLv3, TLS handshake, Server finished (14):
* SSLv3, TLS handshake, Client key exchange (16):
* SSLv3, TLS change cipher, Client hello (1):
* SSLv3, TLS handshake, Finished (20):
* SSLv3, TLS change cipher, Client hello (1):
* SSLv3, TLS handshake, Finished (20):
* SSL connection using DHE-RSA-AES256-SHA
etc..

I have updated openssl to 1.0.1 and still that same problem , I am using Ubuntu 12.04 server.
Most sites seem to handshake fine , its driving me insane!

My other server with 32 bit 12.04 works fine.

---

### Post by bronzeblood on 2012-07-13
Problem solved.

The MTU on the server was set to high , I contacted the data center and set the MTU to 1400 and now all works fine. Hope this helps anyone with similar problems.

---

