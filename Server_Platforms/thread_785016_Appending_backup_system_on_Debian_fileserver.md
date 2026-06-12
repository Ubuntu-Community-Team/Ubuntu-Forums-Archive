---
title: "Appending backup system on Debian fileserver"
date: 2008-05-07
forum: Server Platforms
---

### Post by Madman6510 on 2008-05-07
Recently, after hearing horror stories about how important backups are, I decided to throw together another fileserver for backups.

Now, both the servers are working perfectly, connecting to all the windows machines through Samba. The main fileserver has ALL of the user files and settings for every windows machine on the network. What I need to do is make it so that the main server backs up all of the files in a certian directory (/network, if you need specifics" to a samba share on the backup server. I want this backup to run every night at 3 AM, doing an appending backup (only backing up new or changed files, while leaving the old ones alone to save time).

Sorry if this sounds REALLY complicated, but I have absolutely NO idea on how to do this.

---

### Post by hyper_ch on 2008-05-07
with rsync and cron :)

---

### Post by windependence on 2008-05-07
For a little heavier solution you can try AMANDA or BACULA.

[http://www.amanda.org/](http://www.amanda.org/)

[http://www.bacula.org/en/](http://www.bacula.org/en/)

-Tim

---

### Post by cdtech on 2008-05-07
A good backup technique can mean the difference between a slight computer setback or living through your own electronic apocalypse, trust me, I know.

I sent you a section of the script I use for my server. See what you think, if thats what your looking for, let me know. It's saved my a## a few times, I've pulled files from the tar that I accidently rm'd once or twice.

It back's up using monthly, weekly, and daily incremental.

Hope this helps....

---

### Post by songshu on 2008-05-08
personally i use rsnapshot.

i think its a great simple solution that allows to do even hourly backups without wasting much diskspace

it works something like this

    *
      !!!MIND, this is a great script but, FOR SOME REASON IT USES tabs AND WILL NOT WORK WITH SPACES!!!!

# apt-get install rsnapshot
# nano /etc/rsnapshot.conf

comment out the interval's for the backup

interval        hourly  6
interval        daily   7
interval        weekly  4
interval        monthly 6

then we set the directories we want to backup for the file server:

backup  root@192.168.1.8:/home/share/   local/shares/
backup  root@192.168.1.10:/var/www/avantfax/faxes/      local/faxes
backup  root@192.168.1.88:/home/        local/mails


And uncomment the localhost entries

Too make sure that cron will do the hard job for us:

# nano /etc/cron.d/rsnapshot

and uncomment so it looks like this

  GNU nano 2.0.2                                    File: /etc/cron.d/rsnapshot

# This is a sample cron file for rsnapshot.
# The values used correspond to the examples in /etc/rsnapshot.conf.
# There you can also set the backup points and many other things.
#
# To activate this cron file you have to uncomment the lines below.
# Feel free to adapt it to your needs.

 0 */4  * * *           root    /usr/bin/rsnapshot hourly
 30 3   * * *           root    /usr/bin/rsnapshot daily
 0  3   * * 1           root    /usr/bin/rsnapshot weekly
 30 2   1 * *           root    /usr/bin/rsnapshot monthly

rsnapshot will need ssh to do remote backups

# apt-get install openssh-server

# nano /etc/ssh/sshd_config

and make sure ssh only listens to the local address

ListenAddress 192.168.1.13

Too make sure that rsnapshot can login without a password

# ssh-keygen -t rsa

and accept the defaults without a passphrase

# ssh-copy-id -i ~/.ssh/id_rsa.pub root@192.168.1.8
# ssh-copy-id -i ~/.ssh/id_rsa.pub root@192.168.1.10

---

### Post by dgarnett on 2008-05-08
rdiff-backup works really well for what you're trying to do as well.  You can also check out Duplicity if encrypting the backups is important.

---

