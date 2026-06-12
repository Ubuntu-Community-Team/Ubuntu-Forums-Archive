---
title: "Database clarification (MySQL + ownCloud)"
date: 2014-09-29
forum: Server Platforms
---

### Post by Roasted on 2014-09-29
Hello friends. I'm running ownCloud on my 12.04.5 server at home. I noticed the sync client was running crazy slow, to the point ownCloud was nearly unusable. I read through ownCloud's documentation and they recommend MySQL/MariaDB/Postgre, despite SQLite being the default option (they choose SQLite due to the less amount of administrative overhead), which I suppose makes sense.

I switched to MySQL. I found a guide online and created a database for ownCloud simply named "owncloud", along with a corresponding user. (by the way, this sucker is *fast* now that I switched it)

Here's my question... despite the fact things are working, I still like to 'make sure' all is well... am I correct in understanding that all you need is one database + one database user for the multitude of ownCloud users to function? i.e. I don't need specific users within MySQL/Maria/whatever to make this happen? I guess all ownCloud users are accessing the "owncloud" MySQL database... aka me + my wife + my mother + mother in law + bob + **** + jane + etc + etc = all using the owncloud database via the exact same db user I created.. eh?

For security purposes, am I best off creating one user per database? Or am I okay if I'm using a generic "administrator" (or whatever) account and assigning that user to have full privileges (or whatever necessary) over the any database I add, whether it be a scenario where it's just ownCloud, or in another more complicated scenario where it's ownCloud database + abc database + xyz database, etc?

I'm sure in the business world having other users with limited privileges here and there for certain databases would be a different story, but we're talking about a home setup here. That said, I don't want my home setup to be a rag-tag type of comedy show. I just want to make sure that I'm doing this logically. Like anything else, I'd rather do it once. ;)

Thanks for any insight!

---

### Post by mastablasta on 2014-09-29
i think that database made for user owncloud where there are more users in it. at least most of web stuff works like that. the program gets access to database not the user of that program (except for admin maybe) make sure you have good password try not to name it admin or whatever is default in MySQL.

Also what si up with sync client being slow? it seem the issue is from 2013. I am still testing it if it is usable or not. the client needs work in my opinion. there is not setting I could find to set up the time for syncing (e.g. so it would do it from 1 AM -5PM only).

---

### Post by Roasted on 2014-09-29
I don't think it's a sync client issue. At least, not anymore. There were some speed issues a year/two years ago, but the client itself has been patched. All sources indicated that the database in question is the defining point. I understand ownCloud's decision to use sqlite by default, because it'll still serve the needs of many people running smaller setups. I only noticed it running terribly slow once I switched our household from Dropbox to ownCloud for our automatic "sync pictures/videos over wifi" phone setup. Then we went on vacation, took a thousand pictures, came back, and OC ran darn slow. Once I switched it to MySQL, it was outstandingly faster.

That said, I just don't have much experience with MySQL, which is why I wasn't sure if there was a "best practice" type of process I should follow, or if I happened to have already done it properly without realizing it. It felt weird to me that ownCloud would access MySQL for ALL ownCloud users based entirely on one MySQL user, but then as I started to think more deeply about it, I feel like I understood it. Kind of like a secure car garage. Everybody has access because the guy at the front gate has the key and lets you in as long as you're a legit 'customer' of that car garage.

---

### Post by badger_8007 on 2014-09-30
You only need to setup 1 database and 1 mysql user because that will be used by the ownCloud service, regardless of how many users you have setup "inside" owncloud, it will automatically write up their info (activity, etags, etc) in the tables of the database for each "user". Regarding the user you created it is ok to do it as a security measure because (if you set it up according to the tutorial on ownCloud site) that user only will have full privileges over the owncloud db, and it keeps you from using the "root" account for it, which in itself is a security risk.

I would really advise you to upgrade your server installation to 14.04 because I think it runs better with it, but that is up to you.

I myself have setup owncloud 7.0.2 in Ubuntu Server 14.04.1 for using it on our business and so far it is working fine with MariaDB 10.0.14, Apache 2.4, PHP 5.5.9, and a 100Mbps fiber internet ;)

---

### Post by Roasted on 2014-10-01
Thanks for the info. That helps solidify what I thought made sense, but I'd always rather ask and make sure. I actually had interest in tinkering with MariaDB myself. I might end up doing that given the way things with MySQL are being handled these days. Since MariaDB is compatible I guess I'd follow pretty much the same instructions for the most part to run MariaDB, eh?

I'm definitely planning on upgrading my server. It's a limitation of time right now in case anything goes south. Soon I'll pull an image of the install with Clonezilla and do an in place upgrade (because why not?). Worst case I do a rebuild or image back to 12.04.5, but I tar /etc nightly so all of my config files are a copy paste away. :) I did a rebuild last year after my root drive failed. I had that darn thing and all of my services running before two Pink Floyd songs were over, which was almost a bummer given I had a sweet playlist set up...

---

### Post by mastablasta on 2014-10-01
yeah it's amazing how fast things are up and running. I just saw a video posted by Mr. Shuttleworth on G+ where Juju deployment is explained. I mean it was  clicky, clicky, click, wait a bit for files to be copied and all is suddenly setup. amazing!

I think I will need to go with MySQL (mariaDB) as well since sql lite seems to be aimed at single user. that is if we go the own cloud way. - since it seems like you were successful -  what tutorial did you follow?

---

### Post by Roasted on 2014-10-01
> **mastablasta said:**
> yeah it's amazing how fast things are up and running. I just saw a video posted by Mr. Shuttleworth on G+ where Juju deployment is explained. I mean it was  clicky, clicky, click, wait a bit for files to be copied and all is suddenly setup. amazing!

I think I will need to go with MySQL (mariaDB) as well since sql lite seems to be aimed at single user. that is if we go the own cloud way. - since it seems like you were successful -  what tutorial did you follow?

I ran SQLite for quite a while without issue. What changed for me was switching our phones to upload pictures/videos over wifi to ownCloud instead of Dropbox. My wife and I are like any other first time parents with smartphones. Clickity click snap snap ZOOM and just like that we have 800 new pictures. ;) 

When we were on vacation last week, we had wifi, so our phones synced over wifi to my server back home for any new pictures we took. Thing is when I got home, things were crazy slow. The web UI was slow, the sync client on my computer was slow, etc. To give you an idea, it gave me an ETA of 53 hours to synchronize 850 MB of pictures over GIGABIT to the server. A bit of Googling suggested something other than SQLite was the way to go. 

I followed [this guide]("http://doc.owncloud.org/server/6.0/admin_manual/configuration/configuration_database.html"), however, I really only recall running these particular commands... 

```
To start the MySQL command line mode use:

mysql -uroot -p

Then a mysql> or MariaDB [root]> prompt will appear. Now enter the following lines and confirm them with the enter key:

CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
CREATE DATABASE IF NOT EXISTS owncloud;
GRANT ALL PRIVILEGES ON owncloud.* TO 'username'@'localhost' IDENTIFIED BY 'password';


```

I seem to think there was a variable I had to change in the config/config.php file... something about saying sqlite3 => false, so ownCloud didn't boot up utilizing sqlite again. At the login screen of the web UI it asked me what I wanted to do, so I selected MySQL, put in the information from the CREATE USER/CREATE DATABASE commands above, and I was golden.

---

### Post by SeijiSensei on 2014-10-01
I suggest learning how to run mysqldump from the command line to back up your database.  It will create a plain-text file that can be read back in with the mysql command-line client if you need to restore the data.  Here's a script I use for this purpose: [http://ubuntuforums.org/showthread.php?t=2218776&p=12997721&viewfull=1#post12997721](http://ubuntuforums.org/showthread.php?t=2218776&p=12997721&viewfull=1#post12997721)

---

### Post by mastablasta on 2014-10-02
I think owncloud has backup app that will to backups,. perhaps it dumps the database as well. otherwise the dump is very important and saved "my life" 3 months ago. I was able to reinstall and upload a years work after the hack. 

anyway always a good thing to be remembered about this option once in a while.

---

### Post by Roasted on 2014-10-02
Good idea. I should probably tag the database dump as part of my backup scheme. Right now what I do is I have a 2nd server on my LAN. My main server sends a WOL (wake on LAN) packet to it at 3 AM, then a few moments later when it's booted up and available, the main server rsyncs my data over, then once done, remotely shuts it down. That way I have backups in a totally separate box but don't have it running 24/7 sucking down electricity when it only needs to run a few moments a day. I rsync my ownCloud data folder as part of that process, but the database dump makes a world of sense as well. Thanks for the fyi!

---

