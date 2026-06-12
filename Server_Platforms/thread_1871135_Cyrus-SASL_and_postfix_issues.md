---
title: "Cyrus-SASL and postfix issues"
date: 2011-10-28
forum: Server Platforms
---

### Post by ZaphoidPA on 2011-10-28
Hi. 

I am trying to setup Auth SMTP with postfix and cyrus-SASL. I have, I  believe setup SASL correctly, and testsaslauthd -u user -p password  responds with "OK". I am running SASL in rimap mode against a remote  IMAP server. 

Attempts to connect through to the SMTP daemon result in authentication failures, and the following log messages:

Oct 27 22:17:32 computer postfix/smtpd[30787]: warning: SASL authentication failure: Password verification failed
Oct 27 22:17:32 computer postfix/smtpd[30787]: warning: unknown[192.168.0.34]: SASL PLAIN authentication failed: generic failure
Oct 27 22:17:34 computer postfix/smtpd[30787]: warning: SASL  authentication failure: cannot connect to saslauthd server: No such file  or directory

Any thoughts on where I should be looking? I have googled high and low, and have not come up with any answers. 

I am running Ubuntu Server 10.4. 

Thanks,
Richard.

---

### Post by vasile002 on 2011-10-29
I believe postfix is looking for the saslauthd socket inside /var/spool/postfix because it runs chrooted. Try this:
```

mkdir /var/spool/postfix/var/run/saslauthd/
ln -s /var/run/saslauthd/SOCKTENAME /var/spool/postfix/var/run/saslauthd/SOCKETNAME

```

replace socketname with the name of the socket

---

### Post by ZaphoidPA on 2011-10-31
I did:

 ln -s /var/run/saslauthd/mux /var/spool/postfix/var/run/saslauthd/mux

..and I get:

warning: SASL authentication failure: cannot connect to saslauthd server: Too many levels of symbolic links

So I suspect my issue is I have missed a configuration somewhere and postfix or SASL don't know where to "talk" to each other.  Now the fun part is figuring out which is missing the mark.

---

### Post by ZaphoidPA on 2011-10-31
Got it!

Found this article here, and it very, very nicely tied everything together.

[http://www.jimmy.co.at/weblog/?p=52](http://www.jimmy.co.at/weblog/?p=52)

It was a combination of pathing and permissions. 

Regards,
Richard.

---

