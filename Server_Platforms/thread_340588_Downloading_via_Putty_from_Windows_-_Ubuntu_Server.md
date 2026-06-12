---
title: "Downloading via Putty from Windows - Ubuntu Server"
date: 2007-01-17
forum: Server Platforms
---

### Post by ade234uk on 2007-01-17
I have logged in to server via PUTTY and backed up the work database with following command. 

mysqldump -p -u USERNAME DATABASENAME > databasebackup.sql

This is scary for me. I am used to using PHPMyAdmin. Since the database is about 80mb I need to learn how to use PUTTY. I am hoping PUTTY becomes my friend.

I can now see databasebackup.sql listed when I enter dir

A couple of questions:

1) How do I download this via PUTTY to my local machine.

2) Once downloaded how do I delete the file using PUTTY

I am using Windows as my desktop

---

### Post by MrHorus on 2007-01-17
> **ade234uk said:**
> 
1) How do I download this via PUTTY to my local machine.

You don't - PuTTY is a Windows SSH client.
Since your server is running SSH you *CAN* connect via SCP and copy it down that way however.

> 2) Once downloaded how do I delete the file using PUTTY

Same as any other file: ```
rm <filename>
```

---

### Post by paul.maddox on 2007-01-17
You can use WinSCP (freeware) to download files from your server.

[http://winscp.net/eng/download.php]("http://winscp.net/eng/download.php")

---

### Post by Brazen on 2007-01-17
> **paul.maddox said:**
> You can use WinSCP (freeware) to download files from your server.

[http://winscp.net/eng/download.php]("http://winscp.net/eng/download.php")

Yes, WinSCP will use the ssh service to download the files.

---

### Post by ade234uk on 2007-01-17
Thank you very much, your advice has been excellent. 

Just one more question.

Lets say my database is 300mb, and I export as a gzipped file how would I import this back in via PUTTY or WinSCP to mysql?

Or could I upload it as the gzipped file through WinSCP and then extract this in the folder using WinSCP?

---

### Post by jtc on 2007-01-17
Once you've uploaded the file using WinSCP it is probably easier to use Putty and extract in from the shell. If it's gzipped you want to use the command 

```
gunzip filname.gz
```

To restore your mysqlbackup using the mysql-commandline-client you use the following commands.

First, choose your database
```
mysql> use databasename;
```

Then run/load your backuped sql-file
```
mysql> source filname.sql;
```

---

### Post by ade234uk on 2007-01-17
Could I also not extract it like you suggested but then

mysql -p -u USERNAME DATABASENAME < databasebackup.sql

To import the database back.

---

### Post by jtc on 2007-01-17
> **ade234uk said:**
> Could I also not extract it like you suggested but then

mysql -p -u USERNAME DATABASENAME < databasebackup.sql

To import the database back.

Yes, that ought to work as well.

---

### Post by ade234uk on 2007-01-17
Thank you very much for your help.

I have been creating websites for the last few years. My own ones and for my boss.

About 3 months ago I was put in charge the auction site at work. Its was such a good opportunity to learn something I went for it.

The largest databases I had worked on in the past have been about 8mb please dont laugh.

The auction database has now hit 80mb, this is tiny compared to some I hear about but massive for me.

But this has now put me on another learning curve, as this is too big to import through PHPMyAdmin I am now having to learn the real way through PUTTY and others.

Whenever I get on the server I get nervous, stupid I know. I have set my own Ubuntu up at home before and I am so glad I did this, it was so vital.

Now its the real deal.

---

