---
title: "Ubuntu Soundcard experience"
date: 2020-11-07
forum: The Cafe
---

### Post by tmlake on 2020-11-07
Hello all,

I'm very upset with the Soundcards support for the Linux platform.
It's such a good and important piece of hardware, but of all it is the most problematic. 
I use it for a Home-Theatre.
No need to develop complicated third-party drivers, just a plug-and-play from the Kernel.

So, I need to buy a new soundcard for my Linux system.

Best vendors are Asus, which in my opinion has the most stable drivers and full use of the card
[https://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus](https://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus)

And Creative, but Linux support is very buggy
[https://www.alsa-project.org/wiki/Matrix:Vendor-Creative_Labs](https://www.alsa-project.org/wiki/Matrix:Vendor-Creative_Labs)

However this ALSA page is far from updated, the latest driver is for Kernel 3.8 and Xonar DSX.

I believe there are many others working models not shared on these pages, like this guy with an Xonar AE:
[https://www.amazon.com/gp/customer-reviews/R3FGKQ7IBL3OML/ref=cm_cr_arp_d_rvw_ttl?ie=UTF8&ASIN=B077DGQFTF](https://www.amazon.com/gp/customer-reviews/R3FGKQ7IBL3OML/ref=cm_cr_arp_d_rvw_ttl?ie=UTF8&ASIN=B077DGQFTF)

And here, Xonar SE and others (translate the page to English)
[https://www.muylinux.com/2019/04/15/calidad-sonido-linux-asus-xonar-essence/](https://www.muylinux.com/2019/04/15/calidad-sonido-linux-asus-xonar-essence/)

Which brand do you think has the best sound quality for playing music?
I'm really not interested in gaming, but a gaming soundcard is most welcomed.

For the last couple of years I've been messing around with the Asus Xonar D2 with excellent use without any issue.
I gotta say it really improves the sound, a lot. The sound of my onboard Realtek ALC1150 is hollow like a greyish xerox, compared to the colorful Monet, full-bodied sound a Xonar D2 gives.

As with all soundcards, it just requires a simple adjustment on alsamixer in the Terminal, and increase all channels to 100%.

But sadly it got fried and now I'm looking for a replacement. Still I recommend it, blindly.
I'm thinking of the Xonar AE, but I'm afraid of a weak support, when there's not enough documentation.
If I get too worried, then I'll go with the Xonar DGX.

Perhaps if Xonar AE having the same CM6632A chipset as Xonar U7, ALSA will accept it?

Anyone who has successfully ran a soundcard on Ubuntu not listed on ALSA page, please share us a feedback.

Please share here documentation, guidance and experiences found around the web.

Many thanks.

---

### Post by QIII on 2020-11-07
Let me help you with a misapprehension:  Drivers are created by the ***OEMs***, not my Linux developers and not by Windows developers. If things work in Windows, it's because the ***OEMs*** make sure they do because not doing so would mean certain death.  Microsoft doesn't lift a finger to help.

If Linux developers are able to create something to replace a non-functional OEM driver, then they are doing so blindly into a black box, since they do not have direct knowledge of the inner hardware workings.

Saying "Just write a driver, Linux guys" demonstrates a significant misunderstanding.

---

### Post by tmlake on 2020-11-07
It was not my intention at all, I understand it requires time and effort from well-intentioned people that mostly do it without an earned remuneration.
Which OEM is really dedicated for the Linux community, when things work.. AMD and... :-|

Just take a look at the situation, almost every videocard on the market is plug-and-play, processors, open-source drivers are excellent.
Now audiocards suffer a preconception of not being an essential component of a PC build and most people think they won't even notice a difference. If you sit and listen to all your favorite songs, you'll begin to notice the richness in details and much more. It's an essential piece of hardware for audio production, let's say Ubuntu Studio.

We're lucky when we're able to buy a working model [-o<

I criticize the lack of interest of the community overall to what could lift the Linux platform to a higher experience and reputation.

---

### Post by MartyBuntu on 2020-11-07
I didn't think audio drivers in Linux were so neglected and broken....

---

### Post by QIII on 2020-11-07
And why do you suppose they are plug and play?  Because of Microsoft developers?  No.  They are plug and play because the OEMs bend over backwards to make sure that their drivers work with Windows and can be approved for Microsoft's driverbase.  Microsofts driverbase contains drivers that the OEMs supply -- unless the hardware is branded from Microsoft. OEMs follow the money.  They exist to make a profit.  That is what businesses do.  Spending the same resources on 2% of the desktop market really doesn't make any sense from a business perspective and I don't blame them.

This will change when the OEMs provide open-source drivers that can be reviewed by the Linux kernel developers and included as modules.  I don't see anyone flushing profits to do that.

The Linux community cannot control the OEMs.

That said, I've never encountered non-functional audio.  But I don't expect digital audio to even hold a candle to Deutsche Grammophon vinyl.

---

### Post by CatKiller on 2020-11-08
> **tmlake said:**
> Which OEM is really dedicated for the Linux community, when things work.. AMD and... :-|

I wouldn't include AMD on that list. The company in that spot is Intel, save for when they'd licensed PowerVR stuff. Both AMD's and Nvidia's approaches are fundamentally flawed in different ways.

The OEMs that support Linux are the customer-facing ones that sell hardware for Linux: Dell, Lenovo, System76, and so on.

If you want hardware support for Linux then you need to buy from companies that support Linux. Tell them that's why you're buying their products, and tell companies that don't support Linux that that's why you're *not* buying their products.

In the absence of that, you have to rely on standardisation to do the work for you, which takes the hardware manufacturer out of the equation. Be very suspicious of companies that wish to eschew standards compliance in favour of "adding value."

At the bottom of the compatibility scale is hardware that is sufficiently common and sufficiently boring that other people have done the work to make it supported. It isn't their *responsibility* to do that, but they had an itch to scratch.

Hardware manufacturers that won't do the work themselves, and who hamper the efforts of others to do the work, do not deserve your money. If you give them any, you reward the creation of incompatible hardware.

---

### Post by poorguy on 2020-11-09
I've had Linux sound card problems with Creative Audio Sound Blaster cards that were from the days of Windows XP.

---

### Post by tmlake on 2020-11-10
> **CatKiller said:**
> 
If you want hardware support for Linux then you need to buy from companies that support Linux. Tell them that's why you're buying their products, and tell companies that don't support Linux that that's why you're *not* buying their products.


Very well stated. 

And donate to your favorite devs, it will just make them feel on a happier day and even consider fixing areas you require support, like Ubuntu does with its donations requests.

I wanna put my hands on an Ubuntu Phone someday.

---

### Post by MartyBuntu on 2020-11-12
I had a Creative X-Fi PCI-E card that wasn't supported back when I bought it, over ten years ago.
Creative has been borderline hostile with their Linux support.

I still have it on the shelf...maybe I'll take it out and hook it up one of these days....

---

### Post by tmlake on 2020-11-14
> **MartyBuntu said:**
> I had a Creative X-Fi PCI-E card that wasn't supported back when I bought it, over ten years ago.
Creative has been borderline hostile with their Linux support.

I still have it on the shelf...maybe I'll take it out and hook it up one of these days....

Really, it's somewhat brand new then! :lolflag:

Yes you should, take a look at

[https://www.alsa-project.org/wiki/Matrix:Vendor-Creative_Labs](https://www.alsa-project.org/wiki/Matrix:Vendor-Creative_Labs)

There's some 15 X-Fi models tested under ALSA since then, half of them fully operational.

---

