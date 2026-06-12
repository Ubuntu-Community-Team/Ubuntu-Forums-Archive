---
title: "amavis connection refused and spam mails are not tagged"
date: 2006-11-03
forum: Server Platforms
---

### Post by neversfelde on 2006-11-03
Hey there,

I've set up a mailserver for the first time and postfix delivery and cyrus imap are working fine. i used [this]("https://help.ubuntu.com/community/PostfixAmavisNewClamAVSpamAssassin") howto in the ubuntu wiki.

After the first setup I wanted to integrate amavis spam and virus scanner. I had several problems with clamav, so I decided to concentrate on the spam function. So I onyi commented out the

> @bypass_spam_checks_maps = (
   \%bypass_spam_checks, \@bypass_spam_checks_acl, \$bypass_spam_checks_re);

section in /etc/amavis/conf.d/15-content:filter_mode.

/etc/amavis/con.d/50-user looks like this

> $final_virus_destiny = D_PASS; # (data not lost, see virus quarantine)
$final_banned_destiny = D_PASS; # D_REJECT when front-end MTA
$final_spam_destiny = D_PASS;
$final_bad_header_destiny = D_PASS;     # False-positive prone (for spam)

$sa_tag_level_deflt = -1000;

$sa_tag2_level_deflt = 5.0;

$sa_kill_level_deflt = 10;

$sa_spam_subject_tag = '***SPAM*** ';


in order to test amavis. I'm glad that postfix delivers the mails further on, but now there is an error like this in in /var/log/mail.info

> postfix/qmgr[30531]: warning: connect to transport amavis: Connection refused


it might not have any effects, but I'm interested in removing it.

Spam should be detected by amavis and spamassassin because theres a line like this

> amavis[30533]: (30533-02) Passed SPAM, LOCAL [127.0.0.1] [64.223.35.177] <SRS0=gsgM=EP=angleseyinteractive.com=debutante@srs.kundenserver.de> -> chrman@localhost>, quarantine: /var/lib/amavis/quarantine, Message-ID: <C825ED37.5429735@angleseyinteractive.com>, Resent-Message-ID: <200611031557.17309.debutante@angleseyinteractive.com>, active.com>, mail_id: 0W0ZJ27qGXZN, Hits: 7.239, 19730 ms


When I'm changing the handling method for spam in D_REJECT Spam is not delivered to the clients anymore, so everything shoul be alright., shouldn't?
The real problem is that Spam emails are not tagged with ***SPAM*** and thats the way I want to use it.

So what am I doing wrong? Would be great if anybody woul be able to help me to solve this problem. By the way, I`m using Dapper LTS.

Thanks for reading


Christian

---

### Post by neversfelde on 2006-11-03
I found this in launchpad

> The default config fails to define @local_domains_maps, ergo no recipient is considered local. This is bad.
Adding either
@local_domains_acl = ( ".$mydomain" );
or
@local_domains_maps = ( [".$mydomain"] );
to the config will fix this problem.

So it might be a problem with the domain configuration, so I added "@local_domains_maps = ( [".$mydomain"] );" to 50-user. But no result. I'm trying :)

---

### Post by neversfelde on 2006-11-03
The problem with the tag is solved. Reconfigure the domains was the right way. But how about the "connection refused" message?

---

### Post by fiery on 2006-11-21
Hey neversfelde, 

I was getting a 'connection refused' message as well. My mail.log was showing:
  Nov 20 19:35:48 hostname postfix/smtp[4054]: 475488F9D6:
  to=<user@localhost>, relay=none, delay=9009, delays=9008/0.7/0.06/0,
  dsn=4.4.1, status=deferred (connect to 127.0.0.1[127.0.0.1]: Connection
  refused)
  Nov 20 19:35:48 hostname postfix/smtp[4054]: fatal: valid hostname or
  network address required in server description: (127.0.0.1):10024

And when debugging amavis I was presented with the following error:
  The value of variable $myhostname is "", but should have been
  a fully qualified domain name; perhaps uname(3) did not provide such.
  You must explicitly assign a FQDN of this host to variable $myhostname
  in amavisd.conf, or fix what uname(3) provides as a host's network name!

I couldn't work out what was going on as I had completed the already in place line/setting in /etc/amavis/conf.d/05-node_id:
  chomp($myhostname = `hostname.example.tld`);
  
Even after looking through all the the files within /etc/amavis/conf.d/ left me stumped as there was no where else to fill in. I was especially confused about 'The value of variable $myhostname is ""', when it was definitely filled out in 05-node_id.

I fixed both problems by adding the following to /etc/amavis/conf.d/50-user:
  $myhostname = "hostname.example.tld";
I got this from: [http://openmailadmin.ossdl.de/wiki/howto/Postfix-SASL-Cyrus-MySQL-Amavis-Postgrey-SpamAssassin-ClamAV-Squirrelmail-Mailman-Mailgraph-OMA](http://openmailadmin.ossdl.de/wiki/howto/Postfix-SASL-Cyrus-MySQL-Amavis-Postgrey-SpamAssassin-ClamAV-Squirrelmail-Mailman-Mailgraph-OMA)

The confusion for me is that while the old amavis.conf (prior to Debian splitting it into all the different files under /conf.d) file held all the options and comments, allowing you to uncomment out as was needed, the new 50-user contains pretty much nothing, other than a link to /usr/share/doc/amavisd-new/ which unfortunately has the old amavis.conf info (under the 'examples' directory), and no actual example of the new conf.d files... Going to the amavisd-new website ([http://www.ijs.si/software/amavisd/amavisd-new-docs.html](http://www.ijs.si/software/amavisd/amavisd-new-docs.html)) doesn't help either as they don't use the conf.d split-config-files way of doing things. 

Looking at flurdy's page ([http://flurdy.com/docs/postfix/#conf_cont](http://flurdy.com/docs/postfix/#conf_cont)) I can see that there are many more settings I need to populate 50-user with to get spam and virus scanning working properly, but I am just happy that I can finally receive emails. :-D (I'll take my time and work my way through the rest of the settings in a couple of days once my stress levels have gone back down.) 

The fact that we need to add all this extra info to 50-user is unfortunately probably very obvious to the more knowledgeable types, but it left me banging my head for days! 

I hope this post helps you neversfelde, as well as any others out there!

Cheers,

---

