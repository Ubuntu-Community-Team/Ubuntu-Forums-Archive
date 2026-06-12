---
title: "A Mailserver on Ubuntu 16.04: Postfix, Dovecot, MySQL"
date: 2016-06-09
forum: Server Platforms
---

### Post by tresrob on 2016-06-09
Hello everyone
I installed a new mail server using Postfix, Dovecot and mysql for managing users.
Sending and receiving mail internally works fine.
I activated the email address rewriting because the mail is sent out.
But i have problem to send mail outside width specific  relayhost that requires to authenticate the user
I created a table in the database that contains user name and password, I tried to configure Dovecot but does not work.
In the previous version I used Cyrus SASL with sasl-passord.cf and main.cf I had indicated to aim this file, but now with dovecot and mysql do not know how to do.
Please can anyone help me thanks

---

