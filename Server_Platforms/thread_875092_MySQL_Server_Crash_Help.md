---
title: "MySQL Server Crash Help"
date: 2008-07-30
forum: Server Platforms
---

### Post by Crof on 2008-07-30
I'm having a little trouble with my MySQL server.  

I'm running Ubuntu server 7.10 and am fairly new to setting up and configuring things without a GUI.

I had the MySQL server configured and my database was getting started.  Yesterday the power went off in the middle of the night. When I turned my computer back on everything was fine except the MySQL server no longer starts.

**The error I get is:**

* Starting MySQL database server mysqld         [[COLOR="Red"]fail[/COLOR]]

If there is some way to repair the MySQL I would like to just so I get experience trouble shooting something like this, but I assume it would be far easier to just reinstall it.

I have tried restarting both the computer and just the MySQL server: doesn't help.  I can't get any more descriptive errors either.

**The real problem:**
I simply can not find the command to reinstall the MySQL server!  Can anyone point me in the right direction?  

Thanks in advance! :)

---

### Post by ASK47 on 2008-07-30
Definitely easier to reinstall it. That is, if your data is safe. 

[FONT="Fixedsys"]apt-get install mysql-server mysql-client libmysqlclient15-dev[/FONT]

or

[FONT="Fixedsys"]aptitude install mysql-server mysql-client libmysqlclient15-dev[/FONT]

I'm curious as to how to repair such a problem, myself.

---

### Post by tinny on 2008-07-30
If you can do a reinstall (with out losing valuable data) then do it :)

Remove (completely)

```

sudo apt-get remove --purge mysql-server

```

reinstall

```

sudo apt-get clean
sudo apt-get update
sudo apt-get install mysql-server

```

Or if you want to fix this problem post back the bottom few lines of your MySQL log.

The path to your MySQL error log is defined in the /etc/mysql/my.cnf file.

look for the "err-log" property. Probably "/var/log/mysqld.log"

---

### Post by Crof on 2008-07-31
Thanks for the advice.  Oddly, neither suggestion solved the issue.  Running **sudo apt-get remove --purge mysql-server** seemed to work, but then running **/etc/init.d/mysql restart** would still claim to successfully stop and try to start the mysql server.  

In any case, reinstalling MySQL server and client has not seemed to solve the issue. I would love to copy/paste the log file but this is not the server and I'm unaware of an easy way to transfer the log file (haven't quite mastered the skills of mounting/unmounting usb drives without putting all the data on them at risk :wink: )

But here what seems to be important from it after attempting both installs and restarting the whole system:

[INDENT]Jul 31 00:26:14 ubuntu mysqld: [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
Jul 31 00:26:14 ubuntu mysqld: [ERROR] DO you already have another mysqld server running on port: 3306 ?
...
Jul 31 00:26:27 ubuntu /ect/init.d/mysql[4224]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Jul 31 00:26:27 ubuntu /ect/init.d/mysql[4224]: check that mysqld is running and and that the socket: '/var/run/mysqld/mysqld.sock' exists![/INDENT]

Turns out **/var/run/mysqld/mysqld.sock** doesn't exist.  In fact nothing is in that directory at all.  Some research showed that the mysqld.sock file is created by mysql when it starts.  The problem seems to be that the port 3306 is in use when the server tries to start.

I'm not sure how to check what would be holding the port open that wasn't before.  Is there a way to check what ports are being used by what program or even a way to force them to become open again?

---

### Post by Crof on 2008-07-31
My server is now working properly! :)

The problem was that when my server restarted itself, it got a new IP Address from my modem.  There were static addresses in my /etc/mysql/my.cnf file that had my old IP address in there.  I had just configured the MySQL server for remote logins a few weeks ago.  Apparently it hadn't changed IP addresses in that time till just now.

In any case, I just set up the system to have a static IP address and set it to the old address and it instantly fixed my issue!

Also despite doing those purges and reinstalls, all the settings and tables remained unchanged.  Very odd....not that I'm complaining :cool:

Thank you both again.

And for the reference of anyone who may stumble upon this problem, a nice set of instructions for setting your ubuntu machine to have a static address can be found [here]("http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/")

---

### Post by cariboo on 2008-07-31
Just a couple of things. If you look at the first line of your posted error message, it tells you what the problem is. When trying to troubleshoot problems pay attention to what the logs says. It took me a while to see what I read in the logs, but sure is a lot easier now.

The second point is you can use sftp to transfer files from your server to your desktop in ubuntu simply open nautilus and in the address bar type:

```
sftp://user@server
```

Where user is your username and server is your server name or ip address. In windows you can use winscp, I've never used it but windependence recommends it highly.

Jim

---

### Post by Ed1000 on 2008-12-31
Just a quick reply though your problem seems fixed:
I had similar problems and whatever I did to re-install MySQL just turned out a failure, it would not reinstall, so i decided to repair the mysql tables (as was your initial question)
cd-to your *.MYA directory in your MySQL dirctories

cd /var/lib/mysql/mysql
/etc/init.d/mysql-backend stop
/etc/init.d/mysql stop
myisamchk *.MYI

that should give you a listing telling you what tables need repairing. Then type:

myisamchk -r xxx.MYI

in which 'xxx' is the name of the table to be repaired.

I found your mail very interesting as I suffered many server crashes recently (3-4 times a day) and slowly I got th eimpression that that happened after I set up the server with a static address replacing the dynamic address. 
repairing my tables did not prevent the server crashes
I changed it back to dynamic ip and no problems since (1 day)
in my my.cf file however there was no old or new ip address, just 127.0.0.1

---

