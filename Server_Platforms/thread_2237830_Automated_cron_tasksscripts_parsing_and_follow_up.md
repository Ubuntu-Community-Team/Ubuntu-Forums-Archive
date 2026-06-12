---
title: "Automated cron tasks/scripts parsing and follow up"
date: 2014-08-04
forum: Server Platforms
---

### Post by toni6 on 2014-08-04
Hi all,

We are managing about 85 Ubuntu servers world wide. All these servers have some cron jobs to simplify our own work.
At this moment every cron job sends out the result via e-mail to a single mailbox at our HQ. This allows us to check if the cron job did run successful or not.

**Drawback of the current setup**
The setup was invented when we had a server or 10, so it was manageable.
Today 85 servers spit out 400 e-mails a day that need to be checked manually.
To make things worse, if a cron job doesn't run at all, the checker might not notice it due to the vast amount of e-mails.

**Setup we are looking for**
I'm not keen on changing all server cron jobs, but if it has to be done, then I'm fine with that.
But I rather seeks for a system that can parse the central mailbox and verify if the e-mails are indeed received in time and with correct data.
So I'm looking for a framework that:
[LIST]
[*]Allows us to define the tasks that need to run, and to which the framework matches the received e-mails to see if the task is indeed running.
[*]Allows to bump an alert if a task has failed or didn't run at all.
[*]Allows us to easily create new tasks based on either a received e-mail or a crontab read out from a remote server.
[/LIST]

I like to ask you for idea's about our solution.
Perhaps we are looking for a solution that will never work, and perhaps we are still running our servers to much as home systems.
So share you thoughts, opinions, idea's to simplify our life as system engineer even more.

Thanks!
Toni.

---

### Post by ian-weisser on 2014-08-04
You seem to describe two problems:
1) Filtering out the routine (success) e-mails
2) Detecting if a machine fails to send e-mails

And possibly:
3) Moving away from an e-mail based system entirely


Filtering out e-mails requires you to build a parser, parse each e-mail for the expected language, and determine your logic for escalating the e-mail to a human-monitored account.

Detecting when a machine fails to send an e-mail requires you to build a database of machines and jobs, and use it to track the emails received. This can use the same parser, since you need to determine the job.

Moving away from e-mails entirely has many candidates.

For example, you can have a master application at HQ ssh into each remote server,  test and perform the cron jobs itself, and report various failures (failure to connect, failure to pass test, job failure) as they occur on each machine.

Another example, you can keep e-mail based reporting, but shift the human-monitoring to a pretty status display instead of an e-mail box.

Another example, you can pay any of several vendors (including Canonical) selling easy-remote-management services.

---

### Post by toni6 on 2014-08-04
Hi ian-weisser.
Thanks for your reply.

It is in fact a single problem: tracking automated tasks.
We aren't looking for failure in e-mail sending (never failed in the last 7 years), but sometimes we encounter that CRON itself crashes and thus never executes any task anymore.

> **ian-weisser said:**
> 
3) Moving away from an e-mail based system entirely

Well, this is an option, but in terms of delivering information, e-mail is quite a good platform.

> **ian-weisser said:**
> 
Filtering out e-mails requires you to build a parser, parse each e-mail for the expected language, and determine your logic for escalating the e-mail to a human-monitored account.
Detecting when a machine fails to send an e-mail requires you to build a database of machines and jobs, and use it to track the emails received. This can use the same parser, since you need to determine the job.

Correct. Not a fast solution, but perhaps a solid solution.

> **ian-weisser said:**
> 
Moving away from e-mails entirely has many candidates.
For example, you can have a master application at HQ ssh into each remote server,  test and perform the cron jobs itself, and report various failures (failure to connect, failure to pass test, job failure) as they occur on each machine.

This might work if the Internet lines and VPN's are very stable, but they aren't. Especially not on remote sites.
Plus: most jobs have to perform local tasks only. They just need to send their report to a central system for follow up.

> **ian-weisser said:**
> 
Another example, you can keep e-mail based reporting, but shift the human-monitoring to a pretty status display instead of an e-mail box.

That's what I'm looking for now. All idea's for such a solution are welcome.

> **ian-weisser said:**
> 
Another example, you can pay any of several vendors (including Canonical) selling easy-remote-management services.

If they can include my other systems too (non Linux), then I'm all ears.

---

### Post by tgalati4 on 2014-08-04
I would classify your cronjobs using an 80%/20% rule.  80% of your problems are caused by 20% of the conditions.  So, rewrite your email scripts to send out only those 20%.  You should not have to send out emails saying that something was successful.  That's like saying:  "Send an email if the server is up today."  Assume success unless something goes wrong.

What other chokepoints can you monitor to determine that the cronjobs have executed?  rsyslog, cronjobs to scan syslog, there are several ways to monitor a server.  You could design a custom dashboard for cacti/nagios to show status.  You could investigate new [service orchestration]("https://help.ubuntu.com/community/Orchestra/Overview") frameworks--this would require an investment in time and system design.

---

### Post by toni6 on 2014-08-04
Hi tgalati4,

Thanks for you points. They make sense.
As we already have nagios up and running, I'll create a global check for cron activity (by letting cron execute a regular send_nsca command and check for the service freshness).
This should allow us to verify the status of cron and reduces the amount of mails.

---

### Post by SeijiSensei on 2014-08-04
I recommend becoming familiar with [procmail]("http://www.procmail.org/").  It's basically a Swiss army knife for email.  You can have procmail scan each message's headers and body for regular expressions and take appropriate actions.  You could have it forward key emails to the admin's personal accounts, for instance, or pass the message to a script for further actions.  

Take a look at "[man procmailrc]("http://linux.die.net/man/5/procmailrc")" and "[man procmailex]("http://linux.die.net/man/5/procmailex")" for details.

As for keeping cron running, I run a script every couple of minutes on my servers that scans the result of "ps ax" and restarts any daemons that are not running.  It also sends me an email notice when a daemon is no longer functioning.  There are many such scripts out there on the Internet as well.

---

### Post by toni6 on 2014-08-05
> **SeijiSensei said:**
> I recommend becoming familiar with [procmail]("http://www.procmail.org/").
We are familiar with that, but we run on Exchange 2013.

Anyhow, I modified all server crontabs to dump their human readable output to /dev/null and Nagios shows the CRON status.
My team will test this setup this and next week to see if it is a good solution.

Thanks all for your suggestions.

---

### Post by TheFu on 2014-08-05
Lots of good information above.  Figured I throw in 1 more option for consideration .... a remote management tool like ansible/puppet/salt/rex/cfengine.

We use **ansible** and it supports running arbitrary commands on the remote systems, while reporting the results to the main workstation making the requests. Of course, it does much more than this - system configuration is the main purpose for those tools.

We use cron for most daily tasks and have the output emails sent to a central automation account that isn't monitored too closely.   Sure, we look over it and normally delete "successful" runs, but we also retain 90 days of logwatch output as part of our security method. It has been helpful to see which packages have been recently updated using this a few times after something bad happened.

Can't **fetchmail** pull the output from Exchange and run it through **procmail**?  Just asking - I don't know. Haven't used Exchange since 2007 and if pop3 is disabled ... meh.

Clearly, we could do better automation with our output here too. Hope to see some other options.

---

