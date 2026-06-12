---
title: "Postfix spam 'from' address query"
date: 2011-05-17
forum: Server Platforms
---

### Post by ajmak on 2011-05-17
Hi Guys,

Very new to Ubuntu and Linux so this may be a simple one.

I've recently setup an Ubuntu Server 10.04 box as a mail relay running Postfix and Amavisd-new (Spamassassin & ClamAV) and this has been working really well.  I started to get a few emails through today with the following header

From: <"Socorro Stallings"@Ubuntu-MailRelay.xxxxx.co.uk>, <Marva@ctrip.com>
(removed domain name)

The name's always in quotes and random.  The fqdn is that which I configured in postfix as $myhostname.

I can't figure out how this address is being used.  This box is only used for incoming mail and acts as a relay to Exchange.  Exchange doesn't send out through it.  The only thing that may be going outwards is bounced messages from Exchange which are almost exclusively to linkedin.

The fqdn isn't public.  This box isn't even part of our internal domain, it's just named that way with manual DNS added.

Anyone seen this before?  Will this header have been part of the message when it arrives at postfix or could this have been added by postfix itself?

Thanks,

---

### Post by elico on 2011-05-18
in the logs or actually in the mail you are getting?

---

### Post by ajmak on 2011-05-18
> **elico said:**
> in the logs or actually in the mail you are getting?

Thanks for the reply.

The quote above is directly off the mail headers.  I actually didn't think to check the mail log...

So, I grepped the mail log for the ESMTP id in the head and got the following.

```
/var/log/mail.log.0:May 17 09:08:25 Ubuntu-MailRelay postfix/smtpd[29549]: 113C01C15CA: client=localhost[127.0.0.1]
/var/log/mail.log.0:May 17 09:08:25 Ubuntu-MailRelay postfix/cleanup[29539]: 113C01C15CA: message-id=<B185066E067C4DC0EF3BD0941CA2E03F@ctrip.com>
/var/log/mail.log.0:May 17 09:08:25 Ubuntu-MailRelay postfix/qmgr[21997]: 113C01C15CA: from=<Dean@ctrip.com>, size=12174, nrcpt=1 (queue active)
/var/log/mail.log.0:May 17 09:08:25 Ubuntu-MailRelay amavis[29593]: (29593-02) Passed SPAMMY, LOCAL [xx.xx.xx.xx] [xx.xx.xx.xx] <Dean@ctrip.com> -> <xx@xx.xx>, Message-ID: <B185066E067C4DC0EF3BD0941CA2E03F@ctrip.com>, mail_id: RpeiOaTBHqWF, Hits: 9.503, size: 11335, queued_as: 113C01C15CA, 6387 ms
/var/log/mail.log.0:May 17 09:08:25 Ubuntu-MailRelay postfix/smtp[29542]: ABBB21C15C9: to=<xx@xx.xx>, relay=127.0.0.1[127.0.0.1]:10024, delay=6.4, delays=0.01/0/0.02/6.4, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=29593-02, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 113C01C15CA)
/var/log/mail.log.0:May 17 09:08:25 Ubuntu-MailRelay postfix/smtp[29551]: 113C01C15CA: to=<xx@xx.xx>, relay=xx.xx.xx.xx[10.0.0.8]:25, delay=0.87, delays=0.01/0.02/0.08/0.75, dsn=2.6.0, status=sent (250 2.6.0 <B185066E067C4DC0EF3BD0941CA2E03F@ctrip.com> [InternalId=47014] Queued mail for delivery)
/var/log/mail.log.0:May 17 09:08:25 Ubuntu-MailRelay postfix/qmgr[21997]: 113C01C15CA: removed

```

As you can see, the from address here is completely different which probably answers my original question in that I now don't think the $myhostname of this box has somehow become public.  I'm not sure why the from address would show up completely different when it eventually hits Outlook though?  

The from address shows up as (including quotes but with correct fqdn of $myhostname):

```
"Socorro Stallings"@Ubuntu-MailRelay.xx.xx
```

A grep for Socorro doesn't find any results in the mail log.  My best guess is that there's something in the mail that sets the from address as being 'Socorro Stallings' and postfix is appending the $myhostname variable to it to complete an address.  Is this likely/possible?

---

