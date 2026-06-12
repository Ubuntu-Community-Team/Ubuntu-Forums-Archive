---
title: "/usr/bin/mail: sending mail through Google"
date: 2014-07-30
forum: Server Platforms
---

### Post by smeerbartje on 2014-07-30
I'm using a Ubuntu 14.04.1 server which does some tasks, f.e. SSH, LAMP, RSS aggegration, etc. I have scripted some bash files which help me in cleaning up stuff on the server. The server is NOT running a mail server and now I want to use the bash command "/usr/bin/mail" from within bash scripts. How can I do this? I simply want to SEND mail, I don't want the server to be able to RECEIVE mails. Also I have a Google apps account, so if it's possible to configure the /usr/bin/mail command in a way to it is using hte Google smtp servers, that would be great. So what is the most minimal way to configure this without having to install mail servers on the server?

---

### Post by thufirhawat2 on 2014-07-30
[https://wiki.debian.org/sSMTP](https://wiki.debian.org/sSMTP)

I use SSMTP for things like logwatch, fail2ban, mdadm notifications, and certain scripts so they can use a gmail account I have solely for this purpose to send notifications to my actual e-mail address.

It is pretty easy to set up, just remember gmail will want port 587 for SMTP, so you will need a line in /etc/ssmtp/ssmtp.conf like this:

```
mailhub=smtp.gmail.com:587
[EMAIL="Authuser=senderaddress@gmail.com"]Authuser=senderaddress@gmail.com[/EMAIL]
AuthPass=senderaddresspassword
UseTLS=YES
UseSTARTTLS=YES

```

So just remember that any users with access to that config file will also have access to that gmail account password as far as security is concerned.

---

### Post by smeerbartje on 2014-07-30
Thanks, working great!

---

