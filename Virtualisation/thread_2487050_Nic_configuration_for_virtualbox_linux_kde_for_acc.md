---
title: "Nic configuration for virtualbox linux kde for accessing internet"
date: 2023-05-21
forum: Virtualisation
---

### Post by HuTkW$* on 2023-05-21
Hello,
.
I have a physical machine with no gateway to internet : private network closed.

I wish to create a virtualbox kde ubuntu and accessing to internet. So what network card NIC  configuration virtualbox for accessing internet is good ? : 'bridge' parameter with ip manual configuration -gateway - does not work .

Any suggestion ? Eventually Route line command configuration ?

Thanks !

---

### Post by ajgreeny on 2023-05-21
Are you saying that your host machine has no network connection to the Internet but you want your guest VM to connect?

If that is correct you will obviously be unable to use the default NAT network configuration of VBox and wil have to use a bridged connection using the hardware of your host (I assume the host does have network hardware), either an ethernet cable connection or a wireless network adapter of some sort.
I have no idea how simple it will be to set that up as I have used the default NAT network on all my VMs in both VBox and now KVM/QEMU apart from testing that it worked in VBox for a single session.

Tell us more about your network hardware on the host machine and you may get more helpful responses than mine.

---

### Post by HuTkW$* on 2023-05-21
Thanks, 
My host -physical machine has cable, connection, and possibility to reach the internet by adding gateway ip address.
I decided my host -physical machine not to reach internet, but work on inside private network, with ip manual configuration : @ip, netmask, only.
I tried : 
Virtual box : kde ubuntu with on Vbox network adapter 'Bridge', mean like other machine network.
I i configure manual ip on virtual  machine  @ip, netmask, gateway, and dns : that does not work ! i can ping machines inside my private network, i can ping gateway, but not the internet : the physical ethernet cable is plugged, 

i am not on Nat because physical nic  configuration has no gateway ?


Question : why virtual machine with network configured 'bridge' cannot reach outside ?
If my pshysical nic do not reach internet, a virtual nic could do it ?

---

### Post by MAFoElffen on 2023-05-22
This, from the Oracle- VirtualBox Doc's might help for the initial setup. 
RE: [https://www.virtualbox.org/manual/ch06.html#network_bridged](https://www.virtualbox.org/manual/ch06.html#network_bridged)

Beyond that, then it comes down to "your local LAN network settings". You say you can ping, so ICMP is not getting stopped, at least to your gateway router. 

Since your internal ntwork is "private", there should not be a problem of sharing your internal IPv4 addressing scheme and info on the internal side of the gateway, right? That may help, in looking into what may be going on.

If you need help with commands to collect that information, just ask.

---

