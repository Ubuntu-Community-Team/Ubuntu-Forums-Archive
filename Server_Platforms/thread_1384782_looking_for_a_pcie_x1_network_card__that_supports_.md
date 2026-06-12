---
title: "looking for a pcie x1 network card  that supports tcp offloading"
date: 2010-01-18
forum: Server Platforms
---

### Post by markp1989 on 2010-01-18
my servers cpu gets woken up alot (acording to powertop) by eth0 when downloading files, i figured i could get a cheap pci card that supports offloading.

any recomendations?

thanks :D

---

### Post by cariboo on 2010-01-18
You may be able to set up off loading with the nic you have, have a look [here]("http://wiki.wireshark.org/CaptureSetup/Offloading").

---

### Post by markp1989 on 2010-01-18
thaks for the reply, i didnt think that onboard network cards supported it .

this is after i have used ethtool --offload to set every offload setting to on, i dont know how much this will help.  i will find out later :D 


```
mark@torrentslave:~$ sudo ethtool --show-offload eth0
Offload parameters for eth0:
Cannot get device flags: Operation not supported
rx-checksumming: on
tx-checksumming: on
scatter-gather: on
tcp-segmentation-offload: on
udp-fragmentation-offload: off
generic-segmentation-offload: off
generic-receive-offload: off
large-receive-offload: off
mark@torrentslave:~$ 
```

edit :after doing this my pc lost internet access?

---

### Post by Xianath on 2010-01-19
What's your onboard NIC? I've seen tons of problems with Broadcom NexTreme II cards with TSO enabled, and maybe others have it, too. To make a long story short, the NIC TSO engine completely ignores kernel TCP/IP tunables, and particularly those pertaining to Path MTU Discovery (PMTUD). As a result, if you're unlucky enough to be using protocol encapsulation (which you are if you have any kind of modem) and your ISP blocks ICMP completely (particularly, type 3 "Destination host unreachable" message 4 "Please fragment"), then yes, you'll lose Internet access unless you set your MTU to 576 which is ridiculous but, amazingly, works. This is obviously a shot in the dark but without a network capture that's the best I got at the moment.

Cheers,
Peter

---

### Post by markp1989 on 2010-01-19
> **Xianath said:**
> What's your onboard NIC? I've seen tons of problems with Broadcom NexTreme II cards with TSO enabled, and maybe others have it, too. To make a long story short, the NIC TSO engine completely ignores kernel TCP/IP tunables, and particularly those pertaining to Path MTU Discovery (PMTUD). As a result, if you're unlucky enough to be using protocol encapsulation (which you are if you have any kind of modem) and your ISP blocks ICMP completely (particularly, type 3 "Destination host unreachable" message 4 "Please fragment"), then yes, you'll lose Internet access unless you set your MTU to 576 which is ridiculous but, amazingly, works. This is obviously a shot in the dark but without a network capture that's the best I got at the moment.

Cheers,
Peter

this is my  on board network card.

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

i disabled offloading for tx and that gave my internet back

the mtu for my modem is 1500 if that was what you were asking

thanks for your help, i wasnt aware that onboard network cards could support offloading

---

