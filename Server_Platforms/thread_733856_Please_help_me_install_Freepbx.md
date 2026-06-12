---
title: "Please help me install Freepbx"
date: 2008-03-24
forum: Server Platforms
---

### Post by bmh on 2008-03-24
Dear expert,

I am a newbie in Ubuntu also Linux. I try to install the Asterisk Server and Freepbx 2.4.0 in my server.

All the processing of installation Asterisk done well but when I tried to install FreePBX I got a problem. I could not install the amportal.

Please see follow my server shows:

root@fitel-technology:/usr/src/freepbx-2.4.0# ps aux | grep asterisk
root      5418  0.0  0.0   3884   904 ?        S    18:38   0:02 /bin/bash /usr/sbin/safe_asterisk -U asterisk -G asterisk
asterisk 10058  0.0  0.6  38332  6240 ?        S    18:58   0:00 /usr/sbin/apache2 -k start
asterisk 10059  0.0  0.5  38332  6124 ?        S    18:58   0:00 /usr/sbin/apache2 -k start
asterisk 10060  0.0  0.5  38332  5584 ?        S    18:58   0:00 /usr/sbin/apache2 -k start
asterisk 10061  0.0  0.5  38332  5580 ?        S    18:58   0:00 /usr/sbin/apache2 -k start
asterisk 10062  0.0  0.5  38332  5580 ?        S    18:58   0:00 /usr/sbin/apache2 -k start
asterisk 12142  0.0  0.5  38332  5580 ?        S    19:07   0:00 /usr/sbin/apache2 -k start
asterisk 12143  0.0  0.5  38332  5580 ?        S    19:07   0:00 /usr/sbin/apache2 -k start
asterisk 12144  0.0  0.5  38332  5580 ?        S    19:07   0:00 /usr/sbin/apache2 -k start
root     16220  0.0  0.0   2976   752 pts/1    R+   19:25   0:00 grep asterisk
root@fitel-technology:/usr/src/freepbx-2.4.0# ./install_amp
Checking for PEAR DB..OK
Checking for PEAR Console::Getopt..OK
Checking user..OK
Checking if Asterisk is running..FAILED
[FATAL] ./install_amp
        Asterisk must be running. If this is a first time install, you should start
        Asterisk by typing './start_asterisk start'
        For upgrading, you should run 'amportal start'
root@fitel-technology:/usr/src/freepbx-2.4.0#



I am very thanks for help.
Newbie

---

### Post by tinycamp on 2008-04-23
check your permissions, and why safe_asterisk?..... and WHY does asterisk own apache?

---

