---
title: "Check who was logged in and what actions they performed"
date: 2010-09-14
forum: Security
---

### Post by prakharbansal on 2010-09-14
Hi All,

I am a novice to linux. I want to know the following details :-

1. What was the timestamps of login in few days?
2. Which users logged in?
3. What were the actions they performed on the system? Is it possible to list all the actions performed via terminal and gui interface? If yes than how?


Thanks and Regards,
Prakhar Bansal

---

### Post by amanjsingh on 2010-09-14
I believe you just need to look into this     /var/log/user.log . That has user activity.

---

### Post by BkkBonanza on 2010-09-14
You can find info about logins in the auth.log, eg.

less -S /var/log/auth.log

It will show you logins and privelage elevation and commands. But it won't show you everything a person does when acting within their normal rights. As far as I know there isn't a log for that. Some authentications messages also get sent to /var/log/messages.

You can see what users did at the command line by looking at their ~/.history file or with the history command (for current session) but this assumes they didn't wipe that out. I don't believe there is a log of any sort for GUI apps when run under normal user rights.

---

### Post by bodhi.zazen on 2010-09-14
To see who has logged in use 

last

w 

See also 

[http://www.cyberciti.biz/tips/howto-log-user-activity-using-process-accounting.html](http://www.cyberciti.biz/tips/howto-log-user-activity-using-process-accounting.html)

---

### Post by jhayes on 2010-09-20
i suppose if you are real paranoid,
you could install aide, and have it watch EVERYTHING
this will tell you of any file changes. 
actions, and gui actions performed, thats a toughie. others mentioned some log files, defiantly start there. but users shouldn't have rights to do anything good anyway.

---

### Post by luvshines on 2010-09-21
You may also try setting up 'audit server' [both locally or remotely] and collect various logs [controlled by audit rules] from the machine

---

