---
title: "Use a Nokia phone to connect to internet using wvdial"
date: 2010-09-18
forum: Sudan Team
---

### Post by zero-n on 2010-09-18
Before we start connecting to Internet using your phone is not a good way cause it is costly so be **[COLOR=Red]AWARE[/COLOR]** of what you are doing.



I am running [COLOR=DarkOrange]**Ubuntu 10.04 LTS**[/COLOR] & using [[COLOR=Red]**N73**[/COLOR]]("http://en.wikipedia.org/wiki/Nokia_N73") Nokia phone connected with DKU-50 cable.



1- Install wvdial if not installed yet:
```
sudo apt-get install wvdial
```but if you don't have another available way to connect to the Internet :D
no problem, wvdial packages are in Ubuntu CD but not installed by default :-k[INDENT]                 i- so insert you Ubuntu CD & go to this path [COLOR=Red]**pool/main/w/wvstreams**[/COLOR] to install the dependencies.
[/INDENT][INDENT]                 ii- after installing the dependencies go to this path  [COLOR=Red]**pool/main/w/wvdial**[/COLOR]  to install wvdial.


[/INDENT]2- Connect your phone & when prompt select [COLOR=Red]**PC Suite**[/COLOR] Mode so your phone can be recognized as a modem.



3- Run the following command to detect the phone
```
sudo wvdialconf 
```4- Edit your wvdial.conf file which is located in /etc by any preferable editor i will use gedit.```
sudo gedit /etc/wvdial.conf
```5-In /etc/wvdial.conf change**[COLOR=Red] PHONE_NUMBER[/COLOR]**,**[COLOR=Red]YOUR_USERNAME[/COLOR]**,[COLOR=Red]**YOUR_PASSWORD**[/COLOR] to meet your Internet provider settings.
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
ISDN = 0
New PPPD = yes
Modem = /dev/ttyACM0
Phone = PHONE_NUMBER
Username = YOUR_USERNAME 
Password = YOUR_PASSWORD
Baud = 460800

```6- If your service provider using blank username & password enter anything in username & password fields cause wvdial not allowing empty username & password & enable [COLOR=Red]**Stupid mode**[/COLOR] by writing **[COLOR=Red]Stupid Mode = 1[/COLOR]** in /etc/wvdial.conf
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
ISDN = 0
New PPPD = yes
Stupid Mode = 1
Modem = /dev/ttyACM0
Phone = PHONE_NUMBER
Username = YOUR_USERNAME 
Password = YOUR_PASSWORD
Baud = 460800

```

---

### Post by trailblazer_88 on 2011-11-13
Thanks for the link, it worked for me. There is a small catch to be overcome though - your network manager can interfere with wvdial. If mobile broaband it enabled in the network manager applet, wvdial shows the following:
[COLOR=DarkOrange]
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyACM0: Device or resource busy
--> Cannot open /dev/ttyACM0: Device or resource busy
--> Cannot open /dev/ttyACM0: Device or resource busy[/COLOR]

It can be eaisily overcome by disabling mobile broadband under network manager applet in the notifications area.

---

