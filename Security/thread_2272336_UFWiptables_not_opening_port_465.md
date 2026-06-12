---
title: "UFW/iptables not opening port 465"
date: 2015-04-06
forum: Security
---

### Post by russellclaude on 2015-04-06
Frequent, 5 year visitor- new member, first time poster.  I have added rules to my iptables/UFW, but I cannot get port 465 to show open-- b/c I am trying to firewall a site that needs to send email via Wordpress forms. 


sudo ufw status numbered
Status: active




To Action From
-- ------ ----
[ 1] 465 ALLOW IN Anywhere
[ 2] 22 ALLOW IN Anywhere
[ 3] 80 ALLOW IN Anywhere
[ 4] 25/tcp ALLOW IN Anywhere
[ 5] 587 ALLOW IN Anywhere
[ 6] 587 ALLOW OUT Anywhere (out)
[ 7] 465 ALLOW OUT Anywhere (out)

Thanks for your help!




but netstat doesn't show anything on 465 as open. Wierd because if I turn my firewall off, I can send mail-- but port does not show open then, either???? Can anyone help, please?

---

### Post by CharlesA on 2015-04-06
It's likely the mail is being sent outboard on port 25, not 465.

There is no rule allowing outbound traffic on port 25.

---

### Post by russellclaude on 2015-04-06
Still not working. Why does it work when I turn my firewall off, though?

Status: active
Logging: on (medium)
Default: allow (incoming), allow (outgoing)
New profiles: skip


To                         Action      From
--                         ------      ----
465                        ALLOW IN    Anywhere
22                         ALLOW IN    Anywhere
80                         ALLOW IN    Anywhere
25/tcp                     ALLOW IN    Anywhere
587                        ALLOW IN    Anywhere
53                         ALLOW IN    Anywhere


587                        ALLOW OUT   Anywhere
465                        ALLOW OUT   Anywhere
25                         ALLOW OUT   Anywhere

---

### Post by russellclaude on 2015-04-06
Thanks, by the way...

---

### Post by CharlesA on 2015-04-06
What MTA are you using? Postfix?

Wordpress should send mail via the php mail() function if I remember right. That should default to sending mail via port 25 unless specified otherwise.

Start looking in the logs for postfix or whatever mail transfer agent you are running.

---

### Post by russellclaude on 2015-04-06
I am using Gmail which uses 465. Also not using standard WordPress mail function. LIke I mentioned,  everything works with firewall turned off. I've seen threads with same problem but either they don't list solution for my issue or at all. Thanks again.

---

### Post by russellclaude on 2015-04-06
What is the risk if I just leave the firewall off? Not really expecting that to be a good option.

---

### Post by Habitual on 2015-04-06
> **russellclaude said:**
> What is the risk if I just leave the firewall off? Not really expecting that to be a good option.
If you have a router, this is a possibility.

---

### Post by Doug S on 2015-04-06
Do you see any useful log entries in /var/log/syslog?

Perhaps monitor the resulting iptables rule set to determine if you can identify what is going on with the packets. Observe the counters ( sudo iptables -v -x -n -L ) before and after trying to send the e-mail and / or add some extra logging to help debugging. Note that it can be a little difficult to follow a UFW generated iptables rule set.

---

### Post by russellclaude on 2015-04-06
OK - this has been a great learning experience. Apparently I need to get a better understanding of how ports work. I solved the problem! Thanks to Mark Berry, the author here:

[http://www.mcbsys.com/techblog/2015/01/increasing-the-wp-mail-smtp-timeout/](http://www.mcbsys.com/techblog/2015/01/increasing-the-wp-mail-smtp-timeout/)

It seems that when i turned the firewall on, it made the smtp handshake take quite a bit longer, which I was experiencing with firewall on vs off anyway, so it makes sense. 

I had to go into the phpmailer files:
* /wp-includes/class-phpmailer.php
* /wp-includes/class-smtp.php

...and increase the timeout to something north of 10/15 seconds. This worked perfectly- even with firewall on! All my free time this weekend was wasted on figuring out this issue. Went ahead and reset my firewall to defaults, and I will reconfigure later and test again. -rh

---

### Post by Doug S on 2015-04-06
Thanks very much for reporting back your findings.

Any delay added by the iptables rules set should be very minimal, and so the cause and effect here seems a little odd to me.

---

