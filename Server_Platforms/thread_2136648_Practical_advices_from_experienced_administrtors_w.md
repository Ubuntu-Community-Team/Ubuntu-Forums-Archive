---
title: "Practical advices from experienced administrtors wanted."
date: 2013-04-18
forum: Server Platforms
---

### Post by JnPson on 2013-04-18
I'm new as a Linux administrator and I would like to ask you all what to think about in the daily work with my server? I run Ubuntu 12.04.2. It has installed Samba 4.0.5 with AD DC and internal DNS, it has isc-dhcp-server, and later on quota, cups and Postfix mail server. 


[LIST]
[*]What is the first thing you do when you log on to your server?
[LIST]
[*]I do *apt-get update && apt-get upgrade*. Is this a good thing to do? 
[/LIST]
  
[*]What logs are you following and what commands do you run?
[LIST]
[*]I do *tail -f /var/log/syslog*, but it shows only named and dhcp leases etc. 
[/LIST]
  
[*]How often do you update your server and what makes you decide to update or not?
[LIST]
[*]I run updates as soon as possible, but it can sometimes be a wrong desicion, or? 
[/LIST]
  
[*]What are the pit falls as a linux admin, and what do I have to be careful of?
[LIST]
[*]I know about the root account and the danger in having it enabled. 
[/LIST]
  
[/LIST]

Any advice is valuable to me. Thanks.

//Jn.Pson

---

### Post by TheFu on 2013-04-18
There are as many ways to admin a Linux server as there are Linux admins.  If you admin fewer than 5 servers, doing everything manually, like MS-Windows admins are taught, might be just fine. Soon, any Linux admin should learn that being lazy is the key to becoming a good admin.

> **JnPson said:**
> I'm new as a Linux administrator and I would like to ask you all what to think about in the daily work with my server? I run Ubuntu 12.04.2. It has installed Samba 4.0.5 with AD DC and internal DNS, it has isc-dhcp-server, and later on quota, cups and Postfix mail server. 

I would not run any email on the same server as I run DHCP or DNS or AD. Email is too large a security risk to run on a system running anything else, IMHO.  When it comes to the most hacked services on UNIX/Linux systems, DNS and email are the top 2. Those really need to be run on different machines (even a different VM would be fine) and inside a chroot environment for both.

> **JnPson said:**
> [*]What is the first thing you do when you log on to your server?
[LIST]
[*]I do *apt-get update && apt-get upgrade*. Is this a good thing to do? 
[/LIST]

I avoid logging into servers directly. If I do need to login at all, that means I've failed in some other way.  System logs should be pushed to a centralized system where other tools monitor for issues, not me.  I don't have time to review every line of every log file from every server. I need to have monitoring and alarming systems point out issues that need my direct attention.  

I definitely do not manually install updates. Those are all scripted - though I do manually run that centralized script every Saturday morning. Further, I use dist-upgrade to ensure the new kernels are installed.
  
> **JnPson said:**
> [*]What logs are you following and what commands do you run?
[LIST]
[*]I do *tail -f /var/log/syslog*, but it shows only named and dhcp leases etc. 
[/LIST]

logwatch and some custom scripts help me stay on top of logs. If I had a few more systems, I'd get splunk working.
  
> **JnPson said:**
> [*]How often do you update your server and what makes you decide to update or not?
[LIST]
[*]I run updates as soon as possible, but it can sometimes be a wrong desicion, or? 
[/LIST]
I update weekly, during an approved maintenance window. This minimizes downtime for other users and provides a time period where I can correct any issues - including rebuilding a VM if necessary - to resolve a problem.
  
> **JnPson said:**
> [*]What are the pit falls as a linux admin, and what do I have to be careful of?
[LIST]
[*]I know about the root account and the danger in having it enabled. 
[/LIST]

Root access is a necessary part of our jobs. Use it when you need it, but try to use sudo most of the time so the command is logged.
The most important thing I do as an admin is have backups, versioned backups.  If a server was hacked 30 days ago, I can restore the backup from 31 days ago and be relatively happy.  Backups, backups, backups.  Of course, if I don't know how to rebuild the VM/machine from that backup, then all that effort was a complete waste of time.  Testing restores is mandatory.  Don't THINK you know how to restore, KNOW that you KNOW how to restore.
  

During the week, my systems are up and available - PERIOD.  Ok, there is a 5 minute window nightly during which the email IMAP server is not available ... during backups, but the rest of the time, it is up and available.  The email gateway server is always available, unless it needs to be rebooted for a kernel update.

If I can't perform patching on the Saturday morning as planned, then patching waits for the following Saturday.  Also, if I'm going to be out of town, I will not patch a stable system within 5 days of the trip.

Many large scale admins will talk about rebuilding servers from the ground up using tools like Rex or Chef or Puppet.  Monitoring tools like nagios, nms, zabbix, and others (can't think of the best one for simple setups now, sorry) are critical for environments with many servers too.  These tools are very important when you have more servers and need to automate administration tasks.  Log analysis can be very time consuming. Learn a few different tools and become a regex master.

There are GUI tools like webmin/mysqladmin/etc that some admins swear by.  I've never used them, but when I was new, I did find their appeal very enticing. Fortunately, they all sucked 20 yrs ago, so I never bothered.  These days I see those admin-GUI tools as a liability. From time to time, a security whole will be found in a tool that provides admin access to anyone on the internet.  If you do use those tools, please, please, please, please lock down the remote IP addresses from which logins are allowed. Please.

Learn at least 1 scripting language to help automate tasks. Python is probably the best all-around tool for this today, but some knowledge of bash, ksh, sh, perl and ruby would be a good idea too. Don't fear the shell.

ssh rocks. Know it, love it, use it.
Avoid running plain FTP anywhere.  Avoid running any services on any interface where it isn't needed.

It is hard to dump 20+ yrs of admin experience into a forum.  I can't wait to see what others with slightly different experiences say on this topic too.

---

### Post by JnPson on 2013-04-18
Wow I'm gonna read the answers in your post and the others, like a bible. 
Much, much appreciated advices. Thank you.

---

### Post by TheFu on 2013-04-18
> **JnPson said:**
> Wow I'm gonna read the answers in your post and the others, like a bible. 
Much, much appreciated advices. Thank you.

There are many different opinions on administration techniques. You need to find the best solution to manage the risks that your systems experience.  Bible is too strong a term. There are definitely areas where I can still improve.

I've been relatively lucky over the years - only had 2 systems hacked in all that time and nothing in the last decade.  Does that mean I'm a better admin than anyone else? Nope.  It just means that my systems were** hardened enough **and not something that someone really wanted into.  When I see some admin claiming that all the hardening I do is excessive - clearly they are experts since their system(s) have never been hacked - I have to wonder how much they really understand.  Any system can be hacked. ANY SYSTEM.  I firmly believe it. It doesn't matter what the OS is, if it is connected to a network, it can be hacked.

The best security training that I've ever had was being hacked and figuring out who, how and why they did it.  In my research, the reason was always "because they could."  The systems were not targeted, they just happened to have a weakness in the running program or configuration.

I've had conversations with CEOs explaining that their web site would be hacked and there was nothing we could do about it. Nothing, except to have a good plan to restore service and make the data available. The plan wouldn't allow interactive access for a few hours or days, but the data would be available.  Thankfully, we've never been hacked, but we have a plan and the ability to execute that plan to a completely different service provider, if necessary.  Service would be restored.   Clearly, backups are central to the plan.

BTW, I have a blog where I write about mostly Linux, networking and virtualization stuff. I've been a little busy with life the last few months, so my post frequency has dropped, but used to get 1 article a week out covering all sorts of things. Most of the articles were just a way to keep notes for myself. jdpfu.com

---

### Post by CharlesA on 2013-04-18
> **TheFu said:**
> There are as many ways to admin a Linux server as there are Linux admins.  If you admin fewer than 5 servers, doing everything manually, like MS-Windows admins are taught, might be just fine. Soon, any Linux admin should learn that being lazy is the key to becoming a good admin.

+1. Shell scripts (and other scripts) are your friends. Various monitoring tools are also your friends.

> I would not run any email on the same server as I run DHCP or DNS or AD. Email is too large a security risk to run on a system running anything else, IMHO.  When it comes to the most hacked services on UNIX/Linux systems, DNS and email are the top 2. Those really need to be run on different machines (even a different VM would be fine) and inside a chroot environment for both.

Agreed. I would run an email server on a VM to seperate it from everything else. That way if the email server is owned, the whole server isn't owned.

> I avoid logging into servers directly. If I do need to login at all, that means I've failed in some other way.  System logs should be pushed to a centralized system where other tools monitor for issues, not me.  I don't have time to review every line of every log file from every server. I need to have monitoring and alarming systems point out issues that need my direct attention.

I do the same at work and on my VPS. The only reason I actually log in to those is if I am testing something (on my VPS) or if I need to do an update.  

> I definitely do not manually install updates. Those are all scripted - though I do manually run that centralized script every Saturday morning. Further, I use dist-upgrade to ensure the new kernels are installed.

I have both my home server, VPS and Debian box at work running unattended-upgrades set for security updates only and I have apticron running to notify me of any non security updates that need to be applied. As far as when I apply updates, it depends. On my home box and VPS, I do them whenever I get a notification they are avalible, but on the work machine, I leave it alone until the rest of IT does their 'patch day'

Granted the Debian box at work is only running a few services - apache, mysql and postfix, I rarely check the logs on it because it is only accessible internally and most of the people that use it access it via web browser.
  
> logwatch and some custom scripts help me stay on top of logs. If I had a few more systems, I'd get splunk working.

I've been using logwatch on my home server and VPS, and it really helps to cut down on the time spent parsing logs. It might not catch everything, but it'll tell you if someone is trying to bruteforce your SSH server.

> The most important thing I do as an admin is have backups, versioned backups.  If a server was hacked 30 days ago, I can restore the backup from 31 days ago and be relatively happy.  Backups, backups, backups.  Of course, if I don't know how to rebuild the VM/machine from that backup, then all that effort was a complete waste of time.  Testing restores is mandatory.  Don't THINK you know how to restore, KNOW that you KNOW how to restore.

+9000. I do versioned backups via a custom bash script.
  
> There are GUI tools like webmin/mysqladmin/etc that some admins swear by.  I've never used them, but when I was new, I did find their appeal very enticing. Fortunately, they all sucked 20 yrs ago, so I never bothered.  These days I see those admin-GUI tools as a liability. From time to time, a security whole will be found in a tool that provides admin access to anyone on the internet.  If you do use those tools, please, please, please, please lock down the remote IP addresses from which logins are allowed. Please.

Yes, please lock those tools down so they aren't accessible from the entire internet. I used to use webmin when I was using 9.04 or 9.10, but I've moved to SSH only now. Less services to worry about and you don't have to worry about another vector of attack.

> Learn at least 1 scripting language to help automate tasks. Python is probably the best all-around tool for this today, but some knowledge of bash, ksh, sh, perl and ruby would be a good idea too. Don't fear the shell.

Agreed. I learned BASH, but I really want to learn more python.

> ssh rocks. Know it, love it, use it.
Avoid running plain FTP anywhere.  Avoid running any services on any interface where it isn't needed.


SSH = awesome. I love it and the fact that I can use scp or sftp instead of regular ftp when transferring files.

> **TheFu said:**
> 
I've been relatively lucky over the years - only had 2 systems hacked in all that time and nothing in the last decade.  Does that mean I'm a better admin than anyone else? Nope.  It just means that my systems were** hardened enough **and not something that someone really wanted into.  When I see some admin claiming that all the hardening I do is excessive - clearly they are experts since their system(s) have never been hacked - I have to wonder how much they really understand.  Any system can be hacked. ANY SYSTEM.  I firmly believe it. It doesn't matter what the OS is, if it is connected to a network, it can be hacked.

So far I have been lucky, but I only have 1 box "out in the wild" so that one is pretty much locked down. My home server is only accessible via ssh from certain IPs, and that is the only service that is actually accessible via the Internet.

---

### Post by Habitual on 2013-04-18
Fix more than you break.

20 years.

---

### Post by JnPson on 2013-04-19
I will definitely learn python or bash or some other scripting language, I've seen the strength of scripted installations when Toxic64 helped me with the installation of Samba 4.0.5 GIT, and backups is the most important piece in the puzzle. No backups is like saying, "I never make mistakes" or "no one or nothing can hurt me". 

Can you point me to a good tutorial/howto on scripting languages?

It would also be a good thing for me to learn linux file/folder permissions and security and how it's built with the numbered stuff and what the different numbers means (like 0750 and drwxr-xr-x). 
```
drwxrwsr-x+ 2 3000000 users 4096 Apr 17 11:20 test
```

This below is also a little confusing to me. I understand the principle but have no deeper understanding of the meaning of each of the lines. I would like to know what I'm doing and with that knowledge, make the the most efficient and safest server I can. 
```
[INDENT]mkdir -m 770 /Users
chmod g+s /Users
chown root:users /Users
[/INDENT]

``` ```
[Users]
        directory_mode: parameter = 0700
        read only = no
        browseable = no
        path = /Users
```

Toxic64 helped me with the scripts. I added 'browseable = no' and then I needed to add users roaming profiles so I just copied and pasted the lines. But then again, I don't have the deeper understanding what each line means, and if it is safe or the best way of creating shares. 
```
[INDENT]mkdir -m 770 /Profiles
chmod g+s /Profiles
chown root:users /Profiles
[/INDENT]

``````
[Profiles]
        directory_mode: parameter = 0700
        read only = no
        browseable = no
        path = /Profiles

```

You see what I mean?

If you know how this stuff works or have a nice tutorial please point me there.

---

### Post by JnPson on 2013-04-26
Hi again.
I found several bash-scripting guides and I've downloaded them for offline browsing. I hope these guides are up-to-date and still valid, hopefully nothing important has changed. If so, I might run in to scripting problems later on. 

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)  Advanced Bash-Scripting Guide
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) BASH Programming - Introduction How-To
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/) BASH Guide for beginners

//JnPson

---

### Post by slickymaster on 2013-04-26
Here are some more resources you might take a look at:[URL="http://ptgmedia.pearsoncmg.com/images/0131408828/downloads/0131408828.pdf"]
Managing Linux Systems with Webmin[/URL]
[The GNU/Linux Advanced Administration]("http://ftacademy.org/files/materials/fta-m2-admin_gnulinux-v1.pdf")
[The Debian Administrator's Handbook]("http://debian-handbook.info/download/stable/debian-handbook.pdf")
[Advanced Linux Programming]("http://www.advancedlinuxprogramming.com/alp-folder/advanced-linux-programming.pdf")

---

### Post by CharlesA on 2013-04-26
Don't forget the Bash Pitfalls page!
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

---

### Post by JnPson on 2013-05-17
Bump

---

### Post by vikramk.ibs on 2013-05-18
really good advice.

Thank you

---

### Post by cprofitt on 2013-05-18
I use [Cacti]("http://www.cacti.net/") to monitor the server (uses SNMP) and [OSSEC]("http://www.ossec.net/") to monitor the log files, etc. OSSEC is a Host Based Intrusion Detection System.

---

### Post by JnPson on 2013-05-19
Thank you. Much appreciated advices. I will gather all links to the different software and read-up to learn what it does and how it works.

---

### Post by LHammonds on 2013-05-20
Something not mentioned yet is the configuration of your partitions.  It is usually the 1st thing that must be setup and impacts your system long after initial setup.  There are a million ways to configure your system and the default layout is not the best for long-term management of your server.  The major thing you need to avoid is the root partition filling up and running out of space.  For security reasons and to keep data/temp files isolated, I separate my partitions out so that the root does not have ever-growing data in it.  Look in my sig for info on how I configure my partitions using LVM and how I manage the growth automatically and how I allow myself time to grow my system by adding new drives far before they are needed.

I use Nagios to monitor my switches, printers, Windows servers and Ubuntu servers.  It lets me know when there are problems but more importantly, it allows me to track growth over time so I can accurately predict space consumption since I monitor each drive individually.  The reports allow me to show consumed/free space for a particular drive/partition over time.

I use a custom BASH script to automatically apply security patches.  However, I do not let the server automatically reboot after a kernel update.  I want to be there in case something goes wrong and it cannot boot up (prior experience with an infamous grub bug on 10.04).  Nagios lets me know when a Linux server is wanting a reboot to apply a kernel update.  I login to a non-critical server 1st and do the reboot to make sure the basic process will work.  I then continue up the ladder to the most important servers.  You can see the same script I use to automatically apply security updates in the Ubuntu Server link in my sig.  I also have a link to how I setup a Nagios server (step-by-step)

I don't login to my servers daily.  I only login when Nagios reports a problem (or a server wants a reboot) or a customer reports a problem with the system.

I don't "enable" the root account like many tutorials for Ubuntu 10 and below have recommended in the past.  If I need root access for more than one command (such as during initial setup), I simply use "sudo su" which will give me a root prompt.  However, I don't usually do that unless I need to manage the server in some way.  I do have an "opm" script that I have setup for each of my servers that allows anyone in my IT group to login to a server and perform the usual tasks such as a reboot, restart of primary services or apply a security patch even if they are not very familiar with Linux systems.  All they need to know is how to login and simply type "opm" to start up the menu.  This is also in my Ubuntu server link in my sig.

I must also recommend that you have a good backup system put in place that will handle various likely scenarios.  You need to know if your data should be restored by the hour, by the day, week, etc. and how far back you are expected to go and how granular.  People always want the most for the longest amount of time but physical limitations usually prevent it.  So you have to find a middle ground that handles the bulk of your risk.  Such as being able to restore data/files to a certain point within the last 24 hours and maybe to the day for the last 7 days and maybe to the week for the last 4 weeks and one backup for the last 2 quarters and 1 for the year.  Completely depends on your server, the data stored on it and how valuable the data is to the people using it.  If it is a DNS server, you may only care about having a couple of good backups before the latest kernel update.  If it is a mail server, it might be the most critical and require the most backups, etc.  But no matter how your backups are configured, they need to be automated to a point, they need to be documented, they need to be verified and you need to have the restore process documented and verified periodically.  I cover some ways to backup and restore at the partition level in the Ubuntu Server link in my sig.  Other methods such as Rsync for data are covered in other application-specific threads in my sig.

Good luck,
LHammonds

---

### Post by SirWeazel on 2013-05-20
This is a great thread. The responses have been great reads and sound like the are from experienced people. I saw you asked about file permissions in a previous post. One of the best tutorials I've read  was when i was setting up a media server.  Maybe this read will help you. 
 [http://wiki.plexapp.com/index.php/Plex_Media_Server-Linux_Permissions_Guide](http://wiki.plexapp.com/index.php/Plex_Media_Server-Linux_Permissions_Guide)

---

### Post by JnPson on 2013-05-23
Thank you guys. Will read, will test and will learn.

---

