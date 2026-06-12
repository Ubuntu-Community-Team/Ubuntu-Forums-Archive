---
title: "Postfix Hash Database and Email Password Files"
date: 2020-01-15
forum: Server Platforms
---

### Post by fangorn2 on 2020-01-15
Goodmorning to everybody,

I configured Postfix to send email using Gmail, as described in a [Linode documentation]("https://www.linode.com/docs/email/postfix/configure-postfix-to-send-mail-using-gmail-and-google-apps-on-debian-or-ubuntu/").
At the end, I created the /etc/postfix/sasl/sasl_passwd file and added the SMTP Host, username, and password information:

[smtp.gmail.com]:587 [EMAIL="username@gmail.com"]username@gmail.com[/EMAIL]: password


Then I created the hash db file for Postfix by running the postmap command:

$ sudo postmap /etc/postfix/sasl/sasl_passwd


This created the /etc/postfix/sasl/sasl_passwd.db file.
At this point I sent a test email but unfortunately it was rejected by Gmail.
Less secure apps are already allowed, so I tried to change the password for the Gmail account, as suggested at [Stackoverflow]("https://stackoverflow.com/a/44927470").
Now I suppose I have to create new /etc/postfix/sasl/sasl_passwd and /etc/postfix/sasl/sasl_passwd.db files.
Am I expected to delete these files, create a new /etc/postfix/sasl/sasl_passwd file and rerun sudo postmap /etc/postfix/sasl/sasl_passwd?

---

