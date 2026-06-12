---
title: "Ubuntu Server 16.04..4 LTS very long reboot"
date: 2018-03-27
forum: Server Platforms
---

### Post by Wojciech_Marusiak on 2018-03-27
Hello, 


On my Ubuntu Server I am running nginx with mysql with wordpress on top. 


Today while troubleshooting nginx/wordpress 503 errors (I did increase some upload values and timeouts) I started to notice that my server reboot time is extremly long.


I did following troubleshooting
```

**systemd-analyze **
Startup finished in 1.517s (kernel) + 10.312s (userspace) = 11.830s

```


```

**systemd****-analyze blame**
          4.025s cloudmonitor.service
          3.819s cloud-init-upgrade.service
          3.470s mysql.service
          2.096s cloud-init.service
          1.948s php7.0-fpm.service
          1.182s aegis.service
          1.094s dev-vda1.device
          1.006s nginx.service
           820ms cloud-config.service
           796ms apparmor.service
           795ms cloud-final.service
           774ms cloud-init-local.service
           585ms systemd-journal-flush.service
           394ms grub-common.service
           389ms ecs_mq.service
           318ms networking.service
           309ms accounts-daemon.service
           309ms systemd-logind.service
           292ms agentwatch.service
           289ms irqbalance.service
           277ms console-setup.service
           263ms ntp.service
           231ms sysstat.service
           218ms keyboard-setup.service
           212ms systemd-journald.service
           203ms rsyslog.service
           183ms systemd-tmpfiles-setup-dev.service
           168ms resolvconf.service
           155ms systemd-sysctl.service
           103ms ondemand.service
            99ms systemd-udev-trigger.service
            93ms systemd-tmpfiles-setup.service
            88ms systemd-udevd.service
            82ms dev-mqueue.mount
            80ms sys-kernel-debug.mount
            79ms dev-hugepages.mount
            78ms setvtrgb.service
            77ms rc-local.service
            71ms kmod-static-nodes.service
            28ms user@0.service
            26ms systemd-user-sessions.service
            24ms plymouth-read-write.service
            24ms ssh.service
            23ms systemd-random-seed.service
            15ms systemd-modules-load.service
            15ms ufw.service
            12ms plymouth-quit.service
             8ms plymouth-quit-wait.service
             7ms systemd-update-utmp.service
             5ms systemd-remount-fs.service
             4ms systemd-update-utmp-runlevel.service
             2ms sys-fs-fuse-connections.mount

```
**dmesg**
[https://paste.ubuntu.com/p/f3FbvtRvYq/](https://paste.ubuntu.com/p/f3FbvtRvYq/)


**Syslog full reboot cycles**
[https://paste.ubuntu.com/p/SZRg2nHzM8/](https://paste.ubuntu.com/p/SZRg2nHzM8/)


**kernel log from two max_cycles**
[https://paste.ubuntu.com/p/7PfVYfJVVh/](https://paste.ubuntu.com/p/7PfVYfJVVh/)

---

### Post by Wojciech_Marusiak on 2018-03-28
Anyone?

---

### Post by slickymaster on 2018-03-28
*Thread moved to **Server Platforms**.*

---

### Post by Wojciech_Marusiak on 2018-03-28
> **slickymaster said:**
> *Thread moved to **Server Platforms**.*
Thanks for moving it to correct section.

---

