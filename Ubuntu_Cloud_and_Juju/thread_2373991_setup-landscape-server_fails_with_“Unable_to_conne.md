---
title: "setup-landscape-server fails with “Unable to connect to syslog”"
date: 2017-10-11
forum: Ubuntu Cloud and Juju
---

### Post by wanderer2017 on 2017-10-11
I am trying to get Ubuntu Landscape working.
  I have installed an 16.04.3 LTS server.   As per the instructions for landscape I ran  the following as root 
   add-apt-repository ppa:landscape/17.03
 apt update
 apt install landscape-server-quickstart
  Installation shows the following messages



  ========================================================================    
WARNING: schema upgrade disabled, services might not    restart after an upgrade.    If you are using the 
landscape-server-quickstart package,    setup will be handled for you automatically.    Otherwise, please run 
setup-landscape-server manually after    an upgrade, and read the documentation.
========================================================================

  Job for landscape-package-search.service failed because the control process     exited with error code. See 
"systemctl status landscape-package-    search.service" and "journalctl -xe" for details.

  ========================================================================
  


If I run "setup-landscape-server" command, it fails with "Unable to connect to syslog, exiting" message.

  I updated /etc/rsyslog.conf make sure it was listening on TCP and UDP  ports 514.  I disabled the firewall and AppArmor.  Didn't make a  differece.   Any advice?
  Thanks

---

### Post by deadflowr on 2017-10-12
*Thread moved to **Ubuntu Cloud and Juju***
(This sub-forum also covers landscape issues)

---

