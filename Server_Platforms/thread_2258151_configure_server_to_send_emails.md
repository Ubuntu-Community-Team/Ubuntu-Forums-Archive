---
title: "configure server to send emails"
date: 2014-12-25
forum: Server Platforms
---

### Post by geohei on 2014-12-25
Hi

ubuntu server 14.04.

I have cron jobs running.

I'd like that cron sends stdout to a specific email address. This is foreseen by default, but how do I configure the Ubuntu server to do this?

man cron says:
> ...
cron  then  wakes up every minute, examining all stored crontabs, checking each command to see if
       it should be run in the current minute.  When executing commands, any output  is  mailed  to  the
       owner  of the crontab (or to the user named in the MAILTO environment variable in the crontab, if
       such exists).  The children copies of cron running these processes have  their  name  coerced  to
       uppercase, as will be seen in the syslog and ps output.
...
"... the owner of crontab ...", which I am (root). But how do I configure Ubuntu to send these emails to my (lets say) Gmail account?

Do I have to install postfix, ssmtp, sendmail, ... for this?

Thanks,

---

### Post by MAFoElffen on 2014-12-25
Basic. In my scripts, my servers send mail to a Gmail account that I set up to just be a an admin type of account-- a warning for my servers. I set that account up on my Android phone. If there is a problem, instead of sending mail to system root, where I would only see warnings of a problem while I am on that system, those messages go through ssmtp to that GMail account, for instant warnings. I also send messages through XMessage to my server-bank consoles.

Security issues (to me) are minimal, as they are just set as a port out, not open to incoming. Very low overhead for adding just that capability. (Rather than adding and administering a full-blown email server service,)

It was not an original idea. I needed help on mdadm... and there was a member a few years ago here that helped me. I went to his blog, where he had written a few tutorials. One was a cron triggered script that he used to check the heslth of his disks, that email him if there were problems. I was inspired by that tutorial. I have that bookmarked here somewhere.

If you are interested in that. I'll come back to post that link and give him the credit for that inspiration.

---

### Post by MAFoElffen on 2014-12-25
The member that helped me was "rubylaser" (Zack Reed) and here is that tutorial:
[http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp](http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp)

Thanks to him and his inspiration on that. Funny how on Christmas day, I now reflect how his help not only inspired me on how I set things up today... but in how I strive to share and help others.

---

### Post by TheFu on 2014-12-26
There are nice folks here. I think we strive to be helpful, but that can be hard with limited data and sometimes we just don't know the complete answer for every possible issue.

I setup a "satellite" MTA on all my Linux systems just for cron. These forward all email to my primary email server, which holds many different accounts.  A satellite email server only accepts email from localhost, never any other host on the internet.  When installing postfix, there is a wizard - choose satellite, setup a /etc/alias, run newaliases and be happy.  Of course, I don't know what it takes to get gmail to accept emails from a satellite email server, but I know that at least one forum admin here has posted his config files for that somewhere in the last 4 yrs. ;)  Think he connects on 465/tcp as a normal client with 1 user account.

Sorry I'm not more helpful.

---

