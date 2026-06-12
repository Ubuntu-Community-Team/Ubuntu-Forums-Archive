---
title: "xp in Virtualbox"
date: 2008-05-09
forum: Security
---

### Post by richardjennings on 2008-05-09
Am I correct in my assumption that running Xp in VirtualBox, in a default Ubuntu install, affords xp the same levels of security as Ubuntu? If not can anyone link an article that explains why not? Cheers

---

### Post by hyper_ch on 2008-05-09
I don't get what you mean to ask.

---

### Post by y2kprawn on 2008-05-09
Naaa, you do not get the protection of Ubuntu. 
 
The problem is that when you run any OS inside a Virtual Environment, it runs just like the OS would on a actual machine, the Virtual Environment gives it access to the actual hardware of your system using Virtualisation ([http://en.wikipedia.org/wiki/Virtualisation](http://en.wikipedia.org/wiki/Virtualisation)).
 
So if the OS you are running in virtual box gets a virus, or is compromised in any manner , it is compromised the same way as it is working as an install on your machine. 
 
However, the best thing is that you can keep a copy of your virtual OS and restore it if anything happens, and then secure it from stuff happening to it in the future. Saves you having to reinstall the OS every time. 
 
I am running, Windows Server 2008, Windows XP , Dam Small Linux and and Open Solaris in Virtual Box, when I am using them I always assume I need to protect them the same way as I would protect the OS if it was natively installed (i.e on a hard drive partition or a whole hard drive). The comfort comes in the fact that I can just copy back the OS image file from a backup if anything goes wrong. 
 
I hope this goes some way to answer your question.

---

### Post by ilrudie on 2008-05-09
> **y2kprawn said:**
> Naaa, you do not get the protection of Ubuntu. 
 
The problem is that when you run any OS inside a Virtual Environment, it runs just like the OS would on a actual machine, the Virtual Environment gives it access to the actual hardware of your system using Virtualisation ([http://en.wikipedia.org/wiki/Virtualisation](http://en.wikipedia.org/wiki/Virtualisation)).
 
So if the OS you are running in virtual box gets a virus, or is compromised in any manner , it is compromised the same way as it is working as an install on your machine. 
 
However, the best thing is that you can keep a copy of your virtual OS and restore it if anything happens, and then secure it from stuff happening to it in the future. Saves you having to reinstall the OS every time. 
 
I am running, Windows Server 2008, Windows XP , Dam Small Linux and and Open Solaris in Virtual Box, when I am using them I always assume I need to protect them the same way as I would protect the OS if it was natively installed (i.e on a hard drive partition or a whole hard drive). The comfort comes in the fact that I can just copy back the OS image file from a backup if anything goes wrong. 
 
I hope this goes some way to answer your question.

I second this statement.

---

### Post by richardjennings on 2008-05-09
Thankyou for your replies. I meant to ask if the networking aspect of xp is more secure. I have not had the time to read up on network security, but I was under the impression that Ubuntu keeps ports closed by default. Does XP have the ability to open whichever ports it wants via the virtual machine? If it can, does this comprimise Ubuntu in anyway?

---

### Post by p_quarles on 2008-05-09
Running XP in Virtualbox is really no different from running it on a physical machine. The main difference is that you can make system "snapshots," and use these to undo any damage that may have been done. If you wanted, you could use a safe snapshot every time you reboot the virtual machine.

---

### Post by richardjennings on 2008-05-09
yes that is a great advantage to using a virtualmachine. 

If I understand you correctly, Xp running in the virtual machine makes Ubuntu less secure because it can open whichever ports it likes, (aka "is really no different from running it on a physical machine").

I understand that running a firewall in Ubuntu would probably prevent Xp from opening random ports. Is it possible to simulate a hardware firewall between virtualbox and the kernel? I would like to choose which ports xp is alowed to open, without having to limit Ubuntu.

---

### Post by p_quarles on 2008-05-09
You can run Firestarter to block commonly-exploited ports. Firestarter is a configuration utility for IPtables, a Linux kernel module that is widely used by hardware firewalls. You can also, of course, learn the IPtables command-line, and do it yourself. ;)

I'd also suggest just turning off a lot of the automatic services that Windows runs. You don't always need these for a "real" computer, and many of them are completely pointless in a virtual machine (e.g., zeroconf wireless). Not only will this make the VM more secure, but it will improve performance.

---

### Post by richardjennings on 2008-05-09
The problem with using Firestarter is that it will also limit the ports that the host os Gutsy will be able to use. I want to lock xp down tight, just leaving the online poker ports and the basics. If i used firestarter I would  no longer be able to use pop email or ftp etc..  I had assumed that virtualbox would have a configuration utility to allow ports to be blocked between the host and guest. I have had no luck with google.

---

### Post by richardjennings on 2008-05-09
i found this [http://home.nyc.rr.com/computertaijutsu/vboxbridge.html](http://home.nyc.rr.com/computertaijutsu/vboxbridge.html) which has answered my questions. Cheers.

---

### Post by y2kprawn on 2008-05-10
Cheers for the reply to this, I did not consider the difference between native networking and NAT in my reply. 

Thanks for the link, its an interesting article , sorry my initial answer was not what you were looking for.
Enjoy VirtualBox, its a pretty cool product !!

---

### Post by ububone on 2008-08-15
Hi,

I followed the instructions from 

[http://home.nyc.rr.com/computertaijutsu/vboxbridge.html](http://home.nyc.rr.com/computertaijutsu/vboxbridge.html)

and get my WLAN to host connection working - BUT I have a
big network problem with my host:

here is the actual situation:

ubuntu 8.04 host:
internet o.k.
connection to internal network = did not work

xp client: 
internet o.k. 
connection to internal host-network = o.k.

at /etc/rc.local I wrote the following changes:
> 
sysctl net.ipv4.ip_forward=1 
VBoxTunctl -b -u ralf 
ip link set tap0 up 
ip addr add 193.169.2.20/24 dev tap0 
parprouted eth0 tap0 
chmod 0666 /dev/net/tun 
route add -net 193.169.2.0 netmask 255.255.255.0 tap0 
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 


If I remove the lines my host network works normal - but then I had no
connection to my host from virtualbox :((

Any Idea what is wrong with these lines ?

route -n shows the following

> 
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
193.169.2.30    0.0.0.0         255.255.255.255 UH    50     0        0 tap0
193.169.2.3     0.0.0.0         255.255.255.255 UH    50     0        0 eth0
193.169.2.1     0.0.0.0         255.255.255.255 UH    50     0        0 eth0
193.169.2.4     0.0.0.0         255.255.255.255 UH    50     0        0 eth0
193.169.2.0     0.0.0.0         255.255.255.0   U     0      0        0 tap0
193.169.2.0     0.0.0.0         255.255.255.0   U     0      0        0 tap0
193.169.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         193.169.2.1     0.0.0.0         UG    0      0        0 eth0


when it did not work a trace shows that the internal route seems to try to route thru 193.169.2.30 the tap0 device so maybe here is the mistake

But how can I solve this - I am new to linux an networking seems to be a little bit tricky

Thx

Ralf

---

### Post by ububone on 2008-08-19
no one an idea ? I can't get it work - really frustrating... am I the only one with this problem ?

---

