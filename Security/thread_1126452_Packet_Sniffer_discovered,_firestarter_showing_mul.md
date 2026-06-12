---
title: "Packet Sniffer discovered, firestarter showing multiple hits/second"
date: 2009-04-15
forum: Security
---

### Post by kafka201 on 2009-04-15
Firestarter started showing multiple hits per second so I ran chkrootkit and it showed the following message:
eth1: PACKET SNIFFER(/sbin/wpa_supplicant[5573], /sbin/dhclient3[6233])
I really don't know much about security so if anyone could tell me what to do now I'd be appreciative.  I'm currently running clamav to see if that shows anything but it may be awhile.

---

### Post by kafka201 on 2009-04-15
To follow up I ran rkhunter and got the following messages:

Warning: Network TCP port 60922 is being used by /usr/bin/python2.5. Possible rootkit: zaRwT.KiT
           Use the 'lsof -i' or 'netstat -an' command to check this.

[13:17:49]   Checking /dev for suspicious file types         [ Warning ]
[13:17:49] Warning: Suspicious file types found in /dev:
[13:17:49]          /dev/shm/pulse-shm-1375403604: data
[13:17:50]          /dev/shm/pulse-shm-1147582508: data

When I ran "lsof -i" it only showed pidgin and firefox in use.
Thanks

---

### Post by iponeverything on 2009-04-15
chkrootkit
and 
rkhunter

report the same things on my machine with the exception of:

```
Warning: Network TCP port h is being used by /usr/bin/python2.5. Possible rootkit: zaRwT.KiT
Use the 'lsof -i' or 'netstat -an' command to check this.

```

I have a fresh install, I am behind two masquerade machines and one PIX firewall, so I highly doubt that the SNIFFER message and pulse files in /dev/shm are of any real concern. 

you may want to investigate, if and why you have a python process listening on 60922 as this is only thing that really raises a red flag with me.

run:

```
telnet localhost 60922

```

did it connect?

check your md5's

```
sudo apt-get install debsums

```

```
sudo debsums > /tmp/debsums
grep -v OK /tmp/debsums
```

---

### Post by jdong on 2009-04-15
Everything's normal. dhclient and wpa_supplicant are supposed to listen promiscuously to network traffic to do their job. Pulse does put SHM cookies which look "abnormal" to a rootkit hunter in /dev/pulse.

No need for alarm.

---

### Post by iponeverything on 2009-04-15
jdong- any idea what his 60922 message is about?

---

### Post by jdong on 2009-04-15
> **iponeverything said:**
> jdong- any idea what his 60922 message is about?


Looks like a random TCP port some app was listening on; not enough info to decide if it's rogue or harmless (i.e. IDLE's internal communicator, some transient app, etc).

Do a sudo netstat -alnp | grep 60922

that should give you a line about what process and its full command line that owns the port.

---

### Post by kafka201 on 2009-04-16
Thanks, I ran that command jdong and got no output, so I ran rkhunter again and this time it didn't show anything.  So this and the firewall aren't related?

---

### Post by jdong on 2009-04-16
> **kafka201 said:**
> Thanks, I ran that command jdong and got no output, so I ran rkhunter again and this time it didn't show anything.  So this and the firewall aren't related?


I wouldn't worry. Applications sometimes use TCP for inter-process communication and transiently open up a random TCP port locally. A lot of our stuff is written in Python, so it's not very indicative of a problem either. rkhunter was only looking at port numbers, not traffic patterns / fingerprints of the service listening, so it could very well be coincidence.


There's nothing else that has been posted that would suggest a rootkit's presence, so that's probably the last thing I would personally suspect.

---

### Post by Vimmander on 2010-08-02
Yeah, I get those two "packet sniffers" from chkrootkit every time I run it with my wireless card turned on.  dchpclient3 had always appeared since I first installed, and it seems that wpa_supplicant appeared after I installed the Broadcom B43 driver for my wireless card.  But as you said, jdong, both are harmless.  I'd like to know, however, if the numbers in square brackets are randomly assigned.

Edit:  I did some playing around, and found that the following happens:
1.)  Turn wireless off, then on => dchpclient3 number only changes
2.)  Reboot => dchpclient2 AND wpa_supplicant numbers BOTH change
3.)  No wireless or ethernet => Nothing shows up
4.)  Ethernet only => dchpclient3 number changes and is the only thing to show up

All but #3 come up as packet sniffers, and in all 4 cases, it says "lo: not promisc and no packet sniffer sockets", but only in 1, 2, and 4 does it say PACKET SNIFFER (~stuff about wpa_supplicant and/or dchpclient3 here~), in addition to "lo: not promisc and no packet sniffer sockets"

Security is always an interesting issue, but it's so easy to be paranoid and take things too far with catastrophization.  Just ask bodhi.zazen,  I'm sure I made him age thirty years before it clicked in my head that Linux was secure by nature.

---

