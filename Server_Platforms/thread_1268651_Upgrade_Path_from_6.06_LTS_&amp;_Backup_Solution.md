---
title: "Upgrade Path from 6.06 LTS &amp; Backup Solution"
date: 2009-09-17
forum: Server Platforms
---

### Post by Mhaddy on 2009-09-17
I'm currently running Ubuntu 6.06 LTS and a LAMP server that hosts half a dozen websites and serves email.  I'd like to get 8.04 LTS up and running and I'm wondering if it is best to follow the [upgrade path](https://help.ubuntu.com/community/HardyUpgrades#Upgrade%20from%206.06%20LTS%20to%208.04%20LTS) or perform a fresh install.  When I upgrade my personal operating systems (Mac, Windows), I always start from scratch as I've found it offers more stability, speed, and it's cleaner.  Does the same apply for Ubuntu?

And before I do the upgrade, however I choose to do it, I'd like to know how best to perform backups.  In the past, as all websites are my own development/project sites, I've just kept local copies of the web files and dumped the databases, not worrying about configuration/system files.  However, now I'm looking into NAS solutions to provide a little more peace of mind and aside from copying directories/files one-by-one, is there a simple "backup LAMP-related files" solution?

---

### Post by koenn on 2009-09-17
upgrade should be fine, no need to start from scratch.

A backup is a good idea, however.
What you want is the files with web content, the databases, and your configuration files.

so you need to copy /etc and /var/www or wherever your web sites are located, and an sql dump of the databases. 

That should be sufficient. There are other 'LAMP related' files in other directories, but they shouldn't contain any configuration or customization (unless you've done your own tweaking , but in that case, you'd know).  


Some 3th party software installs to /opt and/or keeps config files in unusual places (/opt, /var/..., /usr/local/ ...), but again, you'd know if you installed those.

---

