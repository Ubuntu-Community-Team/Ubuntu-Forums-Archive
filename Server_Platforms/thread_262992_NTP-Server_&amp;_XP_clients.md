---
title: "NTP-Server &amp; XP clients"
date: 2006-09-22
forum: Server Platforms
---

### Post by isaac_golding on 2006-09-22
I recently installed an NTP-server into my LAN file server.   In the past when running NTP on a Mandrake server I simply installed the ntp-server and its default settings were "good to go"

However after installing on this OS I'm getting the following error:

"An error occurred while Windows was sync'ing with 192.168.1.5
The time sample was rejected because: The peer's stratum is less than
the host's stratum"

All of the config files on the ubuntu boxes for NTP are at default install values.  I'm running the current Ubuntu release....(Sep 06)


I'm being lazy here and hoping somebody has the quick answer so that I dont need to spend a bunch of time doing research on everything I probably never wanted to know about NTP

---

### Post by ewschone on 2006-09-22
Just recently installed an Ubuntu Server and had the same problem, turned out ntpd wasnt running as it should. It had unsufficient rights to write the 'drift'file. And somehow I also had it running twice o.O. 

So check the /var/log/messages and /var/log/sysd logs and do a ps -A | grep 'ntpd' to see what's up. And maybe edit your ntpd.conf to use some local ntp servers.

You might also want to check ntpq to check your server
[http://www.ee.udel.edu/~mills/ntp/html/ntpq.html](http://www.ee.udel.edu/~mills/ntp/html/ntpq.html)

Once the ntpd was running as it should, the error in windows disappeared.

---

### Post by isaac_golding on 2006-09-24
So I spent the better part of a day messing with this thing, reading all about NTP on the web (everything I didnt want to know in the first place) and in the end I was never able to find any errors on the ntp server side of the house and gave up on it.   Its not like I can't sync to external servers.... Just trying to run stuff in house.


But it was a learning adventure none the less....

:-)

---

