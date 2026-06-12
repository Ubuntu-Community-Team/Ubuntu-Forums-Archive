---
title: "Local mail not configured for cron jobs"
date: 2009-09-30
forum: Server Platforms
---

### Post by Jerold on 2009-09-30
I am running Ubuntu 8.0.4 LTS 64 bit server edition. I  am only running VMWare server, and some required packages  beyond the base install. (No apache, mail server, LDAP, etc...) And fully updated of course. 

When I ran a somewhat complicated backup script using cron, it would fail. I just recoded the script to direct all stdout output to a file rather than the screen and it appears to be running now. 

It has taken a bit of research to hunt down the problem and send all screen output to a file. While this may be a workaround, the problem still remains that local email is not working.

The user email did not exist in /var/mail so I created root's with touch /var/mail/root. I even set permissions to 777. (That was just a stab in the dark.) From what I have read, local mail should just work with cron jobs, but it doesn't for me on several servers and even a 8.04 test desktop; however, it works fine on my  9.0.4 desktop.

It appears I've missed a configuration step in the installation, or some magic apt-get command, but I haven't the foggiest notion where I went wrong. If anyone has some pointers how I might fix the problem I would very much appreciate the help.

---

