---
title: "Setting up for sending out mail"
date: 2012-04-22
forum: Server Platforms
---

### Post by bkosborne on 2012-04-22
Hi everyone,

I'm fairly new to Ubuntu and trying to find my way around a few things. I have a pretty bare bones Ubuntu 11.04 server setup at the moment with apache, mysql, and php setup already. It will ultimately become a web server, and for that reason I need to allow it to send out mail.

I have no intention of hosting mail on the server at all, but I need to be able to send it out. I saw this article: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix), but I believe that's intended more for setting up a mail server.

I've seen this as well: [http://library.linode.com/email/exim/send-only-mta-ubuntu-11.04-natty](http://library.linode.com/email/exim/send-only-mta-ubuntu-11.04-natty) (I'm not using a Linode slice), but the configuration also seems to get into receiving mail as well.

Mail is a bit daunting to me - I'm not sure that since I'm going to be using Google Mail to manage mail for the domain, if I even need to do a lot of work here?

Any input is helpful, thank you.

---

### Post by mörgæs on 2012-04-23
Moved to the server forum.

---

### Post by cj13579 on 2012-04-23
Hey I use a program called SSMTP which is availble in the repos. This allows me to send mail from my Ubuntu server via my gmail account.

[This]("http://www.havetheknowhow.com/Configure-the-server/Install-ssmtp.html") is a pretty good tutorial on how to set it up.

---

### Post by smtp on 2012-04-23
You could install either Sendmail or Postfix. Both will be able to send out mails from localhost to outside with default configuration. Please ensure that your host has a FQDN (a real Internet domain).

---

### Post by 95yj on 2012-04-25
Installing Postfix will allow you to send (and receive and relay) mail.  Since you won't be hosting mail, you won't need to install all the other utilities.  Following [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) will get you up and running fast.  Also, [https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer) is the root document which explains all of mail with the first item calling the Postfix document.  Good luck.

---

