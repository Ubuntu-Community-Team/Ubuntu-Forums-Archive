---
title: "Kernel Headers Headers Problem"
date: 2005-10-01
forum: The Cafe
---

### Post by daejavu on 2005-10-01
hi .. im trying to install my new Graphic card .. a Radeon 9600. while installing its latest driver it says kernel-headers not installed .. i updated my apt repositories but it dosent show me any kernel headers for my kernel ..  

i need kernel headers tobe installed so that i can install the graphic driver .. so please let me know a solution to this !

Ive tried  apt-get install linux-kernel-headers $x.x.x.x.x   and Synaptic ... both come back with no kernel headers .. my kernel ver no is 2.6.10.5-386

---

### Post by codejunkie on 2005-10-01
[QUOTE=daejavu]hi .. im trying to install my new Graphic card .. a Radeon 9600. while installing its latest driver it says kernel-headers not installed .. i updated my apt repositories but it dosent show me any kernel headers for my kernel ..  
i need kernel headers tobe installed so that i can install the graphic driver .. so please let me know a solution to this !
Ive tried  apt-get install linux-kernel-headers $x.x.x.x.x   and Synaptic ... both come back with no kernel headers .. my kernel ver no is 2.6.10.5-386[/QUOTE]
```
sudo apt-get install linux-headers-386
```
should install the kernel headers for the 386 kernel.

---

### Post by daejavu on 2005-10-01
will this install all the headers needed by the ATI Graphic Driver ?

---

### Post by tseliot on 2005-10-01
[QUOTE=daejavu]will this install all the headers needed by the ATI Graphic Driver ?[/QUOTE]
The only headers are the ones for your kernel version: e.g. if you use kernel 2.6.10 you will need headers 2.6.10. If you want to know your kernel version open Terminal or Konsole and type "uname -r".

There are no kernel headers for a graphic card, there are only kernel headers for your kernel image. I hope this makes things a bit clearer for you

---

