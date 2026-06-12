---
title: "Test your LAN speed. Are you getting right speed?"
date: 2014-09-21
forum: Ubuntu, Linux and OS Chat
---

### Post by thejar2 on 2014-09-21
I think there may be a popular bug that has gone unnoticed, which reduces LAN speeds in 100/1000mbps environment to 10mbps.

Please check your network Ubuntu to Ubuntu speed.

possibly related to bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1275161](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1275161)  
and even possibly related to bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1264707?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1264707?comments=all)
and finally here: [http://www.reddit.com/r/Ubuntu/comments/23zudj/why_is_ubuntu_networking_so_slow385mbps/](http://www.reddit.com/r/Ubuntu/comments/23zudj/why_is_ubuntu_networking_so_slow385mbps/) 

What LAN speed are you getting?

**Ways to test**


_Method 1 netcat:_
on first computer run # nc -l 1122

on second computer run
# dd if=/dev/zero bs=19004096 count=1 | nc LAN_IP_OF_FIRST_COMPUTER 1122

19mb Test.



[U]Method 2 iperf:
[/U]
On 1st listening computer

# apt-get install iperf
# iperf -s

On 2nd Sending computer
# apt-get install iperf
# iperf -c LAN_IP_OF_FIRST_COMPUTER

---

### Post by thejar2 on 2014-09-24
nano tested/posted, 
meanwhile I checked in another office/ completly different lan, same problem on many systems, but yet some systems remain immune to this bug.


I think many ubuntu users mayb be effected by this.

It would be some nice to see what speeds you guys  are getting.

Just takes 2 ubuntu boxes and 2 minutes of time especially if you got vnc setup :)

:P

also, so many posts all over about network related stuff being slow, such as Remote Desktop Sharing being noticably slower - could have been
caused by this bug.

---

### Post by Habitual on 2014-09-25
YALT (Yet Another LAN Test)
```
wget -O - https://raw.github.com/sivel/speedtest-cli/master/speedtest_cli.py | python
``` ;)

---

