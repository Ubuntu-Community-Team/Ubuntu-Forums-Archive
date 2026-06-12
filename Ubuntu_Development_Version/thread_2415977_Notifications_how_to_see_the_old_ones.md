---
title: "Notifications: how to see the old ones?"
date: 2019-04-03
forum: Ubuntu Development Version
---

### Post by corradoventu on 2019-04-03
Is it possible to review a notification seen on top the screen? Are are the old notifications saved somewhere?
Thanks

---

### Post by Rubi1200 on 2019-04-05
Have you looked under > [COLOR=#111111][FONT=Georgia]/var/log/ [/FONT][/COLOR]?

---

### Post by corradoventu on 2019-04-05
/var/log contains a lot of files and directories..
```
corrado@corrado-p13-dd-0306:~$ ls /var/log 
alternatives.log    btmp.1          gdm3             speech-dispatcher
alternatives.log.1  cups            gpu-manager.log  syslog
apport.log          dist-upgrade    hp               syslog.1
apport.log.1        dmesg           installer        syslog.2.gz
apport.log.2.gz     dmesg.0         journal          syslog.3.gz
apt                 dmesg.1.gz      kern.log         syslog.4.gz
auth.log            dmesg.2.gz      kern.log.1       syslog.5.gz
auth.log.1          dmesg.3.gz      kern.log.2.gz    syslog.6.gz
auth.log.2.gz       dmesg.4.gz      kern.log.3.gz    syslog.7.gz
auth.log.3.gz       dpkg.log        lastlog          unattended-upgrades
boot.log            dpkg.log.1      openvpn          wtmp
bootstrap.log       faillog         private
btmp                fontconfig.log  samba
corrado@corrado-p13-dd-0306:~$ 

```

---

### Post by Rubi1200 on 2019-04-05
Try answer 17 here:
[https://askubuntu.com/questions/105566/is-there-a-way-to-view-notification-history](https://askubuntu.com/questions/105566/is-there-a-way-to-view-notification-history)

[https://prnt.sc/n809ve](https://prnt.sc/n809ve)

Hope this helps.

---

