---
title: "Ubuntu installation over a Network"
date: 2008-06-03
forum: Server Platforms
---

### Post by francastillo on 2008-06-03
Hi, I just started using ubuntu, but Im really curious and I would like to know if there is a way to make an Ubuntu installation over a network, if there is a way, how can I perform it? coz I would like to use a virtual machine to try it since I only have one PC to try it....

Thanks in advance!

:D

---

### Post by prabubecse on 2008-06-03
do u know how to add sun java application server to net beans 6.1... i have problems in finding platform location please help...

---

### Post by windependence on 2008-06-04
> **francastillo said:**
> Hi, I just started using ubuntu, but Im really curious and I would like to know if there is a way to make an Ubuntu installation over a network, if there is a way, how can I perform it? coz I would like to use a virtual machine to try it since I only have one PC to try it....

Thanks in advance!

:D

If you use Vmware server (free) instead of Xen, you won't have to do a network install, you can install from CD.

-Tim

---

### Post by hyper_ch on 2008-06-04
what do you mean by installation of the network?

Have a look here:  [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by francastillo on 2008-06-11
sorry, I meant some sort of application or service like RIS (remote installation services) for windows 2000 server, with an image of an installation disc of windows XP you can install it on many hosts on your network, only by booting from your NIC it would run an unattended installation, post installation scripts, etc etc etc.

is there a way to install ubuntu over a network and if possible, an unattended installation?

thanks in advance! :D

---

### Post by koenn on 2008-06-11
You can do a network install with the so-called "mini iso" : you boot an installer from the mini-CD and it downloads  the software from the official repos, your own mirror, or an apt-cache/apt-proxy.

You can install unattended by using a preseed file (like an answer file for Windows setup), that can either be read from the CD (requires remastering the CD) or from a network server

Obviously, you can combine both. Here are some notes : [http://users.telenet.be/mydotcom/howto/linux/automatic.htm](http://users.telenet.be/mydotcom/howto/linux/automatic.htm)
it's a Debian thing but the mecahnism applies to Ubuntu as well.


To make it complete, you'd need to set up a netboot infrastructure : dhcp + "next server" that serves an installer boot image". Don't know if Ubuntu actively supports that, but I know it can be done. You can probably find a procedure in the Debian Installation manual, or start from here : [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by promodus on 2008-09-14
[http://ubuntuforums.org/showthread.php?t=829482](http://ubuntuforums.org/showthread.php?t=829482)

---

