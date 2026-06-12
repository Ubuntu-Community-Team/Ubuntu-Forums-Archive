---
title: "Linux Smartphones"
date: 2011-03-30
forum: The Cafe
---

### Post by coljohnhannibalsmith on 2011-03-30
Hello,

I am currently wanting to experiment with Linux embedded products.  It is my intention to embed the Zfone telephony encryption product in a number of Linux based SmartPhones.  Part of my proposed experiment will be to enable the promiscuous mode of the WiFi radios, allowing the formation of a Mesh network, with the other SmartPhones and hopefully some Laptops as well.  I suspect I will need a Linux based OS to support such fine-grained control.  Also, the embedded WiFi chipset will need to be able to support this mode as well, which I suspect is controlled by the firmware.

 Can anyone suggest some suitable units?


Thanks, John

---

### Post by coljohnhannibalsmith on 2011-03-30
I'd just thought I'd share my vision with the group.  It's a pipe dream, but I think it's do-able: 

What I'm envisioning is a secure, "utility-less" telecommunications  system, for voice and data communications.  This would be manned not  only by volunteers, but by everyone that carried a phone or Laptop, or  owns a stationary wireless enabled home computer. 

Add to the mix some Meraki, cloud managed, wireless access points,  which are well suited to Mesh networks and mobile use, as vehicle  mounted repeaters, possibly with linear amplifiers; and the phone  companies, with the exception of the long-distance carriers are a  "thing-of-the-past."  The only thing we'd have to pay for is the  electricity. However, the main benefit, hopefully, will be security  against Man-in-the-Middle attacks. 

Also, since the Zfone source-code is published, it may also be  technically possible to advance the encryption algorithm beyond AES256,  latency permitting, by re-writing the encryption algorithm.  The alogorithm could also be re-written to use the highest encryption that the bandwidth of the connection will permit, in an opportunistic manner. 

The ap can then be made available as a download, just like any-other SmartPhone ap. 

Truely a Utopian Paradise! 


John The Dreamer

---

### Post by Johnsie on 2011-03-31
Sounds interesting. How far is the broadcast range for the wifi/chips in mobile phones? How does that range compare to the range of bluetooth?

---

### Post by coljohnhannibalsmith on 2011-04-02
Thanks for the reply,

> **Johnsie said:**
> Sounds interesting. How far is the broadcast range for the wifi/chips in mobile phones? How does that range compare to the range of bluetooth?

I think I know the answer to this.  I believe the range for a WiFi 'Access Point,' is about 200 ft; I'm not sure about WiFi emabled smart phones. For the sake of argument I'm going to assume, for the moment, that the range will be similar. This should work adequately in a sufficiently dense population center. I do know that the power output of a cellphone, using it's native CDMA or TDMA system is adaptive, and this varies from about 500mw - 1000mw, and the range is about 1 1/2 miles, line of sight.  I'm pretty certain that the range of Bluetooth is on the order of about 10ft.  This is so that the original device does not interfere with 'other' Bluetooth enabled devices. The purpose of Bluetooth is just to create a wireless link to a nearby device, to make the device 'cordless;' so an enabled device doesn't need to transmit that much power. I also know that the embedded OS will need to be 'rooted.'

---

### Post by coljohnhannibalsmith on 2011-04-07
After some searching on Google, I discovered the following article:
[SIZE=2]
**The Start to Finish Guide to Rooting Your Android Phone**[/SIZE]

[SIZE=1][http://lifehacker.com/#!5563924/the-start-to-finish-guide-to-rooting-your-android-phone]("http://lifehacker.com/#%215563924/the-start-to-finish-guide-to-rooting-your-android-phone")

Apparently there is an entire community, out-there, involved in doing this.

I've also read that the 'drivers' on Android phones are proprietary and may have to be re-written to allow operation in the Ad-hoc, promiscuous, or monitor modes.  Also, I don't know whether this is controlled by the drivers or the chipset itself, or how to find out.  I guess I'll probably have to start by investing in one of the most likely suspects, and then just experimenting.  The Motorola 'Droid' appears to be a good target for this research, since it has a sizeable community of experienced hackers.

I have downloaded and installed the Android SDK in 'anticipation' of needing it for this purpose:

[http://developer.android.com/sdk/index.html](http://developer.android.com/sdk/index.html)

I've read at least one account of someone having done this successfully.  Also, I've read that the Android store offers an ap, that acts as a "Native Hotspot," allowing the user to wirelessly attach up to 5 individual devices to the Android phone's Internet connection; however, it will only allow these devices to 'share' the Android phone's Internet connection, and not talk to one another, probably to 'prevent' exactly what I'm proposing.

Also, ZiiLABS offers and SDK, a development platform, and what they refer to as an EGG.  The EGG appears to be a bare-bones Smartphone, with the ability to add functional-modules for additional features, and no pre-existing code, allowing the 'developer' to essenial build a system from scratch.  This looks very interesting, but expensive.  I also think they charge for the SDK  'a la carte, which Android doesn't:

[/SIZE][http://www.ziilabs.com/products/software/plaszma/plaszma_sdk.aspx](http://www.ziilabs.com/products/software/plaszma/plaszma_sdk.aspx)

What other embedded Linux OS's are out there for Smartphones, and which are considered to be the best?


Thanks, Hannibal
[SIZE=1]


[/SIZE]

---

### Post by wormyblackburny on 2011-04-07
An interesting thought, but I would think that there would just be too much "noise" for a simple device like a phone to handle. You also mention "electricity" as the only cost. Ever notice how a phone on standby stays charged much longer than a phone in use? If a phone was constantly using its power to retransmit all of these packets of data, it would be dead all the time. The battery technology would need to significantly improve....

---

### Post by coljohnhannibalsmith on 2011-04-07
I haven't thought much about the noise.  I'll probably have to investigate that, after I have a few operational units.  I could probably install a WiSpy Spectrum Analyzer on my Laptop to see a 3D graph of the noise environment.  Also, if I remember correctly 802.11 has something like 22 channels between 2.4 - 2.5 GHz, so it may be possible to load this ISM band pretty densly.

[http://www.metageek.net/products/wi-spy/](http://www.metageek.net/products/wi-spy/)

Oh hey, I just found this as well.  This article looks like it does a good job of addressing the noise issue:

[URL="http://www.eetimes.com/design/microwave-rf-design/4012556/Avoiding-Interference-in-the-2-4-GHz-ISM-Band"]http://www.eetimes.com/design/microwave-rf-design/4012556/Avoiding-Interference-in-the-2-4-GHz-ISM-Band
[/URL]

BTW, you're absolutely correct about the battery life; I've already thought about this, and I believe that there may be many ways to mitigate this problem.  Ideally, at a mature stage, this system would rely primarily on traditional building mounted access points, made expressly available for public use as repeaters, also on vehicle mounted repeaters, so at a mature stage, it would 'not' be necessary to rely entirely on the phone transmitting continuously to function as a repeater.  However, this is probably where we'll have to start.

Here's my first thought on this:

About 15 years or so ago 'fanny-packs' were all-the-rage for the fitness set, because most sweat-suits weren't equipped with pockets, for items like wallets and keys; so maybe the extra batteries could be kept here, at least in the interim?


Hannibal

---

### Post by coljohnhannibalsmith on 2011-04-11
[PPaFin]("http://www.linuxquestions.org/questions/user/ppafin-328852/") from Helsinki, Finland suggested something called FLOW, as a possible hardware platform:

[http://www.gizmoforyou.net/site/en/projects.html?section=filemanager_pro&dir=41&workspace=26](http://www.gizmoforyou.net/site/en/projects.html?section=filemanager_pro&dir=41&workspace=26)

You can't login to get the schematics; but it's reassuring to see that there's somebody else working on a similar project.

Here's what I've been able to retrieve from their site, and it's not much:

1     Initial Information
2     Basic Part Inventory
3     Topology of parts
4     Assembly Drawings
5     Schematic Design
6     PCB Design - Routing
7     PCB Manufacturing
8     Enclosure Manufacturing
9     Assembly
10     Software Development

[B]BTW, I was also able to download the Zfone source and binaries by torrent from here:

[/B][http://thepiratebay.org/torrent/5727745/DEFCON.15_T203_-_The_Zfone_Project_%28Cryptophone%29]("http://thepiratebay.org/torrent/5727745/DEFCON.15_T203_-_The_Zfone_Project_%28Cryptophone%29")

These are currently unobtainable anywhere else, that I'm aware of.


Hannibal

---

