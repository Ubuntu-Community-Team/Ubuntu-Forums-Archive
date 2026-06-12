---
title: "postfix - mail not saved to  directory"
date: 2008-12-09
forum: Server Platforms
---

### Post by bandito40 on 2008-12-09
Hi,

I just installed Postifx, Courier, Mysql, and postfixadmin according to this tutorial [https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto]("https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto"). Everything seams to be fine except for postfixamdin taking a very long time to send mail and create virtual accounts. I figure this is because there are some wrong settings that won't allow one of the mail server components to write an email to disk or create the appropriate file folder.

In /etc/postfix/main.cf the virutal mailbox is pointing too /home/vmail which I created and gave it chmod 777.
virtual_mailbox_base = /home/vmail

In the same config file I also have the following assigned variable.
myorigin = /etc/mailname


I checked /var/mail/computername and ~/Maildir but neither show my messages.

Every user I created with postfixadmin shows in the Mysql database including domains and aliases.

Just the mail is not being saved.

Anyone have any ideas?

Thanks,

Carl

---

### Post by albinootje on 2008-12-09
First of all a chmod 777 can be dangerous in general. The /home/vmail directory and all files should be owned by user vmail, so chmod 700 or 770 should be fine for /home/vmail

You should be able to find your emails in /home/vmail/

It depends on your postfixadmin configuration php-file in what directory-structure within /home/vmail the email will end up.

I'm using postfixadmin + dovecot with Debian on a few mailservers since years. I've followed this howto for it : [http://wiki.dovecot.org/HowTo/DovecotLDAPostfixAdminMySQL](http://wiki.dovecot.org/HowTo/DovecotLDAPostfixAdminMySQL) which is aimed at rpm, but basically only the gid for "mail" needed to be changed so that it worked in Debian.

I prefer dovecot over courier, because of :
1) speed
2) dovecot is focused on security
3) dovecot can handle sieve
4) dovecot has an active development and a resposive author
5) i don't like the maildrop add-on for courier,
   dovecot can do excellent mail-delivery instead

And.. what are you using to read your emails ?
Mutt or pine or ? For mutt you need to make sure it talks to the imap-server software, or read the Mailbox directly.
For thunderbird and squirrelmail it's a matter of configuring it correctly so it talk properly with the imap-server software.

---

### Post by bandito40 on 2008-12-11
This is too confusing.   I tried to change the /home/vmail permissions and also played around with chown but there still the same complications.  So I purged the entire install and decided to try postifx/dovecot/mysql.  I looked at the tutorial in your post but that seams to be more for centos and other non ubunutu verisions of linux making a little complicated for me.  I tried this tutorial [http://bliki.rimuhosting.com/space/knowledgebase/linux/mail/postfixadmin+on+debian](http://bliki.rimuhosting.com/space/knowledgebase/linux/mail/postfixadmin+on+debian).  I ran into one problem and that was configuring dovecot.  Seamed like it would not accept the suggested configuration and I left dovecot with it's factory configuration to get it running.  The end result was the exact same problems.  Worked fine with mysql but would not save and emails.

What is the world am I doing wrong?

Actually I left something out.  I am trying to run this as a test server on my computer for a email based software idea that I am working on. I set all of my server name settings, domains names, and email accounts to be localhost.  Maybe that has something to do with it.

---

### Post by albinootje on 2008-12-11
Interesting. I remember that url you mentioned. 
(But what they write is not true, postfixadmin is not in the official repositories of debian and ubuntu. 
The postfixadmin people however do provide a deb package.)

Did you check the log-files ?

And you didn't answer how you check your email.

Checking in /var/mail or ~/Maildir doesn't make sense because ALL email will end up in /home/vmail (or /var/vmail in some Howtos).

So.. you either have to let your email-client talk to dovecot properly.
(In squirrelmail you need to look at what to use as Prefix in the settings in the imap subsection)

Or you can read the mailfolder directly with mutt, like this :
mutt -f /home/vmail/your_domain/your_user/

You can of course also manually browse /home/vmail/

---

### Post by bandito40 on 2008-12-11
ok.

I looked for log files but did not find them.


I am using Thunderbird, Evolution, and Postifxadmin to check and send mail.  I also use a php script to send mail.

I also check mail by going through /home/vmail and also the other two, /var/mail and ~/Maildir

I guess there is some problem with every MTA that I use.  Anyhow, I'll keep plugin' away.

I tried to telnet to locahost imap but I can connect but not login when dovecot is not configured but cannot connect when it is configured .

I finally got dovecot to restart with the suggested settings but which says the status is [OK] but when using nmap there is not service or port shown and ps -A doesn't show dovecot running either.


Thanks for you help.

---

### Post by albinootje on 2008-12-11
To check whether dovecot works correctly, try : sudo tail -f /var/log/syslog
See also this to check the dovecot installation :
[http://wiki.dovecot.org/TestInstallation](http://wiki.dovecot.org/TestInstallation)

---

### Post by bandito40 on 2008-12-11
OK.  Made some progress.  I finally got dovecot working.  I forget to configure the file /etc/dovecot/dovecot-mysql.conf.  After testing it with telnet like suggested on the page you recommended, everything worked.  I also noticed that the following files and folders where created in /home/vmail/localhost/test:

drwxrwx--- 2 postfix postfix  4096 2008-12-11 13:28 cur
-rwxrwx--- 1 postfix postfix   144 2008-12-11 13:28 dovecot.index
-rwxrwx--- 1 postfix postfix 10272 2008-12-11 13:28 dovecot.index.cache
-rwxrwx--- 1 postfix postfix   104 2008-12-11 13:28 dovecot.index.log
drwxrwx--- 2 postfix postfix  4096 2008-12-11 13:28 new
drwxrwx--- 2 postfix postfix  4096 2008-12-11 13:28 tmp

The mail folders themselves are still empty.

I still can't configure Thunderbird or any other email client to work.  I am sure I am just around the corner from making this work.  Anyhow, here is some output from the Tail application: (bandito/bandito@localhost is the admin for postfixadmin, and it is also the name of my computer)

>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: 8836546969: message-id=<20081211185706.8836546969@bandito>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: warning: 8836546969: virtual_alias_maps map lookup problem for test@localhost
Dec 11 13:57:06 bandito postfix/pickup[14578]: 8884E46969: uid=33 from=<www-data>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: 8884E46969: message-id=<20081211185706.8884E46969@bandito>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: warning: 8884E46969: virtual_alias_maps map lookup problem for bandito@localhost
Dec 11 13:57:06 bandito postfix/pickup[14578]: 88D0346969: uid=33 from=<www-data>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: 88D0346969: message-id=<20081211185706.88D0346969@bandito>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: warning: 88D0346969: virtual_alias_maps map lookup problem for bandito@localhost
Dec 11 13:57:06 bandito postfix/pickup[14578]: 894E946969: uid=33 from=<www-data>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: 894E946969: message-id=<20081211185706.894E946969@bandito>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: warning: 894E946969: virtual_alias_maps map lookup problem for test@localhost
Dec 11 13:57:06 bandito postfix/pickup[14578]: 89A7746969: uid=33 from=<www-data>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: 89A7746969: message-id=<20081211185706.89A7746969@bandito>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: warning: 89A7746969: virtual_alias_maps map lookup problem for bandito@localhost
Dec 11 13:57:06 bandito postfix/pickup[14578]: 89F4346969: uid=33 from=<www-data>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: 89F4346969: message-id=<20081211185706.89F4346969@bandito>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: warning: 89F4346969: virtual_alias_maps map lookup problem for bandito@localhost
Dec 11 13:57:06 bandito postfix/pickup[14578]: 8A43B46969: uid=33 from=<www-data>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: 8A43B46969: message-id=<20081211185706.8A43B46969@bandito>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: warning: 8A43B46969: virtual_alias_maps map lookup problem for test@localhost
Dec 11 13:57:06 bandito postfix/pickup[14578]: 8A8F246969: uid=33 from=<www-data>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: 8A8F246969: message-id=<20081211185706.8A8F246969@bandito>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: warning: 8A8F246969: virtual_alias_maps map lookup problem for test@localhost
Dec 11 13:57:06 bandito postfix/pickup[14578]: 8AD9E46969: uid=33 from=<www-data>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: 8AD9E46969: message-id=<20081211185706.8AD9E46969@bandito>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: warning: 8AD9E46969: virtual_alias_maps map lookup problem for test@localhost
Dec 11 13:57:06 bandito postfix/pickup[14578]: 8B29246969: uid=1000 from=<bandito>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: 8B29246969: message-id=<20081211185706.8B29246969@bandito>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: warning: 8B29246969: virtual_alias_maps map lookup problem for bandito@locahost
Dec 11 13:57:06 bandito postfix/pickup[14578]: 8B75046969: uid=33 from=<www-data>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: 8B75046969: message-id=<20081211185706.8B75046969@bandito>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: warning: 8B75046969: virtual_alias_maps map lookup problem for bandito@localhost
Dec 11 13:57:06 bandito postfix/pickup[14578]: 8BBF046969: uid=33 from=<www-data>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: 8BBF046969: message-id=<20081211185706.8BBF046969@bandito>
Dec 11 13:57:06 bandito postfix/cleanup[14805]: warning: 8BBF046969: virtual_alias_maps map lookup problem for bandito@localhost
Dec 11 13:57:49 bandito postfix/smtpd[14968]: fatal: bad boolean configuration: broken_sasl_auth_clients = yes smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_hostname, reject_non_fqdn_sender, reject_non_fqdn_recipient, reject_unauth_destination, reject_unauth_pipelining, reject_invalid_hostname smtpd_sasl_auth_enable = yes smtpd_sasl_local_domain = bandito smtpd_sasl_security_options = noanonymous
Dec 11 13:57:50 bandito postfix/master[14574]: warning: process /usr/lib/postfix/smtpd pid 14968 exit status 1
Dec 11 13:57:50 bandito postfix/master[14574]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Dec 11 13:58:06 bandito postfix/pickup[14578]: 8C36846969: uid=33 from=<www-data>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: 8C36846969: message-id=<20081211185806.8C36846969@bandito>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: warning: connect to mysql server localhost: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Dec 11 13:58:06 bandito postfix/cleanup[14805]: warning: 8C36846969: virtual_alias_maps map lookup problem for test@localhost
Dec 11 13:58:06 bandito postfix/pickup[14578]: 8F41446969: uid=33 from=<www-data>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: 8F41446969: message-id=<20081211185806.8F41446969@bandito>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: warning: 8F41446969: virtual_alias_maps map lookup problem for test@localhost
Dec 11 13:58:06 bandito postfix/pickup[14578]: 8F8EC46969: uid=33 from=<www-data>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: 8F8EC46969: message-id=<20081211185806.8F8EC46969@bandito>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: warning: 8F8EC46969: virtual_alias_maps map lookup problem for bandito@localhost
Dec 11 13:58:06 bandito postfix/pickup[14578]: 8FDA846969: uid=33 from=<www-data>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: 8FDA846969: message-id=<20081211185806.8FDA846969@bandito>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: warning: 8FDA846969: virtual_alias_maps map lookup problem for bandito@localhost
Dec 11 13:58:06 bandito postfix/pickup[14578]: 9047A46969: uid=33 from=<www-data>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: 9047A46969: message-id=<20081211185806.9047A46969@bandito>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: warning: 9047A46969: virtual_alias_maps map lookup problem for test@localhost
Dec 11 13:58:06 bandito postfix/pickup[14578]: 9094A46969: uid=33 from=<www-data>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: 9094A46969: message-id=<20081211185806.9094A46969@bandito>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: warning: 9094A46969: virtual_alias_maps map lookup problem for bandito@localhost
Dec 11 13:58:06 bandito postfix/pickup[14578]: 90DFE46969: uid=33 from=<www-data>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: 90DFE46969: message-id=<20081211185806.90DFE46969@bandito>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: warning: 90DFE46969: virtual_alias_maps map lookup problem for bandito@localhost
Dec 11 13:58:06 bandito postfix/pickup[14578]: 9131346969: uid=33 from=<www-data>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: 9131346969: message-id=<20081211185806.9131346969@bandito>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: warning: 9131346969: virtual_alias_maps map lookup problem for test@localhost
Dec 11 13:58:06 bandito postfix/pickup[14578]: 917D746969: uid=33 from=<www-data>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: 917D746969: message-id=<20081211185806.917D746969@bandito>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: warning: 917D746969: virtual_alias_maps map lookup problem for test@localhost
Dec 11 13:58:06 bandito postfix/pickup[14578]: 91C8946969: uid=33 from=<www-data>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: 91C8946969: message-id=<20081211185806.91C8946969@bandito>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: warning: 91C8946969: virtual_alias_maps map lookup problem for test@localhost
Dec 11 13:58:06 bandito postfix/pickup[14578]: 9216746969: uid=1000 from=<bandito>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: 9216746969: message-id=<20081211185806.9216746969@bandito>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: warning: 9216746969: virtual_alias_maps map lookup problem for bandito@locahost
Dec 11 13:58:06 bandito postfix/pickup[14578]: 9264646969: uid=33 from=<www-data>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: 9264646969: message-id=<20081211185806.9264646969@bandito>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: warning: 9264646969: virtual_alias_maps map lookup problem for bandito@localhost
Dec 11 13:58:06 bandito postfix/pickup[14578]: 92AFE46969: uid=33 from=<www-data>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: 92AFE46969: message-id=<20081211185806.92AFE46969@bandito>
Dec 11 13:58:06 bandito postfix/cleanup[14805]: warning: 92AFE46969: virtual_alias_maps map lookup problem for bandito@localhost

---

### Post by albinootje on 2008-12-11
Cool that you made progress! :)

It looks like you have some syntax error in the postfix configuration
(/etc/postfix/main.cf)

Dec 11 13:57:06 bandito postfix/cleanup[14805]: warning: 8BBF046969: virtual_alias_maps map lookup problem for bandito@localhost
Dec 11 13:57:49 bandito postfix/smtpd[14968]: fatal: bad boolean configuration: 
--- cut ---
smtpd_sasl_local_domain = bandito smtpd_sasl_security_options = noanonymous

you should leave it like this :

broken_sasl_auth_clients = yes
smtpd_recipient_restrictions =
  permit_mynetworks,
  permit_sasl_authenticated,
  reject_non_fqdn_hostname,
  reject_non_fqdn_sender,
  reject_non_fqdn_recipient,
  reject_unauth_destination,
  reject_unauth_pipelining,
  reject_invalid_hostname
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_security_options = noanonymous

Because postfix will use the $myhostname anyway.
And you need to make sure that your machine is gonna use a real hostname for postfix to deal with.

You need a name like for example test.ubuntulinux.org

This is about /etc/hosts and /etc/hostname
and for postfix about /etc/mailname

See also : man hostname

HTH

---

### Post by albinootje on 2008-12-11
By the way. If dovecot is now running successfully then Thunderbird should be able to connect. Are you testing this on your desktop-machine or somewhere remotely ?

If it's on your desktop-machine, then the settings for "incoming email" for just testing this would be :

server : localhost
port   : 143
username : your-username@your-domain

I don't remember whether dovecot (in ubuntu) automatically creates a hand-made SSL certificate, but if it does, you then can check imap-ssl with port 993 instead of 143.

---

