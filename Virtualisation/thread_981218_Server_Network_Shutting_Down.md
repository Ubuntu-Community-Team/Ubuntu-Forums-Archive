---
title: "Server Network Shutting Down"
date: 2008-11-13
forum: Virtualisation
---

### Post by dweimer on 2008-11-13
I finnally had time to get back to an old project started in September, I ran into a problem then, and was hoping an upgrade to Ubuntu Server 8.04LTS would fix my problem but it didn't.

Here was the old thread:
[http://ubuntuforums.org/showthread.php?t=933299]("http://ubuntuforums.org/showthread.php?t=933299")

Basically I have an install of the x64 bit server running in VMware ESX 3.5U2 the only changes from the base install is the addition of the build-essentials package, and manually compiled squid.  Everything works fine, except that when the server sits idle, its shutting down the network interfaces.  You then have to log into the console and access the network before the server is reachable.
Its only in a test server at this point, in production it may never see enough idle time for this to happen.  However I can't in good faith put something with a known problem of this nature into production.  The ESX servers are running with the high availability and vmotion features enable, connected through multiple NICs using port channel to a redundant Cisco switch stack.  With the storage on an ISCSi SAN that has redundant modules and redundant NICs in each module.  What good is all this redundancy if simple Idle time breaks the service.
I can't seem to find any power settings to adjust everything I see while searching wants to use gnome or kde's built in utilities to manage power savings.  Of course the server install doesn't have these.
It was suggested when I last posted this problem that it could be a VMware issue.  If it is, it is only with Ubuntu guests, as we have Windows server 2000, 2003, and 2008, RedHat Enterprise Linux 4 and 5, Solaris, and even FreeBSD installed on this group of ESX servers.  Almost 30 running VMs in all and none of them besides the Ubuntu install has this problem.
Does anyone have any ideas before I break down and try to convince management to let me buy more licenses of Redhat.

---

### Post by dmizer on 2008-11-14
I would highly suggest taking this one up with VMware. It could be a number of things related to how the host software interacts with the guest, and you're more likely to get a good answer from them. One of my Windows guests used to die like that too, but I never followed up on it.

Just in case someone here has a better idea, I've moved this thread to the virtualization section.

---

### Post by PilotJLR on 2008-11-15
Does this happen with or without Tools installed?

When the guest network goes down, does dmesg or /var/log/messages contain anything useful?

---

### Post by PilotJLR on 2008-11-15
Also, how long does the guest need to be idle before this happens?

To see if I can reproduce this, about 4 hours ago, I made a new 8.04.1 32bit guest on an ESX 3.5 U3 host... I updated everything on the guest, and it's running ONLY openssh-server on top of the normal server base. With Tools compiled and running, I can still ping the guest.
I will try again in the morning and see if it will respond without any intervention.

---

### Post by dweimer on 2008-11-25
Sorry for the late reply, I haven't been checking this thread often while waiting on VMware to respond to my query for support.  I have requested it as a low priority since this project is not in production yet, and is waiting behind a few other projects that are a higher priority.  Just get to do a little here and there while waiting on answers for the other projects.
It happens both with and without the tools installed, not sure of an exact amount of time, but it definitely happens when sitting overnight.  I haven't tried the 32bit version so if you didn't run into the problem it might only be with the 64bit version.

---

### Post by dweimer on 2008-11-26
Interesting, I just noticed today that I can ping and trace route to it just fine, however ssh rejects attempts to connect, and so does the squid proxy service.  Currently the only things running on the server.  Its possible that when it didn't answer to SSH and the Proxy connections that I just assumed none of the networking was working.  The logs on the Ubuntu virtual server nor on VMware ESX server show anything that is indicating anything occurred.  No errors, warnings, or even informational messages, at the time the network is reestablished, and there are no events indicating the time that the problem begins to occur.

---

