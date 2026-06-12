---
title: "logrotate and rsyslog  issue"
date: 2010-03-23
forum: Server Platforms
---

### Post by malikp on 2010-03-23
Recently I installed new server and having some issues with logrotate
 When the logrotate start it will rotate the log files as it should be but never recreate the original file.  Further investigation shows issue is due to command  after logrotate, whis is “reload rsyslog >/dev/null 2>&1 || true”
 

 So far logrotate worked fine for any log file as long as you don't have to issue above reload command.
 Only way I could restart the rsyslog using service rsyslog restart
 

 All the missing log files recreate as soon as rsyslog restarted.  
 I'm using Ubuntu 9.10 with follwing kernel and software vertions
 2.6.31-20-generic-pae #58-Ubuntu SMP Fri Mar 12 06:25:51 UTC 2010 i686 GNU/Linux
 logrotate  3.7.8-4ubuntu1
 rsyslog     4.2.0-2ubuntu5.1
 

 I can confirm file recreation configured. I have another two servers with same software versions and I could not see this issue. Differences are the server with this issue have virtualbox installed and few guests are running (I do not this this is an issue).
 Other diffrence is is var mounted using following options rw,noatime,data=writeback,errors=remount-ro
 File system is ext4
 I do not know they make any diffrence.
 

 Thank you,

---

### Post by malikp on 2010-03-23
I reinstall rsyslog and logrotate didn't make a diffrence.
 

 Reboot the server still the same issue. All the missing logfiles recreated (because rsyslog restsred).
 After logrotate issued sync but didn't create files. Still I had to service rsyslog restart

---

### Post by malikp on 2010-03-24
I think found the issue. Missing create in the below create new logfiles. So far working. i have to keep eye on for few days.

# create new (empty) log files after rotating old ones

# uncomment this if you want your log files compressed

Now it look like this
# create new (empty) log files after rotating old ones
create
# uncomment this if you want your log files compressed

---

