---
title: "Best Backup Solution?"
date: 2011-08-01
forum: Server Platforms
---

### Post by Hack.The.Pow. on 2011-08-01
Hello all.  I am looking for the best way to backup my LAMP server.  I would like to have two separate backups.

The first backup would be all of the settings of the server.  I am extremely pleased with how my server is set up and would have to have to do all of this manually again.  So I would like to backup everything essential that is not in my home folder.  I would like to have it compressed into a archive and automatically backed up to a external drive that I have connected.  If god forbid my system ever crashed I would like to pull this archive up and have everything back up an running quickly.

The second backup as you can probably guess will be my home folder.  I would like to save everything there unarchived(so I can access a single item easier).  I would like this to be automatic as well.

What would be the best way of doing this?  I have searched a bit but none of the suggestions seemed right for me.

Thank you in advance for any suggestions.

---

### Post by masterkoppa on 2011-08-02
I guess the best approach to this is to do some scripting and cron jobs to run daily or whenever you please. I do all my scripting in python :o, but you can do it in whatever you please.

---

### Post by Wim Sturkenboom on 2011-08-02
Note in advance: I don't run an Ubuntu server

I don't see why your configuration needs an automatic backup; it hardly ever changes and you know when you change it. So you can simply copy the modified files. But OK, your call ;)

Most, if not all, of the configuration is in /etc.
```

tar -czf /mnt/yourdisk/config.`date +%F`.tar.gz /etc

```
will create a compressed archive with the name *config.YYYY-MM-DD.tar.gz* in /mnt/yourdisk (the mountpoint for your external disk).

```

cp -R /home/theuser/ /mnt/yourdisk/theuser.bck.`date +%F`

```
will copy theuser's home directory to a directory *theuser.bck.YYY-MM-DD* in /mnt/yourdisk

In both cases
[LIST]
[*]if your disk is mounted somewhere else, adjust the path */mnt/yourdisk*.
[*]you have to make sure that the disk is mounted, else it writes on your harddisk.
[/LIST]
Add the stuff that you want to run automatically to your cron jobs. I make manual backups of my Slackware server so not sure how/what. The first one should definitely be under root's cron, the second one probably under your cron; that should prevent permission issues.


**What is missing:**
[LIST]
[*]your databases; use mysqldump if this is a mysql setup
[*]possibly backup of /var/www and other directories used for websites; you have not indicated your setup with regards to that
[/LIST]

---

### Post by Lars Noodén on 2011-08-02
After running mysqldump, mentioned above, plain [rsync](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup#Backup_with_rsync) is good for saving bandwidth and time on backups.

---

### Post by aeiah on 2011-08-02
+1 for mysqldump and rsync. look into what you can do with rsync's '--link-dest' option. its used for efficient snapshotting. it'll only copy the changes - all your other files will be hard linked to prior versions.

---

### Post by Hack.The.Pow. on 2011-08-02
Thank you all again

Wim Sturkenboom I'll likely use that first command(with /var added in) to backup my settings about once a month or so.  My config doesn't change much but whenever it does I know I would be too lazy(or just forget) to backup whatever files needed to be backed up.

> **aeiah said:**
> +1 for mysqldump and rsync. look into what you can do with rsync's '--link-dest' option. its used for efficient snapshotting. it'll only copy the changes - all your other files will be hard linked to prior versions.

I just googled rsync's --link-dest option and got nothing :confused:

Could you help me out with it?  For my home dir I would like to only backup the changes to various files.  I don't need versioning though because most of the files are video files and remain unchanged.  I also am running low on external hard drive space and couldn't accommodate various versions of all of my files.

---

### Post by Hack.The.Pow. on 2011-08-07
Ok So I figured out the right commands that I need.  However for whatever reason I can't get crontab to run.  

```
jonzo@jonzo-station:~$ sudo crontab -l
[sudo] password for jonzo: 
# Edit this file to introduce tasks to be run by cron.
# 
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
# 
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').# 
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
# 
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
# 
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
# 
# For more information see the manual pages of crontab(5) and cron(8)
# 
# m h  dom mon dow   command
01 03 01 * * tar -czf /media/FreeAgent\ Drive/My\ docs/Backups/Server_Configs/config.`date +%F`.tar.gz /etc /var 
01 03 * * 6 rsync -uar /home/jonzo /media/FreeAgent\ Drive/My\ docs/Backups/Home_Folder
01 02 * * * tar -czf /media/FreeAgent\ Drive/My\ docs/Backups/Server_Configs/config.`date +%F`.tar.gz /etc /var 

```

Is there anything wrong with that file?  

I have run 

```
sudo service cron restart
```

So I know its updated. 

I have also checked that cron is running.

```
jonzo@jonzo-station:~$ sudo !!
sudo ps -eaf | grep cron
jonzo     1631  1467  0 19:34 pts/1    00:00:00 grep --color=auto cron
root     31284     1  0 18:05 ?        00:00:00 cron

```

Can you help me out?  Thanks

---

### Post by Lars Noodén on 2011-08-08
Have you made sure there is an empty line at the end of the crontab?

---

### Post by Hack.The.Pow. on 2011-08-08
Didn't know there needed to be one but I just checked and there was....

---

### Post by toshko3 on 2011-08-08
Check the /var/log/syslog for cron errors. Just search for "cron"

---

### Post by kgatan on 2011-08-08
Id recommend rsnapshots for backups, especially for web-files and config files.
I guess you could call it an extension of rsync.
Its avalible in the reposatory.

You setup rsnapshot on how many backups you want to save based on days/weeks/months but it only uses diskspace of the actual changed files.
Schedule is setup using cron.


For MySQL there are some nice dump scripts that archives the diffrent databases by dates.
Ill dig up what i use and post it later.
Or you just dump each database and let rsnapshot do the archiving.

---

### Post by kgatan on 2011-08-08
Link for automated dump script,

[http://sourceforge.net/projects/automysqlbackup/files/AutoMySQLBackup/AutoMySQLBackup%20VER%202.5/](http://sourceforge.net/projects/automysqlbackup/files/AutoMySQLBackup/AutoMySQLBackup%20VER%202.5/)

---

### Post by Hack.The.Pow. on 2011-08-08
> **kgatan said:**
> Id recommend rsnapshots for backups, especially for web-files and config files.
I guess you could call it an extension of rsync.
Its avalible in the reposatory.

You setup rsnapshot on how many backups you want to save based on days/weeks/months but it only uses diskspace of the actual changed files.
Schedule is setup using cron.


For MySQL there are some nice dump scripts that archives the diffrent databases by dates.
Ill dig up what i use and post it later.
Or you just dump each database and let rsnapshot do the archiving.

I don't actually have anything in MySQL so no need for the dump script but thanks anyway.

Also thanks for the rsnapshot suggestion but rsync works just fine when run from the command line.  Its just a matter of getting cron to run properly.

> **toshko3 said:**
> Check the /var/log/syslog for cron errors. Just search for "cron"

I did find a couple of things in /var/log/syslog related to cron however they didn't seem to apply to my errors.  Here they are anyway.

```
Aug  8 14:17:01 jonzo-station CRON[2904]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug  8 14:39:01 jonzo-station CRON[3487]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
```

The hourly entry shows up ever hour and the other one about every half hour.

I also have this error in there once.
```
Aug  8 07:49:12 jonzo-station anacron[22688]: Job `cron.daily' terminated (mailing output)
Aug  8 07:49:12 jonzo-station anacron[22688]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Aug  8 07:49:12 jonzo-station anacron[22688]: Normal exit (1 job run)
```

I also found this in syslog.1
```
Aug  7 07:58:05 jonzo-station anacron[11655]: Job `cron.weekly' terminated
Aug  7 07:58:05 jonzo-station anacron[11655]: Normal exit (2 jobs run)
```

However I have 3 jobs scheduled....

Can anybody help?

---

### Post by toshko3 on 2011-08-09
I don't know, try with no zeros in the hour - instead of:
```

01 03 01 * * tar -czf /media/FreeAgent\ Drive/My\ docs/Backups/Server_Configs/config.`date +%F`.tar.gz /etc /var 

```
try this:
```
1 3 1 * * tar -czf /media/FreeAgent\ Drive/My\ docs/Backups/Server_Configs/config.`date +%F`.tar.gz /etc /var 
```

Also, you want it in 3:01 AM, right? Not in 15:01!
Try it with a setting in 5 or 10 minutes, so you don't wait until tomorrow, and tell us.

---

### Post by Hack.The.Pow. on 2011-08-09
Ok So I added this to the crontab file.

```
* * * * * echo 'date' >> ~/out
```

But still nothing has been showing up in that file.  So I've determined that cron isn't even trying to execute the statements.

I have been editing this file by running 

```
sudo crontab -e
```

but when I make changes to it it saves it to a file /tmp/crontab.PWT0fK/crontab

Is this normal?

I checked my /etc/crontab file and this is what it contains.

```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --repo$
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --repo$
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --repo$
#

```

Is this normal?  Should I be adding commands directly to there?

**EDIT:** So apparently the echo date command is working now.  I apparently just had to create the file out first.  However the other commands are still not working.  Here is my updated crontab file.

```
1 3 1 * * /bin/tar -czf /media/FreeAgent\ Drive/My\ docs/Backups/Server_Configs/config.`date +%F`.tar.gz /etc /var
1 3 * * 6 /usr/bin/rsync -uar /home/jonzo /media/FreeAgent\ Drive/My\ docs/Backups/Home_Folder
1 2 * * * /bin/tar -czf /media/FreeAgent\ Drive/My\ docs/Backups/Server_Configs/config.`date +%F`.tar.gz /etc /var
* * * * * echo `date` >> ~/out
* * * * * /bin/tar -czf /media/FreeAgent\ Drive/My\ docs/Backups/Server_Configs/config.`date +%F`.tar.gz /etc /var

```

---

### Post by ingeva on 2011-08-09
> **Hack.The.Pow. said:**
> Ok So I added this to the crontab file.

```
* * * * * echo 'date' >> ~/out
```But still nothing has been showing up in that file.  So I've determined that cron isn't even trying to execute the statements.


I've also had trouble with cron lately.
It runs OK as a regular user, but when run as root nothing happens.

This is with 11.04 as well as my previous system, 9.10.

Can this be caused by a buggy update?
No scripts have changed....

---

### Post by Hack.The.Pow. on 2011-08-09
> **ingeva said:**
> I've also had trouble with cron lately.
It runs OK as a regular user, but when run as root nothing happens.

This is with 11.04 as well as my previous system, 9.10.

Can this be caused by a buggy update?
No scripts have changed....

My edit up there says that command actually was working but I just had to create the file first.

I'm not sure what happened with your setup though.  I am running 10.10 btw.

---

### Post by Hack.The.Pow. on 2011-08-09
So I just got it working.  For whatever reason cron didn't like those commands directly in the crontab file.  So I just made two scripts to do what I wanted to do and that ended up working.  

No idea why that worked but whatever.  Maybe the backslash white space escaping broke the commands?  O well.

I will mark as Solved for now but if anybody can figure it out that would be great.  Thanks everybody!

---

### Post by toshko3 on 2011-08-11
I'm glad you did it! I don't know why it doesn't work, but I do it only with scripts already. It is more convenient.
May be there is something related to the fact that it runs in the background. But I don't know, it should throw some errors in the syslog.
:confused:

---

