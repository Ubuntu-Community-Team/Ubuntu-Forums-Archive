---
title: "Create Postfix Mail Logs"
date: 2010-09-12
forum: Server Platforms
---

### Post by liuhb86 on 2010-09-12
I just start to setup a mail server for my group.
Accidentally, I removed the /var/log/mail.*. After
sudo touch /var/log/mail.log
sudo touch /var/log/mail.info
sudo touch /var/log/mail.warn
sudo touch /var/log/mail.err
sudo chmod a+w /var/log/mail*  ,

these log keeps to be empty.

What shall I do to make the logs work?
And how can I check whether the logs is working?

---

### Post by lisati on 2010-09-12
> **liuhb86 said:**
> I just start to setup a mail server for my group.
Accidentally, I removed the /var/log/mail.*. After
sudo touch /var/log/mail.log
sudo touch /var/log/mail.info
sudo touch /var/log/mail.warn
sudo touch /var/log/mail.err
sudo chmod a+w /var/log/mail*  ,

these log keeps to be empty.

What shall I do to make the logs work?
And how can I check whether the logs is working?

Which MTA are you using? When I started using Postfix, the logs were populated automatically.

---

### Post by liuhb86 on 2010-09-12
I don't know... 
Isn't Postfix the MTA?

> **lisati said:**
> Which MTA are you using? When I started using Postfix, the logs were populated automatically.

---

### Post by lisati on 2010-09-12
> **liuhb86 said:**
> I don't know... 
Isn't Postfix the MTA?

Er Yes. Sorry about that, chief!
I think I missed seeing that you were using Postfix when trying to come up with an answer. 
No flashes of inspiration here at the moment......

---

### Post by liuhb86 on 2010-09-12
Finally resolved it...

The syslog service seems down. It works after sudo service rsyslog restart.

Many search results mentioned syslog/syslogd/sysklogd, and it takes time for me to find that the right thing for my Lucid is rsyslog.

---

### Post by kdresser on 2011-11-02
Thanks liuhb86.  You solved my identical dilema.

---

