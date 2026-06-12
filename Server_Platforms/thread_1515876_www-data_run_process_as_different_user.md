---
title: "www-data run process as different user"
date: 2010-06-23
forum: Server Platforms
---

### Post by myrky on 2010-06-23
Hello, I'm new to these forums so I'm not sure this is the right place for this topic.

So, my question/topic thing is:
I have a PHP script that runs on an apache2 web server (www-data).
From this script, i want to launch a process that stays alive all the time, but the parent script keeps on going. So I think I will need to run a command like 'at' to put the process on a queue, and the script can continue and finish, without waiting for the process to stop. But it seems like I will need to run the 'at' command as a different user, because www-data stops the 'atd' process. I'm not sure about that. Does anybody know how this could happen?

---

### Post by Deadpan110 on 2010-06-23
There are several things you can do:

1: Change the user apache runs as - this is fine if your web service only needs 1 user
nano /etc/apache2/envvars

2: Rather than changing the user, make use of suphp so that php is run as the owner/group of the php script (mod_php needs to be removed from enabled modules)

3: Perhaps the best way and safest would be to simply use your webpage to create a todo list in a database and then get a cron script to run every minute as the required user - if there is a job, do it and delete the entry from the database.

---

### Post by myrky on 2010-06-23
Thank you for the quick response.
Your ideas are good, but I'm not sure that I've fully understood them. :P
So, what I actually want to do is to create a control panel and the user can push a button that starts a new server/program. That server/program has to stay running all the time, while the PHP script that starts it won't wait for it to finish. Now the database idea seems cool, but what script will be checking the database?

---

