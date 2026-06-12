---
title: "Mail Server"
date: 2013-11-26
forum: Server Platforms
---

### Post by wolfgentleman on 2013-11-26
I have been having a heck of a time trying to get a fully functional mail server up. I have dovecot setup(everything except for the folders) but postfix is being a pain in the butt. First I can't seem to get it to use dovecot for auth or mail delivery. Second the file it uses to store mail is flooded with output from cron jobs. Is there any user friendly command line interface like aptitude for apt to configure postfix and dovecot? If not, any tutorials, links, and suggestions would be appreciated.

Sorry if my spelling is off I am on my tablet ATM.

---

### Post by nerdtron on 2013-11-26
I think it would be better to have a working system and then study how it works.
Here's the mail solution we use. Installation is very easy.
[http://www.iredmail.org/install_iredmail_on_ubuntu.html](http://www.iredmail.org/install_iredmail_on_ubuntu.html)

---

### Post by wolfgentleman on 2013-11-26
> **nerdtron said:**
> I think it would be better to have a working system and then study how it works.Here's the mail solution we use. Installation is very easy.[http://www.iredmail.org/install_iredmail_on_ubuntu.html](http://www.iredmail.org/install_iredmail_on_ubuntu.html)
From the first couple of sections that is not a viable solution due not being able to spare more than 100MB of RAM and I cannot remove MySQL because it is used in the website and external apps. Also I have 3 domains pointing to the server so I can't set the FQDN. Only one domain will be using the mail server and I will be the only one using it so it only needs one user. I want to set up a single-user IMAP server with a catchall address. So is there any way I can set it up without hassle or removing packages (not counting dovecot and postfix)?

---

### Post by nerdtron on 2013-11-26
If you read the notes, it assumes that you must install it on a freshly installed ubuntu server. And since you just need it for a single domain, single catchall account, you can just spin up a virtual machine with 512MB of ram. You can even remove the clamAV and spamassasin to reduce ram usage.
But if you are out of hard ware, I can't help you.
And since you want to have a mail server on an existing production machine, you really need to do the hard work of manual configuration.
Any particular problems you are having in dovecot? Do you have any related logs? And can you post your postfix configuration?

---

### Post by wolfgentleman on 2013-11-26
For the most part dovecot is configured, I just need to fix the IMAP folders of which I don't know how to do yet. Postfix OTOH is a complete wreck. It uses system users rather than dovecot, it uses /var/mail/user to deliver mail rather than dovecot, and the file is flooded with cron output. I have the catchall setup temporaraly as a system user of mailbox so it redirects everything to /var/mail/mailbox.

---

### Post by wolfgentleman on 2013-11-30
Bump... attaching postfix configs
[ATTACH]248216[/ATTACH]

---

### Post by wolfgentleman on 2013-12-02
bump

---

### Post by wolfgentleman on 2013-12-03
Where is a service I can host a mail server with the following:
Single Catchall Inbox with Multi-Login
IMAP
SSL
External Access
Use a pre-existing domain

The budget is $20. It would be nice if it had a web interface and that I could point a subdomain at it, but it is not a necessity.

---

### Post by bigmonmulgrew on 2013-12-05
Hi
Just a thought. My Brother and I recently discussed setting up a mail server.
I played about with the stuff ing the Ubuntu guide. My brother (having no linux experience) set Citadel up in about half an hour. Might be worth a look as an alternative.
[http://www.citadel.org/](http://www.citadel.org/)

---

### Post by kustomjs on 2013-12-05
iredmail is about the most easiest mail server you use I am using it and I didnt any problems setting it up.

---

### Post by SeijiSensei on 2013-12-05
> **wolfgentleman said:**
> The budget is $20. It would be nice if it had a web interface and that I could point a subdomain at it, but it is not a necessity.

If that's a monthly figure, you can have a complete virtual Linux server at [Linode](http://www.linode.com/).  The basic machine has 1 GB of memory and 48 GB of storage.

---

### Post by CharlesA on 2013-12-05
> **SeijiSensei said:**
> If that's a monthly figure, you can have a complete virtual Linux server at [Linode](http://www.linode.com/).  The basic machine has 1 GB of memory and 48 GB of storage.

+1. I just moved my mail server to [RamNode]("http://ramnode.com/") because they had a 42% off special for their SSD and SSD-cached VPSes. Totally worth it.

Ramnode has a 1GB OpenVZ VPS for $15 a month and a KVM VPS for $24 a month.

---

### Post by wolfgentleman on 2013-12-07
> **SeijiSensei said:**
> If that's a monthly figure, you can have a complete virtual Linux server at [Linode]("http://www.linode.com/").  The basic machine has 1 GB of memory and 48 GB of storage.

So it would be fully setup for me? Mail server, Apache, MySQL, SSH, ect? I need a pgp keyserver as well would I be able to have that preinstalled as well or will I need to install from SSH?

---

### Post by CharlesA on 2013-12-07
> **wolfgentleman said:**
> So it would be fully setup for me? Mail server, Apache, MySQL, SSH, ect? I need a pgp keyserver as well would I be able to have that preinstalled as well or will I need to install from SSH?

Why would you need a pgp key server?  If you do buy a VPS, it'll have SSH installed by default and you manage it entirely via ssh (unless you install something like Webmin, cPanel or the like). This means you would need to set it up, make sure it is secure, and then make sure updates are applied, etc.

Have a read here:
[https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql](https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql)

That is how I have my mail server setup. Of course my mail server is also running spamassassin and other stuff, but that should get your a basic mail server setup and running.

---

### Post by wolfgentleman on 2013-12-07
> **wolfgentleman said:**
> So it would be fully setup for me? Mail server, Apache, MySQL, SSH, ect? I [s]need[/s] really want a pgp keyserver as well would I be able to have that preinstalled as well or will I need to install from SSH?

> **CharlesA said:**
> Have a read here:
[https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql](https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql)

That is how I have my mail server setup. Of course my mail server is also running spamassassin and other stuff, but that should get your a basic mail server setup and running.
I was hoping I would just be able to select mail server, apache, mysql, ssh, ect on a setup menu or something... I will probably switch to linode anyway as they have a setup double what I have now for only $3 more, but I will have to do it after new years. Either way I will need to get the mail server running...

---

### Post by nerdtron on 2013-12-07
That why I recommended installing iRedMail. It's like installing a windows program. Run the installer, select yes, yes, next...provide details.. nah..

Kidding aside, (seriously) it's really simple, after you setup your server, try to run the installer for iredmail. After the installation, (probably in 5 minutes if you have fast internet) your complete mail server is done. No coding is even required.

---

### Post by CharlesA on 2013-12-07
> **nerdtron said:**
> That why I recommended installing iRedMail. It's like installing a windows program. Run the installer, select yes, yes, next...provide details.. nah..

Kidding aside, (seriously) it's really simple, after you setup your server, try to run the installer for iredmail. After the installation, (probably in 5 minutes if you have fast internet) your complete mail server is done. No coding is even required.

+1. I looked into using it originally, but decided against it cuz the memory footprint was a bit high.

Of course, now my production web server has everything iRedMail has minus the iRedMail control panel thing and the memory usage is about the same.

When you do get the server installed, if you don't already have a firewall setup, check out CSF:
[http://configserver.com/cp/csf.html](http://configserver.com/cp/csf.html)

---

### Post by wolfgentleman on 2013-12-07
> **nerdtron said:**
> That why I recommended installing iRedMail. It's like installing a windows program. Run the installer, select yes, yes, next...provide details.. nah..

Kidding aside, (seriously) it's really simple, after you setup your server, try to run the installer for iredmail. After the installation, (probably in 5 minutes if you have fast internet) your complete mail server is done. No coding is even required.

That's what I figured I would do after switching to Linode is install the bare minimum Ubuntu Server, install iredmail, follow their wiki on removing spam detection and filtering (been wanting to get the game server off the home network), install the parts of a webserver that it did not, install sks, then restore backups of database

---

### Post by wolfgentleman on 2014-01-04
Ok, finally go setup on Linode. iRedMail is not as easy as stated. I have managed fix most errors, however iredadmin is not working fully. I keep getting "**Error:** (1054, "Unknown column 'language' in 'field list'")". Also the install seemed to go fine, but it didn't configure itself - only MySQL, Apache, Dovecot, Postfix, ect. I followed their tut for disabling antivirus/antispam, but rather than disabling ClamAV and Amavisd I removed them, deleting the line it says to comment out in main.cf. Also I had to fix some things in the Apache config as I needed it to use mail.twprogrammers.com for webmail/admin panel/ect and not redirect EVERYTHING to webmail. So I don't know what is working and what isn't with the admin panel. Roundcube gives a can't connect error, turns out it didn't configure it either. I tried to fix that one to no avail, but will search tomorrow as well as post configs of everything as well as an sql dump of my mail-related databases. Thanks for suggesting Linode. I am loving it so much better.

---

### Post by nerdtron on 2014-01-05
You installed iredmail on a *fresh* installation of Ubuntu server 12.04 right?
You should have any problems. Anyway, go over to the iredmail forums, the developer is very active answering support questions.
Goodluck!

---

### Post by pft42 on 2014-01-05
Hi,

just came back to this forum after a long time. 
Looking at initial posts of this thread I wonder whether the solution might just be two lines away.
You say dovecot is working - fine (though not sure how you proved it)
Now dovecot has on imagination where inbox lies what what format to use. Postfix has one too. Just need to get both in sync.
In my case this:
   /etc/postfix/main.cf:home_mailbox = Maildir/
   /etc/dovecot/conf.d/10-mail.conf:mail_location = maildir:~/Maildir
This should give you basic operation. SSL etc. is for further work after this

Thomas

---

### Post by wolfgentleman on 2014-01-05
> **nerdtron said:**
> You installed iredmail on a *fresh* installation of Ubuntu server 12.04 right?
You should have any problems. Anyway, go over to the iredmail forums, the developer is very active answering support questions.
Goodluck!
Yes, I had a fresh install of Ubuntu 12.04. Rather than exporting an IMG from the Rackspace server I just backed up /home /etc/apache2 /etc/passwd /etc/shadow /etc/group /etc/gshadow and a few others then did a MySQL dump.


Here is what I did:
[LIST=1]
[*]Installed Ubuntu 12.04 on my Linode 
[*]Downloaded and installed iRedMail 
[*]Followed their wiki tutorial on disabling spam/virus scanning but removed rather than disabled Amavisd, ClamAV, and spamassassin, then *tested it some but came up with errors*:
[LIST]
[*]iredadmin
[LIST=1]
[*]"internal server error" - fixed (vmail database had no tables) 
[*]login page --> username, password, enter --> "internal server error" - fixed (forgot to add myself to vmail tables) 
[*]then login page --> username, password, enter --> (Admin|Preferences --> Save) --> "Error: (1054, "Unknown column 'language' in 'field list'")" - not fixed and haven't found anything useful 
[/LIST]
  
[*]roundcube
[LIST=1]
[*]"DATABASE ERROR: CONNECTION FAILED! Unable to connect to the database! Please contact your server-administrator." - not fixed but haven't had a chance to search 
[/LIST]
            
[/LIST]
  
[*]Imported my MySQL dump 
[*]Merged:
[LIST]
[*]Apache configs (modifying a few things to use mail.twprogrammers.com instead of any domain) 
[*]/etc/passwd 
[*]/etc/shadow 
[*]/etc/group 
[*]/etc/gshadow 
[/LIST]
  
[*] Installed sks, reprepro, ect. 
[/LIST]
 So I don't know if anything is working on the mail system...
[S]Attaching[/S] Too big (~3.3MB) so I am uploading to my site: [here is the link]("http://downloads.twprogrammers.com/configs+logs.tar.bz2") all configs/logs/dumps related to the mailing system.
> **pft42 said:**
> Hi,

just came back to this forum after a long time. 
Looking at initial posts of this thread I wonder whether the solution might just be two lines away.
You say dovecot is working - fine (though not sure how you proved it)
Now dovecot has on imagination where inbox lies what what format to use. Postfix has one too. Just need to get both in sync.
In my case this:
   /etc/postfix/main.cf:home_mailbox = Maildir/
   /etc/dovecot/conf.d/10-mail.conf:mail_location = maildir:~/Maildir
This should give you basic operation. SSL etc. is for further work after this

Thomas
You kinda lost me there...

---

### Post by CharlesA on 2014-01-05
If you installed iredmail on a clean VPS, it should have worked fine. Did you test it before importing the password and shadow files?

That will screw with user/group IDs, which can be a mess to fix.

---

### Post by wolfgentleman on 2014-01-05
> **CharlesA said:**
> If you installed iredmail on a clean VPS, it should have worked fine. Did you test it before importing the password and shadow files?

That will screw with user/group IDs, which can be a mess to fix.

Yes

I also merged php.ini because I increased the upload limit to 25M and some of the error display settings.

---

### Post by CharlesA on 2014-01-05
Huh. The last time I installed iRedMail was on a Debian Squeeze box, but it should work fine on 12.04.

If you want to do it on your own terms, check this out (Linode ftw):
[https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql](https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql)

---

### Post by wolfgentleman on 2014-01-05
[SIZE=5]YES! HAHAHAHAHA![SIZE=3][/SIZE][/SIZE]
I finally got it working! Thank you CharlesA! That link fixed everything! Just used Thunderbird to add folders and perfecto! And thank you SeijiSensei for suggesting Linode. It is MUCH better than Rackspace, for $3 more I get 2x the ram and more than 2x the storage and a much more manageable control panel (although the theme is horrendous). I appreciate all of the time y'all took to help me and I am very grateful.

---

