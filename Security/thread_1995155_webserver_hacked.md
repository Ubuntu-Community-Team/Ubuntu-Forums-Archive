---
title: "webserver hacked"
date: 2012-06-03
forum: Security
---

### Post by LinuxBeginer on 2012-06-03
Hi ,
i have a hosted Ubuntu server which contain some of our sites. One of them have been hacked... inside the site directory are created automatically a bunch of directories with links to some other sites. If i delete them, they are created back.. how/what i can do?
Directory's are created with an user/group id that is not listed in /etc/pasw.

Ubuntu 9.04
Apache/2.2.11 (Ubuntu) DAV/2 PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch  mod_ssl/2.2.11 OpenSSL/0.9.8g Server at xxx  Port 80

Any help appreciated!

---

### Post by unspawn on 2012-06-03
> **LinuxBeginer said:**
> inside the site directory are created automatically a bunch of directories with links to some other sites. If i delete them, they are created back.. Directory's are created with an user/group id that is not listed in /etc/pasw.
- Start by reading the [CERT Intruder Detection Checklist](http://web.archive.org/web/20080109214340/http://www.cert.org/tech_tips/intruder_detection_checklist.html). While stale it still contains useful steps to perform not listed below,
- list user nfo, the process table, open files, network connections and the cron spool (it's good to have this nfo regardless): ```
( lastlog 2>&1; last 2>&1; who -a; ps acxfwwwe 2>&1; lsof -Pwln 2>&1; netstat -Tanpe 2>&1; ls -al /var/spool/cron 2>&1; ) > /path/to/file
```
- list files in /tmp, /var/tmp and the $DOCROOT (might hold clues): ```
find /tmp /var/tmp /var/www -printf "[%T@|%A@|%C@|%u|%g|%m|%l|%s|%y|\"%p\"]\n" 2>&1> /path/to/docroot.log
```
- stop the cron service and web server to stop propagating anything,
- copy your logs including rotated ones to a known safe different machine and parse them using Logwatch for clues (maybe check [this](http://www.linuxquestions.org/questions/blog/unspawn-2450/running-logwatch-in-a-more-portable-way-34714/) for more nfo) ,
- tell us 0) what services are running (web-based management panel, FTP, SSH, web server etc, etc), 1) what software (web log, forum, shopping cart, statistics, etc, etc) including any addons and plugins is running in your web stack and their versions (basically a check for stale and vulnerable software versions), 2) if you or anyone manages the host from a windows machine and 3) if this is a shared host, VPS or a dedicated machine.
* Add any nfo you think would be useful and please be as verbose as possible.

---

### Post by HermanAB on 2012-06-06
Howdy,

Pull the network plug. Stop the http and mail daemons. Have a look at the logs to try and see what happened.  Make a backup of the data and web sites, then re-install the machine.

---

### Post by lisati on 2012-06-06
> **HermanAB said:**
> Howdy,

Pull the network plug. Stop the http and mail daemons. Have a look at the logs to try and see what happened.  Make a backup of the data and web sites, then re-install the machine.

+1: this might sound harsh, but sometimes it's easier to do it this way.

You might also want to take a look at some of the "stickies" in the [security discussions]("http://ubuntuforums.org/forumdisplay.php?f=338") section of the forum.

---

