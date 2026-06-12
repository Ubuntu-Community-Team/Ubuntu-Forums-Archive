---
title: "Staying Connected to the Internet."
date: 2011-12-24
forum: Server Platforms
---

### Post by TripleD on 2011-12-24
_The Problem_
I'm currently working at a university in China. The XP computer in my office was old, slow, and riddled with viruses. I decided to just use my laptop and turn the computer into a linux server that I could leave running to download large files or store temporary documents. 

To connect to the Internet in my office I have to use a piece of intranet software called Dr.Com. Luckily there was a linux version of the client written by a fellow expat at another University. However, the client will only stay connected to the internet for a short while before disconnecting.

_The Setup_

I created an expect script to automate the login of the client:

```

#!/usr/bin/expect
#
# Connect to the internet via the Dr.Com Client
#

spawn "/home/tripled/drlinuxclient2.6.bin"

expect "Please enter account: " { send USERNAME }
expect "Please enter password:" { send PASSWORD }

interact

```

To stay connected to the internet, I created the following shell script. It kills whatever Dr.Com program may currently be running and creates a new one. It uses Dtach to make the program run in the background.

```

#!/bin/sh
#
# Renews the current Internet Connection
#

pkill connectToInternet
pkill drlinuxclient
pkill drcomauthsvr

#You need to wait a few seconds to make sure the old dtach lock file is deleted
sleep 3

dtach -n /tmp/drcom.dtach /home/tripled/connectToInternet

```

I then scheduled a Cron job to run the script every thirty minutes.

```

$ sudo crontab -e

*/30 * * * * /home/triple/renewInternet.sh

```

_The Result_
I walked in to work the next day only to find the computer wasn't connect to the internet. I tried running "renewInternet.sh" manually and, sure enough, the connection sprang into existence. I checked "/var/log/syslog" to see what it is saying:

```

Dec 24 08:30:01 MyComputer CRON[6180]: (root) CMD (/home/tripled/renewInternet.sh)
Dec 24 09:00:00 MyComputer CRON[6175]: (root) CMD (/home/tripled/renewInternet.sh)
...and so on

```

I am really baffled here. I know that my scripts work, and I know that CRON is running them as root. I've tried troubleshooting what could be causing this (computer going to sleep, connection lasting less than fifteen minutes, etc.) but none of these seem to be the problem.

There is one small thing. Every three hours or so, this appears in my system log:
```

Dec 24 08:38:11 MyComputer dhclinet: DHCPREQUEST of 1.185.27.9 on eth0 to 210.36.16.86 port 67
Dec 24 08:38:11 MyComputer dhclinet: DHCPACK of 1.185.27.9 from 210.36.16.86
Dec 24 08:38:11 MyComputer dhclinet: can't create /var/lib/dhcp3/dhclient.eth0.leases: No such file or directory
Dec 24 08:38:11 MyComputer dhclinet: bound to 1.185.27.9 -- renewal in 13645 seconds.

```

210.36.16.86 is the IP of the server that Dr.Com connects to. I think this is related, but I can't think of how. Any insight into how to keep my computer internet-ready would be much appreciated.

---

### Post by lensman3 on 2011-12-24
Try something like the following in a cron.  This is for an ethernet connection that keeps going down and trys to fix the connection. The ifdown and ifup are scripts that kill the old connection and then restart the connection.  The xxx.xxx.xxx.x is your nearest dns server or default gateway.  if ifdown is replace with a ppp-done or a ifup with ppp-on scripted it should work.

I have used the below code for years and it has worked very well.  The only problem I had with it was my ISP crashed bad and every minute a new job was spawned.  Eventually, I ran out of processes ID's and my system crashed!

The following is called "keepalive.sh" and resides in /usr/bin

```

#!/bin/sh

ETH1=eth1

if [ -f /var/run/dhclient-$ETH1.pid ] ; then

 ping -c4 -l3 xxx.xxx.xxx.x  2>&1 | grep "0 received" > /dev/null && \
  { /sbin/ifdown $ETH1 > /dev/null; sleep 2; /sbin/ifup $ETH1; }
else
  /sbin/ifdown $ETH1;
  sleep 2;
  /sbin/ifup $ETH1;
fi

```

---

### Post by TripleD on 2011-12-26
Many thanks for the reply. I took your script an modified it as follows:

```

#!/bin/sh
#
# Checks for internet connectivity. If none exits renew.
#

ETH0=eth0

if [ -f /var/run/dhclient.$ETH0.pid ]
then
   ping -c4 -l3 www.google.com 2>&1 | grep "0 received" > /dev/null && \
      /home/tripled/renewInternet.sh
else
   /home/tripled/renewInternet.sh
fi

```

I chose "www.google.com" because I actually can ping my local DNS server even if the Dr.Com client isn't running. I figure that the odds of google going down in the near future are pretty low, so it's as good a choice as any. As for the other changes, I must confess to being a beginner at scripting, so I simplified things until I could get it to run successfully.

I scheduled cron to run this every minute, and at first it looked like it was working. But then I ran into the same problem as before. Cron would run keepalive.sh (successfully, according to "/var/log/syslog") but I would not be connected to the internet. If I run the exact same script manually, I'm connected.

I might play around tomorrow and see if dtach could be the problem.

---

