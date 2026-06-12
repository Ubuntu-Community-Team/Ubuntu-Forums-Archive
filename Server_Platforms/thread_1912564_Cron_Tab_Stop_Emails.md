---
title: "Cron Tab Stop Emails"
date: 2012-01-20
forum: Server Platforms
---

### Post by dr1134 on 2012-01-20
My server runs a Minecraft server.

I use crontab to have the Minecraft server backup every 30 minutes.

However every 30 minutes an email is sent to the root that the script has ran and what its output is.

It is kind of annoying having my email client go ding every 30 minutes. 

All I care about is when it did not run. Is there a way that I could set cron to send an email if there was an error along with the output of that script?

---

### Post by collisionystm on 2012-01-20
> **dr1134 said:**
> My server runs a Minecraft server.

I use crontab to have the Minecraft server backup every 30 minutes.

However every 30 minutes an email is sent to the root that the script has ran and what its output is.

It is kind of annoying having my email client go ding every 30 minutes. 

All I care about is when it did not run. Is there a way that I could set cron to send an email if there was an error along with the output of that script?

Post the script

---

### Post by dr1134 on 2012-01-20
The script I use is called Multi World

The script can be seen [here]("https://mcshellscript.svn.sourceforge.net/svnroot/mcshellscript/trunk/minecraft_server")

---

### Post by collisionystm on 2012-01-20
Where did you specify your email address? I see no where in this script to put it

---

### Post by dr1134 on 2012-01-20
Every 30 mins this script is ran by crontab. Each time crontab runs this script it sends an email to the local root account email box with the output of the script.

I need to find a way to set crontab to only send an email if there was an error

---

### Post by rubylaser on 2012-01-20
All you need to do is redirect the STDOUT to /dev/null.  You will still be able to get alerts from STDERR.  Something like this...

```
*/30 * * * * /path/to/multi_world.sh > /dev/null
```

---

### Post by dr1134 on 2012-01-20
Ok

So all the output will go to /dev/null

And all the errors will be sent as an email

Thanks for that

---

### Post by rubylaser on 2012-01-21
No problem, don't forget to mark the thread as solved under the Thread Tools at the top.

---

