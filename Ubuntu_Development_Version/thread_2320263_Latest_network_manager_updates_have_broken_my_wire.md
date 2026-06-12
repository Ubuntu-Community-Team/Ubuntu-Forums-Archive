---
title: "Latest network manager updates have broken my wireless"
date: 2016-04-12
forum: Ubuntu Development Version
---

### Post by Irihapeti on 2016-04-12
Machine is Asus EeePC 900.

The latest network manager updates have rendered the wireless unusable. Network manager "thinks" it's an ethernet card instead.

output of ifconfig:

```
wlp1s0    Link encap:Ethernet  HWaddr 00:15:af:a7:6a:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

output of lspci -v

```
01:00.0 Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: AzureWave AW-GE780 802.11bg Wireless Mini PCIe Card
	Physical Slot: eeepc-wifi
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fbef0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Count=1 Masked-
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Kernel driver in use: ath5k
	Kernel modules: ath5k
```

Has anyone else run into anything like this? I.e. is there an existing bug?

---

### Post by grahammechanical on 2016-04-12
The bug is called systemd. :)

wlp1s0 is systemd speak for wl = wireless lan. p= bus = bus 1. s= slot = slot 0. It all means something. lspci -v does not list my wireless adapter. Perhaps because it is not PCI but USB in a special slot on the motherboard just for the WiFi card. 

Network Manager>Connections does list my wireless access point as "802.11 WiFi (wlx0015af0e9be0)"

If you have inxi installed run

```
inxi -n
```

This is what I get
> 
Network:   Card-1: Marvell 88E8056 PCI-E Gigabit Ethernet Controller driver: sky2
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: 00:1a:92:82:db:59
           Card-2: Marvell 88E8001 Gigabit Ethernet Controller driver: skge
           IF: enp6s4 state: down mac: 00:1a:92:82:d4:32
           Card-3: Realtek RTL8187 Wireless Adapter driver: rtl8187
           IF: wlx0015af0e9be0 state: N/A mac: N/A

In systemd speak en = ethernet. wl = wireless. 

This is what ifconfig says
> 
wlx0015af0e9be0 Link encap:Ethernet  HWaddr 00:15:af:0e:9b:e0  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe0e:9be0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1018 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:151461 (151.4 KB)  TX bytes:16892 (16.8 KB)

Regards.

---

### Post by Irihapeti on 2016-04-12
Output of inxi -n

```
Network:   Card-1: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express)
           driver: ath5k
           IF: wlp1s0 state: down mac: 00:15:af:a7:6a:be
           Card-2: Qualcomm Atheros Attansic L2 Fast Ethernet driver: atl2
           IF: enp3s0 state: up speed: 100 Mbps duplex: full
           mac: 00:1f:c6:d9:ee:16
```

Card-1 is showing "state: down". The wireless isn't working and I can't figure out how to get it to work. It was fine until yesterday.

There's been another lot of network manager updates, but it's still not working (even after a reboot).

In case I didn't make myself clear, I'm not personally bothered by the naming conventions or systemd details. I want the wireless to work. It was until yesterday and now isn't. :(

---

### Post by Irihapeti on 2016-04-12
I tried wicd on another install and it works. That appears to be an option if network manager won't work for me.

Edit: reported a bug. We'll see what happens next. :)

---

### Post by ventrical on 2016-04-12
> **Irihapeti said:**
> Machine is Asus EeePC 900.

The latest network manager updates have rendered the wireless unusable. Network manager "thinks" it's an ethernet card instead.

output of ifconfig:

```
wlp1s0    Link encap:Ethernet  HWaddr 00:15:af:a7:6a:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

output of lspci -v

```
01:00.0 Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: AzureWave AW-GE780 802.11bg Wireless Mini PCIe Card
    Physical Slot: eeepc-wifi
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fbef0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [90] MSI-X: Enable- Count=1 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Kernel driver in use: ath5k
    Kernel modules: ath5k
```

Has anyone else run into anything like this? I.e. is there an existing bug?

I have the same machine. :) I last left it on the shelf - but - luckily with it plugged in so it is charged up and raring to go. Lets see....

;)

---

### Post by exploder on 2016-04-12
I have Ubuntu Mate 16.04 running on a new Lenovo laptop and also noticed problems with the network manager updates. When I hover the cursor over the network icon in the panel it no longer displays signal strength.

---

### Post by ventrical on 2016-04-12
I got this after update/upgrade.

```

Errors were encountered while processing:
 /var/cache/apt/archives/systemd_229-4ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ventrical@ventrical-701:~$ 

```

apport reported a crash and subsequently tried to report a bug but failed.

also

but ook here also..

```

Setting up libsystemd0:i386 (229-4ubuntu4) ...
(Reading database ... 109880 files and directories currently installed.)
Preparing to unpack .../libudev1_229-4ubuntu4_i386.deb ...
Unpacking libudev1:i386 (229-4ubuntu4) over (228-2ubuntu1) ...
Setting up libudev1:i386 (229-4ubuntu4) ...
(Reading database ... 109880 files and directories currently installed.)
Preparing to unpack .../plymouth-theme-lubuntu-text_0.61_all.deb ...
Unpacking plymouth-theme-lubuntu-text (0.61) over (0.56) ...
Preparing to unpack .../plymouth-theme-lubuntu-logo_0.61_all.deb ...
Unpacking plymouth-theme-lubuntu-logo (0.61) over (0.56) ...
Preparing to unpack .../plymouth-theme-ubuntu-text_0.9.2-3ubuntu11_i386.deb ...
Unpacking plymouth-theme-ubuntu-text (0.9.2-3ubuntu11) over (0.9.0-0ubuntu9) ...
dpkg: warning: unable to delete old directory '/lib/plymouth/themes/ubuntu-text': Directory not empty
Preparing to unpack .../plymouth_0.9.2-3ubuntu11_i386.deb ...
Unpacking plymouth (0.9.2-3ubuntu11) over (0.9.0-0ubuntu9) ...
dpkg: warning: unable to delete old directory '/lib/plymouth/themes': Directory not empty
dpkg: warning: unable to delete old directory '/lib/plymouth': Directory not empty
Preparing to unpack .../libplymouth4_0.9.2-3ubuntu11_i386.deb ...
Unpacking libplymouth4:i386 (0.9.2-3ubuntu11) over (0.9.0-0ubuntu9) ...
dpkg: considering deconfiguration of ifupdown, which would be broken by installation of systemd ...
dpkg: yes, will deconfigure ifupdown (broken by systemd)
dpkg: considering deconfiguration of udev, which would be broken by installation of systemd ...
dpkg: yes, will deconfigure udev (broken by systemd)
Preparing to unpack .../systemd_229-4ubuntu4_i386.deb ...
De-configuring udev (228-2ubuntu1) ...
/var/lib/dpkg/info/udev.prerm called with unknown argument 'deconfigure'
dpkg: error processing archive /var/cache/apt/archives/systemd_229-4ubuntu4_i386.deb (--unpack):
 subprocess installed pre-removal script returned error exit status 1
addgroup: The group `systemd-journal' already exists as a system group. Exiting.
dpkg: considering deconfiguration of systemd, which would be broken by installation of ifupdown ...
dpkg: yes, will deconfigure systemd (broken by ifupdown)
Preparing to unpack .../ifupdown_0.8.10ubuntu1_i386.deb ...
De-configuring systemd (228-2ubuntu1) ...
Unpacking ifupdown (0.8.10ubuntu1) over (0.7.54ubuntu2) ...
Replacing files in old package systemd (228-2ubuntu1) ...
Preparing to unpack .../udev_229-4ubuntu4_i386.deb ...
Unpacking udev (229-4ubuntu4) over (228-2ubuntu1) ...
Preparing to unpack .../plymouth-label_0.9.2-3ubuntu11_i386.deb ...
Unpacking plymouth-label (0.9.2-3ubuntu11) over (0.9.0-0ubuntu9) ...
Preparing to unpack .../bluez_5.37-0ubuntu5_i386.deb ...
Unpacking bluez (5.37-0ubuntu5) over (5.36-0ubuntu1) ...
Preparing to unpack .../resolvconf_1.78ubuntu2_all.deb ...
Unpacking resolvconf (1.78ubuntu2) over (1.78ubuntu1) ...
Preparing to unpack .../sysv-rc_2.88dsf-59.3ubuntu2_all.deb ...
Unpacking sysv-rc (2.88dsf-59.3ubuntu2) over (2.88dsf-59.2ubuntu3) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for dbus (1.10.4-1ubuntu2) ...
Errors were encountered while processing:
 /var/cache/apt/archives/systemd_229-4ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ventrical@ventrical-701:~$ 

```

basically ..graham is right.

---

### Post by Irihapeti on 2016-04-12
[Bug report is here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1569590") if you'd like to contribute to it.

---

### Post by ventrical on 2016-04-12
actualy I ran

```


sudo dpkg --configure -a


```

and even though systemd is busted I have fully functional desktop and network card working.

regards

---

### Post by ventrical on 2016-04-12
I fixed systemd with this:

```

ventrical@ventrical-701:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  console-setup keyboard-configuration libpam-systemd systemd
Suggested packages:
  systemd-ui systemd-container
The following packages will be upgraded:
  console-setup keyboard-configuration libpam-systemd systemd
4 upgraded, 0 newly installed, 0 to remove and 643 not upgraded.
2 not fully installed or removed.
Need to get 0 B/4,580 kB of archives.
After this operation, 408 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
(Reading database ... 109894 files and directories currently installed.)
Preparing to unpack .../libpam-systemd_229-4ubuntu4_i386.deb ...
Unpacking libpam-systemd:i386 (229-4ubuntu4) over (228-2ubuntu1) ...
Preparing to unpack .../systemd_229-4ubuntu4_i386.deb ...
Unpacking systemd (229-4ubuntu4) over (228-2ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for dbus (1.10.4-1ubuntu2) ...
Setting up systemd (229-4ubuntu4) ...
Installing new version of config file /etc/systemd/logind.conf ...
Installing new version of config file /etc/systemd/resolved.conf ...
addgroup: The group `systemd-journal' already exists as a system group. Exiting.
Removing obsolete conffile /etc/X11/xinit/xinitrc.d/50-systemd-user.sh ...
(Reading database ... 109900 files and directories currently installed.)
Preparing to unpack .../keyboard-configuration_1.108ubuntu14_all.deb ...
Unpacking keyboard-configuration (1.108ubuntu14) over (1.108ubuntu9) ...
Preparing to unpack .../console-setup_1.108ubuntu14_all.deb ...
Unpacking console-setup (1.108ubuntu14) over (1.108ubuntu9) ...
Processing triggers for systemd (229-4ubuntu4) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libpam-systemd:i386 (229-4ubuntu4) ...
Setting up keyboard-configuration (1.108ubuntu14) ...
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
update-initramfs: deferring update (trigger activated)
Setting up console-setup-linux (1.108ubuntu14) ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-1.inc ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-13.inc ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-14.inc ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-15.inc ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-2.inc ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-3.inc ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-4.inc ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-7.inc ...
Installing new version of config file /etc/console-setup/compose.ISO-8859-9.inc ...
Setting up console-setup (1.108ubuntu14) ...
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.120ubuntu6) ...
update-initramfs: Generating /boot/initrd.img-4.3.0-2-generic
ventrical@ventrical-701:~$ 

```

so I will reboot and see if i still have network.

---

### Post by Irihapeti on 2016-04-12
I tried that here and:

```

sudo apt-get -f install
...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

```

Didn't appear to be any problem. :(

---

### Post by ventrical on 2016-04-12
all is well here on my asus EeePC with exception when I boot using upstart I get probems. apport ghost reports ..etc

---

### Post by Irihapeti on 2016-04-12
Now there's a thought. I might try rebooting into upstart and seeing if anything interesting happens.

---

### Post by Irihapeti on 2016-04-12
Well, that was weird.

No upstart option available in grub, so I booted into recovery and ran the dpkg option. Dpkg said there was nothing to do, but what the heck, let's do it anyway. Then rebooted again.

Initially, nm-applet showed the same problem. Used fn keys to turn off wireless, then turn it on again - which hadn't previously done a thing - and.... it's working.

Let's just see that it continues to behave itself. :)

---

### Post by ventrical on 2016-04-12
great.

btw..

```


sudo apt-get install upstart


```

for upstart option in GRuB
but I would advise against it. It's presenting weird apport reports to nowhere .. etc..

---

### Post by Irihapeti on 2016-04-13
Actually, I've discovered there's a bit more to it than I thought. :(

I turned the thing off, then restarted it again later.

After logging in, nm-applet shows "[wireless card name] disconnected"

Turn off wireless with function keys.

nm-applet shows "[wireless card name] device not managed"

Turn on wireless again with function keys

nm-applet shows "Enable Wifi" box unchecked

Check the box to enable wifi and wireless then connects to SSID


Better than it not working at all, but probably not what anyone really has in mind for daily use.


I'll update my bug report accordingly.

---

### Post by darran-kelinske on 2016-08-20
This helped me fix the networking on my Yakkety install! Thank you!

---

