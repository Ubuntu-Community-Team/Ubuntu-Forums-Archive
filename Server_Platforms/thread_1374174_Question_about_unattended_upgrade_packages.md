---
title: "Question about unattended upgrade packages"
date: 2010-01-06
forum: Server Platforms
---

### Post by Modeverything on 2010-01-06
Can anyone tell me where on Ubuntu server I can find the name of recent patches/packages installed and the dates when they were installed?  Also, I see under /etc/cron.daily/ there is a script named apt.  It looks like this is the script that is doing the unattended upgrades, is that correct?

I have an Ubuntu BIND server running that I've just recently built.  I've used Ubuntu desktop for a while, but I'm new to the server.  Anyway, when I logged in today after being gone for two weeks, there was a console message saying, "*** System restart required ***".  So I am assuming that Ubuntu server has an auto-patching feature, similar to Windows Automatic Updates, and I figured that it needed to be restarted after applying some of these patches.

So I decided to check the logs to see what may have been installed, and I found a directory named /var/log/unattended-upgrades that contains many dated files, and one named unattended-upgrades.log.  I opened the unattended-upgrades.log file to find a list of upgrade information, however they all say INFO package <name here> not upgraded, or WARNING Package <name here> has conffile prompt and needs to be upgraded manually.

It looks like nothing was actually upgraded, although I still have the System Restart Required prompt.  Why would I have to restart if nothing was upgraded?  I would like to verify whether or not anything has actually been installed.

Thanks in advance!

---

### Post by BkkBonanza on 2010-01-06
/var/log/dpkg.log and older copies with number extensions .1 .2 etc

dpkg is the actual package manager that aptitude and apt-get calls.

---

### Post by Modeverything on 2010-01-06
Ok, I see now.  Thanks for the help!

---

