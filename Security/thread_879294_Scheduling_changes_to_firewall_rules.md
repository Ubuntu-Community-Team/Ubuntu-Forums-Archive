---
title: "Scheduling changes to firewall rules"
date: 2008-08-03
forum: Security
---

### Post by deadowl on 2008-08-03
First of all, I'm assuming that Firestarter uses iptables. 

In any case, my aunt wants to be able to blacklist certain outgoing internet traffic on her son's computer for certain times of the day. Right now, he either needs to find a job or study to raise his ASVAB scores to the point that he can get into the army, which is being quite the task as he's only in the fourth percentile. Fortunately he's not retarded, just heavily distracted.

I've been attempting to tutor him, giving him some work to do while I'm at work, but whenever I come home he has nothing done and is browsing through MySpace and talking to people on AIM and Yahoo Messenger or some other distraction. The distractions also are preventing him from getting to sleep at a good time to wake up such to look for a job.

I figure using a firewall and rolling out either a blacklist or whitelist for outgoing traffic over time would be the easiest way to prevent him from becoming too distracted without having to do something such as taking the power cord of the computer away when he could still be doing something productive with it, like browsing job websites, emailing potential employers, or studying.

In any case, I'm a newbie to system administration and system security. I don't know how I could schedule the rules to go into/out of effect for specific times of the day. Anyone know of any way of doing this?

---

### Post by The Cog on 2008-08-04
I think you need to write iptables scripts to implement the rules you need. Then use cron to schedule when each script runs adn modified the rules.

You could perhaps use a firewall GUI to set up the rules and then use iptables-save to save the rules when you're happy with them, and use cron to schedule iptables-restore to restore the copy of the appropriate save at the required time.

---

### Post by deadowl on 2008-08-04
Yea, I discovered cron last night and figured out how to use it. I'm currently short on time for what I've heard of iptables having a steep learning curve. 

I thought I might be able to combine cron with the commands "firestarter --stop" and "firestarter --start". That ain't working from crontab for some reason, though my system log is reporting the command to have been called. 

If the GUI is up and I use the gui directly to start/stop the firewall, it will keep that status if I close the GUI. It isn't affected by the crontabbed start/stop commands.

Problem is that I don't see firestarter in ps -e in the first place unless the gui is up, and I need to be able to run it as an administrative service for it to be useful in this context. According to the fs-security website, it should be running as a service automatically.

I don't know. It may have something to do with the computer I'm testing on is running a wireless connection. However, I'm doubtful to that point.


---------------EDIT
I think I should be running /etc/firestarter/firestarter.sh with arguments start or stop?

---

### Post by kevdog on 2008-08-04
It would probably be easier just to edit iptables directly than through firestarter.  If you know the outgoing or incoming ports, then you could block these ports, or simply block all incoming ports for a period of time.  With cron, it could call one "blacklist script" and later at a different time call a "whitelist script" to enable access.

---

