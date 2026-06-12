---
title: "Inspiron 1545 Ubuntu 11.04 wifi don't working"
date: 2011-05-08
forum: Ubuntu Studio
---

### Post by sulliwane on 2011-05-08
Hi there,

I just reinstalled Ubuntu 11.04 on my 1545 laptop, all just gone fine except the WIFI. Just after the fresh install, i was asking to install proprietary driver for boradcom device. I accpet but it gave me an error and asked me to se in the /syslog/jockey.log  !

I ran apt-get :
```
    sudo apt-get remove --purge bcmwl-kernel-source b43-fwcutter
```then restart, and finally launch
```
jockey-gtk
```and accept the proprietary driver, wich this time accepted install fine.

So Here I am, look at this picture :
[IMG]http://55brux.fr/navy[/IMG]
Proprietary driver are installed FINE, it seems that Wifi is recognized well BUT not enabled...?? it's grayed...

I checked "Fn+F2" and tralala...still can't get the WIFI to work.

Here's some command output :
```
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```Thank you in advance, and my apologies for my bad english :o( 

I'm even french, can't be perfect :P

Cheers,

Victor

---

### Post by mikewhatever on 2011-05-08
Try removing and then re-installing bcmwl-kernel-source from the terminal. If that doesn't work, try checking of the module is loaded with 'lsmod' or 'lsmod | grep wl'.

---

### Post by sulliwane on 2011-05-08
I ever tried re-install  "**bcmwl-kernel-source**" in the terminal and it's the same. The installation succeed, but "activate WIFI" is still grayed...

Here you are the command "**lsmod**" output :

```
#lsmod | grep **wl**
**wl**        2642531  0
lib80211    14570  2  lib80211_crypt_tkip,**wl**

 
```

So it seem "**wl**" is well loaded...

Thanks a lot,

Victor

---

### Post by mikewhatever on 2011-05-08
How about the output of
```
rfkill list all
```

You could also try bringing the interface up manually:
```
sudo ifconfig eth1 up
```

---

### Post by sulliwane on 2011-05-08
here's the output :
```
#rfkill list all
0: dell-wifi: wireless LAN
             Soft blocked: yes
             Hard blocked: yes
1: brcmwl-0: Wireless LAN
            Soft blocked: no
            Hard blocked: yes

```

I tried 
```
sudo ifconfig eth1 up 
```
But no change (still grayed).

Thanks !

---

### Post by rickyclarke15 on 2011-05-08
One of the major concerns I have when purchasing my new laptop is the noise created by the fans.

---

### Post by mikewhatever on 2011-05-08
According to rfkill, the wifi is turned off. Are there any switches or buttons to turn it on?
Here is the output I get:
```
0: compal-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: compal-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

Edit:Here is an old discussion, and apparently, F2 worked for some users.
[http://forums.moneysavingexpert.com/showthread.php?t=1436941](http://forums.moneysavingexpert.com/showthread.php?t=1436941)

---

### Post by sulliwane on 2011-05-08
Yes, it definitely seems that a sort of key stay "Blocked" in the wrong position...

But i just have a "Wifi Key" on my laptop as you can see :
[IMG]http://55brux.fr/key.jpg[/IMG]

As you can see, on this keyboard, Dell make the decision to force press on "Fn" before "F1, F2, Fx" key (it's unusual). So in my case, on press on "WIFI key" should activate WIFI (it works like this on my Windows 7 partition).

I can change this behavior in the Bios, so i did just to be sure ..but no change !

ouhhhgaaaaaaaa...things to become crazy !

ps : i've already totally reinstalled my U 11.04 once.

---

### Post by mikewhatever on 2011-05-08
I have a similar keyboard on the Dell mini 10, and the wifi key apparently does nothing as well, while f2 works as expected.
I have to admit that I've no experience with rfkill, but it looks like the syntax is fairly simple. Try the following to unblock all devices:
```
rfkill unblock all
```

I should have asked before, but can you post the output of **lspci |grep -i net** to identify the wireless card.

---

### Post by Murray Wight on 2011-05-08
No real help here, but i run an Inspiron 1545 with 11.04 64bit and ubuntu studio with no wifi problems.

If i run iTunes on Win XP SP2 through VBox, it kills my wifi dead.

Maybe they are related.

P.S. Weird keyboard layout there. Never seen a French one before.

Cheers
Murray

---

### Post by sulliwane on 2011-05-09
OKKayy everyone,

i left my home yesterday so i hadn't been able to give it a try. Today, i called a relation and told him the "instruction", BUT when the computer turned on and ubuntu was launched he told me that "Wireless network are recognized" pop-up appeared !!

so now it works and i don't really know why (it's a little bit frustrating yet :o) in the same way than the majority topics i read concerning WIFI issues on 11.04

When i'll be back to home, i'll investigate a little bit more but i Highly suspect that switching on Win-7 before rebooting on Ubuntu made the trick...

Thanks a lot anyway, for your time and your answers,

See ya !

Victor

ps : In france, we have a common joke about keyboard layout. To demonstrate the superiority of AZERTY upon QWERTY we say : "un clavier AZERTY en vaut deux " => this sentence is inspired of the original one "un homme AVERTI en vaut deux" = "1 person who know worth 2 person" which is equivalent of the english "Forewarned is forearmed" and we plays about **AZERT**Y and **AVERTY** which are two word pretty similar in pronunciation...hope you understood  :D

---

### Post by mikewhatever on 2011-05-09
Well, hope it works from now on.
Anyway, keep us posted.

---

### Post by pkchancey009 on 2011-05-10
I'm running Ubuntu 11.04 (2.6.38-8-generic-pae) on a DELL Insipirion 1525 and my wifi is not working, I have a the Broadcom bcm4312 LP-PHY wireless card. I have taken these measues as listed in Ubuntu forums..

[LIST=1]
[*]Removed Natty's Broadcom kernel 5.100.82.38 and replaced it with Meerkat's 5.60.48.36 which was installed with gDebi.
[/LIST]
Please assist, thanks in advance!

---

### Post by mikewhatever on 2011-05-10
Hi pkchancey009,
according to the screenshot, you have two different wireless drivers installed which may cause problems.
One is **bcmwl-kernel-source**, and the other **b43-fwcutter firmware-b43-lpphy-installer**. Chose the on driver you want to use and remove the other.

---

