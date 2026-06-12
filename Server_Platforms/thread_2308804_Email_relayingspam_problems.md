---
title: "Email relaying/spam problems"
date: 2016-01-05
forum: Server Platforms
---

### Post by musicweb on 2016-01-05
Having problems with other people using our server to send spam to others.
They are using one of our users emails as the "from", and it gets sent through
our ISP. Each time they use different IPs. 
How can we stop this? We would pay for someone to help with our
Postfix configuration if necessary.
We are running Ubuntu 14.04 server.
Here is a portion of our mail log.

```
Jan  5 16:49:07 wmmw postfix/smtpd[13110]: connect from 212095007065.public.telering.at[212.95.7.65]
Jan  5 16:49:17 wmmw postfix/smtpd[13110]: 680141B80946: client=212095007065.public.telering.at[212.95.7.65], sasl_method=LOGIN, sasl_username=michel.grenier
Jan  5 16:49:22 wmmw postfix/cleanup[13117]: 680141B80946: message-id=<060df70a.7c5fd3ee4848ca49@Nici1959>
Jan  5 16:49:22 wmmw postfix/qmgr[12527]: 680141B80946: from=<michel.grenier@wm-mw.org>, size=2827, nrcpt=1 (queue active)
Jan  5 16:49:23 wmmw postfix/smtp[13118]: 680141B80946: to=<frankglaesner69@web.de>, relay=smtp.radioactif.ca[24.226.191.39]:25, delay=8.5, delays=7.7/0/0.52/0.23, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 383931CCA69)
Jan  5 16:49:23 wmmw postfix/qmgr[12527]: 680141B80946: removed
Jan  5 16:49:25 wmmw postfix/smtpd[13110]: disconnect from 212095007065.public.telering.at[212.95.7.65]
Jan  5 17:16:55 wmmw postfix/smtpd[13534]: connect from dslb-094-221-232-248.094.221.pools.vodafone-ip.de[94.221.232.248]
Jan  5 17:17:05 wmmw postfix/smtpd[13534]: E23CC1B8074F: client=dslb-094-221-232-248.094.221.pools.vodafone-ip.de[94.221.232.248], sasl_method=LOGIN, sasl_username=michel.grenier
Jan  5 17:17:10 wmmw postfix/cleanup[13545]: E23CC1B8074F: message-id=<b5edbdce.afdd774cf9ab46b8@Lenovo-PC>
Jan  5 17:17:10 wmmw postfix/qmgr[12527]: E23CC1B8074F: from=<michel.grenier@wm-mw.org>, size=2873, nrcpt=1 (queue active)
Jan  5 17:17:11 wmmw postfix/smtp[13546]: E23CC1B8074F: to=<muh.hellmann@snafu.de>, relay=smtp.radioactif.ca[24.226.191.39]:25, delay=7.7, delays=7.2/0/0.35/0.21, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as ED2C91CCB94)
Jan  5 17:17:11 wmmw postfix/qmgr[12527]: E23CC1B8074F: removed

```

---

### Post by lisati on 2016-01-05
When I was running a postfix server a few years ago, the following helped avoid my server being used as an open relay:

```
smtpd_recipient_restrictions =

    reject_invalid_hostname, 
    reject_non_fqdn_sender, 
    reject_non_fqdn_recipient, 
    reject_unknown_sender_domain, 
    reject_unknown_recipient_domain, 
    reject_unauth_pipelining, 
    permit_mynetworks, 
    reject_unauth_destination, 
    
...
(other tests)
....

    permit

```

---

### Post by musicweb on 2016-01-05
So I should add these lines to my main.cf file?

---

### Post by lisati on 2016-01-05
> **musicweb said:**
> So I should add these lines to my main.cf file?

If you want. :D My example is based on one given on the [SpamCop]("https://www.spamcop.net/fom-serve/cache/349.html") pages.

---

### Post by musicweb on 2016-01-05
I added the options that were missing (a few of them were there)
and now I get this in the logs. Hopefully it means the emails are not
going to our ISP.... ?

```
Jan  5 18:21:10 wmmw postfix/smtpd[16928]: connect from b2b-130-180-33-2.unitymedia.biz[130.180.33.2]
Jan  5 18:21:11 wmmw postfix/smtpd[16931]: connect from ip-109-91-181-221.hsi12.unitymediagroup.de[109.91.181.221]
Jan  5 18:21:21 wmmw postfix/smtpd[16931]: NOQUEUE: reject: RCPT from ip-109-91-181-221.hsi12.unitymediagroup.de[109.91.181.221]: 554 5.7.1 <jessicawoetke@gmail.com>: Relay access denied; from=<michel.grenier@wm-mw.org> to=<jessicawoetke@gmail.com> proto=ESMTP helo=<ZI32-01>
Jan  5 18:21:21 wmmw postfix/smtpd[16928]: NOQUEUE: reject: RCPT from b2b-130-180-33-2.unitymedia.biz[130.180.33.2]: 554 5.7.1 <elke.henniger-rogas@e-mailforum.de>: Relay access denied; from=<michel.grenier@wm-mw.org> to=<elke.henniger-rogas@e-mailforum.de> proto=ESMTP helo=<win81-voss>
Jan  5 18:21:23 wmmw postfix/smtpd[16931]: lost connection after RCPT from ip-109-91-181-221.hsi12.unitymediagroup.de[109.91.181.221]
Jan  5 18:21:23 wmmw postfix/smtpd[16931]: disconnect from ip-109-91-181-221.hsi12.unitymediagroup.de[109.91.181.221]
Jan  5 18:21:23 wmmw postfix/smtpd[16928]: lost connection after RCPT from b2b-130-180-33-2.unitymedia.biz[130.180.33.2]
Jan  5 18:21:23 wmmw postfix/smtpd[16928]: disconnect from b2b-130-180-33-2.unitymedia.biz[130.180.33.2]
```

---

### Post by SeijiSensei on 2016-01-06
It's hard to stop people from spamming using forged messages with legitimate names in the From: field.  You really only have a few options:

1)  Close the account and issue the real user a different name.
2)  Use passwords or certificates to connect to the SMTP service.
3)  Block by domain.  In your case I'd disallow anything from servers with "unitymedia" in their domain names.

In postfix, I use the "smtpd_client_restrictions," "smtpd_sender_restrictions," and "smtpd_helo_restrictions" directives to control access with "Perl-compatible regular expressions."  In your case I'd add this to /etc/postfix/main.cf:
```
smtpd_helo_restrictions = check_helo_access pcre:/etc/postfix/helo_access
```
Then in the helo_access file you would add the rule:
```
/unitymedia/     REJECT
```

I recommend reading [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html).  It takes a couple of readings to understand the entire range of access controls Postfix offers. I would read this before implementing the array of controls lisati proposes since your needs may be different.

As an ISP, are you assigning your customers IP addresses?  If so, I'd consider having two servers, one for inbound mail with many restrictions, and one for your customers that only accepts outbound messages from the IP addresses you provide.  For instance, at one client site, we only allow mail with addresses in the client's domain if it comes from machines on the client's office network.  Since they use MS Exchange, we only allow the organizations' users to send mail from outside through Outlook Web Access.

---

