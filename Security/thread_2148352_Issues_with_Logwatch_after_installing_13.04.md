---
title: "Issues with Logwatch after installing 13.04"
date: 2013-05-24
forum: Security
---

### Post by Scrumps on 2013-05-24
I installed logwatch recently in hopes to monitor samba, bind, isc-dhcp-server, etc. Unfortunately logwatch doesn't appear to be doing that. Whenever I run:
sudo logwatch I get the following e-mail:
[IMG]http://i.imgur.com/AbLdgrQl.pngp[/IMG]

But that is all I get. 

I ran a debug output to file unfortunately it is VERY large:
[http://paste.ubuntu.com/5698843/](http://paste.ubuntu.com/5698843/)

I am not sure how to fix this. :(

---

### Post by unspawn on 2013-05-25
Thanks for providing debug output. If you run Logwatch with the ```
--detail 10 --debug 10 --numeric --filename /tmp/logwatch.log
``` args and then grep your output ```
egrep -ie "(samba|logfile.*samba)" /tmp/logwatch.log
``` then around line 21 you see the service is enabled and on line 22 which log file it will search for. Right after line 24 you should then get the file names listed that expands to, showing "Logfile = /var/log/samba/*" lines, after which you should get a line reading "Preprocessing LogFile: samba" and then one reading "DEBUG: Inside ApplyDate (samba)...". Since you don't have those lines you may want to check 0) if there's any log files at all and 2) if they're in the location Logwatch expects them.

---

### Post by Scrumps on 2013-05-25
Hey, I do have log files for samba at /var/log/samba/ (though it is empty right now as I haven't edited the config for samba yet)
oot@server:~# ls -l /var/log/samba/
total 1236
drwx------ 4 root root    4096 May 25 15:58 cores
-rw-r--r-- 1 root root       0 May 25 15:58 log.10.10.10.252
-rw-r--r-- 1 root root  148755 May 25 21:26 log.dataslum
-rw-r--r-- 1 root root 1025819 May 25 20:44 log.dataslum.old
-rw-r--r-- 1 root root   61775 May 25 21:23 log.nmbd
-rw-r--r-- 1 root root    1094 May 25 16:08 log.smbd


Same goes for Apache, bind9, isc-dhcp-server:
root@server:~# ls -la /var/log/
total 2808
drwxr-xr-x 16 root      root       4096 May 25 19:39 .
drwxr-xr-x 17 root      root       4096 May 25 21:00 ..
-rw-r--r--  1 root      root      52779 May 25 21:08 alternatives.log
drwxr-x---  2 root      adm        4096 May 25 21:10 apache2
drwxr-xr-x  2 root      root       4096 May 25 15:01 apt
-rw-r-----  1 syslog    adm       62143 May 25 21:25 auth.log
-rw-r-----  1 root      adm          31 Apr 23 11:56 boot
-rw-r--r--  1 root      root       1354 May 25 16:08 boot.log
-rw-r--r--  1 root      root      51399 Apr 23 11:57 bootstrap.log
-rw-rw----  1 root      utmp          0 Apr 23 11:56 btmp
drwxr-xr-x  2 clamav    clamav     4096 May 25 17:18 clamav
drwxr-xr-x  2 root      root       4096 May 25 15:24 ConsoleKit
drwxr-xr-x  2 root      root       4096 Apr 19 11:58 dist-upgrade
-rw-r-----  1 root      adm       71333 May 25 16:08 dmesg
-rw-r-----  1 root      adm       71188 May 25 15:28 dmesg.0
-rw-r-----  1 root      adm       17839 May 25 15:24 dmesg.1.gz
-rw-r-----  1 root      adm          59 Apr 23 11:56 dmesg.2.gz
-rw-r--r--  1 root      root     761524 May 25 21:14 dpkg.log
-rw-r--r--  1 root      root      32096 May 25 20:41 faillog
-rw-r--r--  1 root      root        941 May 25 20:41 fontconfig.log
drwxr-xr-x  2 root      root       4096 May 25 15:00 fsck
drwxr-xr-x  3 root      root       4096 May 25 15:21 installer
-rw-r--r--  1 root      root       3422 May 25 16:43 kdm.log
-rw-r-----  1 syslog    adm      315866 May 25 19:39 kern.log
drwxr-xr-x  2 landscape root       4096 May 25 15:24 landscape
-rw-rw-r--  1 root      utmp     292876 May 25 20:41 lastlog
drwxr-xr-x  2 root      root       4096 Apr 24 03:36 lightdm
-rw-r-----  1 syslog    adm         108 May 25 17:18 mail.err
-rw-r-----  1 syslog    adm         944 May 25 21:25 mail.log
-rw-r--r--  1 minidlna  minidlna   1300 May 25 19:24 minidlna.log
drwxr-xr-x  2 root      root       4096 May 25 15:24 news
-rw-r--r--  1 root      root      25794 May 25 16:38 openvpnas.log
-rw-r--r--  1 root      root       2065 May 25 16:13 pm-powersave.log
drwxrwxr-t  2 root      postgres   4096 May 25 19:39 postgresql
drwxr-x---  3 root      adm        4096 May 25 20:45 samba
-rw-r-----  1 syslog    adm      809834 May 25 21:28 syslog
-rw-r--r--  1 root      root     388951 May 25 16:08 udev
-rw-r-----  1 syslog    adm           0 May 25 15:24 ufw.log
drwxr-xr-x  2 root      root       4096 May 25 15:27 unattended-upgrades
drwxr-xr-x  2 root      root       4096 May 25 16:38 upstart
-rw-rw-r--  1 root      utmp      19584 May 25 19:34 wtmp
-rw-r--r--  1 root      root      33780 May 25 16:43 Xorg.0.log


Which is why I am confused. I would think that it would catch all the logs up until the point when the logwatch command is run, is that true? Or does it need to wait a day before it actually sends the logs out?

---

### Post by unspawn on 2013-05-26
Look at your email screen shot, the "Data Range Processed" value then adjust your logwatch.conf / command line "--range" setting?

---

### Post by Scrumps on 2013-05-26
Yeah, I woke up and got a much larger list. Unfortunately, bind9 and isc-dhcp-server were not a part of those which are two of the things I really did want sent to me. :/

---

### Post by unspawn on 2013-05-26
> **Scrumps said:**
> Yeah, I woke up and got a much larger list. 
No, I mean you can adjust what Logwatch reports using that switch like "--range Today".


> **Scrumps said:**
> Unfortunately, bind9 and isc-dhcp-server were not a part of those which are two of the things I really did want sent to me. :/
0. The daemon may be configured to:
- emit no messages. 
- emit messages at a lower facility / priority combo than syslog accepts.
1. Logrotate may have rotated the log file just before Logwatch is run.
2. Logwatch may be: 
- running with not enough "--detail" to filter these messages.
- configured to look at the right log file but it may be empty.
- looking at the wrong log file.
- failing to correctly filter messages.

I've explained how you can trace your debug output for a certain service and without providing relevant details there isn't anything specific I will be able to help you with. In closing you can debug Logwatch by running it over one specific log file or for one specific service (ISC BIND here) any time by running it like ```
logwatch --numeric --range Today --debug 10 --detail 10 --filename /tmp/logwatch.report --service named 2>&1 | tee /tmp/logwatch.tee
``` after which you can inspect ```
less /tmp/logwatch.report /tmp/logwatch.tee
```

HTH

---

### Post by Scrumps on 2013-05-27
So when I do those commands, I eventually get the following:
andrew@server:~$ less /tmp/logwatch.report /tmp/logwatch.tee
/tmp/logwatch.report: No such file or directory
andrew@server:~$ 


My detail in my config file is set to 10, and I see named/bind and isc-dhcp-server running logs to /var/log/syslog

Unfortunately, this is because all of them are looking for /var/log/messages which doesn't exist anymore because of a tweak in Ubuntu. I don't know where it is telling it to look in messages though, because I can't find the config files that would indicate that it is messages versus syslog.


I found this, and edited it to syslog rather than messages:

  GNU nano 2.2.6                                                    File: /usr/share/logwatch/default.conf/services/named.conf                                                                                                               


###########################################################################
# $Id: named.conf,v 1.10 2005/02/24 17:05:20 kirk Exp $
###########################################################################


# You can put comments anywhere you want to.  They are effective for the
# rest of the line.


# this is in the format of <name> = <value>.  Whitespace at the beginning
# and end of the lines is removed.  Whitespace before and after the = sign
# is removed.  Everything is case *insensitive*.


# Yes = True  = On  = 1
# No  = False = Off = 0


Title = "Named"


# Which logfile group...
LogFile = syslog


# Whether or not to lookup the IPs into hostnames...
# Setting this to Yes will significantly increase runtime
$named_ip_lookup = No


# Only give lines pertaining to the named service...
*OnlyService = named
*RemoveHeaders


########################################################
# This was written and is maintained by:
#    Kirk Bauer <kirk@kaybee.org>
#
# Please send all comments, suggestions, bug reports,
#    etc, to [email]kirk@kaybee.org[/email].
########################################################


# vi: shiftwidth=3 tabstop=3 et


I wish messages still existed, this would solve a bunch of problems and be less annoying. Unfortunately, I am still not getting named/bind9 to show up in logwatch. I was able to get dhcpd to show up however.

---

### Post by unspawn on 2013-05-29
> **Scrumps said:**
> So when I do those commands, I eventually get the following:
```
andrew@server:~$ less /tmp/logwatch.report /tmp/logwatch.tee
/tmp/logwatch.report: No such file or directory
```
I have no idea what command line you ran.


> **Scrumps said:**
> Unfortunately, this is because all of them are looking for /var/log/messages which doesn't exist anymore because of a tweak in Ubuntu. I don't know where it is telling it to look in messages though, because I can't find the config files that would indicate that it is messages versus syslog.
LogFile = setting in /usr/share/logwatch/default.conf/logwatch.conf?

*If that doesn't work (debug output) there may be a need to check hardcoded values and replace them:```
tar -cf /tmp/backup.tar $(grep /usr/share/logwatch/default.conf/services/*.conf -e "^LogFile = messages"|cut -d ':' -f 1)
sed -i "s|^LogFile = messages|LogFile = syslog|g" /usr/share/logwatch/default.conf/services/*.conf
```after which you definitely should file a bug report.

---

