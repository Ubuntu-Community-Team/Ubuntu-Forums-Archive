---
title: "usb vs. pci wireless, what's the difference"
date: 2006-02-24
forum: The Cafe
---

### Post by cityismine on 2006-02-24
What's the difference in usb and pci wireless adapters? I wanna get a wireless router, but don't know which adapter to get. What are the pros and cons of both?

---

### Post by Marshall2day on 2006-02-24
I'm not sure but I'll think you'll have better hardware support on PCI devices then you will on USB. I also think that PCI will give you a broader reception range then USB will since the antenna is bigger.

---

### Post by dosed150 on 2006-02-24
well the only difference is ones internal  ones external

---

### Post by majikstreet on 2006-02-24
PCI is better if you are going to use linux... I haven't had too good experience getting USB dongles to work with ndiswrapper... PCI is nicer for me..

---

### Post by Mr. Electric Wizard on 2006-02-24
[QUOTE=majikstreet]PCI is better if you are going to use linux... I haven't had too good experience getting USB dongles to work with ndiswrapper... [/QUOTE]

Me neither

---

### Post by jeremy on 2006-02-26
[QUOTE=majikstreet]PCI is better if you are going to use linux... I haven't had too good experience getting USB dongles to work with ndiswrapper... PCI is nicer for me..[/QUOTE]
Which are the easiest PCI wireless cards to set up in ubuntu?

---

### Post by nickle on 2006-02-26
[quote=jeremy]Which are the easiest PCI wireless cards to set up in ubuntu?[/quote] 
One obvious difference in the set up is that you just plug in the USB, but you have to open your computer (once) to insert the PCI card. If that doesn't bother you then PCI has an advantage that is is actually in the box, whereas the USB is "dangling" somwhere outside; the former is neater in my opinion. However, (as with everything) this can be an advantage if your wlan signal is not strong; through appropriate placement, the USD bevice might get a better signal than the PCI card antenna which is at the back of the computer under the table. I don't think this should be an issue but keep it in mind.

Hal has become very good at detecting attached devices, so there should not be a difference there. The rest of the setup depends on whether the chip is supported by a native linux driver or not. If you chip is supported (as for example atheros), the card should be recognised immediately. If the chip is not supported then you have to use the windows driver using ndiswrapper (there are several good howto's here for this). This is slightly more difficult
Once the driver business has been sorted out, then its a question of configuration. I see no reason why that should be different for PCI vs USB.

If you have USB2.0 on your computer, ensure you get a wifi card that is USB2.0 compatible, this will make a big difference in throughput and performance.

---

### Post by prizrak on 2006-02-26
Just make sure it uses Atheros chipset as it is fully supported by Linux.

---

### Post by Teroedni on 2006-02-26
I cannot give you a advice as i dont know
But i can tell you about mine

I got one Dwl-G122 usb wireless Dlink
Its runs on a athlonxp comp(32bit) and yust work tm
This is on Dapper. I did not need to add anything to get it working:)

I also got one Linksys wireless wusb54g rev 4(usb)
This runs on a Turion 64(64 bits )
It is much more unstable. It sometimes lose the connection so i have to ipdown and ipup again to make it work. But lately it have seem to work better. It may be that the drivers on 64 bits make it unstable, perhaps

I advise you to buy the Dwl-G122 if you go for external(Usb);)

---

### Post by ssam on 2006-02-26
[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

i'd recomend PCI, USB may bottlenect your network speed.

---

### Post by CompShrink on 2006-02-26
[QUOTE=ssam][https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

i'd recomend PCI, USB may bottlenect your network speed.[/QUOTE]
Um... Assuming we're talking about USB 2, not 1.1 or 1, no it won't. Not at all.

USB 2 is 400mbit. You won't find consumer wireless at faster than 400mb/sec. Normal 802.11G (the most common "wifi" for those who don't know) is 54mbit, and rarely reaches that.

It's a matter of preference. The main advantages of each have already been adressed.

USB doesn't have quite as much support as PCI, but not 100% of PCI network cards are supported either. Find a few you might want to buy, and then search for their model numbers, see if they work well in linux. just a search for the model number and linux in google will often bring up useful info, if you click several links and look around.

A lot work under ndiswrapper from the windows INF files, but this support isn't as good as the ones with native drivers. If you can find a good priced one that doesn't need ndiswrapper that's best. If you don't want to go to that much effort, ndiswrapper is acceptable for most people.

Sorry it's not a simple answer. Wireless is still a bit under supported in Linux.

---

### Post by LordHunter317 on 2006-02-26
[QUOTE=Marshall2day]I'm not sure but I'll think you'll have better hardware support on PCI devices then you will on USB. I also think that PCI will give you a broader reception range then USB will since the antenna is bigger.[/QUOTE]Yes, but it's rarely higher gain and that's all that matters.

The only advantage of buying a PCI card with a reverse-SNA connector is that you can put a higher gain antenna on it.

[quote=Compshrink]Um... Assuming we're talking about USB 2, not 1.1 or 1, no it won't. Not at all.

USB 2 is 400mbit. You won't find consumer wireless at faster than 400mb/sec. Normal 802.11G (the most common "wifi" for those who don't know) is 54mbit, and rarely reaches that.

It's a matter of preference. The main advantages of each have already been adressed.[/quote]No, that's no true.  USB 1 is only 1.5 Mb/s.  USB 1.1 is only **12 Mb/s** which is slower than a 802.11g device.  All 802.11g devices are USB 2.0 Hi-Speed devices, and require USB 2.0 ports.  Ignoring the limited network speed, most 802.11g USB dongles will perform terrible on a USB 1.1 port, because they simply aren't prepared to deal with the slower speed bus.

However, once you're on a USB 2 port, you're quite correct in the fact that USB is no longer the bottleneck.

---

### Post by majikstreet on 2006-02-26
I have a Linksys WMP11 version four PCI card on *two* linux computers. It's easy as anything once you get the hang of ndiswrapper :D

All you have to do is get the drivers, unzip them, install ndiswrapper from the ubuntu cd, install the drivers, modprobe ndiswrapper, and bring up the interface.. it's easy. then you can add some stuff into your /etc/network/interfaces
here's the part of mine relevant to this:
auto wlan0
iface wlan0 inet static
 address 192.168.2.6
 network 192.168.2.0
 netmask 255.255.255.0
 broadcast 192.168.2.255
 gateway 192.168.2.1
 wireless_essid wireless
 wireless_mode Managed

now of course you can change static to dhcp, and get rid of address, network, netmask, broadcast, and gateway - but I was having issues with dhcp, some being that my router was being an a#@hole and not giving me the  correct ip address that I defined... but what ever works for you :D

and now there's ndisgtk too :D

---

