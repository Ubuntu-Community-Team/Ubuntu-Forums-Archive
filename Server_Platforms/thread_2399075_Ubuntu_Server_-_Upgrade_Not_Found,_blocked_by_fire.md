---
title: "Ubuntu Server - Upgrade Not Found, blocked by firewall"
date: 2018-08-21
forum: Server Platforms
---

### Post by wgibson84 on 2018-08-21
Hi there,

Am currently looking through the forums but trying to come up with the correct search phase is proving troublesome. 

In short i have a couple of Ubuntu Servers running 12.04 that im trying to upgrade, when searching for updates its just coming back saying none can be found.

I've tried to steer the servers towards our proxy to get the updates through but the server doesn't seem to be using the settings

(i've tried both the /etc/apt/apt.conf and /etc/environment to no avail).

Looking at it from a different angle im trying to see what IP ranges to get unblocked on our firewall to allow the server to talk to the Ubuntu update server. I've found a number of URLs required which i've unblocked but looks like im setting a few hits to [www.ubuntu.com](www.ubuntu.com), this appears to be behind a couple of different IPs  If there a 'complete' list of IP's needed to unblock to allow these updates? 

For [www.ubuntu.com](www.ubuntu.com) specifically i've found 91.189.91.139, 91.189.94.174 and 91.189.95.3 via an NSLookup, but pinging it returns 91.189.90.59.  

Im happy to get these added (even the Class C's) but dont want to find that next week i get different addresses. 


So i either need to get an idea on the IP ranges or work out how to get Ubuntu to use the proxy server for upgrades. 

Thanks in advance, Wayne

---

### Post by slickymaster on 2018-08-21
Thread moved to **Server Platforms** for a better fit

---

### Post by SeijiSensei on 2018-08-21
12.04 reached its [ end of life](https://www.ubuntu.com/about/release-cycle) in April, 2017. I don't believe there are updates for it any more.  You need to consider installing 18.04.

---

### Post by wgibson84 on 2018-08-21
> **SeijiSensei said:**
> 12.04 reached its [ end of life]("https://www.ubuntu.com/about/release-cycle") in April, 2017. I don't believe there are updates for it any more.  You need to consider installing 18.04.

Thats the plan to jump to 16.04/18.04, currently been trying the command 'sudo do-release-upgrade' Is this correct to jump versions?

---

### Post by wgibson84 on 2018-08-21
Might have found the issue,  looks like its struggling to resolve the proxy by name so keyed in its IP. Looks more promising. Will see how things go from here :)

---

### Post by SeijiSensei on 2018-08-21
From what I hear upgrading from 12.04 to 18.04 is not that easy. Many things are different now like the replacement of SysV init scripts with systemd, the use of netplan to configure networking, etc.  I suspect you'll still need to reinstall the full OS.

---

### Post by wgibson84 on 2018-08-21
Lovely,  sounds like there is some fun and games ahead for me on this one.  Only 4 servers to do in the same state! :S

---

### Post by LHammonds on 2018-08-21
I would recommend installing 18.04 in a virtual machine and figure out how you need to configure it as a replacement for your 12.04 server.  As SeijiSensei said, many things have changed in the OS and applications since 12.04.   Once you have documented exactly what you need to do on an 18.04 server to get it running like 12.04, you can then repeat the steps on the real server.  Here is the general procedure I would follow:


[LIST=1]
[*]Backup your 12.04 server and make sure your backup is good.
[*]Create 18.04 vm using VirtualBox or whatever and get a baseline 18.04 server running.
[*]Create a snapshot of the baseline 18.04 server
[*]Install the application(s) you need to match the 12.04 server
[*]Figure out the various configuration settings needed on the new software (most-likely CANNOT and SHOULD NOT just copy the 12.04 configs directly)
[*]Migrate the data from 12.04 and verify that all the services and data work just like the 12.04 server.
[*]Keep the 18.04 vm handy
[*]Backup your 12.04 server again (maybe even migrate the data again to the VM to refresh it)
[*]Remove all partitions on the 12.04 server and install 18.04
[*]Follow the steps you documented when setting up the vm to get 18.04 and the various applications installed.
[*]Having the 18.04 vm available, you could just copy the config files from it and migrate the data back from it to the physical server (if the data was the most-recent copy before shutting down 12.04).
[/LIST]

In my signature below, I have a link to how I install Ubuntu Server 18.04 which might help you with the changes since 12.04 if that is what you are familiar with.

LHammonds

---

### Post by wgibson84 on 2018-08-22
Thanks guys, i'll do some reading up and get some clones ready for test migrations.  Cheers

---

