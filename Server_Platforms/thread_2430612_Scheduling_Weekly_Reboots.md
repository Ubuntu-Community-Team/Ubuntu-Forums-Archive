---
title: "Scheduling Weekly Reboots"
date: 2019-11-04
forum: Server Platforms
---

### Post by linuxnoob87 on 2019-11-04
All,

I think I've figure it out (finally) but wanted to check to see if this will work; I'm looking to reboot my Ubuntu server weekly on Sunday at 1:00 AM. Here's what I have in my crontab:

```
0 1   *   *   sun    /sbin/shutdown -r 0
```

Will this work or do I need to do something else? I've tried deciphering the man file for crontab but can't seem to get the hang of it.

Thanks in advance!

---

### Post by LHammonds on 2019-11-05
Yes that looks correct for the time you want to issue the command.

However, I would be careful about issuing that command.  Some services will shutdown gracefully with the shutdown of the operating system.  Others might not and sometimes the ones that are supposed to shutdown gracefully will not.  In those cases, you would need additional error checking and determine how best to handle those situations.

If you have any services running, you might want to shut them down gracefully first before issuing the reboot command.

Example crontab:

```
0  1  *  *  sun   /var/scripts/reboot.sh
```

Example reboot script (no error checking):

```

#!/bin/bash
systemctl stop nagios
systemctl stop apache2
systemctl stop mariadb
/sbin/shutdown -R now

```

---

### Post by Tadaen_Sylvermane on 2019-11-05
Just a curiosity question. Why reboot it at all? I leave mine running 24/7 unless I have an absolute need to power down or reboot. For me my uptimes are measured in the weeks / months usually until an update demands a reboot or something. I've read of some linux servers going into the years range of uptime. Idk if that's a good thing, but it highlights that rebooting should not really be required much.

---

### Post by LHammonds on 2019-11-06
> **Tadaen_Sylvermane said:**
> Just a curiosity question. Why reboot it at all?
For the OS, you need to reboot at least monthly for the kernel updates.  Some applications require rebooting to clear memory leaks...sometimes daily (e.g. Minecraft server).  Or maybe the application installed tends to create zombie processes, etc.

For the longest time, I just had my servers email me when they needed a reboot because I had bad experiences with booting up after kernel updates back in the days of Ubuntu 10.04 but recently I decided to switch to automated reboots which check for the existence of /var/run/reboot.required and it sends me a reboot notification prior to actually rebooting during the maintenance window.

LHammonds

---

### Post by TheFu on 2019-11-06
> **Tadaen_Sylvermane said:**
> Just a curiosity question. Why reboot it at all? I leave mine running 24/7 unless I have an absolute need to power down or reboot. For me my uptimes are measured in the weeks / months usually until an update demands a reboot or something. I've read of some linux servers going into the years range of uptime. Idk if that's a good thing, but it highlights that rebooting should not really be required much.

Testify!
```
$ uptime
 09:07:58 up 124 days, 19:42,  2 users,  load average: 0.17, 0.10, 0.09

```

Linux/Unix isn't Windows. No need to reboot just because.  The valid reasons to reboot are:
* new kernel/libc
* modifications of startup scripts that need testing
* new hardware with drivers that only get initialized correctly due to a reboot. Often, these devices need a full power cut to properly initialize.

Rebooting just because ... that is a Windows thing.  If there is some process so poorly written that it need periodic rebooting to clean up .... whatever ... open bugs with the project team if you can't switch to a better solution.  Restarting a few processes periodically while the bugs are being addressed is much faster than a total reboot.

---

### Post by linuxnoob87 on 2019-11-06
Looking to reboot weekly as I'm running a Plex server and anything more than a week seems to prevent me from being able to SSH/Log into the system

---

### Post by linuxnoob87 on 2019-11-06
> **LHammonds said:**
> Yes that looks correct for the time you want to issue the command.

However, I would be careful about issuing that command.  Some services will shutdown gracefully with the shutdown of the operating system.  Others might not and sometimes the ones that are supposed to shutdown gracefully will not.  In those cases, you would need additional error checking and determine how best to handle those situations.

If you have any services running, you might want to shut them down gracefully first before issuing the reboot command.

Example crontab:

```
0  1  *  *  sun   /var/scripts/reboot.sh
```

Example reboot script (no error checking):

```

#!/bin/bash
systemctl stop nagios
systemctl stop apache2
systemctl stop mariadb
/sbin/shutdown -R now

```


So I should, then, be able to modify this for the two Plex related services; these should be the only ones to worry about correct? In that, I should only have to worry about 3rd party services.

---

### Post by linuxnoob87 on 2019-11-06
> **TheFu said:**
> Testify!
```
$ uptime
 09:07:58 up 124 days, 19:42,  2 users,  load average: 0.17, 0.10, 0.09

```

Linux/Unix isn't Windows. No need to reboot just because.  The valid reasons to reboot are:
* new kernel/libc
* modifications of startup scripts that need testing
* new hardware with drivers that only get initialized correctly due to a reboot. Often, these devices need a full power cut to properly initialize.

Rebooting just because ... that is a Windows thing.  If there is some process so poorly written that it need periodic rebooting to clean up .... whatever ... open bugs with the project team if you can't switch to a better solution.  Restarting a few processes periodically while the bugs are being addressed is much faster than a total reboot.

Plex, after a week, seems to make the system unresponsive to logging in either locally or via SSH.

---

### Post by TheFu on 2019-11-06
> **linuxnoob87 said:**
> Plex, after a week, seems to make the system unresponsive to logging in either locally or via SSH.

Instead of rebooting the entire system, would restart for plex solve it? Or perhaps the sshd?  Rebooting an entire system without a specific reason just seems wrong to me.

Or review the log files for the real issue and solve that.  It could be plex or something else. 
With monitoring setup, you could see what the normal CPU, RAM, files, swap, networking, and 50 other things for performance are doing.  Munin is pretty easy to setup.

---

### Post by linuxnoob87 on 2019-11-07
> **TheFu said:**
> Instead of rebooting the entire system, would restart for plex solve it? Or perhaps the sshd?  Rebooting an entire system without a specific reason just seems wrong to me.

Or review the log files for the real issue and solve that.  It could be plex or something else. 
With monitoring setup, you could see what the normal CPU, RAM, files, swap, networking, and 50 other things for performance are doing.  Munin is pretty easy to setup.

Interesting; I never thought about restarting the plex service. I'm guessing this would use the crontab file still, but how would you tell it to restart the service? I know how to restart the service from the terminal I just don't know how you'd do it from the crontab file.

Any pointers?

---

### Post by TheFu on 2019-11-07
Same command, just use the full path to it in the root crontab.
On 16.04, 
```
/usr/sbin/service plexmediaserver restart
```
I've been able to avoid systemd stuff, but use the full path to the program.

---

### Post by linuxnoob87 on 2019-11-11
> **TheFu said:**
> Same command, just use the full path to it in the root crontab.
On 16.04, 
```
/usr/sbin/service plexmediaserver restart
```
I've been able to avoid systemd stuff, but use the full path to the program.


So to restart the service every Sunday at 2:30 AM it would be:
```
30 2  *    *    7 ]/usr/sbin/service plexmediaserver restart 
```

Correct?

Thank you in advance!

---

### Post by Tadaen_Sylvermane on 2019-11-12
remove the ]

---

### Post by linuxnoob87 on 2019-11-12
> **Tadaen_Sylvermane said:**
> remove the ]

So one question for you; what in the command tells it that it should be "Sunday" - the "7"?

---

### Post by TheFu on 2019-11-12
```
# m h  dom mon dow   command
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  *  command to be executed
# *  *  *  *  *  command --arg1 --arg2 file1 file2 2>&1

```
Put that in the crontab that you edit using **crontab -e** as a reminder.

---

### Post by Skaperen on 2019-11-12
> **linuxnoob87 said:**
> Looking to reboot weekly as I'm running a Plex server and anything more than a week seems to prevent me from being able to SSH/Log into the system
that's not the way things should work.  i've left my server up for months and when i ssh in, all works fine, every time, just as it should.

about the only trouble i have with a long running Linux is an overly cluttered page table or swap space the slows thing down.  i like to reboot to a clean system when i run upgrades and reboot twice afterwards because some packages like to have some things finish after the next reboot.  and that gets me onto the latest kernel the upgrade brought in.  but i still do all that manually because there is no time i am regularly not using the laptop.

---

### Post by Skaperen on 2019-11-12
```

#       __________ Minute (0-59)
#      / _________ Hour (0-23)
#     / /  _______ Day Of Month (1-31)
#    / /  /   ____ MONth (1-12) -OR- jan,feb,mar,apr,may,jun,jul,aug,sep,oct.nov,dec
#   / /  /   /   _ Day Of Week (0-7) (Sun = 0 or 7) -OR- sun,mon,tue,wed,thu,fri,sat
#  / /  /   /   /  -------------------------------------------------------------
# m h dom mon dow  command  <arguments>  &>logfilename
```

---

### Post by linuxnoob87 on 2019-11-13
> **Skaperen said:**
> that's not the way things should work.  i've left my server up for months and when i ssh in, all works fine, every time, just as it should.

about the only trouble i have with a long running Linux is an overly cluttered page table or swap space the slows thing down.  i like to reboot to a clean system when i run upgrades and reboot twice afterwards because some packages like to have some things finish after the next reboot.  and that gets me onto the latest kernel the upgrade brought in.  but i still do all that manually because there is no time i am regularly not using the laptop.

I know that if I don't reboot weekly (or so) that I can't SSH in. It's running in a VM with plenty of RAM and CPU. I'm hoping that weekly restarts of the Plex service will fix the issue.

---

### Post by linuxnoob87 on 2019-11-13
> **TheFu said:**
> ```
# m h  dom mon dow   command
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  *  command to be executed
# *  *  *  *  *  command --arg1 --arg2 file1 file2 2>&1

```
Put that in the crontab that you edit using **crontab -e** as a reminder.

Done and thanks! I'll report back how it goes.

---

### Post by TheFu on 2019-11-13
> **linuxnoob87 said:**
> Done and thanks! I'll report back how it goes.

Hope you realize those are just comments for reminders what each column means. Nothing more.

---

### Post by linuxnoob87 on 2019-11-14
> **TheFu said:**
> Hope you realize those are just comments for reminders what each column means. Nothing more.

I do and thanks (seriously). The service should restart on Sunday; I'll check and see how responsive the server is after that and report back. I copied that data and put it in the crontab file for future reference.

Thanks again!

---

### Post by Skaperen on 2019-11-14
> **linuxnoob87 said:**
> I know that if I don't reboot weekly (or so) that I can't SSH in. It's running in a VM with plenty of RAM and CPU. I'm hoping that weekly restarts of the Plex service will fix the issue.

something is wrong somewhere if it doesn't let you SSH after any number of days of uptime.  most everyone else here knows that and would want to figure out what it is that is wrong.  it could be a misconfiguration in plex or somewhere else.

have you considered the idea of just restarting SSH every week instead of the whole system?

---

### Post by TheFu on 2019-11-14
I run a plex server on 16.04; upgraded it from 14.04 before that.  Never seen anything like this.  I doubt restarting plex will help.  Check the system log files for any warnings or errrors.  Look at the nearby entries to see what is giving issues.  A failing disk with corrupt data can cause all sorts of funky issues.  So can a not-yet-dead PSU.

ssh failures would be a network issue or firewall issue, IME.  I would turn up the logging for all clients and on the server to solve that issue.  

If ssh crashed, I'd physically go to the machine and login there, trying different TTYs until one worked.  If none worked, I'd look at systemd-logind for the issue.

Startup stuff has changed with every recent LTS. We don't know the release of the OS being run.

But that wasn't the question in this thread.

---

### Post by linuxnoob87 on 2019-11-16
> **Skaperen said:**
> something is wrong somewhere if it doesn't let you SSH after any number of days of uptime.  most everyone else here knows that and would want to figure out what it is that is wrong.  it could be a misconfiguration in plex or somewhere else.

have you considered the idea of just restarting SSH every week instead of the whole system?


Would it make more sense to restart SSH or the Plex service weekly?

I've not done much to my install of Ubuntu Server so I don't know why this happens (just that it happens)

---

### Post by TheFu on 2019-11-16
> **linuxnoob87 said:**
> Would it make more sense to restart SSH or the Plex service weekly?

I've not done much to my install of Ubuntu Server so I don't know why this happens (just that it happens)

No.  Restarting services that run fine, indefinitely, for everyone else in the world isn't a solution.  Linux isn't Windows.

Figure out the root cause, fix that.

---

### Post by linuxnoob87 on 2019-11-17
> **TheFu said:**
> No.  Restarting services that run fine, indefinitely, for everyone else in the world isn't a solution.  Linux isn't Windows.

Figure out the root cause, fix that.


Ok. How? 

Linux (specifically Ubuntu) is still very new to me so I've no idea how I'd even begin to troubleshoot this issue. Not trying to be snarky; I legit don't know how I would troubleshoot this.

---

### Post by linuxnoob87 on 2019-11-17
> **TheFu said:**
> I run a plex server on 16.04; upgraded it from 14.04 before that.  Never seen anything like this.  I doubt restarting plex will help.  Check the system log files for any warnings or errrors.  Look at the nearby entries to see what is giving issues.  A failing disk with corrupt data can cause all sorts of funky issues.  So can a not-yet-dead PSU.

ssh failures would be a network issue or firewall issue, IME.  I would turn up the logging for all clients and on the server to solve that issue.  

If ssh crashed, I'd physically go to the machine and login there, trying different TTYs until one worked.  If none worked, I'd look at systemd-logind for the issue.

Startup stuff has changed with every recent LTS. We don't know the release of the OS being run.

But that wasn't the question in this thread.

Running a Plex server on 16.04 as well. What logs would I be looking at (specifically where would they be and what would I be looking for)? The install is running on an ESXi VM so I don't think it's the HDD and the server has redundant power supplies so I don't think it's that either.

The firewall is disabled on the VM. How do I "turn up the logging"?

---

### Post by TheFu on 2019-11-17
> **linuxnoob87 said:**
> Running a Plex server on 16.04 as well. What logs would I be looking at (specifically where would they be and what would I be looking for)? The install is running on an ESXi VM so I don't think it's the HDD and the server has redundant power supplies so I don't think it's that either.

The firewall is disabled on the VM. How do I "turn up the logging"?

On all Unix-like systems, logs are almost always somewhere under /var/log/.
Look for warnings and errors.  I would use **egrep** to search all of them quickly.

Being a VM doesn't prevent disk failures.

How to turn up logging is specific to each program.  You'll need to read the manpage for each, find the section on logging, debugging, or verbosity settings, then do what it says.  For the sshd (server), I think it requires running it manually with the --debug, but I didn't check that. You should.

For ssh clients, getting more details is enabled by adding more 'v's to the connection request.  
```
$ ssh -vvv userid@remote-server
```
more v's gets more details. I've pretty certain about this, but you should check the manpage. Never trust options from people posting on the internet. The difference between a -p and a -P can be huge.

But since this really isn't the same question as the original, a new thread is needed to help the community.
If you feel you know how to schedule automatic reboots now, please use the "thread tools" button near the top and mark this thread as SOLVED - which helps people seeking answers AND helps stop people looking to help from wasting time on already SOLVED problems.

---

