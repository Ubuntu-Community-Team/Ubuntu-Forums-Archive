---
title: "Fastest Postfix Dovecot configuration"
date: 2016-02-11
forum: Server Platforms
---

### Post by gabor6 on 2016-02-11
Dear Everyone!

I looking for the fastest and secure configuration for a heavy used mail server. I use the google day-by-day but i can't find the perfect configuration, i need to pointing me which software i must use the fastest and secure authentication, mail delivery and sending. I want to use only 25, 587, 993 ports (SMTP, Submission, IMAPS), i have multiple domains, i have (all together) up to 100 email accounts. What i'm exactly looking for the small list of used components (postfix, dovecot, ssl, etc...) and copy of configuration files of postfix-dovecot and a few words why that configuration is better like others. I think my thread will be popular while many others interesting this setting. Thank you!

---

### Post by alexandari on 2016-02-12
The perfect configuration differs from server to server regarding what you actually need. I use Postfix and Dovecot through SASL.

---

### Post by gabor6 on 2016-02-12
Yes, i know, but i opened this thread to share with everybody a "basic good start" configuration. Could you share with us your configuration or your idea (without personal data) please?

---

### Post by Habitual on 2016-02-12
> **gabor6 said:**
> Yes, i know, but i opened this thread to share with everybody a "basic good start" configuration.
But you haven't shared anything but open ports.

---

### Post by gabor6 on 2016-02-12
> **Habitual said:**
> But you haven't shared anything but open ports.

You are right, i not shared configuration details while i'm not a mail server professional, i want to learn too, anyway i don't want to share what myself don't trust. But if you could show us the right "starting config" than do it, you are very welcome.

---

### Post by Habitual on 2016-02-12
There is no right "starting config". Systems vary, Requirements vary. Postfix/Dovecot varies.
Looking for a magic bullet? There aren't any.


There's always time to do it over, but never enough to do it correctly.

Good luck trying to be "popular".

---

### Post by gabor6 on 2016-02-12
> **Habitual said:**
> There is no right "starting config". Systems vary, Requirements vary. Postfix/Dovecot varies.
Looking for a magic bullet? There aren't any.


There's always time to do it over, but never enough to do it correctly.

Good luck trying to be "popular".


It is wise to listen, if you can not meaningfully help you maybe should not have to waste your precious time on unnecessary entries.

---

### Post by lisati on 2016-02-12
> **Habitual said:**
> There is no right "starting config". Systems vary, Requirements vary. Postfix/Dovecot varies.
Looking for a magic bullet? There aren't any.


There's always time to do it over, but never enough to do it correctly.

Agreed. When I was running my own mail server a few years ago, I was never completely satisfied with the configuration, even though I had a usable system.

---

### Post by Habitual on 2016-02-12
> **gabor6 said:**
> if you can not meaningfully help you maybe should not have to waste your precious time on unnecessary entries.

You are asking this forum, so I find your putting requirements on that "rich".
This whole post is unnecessary.

You still haven't shared, and I don't intend to.
Fast != Secure.

Class dismissed.

---

### Post by nerdtron on 2016-02-12
My suggestion on configuring email servers: Use iRedMail.
It's basically a script that install everything you need for an email server, very easy to setup because you'll just input your domain name and some other info. Installation is almost entirely automated. Plus it also configures clamAV antivirus, spamassassin spam filter, iptables and fail2ban for extra security. You can even try it on a newly installed Virtual Machine. The install script will install/configure everything it needs to run the whole email server.

**Note: I'm promoting since I've used it before and it quite worked well. Plus it has a nice admin interface for managing multiple domains and user creation.

Website: [http://iredmail.org/](http://iredmail.org/)
Ubuntu installation (with screenshots): [http://iredmail.org/docs/install.iredmail.on.debian.ubuntu.html](http://iredmail.org/docs/install.iredmail.on.debian.ubuntu.html)

---

