---
title: "Different (Mail) stats between awstats and vhcs"
date: 2009-02-01
forum: Server Platforms
---

### Post by crafter on 2009-02-01
Hi All

I'm been trying to collect logs on my server hosting multiple web and domains, running Ubuntu 7.10.

I noticed a huge difference between email usage figures that VHCS reports (using iptables, I think) and what awstats reports  (using the mail.info logs).

I also want to alert you to the fact that my awstats mail log contains this processing :
perl /usr/sbin/maillogconvert.pl standard < /var/log/mail.info | grep THE_VIRTUAL_DOMAIN

I had to filter the maillogconvert output as the SiteDomain value was not filtering on the domain properly and adding mails from other domains.

The VHCS stats are always much higher, for example in January for one domain, VHCS reported 1.2 G and awstats reported 420 M of email.

Anyone can point me in the right direction here, please?

---

