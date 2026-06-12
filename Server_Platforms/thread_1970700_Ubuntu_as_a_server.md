---
title: "Ubuntu as a server?"
date: 2012-05-01
forum: Server Platforms
---

### Post by Rukiri on 2012-05-01
I use arch and gentoo linux as my 2 primary desktop OSs, but for a server they're just too unstable.

I'm looking at server OSs especially Red Hate, Suse(free unless you want support/updates), Debian, and CentOS.

I plan on hosting a few sites but what matters most is stability, I also know that suse offers gui controls for controlling your web server be it apache, lighttpd, cherokee, nginx, etc.  This is something that I see useful for a server environment.

Ubuntu's desktop is easy to use but I don't really care for the desktop version as I have arch and gentoo.  But for servers it's different I need stability and performance.

How does Ubuntu server (what is it, 12.04 now?) compare to Suse Enterprise Linux Server, Red Hat Enterprise Linux, CentOS, and FreeBSD?

---

### Post by darkod on 2012-05-01
I wouldn't know of direct comparison, but I can tell you something most experienced users will tell you: GUI can bring security and performance concerns on a server.

I understand the logic in looking into a GUI, I myself don't know the command line enough too. But, you are really strongly advised to consider command line only on any linux distribution servers.

I recently used ubuntu 10.04 LTS (12.04 was not out yet) to make a firewall/router machine standing in front of a windows web server. I am very satisfied how it works being under constant attacks (that was the reason the company wanted a dedicated firewall).

In more than three weeks online, no freeze, no reboot, no failure... I am impressed.

Also, ubuntu is supported for updates and you don't pay for anything, except if you are after some really professional support team.

---

### Post by LHammonds on 2012-05-01
I will go ahead and shadow what darkod already said which is almost word-for-word what I would have said.  You definitely do NOT want a gui on a server if you can avoid it.  That doesn't mean you cannot have a web frontend for your applications such as webmin.

I have several Ubuntu Server 10.04 LTS (64-bit) servers.  One running MySQL, another running Nagios for my network monitoring system, another for my email server and for the last year, I have not had a single problem with them (knocks on wood).

I might also note that I'm a relative newbie when it comes to Linux.  But when I was searching for the best solution, I ended up going with Ubuntu because it was free to try and use but the Long-Term-Support meant that if I ever needed to slap support onto the server, I could get professional help asap which is nice-2-know.

Ubuntu 12.04 LTS just released so I'd recommend using 10.04 LTS for a little while first since it has a proven track record..but again, 12.04 has the "LTS" slapped on the end of it which means they plan on supporting that guy for several years.

RedHat also has a proven history but I did not go with it because it would have cost money to implement it.  CentOS is basically a free version of RedHat Enterprise but you have no option to obtain support.

Something else you might want to look at is an offshoot called Zentyal.  I used one of these servers to setup a CUPS print server.  I tried doing it all by hand on an Ubuntu Server but I failed to get it running right.  But when I tried Zentyal, I was able to get it running VERY quickly.  It has been running for 2 months now without any problems too.

**EDIT:** To see how I setup an Ubuntu Server for use with Zimbra mail server, you can see [my step-by-step notes here]("http://www.zimbra.com/forums/installation/56367-my-notes-installing-zimbra-ose-ubuntu-server-10-04-lts.html").

LHammonds

---

### Post by YSS on 2012-05-01
Hi, I installed Ubuntu server without GUI and it has some nice already set defaults you will like as an administrator, little things, like when you login you see the load of your server and stuff like that. 

I ran several CentOS6.2 servers, and they did a great job. Ubuntu is just a little more 'fresh' than CentOS who follows Redhats stuff and removes tthe name redhat and changes it into centos. 

I just installed my T420 to the latest ubuntu, planning on doing my 8 screen desktop later on... MAYBE...

I can't talk about the others distros for servers you are referring too. 

I would also say: Hey, it's linux! What the heck, download and install and see for yourself !!!!!!!

---

### Post by lykwydchykyn on 2012-05-01
I run Ubuntu server and SLES10 on a few servers here at work, but on most of the servers I use Debian stable.  

I don't care much for SLES.  It's a pain to upgrade, which is why I'm still on 10 and not 11.  I don't like YAST, which is pretty much the defining factor of Suse.

Between Debian and Ubuntu, it's mostly a toss-up; Debian gets a lot more testing before release, has a more conservative architecture (uses sysv-init instead of upstart, e.g.), and upgrading is usually simple and painless ( I have servers running squeeze that were originally installed as Sarge and upgraded every release -- still running strong!).  

Ubuntu has newer packages, some time-saving tools (like ufw), some interesting or better-supported services (like cloud stuff, LTSP 5), and the whole PPA thing if you need some special packages not in the main repositories.

I don't have a lot of experience in RedHat and its derivatives, but out of all of them I'd say Ubuntu's distinguishing feature is the newer packages.

---

### Post by Vishal Agarwal on 2012-05-02
The Server with black screen gets rebooted with in half a minute. The best part of my server. Try installing the server w/out GUI, and work with CLI. soon you will start liking it.

---

### Post by shaqa on 2012-05-14
> **Rukiri said:**
> 
Ubuntu's desktop is easy to use but I don't really care for the desktop version as I have arch and gentoo.  But for servers it's different I need stability and performance.

How does Ubuntu server (what is it, 12.04 now?) compare to Suse Enterprise Linux Server, Red Hat Enterprise Linux, CentOS, and FreeBSD?
since you asked about FreeBSD, there are two major versions at the moment. 8.3 and 9.x (haven't played much with the latter yet)

Ive been using both, FreeBSD and Ubuntu  on and off on same PC based home server (I like to tinker, install one, play with it couple of weeks-month, in the end I break something and need to reinstall..then usually the other)

FreeBSD is definitely more stable by nature. Also might be on average faster even while emulating linux code(I have heard of native linux 3D games getting better performance on FreeBSD over emulation layer). Less file systems supported is annoyance. But ZFS (FreeBSD 9.x is using OpenSolaris ZFS by default) is the best file system for server there can be IMHO. Zfs is perhaps quite not as fast as BTRFS but does wonders keeping data from getting corrupted.. And btfrs has still no "stable" version so it does not really count if you need utter reliability.

Ubuntu is more user friendly but for server I would use FreeBSD.. or OpenBSD, depending on situation

---

