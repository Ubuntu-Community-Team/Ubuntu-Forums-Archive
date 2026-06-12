---
title: "apache server, multiple sites, detect which one is slowing down server"
date: 2013-07-19
forum: Server Platforms
---

### Post by sosojni on 2013-07-19
I have VPS with ubuntu server. Installed apache, mysql, zpanel etc. Got around 20 different domains working fine. 
suddenly, today, cpu usage goes up. Using top i can see that now and then, there is "php" service using 50% of cpu. Is it possible to trace that process to file that is starting it? I'd like to know which file / web site is slowing down my server.

---

### Post by SeijiSensei on 2013-07-19
Do you know which sites are using PHP?  Do you have any responsibiilty for the sites yourself or are you just hosting them?  

If a PHP script runs for a long term it often indicates a problem with the database being used.  One common problem is a poorly-indexed database with large numbers of records.  If the web application depends on pulling a set of records selected by unindexed fields, it can take a long time to process.

Have you tried visiting each site and watching to see what happens in top?  Maybe you can isolate the problematic site that way.

It's possible that a PHP script is running out of cron on a scheduled basis.  If so, it will be logged in /var/log/syslog. Also browse around in /etc/cron.*, /var/spool/cron/*, and /etc/crontab.

---

### Post by sosojni on 2013-07-19
All sites are using php. I did try to open every site and watched top but none of home pages are creating that effect (php service that goes for more than 50% of CPU). So i guess problem is somewhere in one of sites in some links that are away from homepage. I cant browse trough every single link on every single web page i host. I tought there is some kind of linux command like top, that would tell me not only services but files that actually started em.

---

### Post by SeijiSensei on 2013-07-20
There is the **lsof** command to "list open files."  That shows all the files each process has open.  However it won't help much in your case unless the high-CPU processes run for long enough that you can use lsof before the process dies.  Even then I'm not sure it will tell you much.

Do any of the sites have a search engine of some kind?  Maybe that isn't very well programmed.

If you can identify the times when the high-CPU processes are triggered, you could look in the site's access.log to see what HTTP request triggered the process.

---

### Post by sosojni on 2013-07-20
Oh thanks, ill look into that command. As it happens when i'm at work, and i monitor server all the time, i guess ill be able to catch it sooner or later. When it starts it lasts for few minutes.
And as far as logs go....i really hope i wont be forced to look trough logs of every and each site.

---

