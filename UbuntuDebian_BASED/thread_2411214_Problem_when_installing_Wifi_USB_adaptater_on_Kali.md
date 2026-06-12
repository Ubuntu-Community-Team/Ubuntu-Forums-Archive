---
title: "Problem when installing Wifi USB adaptater on Kali"
date: 2019-01-27
forum: Ubuntu/Debian BASED
---

### Post by neynd on 2019-01-27
Hello everybody,

After looking for an answer on the forum, I decide to post my problem here. So, I installed Kali on my MacBook pro (Virtual Machine), I have a wifi key from the brand wise Tiger (WT AC9006). After downloading the good drivers and update kali, i wanted to run the installer.sh at first; but impossible, during the installation always the same ERROR:


[FONT=system-ui]Authentication requested [root] for make driver:[/FONT]
[FONT=system-ui]make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.19.0-kali1-amd64/build M=/root/Documents/linux/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51  modules[/FONT]
[FONT=system-ui]make[1]: [FONT=inherit][FONT=inherit]*[/FONT][/FONT] /lib/modules/4.19.0-kali1-amd64/**build** : Aucun fichier ou dossier de ce type. Arrêt.[/FONT]
[FONT=system-ui]make: [FONT=inherit][FONT=inherit]*[/FONT][/FONT] [Makefile:1551: modules] Error 2[/FONT]
[FONT=system-ui]##################################################[/FONT]
[FONT=system-ui]Compile make driver error: 2[/FONT]
[FONT=system-ui]Please check error Mesg[/FONT]
[FONT=system-ui]##################################################
[/FONT][COLOR=#FFFFFF][FONT=system-ui]
[/FONT][/COLOR]And indeed, when I go to check, no file / build

For indication: 
#[FONT=system-ui]cd /lib/modules/4.19.0-kali1-amd64
#ls
#4.19.0-kali1-amd64  4.18.0-kali2-amd64

And with lsusb Kali recognizes my USB adaptater

[/FONT][COLOR=#FFFFFF][FONT=system-ui]
[/FONT][/COLOR]Thank you in advance for your help [COLOR=#FFFFFF][FONT=system-ui]
 [/FONT][/COLOR]

---

### Post by coffeecat on 2019-01-27
*Thread moved to **Ubuntu/Debian BASED** sub-forum.*

---

### Post by oldos2er on 2019-01-27
You should try [https://forums.kali.org/](https://forums.kali.org/) instead.

---

