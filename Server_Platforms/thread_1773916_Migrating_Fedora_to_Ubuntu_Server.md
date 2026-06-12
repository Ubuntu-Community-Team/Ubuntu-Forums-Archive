---
title: "Migrating Fedora to Ubuntu Server"
date: 2011-06-02
forum: Server Platforms
---

### Post by blehmonster on 2011-06-02
Hi,

I have been running a Fedora server for the past 7 years (since ~FC2).  The server hardware is now beginning to fail and I've secured new Dell hardware to replace it.  When I do replace the hardware, I'm planning on loading a new distro due to the 'bleeding edge' nature of Fedora.  I'm a relatively competent sysadmin when it comes to RedHat products, but I am interested in exploring Ubuntu.  I've used it briefly as a desktop in the past, so I'm familiar with the basics behind apt-get and sudo in comparison to yum and su.  

My current Fedora server is a basic LAMP stack with a pdns caching nameserver and a moderately complex Postfix/dspam/spamassassin mail configuration.   Otherwise, the software/services installed are minimal and I would assume standard (dovecot, rsyslog, ntpd, ssh, pureftpd, etc).  Has anyone here had any experience in migrating a Fedora server to Ubuntu?  I'm not familiar with how conservative the Ubuntu distro is, so I'm worried about things like newer versions of Dovecot (Fedora) causing compatibility issues with an older version of Dovecot on Ubuntu.  

Any help, stories or suggestions would be greatly appreciated!

---

### Post by lfacchinelli on 2011-06-03
You should check out compatibility issues with apps' versions.


In ubuntu (actually in all debian based OS) you can install a specific version of an app using
apt-get install APP=VERSION

So, if you want to replicate apps' version from Fedora to Ubuntu you can , so just need to copy your files from Fedora to Ubuntu and that's it.
But, imho always try to update yours app to the latest stable versions, obviously you should take care of possibly incompatibility of config files and so.

Regards

---

### Post by HermanAB on 2011-06-03
Linux is Linux is Linux...

However, Fedora has a large colelction of wizards to help you set up things and Ubuntu doesn't.  That is about the only difference.

---

### Post by ian dobson on 2011-06-04
Hi,

I've done afew migrations in my time and the most important thing is planning. Sit down and look at exactly whats installed on the old box, make a list of whats installed and the versions. Then see what versions are available on the new box and see where you could have problems/study the release notes to see if anything major could cause you problems.

Now sit down away from the systems and think about what services should be installed in what order (dns/basic networking first), samba,mysql,apache next then spamassassin and then email. So it's just a matter of finding the dependancies between the packages.

The last site I updated, they has a very complex apache configuration, so we transfered all the files over including the config files. Started apache with the new config files and started fixing what was broken. That took almost 1/2 day, but as I already had done my ground work it wasn't too bad.

Once the new box is up and running, test, test, TEST until your 100% happy.

The biggest problems with the installations that I've seen is that the documentation (what,where,why) is really lacking and only the sysadmin knowns whats really installed.

Regards
Ian Dobson

---

### Post by Lars Noodén on 2011-06-04
> **blehmonster said:**
> 
Any help, stories or suggestions would be greatly appreciated!

I usually recommend using Debian on the servers.  The long release cycle is a great help for easy maintenance.  It's rather similar to Ubuntu and in some cases it will be hard to notice a difference.

---

