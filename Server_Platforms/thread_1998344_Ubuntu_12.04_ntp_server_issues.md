---
title: "Ubuntu 12.04 ntp server issues"
date: 2012-06-06
forum: Server Platforms
---

### Post by ranger12 on 2012-06-06
Boy just when you seem to get one thing going on this server - another thing arises. I cannot get the ntp server to function properly. I have the server firewall down and the router firewall down and from the server prompt I issue this:

ntpdate -q time-a.nist.gov or any other time server and I get this:

ntpdate[3927]: no server suitable for synchronization found

I have been researching on the net and all I have been able to find is the issue about the firewall.

I have tried various settings in my ntp.conf file that I have found around the net.

I will attach my ntp.conf file.

---

### Post by wilee-nilee on 2012-06-06
> **ranger12 said:**
> Boy just when you seem to get one thing going on this server - another thing arises. I cannot get the ntp server to function properly. I have the server firewall down and the router firewall down and from the server prompt I issue this:

ntpdate -q time-a.nist.gov or any other time server and I get this:

ntpdate[3927]: no server suitable for synchronization found

I have been researching on the net and all I have been able to find is the issue about the firewall.

I have tried various settings in my ntp.conf file that I have found around the net.

I will attach my ntp.conf file.

Wow server 21.04, are you like using a time machine. ;)

Report yourself to the mods to fix your header, they luv doing that, no biggie.

---

### Post by Doug S on 2012-06-06
Note sure how to help. It seems to work fine for me (12.04 test computer):```
doug@s15:~/temp$ ntpdate -q time-a.nist.gov
server 129.6.15.28, stratum 1, offset -1.652459, delay 0.17758
 6 Jun 11:39:16 ntpdate[1182]: step time server 129.6.15.28 offset -1.652459 sec
```As a test, try eliminating your restrict rules.

---

### Post by ranger12 on 2012-06-06
Okay Doug, I will give that a try and see what happens. Thanks.

---

### Post by ranger12 on 2012-06-06
I remmed out all the restrict rules but it did no good. I get the same result. It is amazing how something,that according to the server guide, should be easy to set up.  I would imagine that means the server is not getting synced on boot up either. I set this box up several weeks ago and I thought it was working. I didn't discover it I guess until I tried a query from my workstation. I also tried it directly on the server. I wonder what else I think is working that actually isn't.:)

---

### Post by Doug S on 2012-06-06
I don't normally run the ntp daemon, and so normally do not even have an /etc/ntp.conf file, which I know that ntpdate will use if it is there.
 
I installed ntp on my other 12.04 test computer. I see the npt.conf file is as you posted (at least I think, I didn't check carefully). Things still seem to work fine for me:```
doug@test-smy:/etc$ ntpdate -q time-a.nist.gov
server 129.6.15.28, stratum 1, offset -2.028687, delay 0.18288
 6 Jun 14:41:19 ntpdate[3056]: step time server 129.6.15.28 offset -2.028687 sec
doug@test-smy:/etc$ ps aux | grep ntp
ntp       3042  0.0  1.1   3856  1380 ?        Ss   14:39   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 110:118
doug      3059  0.0  0.6   4360   780 pts/1    S+   14:45   0:00 grep --color=auto ntp

```Are you comfortable running tcpdump or tshark or similar to observe packet level activity? That is where I would look next, but maybe someone else has a better idea what to do next.

---

### Post by ranger12 on 2012-06-06
Okay Doug, some people should not be around computers - like me. I thought before I initially posted I had turned off the firewalls before I tried ntpdate. I had not, thought I had but apparently not - duh. I did still change some settings in my ntp.conf. I used time servers here in the US and I also put a dns record in my dns zone so I could do address resolution from the command line. It works fine now. Firewalls are great most of the time, but when it comes to configuring things... So chalk this up as solved. I really should be more thorough before I get on here and post. Thanks for at least offering your help.:p

---

### Post by Doug S on 2012-06-06
O.K., glad you got it sorted out.

---

