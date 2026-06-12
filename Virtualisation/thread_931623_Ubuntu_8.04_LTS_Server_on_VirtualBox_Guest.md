---
title: "Ubuntu 8.04 LTS Server on VirtualBox Guest"
date: 2008-09-27
forum: Virtualisation
---

### Post by c.monty on 2008-09-27
hi!
when starting new installation of Ubuntu 8.04 LTS Server on VirtualBox Guest I get this error:
This kernel requires the following features not present on the CPU: 0:6

This error is related to wrong linux kernel, and several instructions ([http://burnz.wordpress.com/2008/09/04/how-to-setup-headless-xvm-virtualbox-on-ubuntu-server/]("http://burnz.wordpress.com/2008/09/04/how-to-setup-headless-xvm-virtualbox-on-ubuntu-server/") or [http://ubuntuforums.org/showthread.php?p=4813109]("http://ubuntuforums.org/showthread.php?p=4813109")) tell me to install different linux kernel by booting from CD in rescue mode.

Everything is working unless command
apt-get install

I get this information:
bash: apt-get: command not found

How can I install new kernel if apt-get is not available?

---

