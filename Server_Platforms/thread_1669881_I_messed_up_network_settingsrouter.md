---
title: "I messed up network settings/router"
date: 2011-01-18
forum: Server Platforms
---

### Post by pstrbrc on 2011-01-18
Ubuntu server w/gui, LAMP
was able to get it set up behind a belkin router using info from 
[http://www.zaphu.com/2007/08/07/ubuntu-lamp-server-setup-guide-with-desktop-gui/]("http://www.zaphu.com/2007/08/07/ubuntu-lamp-server-setup-guide-with-desktop-gui/"), downloaded a typo3 based cms, have it installed. All of theis time I was using the server computer itself to follow instructions on the web by using Firefox browzer on the gui. Everything worked, I was able to ping all other computers on the lan as well as load websites, etc. That was last night. This morning I can access my website from another computer on the lan both from my web ip address, as well as my lan ip address. What I can't do is ping anything past my lan from my web server machine. Now, I haven't changed any router settings, so I'm wondering if I messed up my etc/network/interfaces file in any way. The only thing I did late yesterday was to load bind9 and begin setting up a dns server function for my lan. Again, following the instructions of the Zaphu site. 

Here is what etc/network/interfaces looks like:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    [INDENT]address 192.168.2.4
    netmask 255.255 255.0
    network 193.168.2.0
    broadcast 192.168.2.255
    gateway 192.168.2.0[/INDENT]


Now, I'm posting this from another computer on my lan, so I know my router is communicating with the web. What do I check next?

---

### Post by volkswagner on 2011-01-18
Did you make a typo?  "network" says 193 not 192

---

### Post by volkswagner on 2011-01-18
Did you make a typo?  "network" says 193 not 192

What is output of
[code]route[code/]

---

### Post by pstrbrc on 2011-01-18
> **volkswagner said:**
> Did you make a typo?  "network" says 193 not 192

What is output of
```
route[code/]

Yep. typo. 

Output of [code]route
``` is (remember, I can't copy and paste this, so I'll try to type it in the format that the terminal writes it, but...)

```
pstrbrc@xxxserver:~/Desktop$ route
Kernel IP routing table
Destination     Gateway     Genmask      Flags  Metric  Ref     Use  Iface
192.168.2.0     *           255.255.255.0 U     0       0        0    eth0
link-local      *           255.255.0.0   U     1000    0        0    eth0
default         192.168.2.1 0.0.0.0       UG    100     0        0    eth0
pstrbrc@.......

```

---

### Post by spynappels on 2011-01-18
Also your gateway is incorrect, it cannot be 192.168.2.0 as that is not a permitted IP address in the subnet. It should probably be 192.168.2.1, but it should definitely point to the IP of your router.

---

### Post by spynappels on 2011-01-18
Also your gateway is incorrect, it cannot be 192.168.2.0 as that is not a permitted IP address in the subnet. It should probably be 192.168.2.1, but it should definitely point to the IP of your router.

---

### Post by HugoSerrano on 2011-01-18
install openssh-server in your server so you can connect to him from other machine.
from other machine console:
ssh user@192.168.2.4

then you can copy past things :-P
But probably you wont be able to install it, you need the network connection!

Like spynapples said, your gateway can't be that one. Maybe another typo? But the what you describe match with that error in the configuration file.

Regards.

---

