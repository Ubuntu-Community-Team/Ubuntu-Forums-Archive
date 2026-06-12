---
title: "Using the mailx in the Terminal to send Email."
date: 2011-06-15
forum: Server Platforms
---

### Post by jairomarcel on 2011-06-15
I've searched in many tutorials about how to configure the mailx to send emails by command line but I didn't found nothing that could correct this problem.

This is what happen when I try to send a simple email:

[I]$ ls -lh | mail -s "List Email" [email]jairomarcel@gmail.com[/email]
send-mail: a conta default não foi encontrada em /home/jairo/.msmtprc
Can't send mail: sendmail process failed with error code 78[/I]

What can I do to resolve this?

Thanks,

Jairo. ;)

---

### Post by howefield on 2011-06-16
Thread moved from "*Tutorials and Tips*" to "*Server Platforms*"

---

### Post by SeijiSensei on 2011-06-16
You also need an SMTP server.  Run "sudo apt-get install postfix" and try sending from the command line again.

If you have postfix or sendmail installed already, take a look in /var/log/mail.log to see what errors were generated.

---

