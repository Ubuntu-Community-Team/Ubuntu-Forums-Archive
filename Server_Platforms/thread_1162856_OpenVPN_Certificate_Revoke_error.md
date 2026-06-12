---
title: "OpenVPN Certificate Revoke error"
date: 2009-05-18
forum: Server Platforms
---

### Post by dipeshmehta on 2009-05-18
Hello,

I am trying to revoke a certificate as guided at [http://openvpn.net/index.php/documentation/howto.html#revoke](http://openvpn.net/index.php/documentation/howto.html#revoke) but not getting through.  I get following output:
```
root@server1:/usr/share/doc/openvpn/examples/easy-rsa/2.0# ./revoke-full user1
Using configuration from /usr/share/doc/openvpn/examples/easy-rsa/2.0/openssl.cnf
error on line 282 of config file '/usr/share/doc/openvpn/examples/easy-rsa/2.0/openssl.cnf'
32288:error:0E065068:configuration file routines:STR_COPY:variable has no value:conf_def.c:629:line 282
Using configuration from /usr/share/doc/openvpn/examples/easy-rsa/2.0/openssl.cnf
error on line 282 of config file '/usr/share/doc/openvpn/examples/easy-rsa/2.0/openssl.cnf'
32289:error:0E065068:configuration file routines:STR_COPY:variable has no value:conf_def.c:629:line 282
cat: crl.pem: No such file or directory
user1.crt: /C=IN/ST=GJ/L=RJ/O=ABC/OU=MKT/CN=USER1/emailAddress=USER1@DOMAIN.COM
error 3 at 0 depth lookup:unable to get certificate CRL

``` 

Can anybody please help me ?

Dipesh

---

### Post by dipeshmehta on 2009-05-21
***   bump   ***

---

### Post by senor_smile on 2010-02-02
I am having the same problem.  anyone have any clue how to revoke certs made from openvpn on ubuntu?

---

### Post by senor_smile on 2010-02-02
Fixed!  

see:
[https://bugs.launchpad.net/ubuntu/+source/openvpn/+bug/231199](https://bugs.launchpad.net/ubuntu/+source/openvpn/+bug/231199)

---

