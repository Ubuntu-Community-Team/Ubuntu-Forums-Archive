---
title: "Postfix/Dovecot/POP and SMTP"
date: 2009-11-03
forum: Server Platforms
---

### Post by HuXu on 2009-11-03
Ok so I followed [https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer) to the T setting it up as I went along and things seem to work just fine BUT when i try to setup the email account with evolution I get

Unable to connect to POP server mail.mydomain.com.
Error sending password: Resource temporarily unavailable

The steps I took when setting it up were all the way through everything to just do a POP3 and SMTP server using TLS (I need to figure out how to do SSL because Outlook isnt compatible with TLS) and I did it how the instructions said to do.  

Anyone know what the problem is?  I had set it on PLAIN for SMTP but then changed it to Login because I am having it be just my system users and using shadow.

---

### Post by druhboruch on 2009-11-03
> **HuXu said:**
> Ok so I followed [https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer) to the T setting it up as I went along and things seem to work just fine BUT when i try to setup the email account with evolution I get

Unable to connect to POP server mail.mydomain.com.
Error sending password: Resource temporarily unavailable

The steps I took when setting it up were all the way through everything to just do a POP3 and SMTP server using TLS (I need to figure out how to do SSL because Outlook isnt compatible with TLS) and I did it how the instructions said to do.  

Anyone know what the problem is?  I had set it on PLAIN for SMTP but then changed it to Login because I am having it be just my system users and using shadow.

This how to worked great for me:

[http://craigballinger.com/blog/2009/07/postfix-dovecot-mailserver-on-ubuntu-904-jaunty-jackalope/](http://craigballinger.com/blog/2009/07/postfix-dovecot-mailserver-on-ubuntu-904-jaunty-jackalope/)

It is for Jaunty, but it works just great with Karmic

---

### Post by HuXu on 2009-11-04
Thanks! I think that fixed my problem!

But now I'm on a blacklist but I am working with Verizon to remove that.  But I do have another problem.  In my mail log went I try to send mail to a user I see this "...Maildir/cur) failed: Permission denied" who/what group should own the Maildir and its contents?

[EDIT]

I simply google searched it and found that you do "chown username /home/username/Maildir /home/username/Maildir/cur /home/username/Maildir/new /home/username/Maildir/tmp"

---

