---
title: "Problem accessing webserver from outside LAN"
date: 2010-10-20
forum: Server Platforms
---

### Post by reklaw on 2010-10-20
I posted this question a while ago but haven't had any luck getting it answered so I reworded everything to make it more clear.

I started an Ubuntu web server on an old work laptop. The purpose of this server is to host a small file-sharing site, a forum, and a wiki. I have no prior experience with command line Ubuntu but am trying to figure this all out.

So far I’ve setup the LAMP server, so apache, mysql, and php are installed. I’ve also installed phpBB3 and Mediawiki. Both phpBB3 and Mediawiki are able to open from inside my LAN. I also have SSH setup and am able to use putty to manage the server from inside my LAN. Mediawiki runs slow internally but this is a secondary concern.

Externally to the LAN I can access the webserver using SSH(but sometimes it is too slow for anything that opens up such as nano or the SQL password prompt to display and the connection drops). I can also browse to the site and see the default apache welcome message. But I cannot open the mediawiki or phpbb site. Both will sit indefinitely and not open. The access log on the server shows that the request is being passed through though.

Again, if there are any logs or config files that would help let me know and I'll post them as well.

Thanks for any help!!

---

### Post by SeijiSensei on 2010-10-20
I'm guessing that the index.php scripts are timing out.  What do you see in /var/log/apache2/error.log?  

You can have PHP spit its errors out on the screen by setting display_errors to "on" in /etc/php5/apache2/php.ini then restarting apache with "sudo service apache2 restart".

---

### Post by cariboo on 2010-10-20
How is your server connected to the network? If it times out using ssh, you're aren't going to be able to access much via http. Another thing to check is if there is anything using all your cpu cycles, use top, it is installed by default.

---

### Post by reklaw on 2010-10-20
Just tried to edit the php.ini as well as run top and both have the problem with SSH timing out so I'll have to do that after work.

Cariboo,
The server is plugged into a router which is plugged into a cable modem. The router is setup to update the dyndns entry and then I use that domain name to connect.

The connection isn't anything great but it is standard comcast speed, at least a few megabits consistently.

Will check CPU cycles and check the php.ini around 6 and post the results.

Thanks!

---

### Post by reklaw on 2010-10-20
This is what I set php.ini to...

; display_errors
;   Default Value: On
;   Development Value: On
;   Production Value: On

; display_startup_errors
;   Default Value: Off
;   Development Value: On
;   Production Value: Off

; error_reporting
;   Default Value: E_ALL & ~E_NOTICE
;   Development Value: E_ALL | E_STRICT
;   Production Value: E_ALL & ~E_DEPRECATED

; html_errors
;   Default Value: On
;   Development Value: On
;   Production value: On

; log_errors
;   Default Value: On
;   Development Value: On
;   Production Value: On

This is what was in the error log after I made those changes.

This error popped up every now and then.
[Wed Oct 20 19:47:06 2010] [error] [client xx.xx.xx.xx] File does not exist: /var/www/favicon.ico

The rest of the errors was just lines of this.
[Wed Oct 20 19:47:14 2010] [error] [client xx.xx.xx.xx] PHP Warning:  dba_open(/var/lib/mediawiki/images/tmp/mw-cache-wikidb.db,cl): No such handler: db3 in /usr/sha$

The content of the top output looked fairly low... Here that is...

top - 19:41:07 up 7 min,  1 user,  load average: 0.02, 0.03, 0.00
Tasks:  92 total,   1 running,  91 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.2%sy,  0.0%ni, 99.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2577832k total,   153076k used,  2424756k free,    14856k buffers
Swap:  7548920k total,        0k used,  7548920k free,    64724k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1453 lee       20   0  2520 1188  924 R    0  0.0   0:00.45 top
    1 root      20   0  2756 1604 1196 S    0  0.1   0:00.51 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0
    4 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1
    7 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      20   0     0    0    0 S    0  0.0   0:00.04 events/0
   10 root      20   0     0    0    0 S    0  0.0   0:00.00 events/1
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 pm
   17 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers
   18 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default
   19 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/0
   20 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/1
   21 root      20   0     0    0    0 S    0  0.0   0:00.00 kblockd/0
   22 root      20   0     0    0    0 S    0  0.0   0:00.00 kblockd/1
   23 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpid
   24 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpi_notify
   25 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug
   26 root      20   0     0    0    0 S    0  0.0   0:00.00 ata/0
   27 root      20   0     0    0    0 S    0  0.0   0:00.00 ata/1
   28 root      20   0     0    0    0 S    0  0.0   0:00.00 ata_aux
   29 root      20   0     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd
   30 root      20   0     0    0    0 S    0  0.0   0:00.00 khubd
   31 root      20   0     0    0    0 S    0  0.0   0:00.02 kseriod
   32 root      20   0     0    0    0 S    0  0.0   0:00.00 kmmcd
   35 root      20   0     0    0    0 S    0  0.0   0:00.00 khungtaskd
   36 root      20   0     0    0    0 S    0  0.0   0:00.00 kswapd0
   37 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd
   38 root      20   0     0    0    0 S    0  0.0   0:00.00 aio/0
   39 root      20   0     0    0    0 S    0  0.0   0:00.00 aio/1
   40 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea
   41 root      20   0     0    0    0 S    0  0.0   0:00.00 crypto/0
   42 root      20   0     0    0    0 S    0  0.0   0:00.00 crypto/1
   46 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_0
   48 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_1
   50 root      20   0     0    0    0 S    0  0.0   0:00.00 kstriped
   51 root      20   0     0    0    0 S    0  0.0   0:00.00 kmpathd/0
   52 root      20   0     0    0    0 S    0  0.0   0:00.00 kmpathd/1
   53 root      20   0     0    0    0 S    0  0.0   0:00.00 kmpath_handlerd
   54 root      20   0     0    0    0 S    0  0.0   0:00.00 ksnapd

---

### Post by cariboo on 2010-10-22
Are you trying to access the server via the external ip from inside your local network, or from another location?

---

### Post by reklaw on 2010-10-22
From outside, I'm actually using a dyndns name because I don't have a static IP address. The domain name is lwalker.dyndns.info. 

I tried using port 8080 to see if Comcast was blocking traffic on 80 but that didn't make a difference.

---

### Post by SeijiSensei on 2010-10-22
> The rest of the errors was just lines of this.
[Wed Oct 20 19:47:14 2010] [error] [client xx.xx.xx.xx] PHP Warning: dba_open(/var/lib/mediawiki/images/tmp/mw-cache-wikidb.db,cl): No such handler: db3 in /usr/sha$

Something in mediawiki wants to open a "Berkeley DB3" database, but your version of PHP doesn't have a db3 handler.  Neither does mine.  The "dba" module only supports DB4.  Attempts to find an Ubuntu PHP module for db3 have been in vain.

Did you install mediawiki from the Ubuntu repositories?  I don't see many people reporting this problem after a quick Google search for "php5 db3" or "mediawiki db3".

You truncated the line which points to the filename (some place under /usr/share/ it appears) and line number in that file which generated the PHP error  Find that line and see if you can figure out how to force mediawiki to use db4 instead.

---

### Post by reklaw on 2010-10-22
I installed mediawiki from the repositories using Aptitude. Wondering if I chose something incorrect in the configuration… will check that, thanks for the idea!

---

### Post by reklaw on 2010-10-25
reconfig of mediawiki seems to have cleared up the internal mediawiki issues but the external issues still exist. I'm beginning to think that the problem doesn't exist anywhere on the server and am going to try a different connection.

Perhaps a spare T1 at work will be put to use.

Thanks!

---

### Post by reklaw on 2010-10-25
Found the problem. MTU settings on the router or the cable modem look to be the culprit. When I lowered the MTU on the server it allows me to open everything. It still is slow but I think once I can get into the router and fix the MTU there it will fix the issue.

Any recommendation on optimal MTU size?

Thanks!

---

