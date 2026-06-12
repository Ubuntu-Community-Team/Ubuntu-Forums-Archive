---
title: "Postfix/dovecot/MySQL auth problem?"
date: 2013-05-09
forum: Server Platforms
---

### Post by mmangus624 on 2013-05-09
I set up a mail server on Ubuntu 12.04 LTS on an Amazon public EC2 instance. I have an MX record pointing to it 'myserver@mydomain.net' and I can connect to it with my local Thunderbird client with the email user I set up. All of that is working. What isn't working is mail flow. When I send an email to the user I created it never arrives. When I send and email from the user I created it never arrives. I'm seeing the following in /var/log/mail.log:

```
May  9 15:56:54 responder postfix/smtpd[2220]: connect from myserver.mydomain.net[127.0.0.1]
May  9 15:56:54 responder postfix/smtpd[2220]: disconnect from myserver.mydomain.net[127.0.0.1]
May  9 15:56:54 responder dovecot: imap-login: Aborted login (no auth attempts): rip=127.0.0.1, lip=127.0.0.1, TLS
```

Thinking it might be an authentication problem I checked telnet localhost imap which seemed to work fine:

```
Trying 127.0.0.1...
Connected to myserver.mydomain.net.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE STARTTLS AUTH=PLAIN AUTH=LOGIN AUTH=DIGEST-MD5 AUTH=CRAM-MD5] Dovecot ready.
```

I'm using a self-signed certificate.

I also tried this command that seems to work:

openssl s_client -connect localhost:993
```

CONNECTED(00000003)
...
verify return:1
---
Certificate chain
...
---
Server certificate ...
---
No client certificate CA names sent
---
SSL handshake has read 1870 bytes and written 440 bytes
---
New, TLSv1/SSLv3, Cipher is DHE-RSA-AES256-SHA
Server public key is 2048 bit
Secure Renegotiation IS supported
Compression: zlib compression
Expansion: zlib compression
SSL-Session:
    Protocol  : TLSv1.1
    Cipher    : DHE-RSA-AES256-SHA
    Session-ID: 96384859EC39329E56F258FE9A61E1D80872B95B37E4F5D351CED89A4FF6AF5B
    Session-ID-ctx:
    Master-Key: 75CEC157679A6EC511C9141C1376C4CFC318DF2F14AC09D59F869C01A91B0D884458B53383B5CAC80595A60623F630FB
    Key-Arg   : None
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
...
    Compression: 1 (zlib compression)
    Start Time: 1368115246
    Timeout   : 300 (sec)
    Verify return code: 18 (self signed certificate)
---
* OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE AUTH=PLAIN AUTH=LOGIN AUTH=DIGEST-MD5 AUTH=CRAM-MD5] Dovecot ready.

```


It seems very close to working. What am I missing?

---

### Post by darkod on 2013-05-09
How about telnet from outside, not localhost?

Are you sure you set up postfix and dovecot to use the mysql correctly?

---

### Post by SeijiSensei on 2013-05-09
Do you have the **postfix-mysql** and **dovecot-mysql** packages installed?

---

