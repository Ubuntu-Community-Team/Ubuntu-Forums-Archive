---
title: "Apache or PHP keep logging out"
date: 2021-12-13
forum: Server Platforms
---

### Post by osavill-z on 2021-12-13
Hi, 

Since we moved from 16.04 to 20.04 our websites have developed a really annoying habit. Every 30 minutes they log users out. I've tried everything, but nothing seems to help. 

So far I've set all the parameters I can find to extend the PHP session lifetime, removed the sessionclean entry from /etc/crontab, reviewed /var/spool/cron/root and /var/spool/cron/www-data and found no mention of sessions.

To be honest, I don't know if this is Apache or PHP logging people out. Our systems run an in house developed PHP app, so there's no CMS getting in the way. My development machine also does this now after going from 18.04 to 20.04, I'm now running 22.04, and it still happens which makes me think this was a deliberate choice by Ubuntu, which is maybe why it's so difficult to switch off. 

I understand the reasons why 30 minutes may be a good idea, but it's not a good idea when we get logged out of the system midway through taking a telephone order! Please can someone help me sort this out? Ideally we'd like to make if twelve hours to cover everyone's working hours.

---

### Post by slickymaster on 2021-12-13
Thread moved to **Server Platforms** for a better fit

---

### Post by SeijiSensei on 2021-12-13
Does the web site use session cookies? How long is the cookie timeout?

---

### Post by osavill-z on 2021-12-14
Boy! Do I look silly now!! :-) I tracked down where the login takes place and some lines earlier were ini_set directives to set the session timeout to 1 hour, so the comments said, but some were one hour and some were two. So I've extended those out, and now it seems to be as it was before. I can only assume that despite the previous developer's ambitions Ubuntu 16.04's Apache and PHP basically ignored these values and gave only the illusion that it was 1 hour, and then, when it started working, despite my best efforts, obviously these ini_set directives overrode any external changes I made.

Is it also possible that Ubuntu 16.04's Apache and PHP used these for an hour of idle time, but now they are absolute times?

---

