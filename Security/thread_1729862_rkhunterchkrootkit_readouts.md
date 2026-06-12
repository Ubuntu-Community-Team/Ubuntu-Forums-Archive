---
title: "rkhunter/chkrootkit readouts"
date: 2011-04-15
forum: Security
---

### Post by thelugnut on 2011-04-15
I have completed running rkhunter and chkrootkit with the following results. I do not know what the warnings are or what they might be. Can someone help me understand what I have here?
Thanks


--------------------------------------------------------------------------------
Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

--------------------------------------------------------------------------------

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

------------------------------------------------------------------------------
(/var/log/rkhunter.log)

Warning: Suspicious file types found in /dev:
[19:59:51]          /dev/shm/pulse-shm-4189787853: data
[19:59:51]          /dev/shm/pulse-shm-2627624727: data
[19:59:51]          /dev/shm/pulse-shm-2399751008: data
[19:59:51]          /dev/shm/pulse-shm-368144462: data
[19:59:51]   Checking for hidden files and directories       [ Warning ]
[19:59:51] Warning: Hidden directory found: /etc/.java
[19:59:51] Warning: Hidden directory found: /dev/.udev
------------------------------------------------------------------------------
------------------------------------------------------------------------------
I then ran chkrootkit with the following warnings:
------------------------------------------------------------------------------
Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/pymodules/python2.6/.path /usr/lib/xulrunner-1.9.2.16/.autoreg /usr/lib/firefox-3.6.16/.autoreg
------------------------------------------------------------------------------

---

### Post by bodhi.zazen on 2011-04-15
There is information on this in the stickies and this recent page

[https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter)

This is not windows and to use these tools you need to be willing to read and use google. They put out a lot of information and warnings as well as a lot of false positives.

Only you can determine what is normal on your system and tracking a root kit is complicated.

See the links in the security sticky on forensics and notice that "how to's" on forensics and rootkits do not typically use these tools.

---

