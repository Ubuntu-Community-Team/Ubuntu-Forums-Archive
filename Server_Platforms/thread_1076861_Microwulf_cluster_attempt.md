---
title: "Microwulf cluster attempt"
date: 2009-02-21
forum: Server Platforms
---

### Post by RexAtHighSpeed on 2009-02-21
I'm a casual linux user trying to set up my first linux cluster using  kubuntu on the head and ubuntu server on the compute nodes by following this guide... [http://www.calvin.edu/~adams/research/microwulf/sys/microwulf_notes.pdf]("http://www.calvin.edu/~adams/research/microwulf/sys/microwulf_notes.pdf")

I've got the head configured and one node that I'm trying to connect to the head. I've had various stages of success but none end with diskless node booting from pxe image. I need some basic troubleshooting help here.

First things first. I'm using dhcp3-server on the head. How can I make sure that it is configured properly? NetworkManager reports that eth0 is 'unmanaged'. Why is this? I've edited so many files I don't know where I'm at now! :|

Please help! Thanks~

---

### Post by RexAtHighSpeed on 2009-02-23
No one can help with dhcp3-server??

---

### Post by koenn on 2009-02-23
if your dhcp server starts without errors and doesnt write any complaints in /var/log/syslog, you can rest assured it's working and configured properly; it makes noise when the config file is not correct.

And when you've edited so many files that you don't know where you are, you've reached the point where you start all over again, and this time take notes.

---

### Post by RexAtHighSpeed on 2009-02-24
Ouch that hurt! but its the truth. It's one of those things where this next thing will do the trick... that didn't work... this NEXT thing will fix it... etc. etc. etc. Hours later I realize I'm lost.

I've figured out the problem with dhcp. Now it assigns an IP to the node and stops at the tftp portion. It times out. How can I find out where I've gone wrong with the tftp setup? I've read a few howtos online but I did not learn how to troubleshoot my situation.

---

### Post by koenn on 2009-02-24
oh, so that's a network boot ? (I'm not familiar with the inner workings of clusters). You're using PXE ?

In any case; reboot the node, then look at the end of /var/log/syslog of your dhcp / ftp server. Look for lines that say your dhcpd gave a lease to the node. In the next lines, your tftpd should report receiving a request for this or that file, and then a line saying that it's serving that file (or why it doesn't). So, based on what you find in syslog, you can figure out where tftp goes bad.

---

