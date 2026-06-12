---
title: "Zentyal removal, configuration remains"
date: 2013-03-26
forum: Server Platforms
---

### Post by Kieron on 2013-03-26
So I installed Zentyal on my ubuntu headless server (12) and didn't like it, so proceeded to --purge it with aptitude.

It has since completely wrecked everything. My networking is completely reconfigured, LDAP errors, DNS is pointing to localhost.. a whole host of problems basically.

ifconfig -a shows my network is configured fine using DHCP. I have tried autoremove, autoclean, and any other apt-get commands I can think of.

Am I going to have to go through manually to reconfigure my entire system, removing all the things it has left over by hand? I really am disappointed in Zentyal, I've installed and uninstalled plenty of packages over the 6 years this server has been running with no problems at all.

Hope someone can help me get this resolved. Thanks!

---

### Post by WhaleVPS on 2013-03-26
For LDAP the server shouldn't be configured via DHCP in the first place, it should have a static IP. It may work I'm not 100% sure but its probably better to give it a static IP.  What do you mean DNS points to localhost? It should point to localhost. When you install LDAP you need a number of A, CNAME, SRV and other records within DNS for LDAP to work. 

You should be able to uninstall it via apt-get purge <package>

I'm sorry but it sounds like you may need to do a bit more reading up on the product before installing it next.

---

### Post by LHammonds on 2013-03-28
Actually, the best thing is to make a backup of your system BEFORE you make any major changes so you can easily go back to the way it was before the change.

If your partitions are all LVM, you can do LVM snapshots.  If you are running inside a Virtual Machine, you can also make snapshots at the machine level.

If no LVM or virtual, you can use fsarchiver to make backups of your partitions.

When testing software, I always recommend doing it in a temporary virtual machine 1st that you can simply delete if it doesn't work out.  I use VirtualBox on my PC.  When at work, I use VMware and simply create a new virtual machine.  It only takes about 15 minutes to get an Ubuntu Server 12.04 installation up and running.  But I always have a generic server ready to use which retains a permanent snapshot to a "clean" state so I can easily test stuff and quickly revert back to a pristine installation.

Check my sig for details on how I configure partitions, use LVM and backup/restore using fsarchiver.

LHammonds

---

