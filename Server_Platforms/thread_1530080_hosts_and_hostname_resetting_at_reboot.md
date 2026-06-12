---
title: "hosts and hostname resetting at reboot"
date: 2010-07-13
forum: Server Platforms
---

### Post by bsodmike on 2010-07-13
Hi,

I'm facing bit of a conundrum with my new server. It is essentially a distributed-virtual Plesk Virtuoso container with a rather simple LAMP setup (PHP5 etc) and virtual hosting.  Running 10.04 LTS.

The issue is that on each reboot, the /etc/hosts and /etc/hostname files are reset with their original configs causing the virtual hosting to break, i.e. rather than hosting the vhosts correctly, it essentially routes all traffic to /var/www, or essentially 000-default ~ this beats the whole point of vhosting in the first place!

Is there any way to get around them being overwritten at boot?

A very crude workaround would be to set a script to load at boot via init.d and have it rewrite both files to their correct configs - of course, I have no idea as to the point during boot at which they get replaced.

Thanks, Mike.

---

### Post by terazen on 2010-07-14
Do any other files not retain changes after a reboot?  Is this a virtual machine?

---

### Post by kevinthecomputerguy on 2010-07-15
Do you have dhcp3-server installed? If so, fastest way to see if its that, remove it, and reboot twice, and see if your settings stick. (apt-get remove dhcp3-server) If so then the problem is in the dhcp3-server config. /etc/dhcp3/dhclient.conf
You can edit the line(s) that say supersede
# supersede domain-name "diy.lan";
# supersede domain-name-servers 127.0.0.1;
There is another line for the hostname too, it think its called #send hostname
But removing the dhcp server might quickly put you on the right track if thats it.
-Kev

---

