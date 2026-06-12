---
title: "Is someone trying to hack my mail server?"
date: 2008-12-06
forum: Server Platforms
---

### Post by Twizzle on 2008-12-06
I have set up a simple home server for storage and email and have just notice the following in my mail.log:

> Dec  6 06:44:35 thegcs postfix/smtpd[10698]: warning: TLS library problem: 10698:error:0906D066:PEM routines:PEM_read_bio:bad end line:pem_lib.c:746:
Dec  6 06:44:35 thegcs postfix/smtpd[10698]: warning: TLS library problem: 10698:error:0B084009:x509 certificate routines:X509_load_cert_crl_file:PEM lib:by_file.c:280:
Dec  6 06:44:36 thegcs postfix/smtpd[10698]: connect from 124-11-193-196.static.tfn.net.tw[124.11.193.196]
Dec  6 06:44:37 thegcs postfix/smtpd[10698]: NOQUEUE: reject: RCPT from 124-11-193-196.static.tfn.net.tw[124.11.193.196]: 554 5.7.1 <sseenndd1201@yahoo.com.hk>: Relay access denied; from=<jk9l3g4jle@yahoo.com> to=<sseenndd1201@yahoo.com.hk> proto=SMTP helo=<**.**.**.11>
Dec  6 06:44:37 thegcs postfix/smtpd[10698]: lost connection after RCPT from 124-11-193-196.static.tfn.net.tw[124.11.193.196]
Dec  6 06:44:37 thegcs postfix/smtpd[10698]: disconnect from 124-11-193-196.static.tfn.net.tw[124.11.193.196]
Dec  6 06:47:57 thegcs postfix/anvil[10700]: statistics: max connection rate 1/60s for (smtp:124.11.193.196) at Dec  6 06:44:36
Dec  6 06:47:57 thegcs postfix/anvil[10700]: statistics: max connection count 1 for (smtp:124.11.193.196) at Dec  6 06:44:36
Dec  6 06:47:57 thegcs postfix/anvil[10700]: statistics: max cache size 1 at Dec  6 06:44:36


It looks to me as if someone is trying to use my email server to send spam. Am I understanding it correctly?

If so, can I assume that it succeeded in refusing it and my sever is 'safe'?

---

### Post by wkitty42 on 2008-12-06
> **Twizzle said:**
> I have set up a simple home server for storage and email and have just notice the following in my mail.log:



It looks to me as if someone is trying to use my email server to send spam. Am I understanding it correctly?

If so, can I assume that it succeeded in refusing it and my sever is 'safe'?

i've seen pretty much this same type of thing on my protected mail server... the same sending address as well as the same sending machine... my system, though, is protected by a smoothwall express 3.0 firewall with the SEMF (Smoothwall Express Mail Filter) mod which does a lot of stuff to protect the mail server sitting behind the smoothwall...

as for safe? i, personally, don't know but it does look like it thwarted that particular attempt ;)

FWIW: it wasn't a "hack" attempt either... it was simply an attempt to use your system as a relay :?

---

### Post by Twizzle on 2008-12-06
> **wkitty42 said:**
> 
FWIW: it wasn't a "hack" attempt either... it was simply an attempt to use your system as a relay :?

I will get there in the end with all the terminology! :D

Thanks for the post though - I was getting ready to pull the plug on the server just in case!

---

