---
title: "Ubuntu 16.04 ufw rule not working after reboot"
date: 2017-08-23
forum: Security
---

### Post by mike4ubuntu on 2017-08-23
Has anybody else had a problem with the ufw where a working rule no longer works after rebooting.  I have ssh on an additionsal port in addition to 22/tcp, say for example 2200, which I have a ufw tcp allow rule for.  It works fine until I reboot.  After the reboot, ufw status has the rule listed as before, but it no longer works.  I have to delete and then re-enter the allow rule for 2200/tcp to get it working again.  Any ideas?

---

### Post by Andreyshel on 2017-08-23
Does ufw actually start?
show 
sudo ufw status 
and
systemctl status ufw
Thanks

---

### Post by mike4ubuntu on 2017-09-05
yes, the firewall starts just fine after every reboot.

```

&#9679; ufw.service - Uncomplicated firewall
   Loaded: loaded (/lib/systemd/system/ufw.service; enabled; vendor preset: enabled)
   Active: active (exited) since Sat 2017-09-02 13:28:24 EDT; 2 days ago
 Main PID: 471 (code=exited, status=0/SUCCESS)
   CGroup: /system.slice/ufw.service

Sep 02 13:28:24 lic4u systemd[1]: Started Uncomplicated firewall.

```

status is fine also, and includes the alternate ssh port just fine.  However, after the reboot, to make the alternate ssh port work, I have to delete it and put it back in.  This only happens with the alternate ssh port.  all other allowed ports in the ufw are fine after the reboot.

---

