---
title: "Weak wireless on Wild Dog"
date: 2010-05-31
forum: System76 Support
---

### Post by jbraswell on 2010-05-31
Sorry, wireless has been done to death, but...

I recently moved my Wild Dog into a different room, so it's using a wireless connection now.  It sees everything it's supposed to, and it connects, but the signal is rather weak (40-50%), and it occasionally drops and has to reconnect.  My Starling has 90%+ connectivity when it's in the exact same spot. Naturally, both are using the same WPA-encrypted network.

The usual output:

```
jbraswell@jbraswell-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1c:c0:91:15:ad
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.3-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:30 memory:e0300000-e031ffff memory:e0324000-e0324fff ioport:30e0(size=32)
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:1e:58:96:50:1d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.32-22-generic firmware=N/A ip=192.168.1.104 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:e0000000-e000ffff
```

What am I doing wrong?

Thanks

Just to add, I'm running 10.04, and contrary to some of the other recent wireless complaints, the speed is fine while there is an established connection.

---

### Post by thomasaaron on 2010-06-01
Do you have the little black antenna connected to the back of it?
How far are you from the wireless access point?

---

### Post by jbraswell on 2010-06-01
Yes, indeed. It's 20-25 ft from the AP.

---

### Post by thomasaaron on 2010-06-02
OK. Sorry to ask (about the antenna). I've got to. :P

Since your connection quality fluctuates (good sometimes, not so good other times), I think we should rule out the access point itself.

Even if other systems are successfully using it, please unplug it. Let it sit for a minute or two. Then plug it back in and let it initialize.

Does that stabilize the connection?

Also, do you have another AP you can test with.

---

### Post by juelze on 2010-06-02
> **jbraswell said:**
> Yes, indeed. It's 20-25 ft from the AP.

I use ethernet on my PC, so my point is moot.  However, my Meerkat Ion is about 10 feet away from my wifi router and it generally shows 1 bar of signal.  You'd think that at 10 feet away you'd have full signal strength.  Oh well, just thought I'd mention this here.

---

### Post by tmette on 2010-06-02
I had trouble with the WiFi on my Meerkat Ion as well.  When I was right next to the router (within 2 feet) it would connect.  Tom talked to me on the phone and told me to make sure the wire coming from the antenna to the wifi chip wasn't loose.

It wasn't loose, but I changed it from the Aux (2) port to the Main (1) port.  After that I've had GREAT wifi connection.  I've been getting a constant 2-3 bars from 2 floors up and on the opposite end of the house.  I'm up in my bedroom, and our router is down in our basement on the other end.

---

### Post by jbraswell on 2010-06-03
OK, all good suggestions.  Let me give these a try.

tmette, what port are you talking about? The wire from the antennae inside the case?

---

### Post by tmette on 2010-06-03
> **jbraswell said:**
> OK, all good suggestions.  Let me give these a try.

tmette, what port are you talking about? The wire from the antennae inside the case?

Well, you may not have the same type of wifi card that I have in my Meerkat Ion.  Basically, when I open up the computer, there is a single black wire, coming from the antenna that sticks out the back of the computer, and connects to a wifi chip on the motherboard.  There are two little connectors on that wifi chip.  One that says Main and the other says Aux (I assume stands for Auxillary).  Mine was originally set to Aux, so I just popped it off and snapped it on Main.  Ever since, I have had excellent signal strength.

Yours might be set to the right one, but you never know, it might have come loose when you moved the Wild Dog from one room to the other.

---

### Post by thomasaaron on 2010-06-03
juelze, tmette's suggestion was a good one. I'd give it a try. It looks like somebody at the mfg facility may have put the antenna wire on the wrong nipple on the wireless card on a few Ion's.

jbraswell, they have a completely different wireless card than you. The Ion has a laptop wireless card. Your system has a PCI card.

---

### Post by tmette on 2010-06-03
> **thomasaaron said:**
> juelze, tmette's suggestion was a good one. I'd give it a try. It looks like somebody at the mfg facility may have put the antenna wire on the wrong nipple on the wireless card on a few Ion's.

jbraswell, they have a completely different wireless card than you. The Ion has a laptop wireless card. Your system has a PCI card.

Thanks for clearing that up, I didn't think the Wild Dog had the same wireless card as the Meerkats.

---

### Post by jbraswell on 2010-06-04
Hmmm, I'm reading a signal of about 61% now, which is a wee bit stronger than before.  I'll let this run for a day or so and see what happens.  I don't really have any other APs to test it on.  I guess I could see if any of my neighbors are using WEP. :)

---

### Post by juelze on 2010-06-04
> **thomasaaron said:**
> juelze, tmette's suggestion was a good one. I'd give it a try. It looks like somebody at the mfg facility may have put the antenna wire on the wrong nipple on the wireless card on a few Ion's.

jbraswell, they have a completely different wireless card than you. The Ion has a laptop wireless card. Your system has a PCI card.

Thomas, I looked and I have an "ANT 1" and "ANT 2" nipple on the card, but I didn't try changing it.  If I run straight wi-fi I'll try moving the wire, but for now (since I'm running ethernet) I won't bother since the plug-in is so darn tiny!

---

### Post by jbraswell on 2010-06-04
Er, got bumped off again this morning.  

I'm thinking it's not the AP, just because i) my netbook is always over 80%, even when it's much further away, and ii) even though I can't connect to them, my neighbors' signal strengths all look low. 

I guess I should try temporarily turning off WPA.  If that doesn't work, I could try switching the antennae or the card itself.

---

### Post by jbraswell on 2010-06-04
Well, turning off encryption didn't work.

Actually, you know, this is silly...I still have a G router, so I need to buy a new one anyway.  That should completely rule out the AP.

In case it turns out to be the card, what's a good usb wifi adapter that is likely to play well with my machine without too much pain?

---

### Post by jbraswell on 2010-06-06
OK, brand new router. Netbook still rocks no matter how far away from the AP it is inside my house.  Desktop, however, still sucks.  In fact, it looks like it may be worse; as I'm typing this, I'm at 37%.  

Wireless adapter? Bigger/newer antennae?

---

### Post by isantop on 2010-06-07
The Wi-fi card in our Wild Dog in the shop has three antenna ports on it. try picking up some extra antennae somewhere (they should be cheap) and make sure you have one in each of them. If you can't, try moving the antenna around, checking different ports, etc. Check the connection strength after each adjustment.

---

### Post by jbraswell on 2010-06-07
I just bought a foot-long, high-gain phallus of an antennae that I'll try tonight.  If that doesn't work, we can probably rule out the antennae.  

If it doesn't, have you guys frequently used any particular kind of usb wireless adapter? Something that plays well with everything?  If so, I'll give that a shot, too, before I bug you again.

Thanks for the help!

---

### Post by isantop on 2010-06-07
Definitely rule out that antenna!

If you want to go USB wireless, there is a list of devices that seem to work well with linux [urlhttp://wireless.kernel.org/en/users/Devices/USB]Here[/url]. I haven't tried any of them, but supposedly they do work. I'd look at a few reviews before I went and bought one.

---

### Post by jbraswell on 2010-06-08
Well, the situation definitely improved. I'm typically sitting at about 60%, and while I was using it last night, at least, I didn't get dropped.

As long as I don't drop again, I can live with this, but it's still weird...the antennae is about a foot long and has an extension that let's it rest on top of my desk.  I should be getting Japanese TV with this thing, but the signal on my Starling is still way stronger in the same location.

Oh well. Thanks for the help. I'll let you know if I start dropping again.

---

### Post by thomasaaron on 2010-06-09
> I just bought a foot-long, high-gain phallus of an antennae that I'll try tonight.

Was that a Freudian slip? :lolflag:

You're killing me here! ;)

---

### Post by jbraswell on 2010-06-10
No slip, there.  Seriously, this is the one I got: 
[http://www.nextag.com/D-LINK-ANT24-0700-603463462/prices-html?nxtg=eeb0a24051a-1199BBC9C6EBCBB3]("http://www.nextag.com/D-LINK-ANT24-0700-603463462/prices-html?nxtg=eeb0a24051a-1199BBC9C6EBCBB3")

I briefly dropped yesterday when the signal was hanging around %50, but that was the only time so far, and it's quickly reacquired a connection, so this seems alright.

---

