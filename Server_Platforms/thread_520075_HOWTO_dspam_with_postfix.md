---
title: "HOWTO: dspam with postfix"
date: 2007-08-07
forum: Server Platforms
---

### Post by gene02 on 2007-08-07
**[SIZE="6"]HOWTO dspam with postfix[/SIZE]**

[dspam]("http://dspam.nuclearelephant.com/") is a spam filter for mail servers.  I have found it to be less of a resource hog than spamassassin and easier to retrain.  It took me a while to get a robust dspam installation going with email-based retraining support.  The best tutorial I found was [http://dspamwiki.expass.de/Installation/Postfix/NealesSetup]("http://dspamwiki.expass.de/Installation/Postfix/NealesSetup"), but I had to make some small modifications to get it working the way I wanted.  This is my tutorial for how to get mysql-backed dspam running on a postfix-based system:


You should already have a running postfix and mysql installation.

Install the following packages:
[INDENT]
dspam
dspam-doc
libdspam7
libdspam7-drv-mysql
[/INDENT]

I found that the mysql database, user, and tables were not automatically created, so I manually created a dspamdb mysql database and dspam user for that database.  Then I created the tables: 
```

mysql -u dspam -p -D dspamdb < /usr/share/doc/libdspam7-drv-mysql/mysql_objects-XXX.sql
mysql -u dspam -p -D dspamdb < /usr/share/doc/libdspam7-drv-mysql/virtual_users.sql

```

Note that mysql_objects-XXX.sql is one of the /usr/share/doc/libdspam7-drv-mysql/mysql_objects-*.sql files.  Choose whichever looks the most appropriate.

If you don't see /etc/dspam/dspam.d/mysql.conf, copy it from /usr/share/doc/libdspam7-drv-mysql/ and edit the user, password, and database name configuration near the top of the file.

Now, edit the dspam configuration at /etc/dspam/dspam.conf.  We will be configuring dspam to deliver all mail, tagged as spam or innocent, rather than quaranteening it.  Users can then forward mistagged emails to dspam for retraining.  dspam will be called from postfix and re-inject the tagged email back into the postfix pipeline.

First make sure it is set up to use mysql, by checking that the StorageDriver line says:
```

StorageDriver /usr/lib/dspam/libmysql_drv.so

```

We will use postfix's fake sendmail as the trusted delivery agent:
```

TrustedDeliveryAgent "/usr/sbin/sendmail"

```

And comment out the untrusted delivery agent:
```

#UntrustedDeliveryAgent "/usr/bin/procmail -d %u"

```

Comment out all the delivery configuration as the emails will be injected into postfix's own delivery pipeline:
```

#DeliveryHost        127.0.0.1
#DeliveryPort        10026
#DeliveryIdent       localhost
#DeliveryProto       SMTP

```

Comment out all the trusted users except for these:
```

Trust root
Trust dspam
Trust mail
Trust postfix

```

Change the Preference section to deliver all emails, whether spam or not, and put the dpsam signature in the headers.  This will mean that you need to include the headers when forwarding emails for retraining:
```

Preference "spamAction=deliver"
Preference "signatureLocation=headers"  # 'message' or 'headers'
Preference "showFactors=off"
Preference "spamSubject=SPAM"
#Preference "spamAction=tag"
#Preference "signatureLocation=message"  # 'message' or 'headers'
#Preference "showFactors=on"
#Preference "spamAction=tag"
#Preference "spamSubject=SPAM"

```

Change ServerParameters to deliver all email:
```

ServerParameters        "--deliver=innocent, spam"

```

[COLOR="Red"]Woops, I forgot to mention this in the original edit:[/COLOR]
Edit /etc/default/dspam and change "START=no" to "START=yes"


Next, we have to modify the postfix configuration to work with dspam.  Make backup copies of any file that you modify here so that you can quickly roll it back if there are any problems. 

Edit /etc/postfix/master.cf and add these lines:
```

dspam   unix    -       n       n       -       10      pipe
  flags=Ru user=dspam argv=/usr/bin/dspam --deliver=innocent,spam --user $user -i -f $sender -- $recipient
dspam-retrain   unix    -       n       n       -       10      pipe
  flags=Ru user=dspam argv=/usr/local/bin/dspam-retrain $nexthop $sender $recipient

```

That will set up dspam as a transport which gets invoked for each incoming email.  We'll get back to dspam-retrain later.


Edit /etc/postfix/main.cf.  

This cludge will setup postfix so that only incoming mail gets filtered by spamd. Include, as the last restriction, the following smtpd_recipient_restrictions line:
```

   check_client_access pcre:/etc/postfix/dspam_filter_access

```

This is my full smptd_recipient_restrictions as illustration.  Don't copy the whole thing unless you know what all the lines mean, this can break your postfix setup!
```

smtpd_recipient_restrictions = 
                reject_unauth_pipelining
                reject_non_fqdn_recipient
                reject_non_fqdn_hostname
                reject_non_fqdn_sender
                permit_mynetworks
                permit_sasl_authenticated
                reject_unauth_destination
                reject_invalid_hostname
                reject_unknown_recipient_domain
                check_policy_service inet:127.0.0.1:10031
                reject_unlisted_recipient
                check_recipient_access hash:/etc/postfix/access
                check_policy_service inet:127.0.0.1:12525
                check_client_access pcre:/etc/postfix/dspam_filter_access
                permit

```

create the file /etc/postfix/dspam_filter_access with the following contents:
```

/./     FILTER dspam:dspam

```

Add these dspam config lines at the end of main.cf:
```

dspam_destination_recipient_limit = 1
dspam-add_destination_recipient_limit = 1
dspam-fp_destination_recipient_limit = 1

```

In order to do the retraining, we need to set up some special dspam email addresses.  Create the file /etc/postfix/transport with the following contents:
```

spam@your.server    dspam-retrain:spam
ham@your.server     dspam-retrain:innocent

```
your.server should be your mail server domain.

Edit the transport_maps section of main.cf to include:
```

transport_maps = hash:/etc/postfix/transport

```

Apparently, dpsam gets run before aliases are read, so move all aliases in /etc/aliases into /etc/postfix/virtual.
Update the local_recipient_maps line to include virtual and transport:
```

local_recipient_maps = proxy:unix:passwd.byname $alias_maps hash:/etc/postfix/virtual $transport_maps

```

Finally, make sure to uncomment the recipient_delimiter line.  We'll be using this for retraining:
```

recipient_delimiter = -

```


The last missing piece is the retrain script.  This will parse the misclassified emails forwarded to dspam for retraining.  I modified the version at [http://dspamwiki.expass.de/Installation/Postfix/NealesSetup]("http://dspamwiki.expass.de/DspamRetrainScript") to make it a little more robust and to report through syslog.  You can find my version at [http://www.smalltime.com/gene/dspam-retrain.pl.gz]("http://www.smalltime.com/gene/dspam-retrain.pl.gz").  My version requires the installation of the Logger::Syslog perl module.
```

wget http://www.smalltime.com/gene/dspam-retrain.pl.gz
gunzip dspam-retrain.pl.gz
sudo mv dspam-retrain.pl /usr/local/bin/dspam-retrain
sudo chmod 744 /usr/local/bin/dspam-retrain
sudo cpan -e shell
 <... answer all the questions if you've never used CPAN before ...>
 install Logger::Syslog
 exit

```

At this point we should be just about ready to go.  Now we just need to get everything reloaded:
```

sudo /etc/init.d/dspam restart
sudo postalias /etc/aliases
sudo postmap /etc/postfix/dspam_filter_access
sudo postmap /etc/postfix/transport
sudo postmap /etc/postfix/virtual
sudo postfix reload

```

Now try sending yourself an email and see if it gets through.  It should have an X-Dspam-Result header line.  Keep an eye on /var/log/syslog and if anything looks amiss, revert to your backup postfix files while you figure out what the problem was.


For retraining, forward missed spams to [email]spam-username@your.serv[/email]er and falsely tagged innocent emails to [email]ham-username@your.serv[/email]er, where username is your user name and your.server is your server domain name.  Make sure that the X-Dspam-Signature header line is included in any forwarded retrain emails.  You can take a look at the dspam stats after a few emails have gone through with this command:
```

sudo dspam_stats -H

```
You can also use the dspam_train command to get the dspam database up and running if you already have a collection of known good and spammy emails.

Please let me know if you try to follow this and have any problems or corrections.

---

### Post by tim_astley on 2007-08-16
I followed your instructions below and everything stopped :confused:

I had a few problems following the instructions.  I'll list them incase my work around is at fault - which it probably is.

I didn't have a transport_maps section in my main.cf

So I put your line in at the end of main.cf
I also didn't have a local_recipient_maps line so I added that to end of main.cf also.  Though I wasn't sure that was where it should be. Should it have been in virtual?
When I ran
postmap /etc/postfix/virtual
It was very upset about the format of the virtual file - I just copied /etc/aliases into /etc/postfix/virtual - could this be a problem?
 
I noticed that postfix complained that a dictionary (pcre) wasn't installed.  I just installed it and restarted postifx and that was fixed. 

When I tried to email myself I got nothing though lots of traffic seemed to be going through the server - according to mail.log and syslog.  Though - I was emailing an address that was aliased.  I wonder.

Can you shed any light on possible errors?

Further update - I scouted around and another site suggested I should
vi /etc/default/dspam and change START=no to START=yes
I did that and when I restarted dspam I got some positive responses - but on restarting postfix - email dried up.
When I changed the main.cf and master.cf back everything works fine.  So one of them must be wrong I guess.

Tim

---

### Post by gene02 on 2007-08-16
Make sure that where you define transport_maps:
```

transport_maps = hash:/etc/postfix/transport

```
comes before any usage of $transport_maps.  I have mine just before the local_recipient_maps line.

I'm surprised that you don't have a local_recipient_maps section.  You don't have a section in main.cf that starts like this?
```

# REJECTING MAIL FOR UNKNOWN LOCAL USERS
#
# The local_recipient_maps parameter specifies optional lookup tables
# with all names or addresses of users that are local with respect
# to $mydestination, $inet_interfaces or $proxy_interfaces.

```

In my file it is just after the definiton of mydestination.  This is all in main.cf

Can you post the contents of your /etc/postfix/virtual file (without giving away any state secrets)?  Here is an edited excerpt from mine with all domains and usernames altered:
```

# Added by installer for initial user
root    admin_user

# Basic system aliases -- these MUST be present.
MAILER-DAEMON   postmaster
postmaster       admin_user
support             admin_user
abuse               admin_user
logcheck           admin_user

# my aliases
alias1@my.domain   user1
alias2@my.domain   user1
alias3@my.domain   user2

```


You are right about editing /etc/default/dspam  to START=yes, I forgot to mention that.

---

### Post by tim_astley on 2007-08-17
I also have the transport_maps right before the local_recipient_maps line - both at the very end of main.cf.  I don't have the section in main.cf you quote.  I am not sure how old my postfix is but it is up to date.  My main.cf may come from a pretty old distribution though.

I won't post my virtual file just yet - but the difference I can spot is that I have 
root: admin_user

I think it may have been the colons it was complaining about.  I run some mailman mailing lists also and I am used to fiddling with /etc/aliases 
Can I remove the : and have it still work?  You run postalias on the aliases file.  I have always used newaliases.  This may be where the problems lie.

Thanks for your help

Tim

---

### Post by hollymcr on 2007-09-04
I've followed this HowTo from scratch on a fresh 7.04 server install, and I've ended up with a working Postfix install, but although dspam seems to be there and the logs suggest its being used, I'm not getting anything in my headers to show that dspam is really being called.

The log (/var/log/mail.info) says things like:
```
Sep  5 00:39:16 testmail postfix/smtpd[6045]: warning: 10.0.0.17: hostname pc-00017.mytestdomain.co.uk verification failed: Name or service not known
Sep  5 00:39:16 testmail postfix/smtpd[6045]: connect from unknown[10.0.0.17]
Sep  5 00:39:39 testmail postfix/smtpd[6045]: NOQUEUE: filter: RCPT from unknown[10.0.0.17]: <unknown[10.0.0.17]>: Client host triggers FILTER dspam:dspam; from=<mark@myothertestdomain.co.uk> to=<webadmin@testmail.mytestdomain.co.uk> proto=SMTP
Sep  5 00:39:39 testmail postfix/smtpd[6045]: 4DF5F1806A: client=unknown[10.0.0.17]
Sep  5 00:39:50 testmail postfix/cleanup[6058]: 4DF5F1806A: message-id=<20070904233939.4DF5F1806A@testmail.mytestdomain.co.uk>
Sep  5 00:39:50 testmail postfix/qmgr[5789]: 4DF5F1806A: from=<mark@myothertestdomain.co.uk>, size=395, nrcpt=1 (queue active)
Sep  5 00:39:50 testmail postfix/pickup[5788]: D141E18070: uid=107 from=<mark@myothertestdomain.co.uk>
Sep  5 00:39:50 testmail postfix/cleanup[6058]: D141E18070: message-id=<20070904233939.4DF5F1806A@testmail.mytestdomain.co.uk>
Sep  5 00:39:50 testmail postfix/pipe[6059]: 4DF5F1806A: to=<webadmin@testmail.mytestdomain.co.uk>, relay=dspam, delay=21, delays=21/0.01/0/0.07, dsn=2.0.0, status=sent (delivered via dspam service)
Sep  5 00:39:50 testmail postfix/qmgr[5789]: 4DF5F1806A: removed
Sep  5 00:39:50 testmail postfix/qmgr[5789]: D141E18070: from=<mark@myothertestdomain.co.uk>, size=517, nrcpt=1 (queue active)
Sep  5 00:39:50 testmail postfix/local[6064]: D141E18070: to=<webadmin@testmail.mytestdomain.co.uk>, relay=local, delay=0.07, delays=0.04/0.01/0/0.01, dsn=2.0.0, status=sent (delivered to mailbox)
Sep  5 00:39:50 testmail postfix/qmgr[5789]: D141E18070: removed
Sep  5 00:41:51 testmail postfix/smtpd[6045]: disconnect from unknown[10.0.0.17]

```

There's nothing in the mail.err log.

Note that 10.0.0.17 is my desktop that I'm testing from, and the test server is a virtual server on my LAN. The test mail is via a telnet to port 25:
```
220 testmail.mytestdomain.co.uk ESMTP Postfix (Ubuntu)
MAIL FROM: mark@myothertestdomain.co.uk
250 2.1.0 Ok
RCPT TO: webadmin@testmail.mytestdomain.co.uk
250 2.1.5 Ok
DATA
354 End data with <CR><LF>.<CR><LF>
Subject: test

Help
.
250 2.0.0 Ok: queued as 4DF5F1806A
quit
221 2.0.0 Bye
```
.. and the resulting mail header is:
```
From mark@myothertestdomain.co.uk  Wed Sep  5 00:10:41 2007
Return-Path: <mark@myothertestdomain.co.uk>
X-Original-To: webadmin@testmail.mytestdomain.co.uk
Delivered-To: webadmin@testmail.mytestdomain.co.uk
Received: by testmail.mytestdomain.co.uk (Postfix, from userid 107)
        id 8D57318070; Wed,  5 Sep 2007 00:10:41 +0100 (BST)
Received: from localhost (localhost [127.0.0.1])
        by testmail.mytestdomain.co.uk (Postfix) with SMTP id 569111806A
        for <webadmin@testmail.mytestdomain.co.uk>; Wed,  5 Sep 2007 00:10:15 +0100 (BST)
Subject: test again
Message-Id: <20070904231026.569111806A@testmail.mytestdomain.co.uk>
Date: Wed,  5 Sep 2007 00:10:15 +0100 (BST)
From: mark@myothertestdomain.co.uk
To: undisclosed-recipients:;

```

There's no X-Dspam-Result header or any other indication that Dspam is being called. /var/log/dspam is an empty directory.

Any suggestions?

---

### Post by gene02 on 2007-09-24
It sounds like the postfix configuration is correct, but something is wrong with dspam.  Do you have logging on in /etc/dspam/dspam.conf?  That's probably the only way to figure out what the problem is.  I have these settings in dspam.conf:

SystemLog on
UserLog   on
OnFail error

Also, I have 'Opt out' set:
Opt out

Otherwise, each user needs to opt in manually to dspam filtering.

---

### Post by Slotos on 2008-03-17
Why are you launching dspam lmtp daemon if you're using dspam agent for processing?

And in my opinion "Opt out" should be mentioned in the HowTo.

---

