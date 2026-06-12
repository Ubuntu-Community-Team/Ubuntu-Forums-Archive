---
title: "DRBD/Heartbeat causes reboot"
date: 2007-06-21
forum: Server Platforms
---

### Post by holddigga on 2007-06-21
I am somewhat of a n00b in the linux world so bear with me if I am not going in the right direction here. My problem is this. I have a small cluster of servers with two load balancers, lb1 and lb2. The two load balancers run a number of services and one of these is DRBD. I have installed a second hard drive in each of the two servers and created two partitions of equal size, one for the metadata and one for the actual data. They synced up fine originally and then once I set up heartbeat the servers would reboot randomly. If I shut them both down and bring them up at the same time they sync up and the primary server takes the virtual ip address and also becomes the primray drbd server. After a short period of time one of the two servers will reboot and then the other one will go down as well. Being so new to linux I am not really sure where to look in terms of log files (I know logs are stored in /var/log/...), but I don't really know what I am looking for. Any help would be greatly appreciated.

Thanks!

---

### Post by holddigga on 2007-06-21
After three days of troubleshooting I finally post and then find this...the time is not set correctly on each server, on one the ntpdate is starting and the other is not. How can I fix this?

---

### Post by gabr1el on 2007-06-21
it sounds like you may have a halt suck into your drbd.conf file somewhere.  check out the getting started guide from linux-ha.org: [URL="http://www.linux-ha.org/DRBD/GettingStarted"]http://www.linux-ha.org/DRBD/GettingStarted
[/URL]

notice the line:

>   incon-degr-cmd "echo '!DRBD! pri on incon-degr' | wall ; sleep 60 ; halt -f";

that means that by default any inconsistency in the DRBD device will trigger a halt after 60 seconds.  check for that line in your /etc/drbd.conf.

otherwise, you should probably look into enabling debug logging for both drbd and heartbeat.

---

