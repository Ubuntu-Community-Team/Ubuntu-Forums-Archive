---
title: "XP´s can´t get internet-connection"
date: 2011-08-05
forum: Virtualisation
---

### Post by coc1961 on 2011-08-05
I have UBUNTU 64 desktop + 12 gb.ram. I like to have several xp with connection to a MS 2003-server. On 2003-server there is a DHCP, DNS and WINS server

I have made one xp. Bridge to ubuntu and the XP with nat. Working perfect.

I have made another xp. All OK but not the connection to the internet. I have access to all the 2003-server files etc. I can ping the host´s and the router but not the internet-ip´s. This XP is a clone of the XP with no problems. Only the IP and the MAC is different.

If I turn off the XP with no problems and start another XP with the sam configuration, I still can´t connect to the internet.

I´m confused :confused:

---

### Post by lmarmisa on 2011-08-06
Try to switch to bridged adapter mode the network setups of your virtual machines. So, both XP virtual machines will be directly connected to the subnet of your MS 2003 server.

BTW, what virtualization program are you using?.

Best regards,

Luis

---

### Post by coc1961 on 2011-08-07
I´m using virtualbox. The one XP don´t have internet connection anymore )-: The virtualbox´s XP is now both bridge. The XP´s ar register in the 2003´s DNS. The XP´s can ping the internals host. XP A can ping XP B. XP B can´t ping XP A, but that´s proberly something I have done. None of the XP´s can join the internet.

---

### Post by lmarmisa on 2011-08-07
Could you post the results of the commands **ipconfig /all** on both XPs?.

```

C:\Documents and Settings\luis>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : XPENG
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : AMD PCNET Family PCI Ethernet Adapte
r
        Physical Address. . . . . . . . . : 08-00-27-40-5D-5D
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.2.71
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.2.1
        DHCP Server . . . . . . . . . . . : 192.168.2.1
        DNS Servers . . . . . . . . . . . : 192.168.2.1
        Lease Obtained. . . . . . . . . . : Sunday, August 07, 2011 8:32:08 PM
        Lease Expires . . . . . . . . . . : Monday, August 08, 2011 8:32:08 PM

C:\Documents and Settings\luis>


```

---

