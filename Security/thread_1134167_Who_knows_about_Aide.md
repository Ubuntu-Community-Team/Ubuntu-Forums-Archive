---
title: "Who knows about Aide"
date: 2009-04-23
forum: Security
---

### Post by funkfresh01 on 2009-04-23
What do the community think about Aide? I installed the application for the first time and tried to run it by typing aide --init. I got this message:

/var/lib/aide/please-dont-call-aide-without-parameters/aide.db.new for writing

Can anyone interpret this? What did I do wrong? How do I run Aide?

---

### Post by pauna on 2009-05-04
> **funkfresh01 said:**
> What do the community think about Aide? I installed the application for the first time and tried to run it by typing aide --init. I got this message:

/var/lib/aide/please-dont-call-aide-without-parameters/aide.db.new for writing


How does your aide.conf look like? You first need to set up the configuration file to select which directories/files you want to be put into the AIDE database. Then you run "aide --init".

It may be that the "database" or "database_out" directives (i.e. the old and new database filenames) in your aide.conf are not properly configured.

---

### Post by rossigee on 2009-05-19
No, I've just run into the same thing.

grepped the config file (/etc/aide.conf) and dirs (/etc/aide.conf.d/*) for the word 'please-dont-call-aide-without-parameters', but couldn't find it.

Read the README.Debian.gz. No mention of it. Still struggling to configure this after 30mins, should have be done and dusted by now.

Daftness and fail from upstream I guess :)

--
Ross

---

### Post by rossigee on 2009-05-19
This helped...

[http://ubuntuforums.org/archive/index.php/t-1096333.html](http://ubuntuforums.org/archive/index.php/t-1096333.html)

This error message, on the other hand, did not (one more time, for the search engines)...

"Couldn't open file /var/lib/aide/please-dont-call-aide-without-parameters/aide.db for reading"

WTF! On my list of the top ten daft and misleading error messages ever. 

So, in summary of the original poster's questions...

> Can anyone interpret this?

No. Not unless you've either had prior experience of the problem, you're clairvoyant, or you're the developer/packager who designed it to work like that ;^)

> What did I do wrong?

You didn't. Like most people wanting to use AIDE, immediately after installing it you wanted to check it was configured and working. You tried to run 'aide --init' to initialise the database as explained in the vast majority of AIDE docs. However, unbeknown to you or me, it seems that you're supposed to wait for the daily cron job to run before you can actually start using AIDE as per the docs. Any attempt to try to use the 'aide' command before this, you get odd/misleading error messages.

> How do I run Aide? 

After running this, everything should work as per the docs...

$ sudo /etc/cron.daily/aide

However, it's still running, so I'm not sure if we're there just yet :)

--
Ross

---

### Post by rossigee on 2009-05-19
Ah, while Googling to find where to report this as a problem, I also came across this, which may help explain things...

[http://www.debuntu.org/intrusion-detection-with-aide](http://www.debuntu.org/intrusion-detection-with-aide)

---

### Post by ebischoff on 2012-10-16
Same problem here (Ubuntu 12.10), and doing as explained in the above links did not help.

However, the following worked out:
# apt-get install aide
# aideinit

Then, instead of "aide --check", you can run:
# aide.wrapper --check

All of this should at least be documented. Not saying that it would be better if aide could work as advertized in the documentation, and not only with the help of funny wrappers. :(

---

### Post by nothingspecial on 2012-10-16
Thanks for the information.

This thread is old and must be closed.

---

