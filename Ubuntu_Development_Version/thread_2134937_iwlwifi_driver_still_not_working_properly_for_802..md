---
title: "iwlwifi driver still not working properly for 802.11n"
date: 2013-04-12
forum: Ubuntu Development Version
---

### Post by ping-wu on 2013-04-12
The iwlwifi driver is still not working properly for 802.11n.  It may or may not work initially.  If and when it works, the wireless connection will not resume after a suspend.  The only way I have found to work around this problem is to disable the "n" option by creating a file:

/etc/modprobe.d/iwlwifi

which contains the following two lines:

options iwlwifi bt_coex_active=0
options iwlwifi 11n_disable=1

(I don't know wheher the first line is necessary, comment please)

Does anyone know if there is any progress regarding this problem?

---

### Post by screaminj3sus on 2013-04-12
I have no problems with connecting via wireless N, connection dropping or not reconnecting after suspend, but ever since kernel 3.8 I can only get a max of 144mbit on my wireless n (if I downgrade to 3.7 or previous I get 300)

---

### Post by ping-wu on 2013-04-13
My wireless chip is Intel Centrino:

ubuntu@h17:~$ lspci | grep Network
07:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)

What is yours?

---

### Post by screaminj3sus on 2013-04-13
> **ping-wu said:**
> My wireless chip is Intel Centrino:

ubuntu@h17:~$ lspci | grep Network
07:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)

What is yours?

02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)

---

### Post by ping-wu on 2013-04-13
> **screaminj3sus said:**
> 02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)

Ha, same Intel Centrino but actually different versions of Centrino chips, that might explain why the different behavior.

I have noticed that different routers can also different wifi behavior.  My router is Linksys E2500, which actually works better than a previous router (D-LINK DIR655).

---

### Post by Rukiri on 2013-04-13
Are you using a PCI wifi-adapter or USb wifi-adapter?
My personal opinion is to setup a powerline, that way you can just plugin your powerline adapter(has to be an actual outlet) and use a regular ethernet cable.  You'll get more consistent speeds.

---

### Post by ft_ on 2013-04-13
> **Rukiri said:**
> Are you using a PCI wifi-adapter or USb wifi-adapter?
My personal opinion is to setup a powerline, that way you can just plugin your powerline adapter(has to be an actual outlet) and use a regular ethernet cable.  You'll get more consistent speeds.

Ok thanks...
And I complete your personal opinion with [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1112652](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1112652) .
8-[

I use 6205 chip. I experience some slowness with N mode and weak signal (ok with BG mode), but no other issue. Maybe the band frequency does matter (2.4 or 5 GHz) ?
If I set my router to use BG mode only, I do not need some module tweaking.

There are a lot of novelties with kernel 3.9 against iwlwifi. We maybe benefit some backports...

---

### Post by ping-wu on 2013-04-13
> **Rukiri said:**
> Are you using a PCI wifi-adapter or USb wifi-adapter?
My personal opinion is to setup a powerline, that way you can just plugin your powerline adapter(has to be an actual outlet) and use a regular ethernet cable.  You'll get more consistent speeds.

I have done away with desktop PCs, and I don't use a USB wifi-adapter, all my notebooks are using PCI wifi-adapter.

Ideally, we shouldn't use wifi.  My house is extensively wired with ethernet cable; thus I really don't need to use wifi.  However, most people do not have this luxury.  Almost everyone I know (and each of them represents as a potential Ubuntu user) uses wifi.  For me, their interests trump mine.

---

