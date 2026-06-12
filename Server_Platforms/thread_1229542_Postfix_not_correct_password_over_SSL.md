---
title: "Postfix not correct password over SSL"
date: 2009-08-02
forum: Server Platforms
---

### Post by artheus on 2009-08-02
Hi!

I'm trying to run SSL on my postfix smtp server, which I have big-time problems configuring!

When I try to connect to the smtp on my server, through thunderbird, I get a request for a password. And when I enter the password of the user, It doesn't work. It just requests authentication by password one more time. And I know I am entering the correct password.

doesn't the postfix authentication take the password and username from the standard user list?
If it doesn't, how can I configure it to do that, or how can I configure the users, and user passwords in Postfix?

I really don't get how the configuration of the postfix smtp is done.. Even if I read all over, and use guides..
I've set up the listening ports to 2525 in master.cf and I've set up all the important stuff in main.cf, like relayhost, etc..

I've opened the needed ports in the firewall configuration..
But no mail gets sent, even if I use TLS or no security at all..

Could someone please help me to configure this properly, so that I can send mail with my server, through either using an email client like Thunderbird, or usin the mail() in php.

Cheers,
Artheus

---

### Post by artheus on 2009-08-02
Well.. I've found out that my SMTP is actually working properly, when it sends mail to a gmail account.. But the problem is in my IMAP server, which won't recieve the mail I send to it.. So I'll make a new thread about this problem...

Cheers,
Artheus

here's the new thread
[http://ubuntuforums.org/showthread.php?p=7721271#post7721271](http://ubuntuforums.org/showthread.php?p=7721271#post7721271)

---

