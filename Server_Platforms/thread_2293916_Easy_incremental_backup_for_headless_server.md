---
title: "Easy incremental backup for headless server"
date: 2015-09-08
forum: Server Platforms
---

### Post by nitez on 2015-09-08
Hello community!

I have Ubuntu Desktop (12.02) running as a server (GUI disabled at boot)*. Now, that's my server box ...

Whlst I do feel a lot more familiar with command prompt than ever before, I still like some good gui, and when it comes to backing up, I like "back in time" (BIT). However, after setting up the backup scheme in BIT (only selecting specific folders, excluding some media types, etc.), I realised that no backup was being made unless I was actually logged into GUI. Also, I noted many errors related to permissions.

So, in brief, what can I do to setup my backup scheme (incremental) in BIT (other suggestions also welcome!) whilst making sure that (1) it will actually backup as setup (me being logged in or not) and (2) limiting/eliminating errors. I know I could setup some root cron jobs (say with duplicity?), but the structure I want to backup will make it too many lines. Also, if cron is the best option, then where do I define the backups to be kepts (w, m, y) deleted, etc?

Thanks!

* If you ask, I could now install the server version, but as mentioned in earlier posts, I was not ready for a no-gui environment at the time and haven't yet found the time for a new install (again, I know by now that I could have installed the server version, then the gui, etc.). I know the installation will be fast, but as I've made some tweaks over time, I am concerned that the server won't meet my needs as needed.

---

### Post by TheFu on 2015-09-08
back-in-time is fine for 1 person and only their files.  You can run it as root, but there are nuances to doing that. A good understanding of process, file and directory permissions is required. Backups only work on the LAN too, which is an issue.

Forget the GUI. There are many reasons, but mainly
a) getting a backup without using root is next to impossible.
b) running GUI tools as root is a bad, bad, bad, bad, bad, bad idea. There are many unintended side effects that you DO NOT WANT.
c) Backups also need to be automatic - that means run through cron. Cron doesn't do "gui".
d) when you move to a true server eventually, no GUI,  why not learn how to do the system backups now?

So - I've convinced you not to use a GUI and that you must run backups as root (or a root equiv account).  You want them encrypted, at least over the network - that means ssh. You also want to avoid any proprietary file formats. The backups shouldn't mandate using only 1 tool to access them.  So - a tool that works with ssh, runs from cron easily, does encryption is normally **duplicity**.

Duplicity hasn't worked well for me. The backups are old-school, like from 1970, where you need the old backup schedule that has been around for 40+ yrs: [http://blog.jdpfu.com/2009/03/25/backup-schedules-and-retention](http://blog.jdpfu.com/2009/03/25/backup-schedules-and-retention)

I'm unhappy with the old-school backup schedule, preferring to have the most recent backup appear as a mirror, so restoring 1 file from last night is trivial - just a copy. Nice and easy.  Backups must be incremental and versioned. A few times, I needed to go back 2 or 3 weeks to restore a system.  With an old-school backup, the "full" for that week needs to be restored, then each incremental applied to the day that the restore is desired.  If weekly "fulls" happen on Sunday, then to restore a file from Friday would require Sun, M, T, W, T, F backups restored. Eeew.

There is another answer.  I've been calling is the reverse-differential backup.  The tool is **rdiff-backup**.  If you search these forums, you'll find lots of people who have converted.  I've been using it for about 7 yrs now.  [https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/) is the best guide for using rdiff-backup that I've found. Makes things clear and simple.

BTW - when you try out new backup tools, do so on the /etc/ directory.  It is tiny, with root-owed files, symlinks, and other special files so you'll test those quick.  Adding, modifying a text file in there is easy and quick to test.  It is fairly harmless to test restores to other storage too.

I don't use rdiff-backup to backup media files or huge files - like single-file virtual machines. I back those up like they are real machines. Each system usually takes 2-3 minutes a day for backups.  For large media files, a simple **rsync -avz** is what I use. Don't do this unless needed - about weekly, but it is ad hoc.

Settings are stored in the same places for a server as they are for a desktop.  A backup that is never tested isn't really a backup. It is "hope" and hope is NOT a plan.

Of course, your requirements aren't mine and only you can decide the best answer.

---

### Post by nitez on 2015-09-10
Many thanks TheFu for this advise! I've already started testing rdiff [COLOR="#FF0000"][corrigendum: rdiff-**backup**][/COLOR] and seems to work - I'll certainly take your advise about testing the backup! Is the only way to do so to actually restore the backup (or part of a backup with cp if I understand well from some reading) or is it possible to "command-test" a backup (I think I'm making up vocab here)? As I have a rather complex list of wishes on what to backup or not (to save on space), I've started the test using external scripts (backup.include, backup.exclude) which seem to work fine.

Is there an easy way to test the estimated space a backup will occupy (to check that your drive is large enough) - and to automate a warning message/mail when drive capacity is reached?

As indicated earlier, I want to automate this process (i.e. create/delete old backups). In that case, I presume 2 cron lines would be sufficient (rdiff-backup, and rdiff-backup --remove) or should I do this differently?

Talking of automation, is there a way to automate launch of another (second) backup when an external drive is connected?  

> **TheFu said:**
> Settings are stored in the same places for a server as they are for a desktop.
What do you mean with Settings, backup settings? Where are those?

---

### Post by TheFu on 2015-09-10
Settings for any program, regardless of whether it is on the "server" install or a "desktop" install. Those are stored in the same place.  apache settings are in /etc/, personal settings for userids are in the HOME of that user id.  MariaDB settings are in /etc/, ...  rdiff-backup doesn't have any special "settings" files. You control those, like we do with almost every CLI program.

Let's be very clear here.  rdiff is NOT rdiff-backup. They are related, but VERY different. Please always be clear to never confuse someone lurking here later.

The rest of your questions are answered with experience as you learn more about Unix shells and normal commands. Get a generic Linux reference book, carefully read the beginning chapters )200-300 pgs), then skim the rest of it by reading the section, sub, sub-sub-section headers for the rest of the book so you get an idea of what is possible and some program names to accomplish those things.  Web search for "command line linux" should find a free PDF book that is good. You can buy the same book at any bookstore. The PDF versions have been translated into many languages.

IMHO, connecting an external drive shouldn't do anything. It is a security consideration. It definitely SHOULD NOT MOUNT!@!!!@#!@#!@!#!@#!@#!@#  The power to mount is the power to overlay ... which is a huge security issue.

The manpages for every program on the system have detailed explanations for what is possible through a tool. rdiff-backup has some options that are handy. It is worth a read. 

Generally cp shouldn't be used to restore backups, unless it is just 1 file you need. When restoring a directory tree, either use the backup tool or rsync.

Watching drive capacity is something your monitoring tool should be doing - not something a backup tool does. munin, logwatch - start there.

---

### Post by nitez on 2015-09-11
I've added a corrigendum above to avoid future readers confusion.
Thanks for the tips on further readings and programs.

---

### Post by jason_gibson2 on 2015-09-11
I just do it with a script for my data folders to my server. Could be easily modified for locally mounted drives or whatever. I don't believe in entire system backups though. Maybe /etc and /home/$USER but thats about it. Those can easily be versioned as well in a similar fashion.

```
data_backup() { # versioned backups $1 = name of backed up folder | $2 = /path/to/folder being backed up
    if ping -c 1 "$SERVER" ; then
        if [[ -d "$2" ]] ; then
            if ssh -t "$SERVER" "ls $DATABACKUP/${1}/current" >/dev/null ; then
                rsync -az --link-dest="$DATABACKUP"/"$1"/current "$2" "$USER"@"$SERVER":"$DATABACKUP"/"$1"/"$1"."$NOW"
                ssh "$USER"@"$SERVER" "rm -f ${DATABACKUP}/${1}/current && ln -s ${DATABACKUP}/${1}/${1}.${NOW} ${DATABACKUP}/${1}/current"
            else
                rsync -az "$2" "$USER"@"$SERVER":"$DATABACKUP"/"$1"/"$1"."$NOW"
                ssh "$USER"@"$SERVER" "ln -s ${DATABACKUP}/${1}/${1}.${NOW} ${DATABACKUP}/${1}/current"
            fi
        fi
    fi
}

```

---

### Post by CharlesA on 2015-09-12
> **TheFu said:**
> 
Watching drive capacity is something your monitoring tool should be doing - not something a backup tool does. munin, logwatch - start there.

Agreed.

I found a chunk of code that runs a df and emails you the results here:
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

It is kinda hard to believe that was back in 2011...

---

