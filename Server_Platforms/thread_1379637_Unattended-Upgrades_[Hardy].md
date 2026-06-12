---
title: "Unattended-Upgrades [Hardy]"
date: 2010-01-12
forum: Server Platforms
---

### Post by spongypants23 on 2010-01-12
Hi guys!

I'm having a little bit of trouble getting unattended-upgrades to work. I installed it via apt-get, as one would normally do.

...But it's not doing anything. There are no log files, and my server has been running online for 13 days. I've had to do manual updates... which is not really ideal.

I'm not really sure what's going on, nor how this works. I thought it was all automatically configured by dkpg when I used apt-get? I'm not sure if I have to do manually fiddle with cron files... or something. It's rather important that the server stay working.
[I]
What do I do, oh gurus of computer wisdom?[/I]

P.S. I've seen guides where you put cron jobs for apt-get update && apt-get upgrade. That's not really what I'm looking for. I like unattended-upgrades because it will email me when something's not right, and I can look at the logs easily.

Edit: Whoops, I might want to say that I'm running Ubuntu Server 8.04 (Hardy) on it.

---

### Post by barnex on 2010-01-13
Is it possible that automatic updates only installs *security* updates automatically and still let's you do the rest manually?

---

### Post by spongypants23 on 2010-01-13
> **barnex said:**
> Is it possible that automatic updates only installs *security* updates automatically and still let's you do the rest manually?

No. There would be logs of it, and there are none.

Although I've configured it to install from hardy-security and hardy-updates... But it doesn't want to.

---

### Post by jocampo on 2010-01-13
This may not help your question directly but I do not think automatic upgrades for a Server is a good idea. Servers (Linux and Windows) should be upgraded or apply patches in a controlled way which is manually; we never update our servers (Unix, Linux and Windows) in the company I work for, automatic way and we have thousands of servers; we do for laptops and clients but that's a different story. If things go wrong and you have scripts for updates you have no way to stop or check what happened.

---

### Post by inphektion on 2010-03-10
I had same question you did...
if you never figured it out you are missing a package which gives you the 10periodic file needed.  I had orig just created this file myself thinking the apt cron read it somehow.  anyway do the following:

aptitude install update-notifier-common
change your /etc/apt/apt.conf.d/10periodic to: 
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "5";
APT::Periodic::Unattended-Upgrade "1";

---

