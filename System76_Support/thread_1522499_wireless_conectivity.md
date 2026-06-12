---
title: "wireless conectivity"
date: 2010-07-02
forum: System76 Support
---

### Post by Eyore15 on 2010-07-02
1.  After booting, the network-manager shows that I'm connected to my in-house wireless network with an excellent signal strength.  I cannot connect to the internet however.

2.  When I use a wired connection, I'm able to successfully connect to the internet.

3.  Anyone want to hazard a guess as to why I cannot connect via wireless,and even better, suggest a way to fix it?

4.  I'm running Ubuntu 10.04 on a starling.  My system 76 driver is 2.5.1

tnx

mcmn

---

### Post by Tart on 2010-07-06
I'm also having problems with wireless. So I just want to bump your post up, but I noticed that latest system76 driver on my starling is 2.6.something, maybe if you install latest driver it will help you.

[http://ubuntuforums.org/showthread.php?t=1521477]("http://ubuntuforums.org/showthread.php?t=1521477")

---

### Post by thomasaaron on 2010-07-08
Please run the following command from a terminal and let me know the output...

lsmod | grep 8187

Also, can you please test on a different wireless access point?
You also may want to unplug your AP and let it sit for a minute and then plug it back in. Sometimes this fixes jams, even if other devices are working with the AP.

---

### Post by Tart on 2010-07-08
This the output of the command 
```
r8187b                169943  2
```

I updated firmware on my router, performance somewhat improved.

---

### Post by tmette on 2010-07-08
I know this sounds pretty ...well stupid, but have you guys tried rebooting your routers?  I had to do this once after moving my family router.  I would connect to the network, but not get any Internet.  After rebooting our router one more time it's been fine ever since.  Also, try changing the channel your router is  broadcasting on.  I changed ours from 6 to 11 and it helped out the signal too.

---

### Post by claytronic on 2010-07-08
I'm having the same problem with my Lemur. Running 10.4 and latest System76 driver. The other Dell laptops in the house work fine with our Linksys WRVS4400N.

---

### Post by claytronic on 2010-07-08
Update: Just gracefully rebooted the router for kicks and now my connection is working? Weird. Nothing else in the house was affected. :confused:

---

### Post by claytronic on 2010-07-08
Second update: The laptop lost it's connection about 5 minutes after my last post...

Since then I've been playing with the router's different wireless modes. The problem appears to be related to mode N. If I set the router to only G or B+G, my Lemur is able to stay connected.

---

### Post by |Porsche on 2010-07-10
After you connect to your wireless network. Do a ifconfig -a and post results.

---

### Post by Tart on 2010-08-03
> **thomasaaron said:**
> 
Also, can you please test on a different wireless access point?
You also may want to unplug your AP and let it sit for a minute and then plug it back in. Sometimes this fixes jams, even if other devices are working with the AP.

I took my Starling to conference two weeks ago, first major field trip. It worked great in the institute, but absolutely refused to work in a hotel. Signal strength was good, there were multiple access points all around hotel, was able to connect only once, barely in the lobby. 

Can anyone recommend USB adapter that works without problems with ubuntu/starling?

---

### Post by jml on 2010-08-05
The one I used successfully with my Starling is the "Belkin Wireless G USB Network Adapter."  Model F5D7050  I just plugged it in, turned on my Starling and Ubuntu recognized it out of the box.  I was able to use Network Manager to configure it to connect to my WPA encrypted wireless network.

The only thing to remember is to disable/blacklist the internal wireless card.  Until you do that, you will get two separate prompts to connect to a wireless network.  One from the internal and one from the USB card.

---

### Post by isantop on 2010-08-05
That looks like a good card. In fact, I believe we have one or two here for testing.

---

### Post by Tart on 2010-08-05
> **jml said:**
> The one I used successfully with my Starling is the "Belkin Wireless G USB Network Adapter."  Model F5D7050  I just plugged it in, turned on my Starling and Ubuntu recognized it out of the box.  I was able to use Network Manager to configure it to connect to my WPA encrypted wireless network.

The only thing to remember is to disable/blacklist the internal wireless card.  Until you do that, you will get two separate prompts to connect to a wireless network.  One from the internal and one from the USB card.


Thank you! I'll order one. Any reason why newer one with 802.11N, will not work? How do I blacklist internal card?

---

### Post by jml on 2010-08-06
Since the 802.11n protocol has not yet been formally ratified, there may be minor variations from manufacturer to manufacturer.  Also, it is possible that Belkin has used a different chip set in the new card.  I have read that "n" support in various Linux distributions can be spotty.  It would be ideal to actually test the card before buying.  Or at least buy the card from a vendor that has a reasonable return policy.

As for your other question, I found the by searching this forum for the string "blacklist wifi driver" 

# disable builtin wifi in favor of the belkin usb nic
blacklist rtl8187

I never actually had to use this, because the most recent driver updates and Ubuntu 10.04 gives me wireless performance that was good enough for my needs.

Joe

---

