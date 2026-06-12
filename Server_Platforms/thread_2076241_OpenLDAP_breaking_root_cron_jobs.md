---
title: "OpenLDAP breaking root cron jobs"
date: 2012-10-25
forum: Server Platforms
---

### Post by sulobanks on 2012-10-25
I have a fairly standard LAMP setup on 12.04, load balanced over 4 servers.  I had been using a cron job to rsync files periodically from my "main" server to the other 3.  This worked fine until I decided to authenticate against an openldap server (also running 12.04).  Suddenly, all cron jobs for root stopped working.  Normal user cron jobs do work.  I have several more ubuntu servers on the network that I want to switch to ldap for authentication, but I need to fix my cron problem first.

Here is what I have done:
I followed the guide [here]("https://help.ubuntu.com/10.04/serverguide/openldap-server.html") without replication and without kerberos to install my ldap server.
I also followed that guide to set up the web servers to authenticate against the ldap server.  This all worked correctly.

The cron job in question runs as root in a file called sync in /etc/cron.d.  It worked flawlessly before the switch to ldap.
It's a simple rsync -a root@webserver1:/var/www/ /var/www/
The root account is enabled on webserver1.
After the switch, I found this line in /var/log/syslog as often as cron is supposed to run:

CRON[<some number>]: Permission denied

And the files are no longer being synced.
I redirected the output of my script to a separate log file, but nothing ever showed up.  I can run the command in /etc/cron.d/sync manually as root and it runs as expected.

As a test, I changed root's crontab to contain only the following:
* * * * * touch /var/www/file.txt

This also produced permission denied in the syslog and never created file.txt.  Does anyone know of anything about openldap that would deny permissions on root cron jobs?

I would really like to keep running the sync as root, since there are multiple users that connect to work on this web site and preserving permissions is important.

Thanks

---

### Post by sulobanks on 2012-10-25
I figured it out.  Only took me all day.  As usual, it was something stupid that I did.  In case this ever helps someone, I had messed with /etc/security/access.conf on all the servers but the main one to prevent users logging into them and uploading files (since that would have messed with my syncing.  What I didn't have in there was any provision whatsoever for root.  So adding this toward the end of the file:

+ : root : LOCAL

fixed my problem.

---

