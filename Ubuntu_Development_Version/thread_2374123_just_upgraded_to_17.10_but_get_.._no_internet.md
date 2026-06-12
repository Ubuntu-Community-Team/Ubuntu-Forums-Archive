---
title: "just upgraded to 17.10 but get .. no internet"
date: 2017-10-13
forum: Ubuntu Development Version
---

### Post by Kris_M on 2017-10-13
_**jump to post 20**_


17.04 upgrade to 17.10 seemed to go smoothly but on restart, asks for password, thinks a while, and loops back to password. Was running Gnome..

Only other time I have seen this loop was when I was on the wrong video driver (installed on Nvidia), so did alt-ctl-F2 to get terminal and did 
prime-select query which said nvidia, so did
sudo prime-select intel and restarted computer but same loop and no activity on the intel chip.

Any ideas? or should I just clonezilla back... Thanks.

---

### Post by jbicha on 2017-10-13
After clicking your name on the login screen, click the gear button and choose a different session. I suggest either *Ubuntu* or *Ubuntu on Xorg*.

---

### Post by Kris_M on 2017-10-13
> **jbicha said:**
> After clicking your name on the login screen, click the gear button and choose a different session. I suggest either *Ubuntu* or *Ubuntu on Xorg*.

I clonezilla'ed back to 17.04 . I'll try again tomorrow.

So I can't start it in gnome?

EDIT: I think I tried Ubuntu and that didn't work.  I'll try all the others next time.

I saw below that 17.10 wayland doesn't like nvidia...  Maybe I should be running the install when I am running on the intel video?  But does that mean I can't shift back to Nvidia?

Thanks!

---

### Post by dino99 on 2017-10-13
That is a nvidia known issue (closed driver) not working with wayland, which is now the default session. So either use the nvidia card with 'nouveau' or choose a X session when booting; or switch on the intel igp which works well with wayland.

---

### Post by Kris_M on 2017-10-13
> **dino99 said:**
> That is a nvidia known issue (closed driver) not working with wayland, which is now the default session. So either use the nvidia card with 'nouveau' or choose a X session when booting; or switch on the intel igp which works well with wayland.

The problem with nouveau or the intel graphics is neither is fast enough for my very old games (NWN etc). But at least it gives me 2 possibilities, and tells me why it logon looped.

Is this something that will change with wayland? or is that rather permanent?

Thanks!!!

---

### Post by Kris_M on 2017-10-13
lol - I set 17.04 to nouveau but it wouldn't boot. Guess I'll try Intel tomorrow...  Nite!

edit: I tried intel, too but it also gets stuck.
both start kern and hang at /dev/sda1: clean ---------
I'll start a new thread for this since it's 17.04.

---

### Post by jbicha on 2017-10-13
It's also possible for an old GNOME Shell extension to cause GNOME/Ubuntu to fail to start.

Could you try creating a new user and logging in as the new user?

---

### Post by Kris_M on 2017-10-13
> **jbicha said:**
> It's also possible for an old GNOME Shell extension to cause GNOME/Ubuntu to fail to start.

Could you try creating a new user and logging in as the new user?

How would I do that please? Thanks!

---

### Post by Kris_M on 2017-10-14
Okay, I succeeded in converting 17.04 to nouveau and rebooting by removing "nomodeset" from grub, though remarkably unstable - chrome keeps crashing - nonetheless I did the upgrade to 17.10 and was able to boot into it choosing gnome on xorg. (using my GTX750Ti) All the desktop icons are just documents - no correct icons.

Software updater says no internet. Indicator in top bar shows a triangle with a ? inside it. Settings/internet shows me connecting to either of my 2 NICs, so that seems to be recognizing it. I did replug the cable modem and power cycled the router, but no joy. I did not try chrome as I didn't want it to get all bent. Should have tried TBird but didn't. Have it on clonezilla image so easy to get back to.

Any ideas how to get internet to be recognized by software updater etc? Thanks!

---

### Post by cariboo on 2017-10-14
It would help if you gave us some details on the hardware you are using, could you post the output of the following commands:

```
sudo lshw -C network
```

and

```
 cat /etc/resolv.conf
```

---

### Post by Kris_M on 2017-10-14
> **cariboo said:**
> It would help if you gave us some details on the hardware you are using, could you post the output of the following commands:

```
sudo lshw -C network
```

and

```
 cat /etc/resolv.conf
```

Thanks!
I didn't like that nouveau 17.04 build so I rebuilt 17.10 from 17.04 nvidia 187 -  much more stable.
Grub booted it if I add
grub_gfxmode=1280x1024x24
and left nomodeset in linux cmd.

logon to gnome xorg

same results:

this is clonezilla'ed so easy to get back to. (I run on 17.04 until I get this going.)

```
kris@kris-Z97X-UD3H:~$ sudo lshw -C network[sudo] password for kris: 
  *-network                 
       description: Ethernet interface
       product: Ethernet Connection I217-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eno1
       version: 00
       serial: 40:8d:5c:59:ac:23
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.13-4 ip=192.168.1.41 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:26 memory:f7900000-f791ffff memory:f793c000-f793cfff ioport:f080(size=32)
  *-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 00
       serial: 68:05:ca:58:c4:4c
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=1.8-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:f78c0000-f78dffff memory:f7800000-f787ffff ioport:d000(size=32) memory:f78e0000-f78e3fff memory:f7880000-f78bffff
kris@kris-Z97X-UD3H:~$ 
kris@kris-Z97X-UD3H:~$ 
kris@kris-Z97X-UD3H:~$ cat /etc/recov.conf
cat: /etc/recov.conf: No such file or directory
kris@kris-Z97X-UD3H:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 127.0.1.1
kris@kris-Z97X-UD3H:~$ 



```

---

### Post by cariboo on 2017-10-14
It looks like you are missing a DNS server, my /etc/resolv.conf looks like this:

```
cat /etc/resolv.conf
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# 127.0.0.53 is the systemd-resolved stub resolver.
# run "systemd-resolve --status" to see details about the actual nameservers.
nameserver 127.0.0.53

search ca.shawcable.net
```

---

### Post by Kris_M on 2017-10-14
> **cariboo said:**
> It looks like you are missing a DNS server, my /etc/resolv.conf looks like this:

```
cat /etc/resolv.conf
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# 127.0.0.53 is the systemd-resolved stub resolver.
# run "systemd-resolve --status" to see details about the actual nameservers.
nameserver 127.0.0.53

search ca.shawcable.net
```


This is what I have on 17.04 - works fine.  DNS server is through router 8.8.8.8 , same thing through IP if I don't happen to specify it in router.

```
kris@kris-Z97X-UD3H:~$ cat /etc/resolv.conf# Generated by NetworkManager
nameserver 127.0.1.1
kris@kris-Z97X-UD3H:~$ 

```


There is no difference in what lshw shows - checked line by line by Diff Checker.

---

### Post by Kris_M on 2017-10-14
I tried bypassing the router.
I tried adding 8.8.8.8, 8.8.4.4 to ipv4 .
i tried pppoeconf .
I tried sudo service network-manager restart

nothing works.

```
kris@kris-Z97X-UD3H:~$ sudo service network-manager restart[sudo] password for kris: 
kris@kris-Z97X-UD3H:~$ ifconfig
eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 100.65.64.10  netmask 255.255.255.248  broadcast 100.65.64.15
        inet6 fe80::b32:a277:7be:3102  prefixlen 64  scopeid 0x20<link>
        ether 40:8d:5c:59:ac:23  txqueuelen 1000  (Ethernet)
        RX packets 6  bytes 1580 (1.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 65  bytes 8738 (8.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf7900000-f7920000  


enp5s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 68:05:ca:58:c4:4c  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xf78c0000-f78e0000  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 602  bytes 45472 (45.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 602  bytes 45472 (45.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


kris@kris-Z97X-UD3H:~$ 
```

---

### Post by Kris_M on 2017-10-14
I tethered my cell phone to it and same thing - it sees it but for some reason will not use it.

---

### Post by cariboo on 2017-10-15
Try:

```
sudo ln -s /run/systemd/resolve/stub-resolv.conf /etc/resolv.conf
```

it worked for a couple of people.

---

### Post by zika on 2017-10-15
> **cariboo said:**
> Try:```
sudo ln -s /run/systemd/resolve/stub-resolv.conf /etc/resolv.conf
```it worked for a couple of people.It is a kind of creating a dead-loop unwanted in networking as much as here. Better do check the status of systemd-resolved.service.
I do see a lot of of UpStart atavisms here... ;)

---

### Post by Kris_M on 2017-10-15
@cariboo thanks for your patience, I will try that in a bit!

> **zika said:**
> It is a kind of creating a dead-loop unwanted in networking as much as here. Better do check the status of systemd-resolved.service.
I do see a lot of of UpStart atavisms here... ;)

Thanks - how do I check the status of systemd-resolved.service ?


With any test, I restore a clonezilla img of right after upgrade, so any tests I do aren't there the next time I test. When done with I restore 17.04 . I'll continue running 17.04 until I get past this. I am only using 1 partition (much simpler!)_ but I backup/restore the whole SSD (only about 30GB used on it) because sometimes things like to change grub... LOL

---

### Post by Kris_M on 2017-10-15
Thanks all, but nope...

```
kris@kris-Z97X-UD3H:~$ sudo ln -s /run/systemd/resolve/stub-resolv.conf /etc/resolv.conf[sudo] password for kris: 
ln: failed to create symbolic link '/etc/resolv.conf': File exists
kris@kris-Z97X-UD3H:~$ 






/etc/resolv.conf
# Generated by NetworkManager
nameserver 127.0.1.1
```


```
/etc/resolvconf/resolv.conf.d/head

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
# 127.0.0.53 is the systemd-resolved stub resolver.
# run "systemd-resolve --status" to see details about the actual nameservers.
```


I did edit /etc/resolv.conf to 53, but of course network manager restart resets it.

I am sure if I were to delete it and run the ln NM would just recreate it as 1, but I will try that if you want.


/run/resolvconf/interface says
nameserver  127.0.0.53 - same as on 17.04

---

### Post by Kris_M on 2017-10-20
an old one but will show up in searches.

credit beameup:

> **beameup said:**
> Fixed! This link
```
https://askubuntu.com/questions/622470/dns-probe-finished-bad-config-error-in-ubuntu-14-04/622493#622493
```

These commands
```


sudo dpkg-reconfigure resolvconf

Say yes to "prepare /etc/resolve.conf for dynamic updates?"

sudo reboot


```

Thanks!
execute those lines one at a time
I added 
sudo service network-manager restart

---

### Post by Irihapeti on 2017-10-20
Thread closed.

Please do not make multiple versions of the same post. It causes confusion and dilutes community effort.

---

