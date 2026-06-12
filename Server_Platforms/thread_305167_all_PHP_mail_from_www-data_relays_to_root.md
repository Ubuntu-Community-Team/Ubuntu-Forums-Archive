---
title: "all PHP mail from www-data relays to root"
date: 2006-11-22
forum: Server Platforms
---

### Post by XeviouS on 2006-11-22
OK this problem has me pulling my hair out!!

I have just built an Ubuntu 6.10 LAMP server. It has postfix intalled and I can send mail from the command line without issue.

I have also tried this with sendmail and get the exact same problem.

Any emails sent from a PHP script will send sucessfully...and will return TRUE.

However the mail gets delievered to the root account and not to the intended recipient.

Any ideas?

---

### Post by MJN on 2006-11-23
Post your script and mail log files (/var/log/mail.log) so we can see what's what.

Mathew

---

### Post by XeviouS on 2006-11-24
I removed postfix and sendmail and installed EXIM and my PHP mail is now working. 

Thanks anyway!

---

