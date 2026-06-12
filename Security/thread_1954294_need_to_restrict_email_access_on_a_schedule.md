---
title: "need to restrict email access on a schedule"
date: 2012-04-07
forum: Security
---

### Post by dave37 on 2012-04-07
I need to restrict access to email services on our network from Friday at 7 pm until the following Saturday morning at 5 am, and again from Saturday at 7 pm to Sunday 5 am.

I would like to do this on the router as a cron job, it runs dd-wrt but would need to have the schedule exclude a couple of admin machines, preferably by mac address.

Failing that I need to be able to do it on the local machines as a cron job.  Then of course I could not have the cron job on the admin machines to continue to allow their access.

Any help would be greatly appreciated.

---

### Post by SeijiSensei on 2012-04-07
> **dave37 said:**
> I need to restrict access to email services on our network from Friday at 7 pm until the following Saturday morning at 5 am, and again from Saturday at 7 pm to Sunday 5 am.

If you control the mail server, just add entries in cron to shutdown your SMTP server (probably sendmail or Postfix) and your POP/IMAP server (probably dovecot).  Alternatively you can have the server run a script that adds rules to iptables that block connections to ports 25, 110 (if you use POP3), and 143 (IMAP).  If you use the mail submission ports like 587, you'll need to block those as well.

If you don't control the server, you can probably block those ports on the router.

If you disable your SMTP server, make sure you have a backup specified in the MX records for your domain.  Remote servers will generally hold their mail for you until your server comes back online, but it's always better to have an SMTP backup.

---

### Post by dave37 on 2012-04-07
I don't control the mail server, it is an internet accessed mail server.  Unfortunately dd-wrt, the firmware on the router provides excellent improvements over the factory firmware performance but one thing it doesn't allow is blocking by ip address on a schedule, which is essentially what I need to do.

---

### Post by iponeverything on 2012-04-07
dd-wrt has cron and iptables -- what else do you need.

---

### Post by dave37 on 2012-04-07
> **iponeverything said:**
> dd-wrt has cron and iptables -- what else do you need.

Sorry for stating the obvious, but what I need is some help in using those tools to achieve what I need to do.  I am fully aware that dd-wrt has cron and iptables.  What I am hoping for is someone familiar with it to help as I don't have that ability/knowledge.  Yes, I've read the owner's manual.  Rather than spend 20 hours re-inventing the wheel I'm hoping that folks who have encountered this issue will share their knowledge with me.

Thanks!

---

