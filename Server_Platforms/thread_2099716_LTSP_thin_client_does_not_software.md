---
title: "LTSP thin client does not software"
date: 2012-12-30
forum: Server Platforms
---

### Post by aviacliff on 2012-12-30
Hello everybody!
There is the problem: the thin client does not see software from LTSP-server.
1. My hardware: Intel E6320, RAM DDR2 4Gb, nVidia GT218(GeForce210), ASUS P5G41T-MLX.
2. UBUNTU 11.10 x32bit desktop, Unity.
3. Edit interfaces, as
[B]# This file describes the network interfaces available on your system

# and how to activate them. For more information, see interface(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Internet
auto eth2
iface eth2 inet dhcp

 auto eth3
 iface eth3 inet static
 address 192.168.7.1
 netmask 255.255.255.0[/B]
4. sudo apt-get install ltsp-server-standalone openssh-server
5. sudo ltsp-build-client
6. edit dhcp.conf
7. add user vit
8. The thin client to run a successful, but one does not see software from server. When I click the right batton appears window with the words «Create New Folder» «Create New Document» «Organize Desktop by Name» «Keep Aligned» «Change Desktop Backgraund». If select «Change Desktop Backgraund» appears the window «Appearence». If select icon «+»(in the window «Appearence»)  appears «Browser for more picture».
**Qustion: Why does not see the thin client the programs and other software from server?**
Help me if can please.
 Thank you!

---

### Post by aviacliff on 2013-01-03
1.Now I want to edit the file / etc / network / interfaces as

[B]# This file describes the network interfaces available on your system

# and how to activate them. For more information, see interface(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Internet
auto eth2
iface eth2 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1

 auto eth3
 iface eth3 inet static
 address 192.168.7.1
 netmask 255.255.255.0[/B]


2. edit the file / var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default

[B]defaultltsp
label ltsp
kernel vmlinuz
append ro initrinitrd.img quiet splash nbdroot=192.168.0.3:2000

replacing the last line nbdname = ltsp_i386 on nbdroot = 192.168.0.3:2000[/B]


3 Try to create an administrative user account

Execute the following steps (at the visudo step)

[B]# Members of the sudo group may gain root privileges
%sudo ALL=(ALL) ALL 

sudo -s -H
chroot /opt/ltsp/i386
useradd -m adminname -G sudo
passwd adminname
visudo
exit
exit[/B]

And get the following:
>>> /etc/sudoers: syntax error near line 21 <<< 
>>> /etc/sudoers: syntax error near line 22 <<< 
>>> /etc/sudoers: syntax error near line 23 <<< 
>>> /etc/sudoers: syntax error near line 25 <<< 
>>> /etc/sudoers: syntax error near line 26 <<< 
>>> /etc/sudoers: syntax error near line 27 <<< 
>>> /etc/sudoers: syntax error near line 28 <<< 
What now? sudo visudo 


**Can not create an administrative user account in the LTSP client chroot environment.**

---

### Post by aviacliff on 2013-01-06
After six days of searching,
enter :
```
root@v:~# modprobe squashfs 
root@v:~# modprobe unionfs 
FATAL: Module unionfs not found. 
```

It says that my Ubuntu 11.10 does not have **unuinfs**.
I guess I have to install  **unuinfs-fuse.**

---

### Post by aviacliff on 2013-01-13
My mother said it is better to take into English.
Online:
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

**should be very carefully studied and all done in the section Upgrades and Maintenance,**

I unfortunately neglected this point.

---

### Post by aviacliff on 2013-01-20
After installing Ubuntu-desktop-amd the thin client is working normally.

There are currently defect of thin client.
Namely, slowly open the application window (eg chrome-browser).

---

