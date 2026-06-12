---
title: "Can't connect to secured wirelless networks"
date: 2008-03-31
forum: System76 Support
---

### Post by cward002 on 2008-03-31
I just upgraded my wireless card to an Intel Wireless Link 4965 AGN
card. I can connect to unsecured networks (specifically my wireless AP) when I turn encryption off but when it is on thw wirelless will not connect.I am using the iwl3945 driver. Here is the output from lshw -C network

 *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:97:bf:d3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:04:07.0
       logical name: eth0
       version: 10
       serial: 00:18:f3:ec:07:0a
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.100 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
colin@dopey-dolphin:~$ 

I am not sure what other information is necessary for trouble shooting. Please let me know.

thanks

Colin

---

### Post by cward002 on 2008-03-31
Oops I meant to say I am using the iwl 4965 driver

---

### Post by thomasaaron on 2008-04-01
That's strange.

Let's start by making sure your interfaces file is in order.

To fix your /etc/network/interfaces file, go to a terminal
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

---

### Post by cward002 on 2008-04-01
Thanks for replying Thomasaaron

I have tried all the stuff you suggested.

My interfaces fle is set up as you suggested 

I am only trying to connecting through the Network manager icon

I can connect to unsecured wireless networks but cannot connect to secured wireless networks although I can see them in Network Manager.

I am using the iwl4965 driver which was automatically selected when Hardy detected the new card.

sorry to repeat myself. I just want to make sure that I was being clear about what I had already done

thanks for the help Thomasaaron

---

### Post by thomasaaron on 2008-04-01
OK.

I realize you can see the wireless networks.
But.... Make sure your wireless switch is on.

Which System76 model do you have? The System76 driver will tell you.

---

### Post by cward002 on 2008-04-01
Hi thomasaaron

I am using the GAZP4 (bought in June 2007)

I am running Ubuntu 8.04 which Irealize may be a bit of  an issue as there is no system76 driver released yet. Everything works out of the box without it though. If you can't help me until Hardy is official I completely understand. 

Thanks Thomasaaron

---

### Post by cward002 on 2008-04-01
Here are the results of an iwlist scan:


 Cell 05 - Address: 00:1D:7E:2D:84:03
                    ESSID:"Dopey-Dolphin"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=92/100  Signal level=-38 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000002745baba97

---

### Post by thomasaaron on 2008-04-02
I'm not sure.

Can you give more details about the encrypted network you are trying to connect to? Are you sure you have NM correctly configured with the router? It is very picky in this regard.

---

### Post by cward002 on 2008-04-02
the router is a linksys WRT150N configured to use WPA2. I am on Bell Sympatico which uses PPPOE to connect. The router is set up for this. I have tried to confgure the connection using the PPPOECONF program but to no avail, the program doesn't ecognize the connection. The connection is WLAN0. I have also tried removing the security from the router but this does not work either so maybe this is not a security issue although I can connect to other unsecured wireless networks.

I'm stumped!!!!

Thanks for the help

Colin

---

### Post by thomasaaron on 2008-04-02
Looks like it might be this bug. There is a work-around here too:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/140422](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/140422)

---

### Post by cward002 on 2008-04-02
That certainly sounds like my problem.

I will try the fix posted in the thread and let you know. Don't know why that post didn't come up when I searched!!! Wrong search terms I guess

Thanks again Thomasaaron

Colin

---

### Post by cward002 on 2008-04-02
It appears I don't have the directory or the key mentioned in that fix!!!!!! Is there a way to create it or am I missing something?

---

### Post by thomasaaron on 2008-04-02
Make sure you are typing the paths correctly.
I just checked on Gutsy and they are there.

I'll try to check on Hardy tomorrow to make sure nothing has changed.

---

### Post by cward002 on 2008-04-03
well this just curiouser and curiouser

I had an inspiration last night that maybe if I reset the router and modem that that might fix things. unfortunately it made things worse!!!!

I first reset the router. I could then connect over wireless But then I tired the wired connection and it was down. The wired light on the router was off. so I thought If I reset the modem as well... well then I could connect over the wired connection but not wireless . I am extremely confused and am not even sure that the steps that I took as I outlined them here are in the correct order!!!! I then decided to unplug the router and so I am now connected directly to the modem and it is working. So I am thinking that the router is bad, which is strange because its brand new!!! :lolflag:

thanks again for al your help Thomasaaron

---

### Post by cward002 on 2008-04-03
I decided to do a complete re-install to see if maybe there was a stale configration file somewhere. The behaviour has gone back to " normal" in that it can connect over wired but not wireless.!!!

---

### Post by cward002 on 2008-04-03
Just found this thread which might explain my problems

[http://ubuntuforums.org/showthread.php?p=4643605#post4643605](http://ubuntuforums.org/showthread.php?p=4643605#post4643605)

I did have the partial upgrade issue yesterday. Anyway, when I get home I am going to start from scratch and see what happens!!!

---

### Post by cward002 on 2008-04-04
Well it took a while but things seem to be sorted now!!!! I can finally connnect again to both my wired and wireless.

I am not sure if it  was an update that fixed it or what but I don't care. I am a happy camper!!!!!

and by the way, the GCONF key is back where it should be.


Thanks again for all your help Tom

Colin

---

### Post by thomasaaron on 2008-04-04
Glad you're up and running.
Sometimes we have to just be thankful for the small mysteries.:)

---

### Post by cward002 on 2008-04-17
This problem has returned for me. I can no longer connect to secured wireless networks. It is not quite the same however, as I can still see the gconf-key, which I couldn't before. I am going to try the fixes in ths thread tonight and see how it goes.

---

### Post by cward002 on 2008-04-21
Well it's exactly the same as before. The gconf key is missing again. Given that the release is three days away, I doubt this will be fixed. I tried all the fixes suggested but it didn't help. Although I couldn't try the gconf fix because there is no networking key but maybe an update will fix it again!!!

---

### Post by thomasaaron on 2008-04-21
When this happens, does rebooting your computer solve the problem?

---

### Post by cward002 on 2008-04-21
No. I wish it was that simple!!!!!:lolflag:

---

### Post by cward002 on 2008-04-21
I should add that when I shut down the computer I get a slew of error messsages referring to network manager and my system takes a long time to shut down. I can't remeber what the messages say but if I remember tonight I will write them down and post them

---

### Post by ctsdownloads on 2008-04-21
I might be able to help, have spent the better part of two years avoiding anything to do with NDISWrapper, instead using RaLink based stuff. Moving on...

Some thoughts, the linksys WRT150N is a Pre-N Router :

- Have you checked the router to see if you have a 802.11g only setting? On my box, I use a specific G USB dongle and actually went so far as to make sure my router was using 802.11g ONLY, as I had Super G as an option.

- With my Ralink based cards, this is what I have tremendous success with.

Wireless Channel: Auto
802.11 Mode : G Only
Security Mode: WPA-Personal
WPA settings: WPA-Only (rather than WPA2)

---

### Post by cward002 on 2008-04-21
thanks for trying to help. unfortunately, it didn't seem to help. I still can't connect

---

### Post by ctsdownloads on 2008-04-21
Based on everything I have read, I have to concur with the big mentioned on the front page - [http://ubuntuforums.org/showpost.php?p=4637562&postcount=10](http://ubuntuforums.org/showpost.php?p=4637562&postcount=10)


It especially makes sense with the point you mentioned about gconf losing your WPA info. You said you were unable to use the work-a-round listed on this page?
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/140422](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/140422)


That said, on my old Feisty box (slow to upgrade here), I did not see any sort of path for /system/networking/wireless/networks/ using gconf-editor.

That said, I did find that in a terminal pasting in the following:

sudo gconftool --recursive-unset /system/networking/wireless/networks

appears to do as advertised, meaning it did not kick out any errors.

So were you using gconf-editor or the pasted option above in a terminal instead? I am willing to bet money it is the bug listed on the first page. And despite the path not showing up under gconf-editor, the fact that it gave me zero errors when ran under a terminal leads me to believe this is a fix.

So let's try this again, just for giggles.

Open a terminal window, with your mouse paste in this *exactly*:

> sudo gconftool --recursive-unset /system/networking/wireless/networks

then after that in the same terminal:

> sudo /etc/init.d/networking restart

This will restart the network settings and if the bug is the problem, this ought to do it. If it does not do it, try again on a clean install, the try the above again - I will eat my shoe if I am wrong on this. And my shoes are getting pretty nasty! ;)

---

### Post by cward002 on 2008-04-22
I'll try this when I get home tonight

---

### Post by cward002 on 2008-04-22
I hope you're hungry!!! LOL I followed youe instructions exactly but I still can't connect over wireless. I get no errors when I restart the networking. It just simply won't connect. I even re-installed from scratch again and tried it without updates but still nothing. I am going to try updating and see if that helps.

---

### Post by cward002 on 2008-04-22
I hope you haven't eaten your shoes yet!!!!! I AM A MORON!!!!!!!!!! I had forgotten that I had enabled the MAC filtering on my router. I I thought the MAC Address stayed the same and so the MAC addresses in there would be the only ones allowed to connect but I guess they changed!!!! Anyway, I disabled the MAC Filter and everything is beautiful!!!!!!! I can't mark this thread solved because the option is not under Thread tools anymore. If the mods could do it, I would appreciate it.

---

### Post by ctsdownloads on 2008-04-23
<pulls shoes out of mouth> Good to hear you got it resolved. Totally relating to the MAC address thing, been there myself - it's a real V8 moment. ;)

---

### Post by cward002 on 2008-04-23
glad to know I'm not alone!! I was sure that I had disabled the MAC address filtering but I guess not!!!!! LOL Oh well, live and learn!!!! thanks for everyone's help!!!!!

---

