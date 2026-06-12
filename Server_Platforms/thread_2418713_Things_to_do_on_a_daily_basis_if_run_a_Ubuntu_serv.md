---
title: "Things to do on a daily basis if run a Ubuntu server"
date: 2019-05-10
forum: Server Platforms
---

### Post by likewise2 on 2019-05-10
If I run a server on Ubuntu and say my site is running on plain LAMP stack. Then what day to day activity I have to perform?

People say about updating security patches and all. But if anybody can provide a list of all things that I must have to do on a daily basis or say weekly basis. Then it will be really helpful for me.

Note:- I am not talking about taking site backups such as files and databases.

---

### Post by howefield on 2019-05-10
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by LHammonds on 2019-05-10
If you configured it right...nothing on a daily basis and most-likely nothing on a weekly basis.

The only thing I "have to" do on my servers is apply the kernel patches which requires a reboot.  And I only do this because I don't want this specific task automated.  If a server reboots for a kernel update, I want to be there to ensure there is enough room in /boot and to note which kernel it is updating from/to.  I also do this with the least critical server so if there is an issue/bug, I want to work it out before subjecting my most critical servers to it.

I have automated the vast majority of other tasks so I do not have to mess with them unless there is a problem.

The /boot and /var should be kept clean using the "apt autoremove" command which is scheduled with the update/upgrade commands.
The MariaDB has jobs scheduled to dump all databases into a single .sql as well as break it out to database-specific files and then down to the table-specific files by database...which then gets archived and copied offsite.
I have a Nagios server that watches all the servers for specific services and to record statistics such as disk usage.  It should notify me if anything gets out of whack such as running low on disk space, need for reboot after updates, services not working, etc.

How I accomplish all this is documented in my how-to guides.  See my sig for details.

LHammonds

---

### Post by likewise2 on 2019-05-10
> **LHammonds said:**
> If you configured it right...nothing on a daily basis and most-likely nothing on a weekly basis.

The only thing I "have to" do on my servers is apply the kernel patches which requires a reboot.  And I only do this because I don't want this specific task automated.  If a server reboots for a kernel update, I want to be there to ensure there is enough room in /boot and to note which kernel it is updating from/to.  I also do this with the least critical server so if there is an issue/bug, I want to work it out before subjecting my most critical servers to it.

I have automated the vast majority of other tasks so I do not have to mess with them unless there is a problem.

The /boot and /var should be kept clean using the "apt autoremove" command which is scheduled with the update/upgrade commands.
The MariaDB has jobs scheduled to dump all databases into a single .sql as well as break it out to database-specific files and then down to the table-specific files by database...which then gets archived and copied offsite.
I have a Nagios server that watches all the servers for specific services and to record statistics such as disk usage.  It should notify me if anything gets out of whack such as running low on disk space, need for reboot after updates, services not working, etc.

How I accomplish all this is documented in my how-to guides.  See my sig for details.

LHammonds

If there is nothing to be do apart from backing up database, which in your case you have scheduled it. Then why people keep saying about day to day tasks?

---

### Post by Tadaen_Sylvermane on 2019-05-10
I've never heard of having to actively manage a server day by day. Maybe in the enterprise I guess. At home my server / main htpc has a current uptime of 67 days. I think I've sshed into it twice in that time to run updates. It mostly takes care of itself.

---

### Post by likewise2 on 2019-05-11
> **Tadaen_Sylvermane said:**
>  I think I've sshed into it twice in that time to run updates.
 
I am sorry I didn't understand what you meant by ''sshed''!!

---

### Post by lisati on 2019-05-11
> **likewise2 said:**
> I am sorry I didn't understand what you meant by ''sshed''!!

"ssh" is a method of "remotely" logging in to one computer from another, which can be useful if you are running a "headless" server (no keyboard or monitor) or if the server is based in another part of the same building.

If you decide to utilize this approach, I'd strongly recommend limiting SSH access only to devices and users that you can trust. Not having any kind of public access from devices outside the server's local network would be a good idea, particularly while you're finding your way around with SSH.

---

### Post by likewise2 on 2019-05-11
Ohh!! that I know. I use putty.

---

### Post by TheFu on 2019-05-11
> **likewise2 said:**
> If I run a server on Ubuntu and say my site is running on plain LAMP stack. Then what day to day activity I have to perform?

People say about updating security patches and all. But if anybody can provide a list of all things that I must have to do on a daily basis or say weekly basis. Then it will be really helpful for me.

Note:- I am not talking about taking site backups such as files and databases.

Daily, versioned, backups are my #1 security tool.  I get a daily report about the successful completion for each system.  With sufficient versioned backups, pulled, not pushed, not locally connected, any security failure can be recovered AND what happened, can be determined.  After all, restoring from a backup just to be hacked 5 min later isn't too smart.  Backups seem simple, but there are nuances to how those backups need to be performed to have the most useful protection.

What is needed is dependent on the server, which programs it runs, who can access them, what the attack risks are, what the attack vectors are, what other systems are on the same subnet or can be accessed, and how well you've already addressed each of those when you setup the box.

For example, for servers with a low-risk service that isn't available on the internet, the effort I put into daily maintenance is minimal.  I'll check the monitoring and logs to see if anything "looks funny."  There are monitoring tools, alarming tools, and log screeners to make this easier.  I spend about 30 seconds a day on trivial servers like that.

For higher risk servers, I'll usually put a front-end to control access - like an email gateway for email servers or a reverse proxy for web servers, to make attackers have to break 2 systems, not just 1.  

Network architecture is very important to security. If I get to design the network, many risks can be mitigated, whereas if I'm stuck on a hosting provider or VPS seller, there isn't much I can do to prevent the bad-guys from even getting to my server.

Every morning, here's what I do for each server:
* Check the status for the backups.  Did it complete as expected?  Did it take about the normal time or longer? If it is much longer, why?  Did the server get hacked and all files encrypted? I get an email summary for all the backups daily. 
* Go through any alarms from the monitoring system. Do the servers each appear to be running normally?  More CPU, more RAM used or not?  There are 30+ other things to monitor.  Disk storage, open files, network traffic, lots of traffic going places that it shouldn't?  There is a dashboard that shows red/yellow/green. Red is usually for low disk space or 1 box used to overheat and slow down.
* Go through the log summaries (logwatch). Any errors, warnings that need to be handled now, today, tonight, or can they wait until a maintenance period?  Was any software installed that I didn't expect?  Any software removed?

For an email server, I'll go through some of the logs beyond the log summary.  Looking for specific attacks and decide if I want to do anything about them. I have a few scripts that block SASL authentication failures. Previously, I used a tool, but it had some failures that I wasn't able to figure a fix, so made one of my own with about an hour work. End-users are terrible at choosing passwords and for IMAPS email there isn't really a good solution besides forced length and complexity. Every year, we force password changes and inactive accounts are automatically disabled if I forget.

For a web server,  I'll go through some of the logs beyond the log summary.  Looking for specific attacks and decide if I want to do anything about them. I get a summary of the attack sources daily and how many each has attempted. I already block any php attacks, since we don't allow php web-app on the internet.  Anyone hitting any public website with a URL ending in .php gets blocked after about 20 attempts. We block on subnet, user-agent, incorrect referrer, and specific URL requests.  /admin/ cannot be accessed over the internet, for example.  Only localhost is allowed to access admin pages on our systems. That means the admin needs to use an ssh-tunnel. There are some exceptions for my workstation's IP when at known locations.

I used to be pretty relaxed about security.  Then I got hacked.  Since then, it is a completely different story.  I was doing the normal stuff - which was basically nothing besides backups and patching.  I got lucky. Had a weekly backup that let me see exactly what changed.  Getting 1,000 emails an hour from the server every time their attack script ran (it was local) trying to escalate to root was a huge help.  If that hadn't happened, I probably wouldn't know about the attack - not back then.

The world is a different place now.  I see thousands of attacks every hour and that doesn't count the attacks our network blocks.  My tiny home server sees a few hundred attacks daily.

Please be very careful putting any php-webapp on the internet.

My list is pretty minimal and full of automation.  In the 1990s when I first started doing admin work, I didn't automate many things, just used cops to check file permissions weekly.  Some days I don't have time to look as deeply.  All our systems have at least 60 days of versioned backups.  Higher risk systems get 180 days.  Backups are critical for security.

---

### Post by LHammonds on 2019-05-14
> **likewise2 said:**
> If there is nothing to be do apart from backing up database, which in your case you have scheduled it. Then why people keep saying about day to day tasks?
You need to be more specific.  I cannot reply to something so vague as "people keep saying about day to day tasks."

As TheFu has mentioned, it really depends on what you are running.  Many of my services are intranet-based and the attack vectors are greatly reduced.  I do not count the "check emails" as part of the "day to day tasks on the server" since I do not touch the server to review email notifications (unless their are failures, warnings or automated increases for storage space).

LHammonds

---

