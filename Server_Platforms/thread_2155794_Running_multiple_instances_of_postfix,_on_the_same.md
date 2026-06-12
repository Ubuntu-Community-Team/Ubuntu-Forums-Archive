---
title: "Running multiple instances of postfix, on the same port"
date: 2013-06-19
forum: Server Platforms
---

### Post by insidus on 2013-06-19
Hey,

I've run into a problem. I need to setup an email server (Postfix and Dovecot) to send both authenticated and unauthenticated emails, which probably uses two instances of postfix.

I need one instance to send all emails using an authenticated email address using dovecot (which is setup and working) and to be able to check the "from" field, to make sure that is also valid. (It is possible to spoof the from field when sending an email)
The other instance i need to be able to accept all emails comming from IP 192.168.10.246, unauthorised (Using a VOIP phone system to send voicemails to user accounts which doesn't support user acocunts/passwords to login), which needs to be able to forwards the emails to the correct clients email.

I'm using Ubuntu 12.04, running Postfix and Dovecot. I used this guide to set up Vmail and accounts for Dovecot : [https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto) 

If you need any config information then please let me know, any help is always appreciated!

/Insidus

---

