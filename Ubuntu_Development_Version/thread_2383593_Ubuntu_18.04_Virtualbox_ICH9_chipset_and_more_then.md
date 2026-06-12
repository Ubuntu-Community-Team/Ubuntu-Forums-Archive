---
title: "Ubuntu 18.04 Virtualbox ICH9 chipset and more then 8 NICs"
date: 2018-01-27
forum: Ubuntu Development Version
---

### Post by Andrew_Welham on 2018-01-27
I'm testing with the early release of Ubuntu 18.04, and having difficultly with net plan and more than 8 interfaces..
 I am using the **ICH9 chipset** with in virtualbox (Latest version) to enable up to 36 nics

my netplan file look like
```
 # This file describes the network interfaces available on your system# For more information, see netplan(5).
network:
 version: 2
 renderer: networkd
 ethernets:
   enp0s3:
     dhcp4: no
     dhcp6: no
     addresses: [192.168.0.3/24]
     gateway4: 192.168.0.1
     nameservers:
         addresses: [dnsserver1,dnsserver2]
   enp0s8:
     dhcp4: no
     dhcp6: no
     addresses: [192.168.1.3/24]
     gateway4: 192.168.1.1
     nameservers:
         addresses: [dnsserver1,dnsserver2]
   enp0s9:
     dhcp4: no
     dhcp6: no
     addresses: [192.168.2.3/24]
     nameservers:
         addresses: [dnsserver1,dnsserver2]
   enp0s10:
     dhcp4: no
     dhcp6: no
     addresses: [192.168.3.3/24]
     nameservers:
         addresses: [dnsserver1,dnsserver2]
   enp0s16:
     dhcp4: no
     dhcp6: no
     addresses: [192.168.4.3/24]
     nameservers:
         addresses: [dnsserver1,dnsserver2]
   enp0s17:
     dhcp4: no
     dhcp6: no
     addresses: [192.168.5.3/24]
     nameservers:
         addresses: [dnsserver1,dnsserver2]
   enp0s18:
     dhcp4: no
     dhcp6: no
     addresses: [192.168.6.3/24]
     nameservers:
         addresses: [dnsserver1,dnsserver2]
   enp0s19:
     dhcp4: no
     dhcp6: no
     addresses: [192.168.7.3/24]
     nameservers:
         addresses: [dnsserver1,dnsserver2]
   enp2s0:
     dhcp4: no
     dhcp6: no
     addresses: [192.168.8.3/24]
     nameservers:
         addresses: [dnsserver1,dnsserver2]


```
The dns server values have been removed
it all generates ok
and all works except  for the interface   enp2s0
Even if i remove the interface enp0s19 to make 8 interfaces the last entry does not work

if i manually configure with ifconfig enp2s0 192.168.8.3
it works, so it look slike netplan

any guidance on my error ?

---

### Post by Andrew_Welham on 2018-01-27
I've just tried another config whee my netplan file looked like 
```
# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
 version: 2
 renderer: networkd
 ethernets:
   enp2s0:
     dhcp4: no
     dhcp6: no
     addresses: [192.168.8.3/24]
     nameservers:
         addresses: [dnsserver1,dnsserver2]
```

and it did not work, so it look like netplan and the interface name / card type as virtualbox has a different card selected for this interfaces.
the first 8 are Intel PRO/1000 and virtual box has selected PCnet-FAST III for this interface ?

any ideas?

---

### Post by slickymaster on 2018-01-27
*Thread moved to **Ubuntu Development Version**.*

---

### Post by Andrew_Welham on 2018-01-27
tried the virtual box guest additions 

netplan --debug apply produces something strange for enp2s0

```
DEBUG:netplan generated networkd configuration exists, restarting networkd
DEBUG:no netplan generated NM configuration exists
DEBUG:device enp0s17 operstate is up, not replugging
DEBUG:netplan triggering .link rules for enp0s17
DEBUG:device enp0s8 operstate is up, not replugging
DEBUG:netplan triggering .link rules for enp0s8
DEBUG:device enp0s18 operstate is up, not replugging
DEBUG:netplan triggering .link rules for enp0s18
DEBUG:device enp0s16 operstate is up, not replugging
DEBUG:netplan triggering .link rules for enp0s16
DEBUG:device enp0s9 operstate is up, not replugging
DEBUG:netplan triggering .link rules for enp0s9
DEBUG:device lo operstate is unknown, not replugging
DEBUG:netplan triggering .link rules for lo
DEBUG:device enp0s10 operstate is up, not replugging
DEBUG:netplan triggering .link rules for enp0s10
DEBUG:device enp0s3 operstate is up, not replugging
DEBUG:netplan triggering .link rules for enp0s3
DEBUG:replug enp2s0: unbinding 0000:02:00.0 from /sys/bus/pci/drivers/e1000
DEBUG:replug enp2s0: rebinding 0000:02:00.0 to /sys/bus/pci/drivers/e1000
DEBUG:device enp0s19 operstate is up, not replugging
DEBUG:netplan triggering .link rules for enp0s19
```

---

### Post by Andrew_Welham on 2018-01-27
when you  go in the
[COLOR=#000000]/sys/bus/pci/drivers/e1000[/COLOR]
directory you get 
```
# ls -als /sys/bus/pci/drivers/e1000
total 0
0 drwxr-xr-x  2 root root    0 Jan 27 13:12 .
0 drwxr-xr-x 27 root root    0 Jan 27 13:02 ..
0 lrwxrwxrwx  1 root root    0 Jan 27 13:11 0000:00:03.0 -> ../../../../devices/pci0000:00/0000:00:03.0
0 lrwxrwxrwx  1 root root    0 Jan 27 13:11 0000:00:08.0 -> ../../../../devices/pci0000:00/0000:00:08.0
0 lrwxrwxrwx  1 root root    0 Jan 27 13:11 0000:00:09.0 -> ../../../../devices/pci0000:00/0000:00:09.0
0 lrwxrwxrwx  1 root root    0 Jan 27 13:11 0000:00:0a.0 -> ../../../../devices/pci0000:00/0000:00:0a.0
0 lrwxrwxrwx  1 root root    0 Jan 27 13:11 0000:00:10.0 -> ../../../../devices/pci0000:00/0000:00:10.0
0 lrwxrwxrwx  1 root root    0 Jan 27 13:11 0000:00:11.0 -> ../../../../devices/pci0000:00/0000:00:11.0
0 lrwxrwxrwx  1 root root    0 Jan 27 13:11 0000:00:12.0 -> ../../../../devices/pci0000:00/0000:00:12.0
0 lrwxrwxrwx  1 root root    0 Jan 27 13:11 0000:00:13.0 -> ../../../../devices/pci0000:00/0000:00:13.0
0 lrwxrwxrwx  1 root root    0 Jan 27 13:11 0000:02:00.0 -> ../../../../devices/pci0000:00/0000:00:19.0/0000:02:00.0
```


where you can se the first 8 nics, and then the 9th which looks different

---

### Post by slickymaster on 2018-01-29
Andrew_Welham, please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting terminal output

---

### Post by Andrew_Welham on 2018-02-18
I found the answer in the end. Virtualbox for nics over 8 does not have the cable set as connected, and so the kernel will not assign an IP. 
The command
```

VBoxManage modifyvm vmname --cableconnected9 on

```
worked for me

---

