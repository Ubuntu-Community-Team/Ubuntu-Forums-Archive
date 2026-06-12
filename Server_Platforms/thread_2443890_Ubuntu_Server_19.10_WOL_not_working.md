---
title: "Ubuntu Server 19.10: WOL not working"
date: 2020-05-21
forum: Server Platforms
---

### Post by wizzlepot on 2020-05-21
Hello everybody,

I installed Ubuntu Server 19.10 on a machine and I am trying to get WOL working.

I set the BIOS correctly and the Wake-on to G for the relevant ethernet card.

Here is my "ethtool <ethCard>" output:

```

        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: Symmetric Receive-only
        Supports auto-negotiation: Yes
        Supported FEC modes: Not reported
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: Symmetric Receive-only
        Advertised auto-negotiation: Yes
        Advertised FEC modes: Not reported
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
                                             1000baseT/Half 1000baseT/Full
        Link partner advertised pause frame use: Symmetric Receive-only
        Link partner advertised auto-negotiation: Yes
        Link partner advertised FEC modes: Not reported
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
                               drv probe ifdown ifup
        Link detected: yes



```

here is the relevant output of lspci:

```

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)

```

I installed the r8168-dkms packaged, which I found loaded through lsmod.


I connected the machine via an ethernet cable to another one, set them on the same network (tested through ping) and the tried with both the linux Wakeonlan command and with a "Wake on Lan" windows appllication. Both failed.

Previously, I tried the same but using a windows installation. With Windows on this machine the WOL worked, therefore the BIOS is ok.

Does anyone have any idea?

Thanks in any case :)

---

### Post by mörgæs on 2020-05-22
HI, welcome to the fora.

Before you put more time into 19.10: This release has only two months of support left. Have you considered beginning with a clean install of 20.04?

---

### Post by SeijiSensei on 2020-05-23
Are you building a server with WOL? My servers are always available 24/7. To my mind, that's part of the definition of a "server." Usually WOL is a client-side technology.

---

### Post by wizzlepot on 2020-06-05
Hi, thank you for the reply, no I did not. If I remember well the 19.10 was the latest when I started configuring it :D , anyway I guess I can upgrade to that, right?

---

### Post by wizzlepot on 2020-06-05
Hi SeijiSensei, thanks for the reply.
Yes that is my personal little server of home, I wanted a computer acting as a server for whatever I want to store there which is important to me.
Since till now I don't need it always up and running (thanks Git :p ) I would like to being able to do the WOL.

---

### Post by LHammonds on 2020-06-05
Any of this helpful?

[How to setup wake on lan for ubuntu](https://kodi.wiki/view/HOW-TO:Set_up_Wake-on-LAN_for_Ubuntu)
[How to enable wake on lan in ubuntu 18.04](https://www.techrepublic.com/article/how-to-enable-wake-on-lan-in-ubuntu-server-18-04/)
[How  to enable wake on lan in ubuntu 16.04](https://askubuntu.com/questions/764158/how-to-enable-wake-on-lan-wol-in-ubuntu-16-04)

---

### Post by wizzlepot on 2020-06-28
Hello everyone,


so....I installed the Ubuntu Server 20.4 LTS, and followed the link [https://askubuntu.com/questions/764158/how-to-enable-wake-on-lan-wol-in-ubuntu-16-04](https://askubuntu.com/questions/764158/how-to-enable-wake-on-lan-wol-in-ubuntu-16-04) on how to enable the "wake-on: g" option in the output of the "**sudo** ethtoo *myinterfac*". I wrote "sudo" in bold cause without it does not state that parameter.
Again I installed the r8196-dkms package, reboot the system, them powering it off.
Using a windows wol program to send the package the system does not wake up.

Do you have any idea?

Thanks in any case :)

---

### Post by Tadaen_Sylvermane on 2020-06-28
I'd suggest going through your bios / efi again. I had a hell of a time getting it to work on a couple of my media center machines. It wasn't just a single setting, rather 2 or 3 different ones in entirely different menus.

---

### Post by wizzlepot on 2020-08-18
Hi all, actually as Tadaen_Sylvermane  suggested was a bios issue, setting the right settingS now works.
Thanks everyone for the ideas :)

---

