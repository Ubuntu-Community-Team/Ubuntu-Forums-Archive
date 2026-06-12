---
title: "How can I lower sendmail DNS lookup timeout/delay?"
date: 2008-07-22
forum: Server Platforms
---

### Post by BlackDex on 2008-07-22
Hello there,

I have a problem with sendmail.
when i enter "RCPT TO: [email]foo@bar.com[/email]"
And bar.com is very slow or non responsive with returning MX records or what ever, sendmail keeps waiting for about 60sec and then comes with the message "250 2.1.5 [email]foo@bar.com[/email]... Recipient ok (will queue)"
While if it is a @hotmail adres or something it response directly and without the "will queue" message.

Is there a way to configure sendmail to lower the timeout? Or do somthing else so this gets ignored or something?

Thx.

---

### Post by windependence on 2008-07-22
Install postfix. I'm not being funny or sarcastic here. Sendmail is IMHO old, buggy, and insecure, and REALLY a bear to configure. The config files are cryptic. 

Postfix is a drop in replacement for sendmail. If you are going to install it, do not uninstall sendmail, just install postfix (sudo apt-get install postfix) and configure it and you will be happy.

-Tim

---

### Post by BlackDex on 2008-07-24
Well i did that, but now i get the following error message.
And i searched the net about this problem, but didn't find a soluttion.
How can i fix this?

```

Running newaliases
postalias: fatal: open database /etc/aliases.db: Permission denied
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1

```

---

### Post by MJN on 2008-07-24
Run whatever command you did using sudo (i.e. **sudo <command>**) as this will given the command sufficient permissions to do its work.
 
Mathew

---

### Post by BlackDex on 2008-07-24
i did this, and i still get the same error message.

```
sudo newaliases 
postalias: fatal: open database /etc/aliases.db: Permission denied
```

ls /etc/aliases*
```
ls -al /etc/aliases*
-rw-r--r--+ 1 root root 51 2008-07-24 11:59 /etc/aliases
```

btw: i even did a sudo su and executed the command, no luck.
And i changed the permissions to rw-rw-rw- also no luck.

---

### Post by MJN on 2008-07-24
Hmm... strange! What's most odd is that you don't even have a /etc/aliases.db file - can you double-check and, if you do, delete it and retry?
 
Other than that I'm afraid I'm at a loss... I've not seen this situation before myself (hence why I'm taking the errors at face value).
 
Mathew
 
Edit: Just spotted the + at the end of your file permissions - I believe this relates to ACLs but I I don't use them I'm still none the wiser as to what your problem is, but it stands to reason that it could well be the culprit (the man page for setfacl suggests that **setfacl -b /etc/aliases** will at least remove the ACL entries so you could try that as a starter for ten).

---

### Post by BlackDex on 2008-07-24
Well i found that if i do a "sudo postalias /etc/aliases" it will create the aliases.db, but then after the newaliases it still gives the same error message.

Also when i run apt-get again it tells that there is one package not fully installed, which is postfix, and this also gives the same error.

```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up postfix (2.5.1-2ubuntu1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
postalias: fatal: open database /etc/aliases.db: Permission denied
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by MJN on 2008-07-24
I added an* Edit:* whilst you were probably typing, have a go with removing the ACL as mentioned.
 
Mathew

---

### Post by BlackDex on 2008-07-24
Hmm.. I don't know why those acl's are there.
And i can't remove it :(.

---

### Post by figure002 on 2010-07-22
I had the same problem as BlackDex with the very long delay very time an email was sent with sendmail. So I decided to install postfix as well. I posted to installation log below, and as you can see, in contrast to BlackDex's install, my install was successful.

Glady, the long timeout has disappeared when and email is sent via my PHP application. Sadly however, the emails never arrive now, which did when I was using sendmail. Anyone knows what's going on? Does it have anything to do with the mailname I set (saibot.no-ip.info)?

EDIT: I think I found the problem. The Postfix server fails to start. You can tell, because the 'reload' command fails:
```
serrano@saibot:~$ sudo /etc/init.d/postfix restart
 * Stopping Postfix Mail Transport Agent postfix              [ OK ] 
 * Starting Postfix Mail Transport Agent postfix                [ OK ] 
serrano@saibot:~$ sudo /etc/init.d/postfix reload
 * Reloading Postfix configuration...           postfix/postfix-script: fatal: the Postfix mail system is not running
                             [fail]

```Installation log:
```
serrano@saibot:~$ sudo apt-get install postfix
[sudo] password for serrano: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  sendmail-base procmail sensible-mda sendmail-cf libdb4.7 python-pygments
Use 'apt-get autoremove' to remove them.
Suggested packages:
  postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin resolvconf postfix-cdb
The following packages will be REMOVED:
  sendmail sendmail-bin
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 2 to remove and 0 not upgraded.
Need to get 1,321kB of archives.
After this operation, 1,090kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://nl.archive.ubuntu.com/ubuntu/ lucid/main postfix 2.7.0-1 [1,321kB]
Fetched 1,321kB in 1s (663kB/s)    
Preconfiguring packages ...
(Reading database ... 301262 files and directories currently installed.)
Removing sendmail ...
dpkg: sendmail-bin: dependency problems, but removing anyway as you requested:
 sensible-mda depends on sendmail-bin | mail-transport-agent; however:
  Package sendmail-bin is to be removed.
  Package mail-transport-agent is not installed.
  Package sendmail-bin which provides mail-transport-agent is to be removed.
 sensible-mda depends on sendmail-bin | mail-transport-agent; however:
  Package sendmail-bin is to be removed.
  Package mail-transport-agent is not installed.
  Package sendmail-bin which provides mail-transport-agent is to be removed.
Removing sendmail-bin ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Selecting previously deselected package postfix.
(Reading database ... 301209 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.7.0-1_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Processing triggers for man-db ...
Setting up postfix (2.7.0-1) ...
Adding group `postfix' (GID 131) ...
Done.
Adding system user `postfix' (UID 122) ...
Adding new user `postfix' (UID 122) with group `postfix' ...
Not creating home directory `/var/spool/postfix'.
Creating /etc/postfix/dynamicmaps.cf
Adding tcp map entry to /etc/postfix/dynamicmaps.cf
Adding group `postdrop' (GID 132) ...
Done.
setting myhostname: saibot
setting alias maps
setting alias database
changing /etc/mailname to saibot.no-ip.info
setting myorigin
setting destinations: saibot.no-ip.info, saibot, localhost.localdomain, localhost
setting relayhost: 
setting mynetworks: 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
setting mailbox_command
setting mailbox_size_limit: 0
setting recipient_delimiter: +
setting inet_interfaces: all
WARNING: /etc/aliases exists, but does not have a root alias.

Postfix is now set up with a default configuration.  If you need to make 
changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Stopping Postfix Mail Transport Agent postfix            [ OK ] 
 * Starting Postfix Mail Transport Agent postfix            [ OK ] 

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by MJN on 2010-07-22
Post the mail log (/var/log/mail.log) as it may shed some light on what is wrong.
 
Mathew

---

### Post by figure002 on 2010-07-22
Here's today's log. I'm not sure what part belongs to postfix or sendmail though..

```
Jul 22 00:00:01 saibot sm-msp-queue[2475]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 00:01:01 saibot sm-msp-queue[2475]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 00:20:01 saibot sm-msp-queue[2883]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 00:21:01 saibot sm-msp-queue[2883]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 00:40:02 saibot sm-msp-queue[3280]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 00:41:02 saibot sm-msp-queue[3280]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 01:00:01 saibot sm-msp-queue[3785]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 01:01:02 saibot sm-msp-queue[3785]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 01:20:01 saibot sm-msp-queue[4583]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 01:21:01 saibot sm-msp-queue[4583]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 01:34:09 saibot sm-mta[4975]: o6LNY9k9004975: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 01:34:30 saibot sm-mta[4982]: o6LNYUUW004982: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 01:34:30 saibot sendmail[4984]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 01:35:30 saibot sendmail[4984]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 01:35:30 saibot sendmail[4984]: o6LNZUXC004984: from=www-data, size=1229, class=0, nrcpts=0, msgid=<201007212335.o6LNZUXC004984@saibot>, relay=www-data@localhost
Jul 22 01:35:31 saibot sm-mta[4986]: o6LNZVAG004986: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 01:35:45 saibot sm-mta[4993]: o6LNZjUr004993: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 01:40:01 saibot sm-msp-queue[5149]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 01:41:01 saibot sm-msp-queue[5149]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 01:42:53 saibot sm-mta[5231]: o6LNgrwF005231: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 01:43:57 saibot sm-mta[5250]: o6LNhvvi005250: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 01:44:05 saibot sm-mta[5255]: o6LNi5MJ005255: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 01:44:51 saibot sm-mta[5262]: o6LNiphm005262: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 01:44:52 saibot sm-mta[5265]: o6LNiqZO005265: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 01:45:17 saibot sm-mta[5268]: o6LNjHZ3005268: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 01:45:32 saibot sm-mta[5275]: o6LNjWQZ005275: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 01:57:10 saibot sm-mta[5402]: o6LNvA4t005402: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 01:58:31 saibot sm-mta[5421]: o6LNwVk3005421: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 01:58:31 saibot sm-mta[5423]: o6LNwVVQ005423: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 01:58:53 saibot sm-mta[5429]: o6LNwrxx005429: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 01:58:53 saibot sm-mta[5430]: o6LNwrv8005430: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 02:00:01 saibot sm-msp-queue[5473]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 02:00:04 saibot sm-mta[5514]: o6M004ED005514: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 02:00:14 saibot sm-mta[5517]: o6M00Ev7005517: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 02:01:01 saibot sm-msp-queue[5473]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 02:10:45 saibot sm-mta[5655]: o6M0AjLx005655: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 02:20:02 saibot sm-msp-queue[5837]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 02:21:02 saibot sm-msp-queue[5837]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 02:40:01 saibot sm-msp-queue[6082]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 02:41:01 saibot sm-msp-queue[6082]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 02:42:07 saibot sm-mta[6145]: o6M0g72x006145: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 02:49:17 saibot sm-mta[6203]: o6M0nHwt006203: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 02:49:20 saibot sm-mta[6207]: o6M0nKJJ006207: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 02:49:27 saibot sm-mta[6210]: o6M0nRuB006210: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 03:00:01 saibot sm-msp-queue[6281]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 03:01:01 saibot sm-msp-queue[6281]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 03:20:01 saibot sm-msp-queue[6383]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 03:21:01 saibot sm-msp-queue[6383]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 03:40:01 saibot sm-msp-queue[6504]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 03:41:01 saibot sm-msp-queue[6504]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 04:00:01 saibot sm-msp-queue[6598]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 04:01:01 saibot sm-msp-queue[6598]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 04:20:01 saibot sm-msp-queue[6696]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 04:21:01 saibot sm-msp-queue[6696]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 04:40:02 saibot sm-msp-queue[6814]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 04:41:02 saibot sm-msp-queue[6814]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 05:00:01 saibot sm-msp-queue[6913]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 05:01:01 saibot sm-msp-queue[6913]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 05:20:01 saibot sm-msp-queue[6991]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 05:21:01 saibot sm-msp-queue[6991]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 05:40:01 saibot sm-msp-queue[7099]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 05:41:01 saibot sm-msp-queue[7099]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 06:00:01 saibot sm-msp-queue[7206]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 06:01:01 saibot sm-msp-queue[7206]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 06:20:01 saibot sm-msp-queue[7286]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 06:21:01 saibot sm-msp-queue[7286]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 06:40:02 saibot sm-msp-queue[7401]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 06:41:02 saibot sm-msp-queue[7401]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 07:00:01 saibot sm-msp-queue[7513]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 07:01:01 saibot sm-msp-queue[7513]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 07:20:01 saibot sm-msp-queue[7618]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 07:21:01 saibot sm-msp-queue[7618]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 07:40:01 saibot sm-msp-queue[7728]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 07:41:01 saibot sm-msp-queue[7728]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 08:00:01 saibot sm-msp-queue[7819]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 08:01:01 saibot sm-msp-queue[7819]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 08:20:01 saibot sm-msp-queue[7938]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 08:21:01 saibot sm-msp-queue[7938]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 08:40:02 saibot sm-msp-queue[8039]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 08:41:02 saibot sm-msp-queue[8039]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 09:00:01 saibot sm-msp-queue[8139]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 09:01:01 saibot sm-msp-queue[8139]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 09:20:01 saibot sm-msp-queue[8256]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 09:21:01 saibot sm-msp-queue[8256]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 09:40:01 saibot sm-msp-queue[8367]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 09:41:01 saibot sm-msp-queue[8367]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 10:00:01 saibot sm-msp-queue[8465]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 10:01:01 saibot sm-msp-queue[8465]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 10:18:18 saibot sm-mta[8611]: o6M8IIrH008611: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 10:20:06 saibot sm-msp-queue[8685]: My unqualified host name (saibot) unknown; sleeping for retry
Jul 22 10:21:06 saibot sm-msp-queue[8685]: unable to qualify my own domain name (saibot) -- using short name
Jul 22 10:29:55 saibot postfix/master[9521]: fatal: bind 0.0.0.0 port 25: Address already in use
Jul 22 10:32:59 saibot sm-mta[9549]: o6M8WxU0009549: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 10:33:45 saibot sm-mta[9554]: o6M8Xj2O009554: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 10:33:45 saibot postfix/postdrop[9557]: warning: unable to look up public/pickup: No such file or directory
Jul 22 10:47:23 saibot sm-mta[9735]: o6M8lNcL009735: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 10:48:05 saibot sm-mta[9748]: o6M8m59L009748: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 10:48:05 saibot postfix/postdrop[9751]: warning: unable to look up public/pickup: No such file or directory
Jul 22 11:28:30 saibot postfix/postfix-script[10231]: fatal: the Postfix mail system is not running
Jul 22 11:28:43 saibot postfix/master[10332]: fatal: bind 0.0.0.0 port 25: Address already in use
Jul 22 11:28:52 saibot postfix/postfix-script[10348]: fatal: the Postfix mail system is not running
Jul 22 11:29:05 saibot postfix/master[10449]: fatal: bind 0.0.0.0 port 25: Address already in use
Jul 22 11:29:20 saibot sm-mta[10451]: o6M9TKuJ010451: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 11:29:20 saibot postfix/postdrop[10454]: warning: unable to look up public/pickup: No such file or directory
Jul 22 11:32:00 saibot sm-mta[10485]: o6M9W0MI010485: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 11:32:04 saibot sm-mta[10488]: o6M9W4aM010488: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 11:32:36 saibot postfix/master[10619]: fatal: bind 0.0.0.0 port 25: Address already in use
Jul 22 11:32:40 saibot postfix/postfix-script[10635]: fatal: the Postfix mail system is not running
Jul 22 11:54:12 saibot postfix/master[11131]: fatal: bind 0.0.0.0 port 25: Address already in use
Jul 22 11:54:24 saibot postfix/postfix-script[11147]: fatal: the Postfix mail system is not running
Jul 22 11:54:59 saibot sm-mta[11154]: o6M9sxSL011154: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 11:55:07 saibot sm-mta[11164]: o6M9t7cg011164: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA-v4
Jul 22 11:55:07 saibot postfix/postdrop[11167]: warning: unable to look up public/pickup: No such file or directory
```

---

### Post by MJN on 2010-07-22
> **figure002 said:**
> ```
Jul 22 10:29:55 saibot postfix/master[9521]: fatal: bind 0.0.0.0 port 25: Address already in use
```
 
Your issue is that Postfix is unable to start (and bind to port 25 as MTA's do) because it seems Sendmail (or something else) is still running (and hence hanging onto that port).
 
The installation output shows a bit of a rocky course because it fell into a race condition - Postfix cannot be installed whilst Sendmail is installed and so the latter was requested to be removed, however sensible-mda required an MTA - whether that be Sendmail or Postfix be installed - and so was effectively reluctant to let Sendmail go given that it didn't know Postfix was due to be installed to replace it. (It doesn't work quite like that, but it illustrates the point).
 
I'd remove sensible-mda if I were you (as you won't necessarilly require it with Postfix), then remove sendmail (again, just in case), then try and start Postfix and see how you get on from there.
 
Mathew

---

### Post by figure002 on 2010-07-22
> **MJN said:**
> Your issue is that Postfix is unable to start (and bind to port 25 as MTA's do) because it seems Sendmail (or something else) is still running (and hence hanging onto that port).
 
The installation output shows a bit of a rocky course because it fell into a race condition - Postfix cannot be installed whilst Sendmail is installed and so the latter was requested to be removed, however sensible-mda required an MTA - whether that be Sendmail or Postfix be installed - and so was effectively reluctant to let Sendmail go given that it didn't know Postfix was due to be installed to replace it. (It doesn't work quite like that, but it illustrates the point).
 
I'd remove sensible-mda if I were you (as you won't necessarilly require it with Postfix), then remove sendmail (again, just in case), then try and start Postfix and see how you get on from there.
 
Mathew
Thanks for the explanation! Rebooting the system fixed the port in use problem as this allowed sendmail to be completely removed. I also removed sensible-mda. Now Postfix works like a charm! Thank you very much! :D

---

### Post by MJN on 2010-07-22
You're welcome, and well done for getting it working!
 
(One tip though: Try and resist the temptation to reboot to get yourself out of sticky situations - it's rarely necessary unlike with some other OS's where it may well be regarded as standard practice! ;))
 
Mathew

---

