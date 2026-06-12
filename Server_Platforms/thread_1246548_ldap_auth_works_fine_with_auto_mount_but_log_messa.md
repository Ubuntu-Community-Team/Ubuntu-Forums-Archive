---
title: "ldap auth works fine with auto mount but log messages!"
date: 2009-08-21
forum: Server Platforms
---

### Post by upengan78 on 2009-08-21
Hi,
 
I have a jeos (x86_64) 8.04 which is an ldap client.
 
The authentication for local as well as ldap users works fine and the home directory also gets mounted from nfs server.
 
Now when everything is working fine, the messages in the log file are bothering me,
 
Below log is when a local user logs in via ssh then does sudo su -
Then a ldap user logs into the system. As said auth worked fine all the time.
 
auth.log
>  
Aug 21 19:06:52 servername sshd[25917]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Aug 21 19:06:52 servername sshd[25917]: pam_ldap: reconnecting to LDAP server...
Aug 21 19:06:52 servername sshd[25917]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Aug 21 19:07:01 servername sudo: user_local : TTY=pts/6 ; PWD=/export/home/user_local ; USER=root ; COMMAND=/bin/su -
Aug 21 19:07:01 servername su[25924]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Aug 21 19:07:01 servername su[25924]: pam_ldap: reconnecting to LDAP server...
Aug 21 19:07:01 servername su[25924]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Aug 21 19:07:01 servername su[25924]: Successful su for root by root
Aug 21 19:07:01 servername su[25924]: + pts/6 root:root
Aug 21 19:07:25 servername sshd[25915]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=a.b.c.d.sbcglobal.net user=user_ldap

 
below log is taken from syslog file, Notice the CRON is unncessarily trying to connect to ldap server. some messages also come when the localuser did 'sudo su -'
 
>  
Aug 21 19:01:01 servername CRON[25838]: pam_ldap: reconnecting to LDAP server...
Aug 21 19:01:01 servername CRON[25838]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Aug 21 19:01:01 servername /USR/SBIN/CRON[25839]: (root) CMD (/export/home/local_user/report_disk)
Aug 21 19:07:01 servername sudo: pam_ldap: ldap_simple_bind Can't contact LDAP server
Aug 21 19:07:01 servername sudo: pam_ldap: reconnecting to LDAP server...
Aug 21 19:07:01 servername sudo: pam_ldap: ldap_simple_bind Can't contact LDAP server
Aug 21 19:17:01 servername CRON[26003]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Aug 21 19:17:01 servername CRON[26003]: pam_ldap: reconnecting to LDAP server...
Aug 21 19:17:01 servername CRON[26003]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Aug 21 19:17:01 servername /USR/SBIN/CRON[26004]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)

 
 
I want to avoid these messages from appearing the log files and filling up the disk. I don't think it is something with log level but probably some pam config issue,
 
PAM config on ldap client,
 
>  
 
@common-auth
 
auth sufficient pam_unix.so likeauth nullok
auth sufficient pam_ldap.so use_first_pass
 
@common-session
 
 
session sufficient pam_ldap.so
session required pam_unix.so
 
 
@PAM SSH
 
# PAM configuration for the Secure Shell service
# Read environment variables from /etc/environment and
# /etc/security/pam_env.conf.
auth required pam_env.so # [1]
# In Debian 4.0 (etch), locale-related environment variables were moved to
# /etc/default/locale, so read that as well.
auth required pam_env.so envfile=/etc/default/locale
# Standard Un*x authentication.
@include common-auth
# Disallow non-root logins when /etc/nologin exists.
account required pam_nologin.so
# Uncomment and edit /etc/security/access.conf if you need to set complex
# access limits that are hard to express in sshd_config.
# account required pam_access.so
# Standard Un*x authorization.
@include common-account
# Standard Un*x session setup and teardown.
@include common-session
# Print the message of the day upon successful login.
session optional pam_motd.so # [1]
# Print the status of the user's mailbox upon successful login.
session optional pam_mail.so standard noenv # [1]
# Set up user limits from /etc/security/limits.conf.
session required pam_limits.so
# Set up SELinux capabilities (need modified pam)
# session required pam_selinux.so multiple
# Standard Un*x password updating.
@include common-password
 
PAM CRON
@include common-auth
auth required pam_env.so
@include common-account
@include common-session
# Sets up user limits, please define limits for cron tasks
# through /etc/security/limits.conf
session required pam_limits.so
 

 
nssswitch.conf has passwd, groups, shadow options setup for "files ldap"
 
 
Any idea to avoid these messages or what could be issue?
 
This is libnss-ldap.
 
Thanks

---

