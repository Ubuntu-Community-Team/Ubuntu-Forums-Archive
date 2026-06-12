---
title: "How to retrieve remote certificate for postfix-tls"
date: 2005-08-24
forum: Server Platforms
---

### Post by tribut on 2005-08-24
Hi.

I try to set up postfix to use TLS when relaying mail to a smarthost, according to [the postfix-tls docs](http://www.aet.tu-cottbus.de/personen/jaenicke/postfix_tls/doc/index.html).

Everything works exept for the validation of the remote certificate:
```

postfix/smtp[9760]: verify error:num=20:unable to get local issuer certificate
postfix/smtp[9760]: SSL_connect error to auth.mail.onlinehome.de: -1
postfix/smtp[9760]: 9760:error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed:s3_c
lnt.c:844:

``` 

I spent hours searching the net on how to retrieve the remote certificate so postfix can validate the remote host. Some howto recommended
```
$ openssl s_client -starttls smtp -connect smarthost:25
```

But unfortunately my smarthost requires HELO to be sent before STARTTLS ("503 bad sequence of commands"). This is a [known bug](http://archives.neohapsis.com/archives/postfix/2005-02/0172.html) and I can't find any other hints :(


Any help would be grately appreciated!
felix

---

### Post by tribut on 2005-08-24
I finally found a way:
SSL_Tool.exe (which runs just fine under wine) from [http://sites.inka.de/ximera/hamster-en.html#ssl-tools](http://sites.inka.de/ximera/hamster-en.html#ssl-tools) does the trick.

---

