---
title: "Postfix not sending emails to local domain"
date: 2014-01-03
forum: Server Platforms
---

### Post by shakeypuss on 2014-01-03
I have  a machine with Ubuntu 12.04, Apache, MySql and PHP installed. It is used to receive applications and send out email notifications via Postfix. My problem is that it will send to any user outside of the local domain but if it tries to send to the local domain user then it bounces because there is no such user on the local machine. The local mail users are handled by a Windows Exchange server in the domain. How do I configure so that it looks to another server for users in the local domain? Thank you.

---

### Post by SeijiSensei on 2014-01-04
Take a look at the "[transport](http://www.postfix.org/transport.5.html)" function in Postfix.  I think you might be able to use the [local_transport](http://www.postfix.org/postconf.5.html#local_transport) option.

---

### Post by pft42 on 2014-01-05
Probably things are much easier and just result of wrong interpretation of words.
In Ubuntu (all Unix?) 'local' means the individual machine, i interm of booted OS (not even HW in case of virtual systems).
Any other difnition does not make sense as no machine can have a clue what else could be meant by local (room, house, company ... - all term undefined in OS)

So, if mails to your_domain bounce to non-xistent local users, this clearly indicates that postfix thinks that it should handle this domain as told via configuration (see parameter 'mydestination')
If in reality the domain is handled elsewhere (in this case the exchange server), then just remove it from postfix's config.

Thomas

---

### Post by SeijiSensei on 2014-01-05
> **pft42 said:**
> If in reality the domain is handled elsewhere (in this case the exchange server), then just remove it from postfix's config.

That only works if there is a DNS MX record pointing to the Exchange server that Postfix can use to route the mail.  Usually that means there needs to be an internal DNS server that provides mappings for the local network, while another, public, DNS server provides information to the Internet.  That's why SMTP server programs like Postfix and sendmail have methods to override DNS routings for specified domains.  I use sendmail which has the [mailertable]("http://www.sendmail.com/sm/open_source/docs/m4/mailertables.html") option for this purpose.  My reading of the Postfix documentation suggests that transport maps provide the equivalent functionality for that software.

---

### Post by pft42 on 2014-01-05
Right direction. 
But then the bounces due to "non-existing local users" should be gone, .i.e. replaced by a different misbehavior, right?
What's your status with transport maps? I have not used it, but I am quite familiar with postfix.

---

### Post by shakeypuss on 2014-01-08
I finally found the answer here:
[http://www.nooblet.org/blog/2007/postfix-transport-maps-diverting-mail-traffic/](http://www.nooblet.org/blog/2007/postfix-transport-maps-diverting-mail-traffic/) 
Thanks all.

---

