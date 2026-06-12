---
title: "MySQL stopped after upgrading to karmic koala"
date: 2009-11-10
forum: Server Platforms
---

### Post by tkhobbes on 2009-11-10
Hi all, I upgraded to karmic koala yesterday using do-release-upgrade.

During the upgrade, I chose to keep the existing my.cnf configuration... and now mysql does not start anymore. Manually invoking
/etc/init.d/mysql start
results in a [[fail]].

However, /var/log/messages is full of these:
```

Nov 10 22:07:50 eee-box kernel: [ 6223.686375] type=1503 audit(1257887270.326:66): operation="open" pid=3345 parent=3344 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"

```

I think this might have something to do with apparmor or similar, however, I have absolutely no idea how to fix it... can anybody help?

thx, tkhobbes

---

### Post by Vegan on 2009-11-10
Try restarting mysql and see what messages are posted.

---

### Post by tkhobbes on 2009-11-11
Well - the only thing happens is as follows:
```
thomas@eee-box:~$ sudo /etc/init.d/mysql start
[sudo] password for thomas:
 * Starting MySQL database server mysqld                                                                         [fail]

```

And then in /var/log/messages, I have like 20 messages such as the ones above in my first post.... :(

That's all I can find on messages, unfortunately...

---

### Post by tkhobbes on 2009-11-15
*bump* - anyone?

---

### Post by wojox on 2009-11-15
What seems to be the problem? It's started.

---

### Post by t3r0 on 2009-11-15
Hi,

That's AppArmor configuration issue. Configure AppArmor to allow the needed paths or disable it for mysql. 

- Tero

edit: 

To disable apparmor for mysql run $sudo touch /etc/apparmor.d/disable/usr.sbin.mysqld and reload apparmor profiles.

---

### Post by tkhobbes on 2009-11-16
Well - problem seems to be known, here's what I did to solve it finally: [http://www.hobbes.ch/2009/11/mysql-stopped-working-after-update/](http://www.hobbes.ch/2009/11/mysql-stopped-working-after-update/)

---

