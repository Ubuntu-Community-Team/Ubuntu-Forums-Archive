---
title: "Need my server to always reboot instead of shutdown."
date: 2020-03-20
forum: Server Platforms
---

### Post by acenova on 2020-03-20
I recently set up an Ubuntu server in my home for running game servers for myself and my friends. I have already set up the BIOS to automatically boot when it receives power, so it can recover from power outages, but I also want it to be recoverable for when I inevitably type "sudo shutdown now" and forget the "-r".

After some googling, I installed molly-guard, which adds an extra layer of confirmation, but I still want the server to be absolutely idiot proof.

I was also able to find lots of people with the complete opposite problem; trying to shut down their Linux machine caused it to reboot, but I won't claim to be enough of a Linux wizard to apply those solutions to my problem.

I'm open to any suggestions, even if it just means something like "alias shutdown='shutdown -r'" (although something a little more robust would be nice)

Thanks in advance!

---

### Post by TheFu on 2020-03-20
Unix systems have this problem.  They do what we tell them to do.

I&#8217;d use **sudo reboot** instead.
Plus systemd is taking over, so there are different commands for stuff now.

---

### Post by LHammonds on 2020-03-29
+1 for using "sudo reboot" instead.  Do not try to remap the shutdown command.

You could also use a script rather than doing it by hand...which is prone to mistakes such as syntax and not stopping certain services in the right order, etc.

I have managed 100+ servers and MUCH prefer setting up a script for every machine I manage so that it handles the machine-specifics via a common script name...then package it up inside a menu for easy access.

For example, I have the following scripts:

reboot.sh
shutdown.sh
servicestop.sh
servicestart.sh
servicerestart.sh

The critical bits are in servicestart.sh and servicestop.sh such as the commands to stop web services, database services, file syncs, etc. that need to happen every time the services are stopped or started.

The servicerestart.sh simply calls the stop and start scripts
The shutdown script calls the stop script and then issues the shutdown and poweroff command
The reboot script calls the stop script and then issues the reboot command

You can use the "dialog" program to build a menu which calls these typical high-level commands for each and every server.  They can all look exactly the same from the operator menu but what is done to stop/start services can differ depending on what the server does.

To see an example of this "operator menu" can you can see it on my [How to Install Ubuntu Server](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=244#p624) thread.

LHammonds

---

### Post by acenova on 2020-03-30
Thanks for the advice! I'll probably go with a few scripts to shut things down then, and I'll make use of "sudo reboot" for sure.
I'm only running a few independent game servers (so far, anyway), so I'm not sure I'll need a servicestop.sh, but I might as well set up a blank one for later. As for *starting *services, I've just got a cron job for each one on its own user.

---

