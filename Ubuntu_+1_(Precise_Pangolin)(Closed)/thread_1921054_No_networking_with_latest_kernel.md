---
title: "No networking with latest kernel"
date: 2012-02-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rv65 on 2012-02-06
I have kernel v3.2.0-14 on my precise install and I do not have any networking after I did the update. I have a Realtek 8111 gigabit lan controller, so I think something in that kernel broke the networking. Any response would be great.

---

### Post by dino99 on 2012-02-06
check /etc/resolv.conf & /etc/network/interfaces

note: i have less trouble using wicd compared to network-manager

---

### Post by rv65 on 2012-02-06
I have nothing in my interfaces. Just the basics.

---

### Post by VinDSL on 2012-02-06
> **dino99 said:**
> note: i have less trouble using wicd compared to network-manager
+1

network-manager hasn't worked for me (wired connection) since I upgraded to Linux 3.2

Wicd works fine...  ;)

---

### Post by cariboo on 2012-02-06
@rv65, make sure you have the correct driver loaded for your device:

```
sudo lshw -C network
```

will give you the needed info.

---

### Post by prusswan on 2012-02-06
If Ubuntu is unable to load the correct default driver for your NIC (such as the case of r8169 driver loaded for r8168 ), then this problem will occur after every kernel upgrade, and you will have to repeat the steps described in [http://ubuntuforums.org/showthread.php?t=1661489](http://ubuntuforums.org/showthread.php?t=1661489) to install the correct driver.

Btw, does anyone know why this issue of wrong default driver is neglected for this long? I encountered this since 10.04 and it looks like it will take more than two LTS for something serious to be done about it. There are a number of bug reports but I will just cite this: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141343](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141343)

---

### Post by varunendra on 2012-02-07
> **prusswan said:**
> If Ubuntu is unable to load the correct default driver for your NIC (such as the case of r8169 driver loaded for r8168 ), then this problem will occur after every kernel upgrade, and you will have to repeat the steps described in [http://ubuntuforums.org/showthread.php?t=1661489](http://ubuntuforums.org/showthread.php?t=1661489) to install the correct driver.
+1

A concise approach by praseodym: [http://ubuntuforums.org/showthread.php?p=11477748#post11477748](http://ubuntuforums.org/showthread.php?p=11477748#post11477748)

If these don't help, please post the outputs of:
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
```

---

