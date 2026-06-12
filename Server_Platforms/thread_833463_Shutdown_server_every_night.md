---
title: "Shutdown server every night"
date: 2008-06-18
forum: Server Platforms
---

### Post by GSMX on 2008-06-18
Hi,

I have made some homeserver thingy, it's just some crappy old computer which i only use as fileserver and {sometimes} as webserver.

The pretty part: it's all working

The not so pretty part: I only use it when the sun shines, so this old power-consuming is using power and power every night for no purpose...

I know the command for shutting down at e.g. 23:00 is "sudo shutdown 23:00". But how can i execute this command (as root), every time i start the computer?

btw, it's server 7.10

---

### Post by MJN on 2008-06-18
There are many ways to skin this cat, but as an alternative to what you were asking it might prove more elegant to let cron turn the machine off according to schedule. Specifically, put the following into a file in /etc/cron.d/

```
# Cron job to turn the machine off at 2300hrs every night

# Send any error output to root for fault diagnosis
# (STDOUT will be redirected to /dev/null)
MAILTO=root

# Actual schedule/command
# Format: Min Hr DayofMth Mth DayofWk User Command
00 23 * * * root shutdown > /dev/null
```One advantage of doing it this way is that you could customise the schedule if, say, you wanted it to remain on later at the weekends etc.

Mathew

---

### Post by GSMX on 2008-06-19
thanks

it looks like it's working :)

and if i understand it right, i can just make these kind of tasks (any task) in /etc/cron.d/ just like some sort of task-manager? 

thanks again

---

### Post by MJN on 2008-06-19
That's right. I would recommend learning a little about cron as it is incredibly useful.
 
There are many other ways rolling cron to make it do what you want, including have personal 'crontabs' for each user, using the scheduled system cron jobs in /etc/cron.[hourly|daily|weekly]/ etc - as the administrator of my server I tend to use /etc/cron.d to allow me to have the granular control I require whilst also keeping my cron jobs all in one place.
 
Mathew

---

### Post by GSMX on 2008-06-19
ok, thanks for the advice!

---

