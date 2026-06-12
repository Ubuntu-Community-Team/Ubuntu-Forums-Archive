---
title: "Ubuntu Server - Shutdown script"
date: 2012-07-17
forum: Server Platforms
---

### Post by rodrigomartinho on 2012-07-17
Hello.

I am running Ubuntu Server x64 12.04. I have apcupsd properly running. I would like my server to run a script before it is shutdown by apcupsd.

Since I didn't find something specific for a shutdown from apcupsd, I tried to make a general shutdown script, putting it at init.d and running update-rc.d for making the symlinks in rc0.d (shutdown) and rc6.d (restart).

My script is for making a backup of a mysql database. When I tested it shuting down the server, the script was run, but the resulting file was empty. That leads me to think the script didn't have the proper time to finish.

So, I would like some help for:

1. Making a script specific for a shutdown from apcupsd, or
2. For a general shutdown script (which would be very fine for my needs too), if it is right that my script didn't have enough time to run, how could I control its running time so I am sure it will finish before shut down. In future, my script won't only make a backup of my data, but it will upload it via ssh to another server, which will take some time (about 5 min).

Thaks in advance,

Rodrigo Martinho.

---

### Post by LHammonds on 2012-07-18
I'm guessing the shutdown called your script and then immediately continued the other shutdown processing such as stopping the mysql service, unmounting drives, etc.
 
You probably need to figure out how to make sure the script is run 1st and nothing continues until that script is finished.
 
If you cannot get that to work well, you might want to look at having mysqldump called at a regular interval throughout the day and always write to the same location/file(s).
 
LHammonds

---

### Post by rodrigomartinho on 2012-07-19
Hello LHammonds.

That's what I am thinking, the other shutdown processes go on, so my script isn't finished.

What I am looking for is exactly a way to make other shutdown processes wait for my script to finish before they are run. Any clue?

I read something about exit codes. Are they a way of accomplishing this?

I already thought about making the backup regular along the day, but that wouldn't be the best practice. In fact, I already do this once a day. But, since I need the most indate data before shutdown (a dotproject database, used for managing my companies' projects, so I move it to another server), I would need many backups a day, and all that just for some energy breakdowns in a year.

Regards,

Rodrigo Martinho.

---

### Post by LHammonds on 2012-07-19
Well, when you are in a script, you can get the exit code of the last command executed by using $?
 
Example:
```

tar -cpzf /tmp/backup.tar.gz /opt 1>/dev/null 2>&1
RETURNVALUE=$?
case ${RETURNVALUE} in
0)
  echo "Program worked as expected."
  ;;
1)
  echo "Error Code 1 - This program failed"
  ;;
*)
  echo "Error Code ${RETURNVALUE} - This program failed"
  ;;
esac

```
 
**EDIT:** How long does it take for mysqldump to create a single sql export for all your databases?  If it does not take a large amount of time, you could export to the same file (always overwriting) which means you don't take up any more space that just that one file.  How long it takes to do the export will determine if this would be viable or not.

---

### Post by rodrigomartinho on 2012-07-19
Ok, so it seems exit codes have nothing to do with controlling shutdown proccesses.

mysqldump doesn't take more than some seconds for this database. So I could use your suggestion and make many dumps a day. But the dump isn't all I need to do. I need to upload the database via ssh to another server, which would take 5-10 min, and making this many times a day would consume my bandwidth much more than needed if I learned how to control the shutdown proccesses, so dump and upload would need to be done only once before shutdown.

---

### Post by BkkBonanza on 2012-07-20
A better place to put your script would be in the /etc/init/mysql.conf config file for mysql. This doesn't use the old SysV /etc/init.d method but the new way (Upstart). Google and read up on Upstart as it allows you to set a pre-shutdown script for each service and you should be able to prevent mysql from exiting before it's done.

Of course, you'd have to make sure your UPS gives you enough time when apcupsd triggers shutdown.

---

### Post by rodrigomartinho on 2012-07-20
Thx for the advice on Upstart. I will read about it and make some more tests. After them I come back to tell the results.

---

### Post by LHammonds on 2012-07-20
If you continue to export to sql file throughout the day, be sure to compress the file BEFORE you send it offsite to reduce bandwidth.

I use 7-zip to get the smallest file reasonable as well as tar to retain user/group permissions.  Check my sig for links to server setups which contain scripts I use to compress and copy to a remote offsite location.  I also have a purge function that will purge the oldest files until there is enough room to copy the archive...this allows for the maximum amount of backups to be retained which fits on the storage device.

Something else you might want to consider for offsite storage is to use the same filename throughout the day so that what you have on offsite storage is the latest file for the day and only one archive per day.  Example filename: **2012-07-20-schema.tar.7z**   This file can be generated and copied over the wire 20 times a day but the offsite location would only have the latest copy.

It all depends on your hardware capability and your needs.

LHammonds

---

### Post by andreiflorescu on 2012-07-20
I am not an expert.
I found this solution.
I would like to hear comments on it.
Maybe it is not the right one.

I wrote a script to dump the database on shutdown, and put it in /etc/init.d/ ...
 Before the dump operation I started the mysql daemon. And it worked.
I use ubuntu 11.10.

something like:

service mysql start
mysqldump -u root -p[root_password] [database_name] > dumpfilename.sql
service mysql stop

---

### Post by rodrigomartinho on 2012-07-21
I read a little about Upstart, got an example script and made some tests.

This is the script I put on /etc/init:

```

description "dotProject backup"
author "Rodrigo"
#env HOME=/home/rodrigo
start on runlevel [0123456]

pre-start script
# echo "Starts dotproject backup"
end script

script
#service mysql start
/data/temp/dotproject_backup_script
#service mysql stop
end script

post-stop script
# echo "Ends dotproject backup"
end script

```

When I run like this, the same thing happens as when trying using init.d: the .sql file is created, but void.

I also tried andrei's suggestion, but when I make the test with the  mysql start and stop lines uncommented, it seems my script isn't run at  all (no file created). I didn't try andrei's suggestion on init.d yet  though.

I tried too to directly put the mysqldump command on Upstart script (instead of  using my script that have it, named here as "dotproject_backup_script")  and the same behaviour happened.

---

### Post by BkkBonanza on 2012-07-21
With that Upstart config you will get the same results because you didn't put in a dependency. Also your runlevels line is wrong. Your config will do your backup at system start and shutdown. (0 is shutdown, 6 is reboot, 2345 is more what you want).

That is, you would need to make the mysql config dependent on your backup config so that it doesn't shutdown until your backup is done. But probably easier for you is to simply modify (make backup copy first) the /etc/init/mysql.conf config. 

On my server it doesn't currently have a pre-stop script and that's what you would want. Add a pre-stop script that calls your backup. It will run before mysql stop trigger happens. It already has a pre-start and post-start but those get triggered when mysql is started.

Alternately you could add a dependency but that's something I've not tried myself. If you look at that mysql.conf you'll see it has a start dependency like this,

```
start on (net-device-up
          and local-filesystems
	  and runlevel [2345])
```

This makes mysql dependent on those 3 conditions being met. You could alter the "stop on" conditions to make it only stop when your backup is completed. Then you set your backup conf to only start on runlevel 0 (shutdown). mysql wouldn't shutdown until both runlevel 016 and your backup is done. I'm not sure if the kernel will wait on mysql though. That would require more reading on whether upstart requires all jobs to complete or whether after some timeout it just kills everything.

Anyway, I think the condition would be something like this,

```
stop on (runlevel [016]
        and backup stopped)

```

Where backup is the name of your backup job started by backup.conf

---
All of this seems rather tricky. Looking briefly at the apcupsd docs I see that when your ups detects a problem and when it goes onto battery there is a call made each time to /etc/apcupsd/apccontrol with an argument. You would likely find it better and much easier to trigger your backup from the "powerout" message. According to my reading (I don't have one) there is no default action for these messages but you could simply start your backup by adding a section like this to the /etc/apcupsd/apccontrol script.

```

if [ "$1" = "powerout" ]; then
  dobackup
fi

```

As long as your UPS gives you enough time between detecting the power out, to going onto battery and then to shutdown.

---

### Post by rodrigomartinho on 2012-07-21
Thanks for the help BkkBonanza.

I thought it would be easier to accomplish this. I'll need some more reading.

After further tests with mysql conf file and/or apcupsd I come back to tell the results and maybe ask for more help.

---

### Post by andreiflorescu on 2012-07-23
> **andreiflorescu said:**
> I am not an expert.
I found this solution.
I would like to hear comments on it.
Maybe it is not the right one.

I wrote a script to dump the database on shutdown, and put it in /etc/init.d/ ...
 Before the dump operation I started the mysql daemon. And it worked.
I use ubuntu 11.10.

something like:

service mysql start
mysqldump -u root -p[root_password] [database_name] > dumpfilename.sql
service mysql stop


[COLOR=Navy]I wrote two files
[/COLOR]
/etc/init.d/backup_mysql
/etc/init.d/backup_mysql.sh

[COLOR=Navy]owner and permission for this two files[/COLOR]
-rwxr-xr-x 1 root root 187 2012-07-23 07:51 /etc/init.d/backup_mysql
-rwxr-xr-x 1 root root 542 2012-07-23 07:56 /etc/init.d/backup_mysql.sh

[COLOR=Navy]content of this two files[/COLOR]
1.) /etc/init.d/backup_mysql

#!/bin/bash
#backup database anatomie

echo "begin database backup"
mysqldump -u root --password='password' --opt anatomie > /home/andrei/backupMYSQL/backup.sql
echo "end database backup"

2.)  /etc/init.d/backup_mysql.sh

#!/bin/bash
#backup database anatomie 

#redirect stdout and stderr to file /home/andrei/erori
#for this script

#status of mysql daemon and start mysql
service mysql status 2>/home/andrei/erori 1>>/home/andrei/erori
echo "start mysql daemon" >>/home/andrei/erori
service mysql start 2>>/home/andrei/erori 1>>/home/andrei/erori

#run scrip backup_mysql that backs up the database anatomie
/etc/init.d/backup_mysql 2>>/home/andrei/erori 1>>/home/andrei/erori

#stop mysql daemon
service mysql stop  2>>/home/andrei/erori 1>>/home/andrei/erori

- [COLOR=Navy]made  appropriated [/COLOR][COLOR=Navy]links[/COLOR]
sudo update-rc.d backup_mysql.sh start 10 0 6 .

- [COLOR=Navy]created the directory /home/andrei/backupMYSQL[/COLOR]

For me this worked.
I am realy interested.
Does it work for you ?

---

### Post by rodrigomartinho on 2012-07-23
Hello andrei. Thx for your help.

Since Upstart is the replacement of init.d, I got interested in learning it. So I am firstly making the tests BkkBonanza suggested. Soon I 'll make your tests too.

After some reading on Upstart I got what BkkBonanza meant. Instead of making a new job, I could work on mysql's one. So the first thing I tried, as suggested, was to put a pre-stop script on mysql that calls my backup script. It worked. Now the resulting file wasn't void anymore.

Since this dump takes just 1 second or so, I still don't know if system will wait for the other part of the process, taht is to upload the resulting dump file via ssh, which would take about 5 min.

This will be my next test. To put the ssh upload on the pre-stop script.

Soon I come back with the results.

---

### Post by rodrigomartinho on 2012-07-23
I made one test and it seems it worked! I just had a problem with permissions on the uploaded file, but that is a problem related to the rsync command itself, not with the Upstart script.

I will learn to generate the pass keys for ssh and make some tests.

---

### Post by rodrigomartinho on 2012-07-24
I made further tests. Now I understood how rsa keys works and generated the needed ones for the passwordless ssh upload of the mysql dump.

After that, I had another problem with the rsync command, because I have spaces on folder names. After solving this, all worked as expected.

So, concerning the specific problem of the shutdown script, a pre-stop condition on mysql Upstart script, as suggested by BkkBonanza, was all that was needed.

Due to rsync compression, my upload is actually taking less than a minute, so I still don't know if other problems could happen if pre-stop condition took too much time.

I will make some last tests, if all works as worked now this is solved. Thank you all for your help.

---

