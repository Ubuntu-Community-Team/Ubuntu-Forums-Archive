---
title: "Unattended upgrades and &quot;Aptitude::CmdLine::Assume-Yes&quot;"
date: 2010-05-20
forum: Server Platforms
---

### Post by prlawrence on 2010-05-20
QUESTION
Should I include "Aptitude::CmdLine::Assume-Yes" as a line in /etc/apt/apt.conf.d/10periodic?

DETAILS 
I followed the first option ("Using apt.conf.d") on [https://help.ubuntu.com/community/AutomaticSecurityUpdates/](https://help.ubuntu.com/community/AutomaticSecurityUpdates/) and later received a nice email from the server.  Great!

However, while the email gave no indication of problems, /var/log/unattended-upgrades/unattended-upgrades.log included this line:

```
  2010-05-13 20:54:46,642 WARNING pkg 'openjdk-6-jre-headless' has conffile prompt and needs to be upgraded manually

```

So I tried the second method "in person" as root on the server:
> 
  root@dev-git-001:/var/log# aptitude update
  root@dev-git-001:/var/log# aptitude safe-upgrade -o Aptitude::Delete-Unused=false --assume-yes --target-release `lsb_release -cs`-security


This worked, and openjdk-6-jre-headless seemed to install without any prompts.

So, if these two methods are presented as alternatives on the AutomaticSecurityUpdates community page, should we include the "Aptitude::CmdLine::Assume-Yes" line in the recommended /etc/apt/apt.conf.d/10periodic?

Or am I misunderstanding this issue entirely?

Thanks for your time,
Phil Lawrence

PS - I just saw someone's post saying that one must install update-notifier-common, that it's not enough to simply create /etc/apt/apt.conf.d/10periodic.  Is that true?

---

