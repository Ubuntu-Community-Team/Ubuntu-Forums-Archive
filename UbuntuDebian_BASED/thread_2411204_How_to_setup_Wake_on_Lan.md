---
title: "How to setup Wake on Lan"
date: 2019-01-26
forum: Ubuntu/Debian BASED
---

### Post by emilward on 2019-01-26
I can't figure out how to setup WoL on Pop_OS! 18.04 (ubuntu 18.04). My BIOS has it turned on and my NIC supports it. I have ethtool installed and I have port fowarding setup in my router. All I need now is to setup Ubuntu and that's where I'm having issues. I have tried several different tutorials, including:

[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)
[https://kodi.wiki/view/HOW-TO:Set_up_Wake-on-LAN_for_Ubuntu](https://kodi.wiki/view/HOW-TO:Set_up_Wake-on-LAN_for_Ubuntu)
[https://askubuntu.com/questions/1068900/18-04-lts-upgrade-has-stopped-wol-wake-on-lan](https://askubuntu.com/questions/1068900/18-04-lts-upgrade-has-stopped-wol-wake-on-lan)
[https://www.scivision.co/linux-worldwide-wake-on-lan/](https://www.scivision.co/linux-worldwide-wake-on-lan/)
[http://ubuntuguide.net/remotely-turn-on-ubuntu-from-lan](http://ubuntuguide.net/remotely-turn-on-ubuntu-from-lan)

and none of them work. I have also tried several different video tutorials on YouTube and none of them help either. Can anyone tell me how to setup WoL on Ubuntu 18.04?

---

### Post by wildmanne39 on 2019-01-26
*Thread moved to **Ubuntu/Debian BASED a more appropriate sub-forum**.*

---

### Post by TheFu on 2019-01-27
WoL is an ethernet-only capability.  It cannot be routed.  Basically, only another system on the same LAN segment can send the WoL packets to the NIC using the MAC.

Port forwarding on any router cannot help. Ethernet doesn't traverse routers in the way WoL needs.

---

### Post by emilward on 2019-01-31
My other system is on the same LAN and I only enabled port forwarding for the sake of thoroughness. It's what was suggested in one of the links I provided and even though I was sure it wouldn't matter, I did it just so I knew I've tried everything. WoL works just fine with Windows 10. It's just Ubuntu that I'm having issues with

---

### Post by TheFu on 2019-01-31
So, WoL works on the same machine running a different OS? It isn't perfectly clear.

WoL support is highly connected to the hardware being used, mainly the BIOS settings and exact, specific motherboard, assuming the NIC does support it.

I don't have any extra knowledge than what is in the help.ubuntu.com pages.  I know it worked for me on 14.04 for 3 different systems. I haven't attempted it since (systemd became the default after then). Sorry.

/etc/network/interfaces isn't used in 18.04, netplan is.  Initializing the NIC at boot needs to happen some other way, but you can manually set it in the meantime. I assuming you are doing that and validating it has been enabled.

---

### Post by emilward on 2019-02-01
no I have one machine (running Windows and Ubuntu) that I want to wake up remotely. I also have another PC (and smartphone) that I can "wake up" the remote PC (that is running windows and Ubuntu) when it's booted into Windows but I can't wake it up when it's booted into Ubuntu. In Windows, I can wake up the remote machine from any device connected to the network including my android phone. But I can't get the same functionality to work in Ubuntu

---

### Post by TheFu on 2019-02-01
And the motherboard for the system that won't wake up is?

Perhaps if you gave each computer a name, it would be clearer?  I can't tell if you want to wake both systems when running ubuntu from both of them or if it is just 1 machine that won't wake when running Linux.  I'm so easily confused.

Also, all these are wired ethernet connected, right?

---

### Post by emilward on 2019-02-03
I just want to wake up the PC running Ubuntu. That's it. That's all I want to do. It is connected to my router via ethernet. I would like to wake it up from another PC I have connected to my LAN as well as from my smartphone. My Ubuntu PC is dual-booting with Windows10 and when it is in Windows 10, WoL wokes fine. I can wake it from another PC on my LAN as well as from my smartphone. But when that same PC is running Ubuntu, WoL doesn't work at all.

---

