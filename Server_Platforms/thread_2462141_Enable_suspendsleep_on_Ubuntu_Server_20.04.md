---
title: "Enable suspend/sleep on Ubuntu Server 20.04?"
date: 2021-05-14
forum: Server Platforms
---

### Post by tr00don on 2021-05-14
Hi, I set up Ubuntu Server 20.04 on a home PC and plan to leave it on for hours/days. However, it will seldom run custom, CPU-intensive tasks so I would like to enable suspend and hybrid sleep on this system, if possible; they seem to be disabled by default. Basically, I am looking for the functionality advertised for powernap, a package that seems to have been abandoned/discontinued in this Ubuntu release:

[INDENT][SIZE=3][FONT=courier new][COLOR=#333333][SIZE=2]PowerNap is a configurable daemon that will bring a running system to a lower power state according to a set of configuration preferences. It acts as a sort of "screensaver" for servers, watching the process table for activity rather than the keyboard or mouse.[/SIZE][/COLOR][/FONT][/SIZE][/INDENT]

A Google search for a solution pointed me to "sudo systemctl unmask sleep.target..."; however, this didn't seem to change anything. Then I uncommented the lines in "/etc/systemd/sleep.conf" and rebooted, to no avail. Any suggestions?

---

### Post by LHammonds on 2021-05-14
Maybe something like [this solution](https://askubuntu.com/questions/1256363/shutdown-ubuntu-server-when-idle)?  At the bottom of that page, he has a script to kicks off a shutdown but you could modify it to do a suspend.

Or, if you know for certain the server is not needed between a certain time, you could add a crontab schedule to initiate the suspend.  If crontab still works under suspension, you could have another wake it up the next morning.

However, if you only need this server during those times a CPU-intensive tasks runs, maybe you could add a wakeup script just prior to the task and issue a suspend right after it finishes.  This assumes one can "wake" the server from a schedule on the suspended server.  It is just theory to me cause I've never needed it...my servers are virtual and thus, the host hardware is active regardless of VM activity.

LHammonds

---

### Post by tr00don on 2021-05-14
That script looks great, thank you! I am also curious how to enable the built-in power management features though.

---

### Post by LHammonds on 2021-05-14
Is your ID inspired by the game called Ark: Survival Evolved?  If so, I have an overwhelming urge to run from you.  LoL

LHammonds

---

