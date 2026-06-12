---
title: "Runs commands at a scheduled time"
date: 2010-10-20
forum: Server Platforms
---

### Post by SirMeaky on 2010-10-20
Hey, I am running Ubuntu Server 9.04 and I was wondering, how would I setup scripts that run a certain command at a certain time?

Also would I be be able to run multiple commands? For example once one of the commands has finished running could it start another command straight after?

Thanks :)

---

### Post by utnubuuser on 2010-10-20
read up on "Cron"

---

### Post by Ryan Dwyer on 2010-10-20
You need to edit /etc/crontab.

You can do stuff like: command1 && command2 # which will only run command2 if command1 succeeds. If you want to run command2 regardless of whether command1 worked, use a bash script.

---

