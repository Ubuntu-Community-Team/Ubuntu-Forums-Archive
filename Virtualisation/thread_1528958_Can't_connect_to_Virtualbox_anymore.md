---
title: "Can't connect to Virtualbox anymore"
date: 2010-07-11
forum: Virtualisation
---

### Post by EarthMind on 2010-07-11
I've tried many things in order to get it to work again but it just won't work. eth0 doesn't show up in Virtualbox anymore no matter what I do.

I tried using different virtual adapters, MAC's, reinstalling virtualbox and the host-only adapters, setting the virtual adapter IP and DCHP details manually, etc...

Any help is really appreciated.

---

### Post by Steve603z on 2010-07-11
do you mean that the linux guest OS cannot see eth0, or that you cannot setup bridge mode?

if you mean that the linux guest OS cannot see eth0, try using the command ```
sudo ifup eth0
```

---

### Post by EarthMind on 2010-07-11
I can't set up bridged or host-only adapter mode. I tried "ifconfig eth0 up" but got as error: no such interface, or sometrhing like that.

---

### Post by EarthMind on 2010-07-12
Any more info, please? I really need to get this working asap.

I changed the /etc/network/interfaces file and set IP mode to dynamic and now I always get these errors:
network-interface (eth8) pre-start process (500) terminated with status 1
network-interface (eth8) post-stop process (531) terminated with status 1

---

### Post by EarthMind on 2010-07-12
I solved it.

The "terminated status 1" messages appeared because of a typo in /etc/network/interfaces and the reason why I couldn't connect to Virtualbox anymore and eth0 not showing up is because eth0 changed to eth12 (after all the trying) and I configured /etc/network/interfaces to a static ip but still used eth0 instead of eth12.

Instructions: use iwconfig to check what your virtual adapter card name is and then use "sudo ifconfig ethX up" to enable it. Now reboot your guest OS.

---

