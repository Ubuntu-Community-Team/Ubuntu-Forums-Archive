---
title: "Back up Tools and a special SAMBA SHARE"
date: 2010-08-09
forum: Server Platforms
---

### Post by ivikas on 2010-08-09
Hello all,

         I am a php devloper and  recently my company purchased an IBM X3400 M2 Server and i was told to set up the server.I installed the Ubuntu 10.04 LTS Server i386  version.Everything went up smoothly and i have some queries to be asked.

1.)Our scenario is like this,--> we have an a production LAMP Server and we need the to backup all the contents of www folder and all Mysql files.I plan to do this with a shell script and use the rsync for syncing and  backup.

                    Again i have a mysql backup shell script that i want to activate on system shut down Like when i shut down my server,the backup script should run taking all the backups,  just before the Shutdown.The script should run take the backups, one, on the server itself and other on a remote machine sync with rsync and system should then go for Final shut down.How can we achieve this.I know of cron jobs but i prefer the above way.Suggestion requested here.

2.)To Set up a Special Samba share.

I need to set up a samba share that will allow only files to be copied and not be deleted.For eg i will create a folder "WEBSITE-BACKUPS"(will contain the list of all finished website works plus mysql dump)

The user on the network will have only permission to paste into this folder.Like a user just paste his work say 'abcwebsite',he will have only this privilege and no DELETE privilege or right.Can this be done?


3.)I have a LAN, in this the IBM Machine is acting as Production LAMP server with around 20 machines connecting and working with files on this server.All other machines are Windows.Can i get a log based on the ip like who has accessed with files at what times or last modification time from an IP address.
                        I usually get complaints from my fellow developers that somebody has deleted or modified their work which is in this IBM Server.So is there any way to monitor this.I also know about subversion,the versioning system but most people here are uncomfortable with  check in / check out commands.Please suggest a way for this.

Thanks for your time for reading all this.It will be greatly appreciated if you could suggest a solution or even a web link in the right direction.

Thanks In advance

Take Care.

---

### Post by rubylaser on 2010-08-09
To be honest with you, you're going to want to backup your code and MySQL databases more frequently than just at shutdown.  This is a Linux server, and really you should hardly ever need or want to shut it down.

So, although you seem against cron, that really is the best way to do it.  I keep daily incremental backups of my websites and mysqldumps, and sync them offsite with rsync.  If you wait for them to run only on shutdown, you'll have downtime or a maintenance window, and it might be too late (corrupt files / hardware failure /etc).

I've never tried to do a special SAMBA share like what you're mentioning.  Code development teams and individual coders should work out of version control like GIT or Subversion.  You never want to be "working" on a production web application.  You should have a development area that you branch and run tests against before things get committed to the trunk and roll into production.

This would fix your problem of point #3, by allowing people to correctly handle the codebase.

---

### Post by HermanAB on 2010-08-09
Hmm, if you shut the server down more than once a year to upgrade Mandriva, then you are doing something wrong...

Coders should use Subversion or CVS.

Your backup script can be plonked into /etc/cron.daily to run 1 minute after 4am each morning.  You need to export the MySQL database with mysqldump and rsync the exported file to backup storage.

---

### Post by CharlesA on 2010-08-09
+1 for rsync.

+2 for cvs or Subversion.

Sticking the backup script in /etc/cron.daily would work well. It doesn't make sense to be shutting down server all the time just to do a backup.

---

