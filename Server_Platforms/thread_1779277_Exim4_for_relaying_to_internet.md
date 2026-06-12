---
title: "Exim4 for relaying to internet"
date: 2011-06-10
forum: Server Platforms
---

### Post by andriu1 on 2011-06-10
Hi all, here we again trying to learn how to's:

Now, i must to install a new server to allow an internat application to send e-mail to external e-mail accounts

I've been reading a bit about sendmail, postfix and exim4, and i've started to exim4 configuration. So, step by step, I've followed instructions described in the link [https://help.ubuntu.com/community/Exim4](https://help.ubuntu.com/community/Exim4).

While configuration, I've selected; 1-Internet site, 2-system mail: hostname.domain.int, 3-IP: 127.0.0.1, 4-Other destination: hostname.domain.int, hostname, localhost.localdomain, localhost, 5-Domain to relay: BLANK, 6-Machine to relay: BLANK, 7-DNS Queries: NO, 8-Delivery method: Maildir format, 9-Split:NO

After I've finished instructions I've tried to e-mail by telnet localhost 25
```
ehlo hostname
250-hostname.domain.int Hello localhost [127.0.0.1]
250-SIZE 52428800
250-PIPELINING
250-STARTTLS
250 HELP

```

No user and password are requested, as I thought that it was going to happen. 

The e-mail is sent succesfully to an external account, but i'd like user credentials to be necessary.

Could anyone has experience with exim4 to help me to know what's wrong?

Thanks in advance for your contributions

Regards,
Andres

---

### Post by andriu1 on 2011-06-21
Hi all, nobody?

Regards
Andres

---

### Post by andriu1 on 2011-06-24
Hello again.

    I've been testing my configuration with swaks  utility and it seems that authentication works anyway, because correct  password for LocalUser is required and test e-mail is received into  destination inbox
```
swaks -a -tls -f origin@domain.com -t destination@domain.com -s ip_exim_server -au LocalUser
```

but I don't understand why trying through telnet allows to send e-mails without authentication

Has anyone a response for this?

Thank you for your time

Regards,
Andres

---

