---
title: "Reset MySQL root password"
date: 2010-09-07
forum: Server Platforms
---

### Post by devinsba on 2010-09-07
I have forgotten my root password for MySQL, what can I do to recover it, I've found a few guides but they don't work on the newer versions of Ubuntu.

I am running on Ubuntu 10.04 server so MySQL is an upstart job so the methods I've seen with launching it without the access checks haven't worked for me

---

### Post by DaithiF on 2010-09-07
Hi, theres not much different about the process under upstart.

1. stop mysql:
```
sudo stop mysql

```2. restart the mysqld daemon directly, following whichever of the init-file or skip-grant-tables methods you prefer, ie.
sudo /usr/sbin/mysqld --init-file=/path/to/filewithsqltoupdatepassword.sql
sudo /usr/sbin/mysqld --skip-grant-tables
(refer to one of the many guides you've probably already seen for more detail on these, note that the --init-file method is the preferred one)

3. kill the manually started mysqld, either ctrl+c if its running in the foreground, or ```
sudo kill -9 mysqld from another terminal

```4. restart mysql as normal using upstart:
```
sudo start mysql

```

---

### Post by fast_ian on 2010-09-14
Hi,

I'm sort of in the same boat - Except (FWIW) I have *no idea* how, why or when any pwd's got set during the install!....

Anyway, I too searched and found many "old" notes - I decided to go the "--skip-grant" route - This does indeed get me to the expected "mysql>" prompt, but:
[INDENT][COLOR=Blue]ian@BMW-Ubuntu:~$ mysql -u root[/COLOR]
[COLOR=Blue]Welcome to the MySQL monitor.  Commands end with ; or \g.[/COLOR]
[COLOR=Blue]Your MySQL connection id is 1[/COLOR]
[COLOR=Blue]Server version: 5.1.41-3ubuntu12.6 (Ubuntu)[/COLOR]

[COLOR=Blue]Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.[/COLOR]

[COLOR=Blue]mysql> SET PASSWORD FOR root@'localhost' = PASSWORD('a_real_pwd');[/COLOR]
[COLOR=Blue]ERROR 1290 (HY000): The MySQL server is running with the --skip-grant-tables option so it cannot execute this statement[/COLOR]
[COLOR=Blue]mysql> exit[/COLOR]
[COLOR=Blue]Bye[/COLOR]
[COLOR=Blue]ian@BMW-Ubuntu:[/COLOR]

[/INDENT]Help! - I did try stopping and restarting in "normal" mode, but still get the dreaded 1045 error, which is where we started of course.....
[INDENT]i[COLOR=Blue]an@BMW-Ubuntu:~$ mysql -u root[/COLOR]
[COLOR=Blue]ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)[/COLOR]
[/INDENT]TIA, cheers,
Ian

---

### Post by DaithiF on 2010-09-14
Hi, 
you can do:
```
update mysql.user set Password = Password('yourpassword') where user = 'root';

```
while in skip-grant-tables mode.

---

### Post by fast_ian on 2010-09-14
*Awesome* - Thanks dude!

It does seem "we" need to update the docs....

Thanks again, cheers,
Ian

---

