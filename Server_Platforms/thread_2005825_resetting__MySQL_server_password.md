---
title: "resetting  MySQL server password"
date: 2012-06-18
forum: Server Platforms
---

### Post by anon0 on 2012-06-18
I tried to update my password in phpmyadmin but it failed because now I can't log in with either the new or the old password. I need to reset the password by command prompt. Some tips on which commands to use?

---

### Post by rubylaser on 2012-06-18
[This]("http://www.cyberciti.biz/tips/recover-mysql-root-password.html") should do it for you.

---

### Post by anon0 on 2012-06-18
> **rubylaser said:**
> [This]("http://www.cyberciti.biz/tips/recover-mysql-root-password.html") should do it for you.

Thanks so much, my password seems to work now.

Although, I'm not sure if mysql is listening when I ask it to stop. I ran "/etc/init.d/mysql stop" (with and without sudo). It returns: 
```
Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service mysql stop

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the stop(8) utility, e.g. stop mysql
```

Some say that's just a suggestion, and that it should have done its job stopping the program anyway. 

So I ran "ps aux | grep mysql" to check if it's been shut down as someone suggested, but there are still things listed there like "sudo mysqld_safe --skip-grant-tables" "/bin/sh /usr/bin/mysqld_safe --skip-grant-tables", etc. 

I ran "service mysql stop" and it says "stop: Unknown instance:" (followed by a blank line). 

A moment ago (when I was resetting my password), mysql seemed to have stopped correctly when asked to, but not anymore. 

Sorry, but does this make sense to anyone?

---

### Post by CharlesA on 2012-06-18
```
sudo service mysql stop
```

If that doesn't work, try this:

```
ps aux | grep mysql
```

It showed this for me:

```
 /usr/sbin/mysqld
```

It worked for me:

```
charles@Precise:~$ sudo service mysql stop
mysql stop/waiting
charles@Precise:~$ sudo service mysql start
mysql start/running, process 4069

```

---

### Post by anon0 on 2012-06-18
Alright I think the problem was the bunch of zombie mysql processes that didn't die properly. This also confused the stop command which took over a minute to run. I killed those old processes and now mysql appears to start and stop as expected. Thanks everyone!

---

### Post by LHammonds on 2012-06-19
On Ubuntu 10.04, the proper way to stop MySQL is **/etc/init.d/mysql stop**

On Ubuntu 10.04, the repository version for MySQL is 5.1

On Ubuntu 12.04, the proper way to stop MySQL is **service mysql stop**

On Ubuntu 12.04, the repository version for MySQL is 5.5

Prefix the commands with "sudo" if you do not login as root or did not temporarily become root using "sudo su"

**[COLOR=black]EDIT:[/COLOR]** Don't forget to mark your thread as "SOLVED"

LHammonds

---

