---
title: "[Fail2Ban] What to know what logfile?"
date: 2017-07-02
forum: Security
---

### Post by calby on 2017-07-02
Hi,
I have some jails in fail2ban that I want to use, but I don't know what logfile I should use - it's two it's either *access.log or *error.log which one should I use?

This jail's is what I want:
apache-shellshock
apache-pass
apache-modsecurity
apache-common
apache-botsearch
php-url-fopen
apache-nohome
apache-badbots
apache-overflows
apache-noscript
apache-auth

---

### Post by Habitual on 2017-07-02
What do the logs indicate?

I thought you identified nginx in your other thread?
I took the apache-badbots.conf and made my own. After watching logs for 3 years. Daily.
and editing that filter based on what I saw in the logs. Daily.
That is what I am paid to do. 
Trouble with that is, you have no idea what the logs "mean" or what to look for, or how you can't trust Useragents.

Personally, enabling 11 jails is a little too over-the-top.

---

### Post by calby on 2017-07-02
> **Habitual said:**
> What do the logs indicate?

I thought you identified nginx in your other thread?
I took the apache-badbots.conf and made my own. After watching logs for 3 years. Daily.
and editing that filter based on what I saw in the logs. Daily.
That is what I am paid to do. 
Trouble with that is, you have no idea what the logs "mean" or what to look for, or how you can't trust Useragents.

Personally, enabling 11 jails is a little too over-the-top.

I did switch to apache as I did switch from seafile to nextfile.
I do mean what logpath I should choose, some do have the /var/log/apache2/*error.log and some have /var/log/apache2/*access.log but i dont know which filter should have what?

---

### Post by Habitual on 2017-07-03
Those logs are shown as examples in /etc/fail2ban/jail.conf
or if you are keeping up with the advices /etc/fail2ban/jail.local
and globbing is specifically mentioned as being supported.

access.log is what you're after.

---

