---
title: "Ubuntu Openvz SSH problem"
date: 2009-03-24
forum: Virtualisation
---

### Post by derickcyril on 2009-03-24
Hi,

My vps is using ubuntu 8.04-minimal image. Evrything works fine until I restart the vps. If I restart the vps, I can not ssh back. It gives a connection refused error message.

The version is:
```
alpha:~# uname -a
Linux alpha.localnet.net 2.6.9-023stab032.1-enterprise #1 SMP Fri Oct 20 03:13:34 MSD 2006 i686 GNU/Linux
alpha:~#
```

Also, I get following error when using apt-get:
```
dpkg: cannot scan updates directory `/var/lib/dpkg/updates/': Unknown error 530	 
```

---

### Post by bodhi.zazen on 2009-03-24
Where did you get the machine from ? did you make it yourself or download it ? If you downloaded it, from where ?

Was the guest ever working normally ? Can you enter it with vzctl ?

---

### Post by derickcyril on 2009-03-25
My VPS provider installed the image. Whenever I restart the VPS, it becomes unaccessible. I have found out that this is because ssh is not starting at boot time.

Now my VPS provider is asking me to use CentOS, which I am not confortable with. I think the kernel 2.6.9 is a bit outdated and may be causing problems.

---

### Post by BkkBonanza on 2009-03-26
I doubt if this is related to kernel version.
Have you tried to see why ssh isn't starting?

There should be a link in /etc/rc3.d along the lines of S16ssh -> ../init.d/ssh

If there isn't then somehow it got disabled. If the server has a control panel then go there to make sure it's enabled. If not then you can do it from the console.

update-rc.d sshd defaults 16 84

And then check that it put the link in for you. The numbers may be a bit different but these are what they are for mine. 

If you do,

ps afx

then you should see /usr/bin/sshd on one line. If not then start the service with,

/etc/init.d/ssh start

---

### Post by derickcyril on 2009-03-26
I think it was related to the permission of the user sshd. I installed another image and is working fine.

---

### Post by byrnef87 on 2010-10-18
Hi,

Sorry to re-open the thread, but I have a pretty similar problem and I wanted to know how you solved it.

More info:
I have a Jumba Vegetarian VPS with Ubuntu 9.10 installed. I've followed this link to upgrade from 9.10 to 10.04 (so that I can use the Virtualmin GPL install script, and because 9.10 isn't even an LTS release!). [https://help.ubuntu.com/community/LucidUpgrades]("https://help.ubuntu.com/community/LucidUpgrades")

However, after I upgrade it requests to reboot, so I restart the container and ssh no longer works. I discovered from the Parallels Power Panel that the sshd process is not initializing, hence why I can't login. I found that the links to /etc/init.d/ssh had been removed from /etc/rc2.d/S16ssh, /etc/rc3.d/S16ssh and so on. So I ran update-rc.d ssh start 16 2 3 4 5 . stop 84 1 . (I also tried stop for 0 1 6), however when I do that and restart the container, only the init process loads up (ie. even fewer processes load up!).

The only error I can find relating to this in any of my log files is in the syslog, which is something along the lines:
"Failed to spawn rc main process: unable to open console: Permission denied"
Before I ran the update-rc.d command, it was:
"job_process.c:483: Unhandled error from job_process_spawn
Failed to spawn ssh pre-start process: unable to set oom adjustment: Operation not permitted"

I've tried googling these errors, but nothing has helped. I'm at a total loss!

Thanks,

Francis

---

### Post by byrnef87 on 2010-10-19
Hey I fixed it.

I followed the instructions in this link:
[https://secure.intovps.com/knowledgebase/16/How-to-Upgrade-from-Ubuntu-910-to-Ubuntu-1004-LTS.html]("https://secure.intovps.com/knowledgebase/16/How-to-Upgrade-from-Ubuntu-910-to-Ubuntu-1004-LTS.html")

Turns out oom and rc were launching a console that wasn't allowed by the container. Restarted the container after commenting out the lines specified in that link (I didn't do the first part, editing /etc/init/openvz.conf) and it worked!

---

