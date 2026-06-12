---
title: "SSH backup utility for linux"
date: 2005-04-06
forum: Server Platforms
---

### Post by Jujimufu on 2005-04-06
Hi.  I run a vbulletin forum like this one at ubuntu, not quite as large.  The database is now too big to backup using their standard methods and I was advised to backup using an SSH utility.  I'm wondering what utility for linux would be best for this task? I checked Synaptic for some programs, but didn't really know what from what. Thanks.

---

### Post by HungSquirrel on 2005-04-06
Perhaps they are talking about using SSH to create a tar.bz2 of important files and databases and transfer them securely to another box.  Other than that, I don't know.

Before my server goes live I'm going to write a shellscript that makes a tar.bz2 of my /var/www directory and transfers it to my desktop machine once a week via a cron job, or something similar.  If anyone has any backup advice/ideas, do share.  :)

---

### Post by alastair on 2005-04-06
Not sure what they mean.

But "scp" works like "cp", so you can securely copy directory structures from one place/machine to another.

Alternatively, you could use something like "rsync" to synchronise directories between two systems (possibly both remote).

---

### Post by Jujimufu on 2005-04-06
What they mean?  Well here are the instructions they have given for backing up using an SSH client:

> 
n order to back up your database via SSH or Telnet you will require 2 things:

1) SSH or Telnet access to your site. You will need to check with your hosting company to see if this is available.

2) An SSH/Telnet Client, such as PuTTy.


I'm pretty sure PuTTy is a windows utility.  I'm looking for a linux utility.

---

### Post by HungSquirrel on 2005-04-06
Heh, the Linux utility is called 'ssh'.  ;)  (By the way, you can get putty for Linux.)

vBulletin is assuming you have your website at a host and need to SSH in to administer it.  Since you sound like you are unfamiliar with SSH, I gather you are running the server on your desktop machine?  In that case all you need to do is create backups regularly using a shellscript that is called by a cron job.  Of course, you need to learn to write shell scripts and set up cron jobs to do that.  ;)

I assume the database you are using is a MySQL one?

[http://dev.mysql.com/doc/mysql/en/backup.html](http://dev.mysql.com/doc/mysql/en/backup.html)

Edit: Off topic, but what part of Alabama are you from?  I'm from Mobile.

---

### Post by Gandalf on 2005-04-06
to backup using SSH it's simple
```

mysqldump -u <<user>> -p <<database>> > <<file>>

```
where <<user>> is te username
<<database>> your database name
<<file>> your file

example
```

mysqldump -u root -p smo > smo.sql

```

get the smo.sql file

to restore it's too simple too
```

mysql -u <<user>> -p <<database>> < <<file>>

```
where <<user>> is te username
<<database>> your database name
<<file>> your file

example
```

mysql -u root -p smo < smo.sql

```

PAY ATTENTION to the direction of the output/input (symbol < or > direction)
good luck!!

---

### Post by deuce868 on 2005-04-07
I would suggest using a script to backup the mysql files like this one:
[http://members.lycos.co.uk/wipe_out/automysqlbackup/](http://members.lycos.co.uk/wipe_out/automysqlbackup/)

Then I would suggest setting up rsync to create a copy of your backup folder onto another machine. 

[http://www.google.com/search?q=how+to+backup+with+rsync+linux&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial](http://www.google.com/search?q=how+to+backup+with+rsync+linux&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial)

HTH

---

### Post by Gandalf on 2005-04-07
[QUOTE=deuce868]I would suggest using a script to backup the mysql files like this one:
[http://members.lycos.co.uk/wipe_out/automysqlbackup/](http://members.lycos.co.uk/wipe_out/automysqlbackup/)

Then I would suggest setting up rsync to create a copy of your backup folder onto another machine. 

[http://www.google.com/search?q=how+to+backup+with+rsync+linux&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial](http://www.google.com/search?q=how+to+backup+with+rsync+linux&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial)

HTH[/QUOTE]
 this is usefull but what he's asking!!! anyway thx :D

---

### Post by deuce868 on 2005-04-07
Why doesn't it fit? You run rsync over an ssh connection and voila...backup of the entire database over ssh and it includes backups by day, week, and month. 

If this isn't what he's asking to do then what is it?

---

### Post by Gandalf on 2005-04-07
maybe it is and i misunderstand but i see that he only wants to backup it once but maybe.. :D

---

### Post by Ric_ on 2005-04-08
If you want to backup up your databases easily! Use phpmyadmin you can apt-get install it. It will give you a web interface which allows your to export your databases and its data.

Hope that helps

---

### Post by dataw0lf on 2005-04-08
Since he's been advised to use a 'ssh utility' , I'm going to assume it is a remote backup, and he does 'want to do it more than once' (what's the point of backing up a forum once?).  rsync tunneled through ssh is probably the easiest and most concise method (and my favorite).

---

### Post by Wombley on 2005-04-08
If it's just backing up a remote (possibly tar.gz'd mysql dump or something...) file, then the command is: ```
scp http://yourserver.com:/path/to/file .
``` this will copy the file at path /path/to/file at remote server [http://yourserver.com](http://yourserver.com) to the current directory. If your username on the remote server is different to the one on the client you will have to use: ```
scp yourremoteusername@http://yourserver.com:/path/to/file .
``` To recursivly copy a whole directory across use the -R option: ```
scp -R http://yourserver.com:/path/to/directory .
``` Note the remote server will have to be running sshd for this (or any of these methods) to work. For more scp options etc try typing: ```
man scp
``` in a terminal.

Edit: By the way: ssh, scp clients etc are all installed by default on pretty much every linux distribution out there, including Ubuntu :-).

---

### Post by shakin on 2005-04-08
[QUOTE=dataw0lf]Since he's been advised to use a 'ssh utility' , I'm going to assume it is a remote backup, and he does 'want to do it more than once' (what's the point of backing up a forum once?).  rsync tunneled through ssh is probably the easiest and most concise method (and my favorite).[/QUOTE]

I whole-heartedly agree. rsync (use --rsh=ssh option to tunnel) is the best way to do a remote backup. If it fails in the middle, just run again and it will continue from where it left off. Next time you want to do a backup, just run the same command and it will only download the changes.

You can also, from your Hoary 'Places' menu, 'Connect to Server' and select SSH as the protocol. Fill in the server domain/IP and username and Gnome will put a folder on your desktop to browse the remote location.

---

