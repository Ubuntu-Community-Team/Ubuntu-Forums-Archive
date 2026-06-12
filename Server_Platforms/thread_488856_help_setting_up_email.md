---
title: "help setting up email"
date: 2007-06-30
forum: Server Platforms
---

### Post by borahshadow on 2007-06-30
Hi I have a server acting as a file server I have 2 drives in a RAID1
I want to setup cron to scan everything with clamav every so often and cron will email if the command fails or has an error(from what I've read) I also want to setup the script that cron runs to email me the results of the scan. also I want mdadm to email me in case a drive fails

But to have this email working my friend told me I have to set up exim
So I tried googleing  but I'm confused and don't know what to do I have installed exim4 and ran dpkg-reconfigure exim4 but I think I configured it wrong because I didn't really know what I was doing

Here is what I want need
exim (or other MTA) to be able to send email to any email (gmail specifically)
I have several gmail accounts so if exim needs to use one of those to send that is ok (smtp is enabled on all my gmail accounts)

also how do you send email from the command line? like how would you pipe the output of a command to an email?
thanks for all your help
I won't be able to check back for a few days but I appreciate all the help this great community is :)

---

### Post by borahshadow on 2007-07-03
bump
anybody surely sombody has similar needs and has set this up thanks

---

### Post by borahshadow on 2007-07-03
Oh I just found this in the man pages for cron 
>        When executing commands, any output is  mailed  to  the  owner  of  the
       crontab (or to the user named in the MAILTO environment variable in the
       crontab, if such exists).
Now if someone could just help me set up exim or anyother MTA so that cron can email to me I would appreciate it

I think I finally figured it out but for other people who are having trouble with sending mail through smtp to gmail smtp.gmail.com doesnot work with exim it is just an alias to gmail-smtp.l.google.com (run ```
host smtp.gmail.com
```)

---

### Post by gabrielsaldana on 2008-07-04
Have you managed to configure exim4 for these needs? I have similar needs of sending and recieving email from command line and cant figure it out.

---

