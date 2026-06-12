---
title: "Built-in apps get an &quot;A&quot;, wireless support an &quot;F&quot;"
date: 2008-01-17
forum: Testimonials &amp; Experiences
---

### Post by newbie2 on 2008-01-17
Dennis O'Reilly  :
> I was disappointed that I wouldn't be able to use Ubuntu the same way I use Windows, at least not until I figure out why I couldn't get Ubuntu to establish a wireless link. I haven't given up hope of replacing Windows with Linux, but neither am I willing to spend hours searching for a solution to a problem I can avoid simply by loading Windows.
[http://www.cnet.com/8301-13880_1-9839735-68.html](http://www.cnet.com/8301-13880_1-9839735-68.html)

---

### Post by Paul820 on 2008-01-17
Wireless support for ubuntu varies with everyone, for me it works out of the box, for others it's a nightmare. Ubuntu support for wireless is better than windows as ubuntu does not need drivers for it. It is getting better and it would be perfect if the manufacturers would start making drivers for the hardware that we all have. Unfortunately, that is going to take time so some have to carry on struggling or try and buy hardware that is known to work with ubuntu.

---

### Post by newbie2 on 2008-01-17
if you read the comments on this article ,Shannon VanWagner got it right me thinks :-\" :
> To All:
If you support Linux, please tell Linksys to make a Linux driver for this device (or ask them to let the Linux Kernel team make a driver for free for the device, see: [http://kerneltrap.org/node/7636](http://kerneltrap.org/node/7636) ).
Here's the "contact us" link for Linksys: [http://tinyurl.com/3ckxn9](http://tinyurl.com/3ckxn9)
Here's the email address for "Open Source" inquiries: [email]linksys-opensource@linksys.com[/email]
"A teaspoon of water or an ocean", it's up to us Linux users to make the difference!
Shannon VanWagner

---

### Post by Gary Stout on 2008-01-18
I had a Linksys wusb54g v4 that gave me fits. Some times it would work, but 80% of the time it did not. After some googling, I found that wireless cards with the Atheros chip set are almost always capatible out of the box. So then I had to find a card that used this chip set. The article gave the catalog number for a model that  Radio Shack had, but after calling the local store, that model was no longer being sold. After some more research, I found that the Netgear units, whose model number ends with a "T"  that Radio Shack sells, do have the Atheros chip set. I ended up getting a Netgear WG111T USB style and it works fine. 

Also, there is NDISWRAPPER that will allow you to use the INF file from your original wireless card installation CD. 

HTH,
Gary

---

### Post by SonicSteve on 2008-01-18
I had to buy a Dlink G650 pc card for my notebook. I had a trendnet usb that wouldn't work to save my life. The down side of the Dlink is that it uses restricted drivers. It works perfectly but if it goes on the fritz the restricted drivers will be cursed.

---

### Post by 3rdalbum on 2008-01-19
The guy from C'Net wrote an article a few days later, saying that he'd got his wifi working with a program called Wifi Radar, which one of the article's readers had suggested to him.

I've got internal wifi. Worked out-of-the-box. Still working right now. Computer is about 3 weeks old. Brilliant.

---

### Post by Darkhack on 2008-01-19
> **3rdalbum said:**
> The guy from C'Net wrote an article a few days later, saying that he'd got his wifi working with a program called Wifi Radar, which one of the article's readers had suggested to him.

Exactly.  Ubuntu has great wireless support.  It's NetworkManager that makes it FUBAR.  The *very* first thing I do when I install Ubuntu is remove NetworkManager.  The second thing I do is remove powernowd because all it does is causes kernel panics and hard freezes, but that's a different issue than the topic at hand.

---

### Post by rustybronco on 2008-01-19
> **Gary Stout said:**
> I had a Linksys wusb54g v4 that gave me fits. Some times it would work, but 80% of the time it did not. 
[http://ubuntuforums.org/showpost.php?p=3609183&postcount=1](http://ubuntuforums.org/showpost.php?p=3609183&postcount=1)

other than that device I have 6 different wireless card that work out of the box,  t.i acx-111, broadcom bcm4318, ralink rt2600, atheros ar2413 chipsets ect.
[http://ubuntuhcl.org/pub/products.php?category_id=32&manufacturer_id=289](http://ubuntuhcl.org/pub/products.php?category_id=32&manufacturer_id=289)
[http://ubuntuhcl.org/pub/products.php?category_id=32&manufacturer_id=19](http://ubuntuhcl.org/pub/products.php?category_id=32&manufacturer_id=19)
[http://ubuntuhcl.org/pub/reviews.php?product_id=503](http://ubuntuhcl.org/pub/reviews.php?product_id=503)
I'd give it a B+ myself

---

### Post by olskar on 2008-01-19
Yes, its a pity Network Manager 7 will not be in hardy :(

---

### Post by SonicSteve on 2008-01-21
> **Darkhack said:**
> Exactly.  Ubuntu has great wireless support.  It's NetworkManager that makes it FUBAR.  The *very* first thing I do when I install Ubuntu is remove NetworkManager.  The second thing I do is remove powernowd because all it does is causes kernel panics and hard freezes, but that's a different issue than the topic at hand.

From my own experience and witnessing that of others I would have to offer a third opinion. 
Perhaps it doesn't deserve an F but nor does it warrant the description of " great". I've tried 3 or 4 different wireless cards and to this point only 2 have worked and only one of those two worked well. One of the 4 worked slightly with ndiswrapper the other not at all. Even with Ndiswrapper it would lock the computer when I tried to login to the encrypted router.

Perhaps not F
but certainly not "great"

---

### Post by 3rdalbum on 2008-01-22
> **Darkhack said:**
> Exactly.  Ubuntu has great wireless support.  It's NetworkManager that makes it FUBAR.

Agreed. NetworkManager does seem pretty buggy - every few weeks I lose the connection and have to switch to another network and then switch back! Seems like a NetworkManager problem.

---

### Post by ddrplayer512 on 2008-01-22
I can understand your expierence with wifi. On my old laptop, wifi sucked with Linux. The Intel ipw3945 wirless card I have worked just fine with Ubuntu.

---

### Post by freebeer on 2008-01-22
FWIW, the wireless that shipped with my Dell laptop (XP factory installed) never worked properly (usually extremely poorly or not at all) for 3 years until they finally released a driver that actually worked.  It's not all "rosey" in the Windows world either.  ;)

---

### Post by SonicSteve on 2008-01-24
Has anyone tried this? It's called wifi radar, I read about it on Technet
[http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)

---

