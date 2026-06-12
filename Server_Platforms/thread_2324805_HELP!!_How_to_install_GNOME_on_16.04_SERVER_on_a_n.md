---
title: "HELP!! How to install GNOME on 16.04 SERVER on a new SuperMicro Server?"
date: 2016-05-16
forum: Server Platforms
---

### Post by richardchiangpan3 on 2016-05-16
HELP! I just got my first server* and it appears only minimal software  is installed. How do I get the GNOME desktop installed?  Am I required  to install Unity?  Right now, although I have a working Internet  connection, package downloads are not getting installed: every time I  try "sudo apt install moreutils" or "sudo apt-get update" I get multiple  messages concluding: "Temporary failure resolving  'us.archive.ubuntu.com' .  What am I doing wrong?  The server appears  fine: bootup is performed without failure; a standard list of  directories is available.  

  Desperate for help, a Ubuntu 16.04 SERVER newbie. 

*The system: completely standard ZaREason  ZR-130 SuperMicro SuperServer 5018R-M/MR with RAID 1+0, four 1TB harddrives,RJ-45  Internet,& 16GB RAM. I have experience with Ubuntu 16.04 DESKTOP OS but  this is my first SERVER OS and I can not get a start.

---

### Post by sudodus on 2016-05-16
It is straight-forward to install a desktop environment (ubuntu-gnome-desktop) into your server, but you should think twice before doing it.

The best option is to learn the tools that are used by the people who manage servers, because those tools are much lighter and I think also very efficient compared to a desktop environment and GUI tools. If you *must* have a graphical environment, you can either install a light and simple window manager for example fluxbox or openbox, or you can install LXDE or Lubuntu Core. These are lighter than the gnome desktop.

Please wait for replies from real server users before you install any desktop environment :-)

---

### Post by howefield on 2016-05-16
Thread moved to the "*Server Platforms*" forum.

---

### Post by $yl9pAR%t on 2016-05-16
Tasksel is a good starting point to you, IMO. The article below are slightly old but should be helpful.

[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

### Post by nerdtron on 2016-05-16
>  every time I  try "sudo apt install moreutils" or "sudo apt-get update" I  get multiple  messages concluding: "Temporary failure resolving   'us.archive.ubuntu.com' .  What am I doing wrong?  The server appears   fine: bootup is performed without failure; a standard list of   directories is available. 

Does your new installed server have access to internet? This could be a misconfigured network or DNS.

May we know why you need a GUI for? From my perspective a GUI will just slow the server performance and since the GUI has only a few options, you won't configure much on it.

---

