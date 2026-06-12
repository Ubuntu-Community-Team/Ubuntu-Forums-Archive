---
title: "Postfix relay problem"
date: 2011-01-12
forum: Server Platforms
---

### Post by tws on 2011-01-12
Hi there.

The scenario:
We have an external server that runs HTTP/DB servers for out shop system.
Then, there's our local, in-house infrastructure that runs a.. yeah... Exchange 2010.

The shop system on the external server needs to send mails to customers (order confirmations, invoices, etc.). seing as sending them directly through the local MTA (Postfix) would cause mail delivery problems because of reverse DNS issues, i've set the Postfix MTA to act as a satellite to our in-house Exchange Server, so the Exchange sends the mail instead, giving recipient mail servers a valid reverse DNS lookup.

Now, mails sent by the (proprietary, uneditable) shop system are relayed correctly and sent to the target e-mail address.
My problem is: Mails not sent by the shop system, but by our own PHP scripts which run on that same external servers, are NOT relayed properly.
So the Exchange is fine with the mails sent by the shop system, but not the mails sent by our scripts.

This is what i get in the mail.log:

The successfully relayed mail sent by the shop system:> Jan 12 16:10:42 appenzeller postfix/pickup[24729]: 95EFD2A22B7: uid=33 from=<www-data>
Jan 12 16:10:42 appenzeller postfix/cleanup[25330]: 95EFD2A22B7: message-id=<20110112151042.95EFD2A22B7@local.domain.tld>
Jan 12 16:10:42 appenzeller postfix/qmgr[24732]: 95EFD2A22B7: from=<www-data@local.domain.tld>, size=2482, nrcpt=1 (queue active)
Jan 12 16:10:44 appenzeller postfix/smtp[25267]: 95EFD2A22B7: to=<my.email@company.tld>, relay=external.mailserver.tld[1.2.3.4]:25, delay=2.3, delays=0.05/0/0.08/2.2, dsn=2.6.0, status=sent (250 2.6.0 <20110112151042.95EFD2A22B7@local.domain.tld> [InternalId=306220] Queued mail for delivery)
Jan 12 16:10:44 appenzeller postfix/qmgr[24732]: 95EFD2A22B7: removed

And here the unsuccessfully relayed mail sent by our scripts:> 
Jan 12 16:10:15 appenzeller postfix/pickup[24729]: BC9432A22B7: uid=33 from=<www-data>
Jan 12 16:10:15 appenzeller postfix/cleanup[25330]: BC9432A22B7: message-id=<20110112151015.BC9432A22B7@local.domain.tld>
Jan 12 16:10:15 appenzeller postfix/qmgr[24732]: BC9432A22B7: from=<www-data@local.domain.tld>, size=2057, nrcpt=1 (queue active)
Jan 12 16:10:15 appenzeller postfix/smtp[25267]: BC9432A22B7: to=<my.email@company.tld>, relay=external.mailserver.tld[1.2.3.4]:25, delay=0.16, delays=0.02/0/0.07/0.06, dsn=5.7.1, status=bounced (host external.mailserver.tld[1.2.3.4] said: 554 5.7.1 This message has been blocked because the return email domain is invalid.(domain name  [email]normal.email@company.tld[/email]   has invalid syntax) (in reply to end of DATA command))
Jan 12 16:10:15 appenzeller postfix/cleanup[25330]: E1D472A22BF: message-id=<20110112151015.E1D472A22BF@local.domain.tld>
Jan 12 16:10:15 appenzeller postfix/bounce[25268]: BC9432A22B7: sender non-delivery notification: E1D472A22BF
Jan 12 16:10:15 appenzeller postfix/qmgr[24732]: E1D472A22BF: from=<>, size=4271, nrcpt=1 (queue active)
Jan 12 16:10:15 appenzeller postfix/qmgr[24732]: BC9432A22B7: removed
Jan 12 16:10:21 appenzeller postfix/smtp[25267]: E1D472A22BF: to=<www-data@local.domain.tld>, relay=external.mailserver.tld[1.2.3.4]:25, delay=5.1, delays=0/0/0.07/5, dsn=5.7.1, status=bounced (host external.mailserver.tld[1.2.3.4] said: 550 5.7.1 Unable to relay (in reply to RCPT TO command))
Jan 12 16:10:26 appenzeller postfix/qmgr[24732]: E1D472A22BF: removed
external.mailserver.tld being our inhouse Exchange server, and [email]normal.email@company.tld[/email] being the From/Reply-To email address set in the PHP scripts.

I can't really know for certain what exactly the shop system does behind the scenes, but what i do know is that the PHP scripts send mail through the normal mail() function with the only extra headers being the From and Reply-To headers.

I tried google-ing for the error message, but all i get are a million entries for a million different problems than mine.

Any hints?

Thanks!

---

### Post by elico on 2011-01-12
well the anwser is in the text...
"Unable to relay (in reply to RCPT TO command))"
 said: 554 5.7.1 This message has been blocked because the return email domain is invalid.(domain name  [EMAIL="normal.email@company.tld"]normal.email@company.tld[/EMAIL]   has invalid syntax) 

either this domain is not FQDN and you can add his name to your hosts file to check \you local\internal DNS server\records.

---

### Post by elico on 2011-01-12
well the anwser is in the text...
"Unable to relay (in reply to RCPT TO command))"
 said: 554 5.7.1 This message has been blocked because the return email domain is invalid.(domain name  [EMAIL="normal.email@company.tld"]normal.email@company.tld[/EMAIL]   has invalid syntax) 

either this domain is not FQDN and you can add his name to your hosts file to check \you local\internal DNS server\records.

---

