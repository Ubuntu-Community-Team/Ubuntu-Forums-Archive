---
title: "Delete old folders"
date: 2015-09-10
forum: Ubuntu Application Development
---

### Post by asterix108 on 2015-09-10
Hello :)

I think if anyone knows how to write a script with the requirements below it will not be a big hassle.

Therefore, it would be great if someone could write this script.
Because my skills are not enough. I have only basic Shell skills.

Either with Shell or another scripting language that can be installed in Ubuntu.

$days=6
$number_folders=5
$backup=path

If more then $number_folders folders are in $backup, folders that are older than $days should be deleted.
The recent / current $number_folders folders should be remain in $backup.

Example one:
There are 10 folders in $backup. 7 folders older then $days. 3 are younger then $days
Desired result:
There should be 5 folders in $backup: The three younger and 2 which are older.

Example two:
In $backup are 5 folder which are older than $days.
Desired result:
It should remain all 5 folders in $backup.

Thanks in advance.

---

### Post by tgalati4 on 2015-09-11
There is already a facility to perform this.  Open a terminal:

```
man logrotate
man logrotate.conf
```

Spacebar to page forward, "q" to quit.

Some examples:  [http://askubuntu.com/questions/461413/rotating-a-log-file-in-my-home-directory-on-ubuntu-server-14-04-lts](http://askubuntu.com/questions/461413/rotating-a-log-file-in-my-home-directory-on-ubuntu-server-14-04-lts)

Look at your existing rotation entries:

```
cd /etc/logrotate.d
ls
cat apt
cat aptitude
cat consolekit
cat cups-daemon

```

Add your own, with the correct settings, then reboot.  The new entries should now take effect.  

Search the web for *logrotate* tutorials. [http://www.thegeekstuff.com/2010/07/logrotate-examples/](http://www.thegeekstuff.com/2010/07/logrotate-examples/)

and [http://www.rackspace.com/knowledge_center/article/understanding-logrotate-utility](http://www.rackspace.com/knowledge_center/article/understanding-logrotate-utility)

---

