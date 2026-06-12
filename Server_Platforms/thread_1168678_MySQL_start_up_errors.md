---
title: "MySQL start up errors"
date: 2009-05-24
forum: Server Platforms
---

### Post by Omega234 on 2009-05-24
I seem to be having issues starting up my MySQL stuff (which worked absolutely fine before I turned off the computer before I went to bed).

I should note that I have my MySQL installed in a non-default location: /apps/mysql/.  I also do not (yet) have an init script for MySQL, so I start it manually.

The output is as follows:

```
/apps/mysql/$ ./bin/mysqld_safe --user=mysql &
[1] 3123

[COLOR="Blue"]/apps/mysql/$[/COLOR] [COLOR="Red"]090524 09:04:11[/COLOR] mysqld_safe Logging to '/var/lib/mysql/omega-ubuntu-server.err'.
touch: cannot touch '/var/lib/mysql/omega-ubuntu-server.err': No such file or directory
chown: cannot access '/var/lib/mysql/omega-ubuntu-server.err': No such file or directory
[COLOR="Red"]090524 09:04:11[/COLOR] mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
./bin/mysqld_safe: line 100 /var/lib/mysql/omega-ubuntu-server.err: No such file or directory
./bin/mysqld_safe: line 137: /var/lib/mysql/omega-ubuntu-server.err: No such file or directoroy
[COLOR="Red"]090524 09:04:11[/COLOR] mysqld_safe mysqld from pid file /var/run/.mysqld/mysqld.pid ended
./bin/mysqld_safe: line 100 /var/lib/mysql-omega-ubuntu-server.err: No such file or directory
```
And then it hangs, so I push return and get:
```
[1]+ Exit 1     ./bin/mysqld_safe --user=mysql
```

The blue above is just my prompt being printed, but I guess it's being printed while the script is executing?  I didn't think it was important, but I left it for integrity.  Same with the stuff in red, which occurs a few times in the errors.  The 09:04:11 was the time that the command was run.

I looked in the mysqld_safe file and tried changing a few lines so it would state different locations for the files:

```
pid_file=/apps/mysql/var/omega-ubuntu-server.pid
err_log=/apps/mysql/var/omega-ubuntu-server.err
```

(Originally there was nothing after each '='.)

After that it did:

```
/apps/mysql/$ ./bin/mysqld_safe --user=mysql &
[1] 3396

/apps/mysql/$ 090524 09:15:14 mysqld_safe Logging to '/apps/mysql/var/omega-ubuntu-server.err'.
090524 09:15:14 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
090524 09:15:14 mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended

[1]+ Done     ./bin/mysqld_safe --user=mysql
```

So at this point I think the .err problem is fixed, but what about the .pid?  Any ideas, please?  Thanks in advance for anything!

---

### Post by Vegan on 2009-05-24
I suspect there may be some corruption of the volume.

Try

```
sudo fsck
```

and see if that helps.

---

### Post by Omega234 on 2009-05-24
Well I've been messing with it for a few hours, and I've come up somewhat better (though it still isn't running properly).

It seems that MySQL simply didn't know where it was installed.  So I had to create softlinks in various places to get it to go back to the actual directory, /apps/mysql.  (It wasn't until after that I realized that most of the directories are defined in my.cnf.)

I have now managed to make it so that MySQL can run.  However, no other program (phpMyAdmin, the wiki I have set up, or the PHPBB forum I have) is able to connect to the MySQL server.  The most descriptive thing I've discovered is the error returned by the wiki:

[quote=wiki]Sorry! This site is experiencing technical difficulties.

Try waiting a few minutes and reloading.

(Can't contact the database server: Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2) (localhost))[/quote]

Which tells me (I think) that everything else thinks the socket will be in /tmp, but MySQL places it in /var/run/mysqld/mysqld.sock.  I tried modifying my.cnf so that "/var/run/mysqld/mysqld.sock" was replaced with "/tmp/mysqld.sock", but it didn't work.  (Nothing seems different, actually.)

So are there any ideas for how to fix this socket location error?  Any help is greatly appreciated.

PS @ Vegan:
If I type "fsck", I get this:
```
# fsck
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda1 is mounted.

WARNING!!!  Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.

Do you really want to continue (y/n)?
```
I wasn't sure if that was really supposed to happen or not, so I just said no.  I don't think it's a corruption error so much as MySQL simply not knowing where it exists.  I'd guess (possibly amaturely) that the MySQL install created a temporary environment variable telling MySQL where to look for stuff, and then since I restarted it, the variable doesn't exist anymore (so MySQL looks in all the "usual" places).  Just a guess, though.

---

### Post by Vegan on 2009-05-24
ok try this:

```

sudo touch /forcefsck
sudo shutdown -r 0

```
this will reboot the machine and run the check at the next reboot

---

### Post by Omega234 on 2009-05-24
I got all the regular startup notifications, then:

```
 * Checking root file system...
fsck 1.41.4 (27-Jan-2009)
/dev/sda1: 86201/3629056 files (2.6% non-contiguous), 797324/14492630 blocks
     [ OK ]
 * Checking file systems...
fsck 1.41.4 (27-Jan-2009)
     [ OK ]
 * Mounting local filesystems...
```
et cetera.  So I guess that means that nothing went wrong.  Thanks for the try, though!

I'm fairly certain at this point that it's just a MySQL problem.  I don't think the socket is where it's supposed to be (or something like that...).

---

