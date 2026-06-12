---
title: "Howto: setup a mail server in Ubuntu"
date: 2005-06-07
forum: Tutorials
---

### Post by flurdy on 2005-06-07
I have rewritten my [How to set up a mail server on a GNU / Linux system](http://flurdy.com/docs/postfix/) , which is now based on Ubuntu Hoary.

(Used to be Mandrake, but is now completely rewritten from scratch to use apt-get, The old one was listed on postfix.org)

It is a complete step by step guide to install, configure and run these packages:
Ubuntu + Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + SquirrelMail 

Not sure whether this should be in the server forum, but it is a howto hence the tips forum.
I must be wrong, but I could not see any other mail server howtos for ubuntu mentioned in the forums.

Feel free to send me comments.

All the installation and configuration sections are complete. Some of the later testing and appendix needs padding out, but as any other document it will forever be in development.  ;-)

---

### Post by Gtaylor on 2005-06-07
Very nice! This will be a big help for those playing with Ubuntu servers.

---

### Post by pdk001 on 2005-06-07
thanks for a tip

---

### Post by skoal on 2005-06-07
At first glance it looks thorough and well designed.  I'll have to give 'er a rip...

thx.

\\//_

---

### Post by Gtaylor on 2005-06-07
Make sure you hit that little check button under avatars and give people positive rep who do things like this. It doesn't look like anyone is using the rep system and maybe it could be employed to reflect well on people's contributions.

---

### Post by SFN on 2005-06-08
[QUOTE=Gtaylor]Make sure you hit that little check button under avatars and give people positive rep who do things like this.[/QUOTE]

I never noticed that. That sure would make a good sticky post.

Thanks flurdy for the HOWTO and thanks Gtaylor for the tip.

---

### Post by keptang on 2005-07-16
I'm unable to access the link in the first message [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/), anyone have a mirror?

Seem like the domain isn't up anymore..

TIA

---

### Post by Heliode on 2005-07-16
[QUOTE=keptang]I'm unable to access the link in the first message [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/), anyone have a mirror?

Seem like the domain isn't up anymore..

TIA[/QUOTE]

Same here. Too bad, I was looking forward to trying this out!

---

### Post by mrcbrown on 2005-07-16
Found a cached version on Google - saved and reposted here:

[http://www.charlesabrown.com/ubuntu/shareme.html](http://www.charlesabrown.com/ubuntu/shareme.html)

If flurdy or anyone else needs a place to post some how-to's drop me a PM - always have some space here or there.

---

### Post by flurdy on 2005-07-17
Cheers mrcbrown.

Thanks for the help, however my own hosting is fine.

I messed around with the network settings on my server on friday,
and put the wrong ip in for the external interface. whoops.

So the demise of me and my server was a bit premature.. :)

---

### Post by caeserjk on 2005-07-20
I have followed the direction on just getting the mail server setup. I have create the users in the maildb tables and mail sent to them will go in the virtual folders. For some reason I cannot use an imap client to check the mail, it will not authenticate the users. Wonder if there is some way which I can check to see if the users are able to login. 

I am currently trying to use evolution. 

P.s. Newb here.

---

### Post by flurdy on 2005-07-21
Turn debug on in courier's imap file and tail the syslog.
Further enable query logging in mysql and tail mysql's log file as well.

For more details see the testing chapter of my howto.

---

### Post by brolewis on 2005-08-03
Holy Cow! This is an excellent reference! I have been trying for over a month to get my email server up and running and I got it working in only 2 days better than I was trying to do. Thanks a TON!

---

### Post by anthonysales on 2005-08-08
i followed all the directions...when i do a squirrelmail configtest, everything goes well..my configuration seems to be ok! but when i try to login, i always get an unknown user and password error! is mysql the only way to add users to the database?! or is there any other easier way? i've been trying to set this up for 2 days, and no luck! ](*,)  ](*,)  is it because the "Current user:" is mail@localhost in my mysql database? the rest of my settings are set at "mail@anthonysales.org" if this is the problem, how do i change the "Current user:"?? thanks in advance for the replies!=)

---

### Post by flurdy on 2005-08-09
[QUOTE=anthonysales]i followed all the directions...when i do a squirrelmail configtest, everything goes well..my configuration seems to be ok! but when i try to login, i always get an unknown user and password error! is mysql the only way to add users to the database?! or is there any other easier way? i've been trying to set this up for 2 days, and no luck! ](*,)  ](*,)  is it because the "Current user:" is mail@localhost in my mysql database? the rest of my settings are set at "mail@anthonysales.org" if this is the problem, how do i change the "Current user:"?? thanks in advance for the replies!=)[/QUOTE]

As usual with debugging this is a step by step issue.
First of all does postfix work okay? if u send mail from the outside does it create folders and files in /var/spool/mail/virtual corresponding to your users table settings?

If postfix is fine then do general imap access work ok ?  

Finally if all the others work we can get to squirrelmail and your specific questions.

Is MySQL the only way to add users? Well you can use a plethero of free admin packages to do this, however I think they all require the system to be set up in a specific way. And in the end they all have to be in put into the MySQL database. You can enable local users outside of the database, but I prefer not to use that hence not in the howto. In the end how many and how often are you going to add users? If loads then just set up a simple web page to insert it into the db via jsp, perl , php etc.

Not sure I understand what you mean by "Current User", and how it relates to your email address.
You have a username to log in to the database, but that has nothing to do with you email user ids. It only relates to database access, not what is specified in the alias and users table. The database username is what you specify in the mysql*.cf in the postfix folder, and in the courier config and also in the squirrelmail config. You send email to and log into the imap server and log into the webmail with the email address you have added to you users table.

My advice is to turn on mysql debugging and tail that log to find out what actually happens.

---

### Post by oberon on 2005-08-09
First I just wana say thanks for the great guide!  One thing though... when entering data into the maildb I am getting errors:

> mysql> INSERT INTO domains (domain) VALUES
    -> ('localhost'),
    -> ('localhost.localdomain');
ERROR 1062: Duplicate entry '0' for key 1 

I have checked the syntax and can't seem to get pas this.  I also tried inserting the rows in PHPMyadmin with the same results.

Thanks,

oberon

---

### Post by flurdy on 2005-08-10
[QUOTE=oberon]First I just wana say thanks for the great guide!  One thing though... when entering data into the maildb I am getting errors:

 

I have checked the syntax and can't seem to get pas this.  I also tried inserting the rows in PHPMyadmin with the same results.

Thanks,

oberon[/QUOTE]

 :) the error indicates the domain already exist in the table. 
check with 
select * from domains where domain like 'local%'

---

### Post by oberon on 2005-08-10
>  the error indicates the domain already exist in the table.
check with
select * from domains where domain like 'local%'

Actually it was my bad... forgot to set the auto_increment on the PKID colum.  Oops. :)

---

### Post by anthonysales on 2005-08-19
whenever i try to start postfix... i get this in my mail.info log 

[FONT=Courier New]localhost postfix/qmgr[9914]: 199703AC50F: to=<root@localhost.localdomain>, orig_to=<root>, relay=none, delay=55163, status=deferred (delivery temporarily suspended: address resolver failure)[/FONT]

i haven't added spamassasin,amavisd or clamav yet..i'm just testing my mail server to see if it works..  any suggestions?! hehe..=)

---

### Post by Rodrigo on 2005-08-19
thank you Oh, thank you!  :grin:

---

### Post by Brad wilkinson on 2005-08-20
have you thought of submitting your HOWTO to the linux documentation project?

---

### Post by FLeiXiuS on 2005-08-20
This is by far one of the best guides...great job!  :-)

---

### Post by ShagzModo on 2005-08-20
does this server read ldap directory?

---

### Post by djtric on 2005-08-21
i got everything up and running. my only problem is, when i add users, squirrelmail says that the home directory doesn't exist. but when i add the folder in the /var/spool/mail/virtual directory, squirrelmail gives me an error saying "ERROR : Could not complete request. Query: SELECT "INBOX" Reason Given: Unable to open this mailbox." my default user (the user i always use when logging in to my box) seems to work fine. i don't even remember adding a folder in to the maildir. did courier imap create it automatically? if so, how did this happen and why won't it happen again? thanks in advance for the replies.  :smile:

---

### Post by cllsr on 2005-08-28
This is an ecellent guide. However I did encounter a problem with Amavis not creating the lock file with the proper permissions.

 I still have not figured it out without manually setting them and resarting Amavis. 

Anyone have a suggestion?

 Since the lock file resides in /var/run/amavis/amavis.lock which needs to be chown'ed virtual:virtual and is amavis:amavis. 

I have not found a way to change it's behavior without it changing itself back upon reboot.

---

### Post by thomask on 2005-08-31
I also thought this was a great guide, though I do not really need multiple domains or antivirus or spam. I am just trying to set up an intranet webmail/email server on a closed (no internet access) LAN...

I also have had a lot of problems with it not recognizing a user, even though I created several via phpmyadmin, and I am pretty fluent with it as I deal with osCommerce, phpbb, coppermine, as well as other php scripts.

You would think there would be a simple way to configure email, as long as it has been around. Photo galleries suprise me with their ease of install and configuration, considering all of the features they have. Why can't email be as simple?

My main user account, mail as well as my other account, thomas, are not being recognized by the squirrelmail or IMAP, as I configured my outlook on a windows box to log in and access it, tried many username/pw combinations to no use. I tried the debug part of the guide, but maybe my version of ubunu has things in different spots, the first time i try:

/etc/init.d/courier stop

it errors out.. and there is no listing for courier in that directory, so wtf? did i screw something up on the install?

I am only thinking of uninstalling the whole mess and starting over.

anybody else have a similar prob?

---

### Post by oberon on 2005-09-04
[QUOTE=djtric]i got everything up and running. my only problem is, when i add users, squirrelmail says that the home directory doesn't exist. but when i add the folder in the /var/spool/mail/virtual directory, squirrelmail gives me an error saying "ERROR : Could not complete request. Query: SELECT "INBOX" Reason Given: Unable to open this mailbox." my default user (the user i always use when logging in to my box) seems to work fine. i don't even remember adding a folder in to the maildir. did courier imap create it automatically? if so, how did this happen and why won't it happen again? thanks in advance for the replies.  :smile:[/QUOTE]

I have the same problem...  I tried "maildirmake' and no change.  How are the maildirs made?  It does not seem to be automatic.  Thanks again for the howto.

-oberon

---

### Post by oberon on 2005-09-04
[QUOTE=cllsr]This is an ecellent guide. However I did encounter a problem with Amavis not creating the lock file with the proper permissions.

 I still have not figured it out without manually setting them and resarting Amavis. 

Anyone have a suggestion?

 Since the lock file resides in /var/run/amavis/amavis.lock which needs to be chown'ed virtual:virtual and is amavis:amavis. 

I have not found a way to change it's behavior without it changing itself back upon reboot.[/QUOTE]

I am working on it and will post it.


-oberon

---

### Post by flurdy on 2005-09-08
Going to try and answer a few questions.

[QUOTE=Brad wilkinson]have you thought of submitting your HOWTO to the linux documentation project?[/QUOTE]

Nah, there are many howtos out there which are excellent. This one is a bit Ubuntu specific in some cases.

[QUOTE=anthonysales]whenever i try to start postfix... i get this in my mail.info log 

[FONT=Courier New]localhost postfix/qmgr[9914]: 199703AC50F: to=<root@localhost.localdomain>, orig_to=<root>, relay=none, delay=55163, status=deferred (delivery temporarily suspended: address resolver failure)[/FONT]

i haven't added spamassasin,amavisd or clamav yet..i'm just testing my mail server to see if it works..  any suggestions?! hehe..=)[/QUOTE]


This still a problem? check that your postfix doesnt think the machine is called localhost.localdomain.

[QUOTE=ShagzModo]does this server read ldap directory?[/QUOTE]

Postfix does yes, however there is no details of this in this howto.

[QUOTE=djtric]i got everything up and running. my only problem is, when i add users, squirrelmail says that the home directory doesn't exist. but when i add the folder in the /var/spool/mail/virtual directory, squirrelmail gives me an error saying "ERROR : Could not complete request. Query: SELECT "INBOX" Reason Given: Unable to open this mailbox." my default user (the user i always use when logging in to my box) seems to work fine. i don't even remember adding a folder in to the maildir. did courier imap create it automatically? if so, how did this happen and why won't it happen again? thanks in advance for the replies.  :smile:[/QUOTE]

Dont create folders in   /var/spool/mail/virtual .
Postfix creates these properly when it receives the first mail intended for that user.

[QUOTE=cllsr]This is an ecellent guide. However I did encounter a problem with Amavis not creating the lock file with the proper permissions.

 I still have not figured it out without manually setting them and resarting Amavis. 

Anyone have a suggestion?

 Since the lock file resides in /var/run/amavis/amavis.lock which needs to be chown'ed virtual:virtual and is amavis:amavis. 

I have not found a way to change it's behavior without it changing itself back upon reboot.[/QUOTE]

Yes, a problem I encountered as well. Hope i remembered to include it in the howto.
Since the lock file is removed and added etc, amavis needs write access to the parent folder. So /var/run/amavis needs to be owned by virtual:virtual .
Also check that    $daemon_user  = 'virtual'; and $daemon_group = 'virtual';
in the /etc/amavis/amavisd.conf.

---

### Post by flurdy on 2005-09-08
[QUOTE=thomask]I also thought this was a great guide, though I do not really need multiple domains or antivirus or spam. I am just trying to set up an intranet webmail/email server on a closed (no internet access) LAN...

I also have had a lot of problems with it not recognizing a user, even though I created several via phpmyadmin, and I am pretty fluent with it as I deal with osCommerce, phpbb, coppermine, as well as other php scripts.

You would think there would be a simple way to configure email, as long as it has been around. Photo galleries suprise me with their ease of install and configuration, considering all of the features they have. Why can't email be as simple?[/QUOTE]

For simple one domain and couple of users, email servers on linux is simple. 

Postfix withouth virtual domains will just use the users on the box as users with the address as username@machinename. 

The default set up works, quickly and easily, however that is not enough for many people so thats why this howto extends this simple setup by adding limtless domains, users, aliases, spam, virus scan etc. 

[QUOTE=thomask]My main user account, mail as well as my other account, thomas, are not being recognized by the squirrelmail or IMAP, as I configured my outlook on a windows box to log in and access it, tried many username/pw combinations to no use. I tried the debug part of the guide, but maybe my version of ubunu has things in different spots, the first time i try:

/etc/init.d/courier stop

it errors out.. and there is no listing for courier in that directory, so wtf? did i screw something up on the install?

I am only thinking of uninstalling the whole mess and starting over.

anybody else have a similar prob?[/QUOTE]


 :smile: Ah its nothing is easy :)
If you have followed this howto, which may not be needed in your case if you just want a simple server, then check if mail dirs exits in virtual spool folder. next check the sql querries if that is where it goes wrong, etc.. :(

[QUOTE=oberon]I have the same problem...  I tried "maildirmake' and no change.  How are the maildirs made?  It does not seem to be automatic.  Thanks again for the howto.

-oberon[/QUOTE]

AS mentioned just above, Postfix creates these folders. If they are not created, then your postfix config is wrong. Simple way to check if things are okay.

---

### Post by alfmatos on 2005-09-08
A few suggestions:

server side mail rules , configurable via squirrelmail (this requires maildrop i think, i'm still strugling with maildrop on ubuntu) - this is the feature i'm really trying hard to get working.

postfixadmin - really comes in handy when administration is required

mysql change - move from mysql tcp access to the the sock , this is fairly easy to do, and safer.


Question : what are the tables for when setting up squirellmail ?

I dindn't follow you're guide, but it's very good. I followed similar one's, but i guessed you already read them, since the similarities are remarkable :)

Anyways, great job. If you need help on the proposed addons, talk to me, i can lend you some words and steps to configure.

---

### Post by olpe on 2005-09-10
Thank you for great howto! I did everything by the howto and everything worked fine until I checked mail.info for the first time. it is full of  

localhost postfix/qmgr[9255]: warning: connect to transport smtp: Connection refused 

warnings. Any idea how to fix this?

I get connection with telnet localhost 25. Squirrelmail is working (but of course not the sending/recieving thing) so I pretty much think that it is only a postfix problem.

---

### Post by Ubuntunub on 2005-09-13
Hello everyone,

I am a nub when it comes to linux or mail servers :-). I have a question about the mailserver. When you set up the mailserver you can create e-mail adresses for use within your lan. But can other external people also mail to you? Because my pc has a dynamic ip.

thanx in advance

---

### Post by cllsr on 2005-09-17
[QUOTE=flurdy]Going to try and answer a few questions.


Yes, a problem I encountered as well. Hope i remembered to include it in the howto.
Since the lock file is removed and added etc, amavis needs write access to the parent folder. So /var/run/amavis needs to be owned by virtual:virtual .
Also check that    $daemon_user  = 'virtual'; and $daemon_group = 'virtual';
in the /etc/amavis/amavisd.conf.[/QUOTE]


I have already done that the problem is when Amavis starts it checks permissions on the directory and automatically changes uid and gid back to amavis:amavis. I am still looking for an answer.

Here is the log entry I keep getting.
root@scorpion:/home/chris # /etc/init.d/amavis stop
Stopping amavisd: amavisd-new.
root@scorpion:/home/chris # /etc/init.d/amavis start
Starting amavisd: mode of `/var/run/amavis' changed to 0755 (rwxr-xr-x)
Pid_file "/var/run/amavis/amavisd.pid" already exists.  Overwriting!
amavisd-new.

Here is the lock file error.

Sep 17 11:41:54 localhost amavis[9842]: Net::Server: 2005/09/17-11:41:54 Couldn't open lock file "/var/run/amavis/amavisd.lock" [Permission denied]\n  at line 239 in file /usr/share/perl5/Net/Server/PreForkSimple.pm

Anyone have an idea what to do from here.

help is appreciated

---

### Post by sebastjanp on 2005-09-21
Maybe it sounds stupid and nubish but in the howto you say
>  Then edit the same in the pop and ssl options, if you are going to use them. 

but I dont find those in courrier folder! Must I create them? What to write inside? Should I just copy & paste from IMAPD file?

I also dont have authmysqlrc file so I just create new one and paste in the content you supplied. Is this correct?

Sorry for my poor English.

---

### Post by majikstreet on 2005-09-21
Hi,
I am following this guide and I skipped to the testing step. When I try to telnet into my machine (from an ssh prompt btw) on port 25, I get a connection refused error. What is wrong? I don't have a firewall on the machine I don't think.

---

### Post by kozimodo on 2005-09-22
I set everything up and it seems to be mostly working (I've omitted virus and spam checking for the moment).  There seems to be an error in the authentication stage though.  In both the mail.log and the sys.log, I get
```
Sep 22 08:36:36 localhost authdaemond.mysql: authmysql: mysql_select_db(maildb ) error: Incorrect database name 'maildb '
```
Is it because IMAP is looking for 'maildb ' instead of 'maildb'?  Should I enquote the postfix configuration files that refer to maildb?

---

### Post by Avicus on 2005-09-23
OK, so I just wanna be forwarding my mail to other external accounts like gmail and hotmail. My main concern is that I don't become an open relay. 
I've followed the howto up to the amavisd part and things are working great. Is it safe for me to stop here? Or is there further things that should be done to ensure I'm safe? I've got a firewall in place too.
I've ran this test [http://www.antispam-ufrj.pads.ufrj.br/test-relay.html](http://www.antispam-ufrj.pads.ufrj.br/test-relay.html) and all tests came up clean. Is this a good/trustworthy thing?

Can I then assume that my server is just a mail forwarding server safe from open relay?

<EDIT> Typo!

Great howto btw, I've been dying to try it out and in 30 mins, its doing what I want!

---

### Post by skgu67 on 2005-09-27
I've got a strange problem.  I'm messing around w/converting my home mail server from Windows (running Mercury) to Linux.  Ivar's HOWTO was a great find and it got me up and running with virtual domains in virtually ;-) no time.

But then out of nowhere postfix suddenly started to complain that it couldn't connect to mysql -- I'd get persistent "trivial-rewrite" errors.  I wiped the machine, reinstalled, got everything running again and then -- BOOM -- same problem.  I had changed NOTHING in the various configuration files for postfix/courier/amavis/mysql between the last time things were working and when everything came crashing down.

I suspect (although I'm not 100% sure) that this is coming about because of some package that I installed after the mail server stuff -- I was messing about with webmin and also (high on my list of suspects) trying to set up a firewall.  Even the second time, I wasn't as careful as I should have been about checking after each change I made to see how things were working.  So I really can't say exactly when things went south.

Anyhow, to make a long story short, if anybody else has experienced similar problems I'd love to know about them.

Thanks,

Seth Green

---

### Post by snaga on 2005-09-29
[QUOTE=majikstreet]When I try to telnet into my machine (from an ssh prompt btw) on port 25, I get a connection refused error. What is wrong? I don't have a firewall on the machine I don't think.[/QUOTE]
I think I am having the same issue. I can send mail fine if I am on the mail server, using telnet or squirrelmail. But if I try to send mail to the mail server from another machine, it never arrives. When I telnet to port 25 on the mail server (from another machine) I get a connection refused. I am not running a firewall at this point.
Anyone have any thoughts?
dm

---

### Post by snaga on 2005-09-30
I managed to figure it out.

I edited the master.cf file in /etc/postfix/. I changed:
```
::1:smtp       inet n   -       -       -       -       smtpd
```
to 
```
smtp       inet n   -       -       -       -       smtpd
```
and commented out this line:
```
127.0.0.1:smtp inet n   -       -       -       -       smtpd
```
It worked right away after I did that (& restarted).

dm

---

### Post by majikstreet on 2005-09-30
[QUOTE=snaga]I managed to figure it out.

I edited the master.cf file in /etc/postfix/. I changed:
```
::1:smtp       inet n   -       -       -       -       smtpd
```
to 
```
smtp       inet n   -       -       -       -       smtpd
```
and commented out this line:
```
127.0.0.1:smtp inet n   -       -       -       -       smtpd
```
It worked right away after I did that (& restarted).

dm[/QUOTE]
I was able to telnet into my machine, I am going to re-run throught the tutorial now.

Thanks, I LOVE YOU!!!

---

### Post by majikstreet on 2005-09-30
Hey,
I have another issue.
I followed the guide and everything, but when I go to squirrelmail, i get "connection dropped by imap-server".

Why?

---

### Post by snaga on 2005-10-01
[QUOTE=majikstreet]
I followed the guide and everything, but when I go to squirrelmail, i get "connection dropped by imap-server".
Why?[/QUOTE]
Not exactly sure, but my suggestion would be to
```

tail -f /var/spool/mail.info
```
then watch the log as you restart all three courier scripts in /etc/init.d. If that doesn't show any errors, watch it as you try to connect with squirrelmail or some other imap client.  I was always able to find problems that way.
dm

---

### Post by dcostelloe on 2005-10-01
[QUOTE=flurdy]Going to try and answer a few questions.
Nah, there are many howtos out there which are excellent. This one is a bit Ubuntu specific in some cases.
This still a problem? check that your postfix doesnt think the machine is called localhost.localdomain.
Postfix does yes, however there is no details of this in this howto.
Dont create folders in   /var/spool/mail/virtual .
Postfix creates these properly when it receives the first mail intended for that user.
Yes, a problem I encountered as well. Hope i remembered to include it in the howto.
Since the lock file is removed and added etc, amavis needs write access to the parent folder. So /var/run/amavis needs to be owned by virtual:virtual .
Also check that    $daemon_user  = 'virtual'; and $daemon_group = 'virtual';
in the /etc/amavis/amavisd.conf.[/QUOTE]


I changed the user to amavis not virtual works good as far as Clamav and Amavis. The other alternative is to changed the boot up /etc.init.d/amavis changed $1 and $2 to virual:virtual

Hope this helps

I am having an issue with the queue not sending the mail to the mailboxes. Anyone else have this and found a fix?

---

### Post by dcostelloe on 2005-10-01
[QUOTE=snaga]Not exactly sure, but my suggestion would be to
```

tail -f /var/spool/mail.info
```
then watch the log as you restart all three courier scripts in /etc/init.d. If that doesn't show any errors, watch it as you try to connect with squirrelmail or some other imap client.  I was always able to find problems that way.
dm[/QUOTE]


Create them your self by using mailmake:

Example:

cd /var/spool/mail/virtual

maildirmake info2  
#make a directory info2 see you users mysql table look for maildr field

chown virtual.virtual info2 -R

This will not fix the issue with courier not creating the directories (still working on that) this will allow you users to access via squirrelmail.

Hope this helps

---

### Post by majikstreet on 2005-10-01
[QUOTE=snaga]Not exactly sure, but my suggestion would be to
```

tail -f /var/spool/mail.info
```
then watch the log as you restart all three courier scripts in /etc/init.d. If that doesn't show any errors, watch it as you try to connect with squirrelmail or some other imap client.  I was always able to find problems that way.
dm[/QUOTE]
$#&^#&@W$%^% There is no such file for that log... /me gives up.

---

### Post by dcostelloe on 2005-10-01
[QUOTE=majikstreet]$#&^#&@W$%^% There is no such file for that log... /me gives up.[/QUOTE]


Just a minor issue try this:

tail -f /var/log/mail.info

tail -f /var/log/mysql/mysql.log

tail -f /var/log/mail.log

I'm also working on this so if you want I can post my config files.

:razz:

See the message above on how to manually create the mail directories.

---

### Post by dcostelloe on 2005-10-02
I have gone over this many times followed the docs and mad some fixes to get things going.

Last item is postfix is not sending the mail to the mail boxes:

Here are my configurations for Postfix:

What I have: Dlink router handles all the dns etc.

Port forward of SMTP to :
Public : 35
Private: 25
Relay via sympatico

Followed the how to: 

Main.cf
# See /usr/share/postfix/main.cf.dist for a commented, more complete version

biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h
myhostname = myservername.mydomain.com

inet_interfaces = all
masquerade_domains = myservername.mydomain.com !myservername.mydomain.com
masquerade_exceptions = root
local_recipient_maps = 
mydestination =
# will it be a permanent error or temporary
unknown_local_recipient_reject_code = 450 
maximal_queue_lifetime = 16d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client relays.ordb.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org, reject_rbl_client cbl.abuseat.org
smtpd_helo_required = yes
disable_vrfy_command = yes
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
content_filter = amavis:[127.0.0.1]:10024
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_non_fqdn_recipient, reject_unauth_destination,reject, defer_if_permit
smtpd_sender_restrictions = reject_non_fqdn_sender permit_sasl_authenticated reject_unknown_sender_domain reject_unauth_pipelining permit
broken_sasl_auth_clients = yes 
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2 
smtpd_sasl_security_options = noanonymous 
smtpd_sasl_local_domain = $myhostname
mynetworks = 127.0.0.0/8,192.168.123.0/8
mynetworks_style = host
relayhost = [smtph.sympatico.ca]
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
tls_random_source = dev:/dev/urandom
# or put it an accessible smtp server 
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl/passwd
smtp_sasl_security_options = 

master.cf
======
smtp      inet  n       -       -       -       -       smtpd
	-o cleanup_service_name=pre-cleanup
cleanup unix n - - - 0 cleanup
	-o mime_header_checks= 
	-o nested_header_checks= 
	-o body_checks= 
	-o header_checks=
amavis unix - - - - 2 smtp
	-o smtp_data_done_timeout=1200 
	-o smtp_send_xforward_command=yes
127.0.0.1:10035 inet n - - - - smtpd
	-o content_filter= 
	-o local_recipient_maps= 
	-o relay_recipient_maps= 
	-o smtpd_restriction_classes= 
	-o smtpd_client_restrictions= 
	-o smtpd_helo_restrictions= 
	-o smtpd_sender_restrictions= 
	-o smtpd_recipient_restrictions=permit_mynetworks,reject 
	-o strict_rfc821_envelopes=yes 
	-o mynetworks=127.0.0.0/8,192.168.123.0/8
	-o smtpd_error_sleep_time=0 
	-o smtpd_soft_error_limit=1001 
	-o smtpd_hard_error_limit=1001
pre-cleanup unix n - - - 0 cleanup
	-o virtual_alias_maps= 
	-o canonical_maps= 
	-o sender_canonical_maps= 
	-o recipient_canonical_maps= 
	-o masquerade_domains=
pickup    fifo  n       -       -       60      1       pickup
qmgr      fifo  n       -       -       300     1       qmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      unix  -       -       -       -       -       smtp
relay     unix  -       -       -       -       -       smtp
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       n       -       -       lmtp
anvil     unix  -       -       n       -       1       anvil
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/local/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -d -t$nexthop -f$sender $recipient
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
smtpd_sasl_auth_enable=yes

Any help would be greatly appreciated

Thanks

Log reports:
Oct  2 13:49:45 localhost postfix/qmgr[6873]: 60BC28480: to=<root@localhost>, orig_to=<root@localhost.localdomain>, relay=none, delay=1, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)

All queue messages report:
(delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)
Oct  2 13:49:45 localhost postfix/qmgr[6873]: C6ED08486: to=<me@mydomain.com>, relay=none, delay=50654, status=deferred (delivery temporarily suspended: connect to 127.0.0.1[127.0.0.1]: Connection refused)

---

### Post by dms on 2005-10-03
First off I just want to say what a great HOWTO this is. I though for sure it was going to take a month to get a server up and running. There were a couple of minor stumbling blocks along the way, but I can now receive e-mail without a problem - with spam and virus protection! 

I am however having a problem sending mail through my server. I have set up SASL exactly as it was done in the guide, but I can't authenticate. When I try to send a message this gets logged in /var/log/auth.log:

sql couldn't connect to any host

In the mysql logs it shows some sort of connection attempt, with the right username and database, but that's it. I'm still pretty new to all this and i'm not sure how to turn on more verbose logging of mysql, but it looks to me like there is a connection attempt. 

In my /var/log/mail.info I am seeing two different errors depending on how I try to authenticate. If I use CRAM-MD5 I see something along the following lines (sorry i don't have the exact logs, still don't have remote access set up on my box):

postfix:smtpd - SASL Authentication failed: No secret in database

If I use PLAIN the error is: 

postfix:smtpd - SASL Authentication failed: Password verification failure

I've tried searching for all of these errors to no avail. I did come across another post of someone having the exact same problem after following this guide, but nobody got back to them. I think one of the errors is probably misleading, but like said I'm still very new to all this (including Linux in general) so I'm not sure which one. Any help would be greatly appreciated. I should be able to post more from my logs and configs later if needed. 
Thanks in advance

---

### Post by snaga on 2005-10-05
I have a better email server now than I've ever had...thanks.

I do have some other things that I want to do, that I'm wondering if I can get some pointers for.

1. I am passing the spam through instead of filtering it out. I'd like to have it append  ****SPAM**** to the subject. I can't seem to figure out how to do that. I've made all the adjustments in spamassassin and avamis that I can find, but it doesn't seem to work.

2. Ideally I would like to automatically deliver spam to my junk folder before I even see it in the client. This would be nice for when I use squirrelmail. I'm not sure how to do that. Do I need procmail? Not sure. Email is still about 50% voodoo to me.

thanks

dm

---

### Post by dms on 2005-10-07
I rebuilt my server and the SASL problems have gone away...of course now TLS doesn't seem to be working, but I haven't had a chance to take a look as to why....

Snaga-
I had a similar problem. I know I uncommented the ****SPAM**** line in both my spamassassin local.cf and in amavis.conf. I also set my tag_level to -999. Also, in the HOWTO this line in amavis.conf is set 
@local_domains_acl = qw(); I left the default and now have spam headers attached to all messages, as well as the subject line change. Not sure about your second question as I am wondering the same thing.

---

### Post by Stryker777 on 2005-10-11
Works like a charm.  I did have to manually create directories for the users but that is easy enough.  Thanks for the info!  
Stryker777

---

### Post by dcostelloe on 2005-10-15
Ok I'm a little angry right now so this is not as a result of this how to:

I upgradr to brezzy and well a new install had to be done as packages like postfix started errors and webmin/squirrelmail error error error

To make a long story short I have everything in place for virtual mail as per the how to... Thank you Flurdy!

Problem with Breezy:

can't get these two libraries:

libsasl7
libsasl-modules-plain

So my virtual mail ain't working.

Question: Is there a way to get around this issue as my validation is returning an error all the time for my mail. No one can get validated!

I have to setup a re-route in order to read mail.

Thanks
Need Help!

Getting very frustrated with the impact to my mail system.

---

### Post by t_ras on 2005-10-16
I don't seem to have postfix-tls in apt-get.
using 5.10 on ADM64.
any Ideas?

---

### Post by t_ras on 2005-10-16
[QUOTE=t_ras]I don't seem to have postfix-tls in apt-get.
using 5.10 on ADM64.
any Ideas?[/QUOTE]

did it manulay...

---

### Post by t_ras on 2005-10-16
no cant find libsasl7...:(

---

### Post by t_ras on 2005-10-16
[QUOTE=dcostelloe]Ok I'm a little angry right now so this is not as a result of this how to:
....

can't get these two libraries:

libsasl7
libsasl-modules-plain
...[/QUOTE]

(also php4-universe-common)

as far as I could check this packages are not avilable for AMD64 and since they seem to be old I guess no one will port them.

Any other options?

---

### Post by sincklation on 2005-10-19
[QUOTE=thomask]I also thought this was a great guide, though I do not really need multiple domains or antivirus or spam. I am just trying to set up an intranet webmail/email server on a closed (no internet access) LAN...

I also have had a lot of problems with it not recognizing a user, even though I created several via phpmyadmin, and I am pretty fluent with it as I deal with osCommerce, phpbb, coppermine, as well as other php scripts.

You would think there would be a simple way to configure email, as long as it has been around. Photo galleries suprise me with their ease of install and configuration, considering all of the features they have. Why can't email be as simple?

My main user account, mail as well as my other account, thomas, are not being recognized by the squirrelmail or IMAP, as I configured my outlook on a windows box to log in and access it, tried many username/pw combinations to no use. I tried the debug part of the guide, but maybe my version of ubunu has things in different spots, the first time i try:

/etc/init.d/courier stop

it errors out.. and there is no listing for courier in that directory, so wtf? did i screw something up on the install?

I am only thinking of uninstalling the whole mess and starting over.

anybody else have a similar prob?[/QUOTE]

i have the same problem and i follow step by step the howto, someone can help ?

in init.d i got this that match courier
courier-authdaemon
courier-imap
courier-imap-ssl

---

### Post by dms on 2005-10-21
Has anyone ubgraded to Breezy after going through this guide? Anything stop working? Any tweaks to look out for? I'm running it now on my laptop, but if that breaks I'm won't be too upset. Thanks for any advice.

---

### Post by Stryker777 on 2005-10-22
The only issue I have on breezy is there is not a postfix-tls for postfix 2.4.4 in breezy so tls wont work.  Other than that, I was able to get everything going. 

Also for Snaga,
I wanted all the spam headers in and had to set
@local_domains_acl = qw();  to my local domains.
ex. 
```

@local_domains_acl = ( ".$mydomain", ".domain1.org", ".domain2.com", ".domain3.net" );

```
and dont forget to set $sa_tag_level_deflt stuff.
ex.
```

$sa_tag_level_deflt  = 0.0; # add spam info headers if at, or above that level
$sa_tag2_level_deflt = 6.3; # add 'spam detected' headers at that level
$sa_kill_level_deflt = $sa_tag2_level_deflt; # triggers spam evasive actions
                           # at or above that level: bounce/reject/drop,
                           # quarantine, and adding mail address extension

$sa_dsn_cutoff_level = 10;  # spam level beyond which a DSN is not sent,
                            # effectively turning D_BOUNCE into D_DISCARD;
                            # undef disables this feature and is a default;

```

---

### Post by flurdy on 2005-10-26
Again, Im going to try and reply to comments here, especially the ones directed to me. The good thing about this forum is many other people are chipping in, (especially as i tend to be slow to reply... )

[QUOTE=alfmatos]A few suggestions:
server side mail rules , configurable via squirrelmail (this requires maildrop i think, i'm still strugling with maildrop on ubuntu) - this is the feature i'm really trying hard to get working.
[/QUOTE]

Im not looking in to maildrop, but if someone has a good link, especially if it works seamlessly with my howto then ill put a link in bold to it.

> 
postfixadmin - really comes in handy when administration is required


What is the experience people have with this? Does it integrate seamlessly or do you have to tweak some settings, or the db?

> 
mysql change - move from mysql tcp access to the the sock , this is fairly easy to do, and safer.



True, socket based is safer, and I may change the howto to use it.

> 

Question : what are the tables for when setting up squirellmail ?



To store addresses and preferences per user.

> 
I dindn't follow you're guide, but it's very good. I followed similar one's, but i guessed you already read them, since the similarities are remarkable :)

Anyways, great job. If you need help on the proposed addons, talk to me, i can lend you some words and steps to configure.

Yup, all the postfix howtos seem to be mix of each other.  You learn from others, improve upon it and then teach others whom go on to keep this cycle going.

---

### Post by flurdy on 2005-10-26
[QUOTE=olpe]Thank you for great howto! I did everything by the howto and everything worked fine until I checked mail.info for the first time. it is full of  

localhost postfix/qmgr[9255]: warning: connect to transport smtp: Connection refused 

warnings. Any idea how to fix this?

I get connection with telnet localhost 25. Squirrelmail is working (but of course not the sending/recieving thing) so I pretty much think that it is only a postfix problem.[/QUOTE]

Could be several things. Not running as root, sendmail or another postfix process is already running and holding onto port 25. Check master.cf for permissions, try not using chroot to see if it is a permission problem. 

Is it still a problem?

---

### Post by flurdy on 2005-10-26
[QUOTE=Ubuntunub]Hello everyone,

I am a nub when it comes to linux or mail servers :-). I have a question about the mailserver. When you set up the mailserver you can create e-mail adresses for use within your lan. But can other external people also mail to you? Because my pc has a dynamic ip.

thanx in advance[/QUOTE]

Other people can mail to you if you want to. However you will then have to use a dynamic dns service, eg. dyndns.org etc.

---

### Post by flurdy on 2005-10-26
[QUOTE=cllsr]I have already done that the problem is when Amavis starts it checks permissions on the directory and automatically changes uid and gid back to amavis:amavis. I am still looking for an answer.

Here is the log entry I keep getting.
root@scorpion:/home/chris # /etc/init.d/amavis stop
Stopping amavisd: amavisd-new.
root@scorpion:/home/chris # /etc/init.d/amavis start
Starting amavisd: mode of `/var/run/amavis' changed to 0755 (rwxr-xr-x)
Pid_file "/var/run/amavis/amavisd.pid" already exists.  Overwriting!
amavisd-new.

Here is the lock file error.

Sep 17 11:41:54 localhost amavis[9842]: Net::Server: 2005/09/17-11:41:54 Couldn't open lock file "/var/run/amavis/amavisd.lock" [Permission denied]\n  at line 239 in file /usr/share/perl5/Net/Server/PreForkSimple.pm

Anyone have an idea what to do from here.

help is appreciated[/QUOTE]


I actually fudged the /etc/init.d/amavis file line 31ish, and changed it to always set the owner to virtual:virtual

---

### Post by flurdy on 2005-10-26
[QUOTE=sebastjanp]Maybe it sounds stupid and nubish but in the howto you say
 

but I dont find those in courrier folder! Must I create them? What to write inside? Should I just copy & paste from IMAPD file?

I also dont have authmysqlrc file so I just create new one and paste in the content you supplied. Is this correct?

Sorry for my poor English.[/QUOTE]

Sounds like you have not installed the courier-imap-ssl package nor the courier-imap-authmysql package.

---

### Post by flurdy on 2005-10-26
[QUOTE=majikstreet]Hi,
I am following this guide and I skipped to the testing step. When I try to telnet into my machine (from an ssh prompt btw) on port 25, I get a connection refused error. What is wrong? I don't have a firewall on the machine I don't think.[/QUOTE]

Either your or your isps firewall is blocking port 25, or there is nothing listening on port 25.

Do netstat -pln on your mails server to confirm something is listening on port 25.

Then try telnet from you mail server to itself on port 25 to confirm what responses to expect.

If all okay so far then postfix is responding okay.

Then try from another machine, if this does not work then it is a firewall issue

---

### Post by flurdy on 2005-10-26
[QUOTE=kozimodo]I set everything up and it seems to be mostly working (I've omitted virus and spam checking for the moment).  There seems to be an error in the authentication stage though.  In both the mail.log and the sys.log, I get
```
Sep 22 08:36:36 localhost authdaemond.mysql: authmysql: mysql_select_db(maildb ) error: Incorrect database name 'maildb '
```
Is it because IMAP is looking for 'maildb ' instead of 'maildb'?  Should I enquote the postfix configuration files that refer to maildb?[/QUOTE]


Yup, you need to be carefull with extra spaces at the end of the lines. Edit couriers authmysql file and check for no spaces after the db name

---

### Post by flurdy on 2005-10-26
[QUOTE=Avicus]OK, so I just wanna be forwarding my mail to other external accounts like gmail and hotmail. My main concern is that I don't become an open relay. 
I've followed the howto up to the amavisd part and things are working great. Is it safe for me to stop here? Or is there further things that should be done to ensure I'm safe? I've got a firewall in place too.
I've ran this test [http://www.antispam-ufrj.pads.ufrj.br/test-relay.html](http://www.antispam-ufrj.pads.ufrj.br/test-relay.html) and all tests came up clean. Is this a good/trustworthy thing?

Can I then assume that my server is just a mail forwarding server safe from open relay?

<EDIT> Typo!

Great howto btw, I've been dying to try it out and in 30 mins, its doing what I want![/QUOTE]

If you have followed the howto so far then it should not be an open relay.

You may want to tie it down further with more secure authentication, encryption and chrooting etc.

---

### Post by flurdy on 2005-10-26
[QUOTE=snaga]I managed to figure it out.

I edited the master.cf file in /etc/postfix/. I changed:
```
::1:smtp       inet n   -       -       -       -       smtpd
```
to 
```
smtp       inet n   -       -       -       -       smtpd
```
and commented out this line:
```
127.0.0.1:smtp inet n   -       -       -       -       smtpd
```
It worked right away after I did that (& restarted).

dm[/QUOTE]

Hmm, havent seen the 127 line before, but obviously it would stop anyone else connecting to you machine. cheers.

---

### Post by flurdy on 2005-10-26
[QUOTE=dcostelloe]I changed the user to amavis not virtual works good as far as Clamav and Amavis. The other alternative is to changed the boot up /etc.init.d/amavis changed $1 and $2 to virual:virtual

Hope this helps

I am having an issue with the queue not sending the mail to the mailboxes. Anyone else have this and found a fix?[/QUOTE]

Yup, think I need to include thus specifc fudge in my howto

---

### Post by flurdy on 2005-10-26
[QUOTE=dcostelloe]Create them your self by using mailmake:

Example:

cd /var/spool/mail/virtual

maildirmake info2  
#make a directory info2 see you users mysql table look for maildr field

chown virtual.virtual info2 -R

This will not fix the issue with courier not creating the directories (still working on that) this will allow you users to access via squirrelmail.

Hope this helps[/QUOTE]

Not sure if id recommened to manually create them, even if mailmake creates a valid dir file structure.

Best to let postfix create it, it is a simple way to verify postfix is working.

---

### Post by flurdy on 2005-10-26
[QUOTE=majikstreet]$#&^#&@W$%^% There is no such file for that log... /me gives up.[/QUOTE]

No such file? Then postfix is not running.  or not installed.

---

### Post by cybergypsy on 2005-10-27
Hi All

Thanks for getting this procedure sorted , but after trying for almost 30 hours to get MySQL authentication working , I am getting this in /var/log/syslog :-

<code>
Oct 27 10:10:10 ubuntu imaplogin: LOGIN: DEBUG: ip=[::ffff:192.168.0.37], command=CAPABILITY
Oct 27 10:10:10 ubuntu imaplogin: LOGIN: DEBUG: ip=[::ffff:192.168.0.37], command=LOGIN
Oct 27 10:10:10 ubuntu imaplogin: LOGIN: DEBUG: ip=[::ffff:192.168.0.37], username=mark
Oct 27 10:10:10 ubuntu imaplogin: LOGIN: DEBUG: ip=[::ffff:192.168.0.37], password=XXmy_passwordXX
Oct 27 10:10:10 ubuntu imaplogin: authdaemon: starting client module
Oct 27 10:10:10 ubuntu authdaemond.mysql: received auth request, service=imap, authtype=login
Oct 27 10:10:10 ubuntu authdaemond.mysql: authmysql: trying this module
Oct 27 10:10:10 ubuntu authdaemond.mysql: SQL query: SELECT id, "", clear, uid, gid, home, concat(home,'/',maildir), "", name, "" FROM users WHERE id = "mark" AND (enabled=1)
Oct 27 10:10:10 ubuntu authdaemond.mysql: zero rows returned
Oct 27 10:10:10 ubuntu authdaemond.mysql: no password available to compare
Oct 27 10:10:10 ubuntu authdaemond.mysql: authmysql: REJECT - try next module
Oct 27 10:10:10 ubuntu authdaemond.mysql: FAIL, all modules rejected
Oct 27 10:10:10 ubuntu imaplogin: authdaemon: REJECT
</code>

Authentication works fine via PAM if set in /etc/courier/authdaemonrc

Any ideas ?

Thanks
mark

---

### Post by nocturn on 2005-10-27
I switched from Amavis to mailscanner, much easier and cleaner IMO

---

### Post by jbinc1 on 2005-11-02
Do you have to use Shorewall with this setup, or will any firewall work? I'm totally new to setting up a firewall, let alone a mail server. I'm trying to figure out getting a mail server up and running so I can start serving my own mail once the contract with my current mail server is up. Any help will be greatly appreciated.

---

### Post by dcostelloe on 2005-11-02
Authentication works fine via PAM if set in /etc/courier/authdaemonrc

Any ideas ?

Thanks
mark[/QUOTE]


Hi Mark,
I think you will need to use a full email address as the ID = [email]mark@yourdomain.com[/email]

:cool:

---

### Post by cybergypsy on 2005-11-04
**dcostelloe** - thanks , got it working now with my domain name , it also worked before without the domain name but I had to update */etc/courier/authmysqlrc* with :-

DEFAULT_DOMAIN                my-domain.goes-here.tld

**jbinc1** - you don`t need to have shorewall on this email server if it is inside your LAN and protected by an alternative firewall (mine is behind my [smoothwall]("http://smoothwall.org/")) , but if its internet-facing you probually should.
The way postfix is setup here is good as it rejects attempts to be used as a spam relay.

**nocturn** - good call with mailscanner - thanks! , I tried for a few *days* to get clamav working with postfix to no avail , mailscanner was working in *minutes*. Now I just need some spam and viruses sent to me ;)

---

### Post by jbinc1 on 2005-11-04
Thanks cybergypsy. I can see I have a lot more reading and testing to do. I understand the basic concept but I'm still not too sure about some of the particulars.:smile:

---

### Post by jbinc1 on 2005-11-04
Thanks cybergypsy. I can see that I have a lot more research to do.:smile:

---

### Post by flurdy on 2005-11-10
[QUOTE=dms]Has anyone ubgraded to Breezy after going through this guide? Anything stop working? Any tweaks to look out for? I'm running it now on my laptop, but if that breaks I'm won't be too upset. Thanks for any advice.[/QUOTE]


I havent upgraded to breezy, but will have to soon, as it is the reason for the [4th edition of the howto]("http://flurdy.com/docs/postfix/edition4.html"). Currently just updating tiny general stuff in the wain chance Ill get an evening free before xmas....

Will then have to create a thread in the 5.10 forums, as presume less and less people read the hoary forums.

People with Breezy, is there really no postfix-tls and libsasl7 packages ?
Is there a work around? Does postfix come with tls in the main package perhaps?

And people: install postgrey, it removes virtually all spam. The only spam that trickles through before spamassassin gets at it is ones that uses backup mx's if they dont have postgrey installed.

---

### Post by TravisNewman on 2005-11-10
Flurdy,
wow. Very thorough howto! I'd like to give you my situation and see if you can give me a hand here.

When I was at college, the UNIX servers were set up so that the mail you'd read when you go into mutt, pine, etc, in the computer labs were the same ones you'd get by using their pop3 server. Basically, [email]user@college.edu[/email] was public and internal on the UNIX systems.

I've found a howto for getting email added to the UNIX mailbox (the same one that gives you updates on what you've installed and such) from pop3, imap, and gmail, and I'd like to connect that to this howto.

Basically, setting up an IMAP server that will use a cron job to run fetchmail every 10 minutes for my wife and myself, download everything there, and then we can log in using any IMAP capable mail client or the webmail interface and access all of our mail, folder structure intact. We both work with many different computers and many different email accounts, and this would simplify things immensely.

From what I'm reading, I imagine that a large part of the howto would be different, just wondering if you have any experience with this kind of thing and can help out of point me somewhere that can.

---

### Post by flurdy on 2005-11-11
What you describe is a plain Unix mail/maildir way of accessing email. Where you mail spool and authentication is worked of from the local user . 

This howto uses virtual users, however still uses normal unix maildir format. 

What I can gather is that you want imap and webmail interface to you email and that you dont need smtp but will gather your email via fetchmail.

This howto does provide an imap and webmail interface so it is accesible and the same from wherever you connect. This is done with the courier and squirrelmail sections.

The main difference is that you dont really need postfix to receive email, but you probaly still need it to send email?

As for fetchmail I hope some other people can assist whether it can be used with virtual users or not? 

Some previous posts discribe how to create the mail dirs if postfix is not needed at all.

---

### Post by TravisNewman on 2005-11-11
so can I just skip the virtual users part and not use mysql at all then?

---

### Post by Ventajou on 2005-11-14
Hi,

Thanks very much for the howto, thanks to you I have a working email server!
There is just one more thing I'd like to be able to do.

I have created an account for my daughter but I'd like to have a way to filter the messages she receives. Basically I'd like to have a list of people who can send her emails. It could even be from her address book. How would I go about implementing that?

Thanks.

---

### Post by Tsurara on 2005-11-16
First, wonderful guide. It was a very easy read and I got everything working in an afternoon over a few (too many) beers.

I have everything running except one thing: I can't authenticate users at all. Would this be more of a database problem? How are the usernames entered? Is there anything other than myphpadmin to manage the database with perhaps an easier learning curve?

Thanks. Sorry if I am not being descriptive, I am somewhat new to E-Mail servers and Linux in general, so if you guys could point me at some logs I should post... I will do that right away.

Thanks again

---

### Post by WetWilly on 2005-11-16
Looking forward to see the complete 4th edition.

Maybe you would like to add [http://www.roundcube.net/](http://www.roundcube.net/) instead of squirrelmail.

Cause Roundcube sure looks hawt!!!

---

### Post by cybergypsy on 2005-11-17
**Tsurara** - instead of phpmyadmin which just allows control of mysql , why not have a look at Webmin ?

```
apt-cache search webmin
``` show lots of modules , you will need to do a ```
sudo apt-get install webmin
``` and ```
sudo apt-get install webmin-mysql
``` at a minimum.
This will setup a secure web interface on [https://server:10000](https://server:10000) , just point your browser there , login as root and off you go. :razz: 

By installing some of the other webmin modules you can control other parts of your server. I use the DHCP , DNS and Samba modules all the time , then sneak back to the text config files and see how things have changed - just another way of learning ;) 

good luck
cybergypsy

---

### Post by Tsurara on 2005-11-17
[QUOTE=cybergypsy]webmin stuff[/QUOTE]

Thanks a lot for the info :) !

---

### Post by Florent on 2005-11-18
Hi and many thanks for this helpfull howto :) 

I have one question regarding Postfix configuration (I've never setup a mail server):
It says that >  First set your server name, this must match what you put in your domains DNS MX records.
```
myhostname = server.yourdomain.com
```

I thought it was for multiple domain names.

Which one should I use in this setting ?

Thanks

---

### Post by Florent on 2005-11-21
Hi,

another remark on your great how-to (I still did not have the time to complete the installation). On the SquirrelMail/Apache2 section, you wrote:
```
ln -s /etc/apache2/sites-available/webmail /etc/apache2/sites-enabled/810-webmail
```

I think the prefered way to enable and disable sites is to use the following commands:
[LIST]
[*]a2ensite
[*]a2dissite
[/LIST]
 and that's the same for modules : a2enmod/a2dismod

here is a reference page with all the explanations: [http://www.debian-administration.org/articles/207](http://www.debian-administration.org/articles/207)

---

### Post by Tsurara on 2005-11-21
Ok, well I got my MYSQL database working, but I still can't log into my server... every time I put in my username/pass I get "Login to server xxx.xxx.xxx failed"

Any ideas as to what might not be working?

---

### Post by flurdy on 2005-11-21
[QUOTE=Tsurara]Ok, well I got my MYSQL database working, but I still can't log into my server... every time I put in my username/pass I get "Login to server xxx.xxx.xxx failed"

Any ideas as to what might not be working?[/QUOTE]

Does the log output the correct username: eg [email]yourname@yourdomain.com[/email] and password?

If so then what does the sql log say?

---

### Post by Tsurara on 2005-11-23
[QUOTE=flurdy]Does the log output the correct username: eg [email]yourname@yourdomain.com[/email] and password?

If so then what does the sql log say?[/QUOTE]

EDIT: Ok, answered my own question, I think I have got imap working :) Thanks!

Ok new issue though, when I try to send myself mail I get this:

```

Nov 23 11:59:21 localhost postfix/smtpd[11950]: connect from zproxy.gmail.com
Nov 23 11:59:24 localhost postfix/smtpd[11950]: NOQUEUE: reject: RCPT from zproxy.gmail.com: 554 <tsurara@tsuraradomain.com>: Relay access denied; from=<myotheremail@gmail.com> to=<tsurara@tsuraradomain.com> proto=ESMTP helo=<zproxy.gmail.com>
Nov 23 11:59:24 localhost postfix/smtpd[11950]: disconnect from zproxy.gmail.com

```

Any ideas?

---

### Post by pcolomes on 2005-11-23
Hi
I'm getting this mistake on my server. This occurs when I try to login via squirrelmail.
It' seems that postfix isn't creating the subdirectories for users.
I tried to make them manually but I had another kind of problems

```
root@webserver:/var/spool/mail/virtual #    ls
test
root@webserver:/var/spool/mail/virtual #
```
("test" it's the folder i've created manually).

```
Nov 23 16:22:38 webserver imaplogin: authdaemon: ACCEPT, username pcolomes@electrored.net
Nov 23 16:22:38 webserver imaplogin: chdir /var/spool/mail/virtual/pcolomes/: No such file or directory

```
Off course I have added pcolomes to mysql database

How do I fix this? I would like to know what part of the config files is the one who creates the folders on the system?
I'm really desperated.
Thanks

---

### Post by Florent on 2005-11-24
[QUOTE=pcolomes]It' seems that postfix isn't creating the subdirectories for users. I tried to make them manually but I had another kind of problems

[...]

How do I fix this? I would like to know what part of the config files is the one who creates the folders on the system?
[/QUOTE]

Did you use mkdir or maildirmake to create users sub directories ?
Have a look at [this post]("http://ubuntuforums.org/showpost.php?p=444216&postcount=72").

Even if maildirmake is not recommended by the howto author, it does the trick for me and I still did not find why postfix would not create them on my machine. postfix seems well configured. I can post my main.cf if someone would help finding the error.

---

### Post by pcolomes on 2005-11-24
Ok Now I've found how to deal with the NON-WORKING directories.
As I was reading somewhere, then someone said when the first mail it's received then postfix will automatically create subfolders.

I tried sending from my gmail account but nothing happened
So I had to send myself mails to all accounts I've created in the users database.

run in console window as root (sudo su) 
- tail -f /var/log/mail.info
then in another console window run
- sudo telnet -d 127.0.0.1 25 [ -d option will activate debug ]
mail from: <ANYUSER@YOURDOMAIN.COM> [it has to be your domain, otherwise it will not work. also it wont work using @localhost]
- rcpt to: <USER1@YOURDOMAIN.COM> [here write the 1st email address you want to "activate". for example: [email]info@hello.com[/email]]
- data
- write anything lalalal lalala lalala [press Intro to next line and write a dot "." to finish data]
- .
- ok queued as xxxxxxx

repeat this process with all users on your database. What a mess uh? I haven't found another way to it.

---

### Post by Florent on 2005-11-24
[QUOTE=pcolomes]Ok Now I've found how to deal with the NON-WORKING directories.
[...]
repeat this process with all users on your database. What a mess uh? I haven't found another way to it.[/QUOTE]

Using maildirmake does the trick for me and it's much more simpler. But It's nice that you finally find a solution that fits for you ;)

---

### Post by pcolomes on 2005-11-25
First, sorry for this extensive post, and thanks for anyone who answers it ;)

Ok, I have solved the first problem but I have 3 more things wich are making me little sick.
The first is a squirrelmail config problem (it seems to). I have configured all ok runing conf.pl script. Everything works ok except language. I need to change it to SPANISH. Ok, so on config menu I select language option es_CL (CL from Chile)

```

SquirrelMail Configuration : Read: config.php (1.4.0)
---------------------------------------------------------
Language preferences
1.  Default Language       : es_CL
2.  Default Charset        : UTF-8
3.  Enable lossy encoding  : false

R   Return to Main Menu
C   Turn color on
S   Save data
Q   Quit

Command >>

```
after that I run l /usr/sbin/locale-gen to generate the squirrelmail locales language files.
```

root@webserver:/ # locale-gen
Generating locales...
  es_CL.UTF-8... done
  en_DK.UTF-8... done
  es_ES.UTF-8... done
  es_US.UTF-8... done
  es_CL.ISO-8859-1... done
  en_GB.ISO-8859-1... done
  en_GB.ISO-8859-15... done
  en_US.ISO-8859-1... done
  en_US.ISO-8859-15... done
  es_ES.ISO-8859-1... done
  es_ES.UTF-8@euro... done
  es_US.ISO-8859-1... done
Generation complete.
root@webserver:/ #

``` 
and restart apache. 
After this I could change english language to spanish but when I enter squirrelmail ([http://host/src/login.php](http://host/src/login.php)) and I select options - display preferences - language I can see just the main window is in new language and the left_main.php still is in english.
So, if I try to send email just after press SEND button, squirrelmail interface changes to spanish, and if I press SEND again it returns to english. 
Why is this happening?

so, problem number 2) sending and receving mail from web interface seems ok. But when I try to use outlook (for example) from another network I can email only to my domain mailboxes (mail@domain.net, [email]pcolomes@domain.net[/email], [email]admin@domain.net[/email] etc). Every mail i send via mail client returns with the message: Denied Relay
So on my mail.warn this is appearing constantly
```

Nov 25 16:26:53 webserver postfix/smtpd[5896]: warning: smtpd_sasl_auth_enable is true, but SASL support is not compiled in
Nov 25 16:26:54 webserver postfix/smtpd[5896]: warning: restriction `permit_sasl_authenticated' ignored: no SASL support


``` 

I have to say have followed step by step 4 times all the HowTO but still cannot make it run. 
"smtpd_sasl_auth_enable is true, but SASL support is not compiled in" --> How can i make SASL be compiled to run with postfix? I have installed the following packages with apt-get install (before it, i've upgraded the repositories)
```

      postfix
      postfix-mysql
      postfix-tls
      libsasl2
      libsasl2-modules
      libsasl-modules-plain
      libsasl2-modules-sql
      libsasl7
      libauthen-sasl-perl
     libauthen-sasl-cyrus-perl

```
Note: /etc/postfix/sasl/smtpd.conf, /etc/postfix/main.cf, /etc/postfix/master.cf are written exactly as this howto: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
Even so I can't use my mailserver from outside because SASL authentication isn't working.. :(
-----------

And the last problem/question is about MX records in DNS zone.
mail.warn:
```

Nov 25 16:40:01 webserver postfix/smtp[6210]: warning: no MX host for mail.domain.net has a valid A record
Nov 25 16:40:02 webserver postfix/smtp[6210]: warning: no MX host for mail.domain.net has a valid A record

``` 
(domain.net it's fake, ;) )

dig my domain:
```

root@webserver:/ # dig mail.domain.net

; <<>> DiG 9.2.4 <<>> mail.domain.net
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 47774
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;mail.domain.net.           IN      A

;; ANSWER SECTION:
mail.domain.net.    166263  IN      A       200.55.215.62

;; AUTHORITY SECTION:
domain.net.         155889  IN      NS      dns1.XXX.com.
domain.net.         155889  IN      NS      dns2.XXX.com.

;; ADDITIONAL SECTION:
dns1.XXX.com.     148958  IN      A       213.229.XXX.XXX
dns2.XXX.com.     148958  IN      A       195.160.XXX.XXX

;; Query time: 24 msec
;; SERVER: 200.75.0.4#53(200.75.0.4)
;; WHEN: Fri Nov 25 17:17:07 2005
;; MSG SIZE  rcvd: 136

root@webserver:/ #

```

and my dns zone file says this:
```

mail  	   	IN  	A  	200.55.215.62
@  	   	IN  	MX  	10 mail.domain.net.
mail  	   	IN  	MX  	10 mail.domain.net.

```

Is this right MX record config? if doesn't, how must I write my MX records?

Sorry for extense but I've been more than 4 days working on this and nothing !
Any help would be apreciated

---

### Post by pcolomes on 2005-11-25
OK, i have answered myself again jejeje
the problem I had with SASL was HALF-solved by reinstalling postfix-tls package
I say HALF-solved because now i've eliminated the SASL warning but still I'm getting this:
```

Nov 25 17:46:52 webserver postfix/smtpd[7738]: connect from inet.electrored.net[200.55.215.61]
Nov 25 17:46:52 webserver postfix/smtpd[7738]: NOQUEUE: reject: RCPT from inet.electrored.net[200.55.215.61]: 554 <xxx@codiner.cl>: Relay access denied; from=<xxx@electrored.net> to=<xxx@codiner.cl> proto=ESMTP helo=<PAULO>
Nov 25 17:46:54 webserver postfix/smtpd[7738]: disconnect from inet.electrored.net[200.55.215.61]

```

---

### Post by cllsr on 2005-11-29
> **pcolomes]OK, i have answered myself again jejeje
the problem I had with SASL was HALF-solved by reinstalling postfix-tls package
I say HALF-solved because now i've eliminated the SASL warning but still I'm getting this:
```

Nov 25 17:46:52 webserver postfix/smtpd[7738]: connect from inet.electrored.net[200.55.215.61]
Nov 25 17:46:52 webserver postfix/smtpd[7738]: NOQUEUE: reject: RCPT from inet.electrored.net[200.55.215.61]: 554 <xxx@codiner.cl>: Relay access denied said:**
> : disconnect from inet.electrored.net[200.55.215.61]

```


Are you sure you have these Cyrus packages installed.
#
Cyrus SASL:

    *
      libsasl2
    *
      libsasl2-modules
    *
      libsasl-modules-plain
    *
      libsasl2-modules-sql
    *
      libsasl7
    *
      libauthen-sasl-perl
    *
      libauthen-sasl-cyrus-perl

---

### Post by dcostelloe on 2005-11-29
I am ready to try agin to upgrade to breezy from Hoary. Last time I experienced issue with the mail server setup etc.

Has anyone managed to setup with breezy?

If so what things will I need to mainatin the Mail setup to Breezy.


Thanks

---

### Post by Stryker777 on 2005-11-30
[QUOTE=pcolomes]
and my dns zone file says this:
```

mail  	   	IN  	A  	200.55.215.62
@  	   	IN  	MX  	10 mail.domain.net.
mail  	   	IN  	MX  	10 mail.domain.net.

```
[/QUOTE]

This is probably going to sound silly but it was the case with mine.  When you do your mx, put it above all your a records just under your ns records.  My isp was seeing my mx as a subdomain thus the change.  Now my mx works properly.  Just move up the mx there.  Also you have 2 10s.  since both mx records go to the same place, just use one mx 10.  Mail servers will lookup your domain name for mx so whether your A is mail or jeepers one mx will work.  If you have a secondary mx us mx 20 mail2.domain.net. or something like that.
Stryker777

ex.
```

			NS	ns1.domain.net.
			NS	ns2.domain.net.
                        MX  	   10 mail.domain.net.
mail  	   	      A  	   200.55.215.62

```

---

### Post by lorenco on 2005-11-30
[QUOTE=dcostelloe]I am ready to try agin to upgrade to breezy from Hoary. Last time I experienced issue with the mail server setup etc.

Has anyone managed to setup with breezy?

If so what things will I need to mainatin the Mail setup to Breezy.


Thanks[/QUOTE]
Yip,  you will have some troubles. I am having some. 

Nov 30 18:01:33 mail postfix/master[13361]: daemon started -- version 2.2.4, configuration /etc/postfix
Nov 30 18:01:33 mail postfix/pickup[13364]: ...
Nov 30 18:01:33 mail postfix/cleanup[13366]: warning: connect to mysql server localhost: Can't connect to local MySQL server through socket /var/run/mysqld/mysqld.sock' (2)
Nov 30 18:01:33 mail postfix/cleanup[13366]: warning: 24FF7xxxx: virtual_alias_maps map lookup problem for xxx
Nov 30 18:01:33 mail postfix/pickup[13364]: warning: maildrop/6690113xxx: Error writing message file


But will keep you posted...

---

### Post by flurdy on 2005-11-30
> **pcolomes]OK, i have answered myself again jejeje
the problem I had with SASL was HALF-solved by reinstalling postfix-tls package
I say HALF-solved because now i've eliminated the SASL warning but still I'm getting this:
```

Nov 25 17:46:52 webserver postfix/smtpd[7738]: connect from inet.electrored.net[200.55.215.61]
Nov 25 17:46:52 webserver postfix/smtpd[7738]: NOQUEUE: reject: RCPT from inet.electrored.net[200.55.215.61]: 554 <xxx@codiner.cl>: Relay access denied said:**
> : disconnect from inet.electrored.net[200.55.215.61]

```

codiner.cl is not in your virtual domains list ?

---

### Post by N6REJ on 2005-11-30
Its pre-included in the postfix main file....
Package: postfix
Priority: optional
Section: mail
Installed-Size: 2140
Maintainer: LaMont Jones <lamont@debian.org>
Architecture: i386
Version: 2.2.4-1ubuntu2
Replaces: postfix-doc (<< 1.1.7-0), postfix-tls
Provides: mail-transport-agent, postfix-tls
Depends: libc6 (>= 2.3.4-1), libdb4.2, libsasl2 (>= 2.1.19), libssl0.9.7, debconf (>= 0.5) | debconf-2.0, netbase, adduser (>= 3.48), dpkg (>= 1.8.3), lsb-base (>= 1.3-9ubuntu3)
Recommends: mail-reader, resolvconf
Suggests: procmail, postfix-mysql, postfix-pgsql, postfix-ldap, postfix-pcre
Conflicts: mail-transport-agent, smail, libnss-db (<< 2.2-3), postfix-tls
Filename: pool/main/p/postfix/postfix_2.2.4-1ubuntu2_i386.deb
Size: 910878
MD5sum: 4b6c5c034d750e894d6f198e6c2f2256
Description: A high-performance mail transport agent
 Postfix is Wietse Venema's mail transport agent that started life as an
 alternative to the widely-used Sendmail program.  Postfix attempts to
 be fast, easy to administer, and secure, while at the same time being
 sendmail compatible enough to not upset existing users. Thus, the outside
 has a sendmail-ish flavor, but the inside is completely different.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by flurdy on 2005-12-02
I created a new thread in the breezy customize forums as I ve updated the howto to edition 4 to cater for Breezy Badger

[Click here to read the new thread]("http://ubuntuforums.org/showthread.php?t=97600")

---

### Post by SleightfulMind on 2005-12-04
When I try to install libsasl2-modules-sql, I get the following error:

The following packages have unmet dependencies:
  libsasl2-modules-sql: Depends: libsasl2 (=2.1.19-1.5ubuntu1) but 2.1.19-1.5ubuntu4 is to be installed
E: Broken packages

Now, I have everything working except the SASL. How can I fix this problem?

Also, when I do telnet 127.0.0.1 25 and enter EHLO gmail.com the server doesn't respond with 250-AUTH. This seems to indicate that the server thinks it can't auth. Will installing libsasl2-modules-sql fix this issue?

Thanks for any help.
- Nate

---

### Post by wannabelinuxconvert on 2006-01-12
Is it possible to use this kind of setup with a dynamic ip address using something like dyndns.org !?

I read a similar article that did accomodate this, but it was using ArchLinux

[http://www.hypexr.org/linux_mail_server.php](http://www.hypexr.org/linux_mail_server.php)

Thanks

Mic

---

### Post by sleepkreep on 2006-02-17
Someone please help me.  I have an interesting setup and need to it work just a certain way.  I use Kubuntu Breezy.  I have KMail fetching all of my mail for me and am quite happy with it.  The directory where the mail is saved is ~/.kde/share/apps/kmail/mail/ .  I am setting up an imap server so I can use squirrelmail to read the mail on my machine.  Courier seems to require that the there be a ~/Maildir directory in order for it to work.  How do I change that to KMail's directory?  For the time being I created a symlink from ~/Maildir ---> ~/.kde/share/apps/kmail/mail .  However, now when I try to access the imap server, I get a error saying "Unable to open this mailbox."  Why can't I open the INBOX?

---

### Post by thegestetner on 2006-11-25
Hello all. I've followed the howto basically to the letter, this time using Edgy, and I can queue and send messages with SMTPd with no problems, but IMAP keeps causing hiccups. Telnet and everything checks out OK, but when I login from a mail program, I get this when I tail /var/log/mail.info :

Nov 25 18:08:30 unendurablylonely imapd-ssl: LOGIN FAILED, user=tom, ip=[::ffff:192.168.1.1]
Nov 25 18:08:30 unendurablylonely imapd-ssl: authentication error: Input/output error
Nov 25 18:08:30 unendurablylonely authdaemond: failed to connect to mysql server (server=localhost, userid='mail'): Client does not support authentication protocol requested by server; consider upgrading MySQL client


All the databases check out as far as I can tell - I can log into MySQL using the mail/password account just fine when I use PHPMyAdmin. 

I suspect that the Mysql client thing is the cause of the problem, but I don't understand what the big deal about authentication is. It's just a cleartext password, and I'm using the latest versions of the client and server from apt-get (5.0.24a).

I'm pretty much stumped. Help!

---

### Post by flurdy on 2006-11-27
> **thegestetner said:**
> Hello all. I've followed the howto basically to the letter, this time using Edgy, and I can queue and send messages with SMTPd with no problems, but IMAP keeps causing hiccups. Telnet and everything checks out OK, but when I login from a mail program, I get this when I tail /var/log/mail.info :

Nov 25 18:08:30 unendurablylonely imapd-ssl: LOGIN FAILED, user=tom, ip=[::ffff:192.168.1.1]
Nov 25 18:08:30 unendurablylonely imapd-ssl: authentication error: Input/output error
Nov 25 18:08:30 unendurablylonely authdaemond: failed to connect to mysql server (server=localhost, userid='mail'): Client does not support authentication protocol requested by server; consider upgrading MySQL client


All the databases check out as far as I can tell - I can log into MySQL using the mail/password account just fine when I use PHPMyAdmin. 

I suspect that the Mysql client thing is the cause of the problem, but I don't understand what the big deal about authentication is. It's just a cleartext password, and I'm using the latest versions of the client and server from apt-get (5.0.24a).

I'm pretty much stumped. Help!


Seems the mysql conf of courier is not correct. hard to tell from the error. maybe courier dont work with mysql 5? is mysql set up to accept connections from localhost network or just sockets? is the mysql user defined set up as localhost only and also any hosts?

ps. are you sure tom should be the username? and not [email]tom@somewhere.com[/email]?

---

### Post by muxecoid on 2006-12-22
Thanks. I try to do it on my home computer before doing it elsewhere, it does not go well cause I have dynamic IP and domain name.

---

### Post by kennova on 2007-02-12
I like your tutorial and appreciate the time you took to write it.  

I have a question about relaying to another smtp server.

The issue I am having is using a relay server that requires authentication.  I am actually using pobox.com as my relay server and it requires my username and password, where my username is a full email address.

I have found in the manual and in other tutorials that you can use commands like
smpt_sasl_enabled = yes and so on
I also created a smtp_sasl_passwd file and ran postman on that file to create the db file.  However, I still get bounced messages.

Any ideas would be helpful.  Thanks.

---

### Post by Verifier on 2007-08-01
Excellent guide.

I got a problem though :(
I can telnet to port 10024 without any problems.

This is the second guide i'm following, the first one didnt work quite well.
Therefore there can be some configuration errors that i might have missed.

Postfix says this:
Aug  1 16:30:33 www postfix/qmgr[4223]: warning: connect to transport smtp-amavis: Connection refused

from main.cf:
```

content_filter = amavis:[127.0.0.1]:10024

```

from my master.cf:
```

amavis unix        -       -       -       -       2       smtp
        -o smtp_data_done_timeout=1200
        -o smtp_send_xforward_command=yes

```

Shouldn't the log say "connect to transport amavis: xxxxxx"? The filter was named smtp-amavis before (when I followed the old tutorial).

Anyone got any hints?

Edit: I've changed back to smtp-amavis in both master.cf and main.cf. Not it complains on "Aug  1 16:41:33 www postfix/qmgr[5595]: warning: connect to transport amavis: Connection refused". lol =)

----------

Another problem: I can't authenticate properly.

Aug  1 16:44:08 www imaplogin: Connection, ip=[::ffff:192.168.1.100]
Aug  1 16:44:08 www imaplogin: LOGIN: DEBUG: ip=[::ffff:192.168.1.100], command=CAPABILITY
Aug  1 16:44:12 www imaplogin: LOGIN: DEBUG: ip=[::ffff:192.168.1.100], command=LOGIN
Aug  1 16:44:12 www imaplogin: LOGIN: DEBUG: ip=[::ffff:192.168.1.100], username=jonas
Aug  1 16:44:12 www imaplogin: LOGIN: DEBUG: ip=[::ffff:192.168.1.100], password=jonas
Aug  1 16:44:12 www imaplogin: authdaemon: starting client module
Aug  1 16:44:12 www imaplogin: authdaemon: REJECT
Aug  1 16:44:17 www imaplogin: LOGIN FAILED, ip=[::ffff:192.168.1.100]
Aug  1 16:44:24 www imaplogin: LOGIN: DEBUG: ip=[::ffff:192.168.1.100], command=LOGOUT
Aug  1 16:44:24 www imaplogin: LOGOUT, ip=[::ffff:192.168.1.100]

---

### Post by t_ras on 2007-08-01
I gave up trying to configure things my self. I use ISPconfig and it works fine.
I do some manual additions some times, but in general the GUI given by it is fine.

---

### Post by tedmasterweb on 2007-10-10
Regarding the permissions issue (Net::Server: 2007/10/10-12:38:46 Couldn't open lock file "/var/run/amavis/amavisd.lock").

This may sound barbaric, but I just commented out the line that sets the permissions (in /etc/init.d/amavis, line 66, #chown -c -h "$1:$2" "$4") and left /var/run/amavis as being owned by amavis.

This seems to work just fine. My only question is if some other process decides to use amavis, will it continue to work? Also, I am starting this manually via sudo /etc/init.d/amavis start. Will it come up fine when rebooting?

This seems like it might be a bug, like, maybe the script should look to see if the daemon_user and gid are being set in the conf files and respect them, if so, and do the default behavior if not.

---

### Post by atjensen11 on 2007-11-19
I really enjoyed the tutorial as well.  I too tried another first before finding this one by Flurdy.

I was able to get through most of it with only minor issues.  I was testing along the way and it all seemed to be working until I tried to login through Squirrelmail or user IMAP remotely.

In both cases (linked I am sure since Squirrelmail is using IMAP), I get an empty inbox.  The mail is being stored in /var/mail/virtual/username.  I can browse there through Webmin and read the mail.  But not so using IMAP.

Any suggestions?

Thanks,
Tom

---

### Post by hartunnoo on 2008-01-28
In this thread it says the network is directly go to outside world, I wonder how if the mail server behind the firewall. How it will be to configure it? I found noting to solve my problem.. Please assist me..  thank you.

---

### Post by cllsr on 2008-01-28
You would need to forward the ports you require from the firewall to the mail server. You would also need to tell postfix about the firewall in the main.cf by virtue of the setting "proxy_interfaces = your. outside.IP.addy".

Hope this helps.:)

---

### Post by phakan on 2008-02-11
Hi!

I'm hoping someone here can help me out... I've been trying to put up a mail server by following this guide. However, it doesn't work :( It doesn't seem to be able to connect to the database when I try to send emails by telnet...

I get the following in my mysql.log:
080212  0:52:18     243 Connect     mail@localhost on maildb
                    243 Query       SELECT destination FROM aliases WHERE mail='hotmail.com' and enabled = 1
                    244 Connect     mail@localhost on maildb
                    244 Query       SELECT domain FROM domains WHERE domain='hotmail.com' and enabled = 1
080212  0:52:58     243 Query       SELECT destination FROM aliases WHERE mail='testingdomain.com' and enabled = 1
                    244 Query       SELECT domain FROM domains WHERE domain='testingdomain.com' and enabled = 1
                    245 Connect     mail@localhost on maildb
                    245 Query       SELECT destination FROM aliases WHERE mail='test@testingdomain.com' and enabled = 1
                    246 Connect     mail@localhost on maildb
                    246 Query       SELECT destination FROM aliases WHERE mail='test@testingdomain.com' and enabled = 1
080212  0:53:13     243 Query       SELECT destination FROM aliases WHERE mail='testingdomain.com' and enabled = 1
                    244 Query       SELECT domain FROM domains WHERE domain='testingdomain.com' and enabled = 1
                    247 Connect     Access denied for user 'mail'@'localhost' (using password: YES)


And my mail.log looks like this:
Feb 12 00:51:22 tremor postfix/smtpd[17806]: connect from mycomputer.mydomain.com[xxx.xx.xxx.xxx]
Feb 12 00:52:58 tremor postfix/smtpd[17806]: warning: restriction `my_networks' after `permit' is ignored
Feb 12 00:52:58 tremor postfix/smtpd[17806]: BD58398FC5: client=mycomputer.mydomain.com[xxx.xx.xxx.xxx]
Feb 12 00:53:13 tremor postfix/cleanup[17809]: BD58398FC5: message-id=<20080211235258.BD58398FC5@thiscomputer.mydomain.com>
Feb 12 00:53:13 tremor postfix/qmgr[17805]: BD58398FC5: from=<xxx@hotmail.com>, size=407, nrcpt=1 (queue active)
Feb 12 00:53:13 tremor postfix/virtual[17811]: warning: connect to mysql server 127.0.0.1: Access denied for user 'mail'@'localhost' (using password: YES)
Feb 12 00:53:13 tremor postfix/virtual[17811]: warning: table virtual_mailbox_maps: lookup [email]test@testingdomain.com[/email]: Success
Feb 12 00:53:13 tremor postfix/virtual[17811]: BD58398FC5: to=<test@testingdomain.com>, relay=virtual, delay=55, delays=55/0.01/0/0.02, dsn=4.3.5, status=deferred (mail system configuration error)


Here's my main.cf:
smtpd_banner = $myhostname ESMTP $mail_name
biff = no
append_dot_mydomain = no

smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

myhostname = thiscomputer.mydomain.com
myorigin = /etc/mailname
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

mynetworks_style = host

local_recipient_maps =
mydestination =


delay_warning_time = 1h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s

smtp_helo_timeout = 60s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12


smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_sender_restrictions = permit_mynetworks, reject_non_fqdn_sender, rejject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_client_restrictions =
smtpd_recipient_restrictions = reject_unauth_pipelining, permit my_networks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit

smtpd_delay_reject = yes
disable_vrfy_command = yes

alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf



I hope someone could help me what I've done wrong here... I'm quite a newbie with Ubuntu so I'm not really sure what I should be looking for here...

Thanks in advance...

/P

---

### Post by cybernet on 2008-03-05
mirror for flurdy.com/docs/postfix/


[http://www.scribd.com/doc/2218859/How-to-set-up-a-mail-server-on-a-GNU-Linux-system](http://www.scribd.com/doc/2218859/How-to-set-up-a-mail-server-on-a-GNU-Linux-system)

---

### Post by jdurand on 2008-03-15
Some time back I started moving our mail server off an OS X system over to our new Ubuntu server.  I had someone helping me but then I got pulled off the project for some important client work.

I could REALLY use some help in finishing this system.  The original person who was helping isn't available now and I don't remember all the details of what he was doing.

The system that's partly set up is:

postfix
amavis-new
clamd
spamassassin
dovecot

It probably won't take much to finish it, we were working on setting up the config files at the time.

---

### Post by damoosemander on 2008-03-31
Hi Flurdy,

Yesterday, I was able to go to [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)  and I was able to access the site, however today it is gone.  I was wondering if you were going to be setting it online again?  I am running 6.06 (dapper) and I am in need of setting up a secure email server ASAP.  It is definately going to be a challange and serious under taking for me.  I was relying on your instructions.

It seems to be the best tutorial around and it would be a shame if it was not up and running!

Thanks,
Damoose

---

### Post by atjensen11 on 2008-03-31
I too have noticed that the site has been up and down over the last few days or even weeks.

One suggestion I have is to view the cached version at Google in the event that you cannot reach the live site.  This helped save me about a week ago when I really needed the instructions.

---

### Post by flurdy on 2008-05-13
Sorry the server has been up and down for awhile (power supply). Ive now moved flurdy.com to an amazon EC2 server, which should be a bit more reliant. :) 

Yes, the google cache version is one ive suggested to people whom contacted me while the site was down. So if it goes down again...

---

### Post by joanindo on 2008-05-15
hey guys,

i just finished setting up a web & mail server for my Lab.
i use Squirrelmail for the webmail so that users can open their emails
when they're not in Lab.

everything works well but there's one problem still bugging me.
i've problem with OPTIONS link in Squirrelmail.

[http://.../mail/src/options.php](http://.../mail/src/options.php)     (wont open when i'm off campus)  ???

when i'm at my Lab (on site) and try to click the link  it works well, but
at home (off site) it doesn't work.

i wonder what the problem is.

if you guys experienced this before and know how to solve it please reply.

cheers,

---

### Post by fade2gray on 2008-06-24
I've got this far...

[[COLOR="Blue"]_Configuration > Pop/IMAP (Courier)_[/COLOR]]("http://flurdy.com/docs/postfix/index.html#config-simple-imap")

...but I can't find...

> vi /etc/courier/authmysql

Should that read "vi /etc/courier/authmysql**rc**" :confused:

Summary: Up to this point in the guide "/etc/courier/authmysql" can't be edited because it doesn't exist, but "/etc/courier/authmysqlrc" does.

Thanks.

---

### Post by fade2gray on 2008-06-24
I'm now at...

[[COLOR="Blue"]_Configuration > Content Checks (amivisd-new)_[/COLOR]]("http://flurdy.com/docs/postfix/#config-adv-content")

> cd /etc/amavis.d/conf.d

Should that read "cd /etc/amavis/conf.d"?

Summary: I can find the directory "/etc/amavis/conf.d", but not "/etc/amavis.d/conf.d".

Edit: Also...

> vi /etc/spamassassin/local.rf

... should that read "vi /etc/spamassassin/local.**c**f"?

Thanks.

---

### Post by fade2gray on 2008-06-24
There seems to be a conflict at [[COLOR="Blue"]_Configuration > Encryption (TLS)_[/COLOR]]("http://flurdy.com/docs/postfix/#config-secure-crypt") - where you are advised to "Please refer to [[COLOR="Blue"]_previous edition_[/COLOR]]("http://flurdy.com/docs/postfix/edition5.html#conf_encryption")  for more detail", where you are told to enter...

```
smtps inet n - n - - smtpd
```

... into the master.cf file.

Returning to [[COLOR="Blue"]_Configuration > Encryption (TLS)_[/COLOR]]("http://flurdy.com/docs/postfix/#config-secure-crypt"), you are told to enter...

```
smtps inet n - - - - smtpd
```

Which is correct?

Thanks.

---

### Post by Wd2048 on 2008-07-18
I am getting ready to set up a server that is going to require a windows environment for a particular software suite. However, we need a mail server, and I'm not particularly wanting to pay for Exchange. Anyone see a problem with running this setup in a VMWare virtual machine running ubuntu hardy heron server edition?

or... even better... i could run the Windows Server in a virtual machine on the Ubuntu server...

---

### Post by yaztromo on 2008-08-14
Is this guide geared towards setting up a server which can bring down mail from my ISP's POP3 boxes. I need something like this:

ISP'S POP3 SERVER ==> OFFICE POP3 SERVER (UBUNTU) ==> OUTLOOK

---

### Post by Linux9 on 2008-08-16
I Need A GUI,I NEED A GUI!!!!!!:)

---

### Post by webmaster_ph on 2008-08-16
> **flurdy said:**
> I have rewritten my [How to set up a mail server on a GNU / Linux system](http://flurdy.com/docs/postfix/) , which is now based on Ubuntu Hoary.

(Used to be Mandrake, but is now completely rewritten from scratch to use apt-get, The old one was listed on postfix.org)

It is a complete step by step guide to install, configure and run these packages:
Ubuntu + Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + SquirrelMail 

Not sure whether this should be in the server forum, but it is a howto hence the tips forum.
I must be wrong, but I could not see any other mail server howtos for ubuntu mentioned in the forums.

Feel free to send me comments.

All the installation and configuration sections are complete. Some of the later testing and appendix needs padding out, but as any other document it will forever be in development.  ;-)

does this apply to hardy too?

appreciate an updated how-to. thanks!

---

### Post by fade2gray on 2008-08-17
> **webmaster_ph said:**
> does this apply to hardy too?

appreciate an updated how-to. thanks!

The link, [How to set up a mail server on a GNU / Linux system]("http://flurdy.com/docs/postfix/"), actually points to the 7th edition guide which is aimed at Hardy.

You'd be better off following this [thread]("http://ubuntuforums.org/showthread.php?t=185913"), though I believe Flurdy has stopped maintaining it. Being a novice I found the guide very heavy going what with the typos and the difficulty in being able to cut and paste from the guide - I ended up following a simpler one.

Good luck.

---

### Post by hailang on 2008-08-18
> **yaztromo said:**
> Is this guide geared towards setting up a server which can bring down mail from my ISP's POP3 boxes. I need something like this:

ISP'S POP3 SERVER ==> OFFICE POP3 SERVER (UBUNTU) ==> OUTLOOK

I think the tool for this is fetchmail. I am looking for the resolution too.

---

### Post by chris_ac on 2008-09-30
i am a it confused on the sectio of the how to guide courier imap. it say to vi /etc/courier/authmysql, i dont have a authmysql file i do have a authmysqlrc file 
i have tried to retrace my steps to see if i left something out but havent been able to find anything. am i suppose to vi /etc/courier/authmysqlrc instead and make the changes.

---

### Post by flurdy on 2008-10-06
Yes, use */etc/courier/authmysqlrc*.
It is a typo by me, that I keep forgetting to change.

---

### Post by kmonson on 2008-10-21
This is a great how-to, but is there some sort of gui for this? :)

---

### Post by three_jeeps on 2008-11-07
A thank-you to flurdy for updating this approach based on Hardy Heron!  
I am running Hardy Heron as a basic web server using Apache 2.  I am using a service that allows me to create a hostname that points to my dynamic IP, issued by my ISP. In the course of setting up my hostname and domain, I have the option of enabling email routing by specifying my MX hostname as my primary mail relay.
My question is: will the mail server setup described by flurdy work, as configured, using my email relaying?  If I need to change something with the server setup or, with my mail routing, please let me know.  

Thanks for your help
-J

---

### Post by Phases on 2008-11-16
Hey guys :) 

I'm hoping someone pretty familiar with this can help me out. I followed the guide the best I could, and have been working on it for five hours now, but am left with a little trouble. 

Wherever the part was toward the beginning (can't seem to find it now) where you test sending an email CLI, I could do. The MAILTO: blah.com part. I emailed my gmail account fine. 

However, when trying to login squirrelmail I get (edit: got, now I'm getting told wrong username and password) the "Connection dropped by IMAP" message, and also when trying the test to connect to IMAP with the CLI test (can't find where I found that, now), I get some sort of 'error, terminating'.  

I will try to find the references to these ^^ and will edit them into this post when I find them. I'm sorry I'm just so scatterbrained right now, been at this long time. 

I can't figure out how to run /usr/share/squirrelmail/src/configtest.php ...even as root I get permission denied. I tried to open it with FF and that didn't work, tried to make +x, that didn't work. 

My syslog, when I try to connect either way, says 1 of 2 things:

If i try to log in with [email]phases@superstickphase.com[/email] I get told supplied password doesn't match encrypted password. I've tried combos galore to get them to match.

If I try to log in with just my username, phases, I get told zero rows returned, no password to compare. 

I've been all over this, and google, for almost six hours now.. Hope someone can help. Thanks.

---

### Post by Phases on 2008-11-17
Puh-lease? :)

---

### Post by madverb on 2008-11-17
eBox makes it really easy but it doesn't have webmail.

[http://ebox-platform.com/](http://ebox-platform.com/)

---

### Post by Phases on 2008-11-17
I only glanced but that seems to be an entire content management system.. I'm just lookin for lightweight email system, and prefer to fix what I've got mostly going..

Thanks for the reply!

---

### Post by Phases on 2008-11-18
I have spent many a more hour on this. 

So far using the test section, I do good. Every part of the test section I pass except at the end it says "try testing from outside server" but doesn't tell how to do that, so I haven't. But,  I can send mail to my  gmail account, however my state email account won't get it. Is this because I need to have it relayed? 

Secondly, when I try to reply to said email, my server logs pop up with "relay access denied".

Third problem, I can't log into squirrelmail. The logs show it pulling my record out of sql, but it says the passwords don't match and I get wrong username/pass from squirrel. 

Any ideas where to start? I've been all up and down the testing page, squirrel and postfix's websites..

Thanks..

---

### Post by Phases on 2008-11-18
> **Phases said:**
> I have spent many a more hour on this. 

So far using the test section, I do good. Every part of the test section I pass except at the end it says "try testing from outside server" but doesn't tell how to do that, so I haven't. But,  I can send mail to my  gmail account, however my state email account won't get it. Is this because I need to have it relayed? 

Secondly, when I try to reply to said email, my server logs pop up with "relay access denied".

Third problem, I can't log into squirrelmail. The logs show it pulling my record out of sql, but it says the passwords don't match and I get wrong username/pass from squirrel. 

Any ideas where to start? I've been all up and down the testing page, squirrel and postfix's websites..

Thanks..

OK, I got send and receive FINALLY working with gmail accounts. I can receive from my work but not send to my work, I guess residential blocks are blocked for spam precaution. 

However, I still can't log into squirrelmail. Any advice appreciated.

---

### Post by Phases on 2008-11-19
Got mail to work with work account, and  yahoo, and everyone else that was blocking it. 

Residential IP's are mostly on spamhaus PBL, due to the amount of spam sent out of residential blocks - so I had to relay it.

I first tried through gmail, which worked but then put my gmail account in the from field to the final destination, which isn't what I wanted. 

Then I found out after digging deeper that comcast provides a relay (free of charge, without having to upgrade to a business account! Holy whack!) that solves all the problems. I can send and receive (so far) to/from anyone. 

Still having trouble with squirrelmail authenticating me, and now getting this error after playing with it a little:

Warning: include_once(DB.php) [function.include-once]: failed to open stream: No such file or directory in /usr/share/squirrelmail/functions/db_prefs.php on line 40

Warning: include_once() [function.include]: Failed opening 'DB.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/squirrelmail/functions/db_prefs.php on line 40
ERROR:

Could not include PEAR database functions required for the database backend.
Is PEAR installed, and is the include path set correctly to find DB.php?
Please contact your system administrator and report this error.  

So. We'll see. If ya have any ideas feel free to post em. 
Thanks

---

### Post by three_jeeps on 2008-11-19
> **Phases said:**
> Got mail to work with work account, and  yahoo, and everyone else that was blocking it. 
-----snip ----
Then I found out after digging deeper that comcast provides a relay (free of charge, without having to upgrade to a business account! Holy whack!) that solves all the problems. I can send and receive (so far) to/from anyone. 
--snip-----


Been watching your posts, sorry I could not help...congrats on getting it working...but I do have a question...

How did you find out Comcast provides a relay? and how can I use it? (e.g.address?)

I also have comcast, but I also have a relay set up at dyndns.org
(well, what I think is a  relay....we shall see).
Thanks
John

---

### Post by Phases on 2008-11-19
> **three_jeeps said:**
> Been watching your posts, sorry I could not help...congrats on getting it working...but I do have a question...

How did you find out Comcast provides a relay? and how can I use it? (e.g.address?)

I also have comcast, but I also have a relay set up at dyndns.org
(well, what I think is a  relay....we shall see).
Thanks
John

Hey John,
Sorry - I shoulda' posted the links here too, but see my last post on this thread, should get ya on your way: 

[http://ubuntuforums.org/showthread.php?t=987371](http://ubuntuforums.org/showthread.php?t=987371)

If you need help hollar. I'm no guru by any means but I've spent a lot of time on this and just helped a friend get through his kinks too so, I'm at least somewhat familiar.

---

### Post by Phases on 2008-11-19
Arg, this is killin' me. 

With the configtest.php for squirrel mail I get:

```
ERROR: Required PHP PEAR DB support is not available. Is PEAR installed and is the include path set correctly to find DB.php? The include path is now: ".:/usr/share/php:/usr/share/pear".
```

I can't find DB.php anywhere with locate, nor where to set that include path. I've got, and reinstalled, php5-pear.. and am all up in it's directory looking for clues..

Ideas?

Edit: nevermind! turns out I needed two more packages that weren't listed. I wish I remembered what they were called, I just did a search for PEAR and dug through the php stuff. I think php-files and php-db. 

------------

So I'm past THAT error. Moving on.. Still can't log in. "Unknown user or password incorrect.

mysql.log shows this:

081119 18:50:46	    613 Query       SELECT id, crypt, "", uid, gid, home, concat(home,'/',maildir), "", name, "" FROM users WHERE id = "phases@superstickphase.com" AND (enabled=1)

my mail.log shows this:

Nov 19 18:52:38 phases78s1 imapd: Connection, ip=[::ffff:127.0.0.1]
Nov 19 18:52:38 phases78s1 authdaemond: received auth request, service=imap, authtype=login
Nov 19 18:52:38 phases78s1 authdaemond: authmysql: trying this module
Nov 19 18:52:38 phases78s1 authdaemond: SQL query: SELECT id, crypt, "", uid, gid, home, concat(home,'/',maildir), "", name, "" FROM users WHERE id = "phases@superstickphase.com" AND (enabled=1)
Nov 19 18:52:38 phases78s1 authdaemond: supplied password '[[my password]]' does not match encrypted password '[[garbly gook]]' (<-- no, they don't match, but i can try the garbly gook and make them match, and still fail)
Nov 19 18:52:38 phases78s1 authdaemond: authmysql: REJECT - try next module
Nov 19 18:52:38 phases78s1 authdaemond: FAIL, all modules rejected
Nov 19 18:52:38 phases78s1 imapd: LOGIN FAILED, user=phases, ip=[::ffff:127.0.0.1]
Nov 19 18:52:43 phases78s1 imapd: LOGOUT, ip=[::ffff:127.0.0.1], rcvd=53, sent=332

---

### Post by Phases on 2008-11-20
Changed the clear password from within phpmyadmin, set up authmysqrc to use that instead of crypt, it authenticated, but then failed, error:

imapd: chdir /var/spool/mail/virtual/phases/: No such file or directory

I looked, there's no 'phases' inside virtual. But there is a phases alongside virtual.

I tried a sym link in virtual, phases, to point to /var/spool/mail/phases but that didn't work. 

Copied phases to virtual/ but that still failed. 

Created a folder called phases and that gave me a different error. 

Anyone know where I can'f find where it's being told /var/spool/mail/virtual/phases? Perhaps if I change that to /var/spool/mail/phases .....

edit: Found where to change it, it's in the sql database. Played with that to no avail. Also created the phases folder under virtual again, still get "dropped by imap" displayed in browser, but no errors in the log.

---

### Post by lukeyduke on 2008-12-22
Try atmail!
It's fantastic, [www.atmail.com](www.atmail.com), and if you are just looking for a webmail client, they do a free version called atmail open.  I find it is a much faster, simpler, better looking interface than any other, such as hotmail and gmail.

You can find an tutorial for installing it on there website here --> [http://atmail.com/kb/2008/installing-atmail-open-webmail-client-on-ubuntu/]("http://atmail.com/kb/2008/installing-atmail-open-webmail-client-on-ubuntu/")

---

### Post by cllsr on 2008-12-22
Phases,
  Delete the directories you created because the mail server will create them for you. All you should have to do is send yourself an email as you did in the test section. That should create the directory for you.

cllsr

---

### Post by MrFreaky on 2009-01-02
I just stumbled on this and the only thing I can say is : WOW

---

### Post by lukeyduke on 2009-01-04
> **MrFreaky said:**
> I just stumbled on this and the only thing I can say is : WOW

Across what?

---

### Post by whoop on 2009-01-26
I've had next to none experience with mail servers in general; so I have to very stupid questions (so bare with me).

1: If I want a local mail server which just sends and receives local mail, what domain do I use? In tutorials you see f.i. example.com, yourdomain.com, domain.com, example.local. These are off course examples. .local could be technically usable (is my guess) but it is not even supported by ubuntu cause it conflicts with avahi. So could anybody give me a **real** example?

2: If I was to use a real FQDN (like mynewmailsever.com) how would other users/providers/networks find my server? Is it like you have to provide a static IP address to the registrar where you got the domain name, and they add it to a main dsn server (just another guess)?

---

### Post by whoop on 2009-01-26
> **lukeyduke said:**
> Across what?
This thread, is my guess :D

---

### Post by sim085 on 2009-02-02
Hi,

Maybe this will get ignored but I really do not know where else to ask. I have checked several internet sites to try and solve my problem but so far cannot even identify what is wrong!

I have followed the tutorial mentioned here. Just before I started the Advanced Mail Server section I had tested my settings. I had some minor problems due to syntax error - solved those. I used telnet to test my environment and the emails I was sending arrived correctly to /var/spool/mail/virtual/<account>/new

Yesterday I started the Advanced Mail Server section and completed it. However the result is not exactly what I was expecting! I must have definitely done something wrong :( 

I can access squirrelmail from an outside machine. However it does not allow me to log in. The error message I get is "Unknown user or incorrect password". 

I therefore tried to use telnet to send the emails again. However no emails want to arrive.

I checked the var/log/mysql/mysql.log file and the database seems to be queried correctly. I checked the var/log/mail.err and no error is displayed. 

I then checked the var/log/mail.log and I did find an error. The last entry in this file is as follows:

Feb 2 15:58:22 ubuntu postfix/smtp[8310]: 6A2FG767D: to=<postmaster@mydomain.com>, relay=none, delay=34, delays=34/0/0, dsn=4.4.1, status=deffered (connection to 127.0.0.1[127.0.0.1]:10024: Connection Refused)

Feb 2 15:58:22 ubuntu postfix/smtp[8307]: disconnect from localhost[127.0.0.1].

I do not know if this is normal maybe because in the Advanced Mail section I blocked such access to postfix. Does anyone know this?

Also does squirrelmail log errors anywhere so maybe I can track where the error is! Note that when I use squirrelmail the mysql logs do show a hit on a database but I always get the above error.

Thanks for any comments,
Sim085

---

### Post by sim085 on 2009-02-03
Hi,

I checked the logs and my settings again and I found out that the application that should work on port 10024 is amavis. I therefore went to /etc/postfix/main.cf and remarked the line which said that the content filter would be amavis. 

Reloaded postfix ... and I could send emails with telnet again :)

I therefore tried to start amavis again and it showed me an error about the host not set. So I opened the /etc/amavis/conf.d/05-node_id and set it as follows:

# chomp($myhostname = 'hostname --fqdn');
$myhostname = smtp.<domainname>.com

I restarted amavis, changed /etc/postfix/main.cf back to how it was, tried telnet and all is fine :) 

However I still have the squirrelmail problem ... if anyone knows anything about this please let me know :)

Regards,
Sim085

---

### Post by albinootje on 2009-02-03
> **lukeyduke said:**
> Try atmail!
It's fantastic, [www.atmail.com](www.atmail.com), and if you are just looking for a webmail client, they do a free version called atmail open.  I find it is a much faster, simpler, better looking interface than any other, such as hotmail and gmail.

You can find an tutorial for installing it on there website here --> [http://atmail.com/kb/2008/installing-atmail-open-webmail-client-on-ubuntu/]("http://atmail.com/kb/2008/installing-atmail-open-webmail-client-on-ubuntu/")

How long have you been using this and with how many users ? 
I've tried a lot of groupware software in the past, and I'm a bit sceptical when it comes to using the open source version of commercial software, from time to time I get the impression it's just meant as advertisement for the commercial version, and to try to push users towards the commercial version in the end.

I've tried to install the open source version of atmail some months ago, ran into installation problems right away, looked at their forum, saw all kind of problems.

But thanks for the link to that installation howto, I'll try it again when I have enough time for that.
So far my users are happy with squirrelmail, and I'm only interested to switch (or offer the users an alternative) if there's a very stable, easy to maintain, and better alternative available.

---

### Post by sim085 on 2009-02-04
Hi again,

I managed to get squirrelmail to work. All I changed was the MYSQL_SERVER value in /etc/courier/authmysqlrc file. From localhost I changed this 127.0.0.1!

I then started to get logs about error in the /var/log/mail.info file where I discovered I had mess with the password. Solved those and everything works fine :)

Now does anyone know how I can retrieve mail from the ISP?

---

### Post by sim085 on 2009-02-05
Hi again,

No one here had problems to receive emails from outside email accounts? I did manage to send emails from my accounts to a hotmail account but not vice versa! I did some research and found about fetchmail. However this seems to only retrieve emails for a single account! Does anyone have any idea on how I can proceed since this step seems not included in the howto!

---

### Post by sim085 on 2009-02-06
managed to solve this one as well .. was a setting in fetchmail.

However I took this path independently from the Howto ... does that mean that the Howto has some other way how to get the mail from the ISP to the mail server? (I would really be interested to know of other means to achieve the same thing in order to improve my set-up)

Regards,
Sim085

---

### Post by ethos84 on 2009-03-12
I've setup the "basic" part but when I try and start shorewall I get:

The firewall won't be started/stopped unless it is configured

Can't telnet into port 25 either.

---

### Post by menaice on 2009-10-15
Is there an udated tutorial on this?  I started to follow the instructions and two things poped out at me so i unistalled what i started and stoped
 
"[FONT=Courier New]sudo aptitude install postfix postfix-mysql[/FONT] This will prompt you to choose type of email server. Select ***internet site*** It will also suggest a server name. Correct this if needed. "    It didn't prompt me for anything to select an internet site.
 
Also
 
**SASL**

sudo aptitude install libsasl2-modules-sql libgsasl7 libauthen-sasl-cyrus-perl
 
The Libgsas17 was not installed

---

### Post by LMSSML on 2010-02-18
Hi people,

I've followed the manual [http://flurdy.com/docs/postfix/#config-simple-firewall](http://flurdy.com/docs/postfix/#config-simple-firewall)

but then I could create mailbox with phpmyadmin using mysql commands and in maildb database althouth every user I create on DB if I try with squirrel or even with roundcube none of them work.

I can see it in /var/spool/mail/virtual/<username> is not created for new users.

Is there any admin software (like webmin) to create user accounts and mailbox ?

I think I missed a step creating user accounts but I couldn't find what is missing.

Just to referre that I have a user created and this user works but hte new ones dosen't work and for the first user the folder for user was created automatically.

Thanks in advanced for the help .

---

### Post by tryinghard on 2010-03-10
apparently I'm getting an error in running the install-extras.sh script in the 5th line  is the php4-cli package name and it fails. even changing it to 5  fails. Please help to clarafy this.
 Thanks
Miles  M Sakaguchi

---

### Post by goodnaturenet on 2010-04-06
I'm attempting to learn how to set up a mail server and I have something configured wrong and haven't been able to find it. I am at the basic mailserver phase and can't figure out last piece I have wrong.
 
Hopefully someone has seen this before:
 
/var/log/mail.log at postfix restart
 
*Apr 6 19:15:57 mail04 postfix/master[11195]: terminating on signal 15*
*Apr 6 19:15:57 mail04 postfix/master[11314]: daemon started -- version 2.6.5, configuration /etc/postfix*
*Apr 6 19:15:57 mail04 postfix/virtual[11320]: fatal: /etc/postfix/mysql_uid.cf: bad string length 0 < 1: where_field =*
*Apr 6 19:15:58 mail04 postfix/master[11314]: warning: process /usr/lib/postfix/virtual pid 11320 exit status 1*
*Apr 6 19:15:58 mail04 postfix/master[11314]: warning: /usr/lib/postfix/virtual: bad command startup -- throttling*
 
I'm sure I've got something simple wrong, but I can't find it. Input?

---

### Post by goodnaturenet on 2010-04-07
> **goodnaturenet said:**
> I'm attempting to learn how to set up a mail server and I have something configured wrong and haven't been able to find it. I am at the basic mailserver phase and can't figure out last piece I have wrong.
 
Hopefully someone has seen this before:
 
/var/log/mail.log at postfix restart
 
*Apr 6 19:15:57 mail04 postfix/master[11195]: terminating on signal 15*
*Apr 6 19:15:57 mail04 postfix/master[11314]: daemon started -- version 2.6.5, configuration /etc/postfix*
*Apr 6 19:15:57 mail04 postfix/virtual[11320]: fatal: /etc/postfix/mysql_uid.cf: bad string length 0 < 1: where_field =*
*Apr 6 19:15:58 mail04 postfix/master[11314]: warning: process /usr/lib/postfix/virtual pid 11320 exit status 1*
*Apr 6 19:15:58 mail04 postfix/master[11314]: warning: /usr/lib/postfix/virtual: bad command startup -- throttling*
 
I'm sure I've got something simple wrong, but I can't find it. Input?
 
 
Got it figured out. Simple typo like I thought. Thank you.

---

### Post by murpheus on 2010-05-02
I was wondering it would be nice to have this in pdf file for downloading

---

### Post by murpheus on 2010-05-02
> **flurdy said:**
> I have rewritten my [How to set up a mail server on a GNU / Linux system]("http://flurdy.com/docs/postfix/") , which is now based on Ubuntu Hoary.

(Used to be Mandrake, but is now completely rewritten from scratch to use apt-get, The old one was listed on postfix.org)

It is a complete step by step guide to install, configure and run these packages:
Ubuntu + Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + SquirrelMail 

Not sure whether this should be in the server forum, but it is a howto hence the tips forum.
I must be wrong, but I could not see any other mail server howtos for ubuntu mentioned in the forums.

Feel free to send me comments.

All the installation and configuration sections are complete. Some of the later testing and appendix needs padding out, but as any other document it will forever be in development.  ;-)


Just thought it would be nice to have this in pdf format for downloading

---

### Post by joedm on 2010-07-21
> **pcolomes said:**
> Ok Now I've found how to deal with the NON-WORKING directories.
As I was reading somewhere, then someone said when the first mail it's received then postfix will automatically create subfolders.

I tried sending from my gmail account but nothing happened
So I had to send myself mails to all accounts I've created in the users database.

run in console window as root (sudo su) 
- tail -f /var/log/mail.info
then in another console window run
- sudo telnet -d 127.0.0.1 25 [ -d option will activate debug ]
mail from: <ANYUSER@YOURDOMAIN.COM> [it has to be your domain, otherwise it will not work. also it wont work using @localhost]
- rcpt to: <USER1@YOURDOMAIN.COM> [here write the 1st email address you want to "activate". for example: [email]info@hello.com[/email]]
- data
- write anything lalalal lalala lalala [press Intro to next line and write a dot "." to finish data]
- .
- ok queued as xxxxxxx

repeat this process with all users on your database. What a mess uh? I haven't found another way to it.

I know this is a bit old, but I figure out my problem with this same error.

What was happening was that I was configuring an alias to an external address before postix had received the first email for my user.  

Hence, the maildir was not created as there was no need to deliver locally.  

So, I just disabled the alias in mysql then sent an email to that user which subsequently created the maildir, then squirrelmail was fine for logging in via imap.

hope this helps.

---

### Post by 10ghost on 2010-07-25
Hi all,
After following the link [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) on setting a mail server.
After installation of the necessary a packages.
The first line in the configuration part
cp /usr/share/doc/shorewall-common/default-config/interfaces /etc/shorewall/ 
I issued the bove command it gives me a response telling the 
/usr/share/doc/shorewall-common/default-config/interfaces 
No such file or directory


What could be the problem .
I have checked the packages i installed and all is ok.
So what else could be the problem?

---

### Post by flurdy on 2010-07-26
> **10ghost said:**
> Hi all,
After following the link [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) on setting a mail server.
After installation of the necessary a packages.
The first line in the configuration part
cp /usr/share/doc/shorewall-common/default-config/interfaces /etc/shorewall/ 
I issued the bove command it gives me a response telling the 
/usr/share/doc/shorewall-common/default-config/interfaces 
No such file or directory


What could be the problem .
I have checked the packages i installed and all is ok.
So what else could be the problem?

Did you install the shorewall-doc package?

---

### Post by flurdy on 2010-07-26
> **joedm said:**
> I know this is a bit old, but I figure out my problem with this same error.

What was happening was that I was configuring an alias to an external address before postix had received the first email for my user.  

Hence, the maildir was not created as there was no need to deliver locally.  

So, I just disabled the alias in mysql then sent an email to that user which subsequently created the maildir, then squirrelmail was fine for logging in via imap.

hope this helps.

And to the original quote using mutt simplifies the local mail testing a lot: echo Initial mail | mutt -s initial [email]a@b.com[/email]

Could probably write some bash/perl loop to do a sql select of aliases/users join as well.

---

### Post by manningkj on 2010-07-26
I have a problem in that I can Telnet messages to my email server but cannot send using an email client (Outlook Express/Thunderbird). The messages do not bounce and there is not even any connection attempt information in the logs. The only information in the logs (other than for my Telnet messages that work) is for disallowed relaying attempts).
 
This was all working fine until I moved offices and therefore broadband connection. The only other thing I can add is that I am now not on a fixed IP, which I handle using DynDNS in my router, which seems to work fine.
 
Any help would be very much appreciated.
 
Thanks.

---

### Post by 10ghost on 2010-07-28
> **flurdy said:**
> Did you install the shorewall-doc package?

Yes i did.
So what else could be the problem?
sudo apt-get install shorewall-doc
[sudo] password for glider: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
shorewall-doc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 225 not upgraded.


information after an attempt to install again.
Pls do you have any suggestion again.
Sorry for the late reply.

---

### Post by manningkj on 2010-07-29
> **manningkj said:**
> I have a problem in that I can Telnet messages to my email server but cannot send using an email client (Outlook Express/Thunderbird). The messages do not bounce and there is not even any connection attempt information in the logs. The only information in the logs (other than for my Telnet messages that work) is for disallowed relaying attempts).
 
This was all working fine until I moved offices and therefore broadband connection. The only other thing I can add is that I am now not on a fixed IP, which I handle using DynDNS in my router, which seems to work fine.
 
Any help would be very much appreciated.
 
Thanks.
 
Forget this, sorry, I had DNS problems.

---

### Post by jasonclark10 on 2010-07-30
I would like to do is setup a mail server to get a feel for it, and then do a relay. Basically to setup both. And, then once I figure this out setup the hardest portion of a server . I appreciate the resources.

---

### Post by duceduc on 2010-08-11
Thank you!!!! I was getting the same error after I finished creating the address table and testing it. I am good now.
```
php-files and php-db
```
> Arg, this is killin' me. 

With the configtest.php for squirrel mail I get:

```
Required PHP PEAR DB support is not available. Is PEAR installed and is the include path set correctly to find DB.php? The include path is now: ".:/usr/share/php:/usr/share/pear".
```
ERROR: Required PHP PEAR DB support is not available. Is PEAR installed and is the include path set correctly to find DB.php? The include path is now: ".:/usr/share/php:/usr/share/pear".
I can't find DB.php anywhere with locate, nor where to set that include path. I've got, and reinstalled, php5-pear.. and am all up in it's directory looking for clues..

Ideas?

Edit: nevermind! turns out I needed two more packages that weren't listed. I wish I remembered what they were called, I just did a search for PEAR and dug through the php stuff. I think php-files and php-db.

---

### Post by 10ghost on 2010-08-28
Based on Howto i followed it worked,.
The problem now faced is that it displays this msg

```

A9EEAE14D6: to=<glider@domainname.net>, relay=local, delay=66, delays=66/0.02/0/0.09, dsn=2.0.0, status=sent (delivered to maildir)

``` 
meaning the mail was sent without any problem
It appereared in the home folder maildir

I discovered that a folder glider was not created in for glider at
/var/mail/virtual/ folder

What could be the problem?
What are necessary steps i need to solve this problem.

---

### Post by kain1983 on 2010-09-07
Hey,

I was wondering if anyone has a walk through of how to enable vacation messages for email accounts.  Flurdy's guide is very nice but vacation/auto reply is an extremely important feature which seems to be missing.

Any help would be appreciated.

Thanks.

---

### Post by karthick87 on 2010-11-01
What about setup ing mail server in ubuntu 10.04?

---

### Post by flurdy on 2010-11-08
> **getyourkarthick said:**
> What about setup ing mail server in ubuntu 10.04?

:confused: 
Sorry don't quite understand your question. The howto is based on 10.04.

---

### Post by cipe53 on 2011-02-07
I have installed courier/postfix/ubuntu with virtual domains as per Flurdy and all is working. 

From an IMAP client, users are able to create folders and move messages to them. These changes I can see reflected under /var/spool/mail/virtual/<user.name>.

I would like to migrate folders and messages from the old courier/exim/ubuntu mail server to the new. When I create folders in /var/spool/mail/virtual/<user.name> via maildirmake.courier, these folders are not recognised by the IMAP client (we have tried two clients). Google suggested I use maildiracl, which makes sense, but I cannot even get the -list command to work. I do not think I understand the arguments for maildiracl -list maildir folder.


I have not been able to Google an answer.

Any suggestions

---

### Post by cazador2011 on 2011-04-13
I've been working through [Flurdy's advanced mail server guide]("http://flurdy.com/docs/postfix/") (a great resource BTW) and have the following suggestions for improvements:
 
1) In SASL section when talking about the smtpd_sender_restrictions, I think a comma is after warn_if_reject?
  2) Also in SASL section, when listing the lines to insert into /etc/pam.d/smtp, instead of the variable aPASSWORD, I think it should be mailPASSWORD.
    3) In the Roundcube setup instructions, the following additional changes to main.inc.php are necessary (at least they were for me):

```
// SMTP username (if required) if you use %u as the username RoundCube
// will use the current username for login
$rcmail_config['smtp_user'] = '%u';
// SMTP password (if required) if you use %p as the password RoundCube
// will use the current user's password for login
$rcmail_config['smtp_pass'] = '%p';
// SMTP AUTH type (DIGEST-MD5, CRAM-MD5, LOGIN, PLAIN or empty to use
// best server supported one)
$rcmail_config['smtp_auth_type'] = 'PLAIN';
```Maybe also want to change imap port to 993 as was done for squirrelmail.

---

### Post by thexcr0w on 2011-07-09
Hallo,

Great working mail server but can you tell me how to set up Mutt to work with the 9th version of the tutorial?

---

### Post by KriBaBa on 2011-09-22
Deleted.. wrong thread ... :S

---

### Post by db4 on 2012-10-01
Kinda a bump but

i followed the tutorial

and know my squirrelmail says:

ERROR
Unknown user or password incorrect.

so i assume i did something wrong with the installation of squirrelmail but i have re-done those and same issue remains.

Anyone knows solution or possible problem?

only thing i didnt do was add template

edit:

> $
Oct  1 19:16:21 mail imapd-ssl: Connection, ip=[::ffff:127.0.0.1]
Oct  1 19:16:21 mail authdaemond: received auth request, service=imap, authtype$
Oct  1 19:16:21 mail authdaemond: authmysql: trying this module
Oct  1 19:16:21 mail authdaemond: authmysqllib: connected. Versions: header 505$
Oct  1 19:16:21 mail authdaemond: SQL query: SELECT id, crypt, "", uid, gid, home, concat(home,'/',maildir), "", name, "" FROM users WHERE id = 'brian'  AND (enabled=1)
Oct  1 19:16:21 mail authdaemond: zero rows returned
Oct  1 19:16:21 mail authdaemond: no password available to compare
Oct  1 19:16:21 mail authdaemond: authmysql: REJECT - try next module
Oct  1 19:16:21 mail authdaemond: FAIL, all modules rejected
Oct  1 19:16:21 mail imapd-ssl: LOGIN FAILED, user=brian, ip=[::ffff:127.0.0.1]
Oct  1 19:16:26 mail imapd-ssl: LOGOUT, ip=[::ffff:127.0.0.1], rcvd=45, sent=363



the SQL query seems to be wrong. it says WHERE id = 'brian' while id is the mail adress so it should be name and when i use @example.com 

edit2: works now<.< with address

---

### Post by okos on 2012-10-01
Hi,

I am using Ubuntu 10.04 LTS

What I am looking for is simply to have logrotate email me the squid3 access.log prerotate.

Things have snowballed after that. 

Having tested mail and mailx, neither will send me an email to xxxxxx.gmail.com.

```
echo “This will go into the body of the mail.” | mail -s “Hello world” xxxxxx@gmail.com
```

I kept getting the error message that I need a MTA
I was looking for a simple MTA like sendmail. I tried dozens of tutorials but nothing seems to work.

I do not want all of the additions such as spamassassin or apache. I just want a simple mta to send logs to my email.

/var/log/mail.err
```
Oct  1 16:29:46 xxxxxx sendmail[22259]: My unqualified host name (xxxxxxx) unknown; sleeping for retry
Oct  1 16:30:46 xxxxxxx sendmail[22259]: unable to qualify my own domain name (xxxxxx) -- using short name

```

/var/log/mail
```
Oct  1 16:30:46 xxxxxx sendmail[22259]: q91NUkoM022259: to=mygmail@gmail.com, ctladdr=me (1000/1000), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30081, relay=[127.0.0.1] [127.0.0.1], dsn=5.3.0, stat=User unknown
Oct  1 16:30:46 xxxxxxx sm-mta[22397]: q91NUkvq022397: from=<me@xxxxxx>, size=81, class=0, nrcpts=0, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]

```
So now I am considering postfix. At one point it is asking for my domain. Since I am not running an online server, it will not be mydomain.com. What would it be? The name of my computer?

Am I on the right track? Any suggestions for a tutorial to successfully get this working?

Thanks
okos

---

### Post by dunbrokin on 2012-10-16
You have reached the same point as me....did you solve it? If so how?

---

