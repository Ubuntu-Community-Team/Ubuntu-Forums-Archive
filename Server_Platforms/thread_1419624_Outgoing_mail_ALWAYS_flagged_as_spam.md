---
title: "Outgoing mail ALWAYS flagged as spam"
date: 2010-03-02
forum: Server Platforms
---

### Post by Norami on 2010-03-02
I've got a web server that's hosting a few sites, and there are a few WordPress instances with these sites. With Wordpress, whenever a user registers with the site, they receive an email, blah de blah. I'm sure you know how all that works. With my server, it sends mail via Sendmail. This is all fine and good, except no matter what, it's flagged as spam. Is there any way to correct this?

Keep in mind that this isn't a mail server, and the only reason the server ever sends mail is for new wordpress users and password resets.

---

### Post by Bachstelze on 2010-03-02
If you have a dynamic IP, especially if you host this server at home,t hat's probably why. Otherwise, it could also be a misconfiguration on your part. If you want, you can send an email to [email]firas@fkraiem.org[/email], I'll see what SpamAssassin says about it.

---

### Post by Norami on 2010-03-02
The server has a static IP. I sent an e-mail to that address. It will be sent by [EMAIL="wordpress@criticallypretentious.com"]wordpress@criticallypretentious.com[/EMAIL]

I guess I should mention that the server runs on Ubuntu Server 9.10

---

### Post by Bachstelze on 2010-03-02
It is indeed misconfiguration on your part.

```
Mar  2 09:49:32 itsuki sm-mta[97930]: o229nWPD097930: ruleset=check_mail, arg1=<www-data@webhost>, relay=204-232-208-69.
static.cloud-ips.com [204.232.208.69], reject=553 5.1.8 <www-data@webhost>... Domain of sender address www-data@webhost
does not exist
```

Check your From: header.

---

### Post by Norami on 2010-03-02
This may sound stupid, but where do I check the From: header? Is it something set in the Sendmail configuration? if so, where might that be?

I figured it might be some sort of configuration error, I actually never configured anything with Sendmail. I just installed it through apt-get.

---

### Post by Bachstelze on 2010-03-02
> **Norami said:**
> This may sound stupid, but where do I check the From: header? Is it something set in the Sendmail configuration? if so, where might that be?

No, it is set by the program sending the mail. In your case, you should have something in the Wordpress admin panel to customize the sender address of confirmation emails.

---

### Post by Norami on 2010-03-02
Odd. In the WordPress CP, the field for the e-mail address to send from is a valid email address. But it still gets flagged as spam

---

### Post by Bachstelze on 2010-03-02
Try this script:

[php]<?php
$to      = 'firas@fkraiem.org';
$subject = 'the subject';
$message = 'hello';
$headers = 'From: webmaster@example.com';

mail($to, $subject, $message, $headers);
[/php]

Be sure to replace the [font=monospace]From:[/font] address with a valid one, save the script somewhere on your server and open it in your browser. Yes, it will just show a blank page, that's normal. ;)

---

### Post by Norami on 2010-03-02
Ok, I sent it.

---

