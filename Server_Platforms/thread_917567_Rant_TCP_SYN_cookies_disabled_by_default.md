---
title: "Rant: TCP SYN cookies disabled by default ???"
date: 2008-09-12
forum: Server Platforms
---

### Post by alecm3 on 2008-09-12
I was lured to migrate from SuSE to Ubuntu server for production servers for my company by a sysadmin that I highly respect.

We installed 2 production servers (the rest are SuSE for now), and suddenly we started getting strange connection problems, with no errors in the application or system logs. The problems were highly intermittent, but amounted to being unable to connect to a port our TCP server was receiving client internet connections on. 

After 3 days of debugging (netfilter, the server application, writing custom bash/awk programs to poll and graph netstat, doing tcpdumps) the problem what traced to random SYN attacks.

It turns out that net.ipv4.tcp_syncookies=1 is commented out in the *server* edition of Ubuntu 8.04!

After all this wasted time (and upset users), my only reaction is "WTF...?" We have many SuSE production servers, starting from 9.0 and they all came with syn cookies enabled. Messages like 

possible SYN flooding on port 80. Sending cookies.

are *very* common in /var/log/messages, anybody who has run a heavily loaded server with many connections has seen tons of them. 

This is the third serious Ubuntu shortcoming I have found in a short time (weird monthly cron job to "check" RAID that overloads a production database once a month, race condition when booting on RAID 1, throwing it into Busybox mode once every 20 reboots) 
I cannot stop wondering if Ubuntu is a toy for Digg users to hate Microsoft and plug their iPhones to the "Linux box", or it's a distribution that can be used for servers?

---

### Post by netztier on 2008-09-12
> **alecm3 said:**
> After 3 days of debugging (netfilter, the server application, writing custom bash/awk programs to poll and graph netstat, doing tcpdumps) the problem what traced to random SYN attacks.


While I'll agree on your reasoning, I'd like to hint that barking up this tree in the forums won't do much, because developers and architects don't tend to hang out here.

Filing a bug report at [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu) might get things rolling in the right direction, i.e. towards the people that will care and might have an answer why the SYN cookies were disabled by default.

In fact, someone's already done so: [https://bugs.launchpad.net/ubuntu/+bug/57091](https://bugs.launchpad.net/ubuntu/+bug/57091)

regards

Marc

---

### Post by alecm3 on 2008-09-12
> **netztier said:**
> I'd like to hint that barking up this tree in the forums won't do much, because developers and architects don't tend to hang out here.


Thanks for the tip, Marc: I am surprized to see the date of that bug: 2006-08-21! 

A developer seems to answer that "use of this option causes the system to violate the TCP standard". I guess SuSE developers understood better that a server-intended Linux distribution is not a computer science exercise, but an operating system that is *actually used* for production servers. But I will bark up that launchpad tree next time, like I did in

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/243434](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/243434)

---

### Post by windependence on 2008-09-12
Alec,

I agree. I have run SuSE and CentOS for a while and what attracted me to Ubuntu was the debian package system and also the community. I am running Ubuntu server on a test box, and there has been a few issues, but there are just a few things that are hard to believe. Example: No ssh installed by default. Not a big one, but on most distros and all the *BSDs I run, this is installed by default unless you specifically tell it not to.

I love the concept of no gui and a bare bones installation that I can customize, but then we have every n00b on the planet trying to install a GUI on the darn thing. I would just love to see Ubuntu get really serious about a real server OS for full production applications. I think that's what they are actually trying for, but we have many in the community who just run it to be "cool". That's fine, but then I hope the developers stay focused on the production side of things and not whether bit torrent will run on it, you know where I'm coming from? </rant off>

-Tim

---

