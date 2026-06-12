---
title: "HOWTO: Installing DenyHosts"
date: 2007-05-21
forum: Tutorials
---

### Post by dbott67 on 2007-05-21
The **denyhosts** package is a great python script used to prevent brute force hacking of your SSH server.  Full details are available at [http://denyhosts.sf.net/](http://denyhosts.sf.net/).

For those that wish to enable remote SSH access, the the best practices would be:

1. [Use RSA/DSA keys]("http://www-128.ibm.com/developerworks/library/l-keyc.html")
2. [TCP Wrappers:]("http://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/ref-guide/s1-tcpwrappers-access.html") Add any known remote host to /etc/hosts.allow and deny all other access in /etc/hosts.deny

The main issue with the above is that:

a) You can only access from a pre-determined host (/etc/hosts.allow)
b) You need to have your private key installed on the remote machine (RSA/DSA)

[COLOR=Purple]This guide is for those that require access from _**any**_ remote machine, yet do not want to have their server constantly bombarded by brute force attacks.[/COLOR]

There are already a number of tutorials in these forums and various places on the 'net that address how to install and configure **DenyHosts** on various platforms, however, the difference between the Ubuntu package in the repositories and compiling yourself (or downloading a pre-complied .deb from somewhere) is that the Ubuntu package will create all of the required links and set the denyhosts script to run as a daemon automatically.

This instructions are specifically for Feisty Fawn 7.04, although they should work in earlier versions.

** 1. Install denyhosts from the repositories:**
```
[COLOR=Red]sudo apt-get install denyhosts[/COLOR]
```**2. Edit the denyhosts configuration file to suit your needs.**  

The default file in the Ubuntu package has been pre-configured for Ubuntu/Debian systems, so most of the settings should be fine:
```
[COLOR=Red]sudo nano /etc/denyhosts.conf[/COLOR]

```For testing purposes, I set the **PURGE_DENY** value to 5 minutes, so that I can test to see if everything is working.  If all is well, I purge the hosts.deny file and then I set it back to 5 days.
```

       ############ THESE SETTINGS ARE REQUIRED ############

########################################################################
#
# SECURE_LOG: the log file that contains sshd logging info
# if you are not sure, grep "sshd:" /var/log/*
#
# The file to process can be overridden with the --file command line
# argument
#
# Redhat or Fedora Core:
#SECURE_LOG = /var/log/secure
#
# Mandrake, FreeBSD or OpenBSD: 
#SECURE_LOG = /var/log/auth.log
#
# SuSE:
#SECURE_LOG = /var/log/messages
#
# Mac OS X (v10.4 or greater - 
#   also refer to:   http://www.denyhosts.net/faq.html#macos
#SECURE_LOG = /private/var/log/asl.log
#
# Mac OS X (v10.3 or earlier):
#SECURE_LOG=/private/var/log/system.log
#
# Debian:
SECURE_LOG = /var/log/auth.log
########################################################################

########################################################################
#
# HOSTS_DENY: the file which contains restricted host access information
#
# Most operating systems:
HOSTS_DENY = /etc/hosts.deny
#
# Some BSD (FreeBSD) Unixes:
#HOSTS_DENY = /etc/hosts.allow
#
# Another possibility (also see the next option):
#HOSTS_DENY = /etc/hosts.evil
#######################################################################


########################################################################
#
# PURGE_DENY: removed HOSTS_DENY entries that are older than this time
#             when DenyHosts is invoked with the --purge flag
#
#      format is: i[dhwmy]
#      Where 'i' is an integer (eg. 7) 
#            'm' = minutes
#            'h' = hours
#            'd' = days
#            'w' = weeks
#            'y' = years
#
# never purge:
PURGE_DENY = 
#
# purge entries older than 1 week
#PURGE_DENY = 1w
#
# purge entries older than 5 days
PURGE_DENY = 5d
#######################################################################

#######################################################################
#
# PURGE_THRESHOLD: defines the maximum times a host will be purged.  
# Once this value has been exceeded then this host will not be purged. 
# Setting this parameter to 0 (the default) disables this feature.
#
# default: a denied host can be purged/re-added indefinitely
PURGE_THRESHOLD = 0
#
# a denied host will be purged at most 2 times. 
#PURGE_THRESHOLD = 2 
#
#######################################################################


#######################################################################
#
# BLOCK_SERVICE: the service name that should be blocked in HOSTS_DENY
# 
# man 5 hosts_access for details
#
# eg.   sshd: 127.0.0.1  # will block sshd logins from 127.0.0.1
#
# To block all services for the offending host:
#BLOCK_SERVICE = ALL
# To block only sshd:
BLOCK_SERVICE  = sshd
# To only record the offending host and nothing else (if using
# an auxilary file to list the hosts).  Refer to: 
# http://denyhosts.sourceforge.net/faq.html#aux
#BLOCK_SERVICE =    
#
#######################################################################


#######################################################################
#
# DENY_THRESHOLD_INVALID: block each host after the number of failed login 
# attempts has exceeded this value.  This value applies to invalid
# user login attempts (eg. non-existent user accounts)
#
DENY_THRESHOLD_INVALID = 5
#
#######################################################################

#######################################################################
#
# DENY_THRESHOLD_VALID: block each host after the number of failed 
# login attempts has exceeded this value.  This value applies to valid
# user login attempts (eg. user accounts that exist in /etc/passwd) except
# for the "root" user
#
DENY_THRESHOLD_VALID = 5
#
#######################################################################

#######################################################################
#
# DENY_THRESHOLD_ROOT: block each host after the number of failed 
# login attempts has exceeded this value.  This value applies to 
# "root" user login attempts only.
#
DENY_THRESHOLD_ROOT = 1
#
#######################################################################


#######################################################################
#
# DENY_THRESHOLD_RESTRICTED: block each host after the number of failed 
# login attempts has exceeded this value.  This value applies to 
# usernames that appear in the WORK_DIR/restricted-usernames file only.
#
DENY_THRESHOLD_RESTRICTED = 1
#
#######################################################################


#######################################################################
#
# WORK_DIR: the path that DenyHosts will use for writing data to
# (it will be created if it does not already exist).  
#
# Note: it is recommended that you use an absolute pathname
# for this value (eg. /home/foo/denyhosts/data)
#
WORK_DIR = /var/lib/denyhosts
#
#######################################################################

#######################################################################
#
# SUSPICIOUS_LOGIN_REPORT_ALLOWED_HOSTS
#
# SUSPICIOUS_LOGIN_REPORT_ALLOWED_HOSTS=YES|NO
# If set to YES, if a suspicious login attempt results from an allowed-host
# then it is considered suspicious.  If this is NO, then suspicious logins 
# from allowed-hosts will not be reported.  All suspicious logins from 
# ip addresses that are not in allowed-hosts will always be reported.
#
SUSPICIOUS_LOGIN_REPORT_ALLOWED_HOSTS=YES
######################################################################

######################################################################
#
# HOSTNAME_LOOKUP
#
# HOSTNAME_LOOKUP=YES|NO
# If set to YES, for each IP address that is reported by Denyhosts,
# the corresponding hostname will be looked up and reported as well
# (if available).
#
HOSTNAME_LOOKUP=YES
#
######################################################################


######################################################################
#
# LOCK_FILE
#
# LOCK_FILE=/path/denyhosts
# If this file exists when DenyHosts is run, then DenyHosts will exit
# immediately.  Otherwise, this file will be created upon invocation
# and deleted upon exit.  This ensures that only one instance is
# running at a time.
#
# Redhat/Fedora:
#LOCK_FILE = /var/lock/subsys/denyhosts
#
# Debian
LOCK_FILE = /var/run/denyhosts.pid
#
# Misc
#LOCK_FILE = /tmp/denyhosts.lock
#
######################################################################


       ############ THESE SETTINGS ARE OPTIONAL ############


#######################################################################
#
# ADMIN_EMAIL: if you would like to receive emails regarding newly
# restricted hosts and suspicious logins, set this address to 
# match your email address.  If you do not want to receive these reports
# leave this field blank (or run with the --noemail option)
#
# Multiple email addresses can be delimited by a comma, eg:
# ADMIN_EMAIL = foo@bar.com, bar@foo.com, etc@foobar.com
#
[COLOR=Purple] ADMIN_EMAIL = you@yourdomain.com[/COLOR]
#
#######################################################################

#######################################################################
#
# SMTP_HOST and SMTP_PORT: if DenyHosts is configured to email 
# reports (see ADMIN_EMAIL) then these settings specify the 
# email server address (SMTP_HOST) and the server port (SMTP_PORT)
# 
#
[COLOR=Purple] SMTP_HOST = mail.yourdomain.com
SMTP_PORT = 25[/COLOR]
#
#######################################################################

#######################################################################
# 
# SMTP_USERNAME and SMTP_PASSWORD: set these parameters if your 
# smtp email server requires authentication
#
[COLOR=Purple]SMTP_USERNAME=you@yourdomain.com
SMTP_PASSWORD=your_password[/COLOR]
#
######################################################################

#######################################################################
#
# SMTP_FROM: you can specify the "From:" address in messages sent
# from DenyHosts when it reports thwarted abuse attempts
#
SMTP_FROM = DenyHosts <nobody@localhost>
#
#######################################################################

#######################################################################
#
# SMTP_SUBJECT: you can specify the "Subject:" of messages sent
# by DenyHosts when it reports thwarted abuse attempts
[COLOR=Purple] SMTP_SUBJECT = Possible SSH Attack[/COLOR]
#
######################################################################

######################################################################
#
# SMTP_DATE_FORMAT: specifies the format used for the "Date:" header
# when sending email messages.
#
# for possible values for this parameter refer to: man strftime
#
# the default:
#
#SMTP_DATE_FORMAT = %a, %d %b %Y %H:%M:%S %z
#
######################################################################

######################################################################
#
# SYSLOG_REPORT
#
# SYSLOG_REPORT=YES|NO
# If set to yes, when denied hosts are recorded the report data
# will be sent to syslog (syslog must be present on your system).
# The default is: NO
#
#SYSLOG_REPORT=NO
#
#SYSLOG_REPORT=YES
#
######################################################################

######################################################################
#
# ALLOWED_HOSTS_HOSTNAME_LOOKUP
#
# ALLOWED_HOSTS_HOSTNAME_LOOKUP=YES|NO
# If set to YES, for each entry in the WORK_DIR/allowed-hosts file,
# the hostname will be looked up.  If your versions of tcp_wrappers
# and sshd sometimes log hostnames in addition to ip addresses
# then you may wish to specify this option.
# 
#ALLOWED_HOSTS_HOSTNAME_LOOKUP=NO
#
######################################################################

###################################################################### 
# 
# AGE_RESET_VALID: Specifies the period of time between failed login
# attempts that, when exceeded will result in the failed count for 
# this host to be reset to 0.  This value applies to login attempts 
# to all valid users (those within /etc/passwd) with the 
# exception of root.  If not defined, this count will never
# be reset.
#
# See the comments in the PURGE_DENY section (above) 
# for details on specifying this value or for complete details 
# refer to:  http://denyhosts.sourceforge.net/faq.html#timespec
#
AGE_RESET_VALID=5m
#
######################################################################

###################################################################### 
# 
# AGE_RESET_ROOT: Specifies the period of time between failed login
# attempts that, when exceeded will result in the failed count for 
# this host to be reset to 0.  This value applies to all login 
# attempts to the "root" user account.  If not defined,
# this count will never be reset.
#
# See the comments in the PURGE_DENY section (above) 
# for details on specifying this value or for complete details 
# refer to:  http://denyhosts.sourceforge.net/faq.html#timespec
#
AGE_RESET_ROOT=25d
#
######################################################################

###################################################################### 
# 
# AGE_RESET_RESTRICTED: Specifies the period of time between failed login
# attempts that, when exceeded will result in the failed count for 
# this host to be reset to 0.  This value applies to all login 
# attempts to entries found in the WORK_DIR/restricted-usernames file.  
# If not defined, the count will never be reset.
#
# See the comments in the PURGE_DENY section (above) 
# for details on specifying this value or for complete details 
# refer to:  http://denyhosts.sourceforge.net/faq.html#timespec
#
AGE_RESET_RESTRICTED=25d
#
######################################################################


###################################################################### 
# 
# AGE_RESET_INVALID: Specifies the period of time between failed login
# attempts that, when exceeded will result in the failed count for 
# this host to be reset to 0.  This value applies to login attempts 
# made to any invalid username (those that do not appear 
# in /etc/passwd).  If not defined, count will never be reset.
#
# See the comments in the PURGE_DENY section (above) 
# for details on specifying this value or for complete details 
# refer to:  http://denyhosts.sourceforge.net/faq.html#timespec
#
AGE_RESET_INVALID=10d
#
######################################################################


######################################################################
#
# RESET_ON_SUCCESS: If this parameter is set to "yes" then the
# failed count for the respective ip address will be reset to 0
# if the login is successful.  
#
# The default is RESET_ON_SUCCESS = no
#
#RESET_ON_SUCCESS = yes
#
#####################################################################


######################################################################
#
# PLUGIN_DENY: If set, this value should point to an executable
# program that will be invoked when a host is added to the
# HOSTS_DENY file.  This executable will be passed the host
# that will be added as its only argument.
#
#PLUGIN_DENY=/usr/bin/true
#
######################################################################


######################################################################
#
# PLUGIN_PURGE: If set, this value should point to an executable
# program that will be invoked when a host is removed from the
# HOSTS_DENY file.  This executable will be passed the host
# that is to be purged as its only argument.
#
#PLUGIN_PURGE=/usr/bin/true
#
######################################################################

######################################################################
#
# USERDEF_FAILED_ENTRY_REGEX: if set, this value should contain
# a regular expression that can be used to identify additional
# hackers for your particular ssh configuration.  This functionality
# extends the built-in regular expressions that DenyHosts uses.
# This parameter can be specified multiple times.
# See this faq entry for more details:
#    http://denyhosts.sf.net/faq.html#userdef_regex
#
#USERDEF_FAILED_ENTRY_REGEX=
#
#
######################################################################




   ######### THESE SETTINGS ARE SPECIFIC TO DAEMON MODE  ##########



#######################################################################
#
# DAEMON_LOG: when DenyHosts is run in daemon mode (--daemon flag)
# this is the logfile that DenyHosts uses to report its status.
# To disable logging, leave blank.  (default is: /var/log/denyhosts)
#
DAEMON_LOG = /var/log/denyhosts
#
# disable logging:
#DAEMON_LOG = 
#
######################################################################

#######################################################################
# 
# DAEMON_LOG_TIME_FORMAT: when DenyHosts is run in daemon mode 
# (--daemon flag) this specifies the timestamp format of 
# the DAEMON_LOG messages (default is the ISO8061 format:
# ie. 2005-07-22 10:38:01,745)
#
# for possible values for this parameter refer to: man strftime
#
# Jan 1 13:05:59   
#DAEMON_LOG_TIME_FORMAT = %b %d %H:%M:%S
#
# Jan 1 01:05:59 
#DAEMON_LOG_TIME_FORMAT = %b %d %I:%M:%S
#
###################################################################### 

#######################################################################
# 
# DAEMON_LOG_MESSAGE_FORMAT: when DenyHosts is run in daemon mode 
# (--daemon flag) this specifies the message format of each logged
# entry.  By default the following format is used:
#
# %(asctime)s - %(name)-12s: %(levelname)-8s %(message)s
#
# Where the "%(asctime)s" portion is expanded to the format
# defined by DAEMON_LOG_TIME_FORMAT
#
# This string is passed to python's logging.Formatter contstuctor.
# For details on the possible format types please refer to:
# http://docs.python.org/lib/node357.html
#
# This is the default:
#DAEMON_LOG_MESSAGE_FORMAT = %(asctime)s - %(name)-12s: %(levelname)-8s %(message)s
#
#
###################################################################### 

 
#######################################################################
#
# DAEMON_SLEEP: when DenyHosts is run in daemon mode (--daemon flag)
# this is the amount of time DenyHosts will sleep between polling
# the SECURE_LOG.  See the comments in the PURGE_DENY section (above)
# for details on specifying this value or for complete details
# refer to:    http://denyhosts.sourceforge.net/faq.html#timespec
# 
#
DAEMON_SLEEP = 30s
#
#######################################################################

#######################################################################
#
# DAEMON_PURGE: How often should DenyHosts, when run in daemon mode,
# run the purge mechanism to expire old entries in HOSTS_DENY
# This has no effect if PURGE_DENY is blank.
#
DAEMON_PURGE = 1h
#
#######################################################################


   #########   THESE SETTINGS ARE SPECIFIC TO     ##########
   #########       DAEMON SYNCHRONIZATION         ##########


#######################################################################
#
# Synchronization mode allows the DenyHosts daemon the ability
# to periodically send and receive denied host data such that 
# DenyHosts daemons worldwide can automatically inform one
# another regarding banned hosts.   This mode is disabled by
# default, you must uncomment SYNC_SERVER to enable this mode.
#
# for more information, please refer to: 
#        http:/denyhosts.sourceforge.net/faq.html#sync 
#
#######################################################################


#######################################################################
#
# SYNC_SERVER: The central server that communicates with DenyHost
# daemons.  Currently, denyhosts.net is the only available server
# however, in the future, it may be possible for organizations to
# install their own server for internal network synchronization
#
# To disable synchronization (the default), do nothing. 
#
# To enable synchronization, you must uncomment the following line:
#SYNC_SERVER = http://xmlrpc.denyhosts.net:9911
#
#######################################################################

#######################################################################
#
# SYNC_INTERVAL: the interval of time to perform synchronizations if
# SYNC_SERVER has been uncommented.  The default is 1 hour.
# 
#SYNC_INTERVAL = 1h
#
#######################################################################


#######################################################################
#
# SYNC_UPLOAD: allow your DenyHosts daemon to transmit hosts that have
# been denied?  This option only applies if SYNC_SERVER has
# been uncommented.
# The default is SYNC_UPLOAD = yes
#
#SYNC_UPLOAD = no
#SYNC_UPLOAD = yes
#
#######################################################################


#######################################################################
#
# SYNC_DOWNLOAD: allow your DenyHosts daemon to receive hosts that have
# been denied by others?  This option only applies if SYNC_SERVER has
# been uncommented.
# The default is SYNC_DOWNLOAD = yes
#
#SYNC_DOWNLOAD = no
#SYNC_DOWNLOAD = yes
#
#
#
#######################################################################

#######################################################################
#
# SYNC_DOWNLOAD_THRESHOLD: If SYNC_DOWNLOAD is enabled this parameter
# filters the returned hosts to those that have been blocked this many
# times by others.  That is, if set to 1, then if a single DenyHosts
# server has denied an ip address then you will receive the denied host.
# 
# See also SYNC_DOWNLOAD_RESILIENCY
#
#SYNC_DOWNLOAD_THRESHOLD = 10
#
# The default is SYNC_DOWNLOAD_THRESHOLD = 3 
#
#SYNC_DOWNLOAD_THRESHOLD = 3
#
#######################################################################

#######################################################################
#
# SYNC_DOWNLOAD_RESILIENCY:  If SYNC_DOWNLOAD is enabled then the
# value specified for this option limits the downloaded data
# to this resiliency period or greater.
#
# Resiliency is defined as the timespan between a hackers first known 
# attack and its most recent attack.  Example:
# 
# If the centralized   denyhosts.net server records an attack at 2 PM 
# and then again at 5 PM, specifying a SYNC_DOWNLOAD_RESILIENCY = 4h 
# will not download this ip address.
#
# However, if the attacker is recorded again at 6:15 PM then the 
# ip address will be downloaded by your DenyHosts instance.  
#
# This value is used in conjunction with the SYNC_DOWNLOAD_THRESHOLD 
# and only hosts that satisfy both values will be downloaded.  
# This value has no effect if SYNC_DOWNLOAD_THRESHOLD = 1 
#
# The default is SYNC_DOWNLOAD_RESILIENCY = 5h (5 hours)
#
# Only obtain hackers that have been at it for 2 days or more:
#SYNC_DOWNLOAD_RESILIENCY = 2d
#
# Only obtain hackers that have been at it for 5 hours or more:
#SYNC_DOWNLOAD_RESILIENCY = 5h
#
#######################################################################

```**3. Create [COLOR=Blue]hosts.allow[/COLOR] and [COLOR=Blue]hosts.deny[/COLOR]:**

[COLOR=Purple]*Note: This step was not necessary in earlier versions of Ubuntu (6.10 & 6.06).*[/COLOR]

In Feisty Fawn 7.04, there appears to be a bug where the **hosts.allow** and **hosts.deny** files are missing.  Create them by typing the 2 commands below:
```
[COLOR=Red]sudo touch /etc/hosts.deny [/COLOR]
``````
[COLOR=Red]sudo touch /etc/hosts.allow[/COLOR] 
```[B]4. Starting & Stopping the denyhosts daemon manually:

[/B] To **start** denyhosts:
```
[COLOR=Red]sudo /etc/init.d/denyhosts start[/COLOR]
```To **stop** denyhosts:
```
[COLOR=Red]sudo /etc/init.d/denyhosts stop[/COLOR]
```[COLOR=Purple]Background: The denyhosts script resides in /etc/init.d/:[/COLOR]
```
dbott@feisty:/etc/init.d$ [COLOR=Red]ls -all denyhosts[/COLOR] 
-rwxr-xr-x 1 root root 1948 2006-12-12 11:35 denyhosts

```[COLOR=Purple]and there is a link in the /etc/rc.3 directory that starts the script automatically at boot-time:[/COLOR]
```

dbott@feisty:/etc/rc3.d$ [COLOR=Red]ls -all S20denyhosts [/COLOR]
lrwxrwxrwx 1 root root 19 2007-05-21 16:28 S20denyhosts -> ../init.d/denyhosts
```**5. Purging hosts from /etc/hosts.deny:**

If there are valid hosts that end up being blocked (i.e. during testing or forgotten password, etc.), you can purge any entries in the **/etc/hosts.deny** file by running the denyhosts script with the **--purge** option.  The hosts must be older than the value set in **PURGE_DENY**, so you may want to lower the value temporarily in order to purge the valid host (i.e. to purge entries older than 1 minute, set **PURGE_DENY = 1m** in the **/etc/denyhosts.conf** file):

**a. Stop the DenyHosts service:**
```
dbott@feisty:~$ [COLOR=Red]sudo /etc/init.d/denyhosts stop[/COLOR]
 * Stopping DenyHosts denyhosts                                     [ OK ] 
```**b. Purge Hosts:**
```
dbott@feisty:~$[COLOR=Red] sudo denyhosts --purge[/COLOR]
```**c. Restart the DenyHosts service:**
```
dbott@feisty:~$ [COLOR=Red]sudo /etc/init.d/denyhosts start[/COLOR]
 * Starting DenyHosts denyhosts                                      [ OK ] 
```While testing, you may want to open 2 terminal windows, one that watches the auth.log file and the other that watches the hosts.deny file:

```

dbott@feisty:/etc/rc3.d$ [COLOR=Red]tail -f -s3 /var/log/auth.log[/COLOR]
May 21 17:31:24 feisty sudo:    dbott : TTY=pts/0 ; PWD=/home/dbott ; USER=root ; COMMAND=/etc/init.d/denyhosts start
May 21 17:36:44 feisty sudo:    dbott : TTY=pts/0 ; PWD=/home/dbott ; USER=root ; COMMAND=/etc/init.d/denyhosts stop
May 21 17:36:51 feisty sudo:    dbott : TTY=pts/0 ; PWD=/home/dbott ; USER=root ; COMMAND=/usr/sbin/denyhosts --purge
May 21 17:36:56 feisty sudo:    dbott : TTY=pts/0 ; PWD=/home/dbott ; USER=root ; COMMAND=/etc/init.d/denyhosts start
May 21 18:17:01 feisty CRON[7806]: (pam_unix) session opened for user root by (uid=0)
May 21 18:17:01 feisty CRON[7806]: (pam_unix) session closed for user root

``````

dbott@feisty:/etc/rc3.d$ [COLOR=Red]tail -f -s3 /etc/hosts.deny[/COLOR]

```-Dave

---

### Post by DigitalDuality on 2007-06-05
d

---

### Post by dbott67 on 2007-06-06
I'm not sure if it is available for Breezy.  Make sure you have the "Backports" enabled in the repos:

[http://ubuntuguide.org/wiki/Ubuntu#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu#How_to_add_extra_repositories)

If it's not available in the Breezy Repos, then you may have to download the Debian .deb and follow the instructions on this page:

[http://denyhosts.sourceforge.net/faq.html#1_15](http://denyhosts.sourceforge.net/faq.html#1_15)
> [B]Is DenyHosts available as a Debian package?

[/B]Thanks to Marco Bertorello, DenyHosts is now available as a  [Debian package]("http://bertorello.ns0.it/debian/binary/denyhosts").  Falko Timme has written a "How To" document on  [How to  setup DenyHosts on Debian]("http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts")

-Dave

---

### Post by neozen on 2007-06-10
awesome mon... been looking for something to do this for quite a while now.... messed around w/ sshblack and a few others but couldn't get them to work (call it lack of time) ... this came straight out of the repos, installed like a champ.. and has blocked 3 dictionary attacks thusfar... nice setup tutorial

---

### Post by silverglade00 on 2007-07-02
In case anyone else is getting the not found error that I got, you have to have Universe enabled in Feisty.

---

### Post by Pentagonees on 2007-08-08
Nice Howto! Two questions actually:

1. How effective is DenyHosts when your machine is behind a router? I mean, doesn't the router have some sort of firewall function, that renders Denyhosts useless?

2. I tried compiling Denyhosts from source, as well as using the *.deb files from the suggested sites, but to no avail... I run Ubuntu 6.06 Dapper-Server edition, with the following repositories enabled:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multivers

---

### Post by dbott67 on 2007-08-08
> **Pentagonees said:**
> Nice Howto! Two questions actually:

1. How effective is DenyHosts when your machine is behind a router? I mean, doesn't the router have some sort of firewall function, that renders Denyhosts useless?

If you do not permit outside SSH access through your router (for example, you create a port-forward rule on the router that permits external traffic on port 22 to reach your Ubuntu computer), then Denyhosts is not needed.  Your router will protect all computers against unsolicited inbound attacks.

But if you wish to allow external access via SSH, Denyhosts will protect against the bruteforce, dictionary-style attacks.

> **Pentagonees said:**
>  2. I tried compiling Denyhosts from source, as well as using the *.deb files from the suggested sites, but to no avail... I run Ubuntu 6.06 Dapper-Server edition, with the following repositories enabled:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multivers

What seems to be the problem?  What happens when you install the .debs using apt-get or Synaptic?  Any error messages?

-Dave

---

### Post by Pentagonees on 2007-08-08
Well, apt-get won't work, since there is no candidate for Denyhosts in 6.06 (I guess...). 

When I try to install the .deb files from the suggested website, it seems to work out, right up to the point where I install the Denyhost package itself (after "sudo dpkg -i denyhosts-something.deb" it seems to start, but then spits out a bunch of errors).

Compiling from source seemed to have worked, but I couldn't get it to start at boottime. 

Then there's the other thing with the two machines that can access (my desktop and my laptop) the server are directly added to the hosts.deny file (with the entry sshd: 192.168.x.xxx), once I try to login. Luckily I had those two IP-addressess mentioned in the hosts.allow file, otherwise I wouldn't have been able to log in.

---

### Post by dbott67 on 2007-08-08
> **Pentagonees said:**
> Well, apt-get won't work, since there is no candidate for Denyhosts in 6.06 (I guess...). 

Yes.  It appears that there isn't a backport of Denyhosts available for Dapper or Breezy.  A search for "Denyhosts" in the packages returns [this result]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=denyhosts&searchon=names&subword=1&version=all&release=all").


> **Pentagonees said:**
>  When I try to install the .deb files from the suggested website, it seems to work out, right up to the point where I install the Denyhost package itself (after "sudo dpkg -i denyhosts-something.deb" it seems to start, but then spits out a bunch of errors).

It may be dependency issues.  Can you post any of the errors?

> **Pentagonees said:**
>  Compiling from source seemed to have worked, but I couldn't get it to start at boottime. 


Try starting the script manually:
```
sudo /etc/init.d/denyhosts start
```If this works, you will need to create a link in /etc/rc.3/ to the script in /etc/init.d/ (see the background section in step #4 above).

> **Pentagonees said:**
>  Then there's the other thing with the two machines that can access (my desktop and my laptop) the server are directly added to the hosts.deny file (with the entry sshd: 192.168.x.xxx), once I try to login. Luckily I had those two IP-addressess mentioned in the hosts.allow file, otherwise I wouldn't have been able to log in.

Step #5 above should help with purging any entries.  Be sure to set the PURGE_DENY value to something fairly low to allow the IP addresses to be purged.

-Dave

---

### Post by Pentagonees on 2007-08-09
I'll give it a go, as soon as I'm home tonight. I'll let you know if it works. Thanks for the help so far!

---

### Post by WookieLuv0nMarz on 2007-08-15
Well i set it all up and im waiting for the attackers.. a client of mine gets over 400 attacks a day from a cheeseegg.br or something.

---

### Post by russell.h on 2007-08-15
Excellent, thank you, I've been sitting around watching hundreds of failed login attempts every hour and beginning to get annoyed just on the principle of the thing (my password is pretty obscure, and they haven't even gotten the user name right yet).

It took this one IP address all of about a quarter of a second to end up in hosts.deny :)

Now maybe I can stop worrying about running out of hard drive space from all these log files.....

---

### Post by satimis on 2007-08-24
Hi dbott67,


Ubuntu 7.04 lamp server amd64


Just came across your guide on searching doc to create hosts.deny and hosts.allow which can't be found on the box.  According to your guide the 2 files created are empty.  Where can I find their scripts.

TIA


B.R.
satimis

---

### Post by dbott67 on 2007-08-24
> **satimis said:**
> ...According to your guide the 2 files created are empty.... 

Yes, the 2 files are empty.  The DenyHosts script will put any "attacking" hosts in hosts.deny automatically, so you don't need to put anything in there yourself.  If you've never been attacked, there won't be anything in the file.

As for the hosts.allow, you would put any hosts in there that you do not want to blacklist (i.e. any trusted IP address).  This would prevent you from getting blacklisted while at work or school if you mis-typed the password more than a few times.

If I'm not explaining myself very well, please let me know.

-Dave

---

### Post by satimis on 2007-08-24
Hi Dave,


Tks for your advice.


> **dbott67 said:**
> Yes, the 2 files are empty.  The DenyHosts script will put any "attacking" hosts in hosts.deny automatically, so you don't need to put anything in there yourself.  If you've never been attacked, there won't be anything in the file.

Noted.

What will be the result if entering "ALL:ALL" on hosts.deny?

> 
As for the hosts.allow, you would put any hosts in there that you do not want to blacklist (i.e. any trusted IP address).  This would prevent you from getting blacklisted while at work or school if you mis-typed the password more than a few times.

Noted and thanks.

> 
If I'm not explaining myself very well, please let me know.

It is quite clear.

B.R.
satimis

---

### Post by dbott67 on 2007-08-25
> **satimis said:**
> What will be the result if entering "ALL:ALL" on hosts.deny?

It would deny access to all services for all hosts.  If you wanted to be able to block everyone, yet still allow yourself in you would need to create an exception or add yourself to hosts.allow.

Here's a sample config I use on my RHEL server at work:
```

[root@hip ~]# cat /etc/hosts.allow 
#
# hosts.allow   This file describes the names of the hosts which are
#               allowed to use the local INET services, as decided
#               by the '/usr/sbin/tcpd' server.
#
sshd: 127.0.0.1

# Domain
sshd: .my.work.domain.com

# Firewall
sshd: ccc.ddd.244.114

# Vendor Tech Support IPs
sshd: xxx.yyy.247.106, aaa.bbb.158.10

# DBott from home
sshd: *.my.isp.com

``````

[root@hip ~]# cat /etc/hosts.deny
#
# hosts.deny    This file describes the names of the hosts which are
#               *not* allowed to use the local INET services, as decided
#               by the '/usr/sbin/tcpd' server.
#
# The portmap line is redundant, but it is left to remind you that
# the new secure portmap uses hosts.deny and hosts.allow.  In particular
# you should know that NFS uses portmap!


sshd:ALL EXCEPT localhost \
: spawn /bin/echo `/bin/date` access denied for %a %h>>/var/log/sshd.log
```

Before changing the hosts.allow and hosts.deny, my log file was filled with brute force attempts to SSH in.  Since enabling this, this is what my log file looks like now:
```
Fri Aug 10 08:47:17 EDT 2007 access denied for ::ffff:64.76.204.99 mail.intervida.org.pe
Fri Aug 10 09:02:13 EDT 2007 access denied for ::ffff:64.76.204.99 mail.intervida.org.pe
Fri Aug 10 09:20:09 EDT 2007 access denied for ::ffff:64.76.204.99 mail.intervida.org.pe
Fri Aug 10 09:30:11 EDT 2007 access denied for ::ffff:64.76.204.99 mail.intervida.org.pe
Fri Aug 10 17:14:41 EDT 2007 access denied for ::ffff:218.55.193.136 ::ffff:218.55.193.136
Sat Aug 11 17:30:57 EDT 2007 access denied for ::ffff:131.104.48.173 potter.cis.uoguelph.ca
Sat Aug 11 17:38:34 EDT 2007 access denied for ::ffff:131.104.48.173 potter.cis.uoguelph.ca
Sat Aug 11 22:31:09 EDT 2007 access denied for ::ffff:24.158.163.108 24-158-163-108.dhcp.jcsn.tn.charter.com
Sat Aug 11 22:31:37 EDT 2007 access denied for ::ffff:24.158.163.108 24-158-163-108.dhcp.jcsn.tn.charter.com
Sun Aug 12 04:22:18 EDT 2007 access denied for ::ffff:222.73.231.121 ::ffff:222.73.231.121
Sun Aug 12 04:27:15 EDT 2007 access denied for ::ffff:222.73.231.121 ::ffff:222.73.231.121
Mon Aug 13 05:03:30 EDT 2007 access denied for ::ffff:222.90.234.68 ::ffff:222.90.234.68
Mon Aug 13 16:44:44 EDT 2007 access denied for ::ffff:218.95.228.152 ::ffff:218.95.228.152
Mon Aug 13 17:04:35 EDT 2007 access denied for ::ffff:218.95.228.152 ::ffff:218.95.228.152
Tue Aug 14 06:21:26 EDT 2007 access denied for ::ffff:222.73.104.213 ::ffff:222.73.104.213
Tue Aug 14 08:42:44 EDT 2007 access denied for ::ffff:222.135.144.23 ::ffff:222.135.144.23
Tue Aug 14 09:48:43 EDT 2007 access denied for ::ffff:222.135.144.23 ::ffff:222.135.144.23
Tue Aug 14 13:02:49 EDT 2007 access denied for ::ffff:59.106.14.41 ::ffff:59.106.14.41
Tue Aug 14 13:13:26 EDT 2007 access denied for ::ffff:59.106.14.41 ::ffff:59.106.14.41
Tue Aug 14 13:39:13 EDT 2007 access denied for ::ffff:61.146.178.13 ::ffff:61.146.178.13
Tue Aug 14 18:31:25 EDT 2007 access denied for ::ffff:222.168.102.67 ::ffff:222.168.102.67
Tue Aug 14 23:00:02 EDT 2007 access denied for ::ffff:82.103.65.2 server.transcapital.bg
Wed Aug 15 13:50:51 EDT 2007 access denied for ::ffff:71.231.123.145 c-71-231-123-145.hsd1.wa.comcast.net
Wed Aug 15 13:59:22 EDT 2007 access denied for ::ffff:71.231.123.145 c-71-231-123-145.hsd1.wa.comcast.net
Wed Aug 15 17:30:52 EDT 2007 access denied for ::ffff:158.75.59.5 opty.xlo.torun.pl
Thu Aug 16 01:06:42 EDT 2007 access denied for ::ffff:222.171.127.162 ::ffff:222.171.127.162
Thu Aug 16 01:09:32 EDT 2007 access denied for ::ffff:222.171.127.162 ::ffff:222.171.127.162
Fri Aug 17 10:54:09 EDT 2007 access denied for ::ffff:211.93.0.213 ::ffff:211.93.0.213
Fri Aug 17 20:14:06 EDT 2007 access denied for ::ffff:202.201.241.243 ::ffff:202.201.241.243
Fri Aug 17 20:16:08 EDT 2007 access denied for ::ffff:202.201.241.243 ::ffff:202.201.241.243
Sat Aug 18 16:29:54 EDT 2007 access denied for ::ffff:202.123.27.159 ::ffff:202.123.27.159
Sat Aug 18 16:55:23 EDT 2007 access denied for ::ffff:202.123.27.159 ::ffff:202.123.27.159
Sun Aug 19 02:00:45 EDT 2007 access denied for ::ffff:211.200.44.249 ::ffff:211.200.44.249
Sun Aug 19 02:06:02 EDT 2007 access denied for ::ffff:211.200.44.249 ::ffff:211.200.44.249
Mon Aug 20 01:37:49 EDT 2007 access denied for ::ffff:211.78.3.69 dns.dotking.com.tw
Mon Aug 20 02:12:07 EDT 2007 access denied for ::ffff:211.78.3.69 dns.dotking.com.tw
Tue Aug 21 01:15:08 EDT 2007 access denied for ::ffff:58.47.168.236 ::ffff:58.47.168.236
Tue Aug 21 01:17:43 EDT 2007 access denied for ::ffff:58.47.168.236 ::ffff:58.47.168.236
Tue Aug 21 03:32:58 EDT 2007 access denied for ::ffff:60.28.23.21 ::ffff:60.28.23.21
Wed Aug 22 06:15:38 EDT 2007 access denied for ::ffff:202.107.245.4 ::ffff:202.107.245.4
Wed Aug 22 06:49:04 EDT 2007 access denied for ::ffff:202.107.245.4 ::ffff:202.107.245.4
Thu Aug 23 03:16:31 EDT 2007 access denied for ::ffff:200.7.97.194 mail.uniqueyacht.com
Thu Aug 23 03:17:53 EDT 2007 access denied for ::ffff:200.7.97.194 ::ffff:200.7.97.194
Thu Aug 23 15:41:22 EDT 2007 access denied for ::ffff:200.205.221.114 ::ffff:200.205.221.114
Thu Aug 23 15:45:26 EDT 2007 access denied for ::ffff:200.205.221.114 ::ffff:200.205.221.114
Fri Aug 24 14:12:53 EDT 2007 access denied for ::ffff:222.122.26.60 ::ffff:222.122.26.60

```-Dave

---

### Post by satimis on 2007-08-27
> **dbott67 said:**
> It would deny access to all services for all hosts.  If you wanted to be able to block everyone, yet still allow yourself in you would need to create an exception or add yourself to hosts.allow.

Here's a sample config I use on my RHEL server at work:
```

[root@hip ~]# cat /etc/hosts.allow 
#
# hosts.allow   This file describes the names of the hosts which are
#               allowed to use the local INET services, as decided
#               by the '/usr/sbin/tcpd' server.
#
sshd: 127.0.0.1

# Domain
sshd: .my.work.domain.com

# Firewall
sshd: ccc.ddd.244.114

# Vendor Tech Support IPs
sshd: xxx.yyy.247.106, aaa.bbb.158.10

# DBott from home
sshd: *.my.isp.com

```
What is #Firewall
sshd: ccc.ddd.244.144 ???

How to find it?  I don't have Firewall box.


> 
```

[root@hip ~]# cat /etc/hosts.deny
#
# hosts.deny    This file describes the names of the hosts which are
#               *not* allowed to use the local INET services, as decided
#               by the '/usr/sbin/tcpd' server.
#
# The portmap line is redundant, but it is left to remind you that
# the new secure portmap uses hosts.deny and hosts.allow.  In particular
# you should know that NFS uses portmap!


sshd:ALL EXCEPT localhost \
: spawn /bin/echo `/bin/date` access denied for %a %h>>/var/log/sshd.log
```
I suppose;```

sshd:ALL EXCEPT localhost \
: spawn /bin/echo `/bin/date` access denied for %a %h>>/var/log/sshd.log
```
in 2 lines?  Tks

I'll test it later.  I'm not on that server.

satimis

---

### Post by dbott67 on 2007-08-27
The Firewall in question is my work firewall.  The server running Redhat is in the DMZ, so I added the firewall IP so that I could access from any machine on the internal LAN.

-Dave

---

### Post by satimis on 2007-08-27
> **dbott67 said:**
> The Firewall in question is my work firewall.  The server running Redhat is in the DMZ, so I added the firewall IP so that I could access from any machine on the internal LAN.

Noted.


Performed following test;

Edited hosts.deny and hosts.allow.

$ cat /etc/host.allow```

sshd: 127.0.0.1

# Domain
sshd: .satimis.com

# Pacific from home
sshd: *.pacific.net.hk

```
Why it needs "."(dot) infront of "satimis.com"


$ cat /etc/host.deny ```

#
# hosts.deny    This file describes the names of the hosts which are
#               *not* allowed to use the local INET services, as decided
#               by the '/usr/sbin/tcpd' server.
#
# The portmap line is redundant, but it is left to remind you that
# the new secure portmap uses hosts.deny and hosts.allow.  In particular
# you should know that NFS uses portmap!


sshd:ALL EXCEPT localhost \
: spawn /bin/echo `/bin/date` access denied for %a %h>>/var/log/sshd.log

```

$ sudo /etc/init.d/denyhosts stop```

 * Stopping DenyHosts denyhosts                                          [ OK ] 

```

$ sudo denyhosts --purge
No printout

$ sudo /etc/init.d/denyhosts start```

 * Starting DenyHosts denyhosts                                          [ OK ] 

```

$ ls -al /var/log/ | grep sshd.log
No printout.  The log file can't be found


satimis

---

### Post by dbott67 on 2007-08-27
[quote=satimis]Why it needs "."(dot) infront of "satimis.com"[/quote]
Putting the dot in front would allow any host from my work domain to be allowed in.  From the [TCP Wrappers Configuration File]("http://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/ref-guide/s1-tcpwrappers-access.html") Site:
> 
_**Section 16.2.1.2**_

*Hostname beginning with a period         (.)* — Placing a period at         the beginning of a hostname, matches all hosts sharing the         listed components of the name. The following example applies to         any host within the example.com domain:           
ALL : .example.com
[quote=satimis]$ sudo denyhosts --purge
No printout[/quote]

Purging the hosts.deny file does not issue any output, however, if you check the file before & after, you will notice that any logged IP address that is older than the PURGE_DENY value will be removed.

[quote=satimis]$ ls -al /var/log/ | grep sshd.log

No printout.  The log file can't be found[/quote]
For Debian-based distros (such as Ubuntu) the sshd is logged in [COLOR=Purple]/var/log/auth.log[/COLOR].

Hope this helps.

-Dave

---

### Post by satimis on 2007-08-27
> **dbott67 said:**
> Putting the dot in front would allow any host from my work domain to be allowed in.  From the [TCP Wrappers Configuration File]("http://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/ref-guide/s1-tcpwrappers-access.html") Site:



Purging the hosts.deny file does not issue any output, however, if you check the file before & after, you will notice that any logged IP address that is older than the PURGE_DENY value will be removed.

All noted.  Tks

> 
For Debian-based distros (such as Ubuntu) the sshd is logged in [COLOR=Purple]/var/log/auth.log[/COLOR].

I got it.

$ tail -f /var/log/auth.log ```

Aug 27 23:17:01 ubuntu CRON[5157]: (pam_unix) session closed for user root
Aug 27 23:39:01 ubuntu CRON[5246]: (pam_unix) session opened for user root by (uid=0)
Aug 27 23:39:01 ubuntu CRON[5246]: (pam_unix) session closed for user root
Aug 27 23:49:54 ubuntu sudo:  satimis : TTY=tty1 ; PWD=/home/satimis ; USER=root ; COMMAND=/sbin/shutdown -h now
Aug 28 09:06:21 ubuntu sshd[4655]: Server listening on 0.0.0.0 port 22.
Aug 28 09:09:01 ubuntu CRON[4826]: (pam_unix) session opened for user root by (uid=0)
Aug 28 09:09:02 ubuntu CRON[4826]: (pam_unix) session closed for user root
Aug 28 09:09:51 ubuntu login[4336]: (pam_unix) session opened for user satimis by (uid=0)
Aug 28 09:17:01 ubuntu CRON[4907]: (pam_unix) session opened for user root by (uid=0)
Aug 28 09:17:01 ubuntu CRON[4907]: (pam_unix) session closed for user root

```

B.R.
satimis

---

### Post by hebetude on 2007-10-11
Here's a little off topic question...

Let's say I want to make a world map of all my blocked IPs based on geographical location (they're all china IPs but I do have 1 from italy!).  Anybody know of some nifty tools to help me make this?

---

### Post by swoosh on 2007-10-18
Hi,

May I know what messages should I expect from 

> tail -f -s3 /etc/hosts.deny

if I attempt a simulated internal attack on my ssh?

I have attempted few tries but nothing is logged. What can I do to see some failed attempts?

Thanks.

---

### Post by dbott67 on 2007-10-18
> **swoosh said:**
> Hi,

May I know what messages should I expect from 



if I attempt a simulated internal attack on my ssh?

I have attempted few tries but nothing is logged. What can I do to see some failed attempts?

Thanks.

You should see something like this:
```
dbott@feisty:~$ tail -f -s3 /etc/hosts.deny
# DenyHosts: Thu Oct 18 22:34:31 2007 | sshd: 192.168.1.107
sshd: 192.168.1.107

```
If you don't get anything showing up after a few attempts, make sure that DenyHosts is running:
```
dbott@feisty:~$ ps aux | grep deny
dbott     5007  0.0  0.0   2884   752 pts/0    R+   22:36   0:00 grep deny
root     20631  0.0  0.5   8336  4760 ?        SN   Oct14   0:00 python /usr/sbin/denyhosts --daemon --config=/etc/denyhosts.conf --config=/etc/denyhosts.conf

```Also make sure that the auth.log file shows the attempts:
```
dbott@feisty:~$ cat /var/log/auth.log | grep sshd
Oct 18 22:33:09 feisty sshd[4851]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.1.107  user=root
Oct 18 22:33:11 feisty sshd[4851]: Failed password for root from 192.168.1.107 port 1482 ssh2
Oct 18 22:34:03 feisty sshd[4889]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.1.107  user=root
Oct 18 22:34:04 feisty sshd[4889]: Failed password for root from 192.168.1.107 port 1483 ssh2
Oct 18 22:34:34 feisty sshd[4909]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.1.107  user=root
Oct 18 22:34:36 feisty sshd[4909]: Failed password for root from 192.168.1.107 port 1484 ssh2
Oct 18 22:35:13 feisty sshd[4909]: Failed password for root from 192.168.1.107 port 1484 ssh2
Oct 18 22:36:24 feisty sshd[4909]: fatal: Timeout before authentication for 192.168.1.107

```

-Dave

---

### Post by dbott67 on 2007-10-18
> **hebetude said:**
> Here's a little off topic question...

Let's say I want to make a world map of all my blocked IPs based on geographical location (they're all china IPs but I do have 1 from italy!).  Anybody know of some nifty tools to help me make this?

There are sites out there that offer software that can do this, such as [http://www.ip2location.com/](http://www.ip2location.com/) and other similar sites.  I don't know if there are any open source IP - Geolocation projects out there, but I'm certain that someone familiar with the API for Google Maps can scrape the data from a service similar to the above and make a pretty cool mash-up.

-Dave

---

### Post by mmistroni on 2008-02-25
Hello,
 followed this tutorial, worked like a charm. have blocked already 6 sites...
i was curious on couple of things:
1- somehow, denyhosts locked me out.... might be because i access (successfully though) my host every day?
2 - i'd like to block access also to port 25 as i noticed that i have many intruder trying to login to my mail server.
i have strong passwords, so i am not particularly worried - also because i am using VPS as a learning tool for configuring my own LInux server - but i'd like to discourage those intruders by locking them out

how will i do it? what is the correct syntax?

is it
BLOCK_SERVICES=sshd, smtp ?

i'd love to use BLOCK_SERVICES=ALL but i fear i will be locked out forever from my VPS (currently, i am using ssh to login)

anyone could give me some advices?

regards
 marco

---

### Post by hebetude on 2008-02-25
Mine started locking me out when I upgraded to Hardy on my server.  Don't know why, I checked the logs and didn't see 3 unsuccessful attempts (as I specified).  Very disappointing it has worked great for months now.

---

### Post by s4s on 2008-05-16
how do is denyhosts disabled or removed when no longer needed?

ty a lot.

s4s

---

### Post by berzerke on 2008-06-27
When I tried to use denyhosts on Gutsy, it would give me the following on startup:

>   File "/usr/bin/denyhosts.py", line 5, in <module>
    import DenyHosts.python_version
ImportError: No module named DenyHosts.python_version


In case anyone else has this issue, I found the fix. Edit the /etc/init.d/denyhosts file.
Change (or comment out) > PYTHON_BIN = /usr/bin/env python"
to
> PYTHON_BIN = "/usr/bin/python2.4"


---

### Post by osx on 2008-09-04
I'm a little confused about allowing hosts. I installed denyhosts on an Ubuntu 6.06.1 server and tested it to make sure my IP would be blocked after the specified threshold. Now, I want to add my IP in the allowed list so that it never gets blocked again.

Some material I read says to create a file called "allowed-hosts" in WORK_DIR and others say to edit /etc/hosts.allow. I've tried both methods and I still cannot get back in from the IP that was blocked.

I'm running version 2.6 of DenyHosts.

What am I doing wrong? Is there a service I need to restart or something? Also, if "allowed-hosts" is the correct file, is the path /etc/allowed-hosts or /usr/share/denyhosts/allowed-hosts or something else?

Thanks.

---

### Post by osx on 2008-09-04
Never mind. I figured it out.

1. You are supposed to use "allowed-hosts"

2. WORK_DIR = /usr/share/denyhosts/data

3. Hosts/IPs in allowed-hosts are still not allowed if they have already been blocked. So, after you add them to /usr/share/denyhosts/data/allowed-hosts you must also delete them from /etc/hosts.deny if they have been blocked already

Thanks.

---

### Post by panosssvent19 on 2013-04-01
I have a issue i am trying to install denyhosts and i have this error anyone can help???

Installing denyhosts (2.6-10) ...
 * Starting DenyHosts denyhosts                                                                                                                               
start-stop-daemon: error while loading shared libraries: libmysqlclient_r.so.16: cannot open shared object file: No such file or directory
invoke-rc.d: initscript denyhosts, action "start" failed.
dpkg: error configuring denyhosts (--configure):
 subprocegure installed post-installation script returned an error 127
Error at the configuration of
 denyhosts
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

