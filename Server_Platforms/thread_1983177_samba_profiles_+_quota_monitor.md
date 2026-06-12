---
title: "samba profiles + quota monitor"
date: 2012-05-19
forum: Server Platforms
---

### Post by Sava on 2012-05-19
Hi guys,

I've a setup of a Ubuntu server and multiple Windows XP Pro clients.

On Ubuntu I had samba setup and created accounts with quota limit of 200Mb.

On several occasions I have users come to me and say the machine won't log them in. When I looked into their account I noticed that they've exceeding (or close to) their quota limit of 200Mb.

Is there a way, say:

1. Auto Notify user that his/her quota is about to max out? Perhaps a popup when he/she logging into her account, or a "Low disk space on your account" notification.

2. I noticed that not only Desktop and My Documents count towards the user's quota limit, but also the cache in Applications Data, for e.g, as well. Is there a way to only count the Desktop + My Documents ?

3. Is it possible to setup a cron script to send myself a weekly report of quota usage from /home/samba/profiles , and let's say have it auto-sorted from biggest usage to the smallest ?

4. As of now when user reaches the limit, the network refuses to let them logon. Is it possible to still let user login, but force them to delete some files right away to make space?


I appreciate any guide/tip you may have,

---

### Post by Sava on 2012-05-20
I figured out some crappy solution, posting here if anyone has the same question as mine:


0 1 * * 1 /../../cronscripts/quotamonitor.sh >> /../../cronscripts/quotamonitor_output.log

I skip the 2>&1 normally put in front of >> to receive an email no matter what's the outcome of the cron job.


quotamonitor.sh has this: 
du -ks * | sort -nr | cut -f2 | xargs -d '\n' du -sh


not too elegant, but should do the job for me. 'll have to wait a couple of hours for the first job to execute and the first email sent.

---

