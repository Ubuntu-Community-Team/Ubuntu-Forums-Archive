---
title: "Syslog files grow larger on 8.04 then 7.10"
date: 2010-05-07
forum: Server Platforms
---

### Post by genoint on 2010-05-07
Hi guys, 
 
I am hoping someone can help. I have an Ubuntu server that is strictly used for Syslog and Cacti, CLI no GUI, it is running on version 7.10. All is well...converted this server to virtual machine using VMWare and it is running on a VMWare ESX4 host. Once it was converted upgraded to 8.04LTS, both machines (physical and virtual) running in parallel with different IP addresses. Cacti and Syslog on both work fine.
 
The issue I am having is on the 8.04 server the syslog files, (not syslog.0) are all larger than the 7.10 server, much larger. On the 7.10 for example, a log file for a VPN device is 17mb, the same file on the 8.04 server is 170mb. This is causing an issue because the log file for the firewall reaches the 2gb limit after only 6 hours or so on the 8.04 server and stops logging data. The same log data on the 7.04 server for a 24 hour period is 500mb. These are not files copied during the conversion, but they are actual logs captured.
 
I searched the forums and the internet and cannot seem to find anything about this. The only thing I have found that is similar was referencing turning off ACPI which I have done by adding noapci switch to menu.lst, and it did not help.
 
If anyone has any suggestions or have come across this before I would appreciate any help.

---

### Post by genoint on 2010-05-12
<<bump>>
 
Sorry for bumping my own post but I haven't gotten any responses.  I guess this is over everyones head then?

---

### Post by volkswagner on 2010-05-12
I feel your pain.

Perhaps if you can show a comparison of the two, we can see what is too verbose?  

I thought my syslog was out of control.  2gig in hours is incredible.  I thought Citadel was overly verbose, but my entries don't compare to your volume.

If you know what is causing the rapid growth, someone may be able to help tame the log hog.

---

### Post by genoint on 2010-05-13
> **volkswagner said:**
> I feel your pain.
 
Perhaps if you can show a comparison of the two, we can see what is too verbose? 
 
I thought my syslog was out of control. 2gig in hours is incredible. I thought Citadel was overly verbose, but my entries don't compare to your volume.
 
If you know what is causing the rapid growth, someone may be able to help tame the log hog.
 
A comparison of the syslog files?  They are identical, coming from the same firewall, just two different syslog servers.  Ubuntu 7.10/8.04 converted using VMware, one is physical, one is virtual.  But I said all of that in my original post...I just don't understand, if both are receiving the same data, why the 8.04 syslog files grow much larger that the original 7.10 server.

---

### Post by arrrghhh on 2010-05-13
You must have some program on a higher debugging level than necessary.  That's why he wanted to compare your syslogs ;)

---

### Post by Vegan on 2010-05-13
One way out is to use bigger root disks.

---

### Post by volkswagner on 2010-05-14
> **genoint said:**
> A comparison of the syslog files?  They are identical, coming from the same firewall, just two different syslog servers.  Ubuntu 7.10/8.04 converted using VMware, one is physical, one is virtual.  But I said all of that in my original post...I just don't understand, if both are receiving the same data, why the 8.04 syslog files grow much larger that the original 7.10 server.

I am having a hard time understanding files that have identical content (same amount of text) with different size on disk (7.10 vs. 8.04).   The file comparison request was for old log files compared to new log files (from 7.10 to 8.04). 

I don't think you will get specific help without posting some log content and/or your syslog.conf.

---

### Post by HermanAB on 2010-05-14
Well, nevermind what causes it - if it works, then all is well.

So, simply edit the logrotate.conf file and let it rotate logs more frequently or keep fewer old copies.

---

### Post by lavinog on 2010-05-16
Read the logs.  Usually something gets repeated over and over again.
You can use the less command to read the log without trying to load the entire file (gui based text readers will likely hang while the whole file is read)

If you don't wish to read the logs, delete them.

---

### Post by genoint on 2010-05-17
> **arrrghhh said:**
> You must have some program on a higher debugging level than necessary. That's why he wanted to compare your syslogs ;)
 
NOPE.
 
Like I said, same firewall sends same trap level, informational to 2 different Ubuntu servers.  Identical logs grow to 2 gb in a few hours on verion 8.10.
 
Anyhow, I am going to take a look at the logs to make sure nothing is getting repeated in the log file.
 
Below is syslog.conf, identical on both machines.  And unfortunately rotating logs more often is not possible as I will have over 10gb per day.  
 
I will also post some log content shortly.
 
#  /etc/syslog.conf     Configuration file for syslogd.
#
#                       For more information see syslog.conf(5)
#                       manpage.
#
# First some standard logfiles.  Log by facility.
#
auth,authpriv.*                 /var/log/auth.log
*.*;auth,authpriv,local0,local1,local2,local3,local4,local5,local6,local7.none          -/var/log/syslog
#cron.*                         /var/log/cron.log
daemon.*                        -/var/log/daemon.log
kern.*                          -/var/log/kern.log
lpr.*                           -/var/log/lpr.log
mail.*                          -/var/log/mail.log
user.*                          -/var/log/user.log
# Logs messages from Catalyst Switches
local6.debug                                    /var/adm/switches
# Logs messages from Internal CISCO routers
local3.debug                                    /var/adm/internal-router
# Logs messages from External CISCO routers
local0.debug                                    /var/adm/external-router
# Logs messages from Concentrator 3000
local7.debug                                    /var/adm/VPN
# Logs messages from  PIX in WPL
local5.debug                                    /var/adm/pix_WPL
# Logs messages from  PIX backup network in WPL
local1.debug                                    /var/adm/pixbackup_WPL
# Logs messages from  Cisco ASA in WPL
local2.debug                                    /var/adm/ASA_WPL
# Logs messages from  Cisco Content Switches 
local4.debug                                    /var/adm/BIGIP
#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
mail.info                       -/var/log/mail.info
mail.warn                       -/var/log/mail.warn
mail.err                        /var/log/mail.err
# Logging for INN news system
#
news.crit                       /var/log/news/news.crit
news.err                        /var/log/news/news.err
news.notice                     -/var/log/news/news.notice
#
# Some `catch-all' logfiles.
#
*.=debug;\
        auth,authpriv.none;\
        news.none;mail.none     -/var/log/debug
*.=info;*.=notice;*.=warn;\
        auth,authpriv.none;\
        cron,daemon.none;\
        mail,news.none;\
        local0,local1,local2,local3,local4,local5,local6,local7.none            -/var/log/messages
#
# Emergencies are sent to everybody logged in.
#
*.emerg                         *
#
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
#daemon,mail.*;\
#       news.=crit;news.=err;news.=notice;\
#       *.=debug;*.=info;\
#       *.=notice;*.=warn       /dev/tty8
# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
# 
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
        news.err;\
        *.=debug;*.=info;\
        *.=notice;*.=warn       |/dev/xconsole

---

### Post by genoint on 2010-05-17
Syslog log files have too many private ip addresses in them.  All devices have same trap lavel sending to 2 different servers, all file sizes are different, see below:
 
Version 7.10
-rw-rw-r-- 1 syslog adm     214010 2010-05-17 15:57 ASA_WPL
-rw-r----- 1 syslog adm     159577 2010-05-16 23:58 ASA_WPL.1
-rw-rw-r-- 1 syslog adm     363868 2010-05-16 00:02 ASA_WPL.3
-rw-rw-r-- 1 syslog adm     412233 2010-05-15 00:00 ASA_WPL.4
-rw-rw-r-- 1 syslog adm     313862 2010-05-13 00:02 ASA_WPL.5
-rw-rw-r-- 1 syslog adm     478234 2010-05-12 00:02 ASA_WPL.6
-rw-rw-r-- 1 syslog adm     510103 2010-05-11 00:02 ASA_WPL.7
-rw-r----- 1 syslog adm       4188 2010-05-17 12:37 external-router
-rw-r----- 1 syslog adm      27463 2010-05-16 06:30 external-router.0
-rw-r----- 1 syslog adm       6971 2010-05-09 05:48 external-router.1.gz
-rw-r----- 1 syslog adm       6270 2010-05-02 06:46 external-router.2.gz
-rw-r----- 1 syslog adm       5598 2010-04-25 06:02 external-router.3.gz
-rw-rw-r-- 1 syslog adm      41642 2010-05-17 15:56 internal-router
-rw-r----- 1 syslog adm      38439 2010-05-16 23:57 internal-router.1
-rw-rw-r-- 1 syslog adm      91709 2010-05-15 23:59 internal-router.3
-rw-rw-r-- 1 syslog adm      74783 2010-05-14 23:58 internal-router.4
-rw-rw-r-- 1 syslog adm      53834 2010-05-12 23:59 internal-router.5
-rw-rw-r-- 1 syslog adm      79046 2010-05-12 00:01 internal-router.6
-rw-rw-r-- 1 syslog adm      94308 2010-05-10 23:56 internal-router.7
-rw-rw-r-- 1 syslog adm          0 2010-05-17 00:02 pixbackup_WPL
-rw-rw-r-- 1 syslog adm          0 2010-05-16 00:02 pixbackup_WPL.1
-rw-rw-r-- 1 syslog adm        297 2010-05-15 22:56 pixbackup_WPL.2
-rw-rw-r-- 1 syslog adm          0 2010-05-14 00:02 pixbackup_WPL.3
-rw-rw-r-- 1 syslog adm          0 2010-05-13 00:02 pixbackup_WPL.4
-rw-rw-r-- 1 syslog adm          0 2010-05-12 00:02 pixbackup_WPL.5
-rw-rw-r-- 1 syslog adm          0 2010-05-11 00:02 pixbackup_WPL.6
-rw-rw-r-- 1 syslog adm          0 2010-05-10 00:02 pixbackup_WPL.7
-rw-rw-r-- 1 syslog adm  290370552 2010-05-17 15:59 pix_WPL
-rw-r----- 1 syslog adm  460471698 2010-05-17 00:02 pix_WPL.1
-rw-rw-r-- 1 syslog adm  754163179 2010-05-16 00:02 pix_WPL.3
-rw-r--r-- 1 root   root 150566661 2010-05-03 16:19 pix_WPL.3.filepart
-rw-rw-r-- 1 syslog adm  557476642 2010-05-15 00:02 pix_WPL.4
-rw-rw-r-- 1 syslog adm  435251497 2010-05-13 00:02 pix_WPL.5
-rw-rw-r-- 1 syslog adm  619231256 2010-05-12 00:02 pix_WPL.6
-rw-rw-r-- 1 syslog adm  704754843 2010-05-11 00:02 pix_WPL.7
-rw-rw-r-- 1 syslog adm      62104 2010-05-17 15:56 switches
-rw-r----- 1 syslog adm      42928 2010-05-17 00:00 switches.1
-rw-rw-r-- 1 syslog adm      46536 2010-05-15 23:59 switches.3
-rw-rw-r-- 1 syslog adm      62357 2010-05-15 00:00 switches.4
-rw-rw-r-- 1 syslog adm      70253 2010-05-12 23:55 switches.5
-rw-rw-r-- 1 syslog adm      94955 2010-05-12 00:00 switches.6
-rw-rw-r-- 1 syslog adm      94798 2010-05-11 00:02 switches.7
-rw-rw-r-- 1 syslog adm   11248525 2010-05-17 15:59 VPN
-rw-r----- 1 syslog adm    4726732 2010-05-17 00:02 VPN.1
-rw-rw-r-- 1 syslog adm   15093635 2010-05-16 00:02 VPN.3
-rw-rw-r-- 1 syslog adm   14167518 2010-05-15 00:02 VPN.4
-rw-rw-r-- 1 syslog adm   18026367 2010-05-13 00:02 VPN.5
-rw-rw-r-- 1 syslog adm   20641256 2010-05-12 00:02 VPN.6
-rw-rw-r-- 1 syslog adm   21724710 2010-05-11 00:02 VPN.7
 
Version 8.04
-rw-rw-r-- 1 syslog adm     5192686 2010-05-17 16:13 ASA_WPL
-rw-r----- 1 syslog adm     2939836 2010-05-17 00:18 ASA_WPL.1
-rw-rw-r-- 1 syslog adm     3992233 2010-05-16 00:02 ASA_WPL.3
-rw-rw-r-- 1 syslog adm     7833584 2010-05-15 00:20 ASA_WPL.4
-rw-rw-r-- 1 syslog adm     7730125 2010-05-13 00:19 ASA_WPL.5
-rw-rw-r-- 1 syslog adm     7775419 2010-05-12 00:10 ASA_WPL.6
-rw-rw-r-- 1 syslog adm     7026370 2010-05-11 00:25 ASA_WPL.7
-rw-r----- 1 syslog adm       37976 2010-05-17 15:26 external-router
-rw-r----- 1 syslog adm      119509 2010-05-16 06:44 external-router.0
-rw-r----- 1 syslog adm       11600 2010-05-09 06:36 external-router.1.gz
-rw-r----- 1 syslog adm        6270 2010-05-03 17:02 external-router.2.gz
-rw-r----- 1 syslog adm        5598 2010-05-03 17:02 external-router.3.gz
-rw-rw-r-- 1 syslog adm      457810 2010-05-17 16:12 internal-router
-rw-r----- 1 syslog adm      393830 2010-05-17 00:18 internal-router.1
-rw-rw-r-- 1 syslog adm      549702 2010-05-16 00:02 internal-router.3
-rw-rw-r-- 1 syslog adm      604071 2010-05-15 00:19 internal-router.4
-rw-rw-r-- 1 syslog adm      657817 2010-05-13 00:18 internal-router.5
-rw-rw-r-- 1 syslog adm      618446 2010-05-12 00:09 internal-router.6
-rw-rw-r-- 1 syslog adm      650027 2010-05-11 00:25 internal-router.7
-rw-rw-r-- 1 syslog adm           0 2010-05-17 00:18 pixbackup_WPL
-rw-rw-r-- 1 syslog adm           0 2010-05-16 00:02 pixbackup_WPL.1
-rw-rw-r-- 1 syslog adm         739 2010-05-15 23:10 pixbackup_WPL.2
-rw-rw-r-- 1 syslog adm           0 2010-05-14 00:29 pixbackup_WPL.3
-rw-rw-r-- 1 syslog adm           0 2010-05-13 00:19 pixbackup_WPL.4
-rw-rw-r-- 1 syslog adm           0 2010-05-12 00:10 pixbackup_WPL.5
-rw-rw-r-- 1 syslog adm           0 2010-05-11 00:25 pixbackup_WPL.6
-rw-rw-r-- 1 syslog adm           0 2010-05-10 00:05 pixbackup_WPL.7
-rw-rw-r-- 1 syslog adm  2147483647 2010-05-17 12:27 pix_WPL
-rw-r----- 1 syslog adm  2147483647 2010-05-16 20:45 pix_WPL.1
-rw-rw-r-- 1 syslog adm  2147483647 2010-05-15 16:05 pix_WPL.3
-rw-rw-r-- 1 syslog adm  2147483647 2010-05-14 14:29 pix_WPL.4
-rw-rw-r-- 1 syslog adm  2147483647 2010-05-12 12:01 pix_WPL.5
-rw-rw-r-- 1 syslog adm  2147483647 2010-05-11 13:14 pix_WPL.6
-rw-rw-r-- 1 syslog adm  2147483647 2010-05-10 13:25 pix_WPL.7
-rw-rw-r-- 1 syslog adm      133352 2010-05-17 16:11 switches
-rw-r----- 1 syslog adm       58683 2010-05-17 00:17 switches.1
-rw-rw-r-- 1 syslog adm       58568 2010-05-15 23:59 switches.3
-rw-rw-r-- 1 syslog adm      131046 2010-05-15 00:18 switches.4
-rw-rw-r-- 1 syslog adm      151961 2010-05-13 00:18 switches.5
-rw-rw-r-- 1 syslog adm      149084 2010-05-12 00:08 switches.6
-rw-rw-r-- 1 syslog adm      150687 2010-05-11 00:22 switches.7
-rw-rw-r-- 1 syslog adm   148486969 2010-05-17 16:13 VPN
-rw-r----- 1 syslog adm    33897648 2010-05-17 00:18 VPN.1
-rw-rw-r-- 1 syslog adm    91643958 2010-05-16 00:02 VPN.3
-rw-rw-r-- 1 syslog adm   130853459 2010-05-15 00:20 VPN.4
-rw-rw-r-- 1 syslog adm   243433903 2010-05-13 00:19 VPN.5
-rw-rw-r-- 1 syslog adm   163653652 2010-05-12 00:10 VPN.6
-rw-rw-r-- 1 syslog adm   148659861 2010-05-11 00:25 VPN.7

---

### Post by lavinog on 2010-05-17
Please wrap your output in code blocks to make it readable.

---

### Post by lavinog on 2010-05-17
```

# Logs messages from Catalyst Switches
local6.debug /var/adm/switches
# Logs messages from Internal CISCO routers
local3.debug /var/adm/internal-router
# Logs messages from External CISCO routers
local0.debug /var/adm/external-router
# Logs messages from Concentrator 3000
local7.debug /var/adm/VPN
# Logs messages from PIX in WPL
local5.debug /var/adm/pix_WPL
# Logs messages from PIX backup network in WPL
local1.debug /var/adm/pixbackup_WPL
# Logs messages from Cisco ASA in WPL
local2.debug /var/adm/ASA_WPL
# Logs messages from Cisco Content Switches
local4.debug /var/adm/BIGIP
```

This looks like debug information.
Are you certain that you need this information?
you can them out:
```

# Logs messages from Catalyst Switches
#local6.debug /var/adm/switches
# Logs messages from Internal CISCO routers
#local3.debug /var/adm/internal-router
# Logs messages from External CISCO routers
#local0.debug /var/adm/external-router
# Logs messages from Concentrator 3000
#local7.debug /var/adm/VPN
# Logs messages from PIX in WPL
#local5.debug /var/adm/pix_WPL
# Logs messages from PIX backup network in WPL
#local1.debug /var/adm/pixbackup_WPL
# Logs messages from Cisco ASA in WPL
#local2.debug /var/adm/ASA_WPL
# Logs messages from Cisco Content Switches
#local4.debug /var/adm/BIGIP

```

If you must have this information logged, this page: [http://colin.bitterfield.com/Articles/syslog_for_the_datacenter.html](http://colin.bitterfield.com/Articles/syslog_for_the_datacenter.html) mentions that you should have 18g available for the logs.

---

### Post by genoint on 2010-05-18
If you must have this information logged, this page: [http://colin.bitterfield.com/Articles/syslog_for_the_datacenter.html](http://colin.bitterfield.com/Articles/syslog_for_the_datacenter.html) mentions that you should have 18g available for the logs.[/QUOTE]
 
I do have more than 18gb available, space isn't the issue.  The issue is, two identical files are different sizes on two different paltforms.  It doesn't make any sense to me.

---

### Post by lavinog on 2010-05-18
What is telling you that they are identical?  did you try using diff to see if they are different?

---

### Post by genoint on 2010-05-18
> **lavinog said:**
> What is telling you that they are identical? did you try using diff to see if they are different?
 
Thanks for that, don't know why I didnt try this.  The packets are being logged twice for some reason, every 6 mins or so it seems that lines are duplicated.

---

### Post by genoint on 2010-05-25
> **genoint said:**
> Thanks for that, don't know why I didnt try this. The packets are being logged twice for some reason, every 6 mins or so it seems that lines are duplicated.
 
If anyone has any insight why this could be happening, it would be greatly appreciated.  I cant figure it out for the life of me as nothing is misconfigured as far as my network equipment is concerned.  Unless 37 devices are misconfigured, as all of my syslog files have duplicate entries.  It most definitely is the Ubuntu Server, I just cannot figure out why it is doing this.  
 
I also upgraded to 8.10.  My next step is to setup a separate server with a fresh install of version 10 and configure all of this from 'scratch.'

---

