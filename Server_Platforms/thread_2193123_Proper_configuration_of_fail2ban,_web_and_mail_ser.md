---
title: "Proper configuration of fail2ban, web and mail server"
date: 2013-12-11
forum: Server Platforms
---

### Post by bigmonmulgrew on 2013-12-11
Hi guys
I have installed fail2ban on my web server.

I just want to confirm the proper configuration of the jail file since this is something that can potentially block access. The server is ubuntu server 12.04, LAMP. It is running a small number of Drupal websites from it. Over Xmas I'm also thinking of adding a mail server.

From looking through the configuration it appears the default install has quite a selection of jails but they are set to disabled by default. I'm thinking I should set all of the following to enabled

ssh-ddos
apache
apache-multiport
apache-noscript
apache-overflow
vsftpd

I was thinking of trying out Citadel for the mail server, any idea if the existing mail server jails would apply to that or would I have to write one?

I'm also thinking that for http the ban time should be longer than the default 600 seconds. Anyone got any thoughts on that. I'm thinking the http bans would typically be overly agressive bots. I was thinking something longer would be better like 1 hour. 

So the manual says to  add a file jail.local to override setting so if I'm interpreting that correctly my jail file should contain this the code below if anyone could check it for me that would be great.

Is there anything else I need to be adding to effectively be blocking bots.

my jail.local
```
[ssh-ddos]

enabled  = true

[apache]

enabled  = true

[apache-multiport]

enabled  = true

[apache-noscript]

enabled  = true

[apache-overflows]

enabled  = true

[vsftp]

enabled  = true
```

---

### Post by bigmonmulgrew on 2013-12-11
I thought I'd go ahead and try it anyway. I got a load of errors after restarting fail2ban. I decided to copy the jail.conf and delete the bits I didnt need, eventually I went with this.

```
[ssh-ddos]

enabled  = true
port     = ssh
filter   = sshd-ddos
logpath  = /var/log/auth.log
maxretry = 6

#
# HTTP servers
#

[apache]

enabled  = true
port     = http,https
filter   = apache-auth
logpath  = /var/log/apache*/*error.log
maxretry = 6

# default action is now multiport, so apache-multiport jail was left
# for compatibility with previous (<0.7.6-2) releases
[apache-multiport]

enabled   = true
port      = http,https
filter    = apache-auth
logpath   = /var/log/apache*/*error.log
maxretry  = 6

[apache-noscript]

enabled  = true
port     = http,https
filter   = apache-noscript
logpath  = /var/log/apache*/*error.log
maxretry = 6

[apache-overflows]

enabled  = true
port     = http,https
filter   = apache-overflows
logpath  = /var/log/apache*/*error.log
maxretry = 2

#
# FTP servers
#

[vsftpd]

enabled  = true
port     = ftp,ftp-data,ftps,ftps-data
filter   = vsftpd
logpath  = /var/log/vsftpd.log
# or overwrite it in jails.local to be
# logpath = /var/log/auth.log
# if you want to rely on PAM failed login attempts
# vsftpd's failregex should match both of those formats
maxretry = 6

```

---

### Post by bigmonmulgrew on 2013-12-11
OK its now running.

however I notice its checking the apache error logs, would it not be better to be checking the access logs?

---

