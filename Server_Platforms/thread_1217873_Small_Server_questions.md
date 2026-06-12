---
title: "Small Server questions"
date: 2009-07-20
forum: Server Platforms
---

### Post by Stoneface on 2009-07-20
I am doing some work on a small server. I just checked out the Server log files @/var/log/apache2/. I saw that there are like 50 access log files!? How many does Ubuntu Apache make before one is removed? Or do I need to do that or use some kind of program for?
Second question, if I would like to backup two databases from the command line can I use:

```

mysqldump -u root - p database_name > database_name_backup.sql 

```

I prefer to enter the password later so it is not shown. But I wonder if this command makes mysqldump think the password is database_name ..?

Third question, is there no way to send the mysql dumps automatically by e-mail? I know Wordpress uses a plugin like that, but I wonder if this can be achieved with a Bash/Server script/Cron Job. Mind you I no nothing about Bash scripts nor Cron jobs.. yet. But I am learning as fast as I can. :-)

The reasons for all these questions is that this server has not been maintained for quite a while and needs to be cleaned up and updated+upgraded asap.

Thanks for all your help!

---

### Post by windependence on 2009-07-20
logrotate should take care of the log files. They're all text and they aren't too big usually.

For the second question here is a very good solution for you and it automates the process:

[http://articles.techrepublic.com.com/5100-10878_11-6051389.html](http://articles.techrepublic.com.com/5100-10878_11-6051389.html)

You are correct, if you execute the command like that it will not work. You can do it the way you want though:

[INDENT]> --password[=password], -p[password]


      The password to use when connecting to the server. If you use   the short option form (-p), you cannot have a space between the option             and the password. If you omit the password value following the             --password or -p option on the command line, you are prompted for             one.
            Specifying a password on the command line should be considered             insecure. See Section 6.6, "Keeping Your Password Secure".
[/INDENT]

mysqldump -u root -p database_name > database_name_backup.sql
On the third question you certainly could script it to e-mail you, but a better way would be to have it SCP (secure copy) it to whatever machine you want. This can be done remotely pretty easily even to a Windoze box.

-Tim

---

### Post by Stoneface on 2009-07-20
For an automatic dump I saw this Bash script when I followed your link Windependance:

```

#!/bin/sh
mysqldump -u root --all-databases >/var/lib/sqldump/mysql.dump

```
the bash file should be mode 0600 to make it secure and no password is needed apparently. 

This script is useful to make a copy and store it locally. What if I would like it to be sent to and external e-mail address or other FTP of HTTP server?

[S]I also need to add the script to cron jobs to run this automatically, right? How do I do that?[/S]

I am reading: [http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/](http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/)

---

### Post by windependence on 2009-07-20
Take a look at SCP. No need to run an insecure FTP server on your box to transfer the files. SCP uses the SSH protocol to move them. You can use it in your scripts also. 

I am working at a client right now so I can't do the example for you, but I will post it when I get done here. I can also help you with cron.

-Tim

---

### Post by Stoneface on 2009-07-25
If you could help met the script and cron job that would be great. I am familiar with SCP as I work with Open SSH. The server is question has a functional openssh installed.
I read this sample to jog my memory on ssh copying [here]("http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s03.html"):

[I]How do I copy files/folders from a remote Ubuntu machine into a local machine (scp)?
	
Assuming that the remote Ubuntu machine has installed SSH Server service. Read How do I install an SSH Server?. Remote Ubuntu machine IP address:192.168.0.1, Remote files/folders location: /home/username/remotefile.txt Local machine save location: . (current directory)

   1.

      scp -r [email]username@192.168.0.1:/home/username/remotefile.txt[/email] .[/I]

So ssh and scp are brothers. Knew about it. Just did most of my copying using SFTP with Filezilla and ssh for command line stuff..

---

