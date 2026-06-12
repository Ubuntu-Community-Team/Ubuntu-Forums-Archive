---
title: "Ubuntu Laptop Support"
date: 2005-10-05
forum: The Cafe
---

### Post by Donshyoku on 2005-10-05
I just ordered a new laptop and would like to view the Ubuntu compatibility.  I am worried about WLAN and audio.

I remember seeing once a wiki about laptop support.  Could someone direct me there?  

Thanks in advance!

---

### Post by dabear on 2005-10-05
here maybe?: [https://wiki.ubuntu.com/LaptopTestingTeam/](https://wiki.ubuntu.com/LaptopTestingTeam/)

---

### Post by mlomker on 2005-10-05
You could also try [linuxquestions.]("http://www.linuxquestions.org/hcl/index.php")

I haven't seen any case where audio didn't work because only a couple chips are built into laptops these days, regardless of the name on the case.  Broadcom wireless adapters will require ndiswrapper but pretty much everything works with it...if you're lucky you're laptop will have an Intel wireless module.

---

### Post by Crazy Man on 2005-10-05
Wireless in Debian based distros (such as Ubuntu) is usually relatively simple to set up.
First open your terminal (or tty session if you're not in X), and as root (su or sudo), edit /etc/network/interfaces.
In between the lines
```

iface eth0 inet dhcp

```
and 
```

auto <wireless_device> #for example eth1 or wlan0

```
put your network details in the following manner:
```

iface <handle> inet dhcp 
wireless-essid <SSID>
Wireless-key <KEY> 

```
Handle is the nickname you give to the network setting. I also believe that the key has to in hex...not sure though. Someone please correct me if I'm wrong.
after you enter the info, exit the editor and as root (su or sudo), type the following:
```

ifup <wireless_device>=<handle>

```
Press enter and you should be set.
Hope this helps.

Note: This is what worked with my PCMCIA Linksys WPC11v3 card.

---

### Post by 23meg on 2005-10-05
[http://www.linux-laptop.net/](http://www.linux-laptop.net/) is a good resource, but i wish you'd checked these sites out before ordering the laptop..

---

### Post by matthew on 2005-10-06
I think this is the one you are looking for.

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)

---

