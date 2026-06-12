---
title: "Server connectivity Issue.  Help needed!"
date: 2010-10-05
forum: Server Platforms
---

### Post by guessswh0 on 2010-10-05
Hello,

I am having a fairly big issue at the moment and hope that you all can help.  I'm trying to introduce people at work to Ubuntu, and running it as a server.  I have it completely installed on a server box we have.

The only services installed on this box are OpenSSH, Apache, PHP, and MySql, just the very basic LAMP setup.  I have statically assigned it an IP address.

The server worked fine for about 4 days, and now it seems to randomly lose network connectivity.  By that, I mean, I cannot hit it from my workstation.  The only thing it is being used for at the moment is to host a wiki, so this is obviously an issue.  I can walk to the server, and apt-get (to test connectivity) and it works perfectly.  When I am at the server console, I have no issues.  Additionally, when the connectivity goes down, I walk to the server, run an apt-get, and connectivity goes back up.  You'll then be able to hit the server for roughly 30 minutes, and then it goes back down, and requires you to walk to the server again.

I've checked syslog, and there is nothing there.  The only entry is PHP's hourly job that purges active sessions.  I've tried commenting out the job to see if that would work, but it still loses connectivity.

In case it helps at all, this is the syslog entry that is repeated every hour:

Oct  4 17:17:01 [SERVERNAME REDACTED] CRON[2272]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  4 17:39:01[SERVERNAME REDACTED] CRON[2277]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Oct  4 18:09:01 [SERVERNAME REDACTED] CRON[2290]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)

I'm afraid people are going to lose interest in using linux as a viable option for a server OS.  I've never had this problem on any of the other Ubuntu boxes that I've setup as a server.  Can anyone provide some insight?  

Thanks for the help.

---

### Post by CharlesA on 2010-10-05
If it started to randomly start losing connection and there were no changes, I'd look at the NIC to make sure it's not having a problem.

Does the same thing happen if you do a clean install of server with a static ip by default?

---

### Post by guessswh0 on 2010-10-05
the only change that was amde was about a week or so ago with the latest patch for the x64 kernel.  But in syslog, I don't see any kernel panic messages or anything like that.

I don't know if this helps, but I have seen a random entry in syslog saying:

init: tty1 main process ended, respawning

But that's the only other entry.

If it was a NIC issue, wouldn't it not only prevent incoming connections, but also outgoing connections?  At the moment, it seems to randomly block all incoming connections 30 minutes in, but allows outgoing connections (when testing from the console).  I've also double-checked, and there are no ranges being blocked in /etc/hosts.deny

It will just randomly cut out in the middle of a ssh connection and I am unable to reconnect unless I go down to the server and have it run an apt-get (anything that causes it to connect to an outside network.


EDIT: As I see I never posted this before, the server is running 10.04.1


EDIT2:  It looks like I am not the only one having this issue... - [http://serverfault.com/questions/142756/nic-going-to-sleep-on-ubuntu-server-10-04](http://serverfault.com/questions/142756/nic-going-to-sleep-on-ubuntu-server-10-04)

---

### Post by CharlesA on 2010-10-05
Any firewall rules in place?

If the nic was having problems, it shouldn't send any traffic, but I've seen cases where network communication was intermittent.

---

### Post by guessswh0 on 2010-10-05
I have no firewall rules in place on this.  Reason being is that this is already on a protected internal network for internal use only, and also because I wanted to make sure that nothing would be blocked (when I installed it about 2 weeks ago, and just haven't implemented iptables yet).

I just created a script that performs an apt-get when called (as that is the command which seems to restore connectivity, and made a cron job that will run it every 3 minutes.  Hopefully that'll keep the server online until I can find an actual fix.

---

### Post by CharlesA on 2010-10-05
Double post.

---

### Post by CharlesA on 2010-10-05
Nice workaround.

The strange thing is that that fixes the communication issue.

EDIT: Saw yer edit, I guess it's a good thing that you aren't alone.

Too bad there isn't any fix for it outside of using the network to get communication back up and running.

Instead of using apt-get maybe just ping the gateway for 10 count and throw that in a script?

---

### Post by guessswh0 on 2010-10-05
Thanks, figured that it should work as it is what I am currently doing to keep incoming connections alive.

The issue is still going though.  Randomly like every 15 minutes I'll lose connectivity, and then I just have to wait for that script to kick in within two minutes (I cut the cron job from 3 to 2 minutes), and once it runs, connectivity is restored.

I'm really leaning that this is a networking issue, but I'm not 100% sure what it would be.

---

### Post by arrrghhh on 2010-10-05
Is it a fresh install, or has it been upgraded a few times?

Just curious, perhaps as an attempt to triage you can try going back to an older kernel, assuming you have a few to chose from in GRUB.

---

### Post by dtfinch on 2010-10-05
Where I work, someone occasionally gives something a static IP address but forgets to either reserve or exclude the IP from the dhcp address pool, so another computer eventually gets assigned the same IP address, and we start experiencing intermittent loss of connectivity to the system. Could that be your problem? Two systems with the same IP?

---

### Post by guessswh0 on 2010-10-06
This has been only updated once, which was the kernel update.  The other updates have been application updates.

I've discovered that it is exactly every 10 minutes the server loses connectivity.  I have not yet tested if it is 10 minutes from when the server boots, or exactly every ten minutes on a certain minute.

I am really thinking this is some sort of networking issue.  What do you all think?

---

### Post by CharlesA on 2010-10-06
Check to see if cron is running something every 10 minutes.

---

### Post by guessswh0 on 2010-10-06
I looked in hourly, daily, and root cron jobs, and only script running is my script to keep it alive.

---

### Post by CharlesA on 2010-10-06
If there isn't a job running every 10 minutes, then I am not sure what could be causing it.

Out of curiousity, is dhclient running by chance?

---

### Post by arrrghhh on 2010-10-06
> **guessswh0 said:**
> This has been only updated once, which was the kernel update.  The other updates have been application updates.

I've discovered that it is exactly every 10 minutes the server loses connectivity.  I have not yet tested if it is 10 minutes from when the server boots, or exactly every ten minutes on a certain minute.

I am really thinking this is some sort of networking issue.  What do you all think?

Did you try the old kernel...?  Just want to triage this if we can.

---

### Post by guessswh0 on 2010-10-06
> **CharlesA said:**
> If there isn't a job running every 10 minutes, then I am not sure what could be causing it.

Out of curiousity, is dhclient running by chance?


I might be looking in the wrong place, but when doing a ps I don't see dhclient listed.

As for the kernel comment, I could be wrong here, but this is Ubuntu Server, and I didn't know you get grub to prompt you to choose a kernel to load on startup with the Server OS.  On this box, it goes to bios, and then straight to Ubuntu startup without prompting me with anything within GRUB.

---

### Post by CharlesA on 2010-10-06
You have to hold down shift to get it to show the menu. Then select the previous kernel.

if dhclient isn't listed in ps, then it's not running.

---

### Post by free beer and brats on 2010-11-23
I am having the exact same problem with ubuntu server 10.04.1 running on a HP Proliant DL370 G6... External connections are refused until the NIC is 'woken up' by a ping request, etc. from a terminal on the machine. I could ssh in and work for a few minutes, but the shell would freeze and not be rousable until the next internal-to-external request was made from the machine. In annoyance, I set a ping to the gateway with -c 100000 so my ssh session would stay valid while I troubleshoot.  So far that has worked, and I suppose a cron job would as well... but c'mon, that's a bit of an ugly 'solution.'  

Anyone find a better workaround for this?  It's a bit of a deal breaker... Also seems to be common: [http://serverfault.com/questions/142756/nic-going-to-sleep-on-ubuntu-server-10-04]("http://serverfault.com/questions/142756/nic-going-to-sleep-on-ubuntu-server-10-04")

I'm running kernel 2.6.32-24-server, btw, and static IP.  I've been pulling my hair out about this for weeks and finally came to the conclusion it's not a problem with any of my settings.

---

