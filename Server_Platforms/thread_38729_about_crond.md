---
title: "about crond"
date: 2005-06-01
forum: Server Platforms
---

### Post by kimes on 2005-06-01
I've got a stupid question about cron daemon..
If I set up crontab like this

 0 1 * * * * /home/somescript.sh

, that means every 1:00AM run somescript.sh, right?

But what I'm curious is what would happen when PC is shutdown at that time?
Just ignored? or run as soon as I turn it on?

hehe...

---

### Post by thrift on 2005-06-01
I'm not exactly sure how this works, but I can tell you where you would find that out:

man anacron

---

