---
title: "rsync and exclude"
date: 2013-11-01
forum: Server Platforms
---

### Post by alfirdaous on 2013-11-01
Good day to you,

I would like to backup and do some excludes:

```

rsync -e 'ssh -p 2345' -avr --log-file=/var/log/rsync.log --exclude-from='backupExcludes' /home/alfirdaous/www/ USER@IP:/home/alfirdaous/BackUps/

```

backupExcludes is on the same directory as the above command line, but while checking destination, I can find all files that I have excluded.

backupExcludes:
```

/home/alfirdaous/www/Downloads/

```

Thx for your assistance

---

### Post by TQLeaman on 2013-11-01
I also use excludes in my RSync backups and the format of the command line I use is this:

[INDENT]rsync $VERBOSE --archive --delete $EXCLUSIONS $SOURCEPATH $BACKUPPATH[/INDENT]

The script uses a bunch of variables in various ways to change what is backed up where and how etc...

For instance my call to back my /Data volume to a local USB hard drive sets up the variables like this:

[INDENT]...
# Backup Data Volume
echo "Backing Up Data" >> $LOGFILE
echo "" >> $LOGFILE

VERBOSE="--verbose"
SOURCEPATH="/Data/*"
BACKUPPATH="/media/tq/WDX/Backup"
EXCLUSIONS="--exclude /Cache/* --exclude lost+found --exclude /VMs/Archives/*"
...[/INDENT]

Unpacked, the command line would look like this:

[INDENT]rsync --verbose --archive --delete --exclude /Cache/* --exclude lost+found --exclude /VMs/Archives/* /Data /media/tq/WDX/Backup[/INDENT]

The three obvious differences are that I am using --exclude not --exclude-from, I am not using an equals sign and not using quotes.

Hope that helps point you in the right direction.

TQ

---

### Post by SeijiSensei on 2013-11-01
> **alfirdaous said:**
> backupExcludes is on the same directory as the above command line

What if you include the full path to backupExcludes?

---

### Post by alfirdaous on 2013-11-02
Thx [**[COLOR=#000000]TQLeaman[/COLOR]**]("http://ubuntuforums.org/member.php?u=153909"), I would like to use a file where I can include all my excluded files and directories.

[**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195"): I included the full path, but the same result:

```

--exclude-from=/etc/cron.daily/backupExcludes

```

---

### Post by SeijiSensei on 2013-11-02
A file in /etc/cron.daily should be a script, not a list of file "globs".

Here's an exclude list I use at a client site.  

```

proc/
sys/
dev/
tmp/
/old/
Temp
backup
pgsql/data/base
quarantine/
SpamAssassin-Temp
usr/share/doc
usr/man/
usr/local/man
usr/share/man
etc/httpd/logs
usr/share/doc
var/spool/squid

```

I have a symlink in /etc/cron.daily to a script called /usr/local/sbin/system-backup.  It runs an rsync command with 

```
rsync -av [...] --exclude-from=/usr/local/etc/system-backup/excludes
```

the file whose contents I listed above.  I'm backing up CentOS servers with this and want to exclude junk like the router's Squid web cache or the binaries of my PostgreSQL databases for which I've already generated text-mode dumps.

---

### Post by alfirdaous on 2013-11-02
I moved the exclude file to the desired directory, and place the folders / files and now it Works Great :)

Thnx everybody

---

