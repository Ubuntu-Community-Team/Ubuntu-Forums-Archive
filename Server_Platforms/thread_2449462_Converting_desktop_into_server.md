---
title: "Converting desktop into server"
date: 2020-08-27
forum: Server Platforms
---

### Post by weirdygeekpsych on 2020-08-27
I am thinking to convert my 5 year old desktop as server with 1TB Internal SSD SATA which has 6GB/s. My mother board [Asus H81MC]("http://www.asus.com/Motherboards/H81MC/") has the hard drive capacity limit up-to 6 GB/s.Will it be more enough if I add 1TB Internal SSD beucase I am about to install Ubuntu Server on itPlease Guide me...Thanks

---

### Post by QIII on 2020-08-27
Hello!

What do you intend this server's purpose to be?

---

### Post by ameinild on 2020-08-27
I'm running an Ubuntu server with a 500 GB NVMe disk, which I use for various stuff like DNS, Unifi Network, Docker etc. This is more than enough if you don't require handling large amounts of data.

My standard installation, with swapfile and 4 GB of docker containers and data consume less then 5% disk space. Under most circumstances I'd say any desktop is perfectly capable of being turned into a server.

---

### Post by SeijiSensei on 2020-08-27
You don't need to "convert" a desktop into a server. Just install the packages you need and off you go. As QIII says, what do intend this server's purpose to be? A web server? DNS? File sharing? A database server?

---

### Post by LHammonds on 2020-08-27
> **weirdygeekpsych said:**
> I am thinking to convert my 5 year old desktop as server

> **weirdygeekpsych said:**
> Please Guide me.
Hard to guide when you did not specify anything other than "server."

Here is [my guide]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=273") on how to setup a production server that is ready to be deployed in just about any role.  The server has no desktop GUI and most all interaction with it will be through a telnet application (like PuTTY) via SSH and command-line.  Life on a server console will be much better if you are familiar with a text editor.  I use VI (or VIM) which is old-school but very quick-n-efficient once you get used to it.  Others prefer text editors such as nano.  It will be up to you what you use but I'd recommend spending some time learning how to be proficient with whatever you choose.

You might want to consider turning this physical box into a virtual environment host...so you can create multiple, separate servers and utilize the hardware much more efficiently.

If it were me, I would [install Proxmox]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=276") and then upload the ubuntu server ISO image to an ISO container.  Then create a virtual machine and attach the ISO image to it and install Ubuntu Server that way.  You could then deploy as many separate virtual machines as your host server could handle.

Just some ideas to contemplate while you think of what kind(s) of services you want. ;-)

> **SeijiSensei said:**
> You don't need to "convert" a desktop into a server.I think what he means is that he is going to re-install that machine which was previously used as a desktop (OS was not specified and probably irrelevant if set on installing Ubuntu Server).

LHammonds

---

### Post by SeijiSensei on 2020-08-27
> **LHammonds said:**
> I think what he means is that he is going to re-install that machine which was previously used as a desktop (OS was not specified and probably irrelevant if set on installing Ubuntu Server).
If it's just to handle a couple of services like Samba, I really don't see the need for a full re-installation. Plus we have no idea about his or her skills at the keyboard. Being thrown into a text-only world can be pretty disconcerting unless you're experienced.

---

### Post by TheFu on 2020-08-27
SATA-3 is 6 Gbps, not 6 GBps.  There is a 8x difference.  Correct units are important.


Fast NMVe SSDs in a fast PCIe gen4 m.2 slot could get to 32 Gbps.

For home users, 100 Mbps is almost always sufficient throughput, so I wouldn't worry.  It isn't like the system is an enterprise DB server with 10,000 TPS workloads.

If you say what this server needs to support AND post a more complete overview of the hardware, you'll get better answers.  For the overview, **inxi -Fxxz** output would be good.  Really, for most home server needs, a raspberry pi v2 with a USB2 external HDD is sufficient for everything, except as a backup server.

---

### Post by ameinild on 2020-09-14
> **LHammonds said:**
> 
Here is [my guide]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=273") on how to setup a production server that is ready to be deployed in just about any role. 



@LHammonds can I ask you something? In your server guide, you define 5 logical volumes. Why do you think this is necessary - and supplementary, is disk space really an issue anymore? Isn't this making things overly difficult to manage, compared to just having a single larger volume for everything? I don't really understand what the benefits are, care to elaborate? Thanks ;)

---

### Post by LHammonds on 2020-09-14
> **ameinild said:**
> @LHammonds can I ask you something? In your server guide, you define 5 logical volumes. Why do you think this is necessary - and supplementary, is disk space really an issue anymore? Isn't this making things overly difficult to manage, compared to just having a single larger volume for everything? I don't really understand what the benefits are, care to elaborate? Thanks ;)
I have been burned every time I setup a server in atomic configuration (everything in 1 partition).  Stuff gets bad when the OS cannot write to the root partition.  Most things that tend to grow are not OS-related...they are application-related.  Specifically log files under the /var can go wild if you enable some services to debug in verbose mode and forget to turn it off...or a database script gets stuck in an infinite loop doing an operation and chews up disk space like its going out of style (happened 3 weeks ago and was called a once-in-a-blue-moon event).

By breaking off partitions that "might" go wildly out of control such as /home, /var and /opt, you can limit the effect of a service/script that goes haywire and causes the system to fill up.  If your MariaDB databases are located in /opt and /opt is its own partition, the filling up of /opt will NOT cause the system to become unresponsive.  Sure, the database service will like fail but you will be able to SSH into the console and diagnose/fix what is wrong.  You are not guaranteed that you can even SSH into the system if the root partition becomes full.  The entire OS will become unstable and if you are NOT physically near that system with console access, you might be looking for another job before it is all said and done.

Of course, I am speaking from a professional standpoint where it is your JOB, not a hobby.  If this is a personal website and you sit at that server several times a week, you probably won't have an issue or can spot the issue by seeing that particular server on a regular basis.  I have been able to manage over 100 servers by myself.  The servers themselves (or my Nagios monitor) will email/txt me BEFORE things start going south.

If I am good at my job, NOBODY knows my name and my company wonders why they pay me.  This is my goal...and I have found that an atomic partition design will NOT allow me to attain that goal.  If a service starts to go down, I need immediate access to resolve it quickly...and isolated partitioning aids greatly in this goal.

I also manage Windows servers and use a similar design.  OS is on C:, Apps and TEMP are on D:, data is on E: and above.  Over time, space on C: will not get change except for updates to the OS itself.  D: will not change much either unless something out of control writes to the TEMP folder.  We only have to worry about space consumption and growth on E: and if E: gets full, it will not affect our ability to connect to the server and manage the volumes.

LHammonds

---

### Post by ameinild on 2020-09-15
Thanks for the clarification. I totally understand how this makes sense in a professional production setup - and I also get that you agree with me for a personal hobby server, it probably isn't going to be an issue. 
I guess every setup has its place, and my point was also the one that you touched upon: Often you'll be able to spot the problems before things go south, if you setup sufficient monitoring (for instance of abnormal logfile growth). 
Still, it's good to be aware of pros and cons of the different setups.
Cheers mate! :cool:

---

### Post by TheFu on 2020-09-15
There are times when daily monitoring of logs isn't sufficient.

I've had log files explode to use 15G in less than 1 hour.

---

### Post by ameinild on 2020-09-15
> **TheFu said:**
> I've had log files explode to use 15G in less than 1 hour.

That's pretty insane ! :eek:

---

### Post by mastablasta on 2020-09-16
> **ameinild said:**
> That's pretty insane ! :eek:

and that's nothing. error in Steam caused error log to fill up the home folder that is 950 GB in size (ok about 600 GB is still free) in 5 hours. so that's over 100 GB per hour. and no one noticed until it home was full as we didn't touch the PC. busy machine, interesting bug.

EDIT: since i had separate home, the solution was simple as boot was still possible (root was not affected). all i had to do was locate and remove the offending file.

on a personal or hobby server this is not much of an issue indeed. however it is easier to recover if you have /home and /var/log on separate partition.. but still on home server you can always boot live, delete the files and reboot or reinstall. any down time due to errors probably doesn't matter so much there.

---

### Post by ameinild on 2020-09-24
> **LHammonds said:**
> Specifically log files under the /var can go  wild if you enable some services to debug in verbose mode and forget to  turn it off...

> **TheFu said:**
> I've had log files explode to use 15G in less than 1 hour.

Related question: Wouldn't it be possibly to also control the size of logs with filesystem quotas, as described in this article?

[https://www.digitalocean.com/community/tutorials/how-to-set-filesystem-quotas-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-set-filesystem-quotas-on-ubuntu-18-04)

The folder /var/log is owned by the group "syslog". If you set a quota for this group with a hard limit of 2 GB or something, wouldn't this have a similar effect?

I know this is only for logs, but maybe it could be used in a less critical setup, where you want to limit the sudden growth of logfiles, and still would prefer a simpler partition setup.

Combined with the root reserved space in tune2fs, I believe this would be a rather good option - haven't tested it though.

---

### Post by LHammonds on 2020-09-24
> **ameinild said:**
> Related question: Wouldn't it be possibly to  also control the size of logs with filesystem quotas
Possible?  Yes.

> **ameinild said:**
> The folder /var/log is owned by the group  "syslog". If you set a quota for this group with a hard limit of 2 GB or  something, wouldn't this have a similar effect?Good  question...I don't know for 100% certainty.  There are files in /var/log  that belong to root:root, root:adm, root:utmp, syslog:adm,  landscape:landscape, root:systemd-journel.  I would imagine quotas only  apply to files associated to that user or group.  I doubt it considers  the owner of root:root for "/" and assumes everything on the disk is  assigned to root:root just because it is the top-level user/group.

Quotas are defined in 3 ways: Users, Groups or FileSystems.

If you have a single, atomic partition scheme and you place a limit on a  User, that limit applies to everything on that system, it cannot be  confined to just /home or whatnot.  Same for Groups.  FileSystems aspect  seems completely useless unless you have multiple partitions which  would then allow you to have different limitations based on partition.   But if you are using separate partitions, you are splitting hairs at  this point and possibly introducing complexity and overhead that is not  needed.

You also need to run quota checks to make sure it does not get "outta whack" such as after an unexpected reboot, etc.

Even if you are mainly just combating logs, you cannot expect to see all  logs in /var/log.  Applications can put logs elsewhere such as in /opt  or /home or /var/lib (such as MySQL/MariaDB binary or general logs).   You might get all the log-using scenarios today but a year from now, if  you install a new application and forget about the quota setup, you can  experience a "gotcha" moment that bypasses all your hard work with a log  file outside your quota setup.

To me, using quotas add more complexity than isolating the root  partition from others via partitions...partitioning requires less  overhead in performance, maintenance and gotcha cases.

There certainly are scenarios where quotas are extremely helpful such as  multi-user systems (ISP FTP/Web/DB, File Server, etc.), but for general  purpose, I prefer the set-n-forget method of partitioning.  Every  server I deploy uses multiple partitions.  If I ever need to utilize  quotas for a specific scenario, I still would not revert to a single,  atomic partition.

LHammonds

---

### Post by ameinild on 2020-09-24
Thanks for the thoughts! :-k

---

### Post by TheFu on 2020-09-24
Log file size can be managed by logrotate.  This is built-into all Ubuntu releases and many other distros.  Check out /etc/logrotate for example configuration files.  Additionally, journalctl has a method to limit log file sizes.   /etc/systemd/journald.conf is the config file for that.  

I wouldn't use quotas for OS limitations, only for end users, who actually would take action to clean up their cruft.  Quotas on the OS would just hide a big issue from the admin, who needs to address the problem.  When /var/log fills up and refuses to accept any more data, I think the system would crash. It certainly will become very slow.

---

### Post by ameinild on 2020-09-25
> **TheFu said:**
> Additionally, journalctl has a method to limit log  file sizes.   /etc/systemd/journald.conf is the config file for  that.

So here you're actually saying that journalctl is much more well thought through than "standard" Linux journalling, since you can actually limit the amount of log spam in an intelligent way, whereas "default" Linux config can crash an entire system by log spamming, if not devising a clever partitioning scheme, or maybe quotas? This is interesting.
> **TheFu said:**
> When /var/log fills up and refuses to accept any more data, I think the system would crash. It certainly will become very slow.

But isn't this the same when the log partition is only 2 GB and suddenly fills up? I'm trying to compare the effects of the 2 different scenarios to manage log file size.

I actually find it quite baffling that apparently the default log system  in Linux is so fragile that it can't easily be configured to limit the  size of logs, and that you have to go through hops and loops to devise a  method to limit a system crash. IMO it would be better to design the  system so you would never be in a case where the logs fill your entire  disk, which I think everybody can agree is a bad situation, that could  rather easily be prevented (for instance by never allowing logs to  consume more than a fixed amount of the free space).

---

### Post by TheFu on 2020-09-25
logrotate has worked for 20-40 yrs, limiting the size of log files.  Misconfiguration is the most common issue.

There is no a central "Linux team" somewhere deciding things. Different Linux distros have different methods of controlling log file growth and limits.  I prefer the logrotate method, but that is mainly because I've used it for decades and it works for logs that are actually managed through it.  

If a 3rd party program doesn't tell logrotate about the log files it uses, I can't blame it for not managing size limits.  The same would apply to journalctl. If it doesn't know about a log file, it can't monitor and limit file sizes.  Even when I've setup journalctl to limit file sizes, it hasn't followed that limit.  I assume the issue is user/config error, because I wanted logs rotated every week regardless of the size and only rotated based on the size when they hit the limit specified. I like to keep 26 weeks of all logs. Call me crazy.

Journalctl does move some external stuff commonly used into the log system. Eventually, that will be good. Now it still feels like an extra middleman in our logging processes.  

/var/ isn't just a log partition. There are many other things there.  As usual, something that seems simple, isn't.
If logs are going to fill a system and nobody is looking at those logs, I would argue that crashing the box to get attention is a desired behavior. Others can disagree.

---

### Post by ameinild on 2020-09-25
Thanks for insights as always. But as you mention yourself, I guess logrotate can't properly handle a sudden log increase to 15 GB / hour before filling the log partition on most systems - or maybe it can? 
Anyway, all I'm saying is that, as a contrast to making separate partitions for /var/log, there could be another space controlling mechanism to ensure that abnormal log generation on it's own wouldn't crash a Linux server.
It sounds like server admins are generally relying on partitioning to solve this issue. On the other hand it sounds like a rather "serious issue", where I don't understand why there isn't a more straightforward and easier solution, that doesn't impose the other limitations that multiple partitions do.

Also, the reason I'm focused on logs is 1) because you and LHammonds bought it up as an explanation for multiple partitions and 2) because almost every post on Askubuntu where a user's system suddenly has no space left is because some insane logging spamming has been in effect. So it's apparently also an issue for many "normal" users that just want to use their PC.

After digging a little more into rsyslogd, it also seems you can limit the size of particular logs. Maybe it would be appropriate that Ubuntu had a default max syslog size of 2GB.

It's ok that we disagree. I maybe just think that Linux (and Ubuntu in particular) could be a little easier for everyone if there was a more straightforward way (and maybe set up as default) to prevent that your system was brought down because of log spamming. And since /var/log is the default location for this, I think that limiting the total size of this dir or the standard log files is a good place to start - even if you have the files on a separate partition. 8-)

---

### Post by TheFu on 2020-09-25
Agreed.  However, the log file that grew on me was in /opt/, not /var/.  

It is a massively integrated suite of F/LOSS tools put together by a company about 15 yrs ago, which was bought, sold, and sold again. They have F/LOSS and commercial customers.

Running out of space can happen anywhere.  /var/log isn't as bad as running out of space in /boot/ during a kernel update. Forcing an admin to pay attention **is** a feature.

---

### Post by ameinild on 2020-09-25
> **TheFu said:**
> Forcing an admin to pay attention **is** a feature.

Gospel - but sending an email first before crashing the server is preferred !! :D

---

### Post by TheFu on 2020-09-25
> **ameinild said:**
> Gospel - but sending an email first before crashing the server is preferred !! :D

**Logwatch**.

---

### Post by LHammonds on 2020-09-25
> **ameinild said:**
> Gospel - but sending an email first before crashing the server is preferred !! :D
[B] Nagios.
[/B][check-storage.sh](https://github.com/LHammonds/ubuntu-bash/blob/master/check-storage.sh)

---

