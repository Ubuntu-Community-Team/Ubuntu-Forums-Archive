---
title: "Posfix"
date: 2008-10-08
forum: Server Platforms
---

### Post by Maltar on 2008-10-08
I am trying to make a e-mail server using postfix. The first step i made was installing bind9 and creating a mx record for the mail-server. then I used the tutorial given [**here**]("http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04") for my postfix installation. 

Now when i try to acces squirrel mail i get the following error: ERROR: Connection dropped by IMAP server.

Troubleshooting this i get the following messages in the mail.err log files.

```
Sep 10 07:25:39 mail-server postfix/smtpd[5594]: fatal: non-null host address bits in "127.0.0.1/8", perhaps you should use  "127.0.0.0/8" instead
```

my postfix conifuration file main.cf has the following line in it
```
mynetworks = 127.0.0.0/8
```

So why am i getting this error did I miss something and does it have any relevance with not being able to login squirrelmail?

---

### Post by MJN on 2008-10-08
> **Maltar said:**
> Now when i try to acces squirrel mail i get the following error: ERROR: Connection dropped by IMAP server.Postfix is only concerned with the SMTP side of things - sending and receiving mail, not the storage of it. This latter role is done by the IMAP server - in your case Courier - and so that's where you need to be looking to solve that problem. I've not used Courier so cannot really comment much on that.
 
That said, you do still have a problem with Postfix which needs to be fixed anyway:
 
> Sep 10 07:25:39 mail-server postfix/smtpd[5594]: fatal: non-null host address bits in "127.0.0.1/8", perhaps you should use "127.0.0.0/8" instead
 
You must have a 127.0.0.1/8 mention somewhere... perhaps in master.cf if not main.cf? (It is most likely to be in a network-related directive as, by definition, the host portion of a network definition should be all zeroes)
 
> did I miss something and does it have any relevance with not being able to login squirrelmail?
 
Yes, and no. (see above.. ;))
 
Mathew

---

