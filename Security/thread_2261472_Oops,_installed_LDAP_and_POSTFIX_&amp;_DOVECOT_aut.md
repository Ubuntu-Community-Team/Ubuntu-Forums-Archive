---
title: "Oops, installed LDAP and POSTFIX &amp; DOVECOT authentification failure"
date: 2015-01-19
forum: Security
---

### Post by dannyboy79 on 2015-01-19
This may seem silly but I am at a loss here. (i realized after I submitted the thread that I am not sure about LDAP and whether or not I installed/enabled it) I am not sure what I did wrong to my server. I was following this guide [http://jonsview.com/how-to-setup-email-services-on-ubuntu-using-postfix-tlssasl-and-dovecot](http://jonsview.com/how-to-setup-email-services-on-ubuntu-using-postfix-tlssasl-and-dovecot) for turning my desktop into a mail server but now when I try to perform updates I am presented with a brand new authentification dialog that I've never seen before. At the same time I switched from Xubuntu to LXQT so that's maybe why I'm so confused. I have been using Ubuntu since 2005, the server has been a LAMP server since Ubuntu 10.04 but previously never had a need to mess with mail servers. Can anyone please tell me why when I enter my proper password for a particular user it fails to authenticate? Thank you
[IMG]https://lh3.googleusercontent.com/-1RVD0CHl3Bs/VLzpB1hLT7I/AAAAAAAADRU/7JVNrS7ZfrU/s798/auth_failure.png[/IMG]

---

### Post by TheFu on 2015-01-19
Of course, the first question is to ask what the log files show. So, what do the log files show?

BTW, you must to more than just install LDAP for it to work. I think there are at least 3 manual settings which must be changed in a config file for it to work at all from any client requesting authentication.  That means both postfix and dovecot will need these settings to connect to the LDAP datastore.

I prefer the how-to guides from howtoforge.com for this stuff. [https://www.howtoforge.com/postfix-virtual-hosting-with-ldap-backend-and-dovecot-imap-pop3-on-ubuntu-trusty-tahr-14.04](https://www.howtoforge.com/postfix-virtual-hosting-with-ldap-backend-and-dovecot-imap-pop3-on-ubuntu-trusty-tahr-14.04)  though I don't use dovecot myself anymore.

---

### Post by dannyboy79 on 2015-01-23
anyone that can help me with this would be much appreciated. thank you.

---

### Post by TheFu on 2015-01-23
Can't help if you don't answer the prior questions.

---

### Post by dannyboy79 on 2015-04-03
which log files do you want to see? i'm still getting the GUI message stating "Authorization failed for some reason". If i try to open synaptic or any app that requires me to enter my sudo password it brings up both the dialog boxes that i have previously posted. i get around the issue by just issueing gksudo synaptic from the terminal but i'd like to be able to use the GUI

---

