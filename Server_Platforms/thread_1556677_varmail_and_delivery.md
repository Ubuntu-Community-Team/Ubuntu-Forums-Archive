---
title: "/var/mail and delivery"
date: 2010-08-19
forum: Server Platforms
---

### Post by Platonov on 2010-08-19
Hi,

I'm having some problems with my e-mail setup. The last couple of months/years I have been using my own mailserver, which works out perfectly fine. I check my e-mail only on the server with (al)pine. There has never been a need to install fetchmail, pine moves the messages automatically to my local mailfolder on startup or when running.
```
   moved ... bytes of new mail to /home/user/mbox from /var/mail/user
```
Today I have installed Dovecot, in order to have POP3-access from other PC's. The access is no problem (I can retrieve messages with the other clients), but *only* when alpine is not running on the local server. Because alpine *re*moves the messages from /var/mail/user, and puts them in /home/user/mbox, whereas the external clients just leave the messages on the server.

I would like to keep using the alpine program on the server too, besides the external clients. I think it could be solved with fetchmail on the local server, and instructing alpine not to retrieve any messages but to leave that up to fetchmail.

My question is... how? I see in htop that sendmail is running as well as postfix. Is it possible that postfix is removing the mail from /var/mail/user when alpine is running?

---

### Post by Platonov on 2010-08-19
There was an mbox file in my /home/user-folder, which caused alpine to move mail from /var/mail/user to /home/user. Deleting the mbox file solved the problem.

---

