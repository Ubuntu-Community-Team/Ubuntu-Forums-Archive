---
title: "postfix and FQDN"
date: 2012-09-04
forum: Server Platforms
---

### Post by wlraider70 on 2012-09-04
I am trying to setup postfix. I have followed several guides, they say the same thing and I am mailing everytime

I think my issue is the domain name.
I don't really have a domain so I used no-ip.


myhostname = **philo**.**something.no-ip.org**

philo is my system name/ my as in "server@philo:~$"
something.no-ip-org is linked to my public ip address.


Am i misunderstanding the concept of a FQDN?
Technically something.no-ip.org is my router not that box.
Isn't that why i used "philo"?

Edit: I do seem to get the email in the mail folder of the user who sent, but im trying to send it to an external address.

---

### Post by Bachstelze on 2012-09-04
A FQDN needs to be something you have a DNS record for. If you are using no-ip's free service, you do not have a record for anything.yourdomain.no-ip.org, and so the FQDN you configure in your server must be just yourdomain.no-ip.org. The internal hostname you have configured on your computer is irrelevant.

---

### Post by wlraider70 on 2012-09-04
ok that makes sense. SO I set 


myhostname = something.no-ip.org
mydomain   = something.no-ip.org

I restarted postfix 


mail [email]me@gmail.com[/email] < test.txt


still nothing

---

### Post by lisati on 2012-09-04
*Thread moved to **Server Platforms**.*

edit: is anything showing up in Postfix's log? It's commonly found at /var/log/mail.log

---

### Post by Bachstelze on 2012-09-04
> **wlraider70 said:**
> 
I restarted postfix 


mail [email]me@gmail.com[/email] < test.txt


still nothing

Do

```
mailq
```

to check that it is not stuck in the queue. If the queue is empty

```
sudo tail /var/log/mail.log
```

---

### Post by wlraider70 on 2012-09-04
:~/Maildir $ mailq
/var/spool/mqueue is empty
                Total requests: 0


```

:/var/log $ tail mail.log
Sep  4 16:29:34 pbx sendmail[2955]: q84KTYe0002955: from=root, size=237, class=0, nrcpts=1, msgid=<201209042029.q84KTYe0002955@something.no-ip.org>, relay=root@localhost
Sep  4 16:29:34 pbx postfix/smtpd[2956]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Sep  4 16:29:34 pbx postfix/smtpd[2956]: connect from something.no-ip.org[127.0.0.1]
Sep  4 16:29:34 pbx postfix/smtpd[2956]: DD92B23E057: client=something.no-ip.org[127.0.0.1]
Sep  4 16:29:34 pbx postfix/cleanup[2959]: DD92B23E057: message-id=<201209042029.q84KTYe0002955@something.no-ip.org>
Sep  4 16:29:34 pbx postfix/qmgr[2936]: DD92B23E057: from=<root@something.no-ip.org>, size=678, nrcpt=1 (queue active)
Sep  4 16:29:34 pbx sendmail[2955]: q84KTYe0002955: to=me@gmail.com, ctladdr=root (0/0), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30237, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (Ok: queued as DD92B23E057)
Sep  4 16:29:34 pbx postfix/smtpd[2956]: disconnect from something.no-ip.org[127.0.0.1]
Sep  4 16:29:35 pbx postfix/smtp[2960]: DD92B23E057: to=<me@gmail.com>, relay=gmail-smtp-in.l.google.com[173.194.68.26]:25, delay=0.55, delays=0.06/0.01/0.1/0.38, dsn=2.0.0, status=sent (250 2.0.0 OK 1346790056 fq7si17474235qab.38)
Sep  4 16:29:35 pbx postfix/qmgr[2936]: DD92B23E057: removed


```

---

### Post by Bachstelze on 2012-09-04
Well, it seems to work fine... Have you checked your spam folder (especially if you have a dynamic IP)? Also, can you recieve mail on your server? If something went wrong on gmail's side, you should have received a notification on [email]root@something.no-ip.org[/email].

---

### Post by wlraider70 on 2012-09-04
Sweet merciful crap son, its in the spam folder

THANKS

---

