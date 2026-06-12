---
title: "RTL8821AE strikes again, on debian jessie"
date: 2017-04-02
forum: Ubuntu/Debian BASED
---

### Post by pietrod21 on 2017-04-02
```$ uname -aLinux rod 3.16.0-4-686-pae #1 SMP Debian 3.16.39-1+deb8u2 (2017-03-07) i686 GNU/Linux$ lspci | grep -i wireless02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter```[https://ubuntuforums.org/showthread.php?t=2245164](https://ubuntuforums.org/showthread.php?t=2245164) I got problems with wireless card, I already test new firmwares here [https://github.com/lwfinger/rtlwifi_new/](https://github.com/lwfinger/rtlwifi_new/) and more than one network manager - wicd disconnect in like 50 sec (but it seems to work on ubuntu [https://github.com/lwfinger/rtlwifi_new/issues/183#issuecomment-287241143](https://github.com/lwfinger/rtlwifi_new/issues/183#issuecomment-287241143) ), while network-manager take even 3 h, connman doent works at all - anyway, my point is, is there any chance updating the firmware can works also here on debian? anybody test that or solve in another way?

---

### Post by pietrod21 on 2017-04-02
result of using this [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) here [http://paste.ubuntu.com/24299680/](http://paste.ubuntu.com/24299680/)

---

### Post by jeremy31 on 2017-04-02
After seeing all the errors you should look into buying a USB wireless device that is Linux supported or contact Lenovo about a replacement card for your computer, something made by Intel.  It appears that Larry Finger is waiting on Realtek to find a fix for these errors

---

### Post by pietrod21 on 2017-04-02
so the kernel update to 3.18 is not possible?

---

### Post by jeremy31 on 2017-04-02
You could try it

---

### Post by pietrod21 on 2017-04-02
it doesnt change a lot except network-manager take more to respond to inputs now...

---

### Post by pietrod21 on 2017-04-03
no, wait, it seems that the old setting were bad since when i change the ssid name via router interface it now... WORKS PERFECTLY!!!!! and... this is another [SOLVED] one!! :D

---

### Post by yetimon_64 on 2017-04-04
> **pietrod21 said:**
> ... this is another [SOLVED] one!! :D

Could you please mark this thread as [SOLVED] by using the "Thread Tools" drop down menu at the top of your browser window please?
I have a guide for how to do so linked in my profile sig if needed, the middle blue link at the bottom of this post.

Cheers, yeti.:)

---

### Post by pietrod21 on 2017-04-05
uh yes sorry i forgot, tbh though there is an annoying little bug in the network-manager gnome interface where you can't actually click on the seeing button near every AP, if you do that then the interface close... If somebody fix this pls let me know, obviously you can change setting via command line or using wicd or similar if you need btw

---

### Post by pietrod21 on 2017-04-15
new feedback, actually solution works but it seems with udp, or streaming in general it gets some problems, also sometimes it stop working - this happens rarely but happens.

---

