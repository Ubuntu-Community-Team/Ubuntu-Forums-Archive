---
title: "What is the best method for regular mysql backups?"
date: 2011-07-20
forum: Server Platforms
---

### Post by wsonar on 2011-07-20
I created a cron and a shell script but I'm not sure how to automatically handle the mysql password prompt. I'm sure it's simple but having trouble figuring it out

---

### Post by ruffEdgz on 2011-07-20
To complete a mysql_dump without a password, read this blog:

[http://blog.bigsmoke.us/2010/08/11/setting-password-for-mysql-user-in.my.cnf](http://blog.bigsmoke.us/2010/08/11/setting-password-for-mysql-user-in.my.cnf)

It still works today since I am doing this for a view other DB's I manage without a problem.

Depending on who is running the cronjob (root or another user), the .my.cnf file will need to be in that persons homedir.

Once that is complete, it should be way easier to complete your mysql dump without the password being inside the cron job file.

---

### Post by wsonar on 2011-07-20
Thank you I will investigate this

---

### Post by rubylaser on 2011-07-20
SeijiSensei posted a nice script he uses a while ago. [http://ubuntuforums.org/showpost.php?p=9882114&postcount=5]("http://ubuntuforums.org/showpost.php?p=9882114&postcount=5")

---

### Post by SeijiSensei on 2011-07-21
> **rubylaser said:**
> SeijiSensei posted a nice script he uses a while ago. [http://ubuntuforums.org/showpost.php?p=9882114&postcount=5]("http://ubuntuforums.org/showpost.php?p=9882114&postcount=5")

Thanks!  You'll notice that script includes the root password, though.  I recommend giving it 0700 permissions if you choose to use something like my script.

---

### Post by wsonar on 2011-08-02
cool thanks

---

### Post by Wim Sturkenboom on 2011-08-02
In my opinion, any showing of a password in a script or config file is bad habit.

Therefore I'm personally more in favour of a dedicated mysql user without a password that only has sufficient permissions to achieve the goal. Does not need e.g. insert, create, drop etc permissions; I think *select* and *lock tables* privileges should be enough.

---

