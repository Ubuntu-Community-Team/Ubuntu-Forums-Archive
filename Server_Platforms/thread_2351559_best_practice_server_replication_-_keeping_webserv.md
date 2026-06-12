---
title: "best practice server replication - keeping webservers in sync"
date: 2017-02-04
forum: Server Platforms
---

### Post by herrmeier on 2017-02-04
Dear fellow ubuntu admins,

what is the state of the art way to keep webservers and its services (mysql/mariadb) in sync?

For SAMBA-Fileservers, that is quite easy.
But what about webservers and its web-apps?
So far I've read about Multi-Master Replication, Tungsten, Multi-Source-Replication, ring replication, point-to-point replication, galera and so on.

Setup so far:
3 sites in 3 locations, upload bandwith each 10-20MBit.
webapplications are:
owncloud
nextcloud
symfony-webapps
wordpress
and so on.
right now I am using mysql, but everything could be configured to use mariadb instead. No nosql-databases so far.

At night, servers all with UPS are locally backuped, (automysqlbackup/rsync mo,tue,...,fr,plus 1st backup of last 3 months) reports are send by email.
But to reduce downtime I am thinking of using the servers at the remote locations as a backup, so that I'd just have to change DNS-Settings at my domain-provider to another location to be up and running again.
Data changes/day usually less then 1GB all in all.

What would your approach be? Are there built-in tools you can recommend? Is there a book/man page/tutorial/google search phrases you can recommend?
Thank you for reading. Looking forward to your responses,

with kind regards

Hans

---

### Post by Habitual on 2017-02-05
> **herrmeier said:**
> Is there a book/man page/tutorial/google search phrases you can recommend?
Hans: I think that's the first time I've ever seen anyone ask for google search terms suggestions. Quite refreshing.
What I tend to do is 
backup DocumentRoot and export the db that goes with it, include the site.conf from webserver daemon, crons scripts.
Pack it up in tar.gz and ship it off to storage.

Something to read: [Simple UNIX/Linux Backup with rsync]("http://rsync.net/resources/howto/rsync.html")
and [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Don't fret, there's a lot of ways to skin this cat, one for every admin.
Be encouraged. Be very encouraged.

---

### Post by SeijiSensei on 2017-02-05
I only run [Linodes]("http://www.linode.com/") now that are imaged nightly.  If disaster strikes, I can immediately revert to yesterday's backup by creating a new VM and loading the snapshot. I also back up server directories like /etc, /home, /usr/local, /var/log, and /var/spool to the external drive on my home office server using rsync.

I run a nightly job to create plain-text dumps of my SQL databases and back them up with rsync to that server.  I use an SQL query to get the list of databases, then iterate over the list to produce dbname.xxsql.gz files.  Here's a snippet from the PostgreSQL script.  I have a similar one for MySQL.

```

# get list of databases
DBLIST=$(echo 'select datname from pg_database;' | psql -U postgres template1 | grep '^\  ' | tail -n+3)
for db in $DBLIST
do
    CURRENT="$db.pgsql"
    echo "Creating current backup file $CURRENT" >> $LOG    
    # dump database, connecting to remote host $HOST if required
    /usr/bin/pg_dump -U $USER -h $HOST $db > $CURRENT
    echo "Compressing $CURRENT" >> $LOG
    gzip $CURRENT    
done

```

I use SSHFS between these VMs with a common /home hosted on one of them.  In my experience my Linodes' uptimes far exceed 99%, and scheduled outages are well-planned and usually brief.  

I'm very happy letting someone else manage the hardware.

---

### Post by herrmeier on 2017-02-05
Thank you so much for your replies.
@Habitual: I am happy, that my posting lifted your mood. But i just read someone saying, that physics is the science of understanding the nature of things and right now we are not even able to think of the right questions. So I just try to get closer to asking the right questions. Thank you for the links you posted. They are already in my browsers favorites. rsync is already in use especially with -e "ssh -p xxxx". It would be no problem to to sync the data and the config folder of owncloud/nextcloud. But what about the database e.g.? Files and database need to be "snapshoted" at the same time. What I could do would be to this at night:
stop services apache2, mysql and then transfer them to another server at night. Import the database and then I would only miss one day of work(worst case).
Also if I want to keep file/folder permissions I'd have to grant root-access. Port knocking seems to be a little old-fashioned. Is there some new approach?

I am looking for some more advanced syncing/replication.
One that would enables me to switch servers from one second to the other.

@SeijiSensei:
Thank you for your kind and informative reply. Please correct me if I am wrong. sshfs could be a problem, since some of the internet connections are VDSL-Internet-connections and thus are disconnected daily by our ISP. sshfs would also not solve the problem of keeping files and database in sync, am I wrong?
Thirdly if you put data into the cloud, then they are from a law-perspective less secure, then if you run them on your own computer.
Your own computer is like a personal diary, meant to be only accessed by you only. Linodes are cloud services, which means you already lifted the exclusion
of others to this data, therefor the data is less secure.

That's why I'd rather keep the data from cloud services. Especially if it is not exclusively my data.

Please keep posting, I am still looking for the perfect state of the art, most efficient solution and I am sure someone is already closer to it, then I am.

With kind regards, 

Hans

---

### Post by SeijiSensei on 2017-02-05
> **herrmeier said:**
> 
@SeijiSensei:
Thank you for your kind and informative reply. Please correct me if I am wrong. sshfs could be a problem, since some of the internet connections are VDSL-Internet-connections and thus are disconnected daily by our ISP.
SSH is a TCP-based service. It should survive things like a disconnection.  I don't have your ISP, and my connections are not interrupted.

> sshfs would also not solve the problem of keeping files and database in sync, am I wrong?
As I said, the servers share a common /home on one of those machines.  If that machine goes down, then the others won't work either.  As I said, in my experience Linodes are highly reliable.  I've lost the /home server due to scheduled maintenance in an early Saturday (EST) morning, but most such outages extend for less than an hour.

As for databases, you can again have a central DB server that the other machines access over the Internet.  All my machines are connected with OpenVPN tunnels, and the DB server is configured to only accept connections from localhost or from an OpenVPN IP address.  I back up those databases nightly using the dumping procedure I described above, but I could back them up more frequently were it necessary.

> Thirdly if you put data into the cloud, then they are from a law-perspective less secure, then if you run them on your own computer. Your own computer is like a personal diary, meant to be only accessed by you only. 

These are servers engaged in commercial services.  There's nothing on them that would be of interest to law-enforcement unless my handful of email clients are engaged in criminal acts.  These servers do not in any way constitute a "personal diary."  My personal files reside on a server in my home.

---

### Post by Habitual on 2017-02-05
Basically,
I don't shut down apache on low traffic sites.
Here's a skeleton
```
#!/bin/bash
# 59 23 * * * /root/webdump.sh 
mysqldump -u<user> -p<pass> <db> > /path/to/file.sql
tar -pczf /path/to/backups/webdump_$(date +%F).tar.gz /path/to/file.sql /var/www/html/ /etc/apache2/sites-enabled/000-default /root/webdump.sh
rm /path/to/file.sql
#EOF
```

Wow, all that to backup? I'm exhausted just reading it.

---

### Post by herrmeier on 2017-02-11
Thank you both again for your input. 
Both versions are not really capable of keeping large webserver data and database in sync. Please correct me if I am wrong.
What I could do though
several cronjobs as root 
```
rsync --update -aAhXv -P --delete --bwlimit=500 -e "ssh -p <PORT>" /var/www/html [email]root@subdomain.domain.tld[/email]:/path/to/backup/hostnamesourcepc/
rsync --update -aAhXv -P --delete --bwlimit=500 -e "ssh -p <PORT>" /var/lib/automysqlbackup [email]root@subdomain.domain.tld[/email]:/path/to/backup/hostnamesourcepc/
```
Perhaps I'll rsync /var/www/html several times per day, so that it is not so much when it really counts.
touch lockfile.lock
Then to be sure I'll do another rsync of /var/www/data right before I stop the webserver
service apache2 stop
do a mysqldump
do another rsync
import the database on the remote server
service apache2 start
remove lockfile.lock.

But that is just a backup. What about database replication? Doesn't anyone use clusters over WAN? I hope to read more from you.

---

