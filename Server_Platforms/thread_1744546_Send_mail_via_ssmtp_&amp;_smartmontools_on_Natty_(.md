---
title: "Send mail via ssmtp &amp; smartmontools on Natty (11.04)"
date: 2011-04-30
forum: Server Platforms
---

### Post by ThePol1 on 2011-04-30
I am not getting test emails from Smartmontools when I boot my server. Ssmpt is configured property because when I restart the Smartmontools daemon once the server is up, I receive test emails.

I receive the following messages in /var/log/syslog:

Apr 30 10:44:12 Ubuntu smartd[981]: Executing test of /usr/share/smartmontools/smartd-runner to [EMAIL="user@domina.com"]user@domain.com[/EMAIL]
Apr 30 10:44:12 Ubuntu sSMTP[1204]: Unable to connect to 'smtp.gmail.com'; port 587.
Apr 30 10:44:12 Ubuntu sSMTP[1204]: Cannot open smtp.gmail.com:587
Apr 30 10:44:12 Ubuntu smartd[981]: Test of /usr/share/smartmontools/smartd-runner to [EMAIL="user@domain.com"]user@domain.com[/EMAIL] produced unexpected output (134 bytes) to STDOUT/STDERR: #012/etc/smartmontools/run.d/10mail:#012send-mail: Cannot open smtp.gmail.com:587#012Can't send mail: sendmail process failed with error code 1#012

It almost seems like some service used to resolve IP addresses hasn't completely started when ssmtp tries to connect to smtp.gmail.com...

---

### Post by ThePol1 on 2011-05-04
<bump>

Any thoughts? I've a work-around in which I restart Smartmontools in rc.local, but it seems like a hack and this was working perfectly in 10.10. Thank you!

---

