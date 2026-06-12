---
title: "Using Nessus from the command line"
date: 2007-12-17
forum: Server Platforms
---

### Post by echokilo on 2007-12-17
I've installed Nessus on a fresh Ubuntu Server Install using the following steps:

$ sudo apt-get install nessusd nessus nessus-plugins
$ sudo update-rc.d nessusd defaults
$ sudo ln -s /etc/init.d/nessusd /etc/rc2.d/S20nessusd
$ sudo /etc/init.d/nessusd start
$ sudo nessus-adduser
$ sudo /etc/init.d/nessusd restart
$ nessus

Now, I would welcome any insight on using it from the command line exclusively.  I would like it to run on the network, doing a full scan of vulnerabilities on a regular cycle and saving the report.

Thank you!

---

### Post by koenn on 2007-12-17
RTFM !
Google it !



but, seriously, here's how ;

man nessus
or
[http://linux.die.net/man/1/nessus](http://linux.die.net/man/1/nessus)

---

