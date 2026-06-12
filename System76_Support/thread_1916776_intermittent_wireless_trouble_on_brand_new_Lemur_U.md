---
title: "intermittent wireless trouble on brand new Lemur Ultra (lemu3)"
date: 2012-01-28
forum: System76 Support
---

### Post by moseymosey on 2012-01-28
I am a recent System76 customer, after having researched various linux-based laptops for quite a while. Many posts on the web talk about how everything "just works" on the Lemur Ultra, so that's what I ordered.

And that's been true, I've found, except for the wireless. Since the moment I opened it I get random wireless dropouts. It makes the laptop unusable for 99% of my intended usage. In my house, I have an ordinary Cisco M20 wireless router. It's been a stable and problem free router, and has worked with various other laptops for the past year without any issues. While my Lemur Ultra can connect to it, and have a functioning connection for a short time, within a few minutes, the connection will "freeze up". I cannot ping any external hosts, and I cannot ping the router (192.168.1.1).  The laptop information is below. I have already updated the System76 drivers on this machine, and rebooted. I've also rebooted the router. The problem persists. Sometimes the connection will suddenly spring back to life after several minutes of staring at the screen. That's nice, but is not a real solution to the problem. My problem is very similar to this:

[https://bugs.launchpad.net/system76/+bug/709796](https://bugs.launchpad.net/system76/+bug/709796)

as well as this:

[https://bugs.launchpad.net/system76/+bug/832489](https://bugs.launchpad.net/system76/+bug/832489)

Driver info: rtl8192ce, 802.11 WiFi (wlan0):
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

db@dbs76:~$ dpkg -l | grep system76
ii  system76-driver                               2.7.1                                   Universal driver for System76 computers.

This is pretty typical to see after only a few minutes of using the connection:

db@dbs76:~$ ping -q google.com
PING google.com (74.125.113.105) 56(84) bytes of data.
^C
--- google.com ping statistics ---
40 packets transmitted, 36 received, 10% packet loss, time 43128ms
rtt min/avg/max/mdev = 27.992/42.028/395.866/59.960 ms

In addition, of course, the connection will just freeze, and nothing works, web browsers will timeout, etc.

Machine details:

Ubuntu 11.10 64 bit	
5 Free GB of Ubuntu One Online Storage and Sync	
14.1" HD LED Display with Super Glossy Surface ( 1366 x 768 )	
Intel HD Graphics 3000	
2nd Generation Intel Core i5-2430M Processor ( 3MB L3 Cache, 2.40GHz )	
6 GB DDR3 SDRAM at 1333MHz - 4GB + 2GB
500 GB 7200 RPM SATA II	
8X DVD±R/RW/4X +DL Super-Multi Drive	
Internal 802.11 B+G+N Wireless LAN + Bluetooth Combo Module

I can make lsmod and dmesg available if anyone is interested.

Tips and suggestions very much appreciated, since without a fix, this brand new purchase is a big waste.

Thanks.

db

---

### Post by jschall1 on 2012-01-28
Get an Intel advanced-n 6230 to replace the garbage realtek chip they sell by default. I don't know why they sell it, they really shouldn't. I had problems with it and you're the second other person I've seen that has problems.

---

### Post by varunendra on 2012-01-29
Hi moseymosey, welcome to the forums!

Have you tried installing the driver from [realtek's]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true") site? Compilation and installation instructions are in the 'readme' file in the downloaded .tar.gz package.

If that does not work, try using wicd or wpa_supplicant (you can install wpagui from synaptic/software-center, if you need a GUI to configure it), instead of Network-Manager - as the post #3 in the 2nd bug-report page you linked suggests.

If both these attempts fail, then yes, we'll need more details. To start with, the outputs of:
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
iwconfig
iwlist scan
dmesg | grep -iE 'wlan | rtl8192'
```

---

### Post by repsah on 2012-01-30
Hello, I just purchased a bonp5 (Bonobo professional) and I have the same exact problem, the wireless connection just freezes after a while.

I tried switching to WICD but it did not solve the problem, so I went back to network-manager.
It doesn't look to me the problem was solved on the previous owner, any idea about what I can do?

Moreover, using a wired connection instead the system freezes completely if the download rate exceeds 400Kb/s, a kernel panic.

Andrea

---

### Post by smarmytime on 2012-01-30
moseymosey, I have a similar problem when I use my FIOS router, and I have to reset my network connection every time it happens - annoying. However, I don't have any problem at all when I use the other WAP I have in my house. Have you tried it with another router/WAP? At a friends house, or local business maybe, if you don't have another one lying around.

---

### Post by moseymosey on 2012-01-31
> **varunendra said:**
> Hi moseymosey, welcome to the forums!

If both these attempts fail, then yes, we'll need more details. To start with, the outputs of:
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
iwconfig
iwlist scan
dmesg | grep -iE 'wlan | rtl8192'
```


Ok, I'm continuing to struggle with this problem. I have both NetworkManager and wpa-supplicant installed and running. It's still the default install which was present when I first opened the laptop. AFAICT, these programs are running.

I downloaded and compiled/installed the latest drivers from the realtek web site. Then I rebooted.

Unfortunately, the problem persists. I also tried to use the laptop outside of my house, and that fails completely. It's so unusable, that it simply must be a hardware problem. The routers I've tried this with are varied, and some of them are "general purpose" routers (for example, at Starbucks) so I doubt the problem lies in my home router. This laptop simply "does not work" on wireless. Every other laptop I've seen works just fine in similar circumstances. People standing around with iPhones pick up the signal and carry on with their lives. Random business people with lenovo thinkpads are typing away. But my Lemur Ultra simply does not work.

Here is the requested information, which I grabbed when I was able to connect to my home router:

[http://pastebin.com/raw.php?i=kS8Mpapn](http://pastebin.com/raw.php?i=kS8Mpapn)

And here is the very same information, except this time I attempted (and failed) to connect to my phone's hotspot (which I've done countless times with other laptops when on the road):

[http://pastebin.com/raw.php?i=fNVJZy23](http://pastebin.com/raw.php?i=fNVJZy23)

In addition, there is some frequent dmesg output while the laptop struggles to make a connection:

[ 2693.307210] wlan0: deauthenticating from 68:7f:74:c8:f7:05 by local choice (reason=3)
[ 2693.327183] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2693.327189] cfg80211: Restoring regulatory settings
[ 2693.327749] cfg80211: Calling CRDA to update world regulatory domain
[ 2693.330438] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 2693.330442] cfg80211: World regulatory domain updated:
[ 2693.330444] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2693.330446] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2693.330449] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2693.330451] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2693.330453] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2693.330455] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2694.205802] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 1/3)
[ 2694.401728] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 2/3)
[ 2694.601465] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 3/3)
[ 2694.801230] wlan0: direct probe to f8:7b:7a:92:9f:e2 timed out
[ 2701.349165] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 1/3)
[ 2701.548512] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 2/3)
[ 2701.748207] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 3/3)
[ 2701.947952] wlan0: direct probe to f8:7b:7a:92:9f:e2 timed out
[ 2708.495983] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 1/3)
[ 2708.695222] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 2/3)
[ 2708.894988] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 3/3)
[ 2709.094710] wlan0: direct probe to f8:7b:7a:92:9f:e2 timed out
[ 2715.643374] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 1/3)
[ 2715.841987] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 2/3)
[ 2716.041735] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 3/3)
[ 2716.241475] wlan0: direct probe to f8:7b:7a:92:9f:e2 timed out
[ 2722.809726] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 1/3)
[ 2723.008724] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 2/3)
[ 2723.208450] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 3/3)
[ 2723.408202] wlan0: direct probe to f8:7b:7a:92:9f:e2 timed out
[ 2729.952286] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 1/3)
[ 2730.151484] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 2/3)
[ 2730.351205] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 3/3)
[ 2730.550969] wlan0: direct probe to f8:7b:7a:92:9f:e2 timed out
[ 2737.103239] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 1/3)
[ 2737.302221] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 2/3)
[ 2737.501967] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 3/3)
[ 2737.701694] wlan0: direct probe to f8:7b:7a:92:9f:e2 timed out
[ 2742.855494] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 1/3)
[ 2743.054766] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 2/3)
[ 2743.254531] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 3/3)
[ 2743.454274] wlan0: direct probe to f8:7b:7a:92:9f:e2 timed out
[ 2749.998231] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 1/3)
[ 2750.197541] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 2/3)
[ 2750.397287] wlan0: direct probe to f8:7b:7a:92:9f:e2 (try 3/3)
[ 2750.597029] wlan0: direct probe to f8:7b:7a:92:9f:e2 timed out

This will continue forever as it tries (and fails) to connect.

I've also emailed support at system76 last Saturday, but have yet to receive any response, or even an acknowledgement.

Any further advice or information would be appreciated. I'm sorry to see other people having the identical problem.

db

---

### Post by varunendra on 2012-02-01
Sorry, I looked as hard as I could, but couldn't find any reasonable solution to this problem.

It looks like several bug reports (e.g., [this]("https://bugs.launchpad.net/ubuntu/+bug/874229") and [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/902557")) related to this driver-kernel combination are in progress, but no one has yet come up with a possible workaround. The only reliable solution I could find so far seems to fall back to an older kernel (3.0.0.12 or earlier).

Accordingly, the only thing that seems most promising after a lot of googling and research is to switch back to 10.04.3 LTS (or any of 10.10 or 11.04 that uses a kernel newer than 2.6.35.xx and upto 3.0.0.12). Although even there you may have to compile and install the proprietary driver from realtek (the one you've already downloaded), but at least it 'should' work flawlessly afterwards, as has been reported by many.

If you wish to try that with a live cd, do not restart after compiling the driver as the readme file suggests (because changes on a live cd will be lost after restart). Instead, just do **sudo modprobe -rfv rtl8192ce** then again **sudo modprobe -v rtl8192ce**. This will be equivalen to a restart for the driver. If it works, just install 10.04 (or whatever that works) and wait for 12.04 LTS hoping it would get permanently fixed in it.


Or,.... if you are ready to try anything and everything before giving up on 11.10 (I hate to say that, but...) you may try these as 'completely blind shots':

[After trying each set of the following commands, DO NOT RESTART, just wait till wireless becomes active again (should be less than a min.), then retry to connect. If it fails again, try the next set:]
```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce swenc=1
```

or
```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce ips=0
```

or, using both parameters:
```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce swenc=1 ips=0
```

As is apparent, it maybe a totally crazy thing to try, giving no positive results at all. But it won't break anything either (and will be reset after a restart) - be assured of that!

Another thing you may try is to disable IPv6, but it is such a far cry that I don't want to even bother with the instructions on 'howto'! :x

---

### Post by moseymosey on 2012-02-01
> **varunendra said:**
> Sorry, I looked as hard as I could, but couldn't find any reasonable solution to this problem.


Ok. Your searching turned up the same sort of links that I found. I appreciate your assistance with this, as do many others, I'm sure.

I am not completely wedded to the latest version of ubuntu, so I might just try different installations of Debian (perhaps just Debian stable?) to see if that helps the situation. AFAIK, I can simply restore back to the default Ubuntu install that came with this laptop if need be, is that correct? 

Also, if I go with Debian stable, would I still be able to take advantage of the System76 driver package?

---

### Post by varunendra on 2012-02-01
> **moseymosey said:**
> AFAIK, I can simply restore back to the default Ubuntu install that came with this laptop if need be, is that correct? 

Also, if I go with Debian stable, would I still be able to take advantage of the System76 driver package?
I'm not sure about either of these, as I have absolutely no experience or any detailed information about system76.

One thing I can definitively say is a completely secure and probably the best backup option is to have your hard disk or system partition(s) image on an external media - like an external hard disk. Clonezilla and remastersys are two utilities I frequently suggest for doing this. Obviously, having an external backup is always better than relying on an internal one - which may get messed up should anything go wrong with the drive.

AFAIK, the .deb packages for ubuntu are slightly different from the packages meant for Debian OS, bacause of the slight difference in directory and system files structure between them. So I doubt any Ubuntu package may be successfully installed on Debian.

Your best bet is to take an image of your current installation on an external drive, then try these things afterwards.

The best thing about these OSes is that we don't have to get wedded to them,.... we can break-up anytime we wish (..and reunite again.. whenever we wish!) ;)

---

### Post by moseymosey on 2012-02-02
> **varunendra said:**
> 
The best thing about these OSes is that we don't have to get wedded to them,.... we can break-up anytime we wish (..and reunite again.. whenever we wish!) ;)

Agreed. The System76 laptops can be restored to factory:

[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

So I'm not worried about messing around with different OS installations. I don't have anything else on this laptop. Since I've had problems from the moment I opened it, I haven't had a chance to accrue any data.

Thanks again for your help, and I'll report back if I have any success solving this otherwise.

---

### Post by smarmytime on 2012-02-02
moseymosey, there is a thread somewhere in here, about using the System76 driver with other distros. From what I can remember, it's just a .conf file that has to be edited; of course, it was more successful with some distros than with others. I don't remember the name of the thread, but I can't imagine it would be too hard to find.

---

### Post by smarmytime on 2012-02-02
Ok, I'm not sure if this is THE thread on how to use it with other distros, but it's got SOME info. If you do go with debian, keep us updated on how it goes - I'd love to hear about it!

[http://ubuntuforums.org/showthread.php?t=802181&highlight=system76+driver+distro](http://ubuntuforums.org/showthread.php?t=802181&highlight=system76+driver+distro)

---

### Post by ebierly on 2012-02-17
i have this exact problem with a brand new lemur ultra just hours old after i did the recommended software updates

Ubuntu 11.10 64 bit	
5 Free GB of Ubuntu One Online Storage and Sync	
14.1" HD LED Display with Super Glossy Surface ( 1366 x 768 )	
Intel HD Graphics 3000	
2nd Generation Intel Core i5-2430M Processor ( 3MB L3 Cache, 2.40GHz )	
8 GB Dual Channel DDR3 SDRAM at 1333MHz - 2 X 4GB	 +$69.00
500 GB 7200 RPM SATA II	
8X DVD±R/RW/4X +DL Super-Multi Drive	
Internal 802.11 B+G+N Wireless LAN + Bluetooth Combo Module

is the only solution rolling back? i didnt see moseymosey report back that that actually did the trick

---

### Post by ccrs8 on 2012-02-19
I'm also experiencing this exact same problem.  Brand new Lemur (ordered late December, delivered in January.  Wireless is unusable.  Right after I got the laptop, I brought it with me for a week long business trip and could not keep a wireless connection at the hotel for more than 5 minutes at a time.  I figured it was a problem with the hotel's wifi, so I didn't look in to it.  But then I noticed the problem at the airport on the way home after that week.  And since then the problem has happened at three other airports, a Starbucks, and several people's houses (including my own).  So it's definitely the computer and not the networks.

The only "solution" is to disconnect and reconnect every time in order to get a connection again.  Network manager says I am connected, but lag time on the internet increases and increases until eventually pages time out.  Disconnecting and reconnecting is the only way to get a decent connection back, and then it goes away 5 minutes later.

Does anyone have a fix for this?  It seems that manually instaling the drivers from source didn't work.  Did rolling back or installing a different distribution?  Anyway, until this is fixed this laptop is usable only plugged in to ethernet, and that sort of defeats the purpose.  Has anyone heard from System76 about this?

---

### Post by Redcard on 2012-02-19
Yep..

This is the problem I have with the GazP laptop of mine.  

System76's answer to me was that "it's the kernel, it'll be okay, it's not our fault , just wait a few days and it'll be fixed."

So, I'd recommend just using wired for a while, because it doesn't sound like this is getting fixed any time soon (It's gone on for about three months for me)

---

### Post by ccrs8 on 2012-02-19
> **Redcard said:**
> Yep..

This is the problem I have with the GazP laptop of mine.  

System76's answer to me was that "it's the kernel, it'll be okay, it's not our fault , just wait a few days and it'll be fixed."

So, I'd recommend just using wired for a while, because it doesn't sound like this is getting fixed any time soon (It's gone on for about three months for me)

Ugh - wonderful.  Thanks for the info.  Unfortunately, using wired isn't an option at my of the hotels I stay in, and at home I have a Wild Dog System76 desktop for all of my computing needs for when I'm not on the road.  So until I can get this wireless issue figured out, this new Lemur is literally useless to me.

> **jschall1 said:**
> Get an Intel advanced-n 6230 to replace the garbage realtek chip they sell by default. I don't know why they sell it, they really shouldn't. I had problems with it and you're the second other person I've seen that has problems.

jschall1 - I'm interested in this idea.  I had a Dell Mini 9 that had an iffy Broadcom wifi card, and replacing it with an Intel card made all the difference.  Do you know if the wifi card you recommended can be installed in the Lemur?  I'm not intimidated by digging around in the computer - I just wouldn't want to open it up if there is no chance of it working.  Also, do you know if there are good Linux drivers for the card?  I did some Googling and came across some posts where folks have had some issues getting the card to work easily in Linux, but they are slightly outdated posts (about a year old - mostly talking about Ubuntu 10.10).

---

### Post by isantop on 2012-02-20
> **ccrs8 said:**
> Ugh - wonderful.  Thanks for the info.  Unfortunately, using wired isn't an option at my of the hotels I stay in, and at home I have a Wild Dog System76 desktop for all of my computing needs for when I'm not on the road.  So until I can get this wireless issue figured out, this new Lemur is literally useless to me.



jschall1 - I'm interested in this idea.  I had a Dell Mini 9 that had an iffy Broadcom wifi card, and replacing it with an Intel card made all the difference.  Do you know if the wifi card you recommended can be installed in the Lemur?  I'm not intimidated by digging around in the computer - I just wouldn't want to open it up if there is no chance of it working.  Also, do you know if there are good Linux drivers for the card?  I did some Googling and came across some posts where folks have had some issues getting the card to work easily in Linux, but they are slightly outdated posts (about a year old - mostly talking about Ubuntu 10.10).

The 6230 is one of the upgrade options we offer, and it works quite well in the Lemur. We can get you a 6230 at upgrade price too ($28), so if you'd like to go that route, please send us an email at support...at...system76...dot...com. 

The default card we sell (the Realtek 8188CE) tests fine in our office, and the majority of realtek cards we sell work fine. We offer the Intel options as an alternative for those who are having problems. 

We don't feel it's right for most users to pay for something they don't need. For those who do need it, that's why we offer the Intel card.

---

### Post by ccrs8 on 2012-02-20
> **isantop said:**
> The 6230 is one of the upgrade options we offer, and it works quite well in the Lemur. We can get you a 6230 at upgrade price too ($28), so if you'd like to go that route, please send us an email at support...at...system76...dot...com. 

The default card we sell (the Realtek 8188CE) tests fine in our office, and the majority of realtek cards we sell work fine. We offer the Intel options as an alternative for those who are having problems. 

We don't feel it's right for most users to pay for something they don't need. For those who do need it, that's why we offer the Intel card.

That sounds like as good a plan as anything.  I'll send an email to your support address to buy it.

Do you know if the installation is easy enough?  Is there a hardware guide somewhere for the Lemur?  Also, will the card be recognized and the drivers installed fairly easily, or will I have to manually build the drivers?

---

### Post by isantop on 2012-02-20
> **ccrs8 said:**
> That sounds like as good a plan as anything.  I'll send an email to your support address to buy it.

Do you know if the installation is easy enough?  Is there a hardware guide somewhere for the Lemur?  Also, will the card be recognized and the drivers installed fairly easily, or will I have to manually build the drivers?

The drivers are already present in Ubuntu, so all you'll need to do is swap the card. Ubuntu will take care of the rest. :) 

It is pretty simple to replace the card. The main panel on the back comes off, then the card is pretty much right there. We can talk you through it over the phone too, if you prefer.

---

### Post by ccrs8 on 2012-02-20
> **isantop said:**
> The 6230 is one of the upgrade options we offer, and it works quite well in the Lemur. We can get you a 6230 at upgrade price too ($28), so if you'd like to go that route, please send us an email at support...at...system76...dot...com.
I emailed and then later called customer service (sorry for being impatient, but I'm going on another trip in two weeks and would like to get something worked out by then), but they said that unless I sent the laptop in to get the card replaced, that it would be better if I purchased the card locally.  No big deal - Amazon has it for around the same price and I think I have an Amazon gift card around here somewhere.

> **isantop said:**
> The drivers are already present in Ubuntu, so all you'll need to do is swap the card. Ubuntu will take care of the rest. :) 

It is pretty simple to replace the card. The main panel on the back comes off, then the card is pretty much right there. We can talk you through it over the phone too, if you prefer.

Thanks - that is good to know.  Is the existing Realtec card an integrated card or a module that I will swap out with this Intel one?

PS: Sorry for semi-hijacking this thread.  Nothing I've contributed is helping fix the issue with the existing card, but it may better document getting a working card.

---

### Post by ccrs8 on 2012-02-20
> **ccrs8 said:**
> Is the existing Realtec card an integrated card or a module that I will swap out with this Intel one?

Nevermind - I took off the bottom panel and answered my own question.  It's a separate module to be swapped out.  Should be quite easy to replace.  I ordered the Intel 6230 from Amazon (as predicted, about the same price, and I did have a gift card), so hopefully next week I'll have this straightened out.

Thanks for the help.

---

### Post by ebierly on 2012-02-21
> **varunendra said:**
> Hi moseymosey, welcome to the forums!

Have you tried installing the driver from [realtek's]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true") site? Compilation and installation instructions are in the 'readme' file in the downloaded .tar.gz package.

If that does not work, try using wicd or wpa_supplicant (you can install wpagui from synaptic/software-center, if you need a GUI to configure it), instead of Network-Manager - as the post #3 in the 2nd bug-report page you linked suggests.

If both these attempts fail, then yes, we'll need more details. To start with, the outputs of:
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
iwconfig
iwlist scan
dmesg | grep -iE 'wlan | rtl8192'
```
[http://pastebin.com/wNxqpvbu](http://pastebin.com/wNxqpvbu)

---

### Post by ccrs8 on 2012-02-23
> **ccrs8 said:**
> Nevermind - I took off the bottom panel and answered my own question.  It's a separate module to be swapped out.  Should be quite easy to replace.  I ordered the Intel 6230 from Amazon (as predicted, about the same price, and I did have a gift card), so hopefully next week I'll have this straightened out.

Thanks for the help.

I received the card today.  It installed without a hitch (both physically and software driver in Xubuntu 11.10).  I can already tell that the connection on my home network is stronger, but I'm going to take it to work with me tomorrow and try it out on my office wifi and at a few local coffee houses around my office, as those are the types of places that really gave me problems with the old card.

---

### Post by ebierly on 2012-02-28
> **jschall1 said:**
> Get an Intel advanced-n 6230 to replace the garbage realtek chip they sell by default. I don't know why they sell it, they really shouldn't. I had problems with it and you're the second other person I've seen that has problems.

this appears to have solved my problem. thank you jschall1!

---

### Post by ubuntu27 on 2012-03-01
The great news is that apparently System76 has decided to ship with Intel Centrino Advanced-N 6230 by default in Lemur Ultra 3. :popcorn:

In "configure and buy" page for Lemur, they only present Intel Centrino Advanced-N 6230. The option for "Integrated Wireless card" is gone now.

[http://www.system76.com/index.php/laptops/model/lemur](http://www.system76.com/index.php/laptops/model/lemur)

---

