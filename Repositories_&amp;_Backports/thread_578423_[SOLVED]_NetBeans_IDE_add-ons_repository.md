---
title: "[SOLVED] NetBeans IDE add-ons repository"
date: 2007-10-17
forum: Repositories &amp; Backports
---

### Post by jemmyyong on 2007-10-17
Hi,

I installed NetBeans IDE from repository "deb [http://download.java.net/ubuntu/](http://download.java.net/ubuntu/) feisty/".   Later I want to install NetBeans IDE add-ons : Mobility Pack, Visual Web Pack, Enterprise Pack, Profiler. Could anyone tell me the repository for NetBeans add-ons ?

Regards,

Jemmyyong

---

### Post by phil- on 2007-10-20
Installing the Visual Web Pack on NetBeans 5.5.1, running on Ubuntu 7.04 AMD 64 - no problem. First make sure your IDE is up to date. Then download, the Visual Web Pack from sun [here]("http://www.netbeans.info/downloads/all.php?b_id=3107") , then follow the instructions found [here]("http://www.netbeans.org/community/releases/55/1/vwp-install.html#install_sollinux") . I chmod +x on the binary, then ran the installer...Everything went fine. When I ran the installer I ran as sudo. And I had to choose my installation directory, the installer, did not choose my location. I installed in /usr/share/netbeans/5.5/ After the installation I reloaded the NetBeans IDE...and Viola! installed.

Hope this helps

phil

---

