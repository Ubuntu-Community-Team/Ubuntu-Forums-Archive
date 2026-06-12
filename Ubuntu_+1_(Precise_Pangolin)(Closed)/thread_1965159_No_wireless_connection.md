---
title: "No wireless connection"
date: 2012-04-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by megabuffen on 2012-04-25
I can't use the wireless connection on my HP Compaq nx7300 running Precise. I've installed the proprietary driver using "Additional drivers" (jockey-gtk).

The expected wireless interface doesn't show up when I run ifconfig. I can only see 'lo' and 'eth1'.

How do I find out what's wrong and fix it?

---

### Post by dino99 on 2012-04-25
install wicd, it might help

---

### Post by megabuffen on 2012-04-25
I installed wicd, but it didn't seem to make a difference. Is there anything in particular I need to do?

---

### Post by dino99 on 2012-04-25
look at ipw3945

[http://superuser.com/questions/59830/how-to-use-ipw3945-on-ubuntu-9-04](http://superuser.com/questions/59830/how-to-use-ipw3945-on-ubuntu-9-04)

[http://www.pc-freak.net/blog/ipw3945-on-kernel-2-6-30/](http://www.pc-freak.net/blog/ipw3945-on-kernel-2-6-30/)

Looks like this chipset needs some driver tweaks, so report a bug against ipw3945 :

ubuntu-bug linux

---

### Post by TBABill on 2012-04-25
Which Broadcom model is it?

---

### Post by megabuffen on 2012-04-25
Broadcom 4311BG, according to [http://h18000.www1.hp.com/products/quickspecs/12614_div/12614_div.HTML](http://h18000.www1.hp.com/products/quickspecs/12614_div/12614_div.HTML)

---

### Post by dino99 on 2012-04-25
look at synaptic and check installation for :
-bcmwl-kernel-source

---

### Post by MARP1961 on 2012-04-25
Is this yet another example of STA driver being installed and not working whereas B43 is not offered but does work with the Broadcom cards?

In the end I did a fresh install and found that selecting 'B43 Firmware Installer' was all I needed. I installed it via Synaptic but you need a wired connection with an ethernet cable for this. Ignore the nagging Additional Drivers.

---

### Post by megabuffen on 2012-04-25
bcmwl-kernel-source is installed.

---

### Post by TBABill on 2012-04-25
> **megabuffen said:**
> bcmwl-kernel-source is installed.
It shouldn't be. Additional drivers offers it, but then sets it up incorrectly. Easiest fix is ```
sudo apt-get install b43-fwcutter firmware-b43-installer
```Once it finishes either restart or ```
sudo modprobe b43
```Wait a few moments, then connect.

---

### Post by MARP1961 on 2012-04-25
I had similar problems and unfortunately found that the installation of the STA driver blocked or blacklisted the B43 one. I got round this by reinstalling and ignoring Additional Drivers and getting B43 Firmware Installer instead. After doing this and rebooting it detected the wifi.

---

### Post by cariboo on 2012-04-25
There is no need to do a complete reinstall to remove the STA driver, just use:

```
sudo apt-get purge bcmwl-kernel-source
```

or install synaptic package manager, and mark the package for complete removal.

---

### Post by terabyte1 on 2012-04-25
You could try stickin' a ethernet wire in the butt-hole of the Router and the other end in the butt-hole of the computer, an if the woody stands to attention and you see the fan in your top-line then its tryin to get through. If this don't happen you could try re-installing it - this sometimes happens an' its just a testing of your patience cos sometimes some gizmo doesn't load properly. Anyway it works for me when I re-install it - the alternative is to upgrade it from your software manager - that often works quicker (Brandy is dandy but Liquor is quicker):lolflag::guitar:! See ya an' good luck!

---

