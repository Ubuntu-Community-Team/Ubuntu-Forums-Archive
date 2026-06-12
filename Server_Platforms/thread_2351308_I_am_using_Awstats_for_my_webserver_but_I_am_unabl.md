---
title: "I am using Awstats for my webserver but I am unable to update it."
date: 2017-02-01
forum: Server Platforms
---

### Post by mbauermeister on 2017-02-01
Ok if go to this link [https://www.michaelbauermeister.info/cgi-bin/awstats.pl?config=michaelbauermeister.info](https://www.michaelbauermeister.info/cgi-bin/awstats.pl?config=michaelbauermeister.info) but if you click update you get the following 
```
Error: Couldn't open server log file "/var/log/apache2/access.log" : Permission denied 

Setup ('/etc/awstats/awstats.michaelbauermeister.info.conf' file, web server or permissions) may be wrong.
Check config file, permissions and AWStats documentation (in 'docs' directory).

```
I have try to find the answer directly and indirectly to solve I can't figure out why I can't update my stat on my website.

I am using the most current ubuntu server os and I am using the apache2 as my software for hosting my website and put it on my website.

---

### Post by wildmanne39 on 2017-02-01
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by TheFu on 2017-02-03
Welcome to the forums..

The update process needs to have read permissions to the apache logs and write permissions to the awstats summary output pages. This is basic Unix User/Group permissions.  There are tutorials available - google "Ubuntu permissions" to find one.  Spend about 30-60 minutes creating at least 3 temporary users, groups and some files/directories under /tmp/ somewhere.  See what works, what doesn't and how you can share files with the most restrictions across 1, 2, 3 userids.  Try some strange things.  For me, until I did this self experimentation, permissions just weren't clear.  
Apache runs under a userid (probably www-data), so file permissions need to allow www-data access to the files and the logs.  Whatever userid is used to generate the awstats, also needs read access to the log files.  Think I was just lazy and made www-data run the cron that generates the stats as html files.

Plus don't forget to update the .conf file for each website you want awstats to make tables/graphs for.  I'm lazy and just update the stats every 6 hrs using cron.  More secure than letting the web server generate them on-the-fly.

---

### Post by Habitual on 2017-02-05
There was in my memory, a perl script that had to be "run" periodically (cron'd)
to update site stats....

---

### Post by mbauermeister on 2017-02-06
I am very new at this can you just dumb it up and give the commands I need to enter my command lines to enable it.

---

### Post by TheFu on 2017-02-06
> **mbauermeister said:**
> I am very new at this can you just dumb it up and give the commands I need to enter my command lines to enable it.

I don't think I can.  It is relatively easy, if you have the necessary understanding of Unix system security.  

The best way I know is to gain that background through directed learning, not being told what to type (which is different for every system).
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a quality, free, no-hassle download, PDF book which provides the needed knowledge. Pay attention to file and directory permissions, but the other items are necessary to understand how processes interact with the file system.

Sorry, I'm just not a good teacher at that level.

---

