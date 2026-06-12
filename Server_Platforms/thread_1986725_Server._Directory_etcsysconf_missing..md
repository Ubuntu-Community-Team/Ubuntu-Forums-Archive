---
title: "Server. Directory /etc/sysconf missing."
date: 2012-05-25
forum: Server Platforms
---

### Post by SteeveJobs on 2012-05-25
[LEFT]Hi everybody !

I am trying to install CloudStack on Ubuntu Server.

I tried a minimal installation (no initial service) of Ubuntu 12.04,
 and a WinZip-decompressed archive of CloudStack to install on the first. --> A lot of problems.

Since there, I have installed a Ubuntu Server 10.04 (the one tested for editting the installation manual of CloudStack), and decompressed the archive on it.
-->Almost all my problems were resolved.

I could install the Management Server of Cloud Stack, and its DataBase.

Now, I have to "add the following line at the beginning of the INPUT chain" of the file
**/etc/sysconf/iptables **:
[some code]: **but the directory sysconf is not here, and by this way, its file iptables not, too.**

Could someone of you help me, please ? Why this file is not here; because of the installation of CloudStack ?

Thank you in advance for your answers.

Ref.:
[http://docs.cloudstack.org/CloudStack_Documentation](http://docs.cloudstack.org/CloudStack_Documentation)
(third link).
[/LEFT]

---

### Post by 2F4U on 2012-05-25
Ubuntu does not have a folder /etc/sysconfig. If you want to use iptables, look at this documentation:

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

