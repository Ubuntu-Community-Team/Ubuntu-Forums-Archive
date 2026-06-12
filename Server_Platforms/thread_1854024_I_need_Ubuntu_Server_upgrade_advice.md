---
title: "I need Ubuntu Server upgrade advice"
date: 2011-10-03
forum: Server Platforms
---

### Post by DoRullings on 2011-10-03
Hi

I am currently running Ubuntu 9.04 Jaunty and tried to upgrade to a newer version, but I get this message when I run do-release-upgrade: > An upgrade from 'jaunty' to 'lucid' is not supported with this tool.

Everything is working fine, but this version is no longer supported and all the repository links for applications is broken, so I can not install programs with apt-get and don not get system updates anymore.

I have googled this topic and it seems to me that I have to run a CD image upgrade, and many does advice a clean install. This is a server running several numbers of servers like LAMP, subversion, iTunes, file-server, and so on. The files and configurations files are scattered all over the hard-drive. I have to 1.5 TB hard-drives that is mirrored for because I also use it as a backup-server. What I am trying to say is that it is not just to backup the home folder and  do a clean install. 

What I need is some advice what is best to do. 
1. Should I go for the latest release or should I stay with a 9.xx version. It is a headless server with no graphic card or desktop environment installed. Basic HW is: 
CPU: AMD Athlon(tm) XP 2800+ (I can not remember if it is 32 or 64 bit system, but I am pretty sure it is 32 bit)
System memory: 1536 MiB (3x512 MiB )
Hard drive: 2x1.5 TB with Ext3 file system.
The server run a couple of web-sites, but with little traffic and there is overall very low load on the server.

2. If you think I should go for a clean install of the latest version, I want a version with long term support so I don't get into this situation again. Which version should I go for then?

3. Is there a way to upgrade the current 9.04 version "jaunty" to a 9.xx version with long term support?

4. Any other and better solution(s)?

Thanks guys!

Thomas

---

### Post by snowpine on 2011-10-03
9.04 is "end of life" so I recommend upgrading to 9.10 and then 10.04 (the current "Long Term Support" release). From 10.04 you will be able to go directly to 12.04 (the next LTS) in April 2012.

Instructions for an end of life upgrade:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by DoRullings on 2011-10-03
Thank you snowpine. After reading the article you linked to I will once again consider doing a clean install. After all there are quite a lot of applications I rarely use or do not use at all anymore, and configurations that need some tweaking anyway.

Thanks!

Thomas

---

### Post by arrrghhh on 2011-10-03
> **DoRullings said:**
> Thank you snowpine. After reading the article you linked to I will once again consider doing a clean install. After all there are quite a lot of applications I rarely use or do not use at all anymore, and configurations that need some tweaking anyway.

I **strongly** encourage the clean install route.

It seems like more work at first, but you'll save yourself all the headache of multiple upgrades, and troubleshooting issues that arise from upgrading.

Also, make sure to keep your server up to date - LTS releases are great for this, as you only have to do upgrades every couple of years, instead of every 6 months ;).

---

### Post by DoRullings on 2011-10-04
Thanks arrrghhh! The decision is made. Clean install it is, and I am definitively going to choose the LTS version this time. I've already started making notes about which directories I have to backup. It is three years or so since I installed the last installation. Do I have to set up the Raid (mirror) or can I use the one that I have already set up. If I remember correctly it was quit easy to set it up so it doesn't really matter.

Well guys, thanks for your quick response and for helping me with the decision making. :-)

Best,
Thomas

---

### Post by Jonathan L on 2011-10-04
> **DoRullings said:**
> Thanks arrrghhh! The decision is made. Clean install it is, and I am definitively going to choose the LTS version this time. I've already started making notes about which directories I have to backup. It is three years or so since I installed the last installation. Do I have to set up the Raid (mirror) or can I use the one that I have already set up. If I remember correctly it was quit easy to set it up so it doesn't really matter.

Well guys, thanks for your quick response and for helping me with the decision making. :-)

Best,
Thomas

Hi Thomas

I echo the other people: 10.04 LTS.

But a thought for your finding your configs.  If you're able to make a clean copy (from Live CD or whatever) of /etc and /usr, you can diff them against your real /etc and /usr and it should find all kinds of differences which you can decide to back up, recreate, or discard.

A suggestion for your new system: whenever you first edit a config file, make a copy of it, in the same directory, for example /etc/vsftpd.conf.DIST and when it comes time to make big changes you just look for the .DIST files.  It's pretty pagan and requires discipline but it works rather well.  You'll be happy about it in 2012 (next LTS) or 2015 (end of life of 10.04 LTS) when you decide to change.

Just a thought.

Kind regards
Jonathan.

---

