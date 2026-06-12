---
title: "Server/Box Intermittently Not Responding"
date: 2010-02-20
forum: Server Platforms
---

### Post by martynemworks on 2010-02-20
Hi All,

I have a Ubuntu server that becomes unresponsive after a certain period of "normal" uptime - anything from 2 weeks right down to 1 hour. Lately, it's something like 2 times a day.

I have a dedicated box with Ubuntu 8.04 LTS Minimal (64 bit) installed. The box serves a website and has the following installed on it:
[LIST]
[*]Apache
[*]PHP
[*]MySql
[*]JRE
[*]iptables
[*]SSHD
[*]...
[/LIST]

I also have shell script running on a completely different box every 5 mins just testing to see if a test page can be served by the Apache server. If this fails, an email is sent to me so I know within 5 mins if the box has become unresponsive.

The box hosts a website that has a low-medium load - taking something in the region of 1000 page hits a day.

When it does become unresponsive, the first place I would normally look to are logs in /var/log/ directory. Not much is going on in there. Interestingly, logs seem to stop about an hour before I get an email - indicating that the test page was still being served by the webserver during this period.

After not finding much in the logs, I nohup'd a vmstat, top and free to log files to see what the performance of the system was like. Again not much - CPU virtually idle, no disk IO, memory fine. The logs stopped at the same time as logs in the /var/log dir but the email came an hour or so later.

My next attempt was nohuping tcpdump -A to a log file to see if anything was coming in from the outside world but all seems ok.

Now I am starting to run out of ideas. I'm thinking of moving the site to another server, completely firewall off my box and see what happens. If nothing, then it would indicate something from the outside world is causing a problem. If there are still problems, its a software or hardware problem.

Has anyone had anything similar? What approach did you take to diagnose the problem? Does anyone have any other ideas?

Happy to post log files ...

Please Help!!!

---

### Post by martynemworks on 2010-02-20
Hmm, have been doing some more digging around on this.

I'm not a linux expert by any means but know enough to get by - but it's the deeper things I not so familiar with. (That was my disclaimer for asking the following question!)

Could it be a kernel panic? Is it true that all kernel panics lead to a system freeze?

---

### Post by cariboo on 2010-02-20
Is your system actually freezing up, or is it just networking that stops? You didn't mention whether it was running headless or not.

**Edit** From rereading your post it looks like you have a monitor an keyboard connected to the system, have you retried restarting networking to seem if that makes a difference.

```
sudo /etc/init.d/networking restart
```

---

### Post by martynemworks on 2010-02-21
> **cariboo907 said:**
> Is your system actually freezing up, or is it just networking that stops? You didn't mention whether it was running headless or not.

**Edit** From rereading your post it looks like you have a monitor an keyboard connected to the system, have you retried restarting networking to seem if that makes a difference.

```
sudo /etc/init.d/networking restart
```

It's a dedicated server - I only have remote access to it. I have both SSH and serial console access to the box - both become unresponsive when the system freezes. I would then reboot from the admin web page that the hosting company provide for me.

---

