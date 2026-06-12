---
title: "No internet access with Intel wifi's; 7260, 7265, n-2200 or Qualcomm Atheros Ethernet"
date: 2017-03-04
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-03-04
In all 3 cases wifi connects fine, have multiple wifi networks to connect to, all show same poor behavior.
When 1st occurring quite some time ago manually setting up a network fixed, now it's devolved to,

Internet access can be had _once_ per 17.04 install. That would either be on first attempt or after manual setup.
Once logging out or restarting there never will be access again. (at least by connecting to network or connecting & manual setup

Old Report here, may update if I actually boot to 17.04 again. 
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1654918](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1654918)

If anyone has one of these 3 specific wifi devices would be interesting to know if they work. 
Also would be curious about the "bridge device" which never saw before 17.04

---

### Post by cariboo on 2017-03-04
The bridged device is there, because lxd is installed by default on at least Xubuntu and Ubuntu.

**Edit:** I see it's been removed now, so I guess we can get rid of the bridged device.

---

### Post by mc4man on 2017-03-12
User side solution here is to use Google nameservers. Then both wireless & ethernet work fine

---

### Post by jbicha on 2017-03-12
lxd is not currently installed by default in any Ubuntu flavor (except Kylin but that's a bug).

However, if you have indicator-datetime (or Unity8) installed, you might have lxd installed [(LP: #1672178)]("https://launchpad.net/bugs/1672178")

---

