---
title: "IPBLOCK IPlist not working"
date: 2011-10-31
forum: Security
---

### Post by IchBinWamphyri on 2011-10-31
when i load [http://tinyurl.com/ya2atpt](http://tinyurl.com/ya2atpt) IPblock i get:
"iplist[4993]: error: can't find level1.gz
ipblock[4947]: error:failed to start, cleaning up"
running ubuntu 11.10
also in terminal i typed:
egrep "iplist|ipblock" /var/log/syslog
and i got this:
Oct 30 23:31:17 Tom1110 &#65279;AptDaemon: INFO: InstallFile() was called: /media/Internal 2TB/Ubuntu Files/Downloads/iplist_0.28-lenny0_i386.deb
Oct 30 23:31:21 Tom1110 &#65279;AptDaemon.Worker: INFO: Installing local package file: /media/Internal 2TB/Ubuntu Files/Downloads/iplist_0.28-lenny0_i386.deb
Oct 30 23:31:25 Tom1110 &#65279;AptDaemon.Worker: INFO: Installing local package file: /media/Internal 2TB/Ubuntu Files/Downloads/iplist_0.28-lenny0_i386.deb
Oct 30 23:32:49 Tom1110 iplist[15354]: error: can't find level1.gz
Oct 30 23:32:49 Tom1110 ipblock[15340]: error: failed to start, cleaning up
Oct 31 10:31:59 Tom1110 iplist[3885]: error: can't find level1.gz
Oct 31 10:31:59 Tom1110 ipblock[3871]: error: failed to start, cleaning up
Oct 31 10:32:49 Tom1110 iplist[3950]: error: can't find level1.gz
Oct 31 10:32:49 Tom1110 ipblock[3936]: error: failed to start, cleaning up
Oct 31 10:40:38 Tom1110 iplist[4194]: error: can't find level1.gz
Oct 31 10:40:38 Tom1110 ipblock[4180]: error: failed to start, cleaning up
Oct 31 10:43:56 Tom1110 iplist[4663]: error: can't find level1.gz
Oct 31 10:43:56 Tom1110 ipblock[4649]: error: failed to start, cleaning up
Oct 31 11:06:09 Tom1110 ipblock[4840]: error: IPblock needs to be run as root
Oct 31 11:06:17 Tom1110 iplist[4846]: error: can't find level1.gz
ive been using this program since karmic and it has been quite useful, has anyone else had any problems/solutions? please help

---

### Post by Diametric on 2011-11-01
Is this for just a local machine or are you running any DNS?

---

### Post by jsharp768 on 2011-11-03
Their servers aren't responding:

[http://www.bluetack.co.uk/config/level1.gz](http://www.bluetack.co.uk/config/level1.gz)

This explains it ([http://www.bluetack.co.uk/):]("http://www.bluetack.co.uk/%29:")
**Dear members and guests, as you may have noticed the Bluetack  forums, forum registration, and our related blocklist services have been  limited. While we continue our research, please consider helping out.** 
**November bills have come in. We have not reached the goal  for this month. Please, if you value our work, donate toward the monthly  server fees.** 

I was able to manually update all of my lists from here: [http://www.iblocklist.com/lists.php](http://www.iblocklist.com/lists.php)

Look for your list, then download it to /var/cache/iplist or whatever is defined in your ipblock.conf.

---

