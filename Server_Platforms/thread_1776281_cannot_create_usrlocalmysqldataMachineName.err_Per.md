---
title: "cannot create /usr/local/mysql/data/MachineName.err: Permission denied"
date: 2011-06-05
forum: Server Platforms
---

### Post by mohaaron on 2011-06-05
I had installed the binary a while ago. Some time back in march mysql stopped auto starting and when I try to manually start I get this error message. It seems like a permission problem and I have been searching for an answer off and on for months now. When trying to start mysql I get this error and the .pid file is also never created.

```
username@MachineName:/usr/local/mysql/bin$ mysqld_safe --user=mysql &
[2] 7674
aaron@aaron-Inspiron-9300:/usr/local/mysql/bin$ 110605 18:32:21 mysqld_safe Logging to '/usr/local/mysql/data/MachineName.err'.
110605 18:32:21 mysqld_safe Starting mysqld daemon with databases from /usr/local/mysql/data
/usr/local/mysql/bin/mysqld_safe: 739: cannot create /usr/local/mysql/data/MachineName.err: Permission denied
eval: 1: cannot create /usr/local/mysql/data/MachineName.err: Permission denied
110605 18:32:21 mysqld_safe mysqld from pid file /usr/local/mysql/data/MachineName.pid ended
/usr/local/mysql/bin/mysqld_safe: 783: cannot create /usr/local/mysql/data/MachineName.err: Permission denied
^C
[2]-  Exit 2                  mysqld_safe --user=mysql
```

Anyone have any idea's?

---

### Post by SeijiSensei on 2011-06-06
What user owns /usr/local/mysql?  What user does mysqld run as?

In a standard configuration like Ubuntu's, the server runs as the user:group "mysql:mysql" and that user and group own the entire /var/lib/mysql tree.  

You're starting the server as user "aaron" it appears.  

Why not just run the standard MySQL available in the Ubuntu repositories and let it handle all this for you?

---

### Post by mohaaron on 2011-06-06
I'm at work now or I would copy past the results of ls -al but the /usr/local/mysql tree is owned by mysql:mysql. I followed the directions for installing the latest generic binary last January. It ran fine for months and then suddenly started having this problem.

The mysql server runs under the mysql user as per the directions. I am logging into ubuntu as aaron. I didn't install the packaged version at the time because it was not up to date with the latest release which I wanted for some new features.

I'm fairly new to Linux and so I didn't know what information to post to help solve the problem. Should I next post the results of the ls -al command for the related directories? Please let me know what information would help to solve this.

Thank you

---

### Post by SeijiSensei on 2011-06-06
I'd install the version from the repositories if it now has the features you need.  Then copy the contents of /usr/local/mysql/data to /var/lib/mysql/data and start mysqld.  It should either start right up, or it may update the format of the databases first, then start.

---

### Post by mohaaron on 2011-06-06
Unfortunately mysql 5.5 is still not available as a package. This is why I installed the binary. I would really prefer to get the binary working again. It worked when I first installed it. So what happened? Do I need to go through the process of uninstalling the binary and then reinstalling it?

---

