---
title: "Daru1 WiFi hosed"
date: 2010-04-18
forum: System76 Support
---

### Post by MarkID on 2010-04-18
Friday afternoon everything was working fine.  Didn't use the Daru1 Saturday.  Turned it on Saturday night.  WiFi doesn't work.  Wired connection works.  WiFi works on Starling, so it's not the modem/router.  Everything up to date.  Driver 2.4.4. Ubuntu 9.10.  Please advise.

---

### Post by gamerchick02 on 2010-04-18
Is there a button on your computer that shuts off the wireless?

I know on my Pangolian I can hit the Function key and F11 and shut off or turn on my wireless.

Try looking around for a wireless on/off switch; it may have gotten pressed somehow.

Amy

---

### Post by MarkID on 2010-04-18
Thanks.  I tried that already.  Doesn't help.

> **gamerchick02 said:**
> Is there a button on your computer that shuts off the wireless?

I know on my Pangolian I can hit the Function key and F11 and shut off or turn on my wireless.

Try looking around for a wireless on/off switch; it may have gotten pressed somehow.

Amy

---

### Post by riseringseeker on 2010-04-18
> **MarkID said:**
> Friday afternoon everything was working fine.  Didn't use the Daru1 Saturday.  Turned it on Saturday night.  WiFi doesn't work.  Wired connection works.  WiFi works on Starling, so it's not the modem/router.  Everything up to date.  Driver 2.4.4. Ubuntu 9.10.  Please advise.

What do ifconfig and iwlist in a terminal return?

---

### Post by MarkID on 2010-04-18
> **riseringseeker said:**
> What do ifconfig and iwlist in a terminal return?

 ifconfig
eth1      Link encap:Ethernet  HWaddr 00:18:f3:c6:cd:e5  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fec6:cde5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:232730 errors:0 dropped:0 overruns:0 frame:0
          TX packets:159524 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:309572589 (309.5 MB)  TX bytes:16526249 (16.5 MB)
          Interrupt:20 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation

---

### Post by thomasaaron on 2010-04-19
Can you *see* wifi access points in network manager?

Also, just for the heck of it...

> To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.

...does that fix it.

Incidentally, wireless should work on the DarU1 out of the box with 9.10. If it doesn't work from a live CD, the wifi adapter may well be hosed.

---

### Post by MarkID on 2010-04-19
The network manager doesn't see *any *wireless networks.  I'll try your operation in a bit.  The strange thing is, it worked fine Friday.  Saturday it didn't.  I can't imagine what had changed. 

> **thomasaaron said:**
> Can you *see* wifi access points in network manager?

Also, just for the heck of it...



...does that fix it.

Incidentally, wireless should work on the DarU1 out of the box with 9.10. If it doesn't work from a live CD, the wifi adapter may well be hosed.

---

### Post by MarkID on 2010-04-19
I launched the text file, and everything(except "auto lo
iface lo inet loopback") was already commented ("#") out.  Next step?

> **thomasaaron said:**
> Can you *see* wifi access points in network manager?

Also, just for the heck of it...



...does that fix it.

Incidentally, wireless should work on the DarU1 out of the box with 9.10. If it doesn't work from a live CD, the wifi adapter may well be hosed.

---

### Post by thomasaaron on 2010-04-19
Live 9.10 CD. Make sure your wireless switch is in the right position before booting.

---

