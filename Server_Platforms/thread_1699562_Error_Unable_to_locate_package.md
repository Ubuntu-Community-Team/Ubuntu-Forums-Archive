---
title: "Error: Unable to locate package"
date: 2011-03-03
forum: Server Platforms
---

### Post by Roseport on 2011-03-03
Ok, another newbie here.  So please be patient.  I have installed the latest server (Ubuntu 10.04).  When I tried (including sudo apt-get update first followed by sudo apt-get install virtinst) I get Unable to locate the package virtinst.  It also did it for a few others as well.  The apt-get update command is successful (on the console it says it is Done).     I have network connection (no proxy) and I am able to ping other systems at home and outside world.  So I don't believe it is network issue.  Any help is greatly appreciated!

---

### Post by uRock on 2011-03-03
Bump for move to Server Platforms.

You will need to edit your sources.list to include whatever PPAs the software you are trying to install come from.

---

