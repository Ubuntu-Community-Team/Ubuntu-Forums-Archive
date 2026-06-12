---
title: "Snort install fails"
date: 2008-05-04
forum: Server Platforms
---

### Post by davegball on 2008-05-04
hey.

I'm trying to install Snort but without success. Following is the result of apt-get install. Note the "invoke-rc.d: initscript snort, action "start" failed" line half way down. Underneath is a tail -f /var/log/syslog which appears to show the configuration trying to find the Snort rules in /etc/snort.conf. Not sure why. 

$sudo apt-get install snort snort-common snort-common-libraries snort-rules-default

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  snort-doc
The following NEW packages will be installed:
  snort
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/461kB of archives.
After this operation, 1057kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package snort.
(Reading database ... 120448 files and directories currently installed.)
Unpacking snort (from .../snort_2.7.0-14_i386.deb) ...
Setting up snort (2.7.0-14) ...
 * Stopping Network Intrusion Detection System  snort                                                     * No running snort instance found
 * Starting Network Intrusion Detection System  snort                                             [fail] 
invoke-rc.d: initscript snort, action "start" failed.
dpkg: error processing snort (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 snort
E: Sub-process /usr/bin/dpkg returned an error code (1)
$

$sudo nano /var/log/syslog 

May  4 15:54:02 sushiman-laptop snort[10553]: , value = 192.168.2.0/255.255.255.0 
May  4 15:54:02 sushiman-laptop snort[10553]: Var 'any_ADDRESS' defined, value len = 15 chars
May  4 15:54:02 sushiman-laptop snort[10553]: , value = 0.0.0.0/0.0.0.0 
May  4 15:54:02 sushiman-laptop snort[10553]: Var 'lo_ADDRESS' defined, value len = 19 chars
May  4 15:54:02 sushiman-laptop snort[10553]: , value = 127.0.0.0/255.0.0.0 
May  4 15:54:02 sushiman-laptop snort[10553]: Parsing Rules file /etc/snort/snort.conf 
May  4 15:54:02 sushiman-laptop snort[10553]: FATAL ERROR: Unable to open
 rules file: /etc/snort/snort.conf or /etc/snort//etc/snort/snort.conf 

$ sudo dpkg-reconfigure snort 
[sudo] password for <>: 
/usr/sbin/dpkg-reconfigure: snort is broken or not fully installed
:~$

$nano /etc/snort/snort.debian.conf 

# This file is used for options that are changed by Debian to leave
# the original lib files untouched.
# You have to use "dpkg-reconfigure snort" to change them.

DEBIAN_SNORT_STARTUP="boot"
DEBIAN_SNORT_HOME_NET="192.168.0.2.0/24"
DEBIAN_SNORT_OPTIONS=""
DEBIAN_SNORT_INTERFACE="eth0"
DEBIAN_SNORT_SEND_STATS="true"
DEBIAN_SNORT_STATS_RCPT="root"
DEBIAN_SNORT_STATS_THRESHOLD="1"

thanks for any insights, 

David.

---

### Post by Thirtysixway on 2008-05-04
It looks to me that it's already installed.

Try running  **sudo apt-get remove snort**

If this doesn't work, try purging  **sudo apt-get --purge**

Hope you get it working.

---

