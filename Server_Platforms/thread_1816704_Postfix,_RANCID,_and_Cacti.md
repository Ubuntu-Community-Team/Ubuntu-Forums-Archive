---
title: "Postfix, RANCID, and Cacti"
date: 2011-08-02
forum: Server Platforms
---

### Post by michaelkahl on 2011-08-02
I have Cacti and RANCID installed and running.  They connect to my network infrastructure and report accordingly....on the local system.  I'd like to setup email alerts so I installed postfix.

I'm not familiar with setting up MTA's at all and have never done so.  I simply want a system that will email me notifications when an event triggers the system to do so.  RANCID will do this out of the box but I have to configure an MTA like postfix.

Any help would be appreciated.

1.  I configured postfix as an Internet Site but this system is not on the public Internet nor does it have a FQDN
2.  I've used this [guide]("http://evilrouters.net/2010/05/31/installing-rancid-on-ubuntu-10-04-lts/") to setup RANCID and here's what it says about configuring the MTA.

> Next, we need to let RANCID know who should receive e-mail notifications for each group of devices.  This is done by creating e-mail aliases in your MTA&#8217;s configuration files.  Most MTAs will use the &#8220;/etc/aliases&#8221; file for this, making our job simple.

For each group that you created, we need to add two aliases to the aliases file named &#8220;rancid-<groupname>&#8221; and &#8220;rancid-admin-<groupname>&#8221;.  Open up the &#8220;/etc/aliases&#8221; file in your text editor and add lines similar to the following:

rancid-atlanta:               jlgaddis
rancid-admin-atlanta:         jlgaddis
rancid-chicago:               jlgaddis
rancid-admin-chicago:         jlgaddis
rancid-newyork:               jlgaddis
rancid-admin-newyork:         jlgaddis

After saving your changes and exiting, you&#8217;ll need to let your MTA know about the changes.  Depending on the MTA, this may be accomplished by running (as root) &#8220;/usr/bin/newaliases&#8221; (if you&#8217;re using sendmail) or &#8220;/usr/sbin/postalias /etc/aliases&#8221; (if you&#8217;re cool and use Postfix).




EDIT:  I'm running Ubuntu Server 11.04

---

### Post by michaelkahl on 2011-08-03
Well the answer is that I needed to setup a smarthost.  Fortunately our organization has a mail server that I was able to configure as the smarthost.  Emails went out and all is good.

---

