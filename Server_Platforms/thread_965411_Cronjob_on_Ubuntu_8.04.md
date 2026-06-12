---
title: "Cronjob on Ubuntu 8.04"
date: 2008-10-31
forum: Server Platforms
---

### Post by wattaman on 2008-10-31
Hello!
Can someone tell me, please, how to set a cronjob from within webmin? Or the SSH command?
I want to run this file */home/username/domains/domain.com/public_html/includes/promo.php* every 5 hours and nothing seems to work.
Thank you!

---

### Post by vpsville on 2008-10-31
In your /etc/crontab

0 */5 * * * root /usr/bin/php  /home/username/domains/domain.com/public_html/includes/promo.php >> /dev/null

Make sure you can run that php file from the command line first, or cron won't be able to do it either.

---

### Post by wattaman on 2008-11-01
> **vpsville said:**
> In your /etc/crontab

0 */5 * * * root /usr/bin/php  /home/username/domains/domain.com/public_html/includes/promo.php >> /dev/null

Make sure you can run that php file from the command line first, or cron won't be able to do it either.

The script won't run from SSH. I've navigated, as root, to the folder where promo.php is and typed *./promo.php* - according to the script's README should work. Instead I get the:
> bash: ./promo.php: /usr/local/bin/php^M: bad interpreter: No such file or directory

Any ideas why this? All files are there, btw, nothing is missing.
Thank for the cron code!

---

### Post by MJN on 2008-11-01
^M is the control code for a carriage return. Linux doesn't use these (it uses line feeds by themselves) to indicate the end of each line and so it sounds like you wrote this script in DOS/Windows.

There are many ways to convert it (i.e. replace CR/LF combinations with a single LF) but the easiest for you to remember/use might be the dos2unix and unix2dos commands. Install them with **sudo apt-get install tofrodos** then convert your script with **dos2unix promo.php**

Mathew

---

### Post by wattaman on 2008-11-01
> **MJN said:**
> ^M is the control code for a carriage return. Linux doesn't use these (it uses line feeds by themselves) to indicate the end of each line and so it sounds like you wrote this script in DOS/Windows.

There are many ways to convert it (i.e. replace CR/LF combinations with a single LF) but the easiest for you to remember/use might be the dos2unix and unix2dos commands. Install them with **sudo apt-get install tofrodos** then convert your script with **dos2unix promo.php**

Mathew

Thanks, m8. I've installed the tofrodos but didn't do the trick. It wasn't a script wroten by me, I'm a noob actually :)
Anyway, forget about it. I'll just look for another similar script that will, hopefully, work.
Thx again

---

### Post by MJN on 2008-11-01
Don't be so quick to give up!

What error do you get now?

Mathew

P.S. I am assuming you have PHP installed? (**sudo apt-get install php5-cli**)

---

### Post by Thirtysixway on 2008-11-02
Under webmin, you can go to

System > Scheduled Cron Jobs

and you can click Create a new scheduled cron job.  Simple.

---

### Post by wattaman on 2008-11-19
Done that, still nothing. The script doesn't do its job and, in webmin, I got the 
> /bin/sh: /home/username/domains/domain.com/public_html/includes/promo.php: /usr/local/bin/php: bad interpreter: No such file or directory


---

### Post by MJN on 2008-11-19
Change any instance of /usr/local/bin/php to /usr/bin/php in your script - it has been written for a different platform (where the location of the PHP command interpreter is different).

Don't you think it would've been worthwhile posting the contents of this script given you've been struggling with it for several weeks now?

And, please, do answer the questions we ask - they are asked for a reason in order so that we can help you.

Mathew

---

### Post by wattaman on 2008-11-19
> **MJN said:**
> Don't be so quick to give up!

What error do you get now?

Mathew

P.S. I am assuming you have PHP installed? (**sudo apt-get install php5-cli**)
Well, you were right... in the end. After I run the 
*sudo apt-get install php5-cli* the cron started to work just fine.
Thank you all!

---

