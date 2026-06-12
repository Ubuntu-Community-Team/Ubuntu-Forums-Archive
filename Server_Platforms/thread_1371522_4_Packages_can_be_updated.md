---
title: "4 Packages can be updated"
date: 2010-01-03
forum: Server Platforms
---

### Post by smeerbartje on 2010-01-03
When I logon to my server (9.04) using putty, I see the following screen:

```

Linux server 2.6.28-17-server #58-Ubuntu SMP Tue Dec 1 22:13:36 UTC 2009 x86_64

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

  System information as of Sun Jan  3 20:10:01 CET 2010

  System load: 0.02                Memory usage: 5%   Processes:       96
  Usage of /:  63.5% of 447.70GB   Swap usage:   0%   Users logged in: 0

  Graph this data and manage this system at https://landscape.canonical.com/

4 packages can be updated.
0 updates are security updates.

Last login: Tue Dec 29 21:32:01 2009 from 192.168.1.49

```

However, when I run (in sudo) 'apt-get update; apt-get upgrade', no packages can be installed:

```

rogier@server:~$ sudo apt-get upgrade;
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  landscape-common
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```
Why is that? Why are the four packages which CAN be installed not installed?

---

### Post by BkkBonanza on 2010-01-03
sudo apt-get update

not upgrade...

---

### Post by smeerbartje on 2010-01-03
> **BkkBonaza said:**
> sudo apt-get update

not upgrade...

I did, first UPDATE, then UPGRADE. Here's the outcome:

```

rogier@server:~$ sudo apt-get update;
Hit http://nl.archive.ubuntu.com jaunty Release.gpg
Ign http://nl.archive.ubuntu.com jaunty/main Translation-en_US
Ign http://nl.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://nl.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://nl.archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://nl.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://nl.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://nl.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://nl.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://nl.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://ppa.launchpad.net jaunty Release.gpg
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Hit http://nl.archive.ubuntu.com jaunty Release
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://ppa.launchpad.net jaunty Release
Hit http://security.ubuntu.com jaunty-security Release
Hit http://nl.archive.ubuntu.com jaunty-updates Release
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://nl.archive.ubuntu.com jaunty/main Packages
Hit http://nl.archive.ubuntu.com jaunty/restricted Packages
Hit http://nl.archive.ubuntu.com jaunty/main Sources
Hit http://security.ubuntu.com jaunty-security/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://nl.archive.ubuntu.com jaunty/restricted Sources
Hit http://nl.archive.ubuntu.com jaunty/universe Packages
Hit http://nl.archive.ubuntu.com jaunty/universe Sources
Hit http://nl.archive.ubuntu.com jaunty/multiverse Packages
Hit http://nl.archive.ubuntu.com jaunty/multiverse Sources
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://nl.archive.ubuntu.com jaunty-updates/main Packages
Hit http://nl.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://nl.archive.ubuntu.com jaunty-updates/main Sources
Hit http://nl.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://nl.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://nl.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://nl.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://nl.archive.ubuntu.com jaunty-updates/multiverse Sources
Reading package lists... Done
rogier@server:~$ sudo apt-get upgrade;
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  landscape-common
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
rogier@server:~$

```

---

### Post by BkkBonanza on 2010-01-03
Hmm. Seems like you're up to date then. The info printed at login is output by the "landscape-common" package. Maybe it thinks it needs to be upgraded in order to get the updates as well. Not sure about that.

Is it possible that an update occurred since the login message? What happens if you logout and login again? Does it still say 4 updates are ready?

Maybe landscape reporting is just out of sync.

---

### Post by smeerbartje on 2010-01-03
> **BkkBonaza said:**
> Hmm. Seems like you're up to date then. The info printed at login is output by the "landscape-common" package. Maybe it thinks it needs to be upgraded in order to get the updates as well. Not sure about that.

Is it possible that an update occurred since the login message? What happens if you logout and login again? Does it still say 4 updates are ready?

Maybe landscape reporting is just out of sync.

Problem solved, I had an instance of 'screen' open in the background. After logging out all sessions, the login screen is up-to-date again. Thanks!

---

