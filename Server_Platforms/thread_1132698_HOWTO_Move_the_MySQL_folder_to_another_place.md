---
title: "HOWTO: Move the MySQL folder to another place"
date: 2009-04-22
forum: Server Platforms
---

### Post by fixitdude on 2009-04-22
MySQL puts it's data in /var/lib/mysql and on some setups the /var directory is in it's own (small) partition, so if you use MySQL for a lot of data you can easily run out of space. I'm trying to plan ahead before it gets too big.

I just did this and found out there's a few tricks when doing this on a Ubuntu system, so before I forget, here's the easiest way to do it.

On Ubuntu there's a security feature called "AppArmor", you have to understand that it restricts what directories a network application like MySQL can access. So if you are using Ubuntu, you must change it's configuration in order for this to work.

The other thing is that MySQL must be completely stopped. So do a "ps ax" to make sure that it's not running after you issue the stop command shown below.

Use mysqldump or phpmyadmin (via browser) to BACKUP ANY DATABASES YOU HAVE. You could also use the "cp -dpR" command to make a copy of the /var/lib/mysql directory just in case.

Enter each command here one at a time to be safe and check things after each step, UNDERSTAND WHAT YOU ARE DOING HERE BEFORE PROCEDING, this is what I did and it worked for me, you may be a idiot and get different results, if you are a idiot don't try this. PLEASE STOP NOW IF YOU ARE STUPID. YOU HAVE BEEN WARNED.

I ask again, did you BACKUP your data?
```

sudo su -          (then enter root password of course)
cd /var/lib
mkdir /home/mysqldata
/etc/init.d/mysql stop       (or mysqld stop depending on system)
mv mysql/ /home/mysqldata/
ln -s /home/mysqldata/mysql
chown -h mysql:mysql mysql

```

Now to fix "AppArmor". Open "/etc/apparmor.d/usr.sbin.mysqld" in your favorite editor that you use for this sort of stuff, non line wrapping!
```

gedit /etc/apparmor.d/usr.sbin.mysqld
--- or ---
vi /etc/apparmor.d/usr.sbin.mysqld

```
Look for the lines with /var/lib/mysql in them, then add two more lines for /home/mysqldata/mysql just like those, that section looked like this when I was done, yours may look the same but you never know in the future so just do what they had in the other lines:
```

  /var/lib/mysql/ r,
  /var/lib/mysql/** rwk,
  /home/mysqldata/mysql/ r,
  /home/mysqldata/mysql/** rwk,

```

It doesn't really hurt to leave the old lines in there, and it lets you go back to the way it was easier.

Save the file and "reload" AppArmor and start MySQL again. If starting it fails, try looking at the logs to figure out what happened. Check all the directories and make sure the symbolic link is in place. If something restarted MySQL while you were doing this you may have problems, find out what is automatically starting it up, a stock desktop install of Ubuntu shouldn't be restarting it.
```

/etc/init.d/apparmor reload
/etc/init.d/mysql start          (or mysqld depending on system)

```
Check "tail -20 /var/log/messages" to see if there are any errors after you start MySQL back up, just in case.

If all goes well, exit root.

To reverse this just remove the symbolic link and move the mysql directory back where it was.

---

