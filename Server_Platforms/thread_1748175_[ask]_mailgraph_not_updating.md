---
title: "[ask] mailgraph not updating"
date: 2011-05-03
forum: Server Platforms
---

### Post by venol on 2011-05-03
I just installed mailgraph on a Linux Ubuntu 10.04 box monitoring Postifix.
Everything seems to be working fine, but the graphs are not always
updating.  When I refresh the web page or close the browser and come back
later, the graph updates and moves to the left, showing new time, the the
data line is not drawn.  Sometimes it does not update for several hours.  I
had started, stopped and restarted mailgraph-init and that doesn't seem to
make a difference.

Any ideas?

---

### Post by venol on 2011-05-04
helo, somebody can help me please.
:(

---

### Post by thesphynx on 2011-05-10
I am having the same problem after upgrading from 10.10 to 11.04.  Ever since then my mailgraph rrds show nothing.  My /var/log/mail.log file has lots of messages entries in it that get updated all of the time.  Not sure what changed.  Any help would be great.

---

### Post by venol on 2011-05-16
[COLOR=#000000][FONT=Times New Roman][COLOR=#222222][FONT=verdana]No graph appear in the graphic created by mailgraph.
I know mailgraph consist of perl and cgi script.
If I have postfix log, how to test mailgraph manually to create the graphic using its perl script from existing postfix log. Just to see whether the graph created or not in the graphic[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by thesphynx on 2011-05-17
Check that www-data is listed in the /etc/default/mailgraph config file as the owner of the web server process.  Change it according to your environment.
Once you have done that chown -R www-data:www-data /var/lib/mailgraph
Then restart the /etc/init.d/mailgraph service.
Once I did this stuff I actually got feedback from the statup script as well as updated graphs.

---

### Post by venol on 2011-05-19
thanks for the reply. The owner /var/lib/mailgraph have change to the user www-data. But, my /etc/default/mailgraph file contains justlike this.


root@venom:/var/www# cat /etc/default/mailgraph 
BOOT_START=
MAIL_LOG=/var/log/mail.log
IGNORE_LOCALHOST=false

nothing parameter indication about user www-data. Where your tutorial installation mailgraph? maybe I can use too.

---

### Post by thesphynx on 2011-05-19
Here is my /etc/default/mailgraph on my 11.04 installation:
 
# This file is sourced by /etc/init.d/mailgraph
#
# This is a POSIX shell fragment
#
# Should Mailgraph start on boot (true|false) (default: true)
BOOT_START="true"
# Logfile used by mailgraph (default: /var/log/mail.log)
MAIL_LOG="/var/log/mail.log"
# Ignore mails from localhost (true|false) (default: false)
# When true, this will pass --ignore-localhost to mailgraph daemon
IGNORE_LOCALHOST="false"
# Extra options to be passed to mailgraph daemon
# See mailgraph -h output (default: "")
EXTRA_OPTIONS=""
# User and group http daemon runs as (default: www-data for both options)
# Restart mailgraph daemon so that these values are taken into account
HTTP_USER="www-data"
HTTP_GROUP="www-data"
 
I don't recall that I had a tutorial. I think I used this when troubleshooting and it allowed me to better understand exactly what mailgraph was doing. I was also trying to troubleshoot a Cacti mailgraph template issue and once I realized all of the files/directories it involved I just checked permissions on them and changed them to what I thought made a little since.
 
[http://www.linuxplayer.org/2010/12/monitoring-email-server-with-cacti/](http://www.linuxplayer.org/2010/12/monitoring-email-server-with-cacti/)

---

### Post by venol on 2011-07-21
mailgraph updating rrd databases. but the problem is mailgraph not display it. I know it by running the command -v at mailgraph run. so, how to display the graph immediately after the rrd was updated ?

---

