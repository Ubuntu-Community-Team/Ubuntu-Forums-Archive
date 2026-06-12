---
title: "Headless Server Goes Completely Offline While tuned still on"
date: 2021-10-17
forum: Server Platforms
---

### Post by luyarauthor456 on 2021-10-17
[COLOR=#000000]I have a server running Ubuntu desktop 20.04 headlessly, with Teamviewer and ssh set up to control it.[/COLOR]

[COLOR=#000000]After a seemingly random interval (usually 1-3 days) the server becomes completely inaccessible despite still being powered on. I am forced to restart it without being able to see what happened because it is only accessed via network[.]("https://apksprofree.com/game-apk/casual/")[/COLOR]

[COLOR=#000000]Any ideas on how to troubleshoot this? Is there somewhere like event viewer in windows that I can check the logs on?[/COLOR]


[COLOR=#000000]Thank you for any help.[/COLOR]

---

### Post by TheFu on 2021-10-18
Does teamviewer have a timeout?  I'm not a fan of third party access systems.

I've been running Ubuntu servers for ... well ... forever and none of my servers do that. I don't use teamviewer or network-manager.  I avoid using a "desktop" ISO install as a server too. Use a server install for server needs.

I do have an Ubuntu 20.04 Mate desktop that has been up and available ... 
```
$ uptime
 20:57:26 up 8 days,  9:13,
```
The networking for it is configured through netplan with networkd as the renderer, not network manager.  I generally purge network manager very early in my new Ubuntu system setups.

Every 10 minutes, that desktop is part of my "can I access these 10 systems list" and it is always available.
I seldom login using a GUI to that system. Almost all access is either through **ssh** or I'll run an **ssh -X** connection to have a GUI program on the system run there, but be displayed here instead.

Is the network connection wired ethernet or something else?

---

### Post by mikequist on 2021-10-19
I have a similar issue and made a post earlier today about it. I used this script:
[https://github.com/ltpitt/bash-network-repair-automation](https://github.com/ltpitt/bash-network-repair-automation)
Which I have running once every minute. Looking at the logs, I found that my network interface (eth0) goes down every 36 hours, pretty much on the dot. I haven't figured out why yet, but this script really helps keep my downtime to 2 minutes every 36 hours.

---

### Post by TheFu on 2021-10-19
> **mikequist said:**
> I have a similar issue and made a post earlier today about it. I used this script:
[https://github.com/ltpitt/bash-network-repair-automation](https://github.com/ltpitt/bash-network-repair-automation)
Which I have running once every minute. Looking at the logs, I found that my network interface (eth0) goes down every 36 hours, pretty much on the dot. I haven't figured out why yet, but this script really helps keep my downtime to 2 minutes every 36 hours.

Yours is a VPS. This thread is about a physical server. Not quite the same.
Check the system logs at the time when the network fails. Anything in there of use?  Try a different NIC, cable, switch port. All normal troubleshooting.

The basic troubleshooting method is to simplify and test, then repeat until the exact component with the issue cannot be simplified further. Then replace that component.
People sometimes blame the wrong thing because they didn't move the cable to a different switch port and learn that it was the switch with the issue, not the cable or computer.  Or they didn't try a different cable ... so they spend weeks with an issue that $3 would have solved.

---

### Post by yancek on 2021-10-20
>  [COLOR=#000000]Is there somewhere like event viewer in windows that I can check the logs on?[/COLOR]

I'm not sure if I am interpreting that statement correctly.  I expect you are aware a default windows system can't read a Linux filesystem so you may mean software comparable to Event Viewer in windows?  You should be aware, if you are using a server, that the log files you need to view are in the /var/log directory and I would suggest the next time you have to reboot the server, you take a look at the various log files there.  I'm not sure which would be best to look at but someone else may have a suggestion.

---

### Post by TheFu on 2021-10-20
On ubuntu, logs can be accessed using any of the 200+ text processing tools that all Unix-like OSes have.  Logs are typically placed in /var/log/ ... somewhere.  Different programs may have their own logs, but many will use the system log ... "syslog".  This directory is for server/system logs. Individual logs for desktop programs and programs manually installed typically are placed into other locations, as configured for that specific program.

The logs that the system uses can also be accessed using **journalctl**.  It has many options and can be configured to retain as much logs as you like, ship the logs to a different log server, and to not retain any logs at all.  I wish I could say what the defaults were for journalctl, but I've always been unhappy with the defaults either not retaining any logs between reboots or allowing logs to grow much too large, so I typically tell it to write logs and keep 500MB worth.  That's usually 5-10 reboots - which is about 6 months for my systems.

Some notes I have on log files:
```
== Log Files ==

journalctl -xe            # See errors for last service
journalctl -b -1          # See prior boot log
journalctl -b -3          # See 3 boot logs ago
journalctl -b             # See current boot log
journalctl -S today       # See logs for today, from midnight
journalctl -xe -S today   # See errors for today, from midnight

journalctl --disk-usage   # See log file disk use
sudo journalctl --vacuum-size=200M    # Drop log file size to 200M, if possible.
```

journalctl can be used to specify specific periods to limit searches, which is why noting the time of an issue within a few minutes is always a good idea.  There's a full manpage on most Linux commands that shows all the available options and arguments to the command to make getting the exact output desired possible.

I didn't show any grep with journalctl. It has a regex engine too, so using that would be a good idea.
Before journalctl, I'd use 
```
sudo egrep -i 'erro|warn' /var/log/*g
```
as my starting point to figure out issues.  The sudo is necessary for some text log files, but not all. Use as needed.

---

### Post by slickymaster on 2021-10-20
*Thread moved to **Server Platforms**.*

---

### Post by CharlesA on 2021-10-20
I think TheFu covered most everything you need to check the logs and see if there is any gaps when the machine becomes non responsive.

Do you have out of band access to the box (IDRAC, IPMI, etc) so you can look at the output on the console when these freezes occur?

Speaking for myself, personally, I would also ditch TeamViewer for any other form of remote access. I cannot provide any recommendations since you didn't mention what the purpose of this server is.

---

### Post by SeijiSensei on 2021-10-20
The (CentOS 6) server running in my closet has been up for over 53 days.  That's actually not very long compared to other machines I've maintained. Stick to SSH and the command line for remote management. If you must run a graphical application on the server, use "ssh -X" to have the program's display appear on your machine.

---

### Post by MAFoElffen on 2021-10-21
Recommendation: Second half of this post: [https://ubuntuforums.org/showthread.php?t=2465986&p=14054377#post14054377](https://ubuntuforums.org/showthread.php?t=2465986&p=14054377#post14054377)

"Event Viewer" is an MS Windows term/app, that loosely translates to Linux, in it's functionally to what TheFu is saying... Event Viewer, in Windows, skims the system logs and you set alerts on audits / preset trigger warnings and threshold events in those logs. You can write a quick script in Linux, and run it as a job to do the same on the log files TheFu mentioned. That is how you replicate the same functionality in Linux, by creating scheduled reports and triggered administrative events.

---

