---
title: "send root's email to an external address"
date: 2010-07-31
forum: Server Platforms
---

### Post by Brazen on 2010-07-31
One thing I've been negelecting on my servers is the email that gets collected in /var/mail/root (I don't think I've seen any other users pop up in /var/mail/).  

IF I have to use an MTA (choosing between Exim, Postfix, Sendmail, qmail, etc) I would prefer to do this with Postfix just because I use postfix elsewhere.  But if I can do this with something lighter, than even better.

I'd thought about just right a ruby script that grabbed that entire /var/mail/root file and email it to [email]admin@company.com[/email] using our company smtp server.  But that just feels hackish.  Ideally, I would like whatever is generating that email to just connect directly to our company smtp server and address the email to [email]admin@company.com[/email].  Or somehow have all mail going to root to be redirected to [email]admin@company.com[/email] using an external smtp server and not having to waste space or resources on running a full MTA on every Ubuntu server.

Thanks for any help.

---

### Post by Brazen on 2010-07-31
I did happen upon this website ( [http://www.cyberciti.biz/faq/disable-the-mail-alert-by-crontab-command/](http://www.cyberciti.biz/faq/disable-the-mail-alert-by-crontab-command/) ) that tells how to redirect mail from cron jobs.  I'm assuming that everything in /var/mail/root came from cron jobs, so does anybody know - can I just put MAILTO="admin@company.com" and NOT install an MTA?

I'd rather have a catch-all for mail from anywhere going to root but I would rather not install an MTA, so if this cron setting works, it may be my best choice.  I still have a problem though, in that this will most definately send directly to the server in the mx record for company.com and I really need it to relay through 192.168.x.x instead, but I can't find any way to set an smtp server to be used by cron.

---

### Post by Brazen on 2010-07-31
Ok, so I just realized something else.  Apparently, the only servers that actually have anything in /var/mail/ are servers that have postfix installed.  I just checked a Dapper server that is 2 years old and a newer Karmic server and neither have anything in /var/mail/.  What happens to cron status messages on servers that don't have an MTA?  Are they just lost forever?

---

### Post by kgatan on 2010-07-31
Use mailx to send mails from command line, works with attached files as well.
I use it to send backup logs from my rsync operations.

Easy to use and you can configure it for external smtp as well.

---

### Post by Brazen on 2010-08-01
> **kgatan said:**
> Use mailx to send mails from command line, works with attached files as well.
I use it to send backup logs from my rsync operations.

Easy to use and you can configure it for external smtp as well.

That's fantasgreat.  However, I just realized I left out a rather crucial piece of information.  I wanted this to happen automagically, without me logging in and running a command.  I totally left that part out.

I know, I know, I could just make a cron job that ran mailx once a week or something, but that just seems hackish.  This is probably a mute point though, as I think nothing gets put in /var/mail unless an MTA is installed anyway.

---

### Post by Bachstelze on 2010-08-01
> **Brazen said:**
> That's fantasgreat.  However, I just realized I left out a rather crucial piece of information.  I wanted this to happen automagically, without me logging in and running a command.  I totally left that part out.

I know, I know, I could just make a cron job that ran mailx once a week or something, but that just seems hackish.  This is probably a mute point though, as I think nothing gets put in /var/mail unless an MTA is installed anyway.

In /etc/aliases

```
root:       foo@bar.com
```

Then run [font=monospace]newaliases[/font].

---

