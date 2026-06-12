---
title: "How to know which user created a user?"
date: 2012-08-27
forum: Server Platforms
---

### Post by albertdiones on 2012-08-27
The title says my question:

"How to know which user created a user?"

Thanks in advance.

---

### Post by diesch on 2012-08-27
Ubuntu doesn't store this information.

---

### Post by albertdiones on 2012-08-27
ok I see, thanks.

I was trying to know if I was the one that made the user that I thought didn't exist yet.

---

### Post by vandorjw on 2012-08-27
i am not sure if previous answer is correct. check /var/log/auth.log


root access is needed to create new users and all sudo commands are recodeded here.

i am currently in my droid and am unable to confirm if this can be checked but i suspect it is possible to track down. check when /etc/shadow and /etc/group were last modified then run a  search in auth.log against those dates and youll have an answers 


cheers cc7

---

### Post by diesch on 2012-08-27
That only works if you still have a *auth.log f*or the time the user was created (by default it's only kept for the last 4 weeks) *and* if the user was created  by GUI or only one admin had a root shell at that time[I].
[/I]

---

### Post by kennethconn on 2012-08-28
> **diesch said:**
> That only works if you still have a *auth.log f*or the time the user was created (by default it's only kept for the last 4 weeks) *and* if the user was created by GUI or only one admin had a root shell at that time*.*

 
Now that sounds like someone who knows EXACTLY what they're talking about.
 
That's the level of knowledge I'd love to have, but sadly, don't - hopefully it's correct!

---

### Post by koenn on 2012-08-28
>  if the user was created by GUI or only one admin had a root shell at that time.

> **kennethconn said:**
> Now that sounds like someone who knows EXACTLY what they're talking about.

well, the "EXACTLY" might not be exactly accurate.

obviously you can't check a log that has been rotated out of existence, but if you require a longer audit trail, you 'd have tweaked logrotate accordingly. Doesn't help after the fact, I know. 

I'm pretty sure sudo commands get logged with the username of the account that sudo'd, so I don't see where the "if only one admin had a root shell" remark refers to. I'd be interested to know, though. 

Quick test : I add an account, the log says:
```

Aug 28 20:30:14 mypc sudo:       me : TTY=pts/0 ; PWD=/home/me ; USER=root ; COMMAND=/usr/sbin/useradd pipo

Aug 28 20:30:14 mypc useradd[2092]: new group: name=pipo, GID=1003
Aug 28 20:30:14 mypc useradd[2092]: new user: name=pipo, UID=1002, GID=1003, home=/home/pipo, shell=/bin/sh

```


That wouldn't change if an other user ran another sudo command, would it ? (Though I understand you can obfuscate stuff by running root shells in stead of sudo commands)

---

