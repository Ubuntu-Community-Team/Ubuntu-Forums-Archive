---
title: "Try update Ubuntu 14 to 16 and reboot --&gt; no more ssh / ufw don't work / no ping"
date: 2019-05-02
forum: Server Platforms
---

### Post by axelgraphikchannel on 2019-05-02
[FONT=arial][COLOR=#4E4E4E]Hi guys, I'm pretty desperate.](*,)[/COLOR]
[COLOR=#4E4E4E]
[/COLOR]
[SIZE=4][COLOR=#4E4E4E]**WHAT I HAVE DONE :**[/COLOR][/SIZE]
[COLOR=#4E4E4E]
[/COLOR]
[COLOR=#4E4E4E]This week I try an **update for my distant server from ubunut 14 to ubuntu 16 with** :[/COLOR]
```
[COLOR=#4E4E4E]/opt/psa/bin/distupgrade.helper.ubt14-ubt16.x64.sh
[/COLOR]
```[COLOR=#4E4E4E]Then the tuto say reboot so I reboot.[/COLOR][COLOR=#4E4E4E]
[/COLOR]
```
[COLOR=#4E4E4E]php7.0-fpm start/running, process 25291[/COLOR]
[COLOR=#4E4E4E]   Please reboot the server and run the following command /opt/psa/bin/distupgrade.helper.ubt14-ubt16.x64.sh to continue.[/COLOR]
[COLOR=#4E4E4E]   STOP Distupgradre[/COLOR]

```[COLOR=#4E4E4E]
[/COLOR]
[SIZE=4][COLOR=#4E4E4E]**WHAT I HAVE NOW:**[/COLOR][/SIZE]
[COLOR=#4E4E4E]
[/COLOR]
[COLOR=#4E4E4E]- **ping **don't return ](*,)](*,)[/COLOR]
[COLOR=#4E4E4E]- **ssh **say **connection Time out** [https://i.stack.imgur.com/NFexe.png]("http://https//i.stack.imgur.com/NFexe.png") :confused:[/COLOR]
[COLOR=#4E4E4E]
[/COLOR]
[COLOR=#4E4E4E]
[/COLOR]
[COLOR=#4E4E4E]When I launch _**rescue mode**_ and access via ssh to a linux image (I choose an ubuntu 14) on my distant server :[/COLOR]
[COLOR=#4E4E4E](By the way when I connect with rescue mode I do :[/COLOR]
[/FONT]```
[FONT=arial][COLOR=#4E4E4E]sudo su[/COLOR]
[COLOR=#4E4E4E]mountall.sh[/COLOR]
[COLOR=#4E4E4E]chroot /mnt/sda2 bin/bash[/COLOR]
[/FONT]
```[FONT=arial][COLOR=#4E4E4E] )[/COLOR]
[COLOR=#4E4E4E]
[/COLOR]
[COLOR=#4E4E4E]- **ufw status**: ```
iptables v1.4.21: can't initialize iptables table `filter': Table does not exist
```[/COLOR]
[COLOR=#4E4E4E]- **uname - a** : ```
Linux 62-210-253-46 4.2.0-35-generic #40~14.04.1-Ubuntu SMP Fri Mar 18 16:37:35 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```[/COLOR]
[COLOR=#4E4E4E]- **lsb_release -a** : [/COLOR][/FONT]```
[FONT=arial][COLOR=#4E4E4E]No LSB modules are available.[/COLOR]
[COLOR=#4E4E4E]Distributor ID: Ubuntu[/COLOR]
[COLOR=#4E4E4E]Description:    Ubuntu 14.04.6 LTS[/COLOR]
[COLOR=#4E4E4E]Release:        14.04[/COLOR]
[COLOR=#4E4E4E]Codename:       trusty[/COLOR][/FONT]
```[FONT=arial]
[COLOR=#4E4E4E]- **ls -lh /lib/module **: ```
total 8,0K drwxr-xr-x 5 root root 4,0K avril 30 09:55
```[/COLOR]```

[COLOR=#4E4E4E]   3.13.0-169-generic drwxr-xr-x 5 root root 4,0K juil. 23  2015 3.13.0-58-generic[/COLOR]

```
[COLOR=#4E4E4E]- I have often the message can't resolve hostname IP-IPI-IPI-IP , but I check hostname and host (could show you content if you want)[/COLOR]
[COLOR=#4E4E4E]- In **syslog **I have a message : ```
apparmor="DENIED" operation="sendmsg" profile="/usr/sbin/named" name="/run/systemd/journal/dev-log" p
```[/COLOR]
[COLOR=#4E4E4E]- **ip address** :[/COLOR]
```

[COLOR=#4E4E4E]1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default[/COLOR]
[COLOR=#4E4E4E]    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00[/COLOR]
[COLOR=#4E4E4E]    inet 127.0.0.1/8 scope host lo[/COLOR]
[COLOR=#4E4E4E]       valid_lft forever preferred_lft forever[/COLOR]
[COLOR=#4E4E4E]    inet6 ::1/128 scope host[/COLOR]
[COLOR=#4E4E4E]       valid_lft forever preferred_lft forever[/COLOR]
[COLOR=#4E4E4E]2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000[/COLOR]
[COLOR=#4E4E4E]    link/ether 0c:c4:7a:0e:9f:da brd ff:ff:ff:ff:ff:ff[/COLOR]
[COLOR=#4E4E4E]    inet 62.210.253.46/24 brd 62.210.253.255 scope global eth0[/COLOR]
[COLOR=#4E4E4E]       valid_lft forever preferred_lft forever[/COLOR]
[COLOR=#4E4E4E]    inet6 fe80::ec4:7aff:fe0e:9fda/64 scope link[/COLOR]
[COLOR=#4E4E4E]       valid_lft forever preferred_lft forever[/COLOR]
[COLOR=#4E4E4E]3: eth1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000[/COLOR]
[COLOR=#4E4E4E]    link/ether 0c:c4:7a:0e:9f:db brd ff:ff:ff:ff:ff:ff[/COLOR]

```
[COLOR=#4E4E4E]- **cat /etc/network/interface   so you see here it's em1 than eth0 above**[/COLOR]
```

[COLOR=#4E4E4E]# The loopback network interface[/COLOR]
[COLOR=#4E4E4E]auto lo[/COLOR]
[COLOR=#4E4E4E]iface lo inet loopback[/COLOR][COLOR=#4E4E4E]
[/COLOR]
[COLOR=#4E4E4E]# The primary network interface[/COLOR]
[COLOR=#4E4E4E]auto em1[/COLOR]
[COLOR=#4E4E4E]iface em1 inet dhcp[/COLOR]

```

-** systemclt or everything else with clt** : ```
Failed to connect to bus: No file or folder find
```

[COLOR=#4E4E4E]And as I said, I was in **an update process**, so after the reboot I have to re launch the command ```
/opt/psa/bin/distupgrade.helper.ubt14-ubt16.x64.sh
``` so I'm a bit afraid of install stuff like ```
apt-get install lsb-core
```[/COLOR][COLOR=#4E4E4E]
[/COLOR]
[COLOR=#4E4E4E]Many many many thanks for your help ![/COLOR][/FONT]

---

### Post by slickymaster on 2019-05-02
Thread moved to **Server Platforms** for a better fit

---

### Post by TheFu on 2019-05-03
I have no idea what /opt/psa/bin/distupgrade.helper.ubt14-ubt16.x64.sh  is. It is not the method used to upgrade 14.04 to 16.04 on Ubuntu systems.
Performing system updates between major releases shouldn't be performed over a network connection. It should only be done using the console.

**I would restore from the backup I made just prior to the upgrade effort, gain console access, then follow approved Canonical upgrade procedures.**

The remaining comments below really doesn't matter if you restore from backup.
Running 
```
sudo su
mountall.sh
chroot /mnt/sda2 bin/bash
```
without context doesn't tell us much.

In rescue mode, you already are root.
Never heard of mountall.sh. It isn't on any of my Ubuntu servers. Must be something specific to your setup or is that something in the normal rescue mode?
Setting up a chroot requires more than just that command.  I'd have to look it up, but it would be about 5-7 commands, I think.

16.04 switched to systemd.  eth0 is gone.  The driver used for the NIC determines the naming for each ethernet device.  Usually they are unique and based on the MAC of the device. It is a new world.

Before doing a system upgrade like this on a production system, always run a few test runs in virtual machines first, so you can iron out any difficulties and not impact production. Always, always, have a know-you-can-restore backup before doing such high risk activities.  Upgrading an OS from version to version is like swapping out the engine for a car or doing open heart surgery.  Would you 'wing-it' for either of those tasks?

If an upgrade fails along the way, the only recovery is to start over. Otherwise, you'll never be able to trust the system.

I get that you are frustrated. Upgrades for systems with zero customizations generally don't break when following the suggested upgrade methods, assuming there aren't file corruption or hardware issues.  Please check the system log files for any issues.

---

