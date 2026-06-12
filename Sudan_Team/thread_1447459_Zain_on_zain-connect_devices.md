---
title: "Zain on zain-connect devices"
date: 2010-04-05
forum: Sudan Team
---

### Post by yasir.elsharif on 2010-04-05
Hello Team Sudan,
I have an issue with zain connect device. If any of you have tried it please help.
With Ubuntu 9.10, zain-connect works fine in terms of connecting to the internet, but if you have tried it with windows: you can send/receive SMS, view/change contacts and even make phone calls from your pc. so I am trying to get these features in my ubuntu.
I knew that umtsmon do all these things. but <again> it couldn't be installed on my ubuntu.
So guys if one of you have an idea on how to tweak that, please help
Yasir

---

### Post by zero-n on 2010-04-05
You can download it from here as a .deb package:
[COLOR=Red]**[http://debian.die-welt.net/umtsmon/umtsmon_0.8+dfsg-1_i386.deb](http://debian.die-welt.net/umtsmon/umtsmon_0.8+dfsg-1_i386.deb)**[/COLOR]

This is not the latest version the latest version is .10

i hope it will work with you

salam

---

### Post by yasir.elsharif on 2010-04-06
Thanks Zero-n
I tried it and again the same error:
umtsmon: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
also I prefer the 64-bit version 'cause my system is.
Thanks anyway
Yasir

---

### Post by zero-n on 2010-04-06
This command will solve the problem of **[COLOR=Red]libqt-mt.so.3[/COLOR]**:

```
sudo apt-get install libqt3-mt
```
& this is a .rpm package from Open Suse:
[http://download.opensuse.org/repositories/openSUSE:/11.2/standard/x86_64/umtsmon-0.9.72.20090509-3.1.x86_64.rpm](http://download.opensuse.org/repositories/openSUSE:/11.2/standard/x86_64/umtsmon-0.9.72.20090509-3.1.x86_64.rpm)

you can use alien to make a .deb file

i am not sure that i can work but i hope so

salam

---

### Post by Adntu on 2010-04-06
[right][size="4"]&#1575;&#1604;&#1587;&#1604;&#1575;&#1605; &#1593;&#1604;&#1610;&#1603;&#1605;
&#1575;&#1584;&#1575; &#1605;&#1575; &#1591;&#1608;&#1604; &#1605;&#1593;&#1575;&#1603; &#1575;&#1604;&#1575;&#1608;&#1576;&#1606;&#1578;&#1608; 64 &#1583;&#1607; &#1601;&#1575;&#1606;&#1575; &#1576;&#1606;&#1589;&#1581; &#1575;&#1606;&#1603; &#1578;&#1606;&#1586;&#1604; 32, 64 &#1576;&#1583;&#1582;&#1604;&#1603; &#1601;&#1610; &#1581;&#1578;&#1575;&#1578; &#1605;&#1575; &#1608;&#1575;&#1587;&#1593;&#1577;
&#1578;&#1581;&#1610;&#1575;&#1578;&#1610;[/size][/right]

---

### Post by zero-n on 2010-04-06
> **Adntu said:**
> [RIGHT][SIZE=4]&#1575;&#1604;&#1587;&#1604;&#1575;&#1605; &#1593;&#1604;&#1610;&#1603;&#1605;
&#1575;&#1584;&#1575; &#1605;&#1575; &#1591;&#1608;&#1604; &#1605;&#1593;&#1575;&#1603; &#1575;&#1604;&#1575;&#1608;&#1576;&#1606;&#1578;&#1608; 64 &#1583;&#1607; &#1601;&#1575;&#1606;&#1575; &#1576;&#1606;&#1589;&#1581; &#1575;&#1606;&#1603; &#1578;&#1606;&#1586;&#1604; 32, 64 &#1576;&#1583;&#1582;&#1604;&#1603; &#1601;&#1610; &#1581;&#1578;&#1575;&#1578; &#1605;&#1575; &#1608;&#1575;&#1587;&#1593;&#1577;
&#1578;&#1581;&#1610;&#1575;&#1578;&#1610;[/SIZE][/RIGHT]



what you mean by this ?

try to be specific in responding to a thread

---

### Post by Adntu on 2010-04-06
[size="4"][right]> **zero-n said:**
> what you mean by this ?

Try to be specific in responding to a thread
&#1581;&#1575;&#1590;&#1585; &#1610;&#1575; &#1586;&#1610;&#1585;&#1608;-&#1575;&#1606;, &#1587;&#1575;&#1602;&#1608;&#1605; &#1576;&#1575;&#1593;&#1575;&#1583;&#1577; &#1603;&#1578;&#1575;&#1576;&#1577; &#1585;&#1583;&#1610;:

&#1575;&#1604;&#1587;&#1604;&#1575;&#1605; &#1593;&#1604;&#1610;&#1603;&#1605; &#1575;&#1582;&#1610; &#1610;&#1575;&#1587;&#1585; &#1575;&#1604;&#1588;&#1585;&#1610;&#1601;
&#1575;&#1584;&#1575; &#1604;&#1605; &#1578;&#1603;&#1606; &#1578;&#1587;&#1578;&#1582;&#1583;&#1605; &#1575;&#1608;&#1576;&#1606;&#1578;&#1608; &#1575;&#1604;&#1605;&#1582;&#1589;&#1589; &#1604;&#1605;&#1593;&#1605;&#1575;&#1585;&#1610;&#1577; 64 &#1576;&#1578;&#1575;&#1611; &#1604;&#1608;&#1602;&#1578; &#1591;&#1608;&#1610;&#1604; &#1608;&#1589;&#1575;&#1585; &#1605;&#1606; &#1575;&#1604;&#1589;&#1593;&#1576; &#1575;&#1593;&#1575;&#1583;&#1577; &#1578;&#1606;&#1589;&#1610;&#1576; &#1575;&#1604;&#1606;&#1592;&#1575;&#1605; &#1601;&#1575;&#1585;&#1580;&#1608; &#1575;&#1606; &#1578;&#1581;&#1584;&#1601;&#1607; &#1608;&#1578;&#1606;&#1589;&#1576; &#1584;&#1575;&#1603; &#1575;&#1604;&#1575;&#1582;&#1585; &#1575;&#1604;&#1605;&#1582;&#1589;&#1589; &#1604;&#1605;&#1593;&#1605;&#1575;&#1585;&#1610;&#1577; 32 &#1576;&#1578;&#1575;&#1611;.
&#1581;&#1610;&#1579; &#1575;&#1606; &#1584;&#1575; &#1575;&#1604; 64 &#1576;&#1578;&#1575;&#1611; &#1587;&#1608;&#1601; &#1610;&#1602;&#1608;&#1605; &#1576;&#1575;&#1583;&#1582;&#1575;&#1604;&#1603; &#1601;&#1610; &#1575;&#1605;&#1575;&#1603;&#1606; &#1590;&#1610;&#1602;&#1577;.
&#1578;&#1581;&#1610;&#1575;&#1578;&#1610;

&#1605;&#1593;&#1604;&#1610;&#1588; &#1610;&#1575; &#1586;&#1610;&#1585;&#1608;-&#1575;&#1606; &#1608;&#1610;&#1575; &#1610;&#1575;&#1587;&#1585;, &#1575;&#1606;&#1575; &#1576;&#1587; &#1581;&#1576;&#1610;&#1578; &#1575;&#1606;&#1576;&#1607; &#1575;&#1606;&#1608; &#1575;&#1604;64 &#1604;&#1604;&#1575;&#1587;&#1601; &#1576;&#1610;&#1608;&#1575;&#1580;&#1607; &#1605;&#1588;&#1575;&#1603;&#1604; &#1603;&#1578;&#1610;&#1585;&#1577; (&#1604;&#1581;&#1583;&#1610; &#1570;&#1582;&#1585; &#1605;&#1585;&#1577; &#1580;&#1585;&#1576;&#1578;&#1608;), &#1608;&#1575;&#1606;&#1575; &#1575;&#1601;&#1578;&#1603;&#1585;&#1578; &#1575;&#1606;&#1608; &#1603;&#1604;&#1575;&#1605;&#1610; &#1605;&#1601;&#1607;&#1608;&#1605; &#1601;&#1610; &#1575;&#1604;&#1587;&#1610;&#1575;&#1602; &#1583;&#1607;.


[/right][/size]

---

### Post by yasir.elsharif on 2010-04-07
Thanks guys,
ziro-n: I tried that too, still have the same problem... Have you installed this program? which architecture are you using? and which interface? mine is gnome.

adntu: I am afraid that I've been using this architecture for a while now, and I am quite happy with it, and you can install 32-bit applications as well.

---

### Post by zero-n on 2010-04-07
Yes i have installed this program with no problems.

architecture : i686

desktop environment : Gnome

---

### Post by yasir.elsharif on 2010-04-13
Thank you guys I got it installed, but still not working, but when I started it with super permissions it worked after changing usb_modeswitch configuration file and enable the exact version of hardware.
the only thing that really bothers me, is how to recharge the sim with more credit and/or request credit reports "*888#" 

Please tell me if you could do this

Thanks in a lot everyone
cheers

---

### Post by zero-n on 2010-04-18
You can try [[COLOR=Red]**Wammu**[/COLOR]]("http://wammu.eu/")

```
apt-get install wammu
```Wammu is used to connect to phones but i can be used with modems

i have successfully connect to my modem using it but i didn't work when trying to send messages.

give it a try.

---

