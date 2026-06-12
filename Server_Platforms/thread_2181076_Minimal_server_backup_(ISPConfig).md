---
title: "Minimal server backup (ISPConfig)"
date: 2013-10-16
forum: Server Platforms
---

### Post by Adonosonix on 2013-10-16
Dear All,

I am looking for a way to fully backup my web server while transferring the smallest possible amount of data.
So, let's say that I have two identical servers installed using the guide: [I]The Perfect Server - Ubuntu 12.04 LTS (Apache2, BIND, Dovecot, ISPConfig 3).
[/I]
By following the tutorial, I end up with a fresh, empty installation of ISPConfig 3, and a working server (mails, DNS, Apache, php, MySQL, etc&#8230;).
Now, let's say I configure one of the server with websites, mailboxes, databases, I add clients in ISPConfig, etc...

Which files/folders should I copy from the used server to the fresh one in order to be able to substitute the old one, and have everything (mailboxes, websites, forums, DNS, etc&#8230;) working perfectly ?

I was thinking of dumping the whole /var since it seems to contain most of the stuff. Is there something else I should copy along with it ?

Thanks for your help.

PS: Backup and restauration will be done through ssh. I use asymmetric DLS, so download (backup) is not an issue. However, restoration (upload) is quite slow (1 Mb/s maximum)

---

### Post by TheFu on 2013-10-16
/var has lots of stuff you just don't need. You'll want to be much more selective.

See my signature for backup options - there are many choices. The more you know and understand about Linux, the more efficient you can be with your backups.  It also depends on whether YOU are running the entire OS or just your data on the box. Very different backup areas would be involved.

A few years ago, I switched to a minimal backup method: [http://blog.jdpfu.com/2011/10/08/optimized-backups-for-physical-and-virtual-machines](http://blog.jdpfu.com/2011/10/08/optimized-backups-for-physical-and-virtual-machines). I've had to restore twice in that time. It definitely works.  

The backup size depends on the purpose of the server. I generally keep 60 days of backups for servers now.  Here's an example for an email gateway server:
```
$ sudo rdiff-backup --list-increment-sizes spamcache
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Wed Oct 16 01:10:06 2013         11.9 MB           11.9 MB   (current mirror)
Tue Oct 15 01:10:08 2013       520 bytes           11.9 MB
Mon Oct 14 01:10:07 2013       520 bytes           11.9 MB
Sun Oct 13 01:10:06 2013       520 bytes           11.9 MB
Sat Oct 12 01:10:07 2013       779 bytes           11.9 MB
Fri Oct 11 01:10:08 2013       644 bytes           11.9 MB
Thu Oct 10 01:10:08 2013       520 bytes           11.9 MB
Wed Oct  9 01:10:06 2013       520 bytes           11.9 MB
Tue Oct  8 01:10:08 2013       833 bytes           11.9 MB
.
.
.
```
As you can see, hardly any data changes on that machine daily. The real email server gets much more change data daily.  A small blog server with about 2K articles .... 
```
$ sudo rdiff-backup --list-increment-sizes typo
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Wed Oct 16 02:50:15 2013          906 MB            906 MB   (current mirror)
Tue Oct 15 02:50:15 2013         2.32 MB            908 MB
Mon Oct 14 02:50:14 2013         2.35 MB            911 MB
Sun Oct 13 02:50:14 2013         22.4 MB            933 MB
Sat Oct 12 02:50:15 2013         2.46 MB            936 MB
Fri Oct 11 02:50:15 2013         2.53 MB            938 MB
Thu Oct 10 02:50:14 2013         2.67 MB            941 MB
Wed Oct  9 02:50:15 2013         2.60 MB            944 MB
Tue Oct  8 02:50:15 2013         2.52 MB            946 MB
Mon Oct  7 02:50:15 2013         2.19 MB            948 MB
Sun Oct  6 02:50:14 2013         21.6 MB            970 MB
.
.
.

```
You can see every 7 days, something causes a larger change. I patch servers every week. That explains it.
BTW, that blog server has about 6G of storage so it can work, but by only storing settings and data specific to the blog and a reverse proxy, I've minimized the amount of data needed to restore.
```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1       4.5G  2.8G  1.5G  66% /
/dev/vda5       1.5G  804M  618M  57% /var/www

```
I like to think this is pretty slick. I don't think I'd recommend the same method to someone new to Linux, but reading the link above might provide some ideas on ways to be more efficient.

---

### Post by houstonbofh on 2013-10-16
Have a look at rsync and the GUI tools that use it.  It can copy only the changes and save a lot of bandwidth for static content.  And if you log it you can see if you are backing up things you do not need, or not backing up things you do need.

---

### Post by Adonosonix on 2013-10-16
Thank you both for your replies. I am not that new to linux. My laptop used to be a Kubuntu from 2004 to 2009. Then I switched to MAC. When I said "[COLOR=#000000]Backup and restauration will be done through ssh[/COLOR]", I meant rsync. And though I agree with you, houstonbofh, that it will save me a lot of brandwidth when backing up, it will still be a real pain when restoring on a new server, since my internet connection is asymmetric DLS (they all are in my country – optical fiber is only available in the main cities) and all the data will need to be copied.

However, I am new to webservers, and I don't know where all the config files are stored, which are the meaningful ones, which can be ignored. That's why I used the example, which is the actual setup. I have an automated script that can reinstall the full ISPConfig setup (as described in the tutorial + a fair amount of security additions) in a few minutes. This is the starting point. Everything works, except that there are no websites, no mailboxes, MySQL only contains a few databases.

So, I won't need to restore fail2ban's config, or php.ini, etc… since they are already setup. But I will need to restore all the mailboxes with their content, all the website data, all the clients in ISPConfig, etc...

To be more specific :

**Is it enough to :**

```
- Restore ISPConfig's database
- Restore /var/lib/mysql/ (to get back all the databases and tables and settings)
- /var/www/ for the websites
- /var/www//var/vmail to get back all the mailboxes and their content
```

Or are there other files that MYSQL and postfix/dovecot, etc... need ? That's where I lack the knowledge.

Thank you for the link to the blog article. I have read it and followed it to the rdiff-backup. Desktop computers are easier to backup : just take care of the /home, keep track of all the apt-get install issued and you're good. Upon restoration, re-install the system. Execute all the apt-gets. Re-create the user account and put back the home folder.

I have tracked all the apt-get issued for the server, kept track of all the changes made on the config files during installation with diff. Now, I only need to know which folders/files to backup.


Currently, I only have one (wordpress) website, with one test article. One client in ISPConfig, with the website, one mailbox with around 10 mails. Here is the space used by the main directories :

```
802M	./usr
674M	./var
280K	./run
204M	./lib
42M	./tmp
28M	./boot
21M	./sbin
16K	./lost+found
12K	./quota.user
12K	./quota.group
8.8M	./bin
8.3M	./etc
8.0K	./media
4.0K	./srv
4.0K	./selinux
4.0K	./opt
4.0K	./mnt
4.0K	./lib64
4.0K	./home
4.0K	./dev
3.6M	./root



```






Thank you for reading me.

---

### Post by TheFu on 2013-10-16
It isn't safe to copy DB files while they are in use. Either shutdown the RDMBS or dump it and backup the exported files.
If you've ever installed non-repo software, back it up.
If you've ever installed .DEB packages, back it up.

While that blog article was about a desktop, I've been backing up servers using a similar technique for years.  YOU really need to know the locations of data and settings for your system to be certain the backups have everything necessary.

The only way that I know to be certain is to do a backup, then try to do a bare-metal restore. Until that is attempted, it is impossible to be certain.

---

### Post by Adonosonix on 2013-10-16
Thank you for your reply.

> **TheFu said:**
> It isn't safe to copy DB files while they are in use. Either shutdown the RDMBS or dump it and backup the exported 
files.


Thanks for the advice. If I backup de databases, I still don't have all the mysql setup (the one I did with phpmyadmin, which includes amongst others the users and their privileges).

> **TheFu said:**
> 
If you've ever installed non-repo software, back it up.
If you've ever installed .DEB packages, back it up.


Done.

> **TheFu said:**
> 
While that blog article was about a desktop, I've been backing up servers using a similar technique for years.  YOU really need to know the locations of data and settings for your system to be certain the backups have everything necessary.


That's the spirit of this post. Hoping that someone with the experience can tell me, given the setup (the popular perfect server 12.04 LTS), which files/directories I am missing. That would save me the hassle of going through the doc of each service (mysql, apache, dovecot, postfix, squirrel, etc…) identify those files, and do 20 to 50  backup /restore… until I get it right.

> **TheFu said:**
>  
The only way that I know to be certain is to do a backup, then try to do a bare-metal restore. Until that is attempted, it is impossible to be certain.

I agree. That's the plan. That's why I have this server with one website, one mailbox, one db, a few mails and blog posts. However, in its current state, the backup plan is incomplete, and the restore plan bound to fail.

As a last resort, I could do:

1. Fresh install.
2. Reboot a few time and identify the modified files (server isn't connected to internet). Those do not need to be saved.
3. Connect the server, create ISPConfig clients, websites, mailboxes
4. Run the server a few hours, and identify the modified files.
5. Remove the files in 2. from the batch of files in 4.
6. For each modified file, add the *directory containing it* to the backup list.
7. Take care of the special cases, like backing up the DBs separately. I still haven't figured out how to backup the mails (short of shutting down postfix+dovecot and get the raw files).

---

### Post by TheFu on 2013-10-16
Well, if you want the really easy way - not the most efficient - drop to single -user mode and backup everything with something like **ddrescue** or **clonezilla**. Single-user mode will shutdown all services so it is safe to backup DB files.

The "perfect server" is a great howto ... have you asked for a "perfect backup" over on that website inside their forums?

---

### Post by houstonbofh on 2013-10-16
If you run rsync on / you will get everything. :)  I do not recommend this. :)  Also, it might cause problems with uuids in fstab...

Also you have databases.  rsync will copy them if they are off.  It will not if they are on.  However, there are wonderfull tools to sync databases.  MySQL in master slave or manual replication with phpmyadmin.  In this case you would have a warm spare...  Here are some options.

[http://superuser.com/questions/90301/sync-two-mysql-databases](http://superuser.com/questions/90301/sync-two-mysql-databases)

---

### Post by TheFu on 2013-10-17
> **Adonosonix said:**
> I have tracked all the apt-get issued for the server, kept track of all the changes made on the config files during installation with diff. Now, I only need to know which folders/files to backup.


I don't track the installed packages.  The system does that already.  In the article, the dpkg commands to save and restore the package list are included.

I'm here to "teach a man to fish ,.,,"

---

### Post by Adonosonix on 2013-10-17
Thank you for your advice. About the installed packages, I meant that I have a nice folder which contains:

1. A re-install script containing all the commands I used to setup the server (that's where the installed packages are "listed").
2. A patch directory containing all the patches that must be applied to various files I did modify during the setup
3. A soft directory containing other stuffs, such as the non-repo packages I installed.

But that's actually off topic. Maybe I should have asked more precise questions. Here is one:

Let's say I have two identical, fresh setup of MYSQL. I use one of the two, create users, DBs, tables, etc.
Now, I want to replicate this configuration on the second setup. In addition to dumping the databases, what configuration / data file should I copy in order to achieve my goal ?

Thank you for the link houstonbofh. Unfortunately, I own only one server. Otherwise, things would have been so much simple. Replication is ruled out. Also, I would like to do more than just backup my database tables.

---

### Post by Adonosonix on 2013-10-17
> **TheFu said:**
> Well, if you want the really easy way - not the most efficient - drop to single -user mode and backup everything with something like **ddrescue** or **clonezilla**. Single-user mode will shutdown all services so it is safe to backup DB files.


Thank you for your suggestion. As I said, I am not interested in backing up everything. Only the data that can't be re-created from scratch. As an example, I do not need to backup apache configuration : it can be recreated. However, I need to backup my mysql databases.


> **TheFu said:**
> 
The "perfect server" is a great howto ... have you asked for a "perfect backup" over on that website inside their forums?

 Thank you for this suggestion.
Actually, I did. But as you can see, it is not an easy question. Otherwise, I would already be happily backing up.
However, as you suggest, maybe I should be asking on specialized forums of individual services (postfix, mysql, etc&#8230;). But I tried here first, there are many more users here, and I can't be the first to have a single server with a single harddrive, that needs backup for a quick re-install in case of a HDD crash, am I?

---

### Post by TheFu on 2013-10-17
I think the answer to your DB question is: "it depends."   I can only suggest that you look on the MySQL support forums for the correct answer for your situation. There are many, many, many different configurations possible and I don't have the knowledge to answer every possible config backup.  However ... dump and restore works 90% of the time, if you want to gamble.  The location of the DB files can be almost anywhere - depends on your setup.

Settings are almost always in /etc/  but can be anywhere.
DBs are almost always in /var/lib/ but can be anywhere.

Here's a DB dump script:
```
#!/bin/bash
DB_NAME=redmine_default
BACKDIR=/root/backup/
/usr/bin/mysqldump -u root \
    -p`cat ~root/$DB_NAME.passwd.root` $DB_NAME | \
    gzip > $BACKDIR/$DB_NAME_`date +%Y%m%d`.gz
find  $BACKDIR -type f -name $DB_NAME\* -atime 60 -exec rm {} \;
```
Then just be certain that the dump BACKDIR gets included in normal backups. Hope that helps, but definitely verify this works for your situation.

By using non-repo installations, you've decided to manually maintain the box. The same applies by using non-default settings. Sometimes there isn't any choice, but there are risks, especially by installing non-repo software since that will likely break dependencies at some point and get your APT system into "APT Hell."  I've had to do this on a few systems here too. Sometimes it just can't be avoided.  

Recently was installing a Redmine server for a client.  I had an older Redmine serve for a different client that couldn't be easily upgraded because I'd used the "latest packages" directly from the redmine website.  Ubuntu has a Redmine package, slightly old, but it is far from install-n-use. Still, that package is much easier on the dependency management than manually maintaining 10 other package versions too. Trade-offs.

Plus, I avoid installing MySQL anymore. MariaDB is a drop-in replacement on the server-side and avoids Oracle (who IO don't trust). All the same client tools/libraries still work.

DB replication isn't simple - ever. There are always complexities. While I've never used replication with mysql, I have with 5+ other RDBMS systems - sync and async replication, local, remote, around the work, follow the sun stuff.  Also did it using storage-only solutions (EMC-BCVs). Log-based replication is the easiest, but also the most likely to get behind and cause corruption, IMHO. If the DB is low transaction rates, then that becomes less of an issue.

I've been thinking about writing a nominal-server backup how-to (including script) ... because there isn't 1-right-way for every situation and the critical nature of the results, I've avoided it.  Hummmmm.  I need to think about that a little.  It isn't hard, just some details.

Or just use **ddrescue** and mirror the HDD 100% like we mostly do on MS-Windows. There are complexities in doing this on UNIX systems - since UUIDs would match too - OTOH, swapping in a HDD as a 100% replacement for the failed HDD is about the fastest way to be up again.

---

### Post by Adonosonix on 2013-10-17
Thank you TheFu for your very detailed answer. I will test that, investigate the options, maybe ask on specialized forum and report back.

---

### Post by c1audiu on 2013-12-22
> **Adonosonix said:**
> Thank you for your suggestion. As I said, I am not interested in backing up everything. Only the data that can't be re-created from scratch. As an example, I do not need to backup apache configuration : it can be recreated. However, I need to backup my mysql databases.
Hello,
I'm using one CentOS 6.4 OpenVZ image with nginx, mysql...and ISPConfig. Have you managed to do the backup? I want to change my CentOS to Ubuntu 12.04LTS or 13.10, but I have files modified everywhere on my system (/etc/postfix/main.cf - fail2ban files, CSF files).
What was your solution?
Thanks in advance.

---

### Post by Adonosonix on 2013-12-22
> **c1audiu said:**
> Hello,
I'm using one CentOS 6.4 OpenVZ image with nginx, mysql...and ISPConfig. Have you managed to do the backup? I want to change my CentOS to Ubuntu 12.04LTS or 13.10, but I have files modified everywhere on my system (/etc/postfix/main.cf - fail2ban files, CSF files).
What was your solution?
Thanks in advance.

Well, no. Sorry to disappoint.
That said, I found out that stopping all services at 3 AM, doing a backup of /etc and /var on a /save partition, then restarting all services was enough. The issue is : you can't get e-mails during that window of time.

The main reason for stopping the services are postfix and dovecot. While there is an utility for safely backing up dovecot while running, it only does mirroring and there is no way to do a save/restore operation to a disk destination. You need a second server. Which I do not own. So I'm screwed.

I am still looking for the answer to the original question, and I will mark it solved once it is. 
So, if anyone has a solution to this issue, you are welcome to share. I am still in need of a solution to quickly save / restore a running server (mail, mysql databases, websites, etc…) over the internet (requires small-sized backup).

---

### Post by houstonbofh on 2014-01-11
Do a job for each service, and only stop the service being backed up.  That will at least keep your mail down time to the lowest amount.  And you will not loose mail (well, perhaps some spam) as the sending mail server will try again generally in three hours.

---

