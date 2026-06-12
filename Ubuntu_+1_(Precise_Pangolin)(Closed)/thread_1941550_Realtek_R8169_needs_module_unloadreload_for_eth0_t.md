---
title: "Realtek R8169 needs module unload/reload for eth0 to work"
date: 2012-03-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-03-15
I have just updated PP and, for the first time ever, had a problem with ethernet. It won't find my NIC (OnBoard, Asus MB, details below):

[10:29 PM][ahsl:AL-DESK:~]
$ lspci -vvvv | grep -i ethernet
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

I have tested a couple times here that the r8169 is loaded, nut I got no eth0 in ifconfig. Then if I sudo modprobe -r r8169 && sudo modprobe r8169 eth0 appears and works fine. I can't explain it, but it's fully reproducible at every boot.

It looks like most reports about Realtek Ethernet problems are more serious than this (people can't make the card work). I'm not sure if I should report it, wait a couple days, add to a current report, etc. Does anyone has any experience with the behavior I described here?

Thanks,
Effenberg

---

### Post by Gregory Lee on 2012-03-15
I seem to have the same controller.
```
# lspci -vvvv | grep -i ethernet
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```
I just updated, but I haven't rebooted.  I don't notice a problem.  Yet.

---

### Post by wnelson on 2012-03-15
The correct driver is found here:
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D%28L%29%3Cbr%3ERTL8168C/RTL8111DP](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D%28L%29%3Cbr%3ERTL8168C/RTL8111DP)

Walt

---

### Post by Harry33 on 2012-03-16
> **effenberg0x0 said:**
> I have just updated PP and, for the first time ever, had a problem with ethernet. It won't find my NIC (OnBoard, Asus MB, details below):

[10:29 PM][ahsl:AL-DESK:~]
$ lspci -vvvv | grep -i ethernet
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

I have tested a couple times here that the r8169 is loaded, nut I got no eth0 in ifconfig. Then if I sudo modprobe -r r8169 && sudo modprobe r8169 eth0 appears and works fine. I can't explain it, but it's fully reproducible at every boot.

It looks like most reports about Realtek Ethernet problems are more serious than this (people can't make the card work). I'm not sure if I should report it, wait a couple days, add to a current report, etc. Does anyone has any experience with the behavior I described here?

Thanks,
Effenberg

I have had problems with the very same Realtek card for as long as I have owned it.
From time to time I have to cut the power off from my desktop PC (from the power supply button) in order to get NIC working again. That has always helped, however.

---

### Post by varunendra on 2012-03-16
The RTL8111/8168B PCI Express card and r8169 driver combination is infamous for bad speeds and intermittent connections. It works for a few, but apparently, creates trouble for most of others. Try the r8168 driver instead following this post : [http://ubuntuforums.org/showthread.php?p=11733546](http://ubuntuforums.org/showthread.php?p=11733546)

As mentioned in the post, that thread contains a few more variations of the installation method. The linked one is a tested method, but new bugs keep coming every other day :)
So please try any of them and tell us which one worked for you.

---

