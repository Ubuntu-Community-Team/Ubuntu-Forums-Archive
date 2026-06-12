---
title: "local mail server help!"
date: 2009-02-12
forum: Server Platforms
---

### Post by 1106 on 2009-02-12
Hi,

I am one of the many new users of ubuntu/linux. Slowly learning bits and pieces and getting there slowly.

So far I have installed webmin on ubuntu 8.10 server edition (I haven't learn enough about the command line yet and want to try and get things running quite quickly so gui is a bit easier for me at this stage.)

I want to set up a local mail server that collects mail from my isp server, store it locally on the mail server then connect to it from various workstations (I will be using IMAP). Eventually I will want to access this mail remotely but I will address this at another date! 

So far I have set-up fetchmail, postfix and dovecot. The fetchmail successfully connects to the isp server brings the mail down and stores it locally. I can see the mail buy clicking 'read user mail' in webmin control panel - I can click on the webmin user and see the mail sat there ( var/mail/webminuser). I am then stuck as to what else I need to configure inorder to use my mail client to connect to the local mail server and collect the mail. 

Also I have been considering just installing citadel as it seems to support everything I eventually want to have (shared calendering etc). But I have already got this far (huge learning curves even for the basics) so I'd like to stick with it.

Any help would be greatly appreciated!!

Many thanks,

Leanne

---

### Post by etali on 2009-02-12
Dovecot handles the imap / pop3 connections:

The default is for dovecot to use the linux user IDs for authentication.  If you don't want to have a user for each email address, then you could set up a list of users and mailboxes.

This may be useful:

[http://www.debuntu.org/how-to-virtual-emails-accounts-with-postfix-and-dovecot](http://www.debuntu.org/how-to-virtual-emails-accounts-with-postfix-and-dovecot)

---

