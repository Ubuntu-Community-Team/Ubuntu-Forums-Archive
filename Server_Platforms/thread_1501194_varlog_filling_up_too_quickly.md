---
title: "/var/log filling up too quickly"
date: 2010-06-04
forum: Server Platforms
---

### Post by anuvnu387 on 2010-06-04
My /var/log is filling up too quickly. I increased by 1 GB in just 1-2 days. I am running Lucid. This never happened when I had Karmic. Below is the file list from /var/log. Note the lines in bold.

total 1.3G
drwxr-x--- 2 root      adm  4.0K 2010-05-30 06:50 apache2
drwxr-xr-x 2 root      root 4.0K 2010-03-30 13:59 apparmor
drwxr-xr-x 2 root      root 4.0K 2010-06-01 06:43 apt
-rw-r--r-- 1 root      root 6.8K 2010-06-02 18:55 aptitude
-rw-r----- 1 syslog    adm   13K 2010-06-03 22:29 auth.log
-rw-r----- 1 syslog    adm  195K 2010-06-03 06:39 auth.log.1
-rw-r----- 1 root      adm    31 2010-05-06 22:10 boot
-rw-r--r-- 1 root      root 1.3K 2010-06-02 21:46 boot.log
-rw-rw---- 1 root      utmp    0 2010-06-01 06:43 btmp
drwxr-xr-x 2 root      root 4.0K 2010-06-01 06:43 ConsoleKit
drwxr-xr-x 2 root      root 4.0K 2010-06-02 06:49 cups
-rw-r----- 1 syslog    adm   29K 2010-06-03 22:30 daemon.log
-rw-r----- 1 syslog    adm  360K 2010-06-02 22:27 daemon.log.1
drwxr-xr-x 2 root      root 4.0K 2010-05-09 15:48 dbconfig-common
-rw-r----- 1 syslog    adm   16K 2010-06-03 06:50 debug
-rw-r----- 1 syslog    adm   31K 2010-06-02 21:46 debug.1
drwxr-xr-x 2 root      root 4.0K 2010-04-23 20:29 dist-upgrade
-rw-r----- 1 root      adm   44K 2010-06-03 06:49 dmesg
-rw-r----- 1 root      adm   41K 2010-06-02 21:46 dmesg.0
-rw-r----- 1 root      adm   12K 2010-06-02 18:36 dmesg.1.gz
-rw-r----- 1 root      adm   12K 2010-06-02 17:13 dmesg.2.gz
-rw-r----- 1 root      adm   12K 2010-06-02 14:18 dmesg.3.gz
-rw-r--r-- 1 root      root  27K 2010-06-02 17:54 dpkg.log
-rw-r--r-- 1 root      root  24K 2010-05-09 19:35 faillog
drwxr-xr-x 2 root      root 4.0K 2010-05-06 22:10 fsck
drwxr-xr-x 3 root      root 4.0K 2010-05-06 22:47 installer
-rw-r--r-- 1 root      root    0 2010-06-02 18:27 kern
-rw-r----- 1 syslog    adm  263K 2010-06-03 22:31 kern.log
-rw-r----- 1 syslog    adm  957K 2010-06-03 06:47 kern.log.1
drwxr-xr-x 2 landscape root 4.0K 2010-05-06 22:48 landscape
-rw-rw-r-- 1 root      utmp 286K 2010-06-03 22:29 lastlog
-rw-r----- 1 syslog    adm     0 2010-05-06 22:47 lpr.log
**-rw-r----- 1 syslog    adm   97M 2010-06-03 22:30 mail.err**
[B]-rw-r----- 1 syslog    adm   69M 2010-06-03 06:48 mail.err.1
-rw-r----- 1 syslog    adm  179M 2010-06-03 22:30 mail.info
-rw-r----- 1 syslog    adm  126M 2010-06-03 06:48 mail.info.1
[/B]-rw-r--r-- 1 root      root    0 2010-06-02 18:18 maillog
[B]-rw-r----- 1 syslog    adm  179M 2010-06-03 22:30 mail.log
-rw-r----- 1 syslog    adm  126M 2010-06-03 06:48 mail.log.1
-rw-r----- 1 syslog    adm   97M 2010-06-03 22:30 mail.warn
-rw-r----- 1 syslog    adm   69M 2010-06-03 06:48 mail.warn.1
[/B]-rw-r----- 1 syslog    adm  246K 2010-06-03 22:31 messages
-rw-r----- 1 syslog    adm  281K 2010-06-03 06:49 messages.1
drwxr-s--- 2 mysql     adm  4.0K 2010-06-03 06:49 mysql
-rw-r----- 1 mysql     adm     0 2010-06-02 17:51 mysql.err
-rw-r----- 1 mysql     adm     0 2010-06-03 06:49 mysql.log
-rw-r----- 1 mysql     adm    20 2010-06-02 17:51 mysql.log.1.gz
drwxr-xr-x 2 root      root 4.0K 2010-05-06 22:47 news
-rw-r--r-- 1 root      root    0 2010-06-02 18:18 openwebmail.log
-rw-r--r-- 1 root      root    0 2010-05-06 22:13 pycentral.log
drwxr-xr-x 3 root      root 4.0K 2010-06-02 19:49 samba
-rw-r--r-- 1 root      root    0 2010-06-02 18:18 secure
[B]-rw-r----- 1 syslog    adm  179M 2010-06-03 22:31 syslog
-rw-r----- 1 syslog    adm  126M 2010-06-03 06:49 syslog.1
[/B]-rw-r--r-- 1 root      root 188K 2010-06-03 06:49 udev
-rw-r----- 1 syslog    adm  384K 2010-06-03 22:31 ufw.log
-rw-r----- 1 syslog    adm     0 2010-05-16 06:33 user.log
-rw-rw-r-- 1 root      utmp  54K 2010-06-03 22:29 wtmp

How do I reduce the amount of logs? This is just a personal small webserver. I rarely look at the logs. I am running logrotate but may be it is not configured correctly. Could anyone suggest ways to reduce logs or direct me to information regarding this. 

Thank you very much.

---

### Post by volkswagner on 2010-06-04
What are you running for your mail server?

How long has the system been running?  Seems odd that log and log.1 have same date stamp, unless it was only rotated once and that was Jun03.

You should have a look in syslog to see what all the entries are, may be a lot of duplicates.

I don't think rotation is working correctly, because I think you you should have log.0 before log.1.

---

### Post by HermanAB on 2010-06-04
If your system is running properly, then you could simply stop syslogd.

Otherwise, edit /etc/logrotate.conf

---

### Post by anuvnu387 on 2010-06-04
Thanks for the replies. I am a linux newbie. I started using Ubuntu server last December. So please excuse me if explain myself well.

I do not believe I am running a mail server (I did not install it while install Ubuntu Server).

The system has been running only for less than 2 days.

If you think that the log names are messed up I would like to say that, last week within 5-6 days my logs reached 6.5 GB. So I deleted all the .gz files. And did #>logfilename for all logs that were big which reset the log files. 

My system is running well. I would not mind stop logging. But I am unable to find anything with the name "syslogd". However I am able to find /usr/sbin/rsyslogd.

Here is my /etc/rsyslog.d/50-default.conf:

#  Default rules for rsyslog.
#
#			For more information see rsyslog.conf(5) and /etc/rsyslog.conf

#
# First some standard log files.  Log by facility.
#
auth,authpriv.*			/var/log/auth.log
*.*;auth,authpriv.none		-/var/log/syslog
#cron.*				/var/log/cron.log
daemon.*			-/var/log/daemon.log
kern.*				-/var/log/kern.log
lpr.*				-/var/log/lpr.log
mail.*				-/var/log/mail.log
user.*				-/var/log/user.log

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
mail.info			-/var/log/mail.info
mail.warn			-/var/log/mail.warn
mail.err			/var/log/mail.err

#
# Logging for INN news system.
#
news.crit			/var/log/news/news.crit
news.err			/var/log/news/news.err
news.notice			-/var/log/news/news.notice

#
# Some "catch-all" log files.
#
*.=debug;\
	auth,authpriv.none;\
	news.none;mail.none	-/var/log/debug
*.=info;*.=notice;*.=warn;\
	auth,authpriv.none;\
	cron,daemon.none;\
	mail,news.none		-/var/log/messages

#
# Emergencies are sent to everybody logged in.
#
*.emerg				*

#
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
#daemon,mail.*;\
#	news.=crit;news.=err;news.=notice;\
#	*.=debug;*.=info;\
#	*.=notice;*.=warn	/dev/tty8

# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
# 
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
	news.err;\
	*.=debug;*.=info;\
	*.=notice;*.=warn	|/dev/xconsole


I read up on logrotate and made some changes. But still the logs increase. I reset all logs yesterday night. The size of /var/log is already 600 MB.

Any help will be greatly appreciated.

---

### Post by volkswagner on 2010-06-09
If you post a portion of the syslog, we may be offer more help.

the less command works great for navigating logs.  If you ssh into the server it is easy to copy and past a portion.

```
less /var/log/syslog
```

You can use page up/down or arrow up/down.  You can easily search for contents.

```
man less
```

---

### Post by anuvnu387 on 2010-06-09
volkswagner!!! you the man. I think I found the problem. I did:

less /var/log/syslog (and all other logs that were huge). 

I found this in common in all the logs (thousands of lines):
-----------
Jun  9 06:53:36 xyzgroup nullmailer[1185]: Starting delivery: protocol: smtp host: smtp.outgoingserver.net file: 1275307981.28977
Jun  9 06:53:36 xyzgroup nullmailer[23981]: smtp: Failed: Connect failed
Jun  9 06:53:36 xyzgroup nullmailer[1185]: Sending failed:  Host not found
--------------
I fixed the outgoing mail server. I am pretty sure that this should solve my log filling up problem. After making sure that my problem is solved I will mark this thread solved.

Thank you!!!

UPDATE (6/10/2010): The problem is now solved. My logs do not grow excessively anymore. Thanks for all your suggestions.

---

