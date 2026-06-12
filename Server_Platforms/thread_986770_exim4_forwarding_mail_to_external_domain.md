---
title: "exim4 forwarding mail to external domain"
date: 2008-11-18
forum: Server Platforms
---

### Post by evquink on 2008-11-18
I have installed exim4 to allow system messages to be sent to an external email address (gmail).  I used these instructions for setting up exim4:

[http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/](http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/)

Using the command "mail [email]username@gmail.com[/email]" works flawlessly but if I try to forward the messages using an entry in /etc/aliases or by placing a .forward file in the home directory, the mail does not go through.  Debug messages (using mail -v) show that both cases (direct mail to the gmail address and the forwarded version) appear to complete successfully. 

Output from commands are below.

Any suggestions would be greatly appreciated.

Following is the output when sending directly to gmail (this works)
```

root@[hostname]:/# mail -v [username]@gmail.com
Subject: This works
Cc: Null message body; hope that's ok
LOG: MAIN
  <= root@[hostname].localdomain U=root P=local S=386
root@[hostname]:/# delivering 1L2dkZ-0001KK-1i
Connecting to gmail-smtp-msa.l.google.com [74.125.93.111]:587 ... connected
  SMTP<< 220 mx.google.com ESMTP 2sm1921767qwi.5
  SMTP>> EHLO [hostname].localdomain
  SMTP<< 250-mx.google.com at your service, [75.73.239.248]
         250-SIZE 35651584
         250-8BITMIME
         250-STARTTLS
         250 ENHANCEDSTATUSCODES
  SMTP>> STARTTLS
  SMTP<< 220 2.0.0 Ready to start TLS
  SMTP>> EHLO [hostname].localdomain
  SMTP<< 250-mx.google.com at your service, [75.73.239.248]
         250-SIZE 35651584
         250-8BITMIME
         250-AUTH LOGIN PLAIN
         250 ENHANCEDSTATUSCODES
  SMTP>> AUTH LOGIN
  SMTP<< 334 ************
  SMTP>> ****************************
  SMTP<< 334 ************
  SMTP>> ************
  SMTP<< 235 2.7.0 Accepted
  SMTP>> MAIL FROM:<root@[hostname].localdomain> SIZE=1419 AUTH=root@[hostname].localdomain
  SMTP<< 250 2.1.0 OK 2sm1921767qwi.5
  SMTP>> RCPT TO:<[username]@gmail.com>
  SMTP<< 250 2.1.5 OK 2sm1921767qwi.5
  SMTP>> DATA
  SMTP<< 354  Go ahead 2sm1921767qwi.5
  SMTP>> writing message and terminating "."
  SMTP<< 250 2.0.0 OK 1227065518 2sm1921767qwi.5
  SMTP>> QUIT
LOG: MAIN
  => [username]@gmail.com R=send_via_gmail T=gmail_smtp H=gmail-smtp-msa.l.google.com [74.125.93.111] X=TLS-1.0:RSA_ARCFOUR_MD5:16 DN="C=US,ST=California,L=Mountain View,O=Google Inc,CN=smtp.gmail.com"
LOG: MAIN
  Completed

```

Following is output when forwarding from the local user etg to gmail
```

root@[hostname]:/# mail -v etg
Subject: This does not work
Cc: Null message body; hope that's ok
LOG: MAIN
  <= root@[hostname].localdomain U=root P=local S=408
root@[hostname]:/# delivering 1L2dnk-0001KX-R2
R: system_aliases for etg@[hostname].localdomain
Connecting to gmail-smtp-msa.l.google.com [74.125.93.111]:587 ... connected
  SMTP<< 220 mx.google.com ESMTP 4sm1862548qwe.3
  SMTP>> EHLO [hostname].localdomain
  SMTP<< 250-mx.google.com at your service, [75.73.239.248]
         250-SIZE 35651584
         250-8BITMIME
         250-STARTTLS
         250 ENHANCEDSTATUSCODES
  SMTP>> STARTTLS
  SMTP<< 220 2.0.0 Ready to start TLS
  SMTP>> EHLO [hostname].localdomain
  SMTP<< 250-mx.google.com at your service, [75.73.239.248]
         250-SIZE 35651584
         250-8BITMIME
         250-AUTH LOGIN PLAIN
         250 ENHANCEDSTATUSCODES
  SMTP>> AUTH LOGIN
  SMTP<< 334 ************
  SMTP>> ****************************
  SMTP<< 334 ************
  SMTP>> ************
  SMTP<< 235 2.7.0 Accepted
  SMTP>> MAIL FROM:<root@[hostname].localdomain> SIZE=1441 AUTH=root@[hostname].localdomain
  SMTP<< 250 2.1.0 OK 4sm1862548qwe.3
  SMTP>> RCPT TO:<[username]@gmail.com>
  SMTP<< 250 2.1.5 OK 4sm1862548qwe.3
  SMTP>> DATA
  SMTP<< 354  Go ahead 4sm1862548qwe.3
  SMTP>> writing message and terminating "."
  SMTP<< 250 2.0.0 OK 1227065716 4sm1862548qwe.3
  SMTP>> QUIT
LOG: MAIN
  => [username]@gmail.com <etg@[hostname].localdomain> R=send_via_gmail T=gmail_smtp H=gmail-smtp-msa.l.google.com [74.125.93.111] X=TLS-1.0:RSA_ARCFOUR_MD5:16 DN="C=US,ST=California,L=Mountain View,O=Google Inc,CN=smtp.gmail.com"
LOG: MAIN
  Completed

```

---

