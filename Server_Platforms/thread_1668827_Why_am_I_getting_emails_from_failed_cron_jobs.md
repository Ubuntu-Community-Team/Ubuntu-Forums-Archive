---
title: "Why am I getting emails from failed cron jobs?"
date: 2011-01-16
forum: Server Platforms
---

### Post by allspiritseve on 2011-01-16
I recently set up exim so that I could test emails sent from my php sites. I have now been getting daily emails that either report errors from cron jobs or report a failure to send emails to root@cory-laptop or cory@cory-laptop about cron errors.

I first of all don't want mail sent to the above addresses, because they are obviously not actual email addresses. Second, I'd really prefer not to get emails when an email failed to send to these addresses. Does anyone have any insight into what I need to change to stop these emails from being sent?

Thanks,

Cory

---

### Post by SeijiSensei on 2011-01-17
Crond mails any error messages that are generated during the execution of a cron job to its owner.  You can fix this problem by redirecting stderr like this:

```

01 00 * * * root /usr/local/sbin/some_script >> /var/log/some_script_log 2>&1

```

The "2>&1" at the end of the line redirects the error output to the main stdout stream.  It's then all appended to a log file. 

If you look at the emails, you should have some idea what the error is.  If you can edit the script, you should be able to trap any errors in the script itself.

As for errors about cory@cory-laptop, does the machine have a hosts entry for "cory-laptop"?  If I wanted to redirect mail for root into cory's account, with sendmail I'd add an alias to /etc/aliases like this:

root:  cory

then run "newaliases" to update the database. That will deliver root's mail to cory's local mailbox.  I don't know if that's how exim does it, but if you know enough to install exim you should be able to find its equivalent for /etc/aliases.

Alternatively, you could just let it deliver root's mail to root's local inbox and leave cory out of it entirely.

---

### Post by allspiritseve on 2011-01-17
The problem is mail isn't being delivered to root's local inbox, it's being sent to my gmail account. I'm not sure how to fix that though.

---

### Post by SeijiSensei on 2011-01-17
Could be a number of things.  Most likely you have your gmail address coded into one of the PHP scripts or you have an alias somewhere that points to your gmail account.

In sendmail, I can run (as root) the command "sendmail -bv [email]someone@example.com[/email]", and it will tell me how it would deliver a message to that address expanding aliases along the way.  Is there a way to ask the same question of exim?

---

### Post by wojox on 2011-01-17
> **allspiritseve said:**
> The problem is mail isn't being delivered to root's local inbox, it's being sent to my gmail account. I'm not sure how to fix that though.

Did you reconfigure it?

```
sudo dpkg-reconfigure exim4-config
```

---

