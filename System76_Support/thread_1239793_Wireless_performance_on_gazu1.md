---
title: "Wireless performance on gazu1"
date: 2009-08-13
forum: System76 Support
---

### Post by jmwink on 2009-08-13
Hi gang,

Been having some issues with the wireless on my gazu1. First was the issue with Gnome Network Manager and keyring, which I haven't completely been able to disable. A workaround was able to mostly disable that default keyring popup on my most used networks, but any advice on how to completely disable the keyring would be helpful. 

The issue however is a bit more substantial than one of software. This morning, I was booted off of my home network, and didn't have time to really troubleshoot the issue because I had to catch a plane. But, in the airport, I noticed I was unable to connect to any of the hotspots (my partner was able to on her computer running XP). Then, when I got here to my folks' house, I wasn't able to connect to their home network unless I sit here in the same room as the router. It reminds me of what people were talking about re: the Starling Netbook. I wondered if there were any other reports of wireless difficulties on the Gazelle, and/or if there were any plans to implement a similar fix.

If this generates some conversation, I have a few more questions to discuss, but I feel like there's enough here to get things started. 

Just in case someone wants them, I'll attach my logs file.

---

### Post by thomasaaron on 2009-08-14
There is no realtionship between the Starling's ex-wireless problem and anything happening on the Gazelle.

Different wireless card, different drivers, different symptoms.

However, your problem is either configuration-related or hardware related. Let's make sure a configuration isn't hosed...

> To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

NOTE:
Unless you are dealing with static IP addresses (which is pretty rare for the
general end-user) you should NOT establish a network connection by going to
System > Administration > Network.

Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little
computer monitor).   

You also might want to try booting from a Live Ubuntu CD and see if your wireless works better that way. If it does, we have a configuration issue. If it doesn't, we may need to get you a new wireless card, as the card in the Gazelle is supported out of the box with Ubuntu; we don't do anything to it.

---

### Post by jmwink on 2009-08-14
Hi Thomas,

Thanks for the help. Here's the entirety of my /etc/network/interfaces file:
```

auto lo
iface lo inet loopback

```

I'll try a livecd and see if that improves any of my performance. In the few hours since writing my previous post, I have seen a bit of improvement in wireless performance, but I'm still being outperformed by 5 year old XP laptops. Are there any other config files you think might be worth digging into?

Thanks again for the prompt help.

---

### Post by thomasaaron on 2009-08-14
Not really.

I'd also suggest trying on some different routers just to make sure we're not dealing with a router issue.

(I know what you're thinking :popcorn:) But I've been seeing issues lately where routers have some computers working well on them while other's can't connect at all or get poor performance. Resetting the router sometimes helps. Sometimes replacing it does too.

---

### Post by jmwink on 2009-08-14
I've long since ceased being surprised by any quirks in the wireless networking realm. When I get back to my home office next week, I'll see if this issue has resolved itself on its own, or if I need to set up the AT&T U-Verse Residential Gateway as a modem and use my own router, or something more drastic. One never knows, really. 

I appreciate the help. I'll keep checking this out with other routers. 

Do you think using wicd would make any difference vs. network manager?

---

### Post by jmwink on 2009-08-17
After spending the last week or so hopping around between different routers, different networks, and using different laptops, I now believe that the range of this card is fairly narrow. Are there any solutions to increasing the range of the card?

As far as I know, the gazu1 uses the Intel WiFi Link 5100: or at least, that's what I gather from this:

> lspci -v | less

> 
[...]
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
        Subsystem: Intel Corporation Device 1201
        Flags: bus master, fast devsel, latency 0, IRQ 2294
        Memory at f4200000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn
[...]


I've read elsewhere about the use of the compat-wireless package, but was nervous to monkey around with anything before asking more the more knowledgeable whether or not that would help at all. Would installing compat-wireless help? The other question I have is whether or not different network managers would be able to connect further from the access point?

Obviously, this is a minor quibble, but it's certainly annoying to have such a limited range, since it defeats the purpose of wireless networking.

---

### Post by showgun22 on 2009-08-23
Hi I find your situation very interesting.
I also have a tread about poor wifi connectivity with my GU which I believe uses the same modem. I also tested my GU with two other brand of routers yesterday and the result was the same very poor and unstable connection that was very jumpy. I was also gone this summer for 6 week using hotels and most of them could not connect unless I was in the lobby while they were stating they usually did not have that type of problem and the connectivity was also jumpy back then.
I sure hope it is a defect modem
Look at my thread 
[http://ubuntuforums.org/showthread.php?t=1230489](http://ubuntuforums.org/showthread.php?t=1230489) 

Hope we are only having a defect modem.
as you said it 
"It's certainly annoying to have such a limited range, since it defeats the purpose of wireless networking"

I agree 100% ....

---

### Post by jmwink on 2009-08-23
It's been a fairly recent thing with my wireless performance seeming so weak, but it really is pretty pitiful compared to older computers. I have started using a wired connection at home, even though I sit right on top of the router. It's not a tremendously big deal, except the purpose of the laptop is portability between my home office and my workplace, and having to wire in decreases the ease of portability somewhat.

My issue, however, doesn't include the large fluctuations in signal strength. If I can connect at home, it frequently reports 100% signal strength. Speeds, however, are pathetic for a 12Mbps 2nd-gen DSL. 

I found the explanation of the antenna somewhat plausible, but not very satisfactory because it means there's not really a solution.

---

### Post by thomasaaron on 2009-08-24
jmwink,

What was the result of connecting via a live CD?

---

### Post by jmwink on 2009-08-24
I used a LiveCD of crunchbang (9.04.1-64 bit) and didn't find the wireless to be super reliable at home. However, at my workplace, the wireless works without any out-of-the-ordinary hiccups. This leads me to think we're looking at router-specific problems. It's a shame that there aren't more reliable standards from router to router and card to card.

Crunchbang works terrifically by the way. On the livecd, I got a funky error message in the terminal when I attempted to run the Sys76 driver, even though the GUI reported that the installation was successful...I know it's not supported, just thought I'd throw it out there.

---

