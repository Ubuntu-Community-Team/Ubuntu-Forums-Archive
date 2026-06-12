---
title: "Cpanel Source Files"
date: 2009-12-12
forum: Server Platforms
---

### Post by bar338 on 2009-12-12
This is my first attempt at running a dedicated linux server for web hosting.  I'm attempting to make the webalizer stats in cpanel publicly available.  I've found tutorials on how to do this.  However, I'm unable to find the config files for this.  

My question is: When cpanel installs an addon such as webalizer where do the files get saved? I've gone through my ssh and done a check to see if the webalizer package is installed and it says it is not, yet I'm able to access webalizer through the cpanel.  So I guess I just need a better understanding of how cpanel relates to the actualy filesystem of a webserver.

I know that this is an ubuntu forum but I've found a lot of good help in the past, but the server is actually running centos. I've also got access to login as root for the dedicated server.

[EDIT: I found the cpanel source files in /var/cpanel/ but I still can't seem to figure out how webalizer is installed]

Here is a little from my log file:
> Webalizer V2.01-10 (Linux 2.6.18-128.4.1.el5) English
Using logfile /usr/local/apache/domlogs/mywebsite.com (clf)
DNS Lookup (10): [new_unode] Warning: String exceeds storage size (252)
5 addresses in 7.50 seconds
Using DNS cache file /home/www/tmp/webalizer/dns_cache.db
Creating output in /home/www/tmp/webalizer
Hostname for reports is 'mywebsite.com'
Reading history file... webalizer.hist
Reading previous run data.. webalizer.current
Saving current run data... [09/24/2009 17:19:18]
Generating report for September 2009
Generating summary report
Saving history information...


Now I just need to find out where the webalizer.conf file is.  I cannot find it for the life of me and i'm not sure if it even exists.  Now that i know where the output is i need to change the ouput to be displayed publicly.  So i need to change /home/www/tmp/webalizer to /home/www/public_html/stats

Thanks for your help.

---

