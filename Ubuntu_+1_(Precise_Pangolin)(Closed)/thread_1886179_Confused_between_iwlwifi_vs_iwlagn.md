---
title: "Confused between iwlwifi vs iwlagn"
date: 2011-11-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by vikrant82 on 2011-11-24
After upgrading to 3.2 kernel, I seem to get iwlwifi module loaded

```
~$ sudo lshw -c network
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N + WiMAX 6150
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 67
       serial: 40:25:c2:2b:80:a4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-1-generic firmware=41.28.5.1 build 33926 ip=192.168.172.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn

```

Previously on 3.0, I think I used to be on iwlagn module. 

However If I try to manually load iwlagn, 

sudo modprobe -r iwlwifi
sudo modprobe iwlagn

I still end up getting iwlwifi as my loaded module. Are these different or same?

I am concerned as, my connection seems to be less unstable, now. Sometimes, the connection is on, but I dont seem to get any connectivity, unless I reboot.

---

### Post by vikrant82 on 2011-11-24
Additionally any one else getting

```
:~$ sudo update-initramfs -u
[sudo] password for kx: 
update-initramfs: Generating /boot/initrd.img-3.2.0-1-generic
W: Possible missing firmware /lib/firmware/rtl_nic/**rtl8168f-2.fw **for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/**rtl8168f-1.fw **for module r8169

```

?

---

### Post by ptrakk on 2011-11-24
3.2 is pretty unstable due to the lack of support because it is so new. you might need to get your cards firmware and put it in that folder. let me see if i can find them for you.

---

### Post by ptrakk on 2011-11-24
i beleive it is in the linux-firmware package. try "sudo apt-get --reinstall -y install linux-firmware" just my guess.

---

### Post by vikrant82 on 2011-11-24
Nope, I checked that, It seems to have:

rtl8168e-*

and I am missing rtl8168f-*, Although these are not hurting at the moment..

So, I will let them sort themselves out.

Though I am concerned about using the right driver for my wireless card. 

I go to: [http://www.intellinuxwireless.org/?n=Downloads](http://www.intellinuxwireless.org/?n=Downloads)

```
6050 Images &#8211; for Intel Centrino Advanced-N + WiMAX 6250 and Wireless-N + WiMAX 6150
iwlwifi-6050-ucode-41.28.5.1.tgz 	12-13-10 12:58:50 	R L
```

I know this is my card's driver. This has "iwlwifi-6050-5.ucode"

SO how do I build a module out of this ? Dump this in my /lib/firmware and ?

BTW I am using 3.2 kernels in precise repos.

---

### Post by Harry33 on 2011-11-24
I have this lan in my Gigabyte mobo:
  	 	 	 	 	 	    [FONT=Ubuntu][SIZE=2]Realtek 8111DL Gigabit Ethernet[/SIZE][/FONT]
  
That also ought to have the rtl8168 driver.
Linux kernel, however, uses rtl8169 driver, which seems to work well.

---

### Post by MacUntu on 2011-11-24
I remember reading that the iwlagn stuff got renamed to/merged into iwlwifi. Now my status led blinks on transfer ([bug](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/894560)), which makes me go crazy (you can just add a file '/etc/modprobe.d/iwlwifi.conf' with the content 'options iwlwifi led_mode=1'), but the 6300 N adapter works just fine.

---

### Post by Starks on 2011-11-25
btw, wireless-n for the 6000-series is broken and throttles your speed.

[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2329](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2329)

---

### Post by vikrant82 on 2011-11-25
On 6150, I am not seeing throttling, but sometimes the connection just dies after some heavy torrenting, and I can see that its not a problem with router, as other nodes (cell, other laptops) are fine.

Also I am using mixed mode on my router (g/n) for my PS3 to connect. 

Although, In Linux, I get usual connection speeds of 65mbps, where as at the same location, I usually get 130 mbps in Win 7.

---

### Post by Starks on 2011-11-25
It's a rate control problem.

Speed goes down and the connection grinds to a halt as the firmware resets.

---

### Post by grubler on 2011-11-27
> **vikrant82 said:**
> Additionally any one else getting

```
:~$ sudo update-initramfs -u
[sudo] password for kx: 
update-initramfs: Generating /boot/initrd.img-3.2.0-1-generic
W: Possible missing firmware /lib/firmware/rtl_nic/**rtl8168f-2.fw **for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/**rtl8168f-1.fw **for module r8169

```

?

I get the same message, *but does not have a wireless card installed.*

```
per@per-P5E3-Deluxe:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.2.0-2-generic
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168f-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168f-1.fw for module r8169

```

---

### Post by vikrant82 on 2011-11-29
r8169, is the module being loaded for you ethernet card.

---

