---
title: "[postfix] Sent email returns to inbox"
date: 2011-01-27
forum: Server Platforms
---

### Post by DarkRanger on 2011-01-27
Hi all,

I have an issue here. I'm running ubuntu 10.04 as a server that hosts a website and our email. I set up the email (Postfix) to work with Dovecot to enable IMAP and POP support.

The mails can be retrieved and sent through this server with no hassles. We just have an issue that all emails sent via a client to any other address (be it on the same domain or not) will return to the inbox of that client.

So basically, I open MS Outlook. Click new message and send it off to my GMail address. After I send it, it pops into my inbox on Outlook (stating that it came from me). The intended recipient also gets the message.

Any ideas?

---

### Post by prshah on 2011-01-27
> **DarkRanger said:**
> I set up the email (Postfix) to work with Dovecot to enable IMAP and POP support.

Click new message and send it off to my GMail address. After I send it, it pops into my inbox on Outlook

Have you also setup an smtp server or are you using GMail's SMTP server? If you are using Gmail's SMTP server, this is Gmail's default behaviour: ie, mail sent through gmail's smtp server via an email client will result in a copy of the mail in the INBOX of the gmail account used to send the mail.

If your gmail account is subsequently forwarding mail to your hosted email solution, you might be seeing this effect.

AFAIK, there is no way to "turn off" receiving inbox copies of sent email via gmail.

---

### Post by DarkRanger on 2011-01-27
It doesn't matter to which address I send it. The scenario was just an example.

We can send emails to ANYONE, it still pops up in our inbox.

---

