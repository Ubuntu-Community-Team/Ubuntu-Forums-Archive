---
title: "postfix tls install"
date: 2007-09-19
forum: Server Platforms
---

### Post by dysolve on 2007-09-19
Hi all I am following the following guide

[http://www.howtoforge.com/perfect_setup_ubuntu704_p5](http://www.howtoforge.com/perfect_setup_ubuntu704_p5)

and when I get to the following part I get some problems. not about below, the guide is is red and the errors are in blue.

[COLOR="Red"]
mkdir /etc/postfix/ssl
cd /etc/postfix/ssl/
openssl genrsa -des3 -rand /etc/hosts -out smtpd.key 1024

chmod 600 smtpd.key
openssl req -new -key smtpd.key -out smtpd.csr

openssl x509 -req -days 3650 -in smtpd.csr -signkey smtpd.key -out smtpd.crt[/COLOR]
[COLOR="DarkSlateBlue"]error: smtpd.csr: no such file or directory[/COLOR]
[COLOR="red"]openssl rsa -in smtpd.key -out smtpd.key.unencrypted

mv -f smtpd.key.unencrypted smtpd.key[/COLOR]
[COLOR="DarkSlateBlue"]error: mv:target 'smtpd.key' is not a directory[/COLOR]
[COLOR="Red"]openssl req -new -x509 -extensions v3_ca -keyout cakey.pem -out cacert.pem -days 3650[/COLOR]

I have done this in the past and have not had issues.. what have I done wrong now?

thanks
David.

---

### Post by MJN on 2007-09-19
[COLOR=Black]It looks fine to me - are you sure you're not making any typos? What does your directory listing look like after each step?
[B]
error: smtpd.csr: no such file or directory [/B]is self-explanatory - the certificate signing request does not exist. Can you confirm the file does exist following the previous step? If not, was there any output suggesting why it wasn't created?

Mathew
[/COLOR]

---

### Post by dysolve on 2007-09-20
thanks for the ideas but I found my problem.. two steps back i used a "1" instead of an "L" lol...

---

