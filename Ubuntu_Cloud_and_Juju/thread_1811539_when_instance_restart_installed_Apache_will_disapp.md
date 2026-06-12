---
title: "when instance restart installed Apache will disappear"
date: 2011-07-25
forum: Ubuntu Cloud and Juju
---

### Post by da vinci on 2011-07-25
After done setup, i try to log in VM by SSH. From VM i try to install Mysql-server and Apache by using apt-get. Then I key-in VM's IP address(192.168.x.x) into web browser and returned a message show that it is working.

Problems :
1) when I key-in same IP (192.168..x.x) from remote PC, its not working

2) when I restart the Instance, whatever i have installed before (Mysgl-server / Apache) all gone, it seems like back to original stage.( tested few times still same).

- Things that installed into VM not permanently store into VM ?? 
- Am i missing anything during installation setup ? or...

:confused::confused::confused:

---

### Post by Rusty au Lait on 2011-07-25
Problem 1 has several causes. Most concern the firewall.

Every instance begins from an image that exists already. What you want requires you to build an image you want when you start an instance. Look here [https://help.ubuntu.com/community/UEC/BundlingImages](https://help.ubuntu.com/community/UEC/BundlingImages)

Answers:
1. yes
2. Does not seem so. You have created and logged into an instance. That sounds like UEC is running.

---

### Post by da vinci on 2011-07-25
yep, UEC is running. The image i use is downloaded from store. but everytime i restart the VM whatever installed will disappear. does anyone try install program and can permanently store into VM ?

---

