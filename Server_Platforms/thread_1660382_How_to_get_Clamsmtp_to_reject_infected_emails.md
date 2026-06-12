---
title: "How to get Clamsmtp to reject infected emails"
date: 2011-01-05
forum: Server Platforms
---

### Post by minhnghivn on 2011-01-05
I've configured Clamsmtp to work with Postfix and things work smoothly. That is, emails with virus are automatically dropped by Clamsmtp.

But I'm trying to get Clamsmtp to REJECT infected emails instead of DROPing them

In the /etc/clamsmtpd.conf (man clamsmtpd.conf) I found an parameter ACTION which takes the value of BOUNCE, DROP, PASS... But there is no REJECT option!

Any help is highly appreciated

---

### Post by kidders on 2011-01-06
Hi there,

The presence of a REJECT action would suggest server admins might want clients to remain connected to their servers while mail was scanned. That would be a _really_ bad idea ... Not something you should even try. The closest you can safely get (in terms of the end user's experience) is to bounce infected messages. It'd be a good idea to clean them first though, in case you get blacklisted for sending viruses.

I hope that helps.

---

### Post by minhnghivn on 2011-01-07
Thank you kidders for your explanation.

Keeping the connection alive while scanning is in progress is not a good choice. However, I would like to notice the sender, immediately, that his/her attachment is infected. This is a good option over BOUNCING the message or silently DROPPING it. 

Can I achieve this (any way) with ClamSMTP ?

---

### Post by kidders on 2011-01-07
Hey again,

"Immediately" is a subjective term, I suppose. Bouncing the message would result in *fairly* immediate notification of a delivery failure (generally a matter of seconds), but relies on the sender checking his mail to see the error. Without maintaining an open SMTP connection for the duration of the virus scan, nothing more immediate than that is possible.

That constraint isn't peculiar to clamsmtp though ... Complex post-processing of email messages for whatever reason (whether virus/spam related or not) is always done asynchronously, for performance/stability reasons. In other words, servers always accept, post-process and *then* reject (ie bounce) email they are not willing to deliver.

Architecturally, this process is normally implemented using two MTAs ...[LIST]
[*]One is exposed to the internet, and does little or no post-processing of messages, so it's capable of accepting incoming mail at a reasonable rate.
[*]The second is responsible for virus scans or other labour-intensive work, so it can't handle mail at anything like the same pace. In theory, messages may stack up for several minutes, waiting to be delivered.
[/LIST]
By the time clamscan gets to look at an incoming message, the original sender is long gone, so there'll always be a short delay between transmission of an infected email & receipt of a delivery failure notice. :-(

---

### Post by minhnghivn on 2011-01-22
Finally I decided to silently remove infected mails. This seems to be the most suitable solution. thank you very much kidders

---

### Post by SeijiSensei on 2011-01-22
> **minhnghivn said:**
> However, I would like to notice the sender, immediately, that his/her attachment is infected.

No, you don't.  Most virus-infected messages are sent by malware running on infected desktops.  There's no one on the other end to receive your notice.

A more plausible concern is mail sent from people within your network.  However, again, I'd argue it's more important in this case to bounce the virus notice to an administrator so they can fix the infected machine.

I use [MailScanner]("http://www.mailscanner.info/") which enables quite fine-grained control over what kinds of notifications are sent.  I only notify senders if an attachment is blocked, since many MS Word users send around documents with macro viruses.  Any other virus is just silently dropped, though notices are sent to the intended recipient and the administrator just in case it was blocked in error.

---

### Post by minhnghivn on 2011-03-13
Nice explanation, thank you SeijiSensei!

---

### Post by tavasti on 2012-04-24
If you really want clamsmtpd check messages during smtp connection, it is possible. 
Configure clamsmtpd as smtpd_proxy_filter in postfix and set in clamsmtpd.conf 'Action: bounce'.

Althou it says 'bounce' it is really answering to smtp connection '550 Virus Detected; Content Rejected'

---

