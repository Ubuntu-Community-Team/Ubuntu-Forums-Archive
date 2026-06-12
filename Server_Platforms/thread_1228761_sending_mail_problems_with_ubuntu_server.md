---
title: "sending mail problems with ubuntu server"
date: 2009-08-01
forum: Server Platforms
---

### Post by benfindlay on 2009-08-01
I have an Ubuntu 8.04 webserver running, with the webmin install script to set up virtual servers etc.

I have been trying to get the mail part of the server to work. I can send and receive mail fine if I log in via the usermin web interface, but am having problems with getting a mail client to send mail. Receiving mail is fine. I have tried both Outlook Express and Thunderbird.

I get the following error: > Sending of message failed
The message could not be sent because connecting to the SMTP server [myaddress] failed. The server may be unavailable or is refusing SMTP connections. Please verify that your SMTP server setting is correct and try again, or else contact your network administrator
Any ideas?

Thanks,

Ben

---

### Post by HermanAB on 2009-08-01
Howdy,

You don't say what mail server you are using and it sounds like it is the first time you are trying to get one to work, so it is probably Postfix.  The way to get Postfix to work is to mozy over to the Postfix web site and start reading and in two weeks or so, you should have it working.

If you want to learn about mail servers, then installing Postfix is a good idea.  However, if you just want to get the mail to work with a minimal amount of hassle, then I suggest that you install Citadel - it takes about 20 minutes - honest!

[http://www.citadel.org](http://www.citadel.org)

---

### Post by kustomjs on 2009-08-01
you could get postfix+dovecot+mysql to work under 10mins.

---

### Post by benfindlay on 2009-08-10
Hi there, yes I am using postfix and dovecot. They were installed using the webmin installation script for getting webmin/virtualmin installed on ubuntu.

Is this parhaps an authentication error, as I find it odd that I can connect through usermin via a browser, and that I can receive using thunderbird, but not send?

Thanks

Ben

---

