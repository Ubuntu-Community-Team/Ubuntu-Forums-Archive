---
title: "Postfix/SMTPD error"
date: 2008-10-26
forum: Server Platforms
---

### Post by DjDarkman on 2008-10-26
I have been trying to configure a mail server, with the help of this [https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto) tutorial, but smtp authentification doesn't work and in the log I found this:

Oct 26 14:29:07 vector postfix/smtpd[7509]: fatal: need service transport:endpoint instead of "inet"
Oct 26 14:29:08 vector postfix/master[7007]: warning: process /usr/lib/postfix/smtpd pid 7509 exit status 1
Oct 26 14:29:08 vector postfix/master[7007]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Oct 26 14:30:08 vector postfix/smtpd[7511]: fatal: need service transport:endpoint instead of "inet"
Oct 26 14:30:09 vector postfix/master[7007]: warning: process /usr/lib/postfix/smtpd pid 7511 exit status 1
Oct 26 14:30:09 vector postfix/master[7007]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling


I have tried googling for this *need service transport:endpoint instead of "inet"* but no luck, can someone help me out with this issue?

---

### Post by MJN on 2008-10-26
Having had a quick scan through that HowTo I can confirm it has an error in it. Specifically, the SMTPD restrictions line:

```
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, **check_policy_service,inet**
```The check_policy_service syntax is to refer to a defined socket e.g. inet:127.0.0.1:1000 being a service listening on the local machine.

However, it looks like the HowTo has either been edited by someone that doesn't understand what's going on or has yet to be finished. The bottom of the page suggests it's the latter...

Mathew

---

### Post by DjDarkman on 2008-10-26
> **MJN said:**
> Having had a quick scan through that HowTo I can confirm it has an error in it. Specifically, the SMTPD restrictions line:

```
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, **check_policy_service,inet**
```The check_policy_service syntax is to refer to a defined socket e.g. inet:127.0.0.1:1000 being a service listening on the local machine.

However, it looks like the HowTo has either been edited by someone that doesn't understand what's going on or has yet to be finished. The bottom of the page suggests it's the latter...

Mathew

Thanks, but what should I do? is there a good tutorial? 

I just need to set up a mail server that can be managable from a database, we want to host websites and give clients email addresses, that's why we need this.

I would really apreciate any help on this.

---

### Post by MJN on 2008-10-26
I cannot recommend one as I learnt and developed mine from scratch.

I'm sure someone else can suggest a good walkthrough guide that they've used though.

Mathew

---

### Post by VorDesigns on 2009-02-24
Apparently not and had I know the document wss valid, I wouldn't have wasted the time  building it this way.
Now I have hours of unexpected troubleshooting.

---

### Post by speeddemon92 on 2009-06-18
you guys were on to something just remove inet from smtpd_recipient_restrictions making the line:

```
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, check_policy_service
```

---

### Post by HermanAB on 2009-06-18
Use Citadel.  You can  install it in about 20 minutes and it uses Oracle BerkeleyDB as its backend.  It can handle tens of thousands of users.

---

