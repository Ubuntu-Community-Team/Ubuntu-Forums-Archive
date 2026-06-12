---
title: "Seeking webmail package recommendation"
date: 2008-07-04
forum: Server Platforms
---

### Post by satimis on 2008-07-04
Hi folk,s


Ubuntu LAMP 6.06 amd64
Postfix


I'm running SquirrelMail as webmail.  I'm searching for a better feature webmail.  What other webmail package would you recommend, preferrable available on repo.


I have no strong object on installing it on package download on its official site.  However for easy upgrade in future I prefer its package being available on repo.


TIA


B.R.
satimis

---

### Post by windependence on 2008-07-04
Well it's not in the repo (I don't think) but Zimbra would be perfect for this. 6.06 supports Zimbra out of the box.

-Tim

---

### Post by Dr Small on 2008-07-04
I use SqWebMail, but it was a little bit difficult to setup.

---

### Post by ixus_123 on 2008-07-04
I think roundcube looks pretty sweet although I have no experience with it apart from using the demo on their site.

[http://roundcube.net/]("http://roundcube.net/")

---

### Post by bmathis on 2008-07-04
+1 for Zimbra... needs a base install without lamp though.

[http://www.zimbra.com](http://www.zimbra.com)

---

### Post by satimis on 2008-07-05
Hi folks,


Thanks for your advice.


The box I'm prepared exploring new webmail is a LAMP server, headless, having following packages running on it.


Ubuntu LAMP 6.06 amd64
Apache2
MySQL-5
Postfix
Cyrus-imap
php5
SugerCRM, community edition

SquirrelMail (which was installed on repo.  I'm prepared removing it latter)


I tried installing roundcube-webmail on another Ubuntu LAMP server, 7.04 amd64) a year ago without success.  Finally I installed SM which is running until now.  SM was downloand on its official site.  Roundcube-webmail was installed on repo.


I found following webmail packages on repo;


$ apt-cache roundcube-webmail```

E: Invalid operation roundcube-webmail
satimis@satimis:~$ apt-cache policy roundcube-webmail
roundcube-webmail:
  Installed: (none)
  Candidate: 0.1-20051021-0ubuntu1
  Version table:
     0.1-20051021-0ubuntu1 0
        500 http://archive.ubuntu.com dapper/universe Packages

```


$ apt-cache policy horde3```

horde3:
  Installed: (none)
  Candidate: 3.1.1-1
  Version table:
     3.1.1-1 0
        500 http://archive.ubuntu.com dapper/universe Packages

```


$ apt-cache policy sqwebmail```

sqwebmail:
  Installed: (none)
  Candidate: 0.47-13ubuntu5
  Version table:
     0.47-13ubuntu5 0
        500 http://archive.ubuntu.com dapper/universe Packages

```


$ apt-cache search zimbra
$ apt-cache search citadel
both without printout.


I visited Zimbra site and its forum 
[http://www.zimbra.com/](http://www.zimbra.com/)

Forum;
[http://www.zimbra.com/forums/](http://www.zimbra.com/forums/)

and found heavy traffic on the latter.  Many postings were there, i.e. many users.


I looked at the archieve of Horde mailing list, quite heavy traffics.  


Regarding Citadel;
Email and Groupware for Web 2.0
[http://www.citadel.org/doku.php?id=start](http://www.citadel.org/doku.php?id=start)

Maillist archieve
[http://www.mail-archive.com/room_citadel_support%40uncensored.citadel.org/](http://www.mail-archive.com/room_citadel_support%40uncensored.citadel.org/)
also heavy traffice was there.


Regarding sqwebmail;
SqWebMail is the webmail module that's bundled with the Courier mail server. 
[http://www.courier-mta.org/sqwebmail/](http://www.courier-mta.org/sqwebmail/)


I'm running cyrus-imap.  I don't know whether it works on my box.  There is no mailing list archieve;

[http://sourceforge.net/mailarchive/forum.php?forum_name=courier-sqwebmail](http://sourceforge.net/mailarchive/forum.php?forum_name=courier-sqwebmail)


Further advice/comment would be appreciated.  TIA


B.R.
satimis

---

### Post by scotty64 on 2008-07-10
> **satimis said:**
> Hi folks,


Thanks for your advice.


The box I'm prepared exploring new webmail is a LAMP server, headless, having following packages running on it.


Ubuntu LAMP 6.06 amd64
Apache2
MySQL-5
Postfix
Cyrus-imap
php5
SugerCRM, community edition

SquirrelMail (which was installed on repo.  I'm prepared removing it latter)


I tried installing roundcube-webmail on another Ubuntu LAMP server, 7.04 amd64) a year ago without success.  Finally I installed SM which is running until now.  SM was downloand on its official site.  Roundcube-webmail was installed on repo.


I found following webmail packages on repo...


Further advice/comment would be appreciated.  TIA


B.R.
satimis

The question is: Do you want an integrated solution, or just a webinterface that connects to an existing (IMAP) server?

For fully integrated solutions I can recommend Citadel. It has an easy-install and upgrade system that can be started via the following command (as root):
curl [http://easyinstall.citadel.org/install](http://easyinstall.citadel.org/install) | sh
All administration tasks and email, calendering etc. can be done via the "Webcit" webinterface. The only problematic thing I came across is managing loads of IMAP-folders, but you can still connect another webinterface (e.g. Roundcube) to Citadel.

Regarding Roundcube: Yes, the installation can be tricky. Depending on what you would like your LAMP server to be used for, you could consider installing the Joomla! CMS ([www.joomla.org](www.joomla.org)) and install the Roundcube for Joomla extension.

enjoy !

---

### Post by satimis on 2008-07-10
Hi scotty64,


Thanks for your advice.


> The question is: Do you want an integrated solution, or just a webinterface that connects to an existing (IMAP) server?

Sorry I'm very clear what did you meant "integrated solution"?


I have been running SquirrelMail for >1 year but not many features found.


> 
Regarding Roundcube: Yes, the installation can be tricky. Depending on what you would like your LAMP server to be used for, you could consider installing the Joomla! CMS ([www.joomla.org](www.joomla.org)) and install the Roundcube for Joomla extension.

Interesting.


I heard Joomla before but never having a chance testing it nor having a full understanding of main application.  I just visited their site mainly targeting on roundcube extension and found follows;

Absolute Beginners Guide to Joomla!
[http://docs.joomla.org/Beginners](http://docs.joomla.org/Beginners)


RoundCube for Joomla
[http://www.joomlaplug.com/Tools/Roundcube/RoubdCube_for_Joomla.html](http://www.joomlaplug.com/Tools/Roundcube/RoubdCube_for_Joomla.html)
[http://extensions.joomla.org/component/option,com_mtree/task,search/Itemid,35/searchword,roundcube/cat_id,0/](http://extensions.joomla.org/component/option,com_mtree/task,search/Itemid,35/searchword,roundcube/cat_id,0/)


Other advice noted with thanks.


B.R.
satimis

---

### Post by scotty64 on 2008-07-11
> **satimis said:**
> ...

Sorry I'm very clear what did you meant "integrated solution"?


With "integrated solution" I mean a package that contains all necessary components for a full featured mail or even groupware system (SMTP MTA, POP3, IMAP, Webinterface, Calendering etc.). Citadel as an example provides all these components without the need to configure each service individually (and the need to study all the different configurations for e.g. postfix, courier, squirrelmail.

About Joomla: I am recommending this solution if you want to host websites on your LAMP machine AND you have an interest in Roundcube. So Joomla could serve both as content management system for your website and hold the roundcube installation.

---

### Post by satimis on 2008-07-11
> **scotty64 said:**
> With "integrated solution" I mean a package that contains all necessary components for a full featured mail or even groupware system (SMTP MTA, POP3, IMAP, Webinterface, Calendering etc.). Citadel as an example provides all these components without the need to configure each service individually (and the need to study all the different configurations for e.g. postfix, courier, squirrelmail.
Noted with thanks.

I have postfix, cyrus-imap, pop3, squirrelmail, etc. running here.

A further question can I build a LAMP box without postfix, imap, pop, webmail allowing citadel taking care the rests?


> 
About Joomla: I am recommending this solution if you want to host websites on your LAMP machine AND you have an interest in Roundcube. So Joomla could serve both as content management system for your website and hold the roundcube installation.
I have CentOS 5 running as guest on VMware on a Ubuntu box.  I'm considering testing Joomla there.  Howver I have a pending problem.  The said Ubuntu box, feisty 7.04, is a mail server having SM running on it.  The server needs ports 25 and 80.  Previously I failed to backport them with proxy to Ubuntu 7.04 box after forwarding the said ports to CentOS.   Thanks


B.R.
satimis

---

### Post by scotty64 on 2008-07-12
> **satimis said:**
> Noted with thanks.

I have postfix, cyrus-imap, pop3, squirrelmail, etc. running here.

A further question can I build a LAMP box without postfix, imap, pop, webmail allowing citadel taking care the rests?


In general: Yes, and it is much easier to configure one Citadel than postfix,cyrus and the rest of the gang. Just make sure that these server daemons are NOT running (port conflicts) when you are going to install Citadel. 
The only exception could be a postfix configuration with special transports for viruschecking, procmail etc. Otherwise Citadel CAN connect to spamassassin and that allows the integration of a viruschecker for mails.

---

### Post by windependence on 2008-07-12
Just FYI, Zimbra has ClamAV, and Spamassassin built in, and uses postfix for mail. It is a complete solution with a nice AJAX front end.

-Tim

---

### Post by satimis on 2008-07-12
Hi scotty64 and windependence,


Thanks for your advice.


Which Ubuntu OS version shall I install?  

Desktop?  It pulls down the GUI packages which is NOT my desire to run them on server.

Server?  It will pull down postix, apache2, mysql, etc.  Remove them later after installation?


I'm not considering building my own Linux OS, LFS.  It is time consuming taking at least 2~3 days to finish a basic OS.

Any advice?  TIA


B.R.
satimis

---

### Post by scotty64 on 2008-07-14
> **satimis said:**
> Hi scotty64 and windependence,


Thanks for your advice.


Which Ubuntu OS version shall I install?  

Desktop?  It pulls down the GUI packages which is NOT my desire to run them on server.

Server?  It will pull down postix, apache2, mysql, etc.  Remove them later after installation?


I would go for the server version and uninstall any unneeded packages afterwards.

---

### Post by windependence on 2008-07-14
If you don't check off anything during the install, you will just get the bare installation which is what you want. Then follow this tutorial:

[http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu](http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu)

You will need to use 6.06 or 6.10 because that is what is supported. Don't worry, there is nothing wrong with the older versions. They work fine.

-Tim

---

### Post by windependence on 2008-07-14
Sorry double post.

-Tim

---

### Post by davidpeace on 2008-07-14
Seamonkey. It's a full internet suite (browser, chat, mail, web page maker, address book) And you can set it up to work with Gmail (send and receive):)

---

### Post by satimis on 2008-07-14
> **scotty64 said:**
> I would go for the server version and uninstall any unneeded packages afterwards.
Noted with thanks.


satimis

---

### Post by satimis on 2008-07-14
> **windependence said:**
> If you don't check off anything during the install, you will just get the bare installation which is what you want. Then follow this tutorial:

[http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu](http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu)

Hi Tim,


Noted with thanks


> 
You will need to use 6.06 or 6.10 because that is what is supported. Don't worry, there is nothing wrong with the older versions. They work fine.

Thanks.  I don't care the version so far if it works and has support on update/upgrade.


B.R.
satimis

---

### Post by satimis on 2008-07-14
> **windependence said:**
> Sorry double post.

-Tim
Don't worry.


satimis

---

### Post by satimis on 2008-07-14
> **davidpeace said:**
> Seamonkey. It's a full internet suite (browser, chat, mail, web page maker, address book) And you can set it up to work with Gmail (send and receive):)
Hi davidpeace,


Interesting information.  Thanks.


I'm not aware Seamonkey, a webmail server.  I have it running on an Ubuntu 7.10 desktop box here.  I'll take a look on it later.


Another thought, all servers here are headless.  I can install Seamonkey on headless server but it can't run on it.  Because it is a GUI browser.  Can users run it on their local PCs remotely?


I heard using Gmail and YahooMail sending mails on server before.  But never test it.  I have a SugarCRM box here.  It has an option to send email via Gmail.  I'll test it later to see how it works.


B.R.
satimis

---

### Post by satimis on 2008-07-19
> **windependence said:**
> If you don't check off anything during the install, you will just get the bare installation which is what you want. Then follow this tutorial:

[http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu](http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu)

You will need to use 6.06 or 6.10 because that is what is supported. Don't worry, there is nothing wrong with the older versions. They work fine.

Hi Tim,


I'm now installing 6.10 and encounter problem on running;

# apt-get update```

Ign http://security.ubuntu.com edgy-security Release.gpg
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy Release.gpg
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Ign http://security.ubuntu.com edgy-security Release
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates Release.gpg
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/main Packages
Ign http://us.archive.ubuntu.com edgy Release  
Ign http://us.archive.ubuntu.com edgy-updates Release
Ign http://security.ubuntu.com edgy-security/restricted Packages
Ign http://security.ubuntu.com edgy-security/main Sources
Ign http://security.ubuntu.com edgy-security/restricted Sources
Ign http://us.archive.ubuntu.com edgy/main Packages
Ign http://us.archive.ubuntu.com edgy/restricted Packages
Ign http://us.archive.ubuntu.com edgy/main Sources
Ign http://security.ubuntu.com edgy-security/universe Packages
Ign http://security.ubuntu.com edgy-security/universe Sources
Err http://security.ubuntu.com edgy-security/main Packages
  404 Not Found
Ign http://us.archive.ubuntu.com edgy/restricted Sources
Ign http://us.archive.ubuntu.com edgy/universe Packages
Ign http://us.archive.ubuntu.com edgy/universe Sources
Ign http://us.archive.ubuntu.com edgy-updates/main Packages
Ign http://us.archive.ubuntu.com edgy-updates/restricted Packages
Ign http://us.archive.ubuntu.com edgy-updates/main Sources
Ign http://us.archive.ubuntu.com edgy-updates/restricted Sources
Err http://security.ubuntu.com edgy-security/restricted Packages
  404 Not Found
Err http://security.ubuntu.com edgy-security/main Sources
  404 Not Found
Err http://us.archive.ubuntu.com edgy/main Packages
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com edgy/restricted Packages
  404 Not Found [IP: 91.189.88.45 80]
Err http://security.ubuntu.com edgy-security/restricted Sources
  404 Not Found
Err http://security.ubuntu.com edgy-security/universe Packages
  404 Not Found
Err http://security.ubuntu.com edgy-security/universe Sources
  404 Not Found
Err http://us.archive.ubuntu.com edgy/main Sources
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com edgy/restricted Sources
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com edgy/universe Packages
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com edgy/universe Sources
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com edgy-updates/main Packages
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com edgy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com edgy-updates/main Sources
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com edgy-updates/restricted Sources
  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-amd64/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-amd64/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-amd64/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-amd64/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-amd64/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-amd64/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-amd64/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.45 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

I suppose this version is not supported anymore.


Besides I can't find curl, fetchmail, etc. on repo.  I'll start another thread later.


B.R.
satimis

---

### Post by windependence on 2008-07-20
We probably need to find some different repository mirrors. Looks like this one is missing a lot of stuff.

-Tim

---

