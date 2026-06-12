---
title: "Oinkmaster running Snort with snort and bleeding rules"
date: 2008-08-27
forum: Security
---

### Post by obitori on 2008-08-27
I'm building Snort to run on my Dell D630 running Ubuntu 8.04 Hardy.  

I used apt-get to install the necessary servers and scripts:

```

sudo apt-get install snort-mysql mysql-server oinkmaster

```

The installation automatically prompts you for a mysql root password.  I will skip this part of the process, but assume that you have mysql server 5.0 up and running.  

You need to set up snort to talk to mysql.  Do the following:

```

cd /usr/share/doc/snort-mysql
less README-database.Debian

```

The Debian README tells you how to get mysql running with the .deb version of Snort.  (It'd prolly work with a source install as well.)  Below are the relevant steps:

```

$ mysql -u root -p
CREATE DATABASE snort
grant CREATE, INSERT, SELECT, UPDATE on snort.* to snort@localhost;
grant CREATE, INSERT, SELECT, UPDATE on snort.* to snort;
SET PASSWORD FOR snort@localhost=PASSWORD('YOUR_PASSWORD_HERE');
flush privileges;
show grants for 'snort'@'localhost';

```

The last command shows that the snort user has the necessary access privileges to the snort tables.  Now, the directory that you are in has a file, create_

```

 $ zcat create_mysql.gz | mysql -u root -h localhost -p snort

```

The -h switch is not needed for a localhost installation, but that's how it appears in the directions.  "snort" is not the switch for -p.  -P tells mysql to prompt for a password.  The word "snort" is the name of the database (created above) to use when executing the commands in the file create_mysql.gz.  Note that the .gz extension means the file is gzipped.  The above command unzips the file and pushes the decompressed contents to mysql for processing.  You will often see a similar command:

```

mysql -u root -p < filename.sql

```

The latter works for a normal ascii file, but in this case, would not because the file is compressed and mysql would interpret the compressed contents as gibberish.  The zcat command transforms the compressed file into decompressed text and | pipes that text to mysql.   Unix gurus often link their commands with pipes in such ways.  

Once you have completed this:

```

 $ zcat create_mysql.gz | mysql -u root -h localhost -p snort

```

I did not use the default password for the snort user on mysql, so after setting up the tables, I ran:

```

dpkg-reconfigure snort-mysql
boot
eth0
any
no <--Don't disable promiscuous mode
yes <--alter ordering to pass|alert|log
[blank] <--No custom options
yes <--email summaries to me
email@example.com <--address to email summaries to
1 <--minimum number of alerts to trigger summary *may need to fine tune*
yes <--set up database for snort-mysql to log to
localhost <--database server hostname
snort <--database (inside of mysql) to use
snort <--name of mysql user that will access database to log snort alerts
YOUR_PASSWORD_HERE <--Enter the same password that you used when you created the snort database above.  This will allow snort to log onto mysql and log its alerts.

```

Snort is ready to be run for the first time, but if you type:

```

sudo /etc/init.d/snort start

```

You'll get an error telling you to remove the file, /etc/snort/db-pending-configuration.  You've configured the database, so go ahead and type:

```

sudo rm /etc/snort/db-pending-configuration

```

Now, you can start the server.

```

root@moosilauk:/etc/snort# sudo /etc/init.d/snort start
 * Starting Network Intrusion Detection System  snort                    [ OK ] 
root@moosilauk:/etc/snort# 

```

We are not done yet.  You still haven't imported the rules sets (updated daily to reflect new viruses and the like).  There are two main sources of snort rules:  [www.snort.org](www.snort.org) and [www.bleedingthreats.net](www.bleedingthreats.net).

The original authors of snort run [www.snort.org](www.snort.org).  They need to make a living, so they sell their rules to subscribers.  It's worth the money for a network administrator to pay for their rules to protect a company website or the like, but for my laptop?  Nah.  

As is often the case when an open source author decides to cash in on the author's product, some were indignant when snort.org started selling its rules.  So, a bunch of users started bleedingthreats.net, originally bleedingsnort.com, and came up with their own rules.  Those rules are always free, but they site appears to have fallen into disuse, so I am not sure how fresh the rules are anymore.

So, I'll download both sets and combine them.  First, I'll grab the free version of snort.org.  It's a little stale, but so what.

[http://www.snort.org ]("http://www.snort.org")

and create a user account.  Then, you will need to go to the configuration page and get the URL for the rules.  You do this by logging in under the name that you registered with snort and going to the account settings page:

[https://www.snort.org/reg-bin/userprefs.cgi]("https://www.snort.org/reg-bin/userprefs.cgi")

At the bottom, you'll see the oinkmaster download codes.  You need to do the following:

1.  Copy the rules URL and paste it into the /etc/oinkmaster.conf file:

```

sudo vi /etc/oinkmaster.conf

```

Here is how the modified "oinkmaster.conf" should look:

```

# -------------------------
# Location of rules archive
# -------------------------
# NOTE: this might need to be changed based on the Snort version
# you are running. This configuration files uses Snort 2.2.x
# url = http://www.snort.org/dl/rules/snortrules-snapshot-2_2.tar.gz
# NOTE: I commented out above line and pasted in below:
url = http://www.snort.org/pub-bin/oinkmaster.cgi/5a08f649c16a278e1012e1c84bdc8fab9a70e2a4/snortrules-snapshot-2.3.tar.gz

```

2.  Unfortunately, the line of gibberish, "5a08f649c16a278e1012e1c84bdc8fab9a70e2a4", must be replaced with an activation code for your snort user account.  To get your own line of gibberish, you must click on the "get code" button in the oink code box at the bottom of your account settings page.  Take that number and replace the above gibberish with your oink code:

```

# -------------------------
# Location of rules archive
# -------------------------
# NOTE: this might need to be changed based on the Snort version
# you are running. This configuration files uses Snort 2.2.x
# url = http://www.snort.org/dl/rules/snortrules-snapshot-2_2.tar.gz
# NOTE: I commented out above line and pasted in below:
url = http://www.snort.org/pub-bin/oinkmaster.cgi/xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx/snortrules-snapshot-2.3.tar.gz

```

Now, if you type:

```

oinkmaster -o /etc/snort/rules

```

Oinkmaster should download the most recent free snort rules from snort.org and store them in /etc/snort/rules.  It automatically restarts snort, so that snort runs with the new rules in place.

Next, I want to add in the rules from bleedingthreats.net.  To do that, I modified a script that I found here:

[http://global-security.blogspot.com/2007/09/bleeding-snort-and-regular-rules-with.html]("http://global-security.blogspot.com/2007/09/bleeding-snort-and-regular-rules-with.html")

I saved my modified script in /usr/local/sbin/ and named it auto-oink.sh.  Here is the file:

```
#! /bin/sh
# auto-oink.sh modified by Bud from JJC's post at
# http://global-security.blogspot.com/2007/09/bleeding-snort-and-regular-rules-with.html 
#
# simple script to run oinkmaster and obtain bleeding threat updates
# in addition to the regular snort.org updates
#
/usr/sbin/oinkmaster -o /etc/snort/rules/
/usr/sbin/oinkmaster -C /etc/oinkmaster-bleeding.conf -o /etc/snort/rules/
/bin/cat /etc/snort/rules/bleeding-sid-msg.map >> /etc/snort/rules/sid-msg.map
/etc/init.d/snort stop
/etc/init.d/snort start
d=`date +%y%m%d%H%M%S`
echo "[$d] Snort rules updated from snort.org and bleedingthreats.net." >> /var/log/auto-oink.log

```

Now, to be safe, type:

```

sudo touch /var/log/auto-oink.log

```

That creates the log file that the auto-oink.sh script uses to record its successful operation.  (Successful, here, meaning only that it went from beginning to end without an error halting execution.)  

Now, we can add the auto-oink.sh file to cron to execute once a day.  Below is the crontab after I added the root entry for auto-oink.sh:

```

sudo crontab -e

# m h  dom mon dow   command
5 11 * * * 	/usr/local/sbin/auto-oink.sh


```

That should be it for getting snort up and running.  This is a working draft.  Comments, additions, criticisms would be appreciated.  I want to do a second mini-FAQ on viewing/understanding the results.  MTF...

Obitori

---

