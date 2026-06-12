---
title: "Stop mails from cronjob"
date: 2009-01-22
forum: Server Platforms
---

### Post by wattaman on 2009-01-22
Hello,
Is there a way to stop a cronjob from sending emails? Everytime the cronjob does a job (and I have some) it sends a mail to *nobody*. Every 3 days I delete around 200MB of emails from the crons.
I admit I'm a beginner as a server admin. I don't have access to server except through webmin and SSH, and I always use webmin.
Anyway, if some of you can help, I have this in the cronjobs panel:
> 
[ -x /usr/lib/mailman/cron/checkdbs && /usr/lib/mailman/cron/checkdbs  
[ -x /usr/lib/mailman/cron/disabled ] && /usr/lib/mailman/cron/disabled  
[ -x /usr/lib/mailman/cron/senddigests ] && /usr/lib/mailman/cron/senddigests  
[ -x /usr/lib/mailman/cron/mailpasswds ] && /usr/lib/mailman/cron/mailpasswds  
[ -x /usr/lib/mailman/cron/gate_news ] && /usr/lib/mailman/cron/gate_news  
[ -x /usr/lib/mailman/cron/nightly_gzip ] && /usr/lib/mailman/cron/nightly_gzip 

They came, apparently, with the new installation of Ubuntu 8.14, I mean I haven't set them and have no ideea what are they doing, but they include the term **mailman** in their commands and this makes me wonder:
- If I deactivate/delete any of them will this stop the cronjobs from sending the mail?
Thank you for your support.

---

### Post by Titan8990 on 2009-01-22
Check this out: [http://unixgeeks.org/security/newbie/unix/cron-1.html](http://unixgeeks.org/security/newbie/unix/cron-1.html)


Look at the section "output from cron"

---

### Post by wattaman on 2009-01-22
> **Titan8990 said:**
> Check this out: [http://unixgeeks.org/security/newbie/unix/cron-1.html](http://unixgeeks.org/security/newbie/unix/cron-1.html)


Look at the section "output from cron"

Thanks, m8! I did, but haven't understood how exactly can I stop the cron from sending mails. I guess is not exactly e newbie info.
I quote from that page:
> If you have a command that is run often, and you don't want to be emailed the output every time, you can redirect the output to a log file (_or /dev/null, if you really don't want the output_).

Can you elaborate a little the underline phrase?
- And regarding my initial question: if I deactivate/delete those crons above (which I know nothing about, I haven't created them) would this stop the other crons from sending mails?

Thanks again!

---

### Post by amauk on 2009-01-22
any output to the error output stream (stderr) will automatically be emailed to the user running the cronjob

to stop this, you need to redirect the stderr to /dev/null

say you have:
0 0 * * 0 command

and command sends an error to stderr
file not found, or whatever

redirecting stderr means the error is sent to /dev/null, and discarded

0 0 * * 0 command 2> /dev/null

---

### Post by wattaman on 2009-01-24
> **amauk said:**
> any output to the error output stream (stderr) will automatically be emailed to the user running the cronjob

to stop this, you need to redirect the stderr to /dev/null

say you have:
0 0 * * 0 command

and command sends an error to stderr
file not found, or whatever

redirecting stderr means the error is sent to /dev/null, and discarded

0 0 * * 0 command 2> /dev/null

the  " >> /dev/null" seems to work. Thanks for the explanation!

---

### Post by linux_tech on 2009-01-24
If you no longer want cron to send eamils you can edit /etc/crontab

and remove the email address listed for MAILTO=

Then you should no longer receive emails.

---

### Post by wattaman on 2009-01-24
> **linux_tech said:**
> If you no longer want cron to send eamils you can edit /etc/crontab

and remove the email address listed for MAILTO=

Then you should no longer receive emails.

Thank, I've tried it before the " >> /dev/null" thing. Aparently MAILTO="" doesn't work for me. But it doesn't matter since is fixed now, anyway

---

