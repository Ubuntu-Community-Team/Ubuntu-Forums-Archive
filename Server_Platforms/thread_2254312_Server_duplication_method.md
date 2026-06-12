---
title: "Server duplication method"
date: 2014-11-26
forum: Server Platforms
---

### Post by DigiAngel on 2014-11-26
Hey all.  So I have similar types of machines here (iMac 20") that I use for Ubuntu servers.  I like to keep one as a backup so I thought I'd share and also invite thoughts on the below method of duping one box to the other.

1.  Install, setup, and configure box #1
2.  Install with same packages and username as box #1 on box #2
3.  Change /etc/ssh/sshd_config to PermitRootLogin yes (will be changed soon) and restart ssh
4.  Stop sql type services then run the below:

```
sudo rsync -avzAXtE --delete --exclude=/etc/fstab --exclude=/boot --exclude=/media --exclude=/dev --exclude=/proc --exclude=/sys --exclude=/mnt --exclude=/var/run --exclude=/run --exclude=/tmp --exclude=/etc/udev/rules.d --exclude=/lib/firmware --exclude=/lib/modules --exclude=/lib/recovery-mode  / root@ip.address.of.box2:/
```

And that's it.  If you reboot you'll have a dup of box #1.  Thereafter I have been doing the below to upgrade/update

1.  Boot box #2 with no network
2.  Run script that stops all services

```
sudo service isc-dhcp-server stop
sudo service postfix stop
sudo service dovecot stop
sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 down
sudo ifconfig eth0 192.168.1.3 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1 metric 1

```

3.  ```
sudo apt-get update && sudo apt-get -y dist-upgrade
```
4.  On box #1 run step 4 from above.

Thoughts?  Thanks.

---

### Post by TheFu on 2014-12-07
Seems reasonable.
After the initial mirror, have you considered just using a devops tool like Ansible to maintain the systems identically?
Also - I've found that if we don't actually swap between 2 redundant systems weekly, things somehow get out of sync and fail when we need to failover most. The weekly swaps are a hassle, but having too much downtime is also bad.

---

