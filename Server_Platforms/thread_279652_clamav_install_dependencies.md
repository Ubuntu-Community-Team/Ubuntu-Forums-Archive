---
title: "clamav install dependencies"
date: 2006-10-18
forum: Server Platforms
---

### Post by dcherryholmes on 2006-10-18
Anyone know how to get around this? BTW, the initial command was "sudo apt-get install clamav".  I tried the -f install as a suggested fix for the problem of not having the dependencies set up in the first place.

root@[hostname]:/etc/mail# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clamav-base (0.88.4-1ubuntu1~dapper1) ...
chown: `clamav:clamav': invalid group
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (= 0.88.4-1ubuntu1~dapper1); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
E: Sub-process /usr/bin/dpkg returned an error code (1)
You have mail in /var/mail/dmc

---

### Post by dcherryholmes on 2006-10-19
Wow.  Really?  

Sendmail is broken, and you'd have to install clamav from source if you want it.  IMO Ubuntu is *not* ready for use in the enterprise.

I submitted a bug report in Launchpad.  If I figure out the answer on my own I'll post it for the next guy who drank the "it just works" kool-aid.

---

### Post by Damiel on 2006-11-04
I got the same problem. After completely removing clamav and reinstalling it the problem went away.

---

