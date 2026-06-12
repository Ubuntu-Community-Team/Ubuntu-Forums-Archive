---
title: "What have you automated with custom shell scripts?"
date: 2008-09-11
forum: The Cafe
---

### Post by kpkeerthi on 2008-09-11
Post in a few sentences what tasks have you automated with custom  shell scripts.

EDIT: Here is what I have:

1. Script to automatically download the [hosts file]("http://www.mvps.org/winhelp2002/hosts.htm") and update /etc/hosts. Cronned it to run once a week.

2. Script to automatically download bad-peers blocklists from bluetack and update deluge. Cronned it to run once a week.

3. Script to backup/restore my partitions.

4. System cleanup scripts.

5. Script to download (download only, no auto-installation!) updates from the repositories. Cronned to run daily.

---

### Post by barbedsaber on 2008-09-11
working on the making coffee in the morning, feeding the dog, waking me up to song from my collection, adjusting the air con, and putting on some bacon.
(I love bacon)

---

### Post by kpkeerthi on 2008-09-11
> **barbedsaber said:**
> working on the making coffee in the morning, feeding the dog, waking me up to song from my collection, adjusting the air con, and putting on some bacon.
(I love bacon)

Well.. great. What BASH version do you have that does all that?

---

### Post by Trail on 2008-09-11
I have a collection of material organized in my filesystem as `.../<year>/<name>/<author>_item'. I use a series of scripts to manage and index that stuff. For example, I maintain directories with symbolic links per year or per name or per creator, another directory with statistics such as largest directory size (as calculated through a maze of greps and awks and trs and stuff), and some other helper stuff for the occasional cleanup.

---

### Post by -grubby on 2008-09-11
I have 2 cronjobs to backup remote mysql databases

---

### Post by beercz on 2008-09-11
Cron job script to back up my home data to remote servers daily.
Cron job script to back up sql databases to remove servers daily.
Scipt to automatically download and install updates on my servers (which I run manually).

Also, as I am using Intrepid, I am having problems with nspluginwrapper package for playing flash movies.  I have created a script that quickly installs a previous version should flash stop working because of updates to this package.  At the moment I have synaptic locking the package to the version that works, but occasionally I update to the lastest version and if it doesn't work, I run my script to quickly revert back to the previous version.  I am looking forward to this script being obsolete soon!

I have also written my own firewall script (based on iptables) but I no longer use it.

---

### Post by gvartser on 2008-09-11
Have a lot of scripts, one of them has automated the whole DL process of nzb's.

1 Dl's all posts.
2 Repairs all files
3 Unpacks the files
4 Creates iso's

All i have to do is put in the writable media to burn.

Everything is initiated from a webpage.

And its quable so I can have unlimited DL's in the que.
/g

---

### Post by forger on 2008-09-11
> **kpkeerthi said:**
> Post in a few sentences what tasks have you automated with custom  shell scripts.

EDIT: Here is what I have:

1. Script to automatically download the [hosts file]("http://www.mvps.org/winhelp2002/hosts.htm") and update /etc/hosts. Cronned it to run once a week.

You'll have more success restricting adware/phishing sites by using [www.opendns.com](www.opendns.com) DNS servers :)

---

### Post by kpkeerthi on 2008-09-11
> **forger said:**
> You'll have more success restricting adware/phishing sites by using [www.opendns.com](www.opendns.com) DNS servers :)

I've been thinking about doing this for quite some time but been lazy or keep forgetting. lol! 

Thanks for reminding, though! Will get this done by this week-end (hopefully!)

---

### Post by koenn on 2008-09-11
> **barbedsaber said:**
> working on the making coffee in the morning, feeding the dog, waking me up to song from my collection, adjusting the air con, and putting on some bacon.
(I love bacon)

This could help towards the dog feeding.
[http://www.leeholmes.com/blog/DIYCatFeederAndWaterDispenser.aspx](http://www.leeholmes.com/blog/DIYCatFeederAndWaterDispenser.aspx)
it's cat oriented but probably customizable.

If you've made any progress on the making coffee in the morning, I'd be interested.

---

### Post by forger on 2008-09-11
> **kpkeerthi said:**
> I've been thinking about doing this for quite some time but been lazy or keep forgetting. lol! 
Thanks for reminding, though! Will get this done by this week-end (hopefully!)
No problem :) It's a 5-minute thing, even if you have a router it's *dead easy* - the more tricky part is to actually log in to opendns and control your locked websites using a dyndns-compatible client program, which takes a bit of more minutes :)

---

### Post by graabein on 2008-09-23
> **kpkeerthi said:**
> 2. Script to automatically download bad-peers blocklists from bluetack and update deluge. Cronned it to run once a week.

3. Script to backup/restore my partitions.

> **beercz said:**
> Cron job script to back up my home data to remote servers daily.

I'm interested in these scripts. If you can post them or submit a link to where I can find examples that would be great.

I've just started reading about bash scripts because I want my file server to automatically download torrents when I drop a torrent file in a certain directory on the server.

Backing up my camera and document folder to the server each night would be sweet.

I'll do a search for rsync (or whatever it was called).

---

### Post by beercz on 2008-09-23
> **graabein said:**
> I'm interested in these scripts. If you can post them or submit a link to where I can find examples that would be great.

I've just started reading about bash scripts because I want my file server to automatically download torrents when I drop a torrent file in a certain directory on the server.

Backing up my camera and document folder to the server each night would be sweet.

I'll do a search for rsync (or whatever it was called).
Hi

I use [rsnapshot]("http://rsnapshot.org") within my script to execute my incremental backups - it is based on rsnyc, and uses ssh with keys.

I use my script to write a log file of my backup and send it to my machine that is being backed up, from the backup machine.  It is my script that cron executes.

Here is the script:

> #!/bin/bash

#script to backup ianpc
#April 2007

#reference for logfile
LOGFILE=/home/ian/ianpcbackup.log

#store the current date and time
TIMENOW=`date`

#add separator to log file
echo "=============================================================" >> "$LOGFILE"
echo "=============================================================" >> "$LOGFILE"

#add the date to log file
echo "Starting backup at $TIMENOW." >> "$LOGFILE"

#execute the backup
/usr/local/bin/rsnapshot -c /home/ian/apps/rsnapshotconfig/rsnapshot.conf daily > "$LOGFILE"

#add separator to log file
echo "=============================================================" >> "$LOGFILE"

#add timestamp and diskspace usage to log file
#store the current (finish) time
TIMENOW=`date`
echo "Finishing backup at $TIMENOW." >> "$LOGFILE"
df -h >> "$LOGFILE"

# copy logfile to ianpc - /home/ian/logs
scp "$LOGFILE" ian@192.168.0.2:/home/ian/logs

#finish
exit 0


---

### Post by kpatz on 2008-09-23
All sorts of stuff...

1.  I have a script to notify me and update my ZoneEdit DNS if my dynamic IP changes (invoked by dhclient).

2.  I have a script to update the 6 or so antivirus programs I have on my box to scan malware samples.

3.  I have a script to scan malware samples with those 6 or so antivirus programs.

4.  On my MythTV box, I have a script I use to update mpd's playlist when I load new music files.

5.  I have a perl script that does reverse-DNS lookups for IPs that probe my firewall, used to update a database.

---

### Post by caljohnsmith on 2008-09-23
I've got a fun little script that does an ARP scan of all the other hosts on my LAN/WLAN, so I can see who else is using the network. It's a really quick way to make sure no nosy neighbors/wardrivers are leeching my WLAN, without having to log into my router to check. :)

---

