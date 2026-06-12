---
title: "Cron emailing root@true"
date: 2008-01-03
forum: Server Platforms
---

### Post by mbower on 2008-01-03
Does anyone have any idea how I can redirect Cron to another email address instead of root@true? 

Here is what I am getting: 

[INDENT]Subject: Cron <root@**machinename**> test -x /usr/sbin/anacron || run-parts --report/etc/cron.daily
Date: Sat, 29 Dec 2007 04:25:36 -0700
Message-ID: <E1J8Zor-00015c-HF@**machincename**.**company**.wan>
From: "Cron Daemon" <root@true>
To: <root@true>

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/lockmail.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/preline.1.gz is a dangling symlink[/INDENT]

I replaced the actual machine name and company with the words in bold. 

I have looked everywhere and can't find where I can point these emails to another email address.  I went through the config process for Exim4, so the @true should be fixed but I still need to replace root with another email address.  

Exim4 is configured to send only (mail sent by smarthost).

---

### Post by andol on 2008-01-03
Well, standard for cron is to e-mail the user which runs the job in question.

One workaround, if you don't read your root-mail is to redirect it to another user or address. Is that a good solution, or do you explicit want cron to send merely these jobs to another address?

---

### Post by kebes on 2008-01-03
If you want all the cron jobs to be sent to some other email address, you can put a "MAILTO" directive in your crontab file. For instance:
```
sudo nano /etc/crontab
```
And add the line (or edit if already there):
```
MAILTO="bob@whatever.com"
```
This will send all emails to [email]bob@whatever.com[/email] (replace with whatever email address you want!). This requires sendmail to be working properly on that system, of course.

If you want different cron tasks to email to different addresses you'll need a different approach, of course...

---

### Post by mbower on 2008-01-03
thanks!!

That should work perfectly.  

I forgot about MAILTO.

I will update with [solved] once I verify that it will work.

---

### Post by dante on 2008-01-03
another alternative is to create a file called .forward
in /root  You can list
one or more email addresses in the .forward file. Any mail
would go to those addresses.

In your case, kebes' solution may be better, as it deals
only with mail generated from cron.  

.forward files come in
handy if you want to get more granular (each user can
have one in their respective home directories), and cover
mail from any source on the server.

---

