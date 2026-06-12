---
title: "Problems with wireless access on Pangolin"
date: 2009-05-01
forum: System76 Support
---

### Post by gila_monster on 2009-05-01
Hi, folks. Me again. I'm having trouble connecting to wireless networks with my panp4n. When running with networkmanager, it could see wireless networks, but I could never get it to connect. After searching the networking/wireless forums, I decided to install wicd and give that a try. wicd seems pretty slick, but it apparently can't find my wireless router, even two feet away from it.

Information on my setup:

/etc/network/interfaces:

```

auto lo
iface lo inet loopback

```

sudo lshw -c network:

```

  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 61
       serial: 00:21:5c:46:a9:c9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:90:f5:8d:1e:da
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 46:17:4b:58:d3:f0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:90:f5:8d:1e:da  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fe8d:1eda/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65448 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56653 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68474686 (68.4 MB)  TX bytes:9621211 (9.6 MB)
          Interrupt:248 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:500 (500.0 B)  TX bytes:500 (500.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:5c:46:a9:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5C-46-A9-C9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

If there's something else you need to see, let me know.

I have seen some posts from people who got things to work with either networkmanager or wicd and the 4965, but the solutions seemed to involve loading an older kernel (27) or installing new drivers from the Intel site. I don't want to leap right into that if this is a known issue with a simpler solution.

And if Mr Aaron or someone is willing to indulge my curiosity -- what are the wmaster0 and pan0 devices?

Thanks much for your time. Mods, I posted to System76 support first, but feel free to move to networking and wireless.


UPDATE: I tried booting with the wireless card already on, and today it sees the router! Is it possible that the wireless card needs to be on before wicd starts or it won't see it? gm

---

### Post by thomasaaron on 2009-05-02
> I tried booting with the wireless card already on, and today it sees the router!

Are you sure you have a PanP4? It has no wireless switch.

Also, what version of Ubuntu are you currently running? Network Manager should work well with your PanP4. Wicd should not be necessary (if you are running straight Ubuntu). However, having wicd installed *may* conflict with network manager. I'm not exactly sure, though.

Can you connect wirelessly to other access points? Maybe a free one at a coffee shop?

If it is connecting *sometimes* to one router, it could be a router-related issue.

Right after a connection attempt fails, please go to System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

Your daemon.log should give us an idea as to what is going on.

---

### Post by gila_monster on 2009-05-02
> **thomasaaron said:**
> Are you sure you have a PanP4? It has no wireless switch.

System76 driver says panp4n. It can turn the card on and off with Fn-F11.

> **thomasaaron said:**
> Also, what version of Ubuntu are you currently running? Network Manager should work well with your PanP4. Wicd should not be necessary (if you are running straight Ubuntu). However, having wicd installed *may* conflict with network manager. I'm not exactly sure, though.

Currently on Ubuntu 9.04. wicd does conflict, but I installed from the repositories -- wicd removed network manager at that time.

> **thomasaaron said:**
> Can you connect wirelessly to other access points? Maybe a free one at a coffee shop?

Don't know yet. I think that will be today's experiment if I get through the infinite list of chores.

> **thomasaaron said:**
> If it is connecting *sometimes* to one router, it could be a router-related issue.

That's possible. It's an old Linksys. But the other boxen in the house can see it just fine.

> **thomasaaron said:**
> Right after a connection attempt fails, please go to System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

Your daemon.log should give us an idea as to what is going on.

Can do. Please note, though, that this is not so much a connection problem as it just wasn't seeing the router at all, until this morning. I was able to connect just fine once it found the router. I think a little wardriving may be on the docket today, just to try out other WAPs.

Thanks, Tom!

---

### Post by thomasaaron on 2009-05-02
Thanks you.

You may want to try to boot from a live CD. The wireless card should work pretty flawlessly that way. (And that will eliminate the possibility of a configuration issue.)

If it doesn't work well under the live CD, it is either the router or the wireless card. So, the next step would be to rule out the router.

---

### Post by gila_monster on 2009-05-02
I'll try some experiments and get back to you. How hard is it to replace the wireless card in a panp4n, out of curiosity?

---

### Post by thomasaaron on 2009-05-02
Piece of cake. Gravy train on biscuit wheels. So to speak. ;)

---

### Post by gila_monster on 2009-05-07
Tom, I'm going to fire some data to you by email about this. I was able to do some testing today.

---

### Post by gpstar on 2009-05-07
my bonobo does the same thing ever since installing jaunty. It wont see any wireless networks and I have to do a reboot for it to work properly. Before in Intrepid and Hardy, i'd have to turn on the wireless card with Fn + F11 then refresh the network list and it would work, but Jaunty requires me to reboot for it to work. I'm using Wicd as well.

---

### Post by thomasaaron on 2009-05-08
We don't test with wicd, but if both of you are using it, you might want to consider installing network manager and testing with that.

---Ooops! Just saw your email. Great explanation. Stand by...---

---

### Post by thomasaaron on 2009-05-08
A few quick questions:
1. What version of Ubuntu are you using?
2. Is it a fresh install, or have you upgraded (and if so, how many times)?
3. Are you using 32-bit or 64-bit.

Regarding Network Manager not being able to connect, a few things come to mind. It could be that you've upgraded (as opposed to a fresh install, and some left over cruft has broken network manager). Or maybe you are trying to connect with a router that is having some difficulties. Do you get these symptoms on ANY router? Or just the router at the Tilted Kilt? It would also be a good idea to try and connect wirelessly from a LiveCD. Your card should work great that way, and it would eliminate the possibility of it being a configuration problem (or a cruft-related problem) on your machine. Also, having both wicd and network manager installed at the same time could be effectively crippling network manager. 

Regarding wicd working whenever the wireless switch is on at boot time, it sounds like the computer may either be loading the module in an order that is causing conflict with other modules. Sometimes the order in which modules are loaded is important. (This also could have something to do with having two wireless managers installed at the same time.)

So, in summary, here is what I'd do:
1. Try network manager from a live CD. If it works, a fresh install would cure all of the problems. If not, do you get the same results from a live CD on multiple networks?

2. Two, if you want to use wicd, uninstall network manager to see if the problem continues (with turning on your wireless switch after booting).

---

### Post by gila_monster on 2009-05-08
> **thomasaaron said:**
> A few quick questions:
1. What version of Ubuntu are you using?
2. Is it a fresh install, or have you upgraded (and if so, how many times)?
3. Are you using 32-bit or 64-bit.

1. 9.04
2. Upgraded, no more than twice. (I can't remember if I did a fresh install back in November.)
3. 64-bit.

> Regarding Network Manager not being able to connect, a few things come to mind. It could be that you've upgraded (as opposed to a fresh install, and some left over cruft has broken network manager). 

That's a bit disturbing. Upgrade process seems relatively smooth. Is this a common problem?

> Or maybe you are trying to connect with a router that is having some difficulties. Do you get these symptoms on ANY router? Or just the router at the Tilted Kilt? 

I've had this problem on more than one router. That doesn't rule out the possibility of multiple routers with problems, of course. Restaurants and pubs are not generally known as bastions of technical acumen.

> So, in summary, here is what I'd do:
1. Try network manager from a live CD. If it works, a fresh install would cure all of the problems. If not, do you get the same results from a live CD on multiple networks?

2. Two, if you want to use wicd, uninstall network manager to see if the problem continues (with turning on your wireless switch after booting).

Oh, network manager is thoroughly uninstalled. That's the first thing I tried.

Thanks for the advice. I'll let you know how things go.

---

### Post by gila_monster on 2009-05-10
Tom et alia,

after an evening of wardriving with my lovely spouse, who spent part of her Mother's Day geeking out with me (I soooo married the right woman), I've determined that I have pretty much the same problem with network manager as I do with wicd.

I did a clean install last night, which brought the system to what should be a pristine state. (I did NOT nuke my data, so everything in .gnome and other configuration directories remained as it was.) On three different routers/WAPs, I was able to get a connection through the wireless.

This only worked, however, when the wireless was already on when the system booted. When I turned the wireless off and restarted, network manager never saw the WAPs. This is exactly what I was seeing with wicd.

I'm not sure why I had trouble at Tilted Kilt. It may have been a problem on their end, or it may have been something with the way I booted the system (I may have turned on the wireless card partway through booting).

The workaround is to make sure the wireless is on when I boot and think I will need to access a WAP. Generally, I'd prefer to only turn on the wireless after booting and I see a need (giving me a chance to change the firewall settings). Might be some workaround with ifup/ifdown -- I may play with that later tonight.

---

### Post by thomasaaron on 2009-05-11
I thought I'd test this at home on my GazV5 and ran into the same problem!

Here was my workaround...

Boot up with wireless switch off.
Turn wireless switch on.
Go to a terminal and run...
sudo /etc/init.d/NetworkManager restart

In a few seconds, it whirred to live and found my wap.

Does that work for you?

---

### Post by gila_monster on 2009-05-11
Yes, that does work.

I noticed something odd when I tried this. If I boot the system with the wireless card off, network manager notices that the card is not there (says "wireless is disabled"). When I turn the card on, the "disabled" notification goes away, but the WAPs don't show up in the list until I use the restart workaround.

In short, it knows the card is live, but apparently doesn't know what to do with it!

I also note that once network manager is able to recognize WAPs, you can turn the wireless card on and off to your heart's content, and it will always see them if the card is on.

---

### Post by thomasaaron on 2009-05-11
I'll look to see if there is already a bug report on this. There probably is, but it might be tough to find it.

In the meantime, you might want to create an icon on your desktop that runs the restart command... or a launcher on your upper panel would be a little nicer.

---

### Post by jml on 2009-05-14
Tom, could this be the problem that I wrote System 76 customer support about a few days ago?  I am having very similar problems with my Starling netbook.  And after reading a few other forums I tried and then discarded WICD.  If needed, can I do a clean install with my USB optical drive rather than using a thumb drive?  Thanks for your time.

Joe L.

---

### Post by thomasaaron on 2009-05-15
Hi, jml.

No, I'm positive this is a different issue. Carl sent you an email with some instructions to try on your Starling. How did those go?

---

### Post by jml on 2009-05-15
Thanks for the quick reply, Tom.  I never received Carl's response.  Could you please ask him to resend it to my DeskMedia account?  Or would it be better for me to resend my initial inquiry?

Joe

---

### Post by thomasaaron on 2009-05-15
Please send an inquiry to support(at)system76(dot)com. I'll get some instructions to you.

---

