---
title: "retrieving postgresql db from Ubuntu12.04 Server hard disc"
date: 2017-07-01
forum: Server Platforms
---

### Post by Heeter on 2017-07-01
Hi all,

A Mirror RAID array failed on a 12.04Ubuntu server running postgresql/apache, a LAPP I guess.

I have the final somewhat working hard disc sitting here on my desk.

The HD is making grinding sound, but I am able to "see" it when mounted to my ubuntu desktop when I mount it using fstab entry. I keep getting superblock errors when I try "mount -a" after fstab edit.

Also, I do have the backup up and running on new hardware, but I would like to retrieve the postgresql db as it will save me a ton of data input since the last backup about a month ago.

I have never done any of this before, so any input will be incredibly appreciated.

Regards

---

### Post by SeijiSensei on 2017-07-01
If it's a RAID1 array, what's the condition of the other disk?  They didn't both fail at the same time, right?  Does that mean the server is running off that disk?

The very first thing you should do if you can get the PostgreSQL server to start again is to run this

```
pg_dumpall -U postgres > pg_backup.sql
```

That will create a pure text backup of the entire database.  Once you get a replacement server up and running, you can restore the database with psql.

You should be running a command like this every night out of cron and copying the backups to a location off the server.

Also you should be planning on migrating that server to at least 14.04 or, better, 16.04.  12.04 reached its end-of-life on April 28th and will get no further updates and, more importantly, no more security updates.

---

### Post by Heeter on 2017-07-01
Hi The other 3 HD in the 4 HD Mirror are toast. The server was running off this last one before before it nearly collapsed too. Server was showing no signs of hard disc failure.

I cannot get the server up and running anymore (Been trying for the last 3 days), so I am trying to do is salvage the DB from the HD plugged into my Ubuntu laptop

New Server is brand new and i converted the last backed up image to a VMWARE appliance, so now it is sitting on a replicated and redundant  appliance setup.

If I can just get this DB off the HD manually using my laptop 

Regards

---

### Post by SeijiSensei on 2017-07-01
You can try copying the entire /var/lib/pgsql directory tree, but I don't know how well that works with PostgreSQL.  Notice that that tree is owned by the postgres user.  You'll need to mimic the ownership and permissions on any new system.  I'd install the postgresql server package, then in /var/lib move the newly-created pgsql directory to pgsql.old and make your backup /var/lib/pgsql.  You might need to make sure you're using the same version of Postgres as was running before since these are binary files whose architecture may change between versions.

Please tell me you will start running a daily pg_dump backup on any new server you set up.  Here's a bash script that I use if you want some guidance:

```

#!/bin/sh

BACKUP_ROOT="/var/lib/pgsql/backups"
LOGDIR=/var/log/backups
ROTATE=8
HOST=localhost

BACKUPDIR="$BACKUP_ROOT/pgsql"
USER=postgres

### No user-configurable parts below! ###

# if a host is listed on the command line, use that
[ "$1" != "" ] && HOST=$1

TODAY=$(date +%y%m%d)
STALE=$(date +%y%m%d --date="$ROTATE days ago")
LOG="$LOGDIR/pgsql-$HOST.$TODAY.log"
STALELOG="$LOGDIR/pgsql-$HOST.$STALE.log"

# make today's directory
mkdir -p "$BACKUPDIR/$HOST/$TODAY"

# retain monthly copy on 15th; delete state logs
[ "`date +%d`" != "15" ] && rm -rf "$BACKUPDIR/$HOST/$STALE"
rm -f $STALELOG

# put the backup in this directory
cd $BACKUPDIR/$HOST/$TODAY

echo -n `date -R` >> $LOG
echo " Postgres backup procedure for $HOST starting" >> $LOG

# get list of databases
DBLIST=$(echo 'select datname from pg_database;' | psql -U postgres template1 | grep '^\ ' |
 tail -n+3)

for db in $DBLIST
do
    CURRENT="$db.pgsql"
    echo "Creating current backup file $CURRENT" >> $LOG
    
    # dump database, connecting to remote host $HOST if required
    /usr/bin/pg_dump -U $USER -h $HOST $db > $CURRENT
    echo "Compressing $CURRENT" >> $LOG
    gzip $CURRENT    
done

chmod 0600 $BACKUPDIR/*

echo -n `date -R` >> $LOG
echo " Postgres backup procedure for $HOST completed" >> $LOG

```

This script extracts the list of databases from PG, then writes individual backup files for each one to the directory specified in BACKUPDIR.  It creates individual dated subdirectories which it keeps for ROTATE days.  It also preserves one backup a month for archival purposes.  The script needs to run as root, so it should be placed in /etc/cron.daily.

---

### Post by Heeter on 2017-07-01
I would like to copy over the just a straight folder, it is being inserted into the exact same setup, an up and running back up, so the permissions and folder structure and users are exactly the same. 

I basically took an image backup of the whole setup and am now running it, just the data is approximately one month old. 

I hit another snag. I am trying to mount the hard disc that I would like to extract the data from through USB, but it is an LVM2 partition. It is not automounting onto my laptop 16.04LTS

Don't know if I should start another thread.

Regards

---

