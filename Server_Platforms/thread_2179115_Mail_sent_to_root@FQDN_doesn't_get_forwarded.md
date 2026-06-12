---
title: "Mail sent to root@FQDN doesn't get forwarded"
date: 2013-10-06
forum: Server Platforms
---

### Post by Rich_Stanton on 2013-10-06
Hi, I have a Ubuntu 12.04 LTS system, running Exim 4.76-3ubuntu3.1. The system has mail configured as a smarthost, so it sends via my ISP's SMTP server. Exim listens on localhost only (and the firewall is on). I have a gmail address set up as a alias for root in /etc/aliases. If I send mail to root or root@localhost, then it's forwarded to my external email account correctly, via the smarthost. However if I send to root@FQDN, the exim logs show that it's not forwarded to my gmail account - it shows that it's sending it to root@FQDN. Then the email just vanishes - I assume it's sent via the smarthost, which tries to deliver it back to this machine, which fails because Exim is only listening on localhost.

The problem is that anything run via cron (cron-apt etc) mails the output to root@FQDN, so the emails from all my cron jobs are vanishing. Why is the forwarding email address ignored if mail is sent to root@FQDN, but applied correctly if it's sent to root@localhost? I've checked my hosts file & the FQDN resolves to 127.0.1.1. I tried changing this to 127.0.0.1, but it didn't make any difference.....

Rich

---

### Post by CharlesA on 2013-10-06
I use this method:
[https://portal.slac.stanford.edu/public/ITHelp/KB/ForwardingMailfromUnix.aspx](https://portal.slac.stanford.edu/public/ITHelp/KB/ForwardingMailfromUnix.aspx)

Lazy, but it works.

---

### Post by Rich_Stanton on 2013-10-07
> **CharlesA said:**
> I use this method:
[https://portal.slac.stanford.edu/public/ITHelp/KB/ForwardingMailfromUnix.aspx](https://portal.slac.stanford.edu/public/ITHelp/KB/ForwardingMailfromUnix.aspx)

Lazy, but it works.

I've tried that - same result. Mail to the FQDN doesn't get forwarded....

---

### Post by Rich_Stanton on 2013-10-07
All fixed - for some reason the FQDN wasn't set in update-exim4.conf.conf, despite being listed correctly when running dpkg-reconfigure exim4-config. Added the FQDN to DC_other_hostnames fixed it all.

---

### Post by CharlesA on 2013-10-07
> **Rich_Stanton said:**
> All fixed - for some reason the FQDN wasn't set in update-exim4.conf.conf, despite being listed correctly when running dpkg-reconfigure exim4-config. Added the FQDN to DC_other_hostnames fixed it all.

Glad you got it sorted out.

---

