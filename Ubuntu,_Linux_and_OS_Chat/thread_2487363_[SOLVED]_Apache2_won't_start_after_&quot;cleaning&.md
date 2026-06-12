---
title: "[SOLVED] Apache2 won't start after &quot;cleaning&quot; cache and logs with Stacer"
date: 2023-06-01
forum: Ubuntu, Linux and OS Chat
---

### Post by something-amazing on 2023-06-01
Be warned that Stacer doesn't just free up hard drive space. It completely removes the /var/log/mysql and /var/log/apache2 directories! Apache2 won't start until these directories and their associated log files are recreated.

I am posting this here, because I cannot believe that such a seemingly refined and widely used app does so much damage. Anyway, if you, like me, used Stacer to free up hard drive space by "cleaning" app logs. You can easily rebuild your log structure and restart your services using the following commands:

```
sudo mkdir /var/log/mysql 
sudo touch /var/log/mysql/error.log
sudo chown -R mysql:mysql /var/log/mysql
sudo systemctl restart mysql

sudo mkdir /var/log/apache2/
sudo touch /var/log/apache2/{access,error,other_vhosts_access,suexec}.log
sudo chown -R root:adm /var/log/apache2/
sudo chmod -R 750 /var/log/apache2
sudo systemctl restart apache2
```

---

### Post by TheFu on 2023-06-01
Should we assume that you've solved the issue?  If so, please mark this thread as **SOLVED** using the thread tools button, so others having a similar issue can find it easier.

---

### Post by something-amazing on 2023-06-01
You are correct, but I see no "Mark as Solved" option under Thread Tools. I see only, Show Printable Version, Subscribe To This Thread, and Add Poll To This Thread. A quick search led me to other threads asking how to mark as solved. It seems that the option is currently not available, hah, so I just added '[SOLVED]' to the title, not sure if that is sufficient.

If a moderator sees this, please feel free to move this thread to a more appropriate forum, such as General Help.

---

### Post by TheFu on 2023-06-01
Actually, solutions belong in the "How-To" sub-forum.
Perhaps your account here doesn't have sufficient posts to mark threads SOLVED?  That would be surprising, since only the person who starts a thread can mark it SOLVED.

---

