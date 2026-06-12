---
title: "Ubuntu GNOME 15.04 b2 Network Problem"
date: 2015-04-04
forum: Ubuntu Development Version
---

### Post by carlos_rodrigo3 on 2015-04-04
[CENTER]First I want to make it clear that I am Brazilian and I am using the google translator so any error written sorry.
[/CENTER]
Motherboard: GA-Z77M-D3H   rev.1.1  

Sometimes for no reason, even showing connected with it no page in the browser, not even update the system, I use firefox and chrome and two are in the same thing, it is strange why not show that disconnect, but I get no internet, e takes off and turn on the connection, someone else is going through this? Does anyone have any tips on how I can ta solving this problem?

---

### Post by grahammechanical on 2015-04-04
Is this wiFi or Ethernet? If Network Manager is connected to the router, then it shows Connected. I am using Ubuntu and for some weeks I have needed to disconnect the Wired (Ethernet) connection and use WiFi because although Ubuntu is connected to the router and the router is connected to the ISP, there is no connection to the Internet or the Ubuntu archives for updating. sometimes there is a connection but it drops. The moment I switch from Wired connection to WiFi the connection to the internet is fine.

I have other installations of Ubuntu 15.04 and I do not seem to get this problem with those installations but I have not tested this thoroughly.

Regards.

---

### Post by carlos_rodrigo3 on 2015-04-04
Ethernet, I use a desktop, and I have no wifi to test, always go to the settings and turn off to work, but after a few minutes I get no network even showing connected

---

### Post by ethan26 on 2015-04-04
I would like to see the answer to this. I also have an ethernet desktop and some times have the same isue

---

### Post by cariboo on 2015-04-04
It would be nice to know if you are having problems with the same wifi chipset.  I'm using:

```
Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
```

with zero problems.

---

### Post by carlos_rodrigo3 on 2015-04-04
I think the onboard network card is RJ-45 without wifi

---

### Post by cariboo on 2015-04-04
Can you run

```
lspci | grep Ethernet
```

in a terminal, and paste the output in your next post.

---

### Post by carlos_rodrigo3 on 2015-04-04
thanks for the code ;)


**[SIZE=3]02:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10)[/SIZE]**

---

### Post by QDR06VV9 on 2015-04-06
Hi carlos_rodrigo3 have you yet tried reinstalling network-manager?
I had the same problem upgrading from 12.04 to 14.04
This worked for me (Seems that card is bit touchy with newer kernels)
I resolved it by logging in recovery mode, with the network, then typing into the console:
```

sudo apt-get remove network-manager
sudo apt-get update
sudo apt-get install network-manager

```
If that doesn't work boot from a live CD, back up your old network settings, clear out any system connection file and copy over the ones from the live CD.
```
sudo su 
```
backup:
```
mv /media/<Name of your Ubuntu Partion>/etc/NetworkManager/NetworkManager.conf /media/<Name of your Ubuntu Partion>/etc/NetworkManager/NetworkManager.conf.broken

```

Remove
```
rm /media/<Name of your Ubuntu Partion>/etc/NetworkManager/system-connections/*

```

And finally:
```
cp /etc/NetworkManager/NetworkManager.conf /media/<Name of your Ubuntu Partion>/etc/NetworkManager/NetworkManager.conf
cp /etc/NetworkManager/system-connections/* /media/<Name of your Ubuntu Partion>/

```
sorry for the late reply out of town for the weekend;)
Regards

---

### Post by carlos_rodrigo3 on 2015-04-06
Unfortunately, I got the upgrade to the latest version of the kernel but it made no difference, then I believe it is something directly connected to the network driver

---

### Post by cariboo on 2015-04-06
Can you open an terminal, and run the following command:

```
lshw -C network
```

and paste the output in your next post. 

The output of the command will show us if the network card is detected properly, and if the driver is loaded.

---

### Post by carlos_rodrigo3 on 2015-04-06
*-network               
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 94:de:80:65:13:2c
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=192.168.25.34 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:29 memory:f7c00000-f7c3ffff ioport:e000(size=128)

---

### Post by cariboo on 2015-04-06
From the output of the lshw command it looks like your nic is working as it should. What does /etc/resolv,conf look like, as it may be that you are having a problem with DNS.

```
cat /etc/resolv.conf
```

on the system I'm currently using, it looks like this:

```
cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
```

---

### Post by carlos_rodrigo3 on 2015-04-06
In my appear the same as its

---

### Post by harry332 on 2015-04-07
Does this help: stop network manager and start it again (when in desktop, from the terminal).
code:
sudo service network-manager stop
sudo service network-manager start

---

### Post by ventrical on 2015-04-07
> **carlos_rodrigo3 said:**
> [CENTER]First I want to make it clear that I am Brazilian and I am using the google translator so any error written sorry.
[/CENTER]
Motherboard: GA-Z77M-D3H   rev.1.1  

Sometimes for no reason, even showing connected with it no page in the browser, not even update the system, I use firefox and chrome and two are in the same thing, it is strange why not show that disconnect, but I get no internet, e takes off and turn on the connection, someone else is going through this? Does anyone have any tips on how I can ta solving this problem?

I was looking at the BIOS manual for that motherboard and am wondering if there is misconfiguration?

Regards..
[http://www.manualslib.com/manual/488761/Gigabyte-Ga-Z77m-D3h.html?page=48#manual](http://www.manualslib.com/manual/488761/Gigabyte-Ga-Z77m-D3h.html?page=48#manual)

---

### Post by carlos_rodrigo3 on 2015-04-07
I think not, because this the same way I used in Ubuntu 14.10, and there everything worked well.

---

### Post by ventrical on 2015-04-07
> **carlos_rodrigo3 said:**
> I think not, because this the same way I used in Ubuntu 14.10, and there everything worked well.

Ok.. thank you for reply.
Does network run in 'live' USB session??

Regards..

---

### Post by carlos_rodrigo3 on 2015-04-07
Is installed on the HD only Ubuntu Gnome 4.15, but the USB is the same as well.

---

### Post by cariboo on 2015-04-07
I'd suggest you add some additional DNS servers in the ipv4 settings section of network manager. Try 8.8.8.8  and 8.8.4.4

---

### Post by carlos_rodrigo3 on 2015-04-07
Remains the same

---

### Post by ventrical on 2015-04-07
Try different ethernet cable. Check plug in connections. I have 4 desktop towers running on KVM. They are all hooked to a router and that is hooked to a main router. Sometimes (for no reason) I will have no network and often times there is a cable slip or problem. If you cannot hook to network with live USB then sounds like hardware problem. Can you still connect with existing 14.10??because if you can then there is definitely something wrong with software install.

Regards..

---

### Post by carlos_rodrigo3 on 2015-04-07
Yes, the internet works normally both in 14:04 and in 14:10, in all distros, xubuntu, Lubuntu, ubuntu-gnome, ubuntu and kabuntu, however I would be experiencing the beta but there is this error, otherwise the beta run smoothly

---

### Post by ventrical on 2015-04-07
When , when ... you boot up betab2 then you don't get network. OK Then .. hold SHIFT  key while 15.04 beta is booting and you WILL get grub MENU. Chooose Recovery Mode option. It will show verbose loading of  modules.. etc... THEN it will come to MENU and you can choose Network, THEN it will go back to Menu and then choose #root.

Then you should be able to run this command:

```


sudo apt-get update

```

and if Network is working it will show you get-> results from the index. So my point is that if Network is working in recovery/root then  it must point to config  file AFTER  the GUI has loaded. It could be that the install may be bricked  (or that means possibly corrupted in some way) and cannot be recovered and may take a new install .. because it sounds like your install is possibly FUBARed (that means not working right at all ) :)

Regards..

---

### Post by zika on 2015-04-08
There is no unfixable installl ;)
Ease of reinstall made us complacent and easy on trigger.
Just take a look in important files /etc/netowrk/interfaces /etc/N..Manager*.conf and You will find a simple reason for this trouble.

---

### Post by malch2 on 2015-04-25
I am having the same problem with Xubuntu 15.04 release version. My laptop has the same AR8161 Ethernet Controller.

My machine is dual boot with Win 7 and the same controller, cable, router all work fine under Windows. The hardware is good.

Same problem when booting from the LiveCD. And the same problem with Network Manager taken out of the loop. Therefore, I suspect a problem with the (oldish) alx driver and the new kernels.

More here:

[http://ubuntuforums.org/showthread.php?t=2275361](http://ubuntuforums.org/showthread.php?t=2275361)

Carlos is not dreaming or making this up :-) He has my profound sympathies.

---

