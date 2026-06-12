---
title: "Blocking new devices with UDEV?"
date: 2010-10-02
forum: Security
---

### Post by irongeek on 2010-10-02
Hi all,
   I'm trying to figure out how to block the install of new USB hardware in Linux, sort of like how I can do it in Windows:

[http://www.irongeek.com/i.php?page=security/locking-down-windows-vista-and-windows-7-against-malicious-usb-devices](http://www.irongeek.com/i.php?page=security/locking-down-windows-vista-and-windows-7-against-malicious-usb-devices)

I'm using blacklisting Dell stuff by vendor ID as an example, though it's not my end goal I'm just trying to figure out how things work.

I do a "cat /proc/bus/input/devices" to figure out which keyboard is which, then a "udevadm info -a -p /class/input/input10" to probe it for strings I can use in a udev rule. My rule looks like this (I tried two different ones, and commented things out):

ATTRS{idVendor}=="413c", MODE="0000", RUN+="/opt/kde3/bin/kate"
#ATTR{modalias}=="input:b0003v413Cp2106e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw", MODE="0000", RUN+="/opt/kde3/bin/kate"


Neather seems to do anything. Any ideas? I'm also not sure how to make some rules override others. Yes, I've seen [http://www.reactivated.net/writing_udev_rules.html#external-run](http://www.reactivated.net/writing_udev_rules.html#external-run) but it's not really helping me.

Thanks,
Adrian

---

### Post by HermanAB on 2010-10-03
There is a Policykit wizard somewhere in a menu, which makes it dead easy.

---

### Post by irongeek on 2010-10-03
Thanks, I don't remember seeing policykit, but now I know what to Google for and hopefully can fine it. Let me know if anyone else has some ideas.

---

### Post by irongeek on 2010-10-03
Ok, I'm not seeing anything in the wizard about keyboards under user properties, and the wizard is not in the same place as some of the docs I've Googled for in Ubuntu 10.10.

---

### Post by HermanAB on 2010-10-04
Anyhoo, Policykit is how you got to do it, wizard or manual.

---

### Post by irongeek on 2010-10-04
Thanks, but can you give me more details on how I could do it? Old docs point to something called "Authorizations" but that's no longer in the menu system.

Thanks.

---

