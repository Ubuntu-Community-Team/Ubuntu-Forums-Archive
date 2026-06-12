---
title: "virtualbox nat not working for xp guest"
date: 2008-08-29
forum: Virtualisation
---

### Post by ilovesocks on 2008-08-29
So I've got VirtualBox running a Windows XP guest on Xubuntu. NAT is supposed to work out of the box, according to my source:

[https://help.ubuntu.com/community/VirtualBox#Networking](https://help.ubuntu.com/community/VirtualBox#Networking)

but I haven't gotten it to work yet. What's strange is that the guest seems to be able to get an IP address (192.168.0.4):

```
C:\Documents and Settings\Sock>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : sock-vbox
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : domain_not_set.invalid

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : domain_not_set.invalid
        Description . . . . . . . . . . . : AMD PCNET Family PCI Ethernet Adapte
r
        Physical Address. . . . . . . . . : 08-00-27-3A-9D-42
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.0.4
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1
        DHCP Server . . . . . . . . . . . : 192.168.0.1
        DNS Servers . . . . . . . . . . . : 192.168.0.1
                                            68.94.156.1
        Lease Obtained. . . . . . . . . . : 29 August, 2008 11:00:26
        Lease Expires . . . . . . . . . . : 30 August, 2008 11:00:26
```

which is different from the host machine's (192.168.0.3). As I understand it, NAT is not supposed to give the guest its own IP. Maybe that's the problem?:


```
br0       Link encap:Ethernet  HWaddr 00:22:15:00:a6:de  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe00:a6de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:644 errors:0 dropped:0 overruns:0 frame:0
          TX packets:683 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:295232 (288.3 KB)  TX bytes:171245 (167.2 KB)

eth0      Link encap:Ethernet  HWaddr 00:22:15:00:a6:de  
          inet6 addr: fe80::222:15ff:fe00:a6de/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:78246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54917 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:105649052 (100.7 MB)  TX bytes:6234690 (5.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79961 (78.0 KB)  TX bytes:79961 (78.0 KB)

tap1      Link encap:Ethernet  HWaddr 00:ff:5b:3f:9a:6d  
          inet6 addr: fe80::2ff:5bff:fe3f:9a6d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69312 errors:0 dropped:70 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:4578929 (4.3 MB)  TX bytes:98214572 (93.6 MB)
```

That bridge does work when I set the guest's network setting to 'Host Interface' with nat1 as the interface name, but with NAT it's no dice. I did try NAT before creating that bridge, but it didn't work.

I would rather use NAT since it's simpler, and the bridge sometimes interferes with the host's connection at boot, which requires me to fiddle around with scripts, bringing things up and down until it works. I don't need to run any servers from Windows, so I'd like to use NAT.

One thing to possibly note is that my ethernet chip is an Atheros (the motherboard is an Asus P5E-VM HDMI), not an Intel. I didn't have any trouble with it until I started fiddling with a bridge.

Any advice on why NAT isn't working would be helpful!


EDIT: I appreciate all the replies, but I decided to switch to vmware server, which set up the bridge for me and works nice and smooth. Problem solved!

---

### Post by reader4 on 2009-01-06
Depending on the issue, you may get more help from the virtualbox forums.  For example:

[http://forums.virtualbox.org/viewtopic.php?p=53408](http://forums.virtualbox.org/viewtopic.php?p=53408)

---

### Post by Dedoimedo on 2009-01-06
Try the following:

Remove the bridge.
Try NAT with eth0 as the host interface.

See if this helps.

Dedoimedo

---

### Post by vipok1980315 on 2009-01-06
We are a professional engaged in Beijing invoice consultation services companies, professional and real and effective invoice, providing strict secrecy mechanism, if you are interested in learn more about Beijing invoice-related information, please visit our company website! Thanks!Acupuncture [[size=1][color=silver]Acupuncture[/color][/size]](http://www.tcmyi.cn/)[size=2] [size=1]&#21271;&#20140;&#21457;&#31080;[/size] [/size][[size=1][color=silver]&#21271;&#20140;&#21457;&#31080;[/color][/size]](http://www.bjzhilv.com/)[size=2] [size=1]&#21271;&#20140;&#21457;&#31080;&#21672;&#35810;[/size] [/size][[size=1][color=silver]&#21271;&#20140;&#21457;&#31080;&#21672;&#35810;[/color][/size]](http://www.bjzhilv.com/) &#27668;&#27169; [[size=1][color=silver]&#27668;&#27169;[/color][/size]](http://www.cnqimowang.com/) Traditional Chinese Medicine [[size=1][color=silver]Traditional Chinese Medicine[/color][/size]](http://www.tcmyi.cn/)

---

