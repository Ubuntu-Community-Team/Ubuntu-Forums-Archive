---
title: "postfix and dovecot issue connecting with thunderbird, outlook and similars"
date: 2015-02-10
forum: Server Platforms
---

### Post by niccolo.ferrari on 2015-02-10
I was setting up a postfix and a dovecot mail server. Now I can send and receive mails reading and sending them with
  ```
mail

```  but I'm not able to configure postfix and dovecot to connect with pop3/imap and smtp with outlook or thunderbird.
  with
  ```
netstat ln4

```  i get:
  ```
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
udp        0      0 127.0.0.1:53            0.0.0.0:*                        

```  I don't see secure smtp port bind.
  any ideas? Thank you

---

### Post by niccolo.ferrari on 2015-02-10
Solved, I only forgot to uncomment

submission inet n       -       -       -       -       smtpd

now all is ok!

---

