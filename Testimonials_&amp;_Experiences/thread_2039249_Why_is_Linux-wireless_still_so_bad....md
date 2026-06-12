---
title: "Why is Linux-wireless still so bad?..."
date: 2012-08-08
forum: Testimonials &amp; Experiences
---

### Post by omelette on 2012-08-08
Am I the only one that thinks this, or do myriads of others experience the same performance but suffer in silence? And this is a serious question!

After 6 years of being 100% Linux-based, wireless has proven to be its only real Achilles-heel.  Currently I have 2 computers that run 24/7, one a Zoran mini-pc with Ubuntu 10.04, the other a Dell M1210 laptop with 3 OS's installed, Ubuntu/Fuduntu/WinXP, the latter having just been added in the hope of gaining some insights into my wireless issues. I'm also working with 3 different wireless cards which are interchangeable between the 2 PC's - Atheros AR5212, Atheros AR928x & Intel IWL3945.

On the laptop the performance of all 3 NIC's has been bad for years but lately it has become abysmal.  The Intel IWL3945 will just stop working, with NetworkManager showing a enter-network-password pop-up, the only way to resolve it being to restart Linux - removing & initialising with 'modprobe' doesn't work!  The Atheros cards are a little more forgiving - they both lose the network-feed constantly (at least 5-6 times a day) but clicking on NetworkManagers signal-strength icon with restore the feed most of the time.

**The kicker to all this is that all three NIC's seem to work perfectly on the Zoran mini-pc - running 24/7, I have never yet witnessed it lose the network-feed!**

Until recently I was convinced that it must therefore be a fault with the Dell laptop - until I installed WinXP and found that the wireless seems to work flawlessly!  Then I again suspected the kernel, so thinking the current but older-sounding 2.6.32-41 kernel in Ubuntu 10.04 must be bug-free, I installed Ubuntu 10.04 on the laptop, only to discover that it loses the feed/network as well...

My final act was to install **Ndiswrapper** with Ubuntu 10.04 and the AR928x NIC, and for the past 2 days (touch wood!) the wireless appears rock-solid! The only downside being that it's limited to 54M/s, less than half the speed I used to get with the Atheros bgn cards.

So my question(s) - are there others suffering similarly, and why is Ndiswrapper limited to 54M?  I was very surprised to find that it's still being actively developed, the last update being just a few months ago!

---

### Post by omelette on 2012-08-11
For the record, with Ubuntu 10.04 installed & running 24/7 on the Dell M1210 laptop and using Ndiswrapper with Atheros (AR928x) M$-drivers, I have just experienced the same problem - namely, it just lost the network where only a reboot was the solution. :(

Whereas the Zotac pc, also running 24/7 with Ubuntu 10.04 but native-Linux Atheros (AR5212) drivers, continues to perform flawlessly!

So I'm convinced (again) that the problem is with the Dell motherboard and not with the Linux drivers - which in a bizarre sort of way is a relief! :D Whether it's some hardware incompatibility or a genuine hardware fault is another question however...

---

### Post by kurt18947 on 2012-08-11
> **omelette said:**
> For the record, with Ubuntu 10.04 installed & running 24/7 on the Dell M1210 laptop and using Ndiswrapper with Atheros (AR928x) M$-drivers, I have just experienced the same problem - namely, it just lost the network where only a reboot was the solution. :(

Whereas the Zotac pc, also running 24/7 with Ubuntu 10.04 but native-Linux Atheros (AR5212) drivers, continues to perform flawlessly!

So I'm convinced (again) that the problem is with the Dell motherboard and not with the Linux drivers - which in a bizarre sort of way is a relief! :D Whether it's some hardware incompatibility or a genuine hardware fault is another question however...

Without a "tie-breaker" (3rd machine) it's hard to say for certain but yes, I'd suspect some hardware/motherboard chip set issue.

---

### Post by TheFu on 2012-08-11
> **omelette said:**
> Whereas the Zotac pc, also running 24/7 with Ubuntu 10.04 but native-Linux Atheros (AR5212) drivers, continues to perform flawlessly!

So what you've learned is that native Linux drivers are good, but trying to run Windows drivers through an emulation layer is bad.  I don't think anyone should be surprised by that.

There isn't any immediate solution. The only long term solutions are:
* **only purchase hardware with** known, good, **linux support**
* **be vocal to hardware manufacturers that you demand they support Linux **with support, drivers and to the same level of other OSes. If they don't, take your business elsewhere.

This applies to all computers, cards and peripherals.  In my many years of Linux use, I've discovered that the better supported hardware is on Linux, the better made that hardware tends to be AND it tends to work great on all OSes.

Complaining to us isn't too productive, though we all enjoy a bitch session.  Complaining to the vendor about their lack of Linux support helps everyone.

---

### Post by omelette on 2012-08-11
> **TheFu said:**
> So what you've learned is that native Linux drivers are good, but trying to run Windows drivers through an emulation layer is bad.  I don't think anyone should be surprised by that.

...

As I mentioned in the opening post, the 100% powered Linux Zotac mini-pc has never given me any grief wireless-wise in over 3 years of 24/7 running.  Whereas the Dell laptop has been a nightmare - I can't exaggerate how bad it is, and has been for years! But it works perfectly otherwise, so either there is some incompatibility between its motherboard and the Linux drivers, or it has a technical fault somewhere.

The Ndiswrapper-wireless seemed to run flawlessly initially, but seeing as it is also permanently disconnecting, common-sense suggests the fault lies elsewhere. The one thing that sucks about Ndiswrapper is it can only provide speeds up to 54M, whereas the very same driver running on WinXP gives you 270Mb/s. 

So I can at least say that Linux wireless doesn't seem to have been responsible for the grief I'm suffering. :)

---

### Post by TheFu on 2012-08-12
> **omelette said:**
> The Ndiswrapper-wireless seemed to run flawlessly initially, but seeing as it is also permanently disconnecting, common-sense suggests the fault lies elsewhere. The one thing that sucks about Ndiswrapper is it can only provide speeds up to 54M, whereas the very same driver running on WinXP gives you 270Mb/s.

So using non-native drivers results in less-than ideal outcomes.  Ndiswrapper is obviously a wrapper, right? 

The Ndiswrapper team has done phenomenal things, but if the wifi chip vendors produced native Linux drivers, we'd probably all be happier.

That was my only point.  I've never needed to use Ndiswrapper myself. Careful selection of Linux compatible hardware prevents that. Taking my business to companies that support Linux isn't always simple or even possible, but I do it whenever I can.

---

### Post by nothingspecial on 2012-08-12
*Thread moved to **Ubuntu Testimonials & Experiences**.*

---

### Post by madjr on 2012-08-12
> **TheFu said:**
> So using non-native drivers results in less-than ideal outcomes.  Ndiswrapper is obviously a wrapper, right? 

The Ndiswrapper team has done phenomenal things, but if the wifi chip vendors produced native Linux drivers, we'd probably all be happier.

That was my only point.  I've never needed to use Ndiswrapper myself. Careful selection of Linux compatible hardware prevents that. Taking my business to companies that support Linux isn't always simple or even possible, but I do it whenever I can.

I can agree to that.

now I either buy from linux vendors (like system76, zareason, etc.) or at least google the "model+ubuntu" to make sure it has no issues with linux/ubuntu.

I had almost zero issues since and good strong wifi. :)

---

### Post by asdk on 2012-08-13
Wifi for me isn't so greats but with wires it works fine, which is all I really need, of course. However, like someone mentioned in this thread, if the card doesn't have good Linux support, don't buy it.

---

### Post by kurt18947 on 2012-08-13
> **madjr said:**
> I can agree to that.

now I either buy from linux vendors (like system76, zareason, etc.) or at least google the "model+ubuntu" to make sure it has no issues with linux/ubuntu.

I had almost zero issues since and good strong wifi. :)

Absolutely.  Some research can save hours or days of anguish.  The other thing to remember is that not all chips from a particular manufacturer are the same.  For instance I've had very good luck with  RealTek for the most part but there are some realtek chipsets that are problematic.  I think it's a good sign if vendors have good Linux support on their own sites, and this is true of any hardware.

---

### Post by mastablasta on 2012-08-13
vendors like system 76 do provide compatible hardware but they still lack performance mashcines. I am thinking latest laptops with switchable graphics.
 
then again not many games work on linux anyway... and i guess people would use desktops for other graphics intense programmes.

---

