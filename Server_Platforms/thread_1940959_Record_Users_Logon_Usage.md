---
title: "Record Users Logon Usage"
date: 2012-03-14
forum: Server Platforms
---

### Post by -jrosco- on 2012-03-14
Hi Guys,
Scenario:
I want to get all users time usage on a linux system via the last or ac commands and using a perl script to manipulate the output of the data. What I need is to use logrotate and then run something like "/usr/bin/ac | perl /root/utils/logon_time.pl" and empty the /var/log/wtmp after backing up to .e.g /var/log/wtmp-YYYY-MM-DD.gz
I'm using logrotate on /var/log/wtmp like this "logrotate /root/conf/logrotate.conf"
 
This is what my /root/conf/logrotate.conf file looks like
 
```

#Start of file
create
compress
dateext
/var/log/wtmp {
    missingok
    daily
    create 0664 root utmp
    notifempty
 postrotate
   /usr/bin/ac | perl /root/utils/logon_time.pl #This script is the one to I use to manipulate the time usage data
 endscript
 rotate 5
}
#End of file

```
 
So this all works fine, but after running logrotate against the wtmp data file any current users logged onto the system will not have their time usage recorded to the wtmp file until they logout and login. Basically I need this process to work in realtime so any current user logged on the system at time the logrotate command is issued will have their time record on the fly in realtime without having to logout and login again. Currently the logged in users will not record their time usage to the new wtmp file.
 
There could a better way to account for user time, but I'm unaware of any other way. I have look through Google and haven't really found anything useful.
 
If anyone needs more info I will be happy to provide it.
 
System Information:
Distributor ID: Debian
Description: Debian GNU/Linux 6.0.4 (squeeze)
Release: 6.0.4
Codename: squeeze
logrotate version 3.7.8-6
Kernel : 2.6.32-5-xen-686
 
Cheers
 
Joel C

---

