---
title: "laptop from 2006, 1GB RAM, use for watching Youtube, what are my options?"
date: 2020-12-08
forum: Ubuntu, Linux and OS Chat
---

### Post by salamilimos on 2020-12-08
**Dell Inspiron E1505 (64-bit)**
Intel Core 2 Duo Processor T7200 at 2.0 GHz per core.
1GB DDR2 667MHz RAM in dual channel mode
ATI X1400 256MB graphics card
120GB SATA SSD
Dell Wireless 1500 (802.11)

  While the RAM is upgradable to 2GB, DDR-2 RAM, especially for laptops is hard to come by these days, so I'm limited to 1GB RAM, also, online shopping isn't an option for me because I don't have a debit or credit card.

I will be using this laptop mostly for watching YouTube videos, so what distro would be cool for this laptop? I'm looking for a distro that is easy to install and hassle free, so that rules out Puppy Linux because I've tried that distro on Virtualbox, the installer was confusing.

Also, it has to be a distro that I can use with Startup Disk Creator to create a liveUSB of. Thanks.

---

### Post by CelticWarrior on 2020-12-08
It's a 32-bit computer. Your options a very limited.
Currently Debian still support 32-bit.

---

### Post by salamilimos on 2020-12-08
> **CelticWarrior said:**
> It's a 32-bit computer. Your options a very limited.
Currently Debian still support 32-bit.

Thank you for reminding me, I forgot to mention, this laptop is 64-bit.

---

### Post by CelticWarrior on 2020-12-08
> **salamilimos said:**
> Thank you for reminding me, I forgot to mention, this laptop is 64-bit.

No, it isn't.
Intel Core Duo is 32-bit. I don't know why you edited the OP to give less (and misleading) information.

---

### Post by salamilimos on 2020-12-08
> **CelticWarrior said:**
> No, it isn't.
Intel Core Duo is 32-bit. I don't know why you edited the OP to give less (and misleading) information.

I wasn't sure anymore about the specs of the laptop's Core Duo because I don't have the laptop right now with me, it's back in my house, and I'm not at home right now.

I know it's 64-bit because I tried my liveUSB of Xubuntu 20.04 64-bit on it and it booted. I've heard that XFCE isn't good for 1GB RAM, especially if I'm going to use it for playing Youtube videos, is that true?

---

### Post by salamilimos on 2020-12-08
> **CelticWarrior said:**
> No, it isn't.
Intel Core Duo is 32-bit. I don't know why you edited the OP to give less (and misleading) information.

Sorry, the laptop is a Intel Core 2 Duo, sorry for the confusion, I'll correct the specs.

---

### Post by CelticWarrior on 2020-12-08
Nothing is good with 1GB RAM nowadays; some very light distros work acceptably; Debian works acceptably but nothing will really work for Youtube.

This [2006 review of a Dell Inspiron E1505]("http://www.notebookreview.com/notebookreview/dell-inspiron-e1505-review-pics-specs/"), not necessarily yours, shows it's a 64-bit machine, because is has an **Intel Core Duo** CPU (64-bit), not an Intel Dual Core (32-bit).

Please do not waste our time with wrong specs. Confirm them and post the correct ones.
Either way, although it being a 64-bit machine, gives you a lot more options, for the purpose you want - Youtube - nothing will work acceptably beyond 480P and even that is a stretch. Youtube and the whole internet is VERY different than it was in 2006.

---

### Post by salamilimos on 2020-12-08
> **CelticWarrior said:**
> Nothing is good with 1GB RAM nowadays; some very light distros work acceptably; Debian works acceptably but nothing will really work for Youtube.

This [2006 review of a Dell Inspiron E1505]("http://www.notebookreview.com/notebookreview/dell-inspiron-e1505-review-pics-specs/"), not necessarily yours, shows it's a 64-bit machine, because is has an **Intel Core Duo** CPU (64-bit), not an Intel Dual Core (32-bit).

Please do not waste our time with wrong specs. Confirm them and post the correct ones.
Either way, although it being a 64-bit machine, gives you a lot more options, for the purpose you want - Youtube - nothing will work acceptably beyond 480P and even that is a stretch. Youtube and the whole internet is VERY different than it was in 2006.

I apologize for the confusion, this was a stupid rookie mistake, it won't happen again. The specs I reposted is the correct specs, and yes, the it's an Intel Core 2 Duo, 64-bit. Once again, sorry for the confusion.

---

### Post by grahammechanical on 2020-12-08
This problem I can see with the specifications of that laptop is the amount of video memory - 256 MB. I built my desktop machine about 2007. It had an Intel Core 2 Duo, I GB Ram and 256 MB video memory.

My machine is running the very latest Ubuntu but now with 4 GB Ram and a video card that has 1 GB video memory. Xubuntu or Lubuntu will be better suited to this machine than Ubuntu. In my opinion. Expect videos to pause while the cache is updated. Internet broadband download rate might be a cause of videos pausing and not just the limits of video memory.

Regards

---

### Post by salamilimos on 2020-12-08
> **grahammechanical said:**
> This problem I can see with the specifications of that laptop is the amount of video memory - 256 MB. I built my desktop machine about 2007. It had an Intel Core 2 Duo, I GB Ram and 256 MB video memory.

My machine is running the very latest Ubuntu but now with 4 GB Ram and a video card that has 1 GB video memory. Xubuntu or Lubuntu will be better suited to this machine than Ubuntu. In my opinion. Expect videos to pause while the cache is updated. Internet broadband download rate might be a cause of videos pausing and not just the limits of video memory.

Regards

I have checked out Lubuntu 20.04 before, in fact, I was on Lubuntu 18.04 on my main desktop, which is 8GB RAM, until Lubuntu dropped LXDE and switched to LXQT, so I switched over to Xubuntu.

Does laptop having an 120GB SSD make a difference in performance? What about Peppermint OS? I heard that's a lightweight distro similar to Lubuntu. Can I use Startup Disk Creator to make a liveUSB of Peppermint?

---

### Post by ajgreeny on 2020-12-08
My suggestion would be Debian 10-LXDE with openbox as the window-manager, and to login using openbox, not LXDE.

You can easily add lxpanel to openbox to give you a very simple desktop; this is the best way I found to use an old netbook also with just 1G RAM, and a 32bit Atom 270N cpu, however, I suspect you may have to think of something else if Youtube videos is your main source of amusement, as they will not play well enough to watch on my machine.

Otherwise, Debian is now so like Ubuntu, even down to being able to use sudo in the same way by using the same password for root as you do for user.

---

### Post by kansasnoob on 2020-12-08
I personally think it would be well worth upgrading to 2GB RAM if you could get someone to find a matched set of 1GB sticks on Ebay or something of that nature.

But even with 1GB you may be able to get by with BunsenLabs Lithium:

[https://www.bunsenlabs.org/installation.html](https://www.bunsenlabs.org/installation.html)

Since you have an SSD be sure and create a physical swap partition of 4 to 6 GB - that should help quite a bit!

Heck, I just went and looked and I have two 1GB sticks of DDR2-667 (1 Nanya and 1 Hynix but both 555-12 timing) and one single 2GB stick of Crucial DDR2-667. What exact make and model laptop is that? I'd send you what you needed out of those three sticks for free if you're in the US - shipping shouldn't be very high here in the lower 48 :)

Just please share the make and model so I know I'm not spinning my wheels. Oh and I'll want to test these first to be sure they're good, but that's easy in a Dell Latitude E6400 (only one screw to remove).

---

### Post by kansasnoob on 2020-12-08
BTW, don't share you address or other personal info on the forum! If you decide you want some of these sticks of RAM click on my userID (kansasnoob) and select private message.

---

### Post by salamilimos on 2020-12-08
> **kansasnoob said:**
> I personally think it would be well worth upgrading to 2GB RAM if you could get someone to find a matched set of 1GB sticks on Ebay or something of that nature.

But even with 1GB you may be able to get by with BunsenLabs Lithium:

[https://www.bunsenlabs.org/installation.html](https://www.bunsenlabs.org/installation.html)

Since you have an SSD be sure and create a physical swap partition of 4 to 6 GB - that should help quite a bit!

Heck, I just went and looked and I have two 1GB sticks of DDR2-667 (1 Nanya and 1 Hynix but both 555-12 timing) and one single 2GB stick of Crucial DDR2-667. What exact make and model laptop is that? I'd send you what you needed out of those three sticks for free if you're in the US - shipping shouldn't be very high here in the lower 48 :)

Just please share the make and model so I know I'm not spinning my wheels. Oh and I'll want to test these first to be sure they're good, but that's easy in a Dell Latitude E6400 (only one screw to remove).

Thanks for the offer, but I don't live in the US, and even if I did, I  wouldn't give anyone my address even in private message, I'm kinda  cautious about my privacy, my parents taught me never to reveal my  address to strangers, I hope you're not offended by that, that's how I  was raised.

The model of the laptop is at the beginning of the thread. Anyway, for now, I'll have to live with 1GB RAM and 120GB SSD. I've read somewhere that you can use USB drives as RAM, is that possible?

---

### Post by CelticWarrior on 2020-12-08
> [COLOR=#000000]I've read somewhere that you can use USB drives as RAM, is that possible?[/COLOR]

No, it isn't.

---

### Post by salamilimos on 2020-12-09
> **CelticWarrior said:**
> No, it isn't.

[https://www.wikihow.com/Use-Pen-Drive-As-RAM](https://www.wikihow.com/Use-Pen-Drive-As-RAM)

This is a tutorial on how to use a USB pen drive as RAM, but this tutorial is for Windows though, so it's possible on Windows but not on Linux then?

---

### Post by CelticWarrior on 2020-12-09
Yes, ReadyBoost is exclusive to Windows and no, ReadyBoost isn't the same as adding RAM. The title is very misleading.

---

### Post by EuclideanCoffee on 2020-12-10
You have higher specs than my HP laptop. I use [https://www.windowmaker.org/](https://www.windowmaker.org/) as my desktop environment. I use Palemoon as my Internet browser. I can't stream video very well, but I can play music and video from my SSD... however I do not play much video or music, typically stuff from friends. Do not use hard drive on this platform, as it's too slow. :)

---

### Post by i-choose-linux on 2020-12-18
I have the same model laptop but with a 32-bit processor.  I believe they made them with both 32 and 64-bit processors.  I have mine running Linux Mint Xfce but with 2GB of RAM.  It does surprisingly well on the internet and can view videos.  These are well built machines.  It was given to me about 3 years ago and I keep it around because it is something of an antique.  Memory is available on eBay. When I got my machine it had 1GB of bad memory and I decided to upgrade to 2GB.  If I replace the operating system when it reaches end of life I will probably use antiX.  I've used it on other low end machines and it uses less memory than Debian, but Debian is pretty good also.  There might be some benefits to just using a 32-bit OS because my experience is that they use less memory.

---

