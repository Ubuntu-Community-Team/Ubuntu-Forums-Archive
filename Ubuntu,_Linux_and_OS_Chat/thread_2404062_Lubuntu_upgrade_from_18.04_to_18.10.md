---
title: "Lubuntu upgrade from 18.04 to 18.10"
date: 2018-10-19
forum: Ubuntu, Linux and OS Chat
---

### Post by atannert on 2018-10-19
Hello,

I tried to upgrade lubuntu from 18.04 to 18.10. The upgrade with the normal upgrade manger was no problem. But after restart I get errors. No real desktop environment only a broken menu. Could start some applications but not everything. 

Looks like the upgrade from LXDE to LXQT doesn't work without problems.

I made a clean install afterwards and it worked without problems.

The new (desktop) environment is in a beta state. E.g. the connection to wlan open a console window with a text based config.

The startup time on a old netbook is ok.

I don't think it a stable release.

---

### Post by coffeecat on 2018-10-19
Since this doesn't appear to be a support request,

*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by oldos2er on 2018-10-19
I'm afraid I  have no help to offer other than "this affects me too. " Haven't had time to see if there's a bug report for this yet.

---

### Post by paeschli on 2018-10-19
Here is my experience:

1. I used to have auto log-on on start up enabled on 18.04. Since updating, I'm greeted with a virtual keyboard on start-up. I have to click the pull down button to see the log-in screen.
[[IMG]http://image.noelshack.com/minis/2018/42/5/1539978023-img-20181019-210039.png[/IMG]]("http://image.noelshack.com/fichiers/2018/42/5/1539978023-img-20181019-210039.jpg")
2. (could be because I have a ten year old laptop) The system freezes for 10 seconds after I have put in my password and clicked Enter before showing the desktop. A 'Logging in...' message with a circling icon would be nice while I wait
3. Double applications are mess (Simple scan & Skanlite, Transmission & QTransmission, LXTerminal & QTerminal, QLipper and KLipper...) Is there any way to remove ALL old Lubuntu 18.04 apps that have received a Qt alternative?
4. I have two WiFi icons, one barely visisble. The sound icon and bluetooth icon are also barely visisble.
[http://trackmania-carpark.com/imagespark/odd/up/5bca33007a5d5.png](http://trackmania-carpark.com/imagespark/odd/up/5bca33007a5d5.png)

EDIT: here's the command that removes most unnecessary software 

sudo apt purge leafpad file-roller galculator gpicview xpad xfburn simple-scan mtpaint pidgin sylpheed transmission-gtk abiword evince gnumeric audacious gnome-mpv guvcview pcmanfm gdebi lxterminal hardinfo lightdm lxpanel lxsession obconf gnome-software gnome-disk-utility system-config-printer-gnome lxhotkey-gtk synaptic update-manager lxpolkit lxtask lxshortcut blueman usb-creator-gtk

---

### Post by aXvMh1oi7oW3a on 2018-10-28
mine too plus when i changed my cpu from tf 20 to turion 68 on acer aspire 5516 it doesn't shutdown,reboot,suspend(WAKES UP IMITATIVELY) and     from usb live the 18.10 cant install something about cdrom/casper fs

---

### Post by kansasnoob on 2018-10-29
In the [release notes]("https://lubuntu.me/cosmic-released/") they went as far as saying:

> **The most major and notable problem is that upgrading Lubuntu from 18.04 to 18.10 causes a fair amount of issues**. Therefore, **we are not officially supporting this upgrade path at this time**, however we have prepared [a page in the Lubuntu Manual]("https://manual.lubuntu.me/D/upgrading.html") which can help address the problems that arise after the upgrade.

It's not very stable and I don't expect it to be until maybe 20.04, but Lubuntu 18.04 is supported until April 2021.

---

