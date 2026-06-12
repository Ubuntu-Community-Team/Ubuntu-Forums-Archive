---
title: "How to speed up package updates using apt-fast"
date: 2013-04-27
forum: Ubuntu, Linux and OS Chat
---

### Post by tslocum on 2013-04-27
[View tutorial]("http://notblog.org/faster-updates-with-apt-fast/")

apt-fast downloads repositories (package sources) and packages in parallel, which can greatly shorten the time it takes to update a system.  In contrast, the default package manager (apt-get or aptitude) downloads repositories and packages sequentially.  The tutorial linked above explains how to install and configure the tool.

---

### Post by vasa1 on 2013-04-27
See [apt-fast : A Bash Script to Speed Things Along]("http://ubuntuforums.org/showthread.php?t=818619&highlight=apt-fast")

---

### Post by goldshirt9 on 2013-04-27
have used, as long as you remember to use the command it is quick

---

### Post by Lasall on 2013-04-27
Hi,

as a maintainer of apt-fast there is to clarify that APT (apt-get/aptitude/etc.) already uses multiple connections to download packages (if the *Acquire::Queue-Mode "host";* option is enabled - which is the default behavior). This will download packages simultaneously from multiple servers but only one package per server. The improvement of apt-fast (actually the download helper aria2) is to download multiple packages in parallel from a single server.

Btw.: Why to use aptitude over apt-get especially on Debian? (Sorry couldn't resist ;) .)

Regards
Lasall

---

### Post by codingman on 2013-04-28
Meh, apt-fast just seems to 1 ms faster than apt-get.

---

