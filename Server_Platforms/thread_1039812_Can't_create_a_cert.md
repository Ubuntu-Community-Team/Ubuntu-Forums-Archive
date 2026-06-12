---
title: "Can't create a cert"
date: 2009-01-14
forum: Server Platforms
---

### Post by shoaibi on 2009-01-14
I have created my own ca, and now i am trying to sign a csr with that but i keep getting:
```

 openssl x509 -req -days 365 -in server.csr -CA ca.crt -CAkey ca.key -out server.crt
Signature ok
subject=/C=BE/ST=Brussel/L=Brussel/O=testcompany/CN=example.com/emailAddress=example@example.com
Getting CA Private Key
Enter pass phrase for ca.key:
ca.srl: No such file or directory
14957:error:02001002:system library:fopen:No such file or directory:bss_file.c:352:fopen('ca.srl','r')
14957:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:354:

```

Passphrase is correct for sure... what is this ca.srl file?

---

### Post by spiderbatdad on 2009-01-14
[http://www.herongyang.com/crypto/OpenSSL_Signing_keytool_CSR_5.html](http://www.herongyang.com/crypto/OpenSSL_Signing_keytool_CSR_5.html)
basically 3 options:
    * Create a text file named "ca.srl" and put a number in the file.
    * Use the "-set_serial n" option to specify a number each time.
    * Use the "-CAcreateserial -CAserial ca.seq" option to let OpenSSL create and manage the serial number.

---

