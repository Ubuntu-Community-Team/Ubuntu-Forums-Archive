---
title: "Stop Postfix auto-appending www-data"
date: 2018-05-07
forum: Server Platforms
---

### Post by achillingsight on 2018-05-07
Hello,
I'm trying to figure out how to stop Postfix from auto-appending www-data to my out going mail function in PHP. What's happening is Postfix is changing my from header (which is specified in PHP) from [email]account@domain.com[/email] to [email]www-data@account@domain.com[/email]. I believe that is the reason that GMail (and a few other hosts) are preventing the e-mail being received to the user.

I've checked the mail logs and according to them the mail is sent successfully, again, suggesting that GMail (or who ever) is rejecting the mail and not an issue with how I have the SMTP setup. I've got Postfix configured properly to connect and send mail through the SMTP server my company uses and that works fine. I also know my mail() script works, as it sends when I send to other e-mail (not GMail for example) and when I test on another server.

So end of story, how do I stop Postfix from auto appending www-data@ to my from field when using the PHP Mail function? I found one post on here that said to add an alias but the person who posted that said it was for sendmail, not Postfix, also it was server version 12, not 16 (I haven't updated to 18).

Thanks,
Dustin

---

### Post by SeijiSensei on 2018-05-08
The web server user, www-data, owns the Apache process sending the mail.  By default the "envelope sender," the address sent during the SMTP exchange, will be [email]www-data@host.domain.name[/email].  (This address can be, and often is, entirely different from the entry in the From: header in the message itself.)  To change the envelope sender, follow the procedure here: [https://serverfault.com/questions/533912/how-do-i-change-the-envelope-from-in-postfix](https://serverfault.com/questions/533912/how-do-i-change-the-envelope-from-in-postfix)

---

### Post by achillingsight on 2018-05-09
That worked perfectly! Thank you very much!

---

