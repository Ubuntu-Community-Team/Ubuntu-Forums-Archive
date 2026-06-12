---
title: "Possible to Automate Security Updates/Patches?"
date: 2005-12-08
forum: Server Platforms
---

### Post by jodeet on 2005-12-08
I currently am the system administrator of 20 some Debian-unstable servers.  I am thinking of switching to Ubuntu-server, largely because I haven't found any way to automate applying security updates, let alone even detecting that security updates exist for installed software.

I understand that if I used Debian-stable, or Debian-testing, automation would be possible to at least some extent.  However, I don't want to use those branches of Debian, because the software versions are too old for my needs.

So, does anyone here automate, in part or in whole, the application of security updates to their ubuntu servers?  If so, how, and how well is it working?

Thanks

---

### Post by moment on 2005-12-08
there is a package called "cron-apt" which automates getting updates and installing them via apt.

---

### Post by UbuWu on 2005-12-09
[https://wiki.ubuntu.com/AutoWeeklyUpdateHowTo](https://wiki.ubuntu.com/AutoWeeklyUpdateHowTo)

---

### Post by super-user on 2005-12-09
For this job I have written a small cron.hourly script for me:

```

#!/bin/bash
#
# simple script which does automatic security updates!
# Daniel
#
function warning () {
  echo | mail -s "`uname -n`:$0: error [$1]." user@localhost
}
version=$(cat /etc/apt/ubuntu_version)

apt-get update > /dev/null 2>&1 || warning update
apt-get upgrade -y -t "$version"-security >> /var/log/apt/security.log 2>&1 || warning upgrade.security
apt-get upgrade --trivial-only >> /var/log/apt/trivial.log 2>&1 || warning updade.trivial
apt-get autoclean > /dev/null 2>&1
exit

```

The file "/etc/apt/ubuntu_version" stores the current installed release (I have "breezy" as the only content!). I use this file for my upgrading scripts.

---

