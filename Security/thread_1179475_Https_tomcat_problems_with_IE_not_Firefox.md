---
title: "Https tomcat problems with IE not Firefox"
date: 2009-06-05
forum: Security
---

### Post by mikeklein on 2009-06-05
I setup tomcat https per apache instructions (using 2-way client auth) and it works fine for Firefox.

However any version of IE (6-8), openssl or N800 browser won't connect.

On IE get generic "cannot display web page".

Using openssl I get "SSL alert number 42" message.

$ openssl s_client -host 192.168.1.10 -port 8443 -CAfile father.vxappliance.com -tls1
CONNECTED(00000003)
depth=1 /emailAddress=hostmaster@vx.com/C=US/ST=CA/L=San Francisco/O=Vir, Inc./OU=Engineering/CN=Vir

verify return:1
depth=0 /emailAddress=foo@bar.com/C=us/ST=ca/L=san francisco/O=vxappliance/OU=engr/CN=father
verify return:1
7952:error:14094412:SSL routines:SSL3_READ_BYTES:sslv3 alert bad certificate:s3_pkt.c:1060:SSL alert number 42
7952:error:1409E0E5:SSL routines:SSL3_WRITE_BYTES:ssl handshake failure:s3_pkt.c:530:

Any ideas? I've tried using openssl s_client with a variety of protocol types and get same message back. I've also tried tweaking certain IE settings...to no avail.

---

