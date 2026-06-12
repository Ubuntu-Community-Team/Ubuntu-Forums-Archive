---
title: "Help setting up Dovecot."
date: 2011-07-30
forum: Server Platforms
---

### Post by Thermolance on 2011-07-30
Today is my first day using Ubuntu. I am trying to see how easy it is to establish a server on it as I am considering giving it a try.

I installed Dovecot.

After installation was complete, I was not given any information such as how to configuration it or anything, so I am assuming it does not need any configuring.

I cannot see it listed anywhere in the menu's.

I have confirmed the service is running via bash.

I've tried to login via IMAP with my UNIX system account and password:

Connect: 10.1.1.3
Username: name
Password: ********

Connect: 10.1.1.3
Username: name@10.1.1.3
Password: ********

Connect: 10.1.1.3
Username: name@localhost
Password: ********

After performing each of these login combination, my mail client tells me the server has gone down.

Whats up with this junk software? Is it really this difficult to do something on Ubuntu?

---

### Post by kgatan on 2011-07-30
You need to be more patient or you will strugle with ubuntu. 

Link below is a mail server guide for ubuntu using diffrent kinds of software, including dovecot,
[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

---

### Post by kwamaking on 2011-07-30
I will tell you from my experience you will need massive amounts of patience.  Make sure to follow directions step by step. 

Setting up Dovecot and postfix wasn't nearly as difficult for me is getting PAM/SASL authentication done. 

One thing I highly HIGHLY recommend with your mail server is to disable the ability for open relay.  Otherwise you will quickly come to find your server's ip will be added to many different spam filters, and blacklisted by many websites because anyone can send mail as anyone from your server. 

Regards,

---

