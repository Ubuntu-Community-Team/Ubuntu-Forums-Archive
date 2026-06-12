---
title: "How to install SendMail on Dapper (6.06 Server Edition)?"
date: 2006-11-03
forum: Server Platforms
---

### Post by bobsta63 on 2006-11-03
Hi all,

I am about to build a new Ubuntu running Dapper (6.06 Server Version) webserver running Apache, PHP, Perl, MySLQ etc.

I am required to install Bugzilla on it and it requires an MTA, I really just want a simple and easy to install one.
The options are: SendMail, qmail or Postfix.

I would like to know, Is there an easier to use and install MTA from the list above? I only need it to send out emails from the Bugzilla Bug Tracking Server.

Can you install them using 'apt-get install'?

Would you say SendMail is the easiest to install, configure (SendMail is the prefered required MTA for Bugzilla).

If you have the command or a HOWTO install SendMail, please post it :)

Thank you very much in advance,

Bobby

---

### Post by DannyG on 2006-11-03
I think the command for installing sendmail is something to the effect of ```
apt-get install sendmail
``` or ```
apt-get install sendmail-common
``` Can't remember off the top of my head.

But [this page]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p5") has a great Howto on installing Postfix with SMTP-Auth and TLS, if you'd prefer follow a guide.

Other than that I don't know much about Sendmail.

Daniel.

---

### Post by psylvester on 2007-03-23
root@zion:/usr/psylvester# sudo apt-get install sendmail-common
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sendmail-common
root@zion:/usr/psylvester# 

When you post something, or answering someone, make sure it works.

---

