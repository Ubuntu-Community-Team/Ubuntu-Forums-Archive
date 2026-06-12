---
title: "No update to 24.04 from 22.04"
date: 2024-07-05
forum: Server Platforms
---

### Post by mandycuba1985 on 2024-07-05
I have a server with Ubuntu 22.04 Jammy, and I am trying to upgrade to 24.04 using do-release-upgrade just as I did from version 20.04 to 22.04. But it always tells me that there is no version available.
Can someone tell me




[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293943&stc=1[/IMG]

---

### Post by Dennis N on 2024-07-05
You are too early to upgrade in one step 22.04 to 24.04. That path is going to be open after the 1st point release (24.04.1). Not yet.
The only upgrade with do-release-upgrade at this time is to 23.10:
```
dmn@Sydney-vm:~$ do-release-upgrade -c
Checking for a new Ubuntu release
New release '23.10' available.
Run 'do-release-upgrade' to upgrade to it.
```
You could upgrade to 23.10, then follow that with an upgrade to 24.04. That is possible, at least until July 11 when 23.10 goes end-of-life.

---

### Post by guiverc on 2024-07-05
The [Ubuntu 24.04 LTS Release notes]("https://discourse.ubuntu.com/t/ubuntu-24-04-lts-noble-numbat-release-notes/39890"), plus [announcements]("https://fridge.ubuntu.com/2024/04/25/ubuntu-24-04-lts-noble-numbat-released/") included the text

> Users of Ubuntu 23.10 will soon be offered an automatic upgrade to  24.04. Users of 22.04 LTS will be offered the automatic upgrade when  24.04.1 LTS is released, which is scheduled for the 15th of August.

That is still in the future, thus the upgrade path isn't open (*except for QA or Quality Assurance testing purpose**s*). Are you wanting a *stable* upgrade (*if so I suggest waiting*) or wanting to help find problems (ie. *QA test*) ?

---

