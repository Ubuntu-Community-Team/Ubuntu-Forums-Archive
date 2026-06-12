---
title: "POLL Do you want RTX? Cross-website-post."
date: 2019-02-15
forum: Ubuntu, Linux and OS Chat
---

### Post by doark on 2019-02-15
Hey, I heard from 1 of the people that do HW reviews that AMD was considering implementing their very own RTX and looking at what people think of RTX. I got 6 votes in 27 hours at LQ :( so I'm trying to reach a larger audience by posting here. Please vote only on 1 site.
Ray Tracing eXtensions are a physical part of the GPU and consume a significant portion of the die space. It is not marketing jargon.
If the RTX GPU has Linux support and some games to play would you purchase a GPU with RTX or RTX like HW?
Bear in mind that AFAIK current Nvidia GPU's do RTX by partially ray tracing the scene (shadows only), at a low resolution. Then use an AI to fill in the missing shadow pixels and finally use the AI to blow the image way up to 1080p at an astounding ~30fps :redface:!!!
My intention is to give AMD some idea of what you guys think.
Feel free to comment also!

Note to voters: Most of the answers that are "no..." become "yes..." if/when Nvidia and AMD do fix the stated problem. And I have listed the common ones.

FYI: Some people think I'm using this poll to pressure AMD/Nvidia. This was *never* my intent. Nvidia has things like physX and hairworks that AMD doesn't and AMD has things like Vega's HBM being used as an LLC (last level cache), that Nvidia does not have. This poll is intended to bring Linux folks into the conversation.
For those of you who will not be buying a new GPU until yours becomes unsupported and/or breaks feel free to check the 2nd option: "Yes, if it's in the same product so that I must buy it if I purchase a GPU."

See below for options, I can't seem to get the official poll SW to work.

---

### Post by TheFu on 2019-02-15
There isn't any "poll" here. Don't think you did this correct.

I just bought a new GPU - first discrete GPU since spending $30 in 2010.  Only reason was because none of the older GPUs were working at 1200p resolutions.  

I don't game much, but did look at features and wanted h.265 encoding support in the hardware for the new GPU. THAT was important to me.  I had to fight to get the GPU to work with my KVM and 1920x1200 monitor because they dropped support for VGA.  Never intended to buy a new KVM or monitor just because last years lower end GPU only had DVI-D and HDMI output.  Ended up getting an active DVI-D converter after trying to force HDMI through a VGA converter that was limited to 1080p (I suppose).  I use HDMI for specific purposes here.  Anyway, using the current proprietary driver for the card, in debug mode helped me figure out that the DVI-D converter EDID wasn't putting out 1200p resolutions.  Had to disabled the driver from trusting any hardware, then manually load the EDID data using another machine (which was going though the KVM already using VGA), and eventually, I got 1920x1200 resolutions offered.

It shouldn't be this hard.

I barely use the GPU on that machine. It is mainly a VM server running email, blogs, websites, VPNs, and a few other services. Most access is via ssh with and without X11 forwarding.

No clue what RTX does or how it might help.  Probably won't matter since I'm still working on games from the 1990s.

---

### Post by doark on 2019-02-15
It appears that there is a bug or something in the server. I keep getting 403 forbidden. I have tried different web browsers and ip addresses just in case. No go.
Here is the question and options I had in mind. Just post a normal reply for now.

Are you interested in buying a GPU with RTX?


Yes, if it's in a different product so that I can buy it separately.
Yes, if it's in the same product so that I must buy it if I purchase a GPU.
No, the cost would have to be 2x less.
No, the cost would have to be 5x less.
No, It's just a hype.
No, the performance is too low. It must be 10x faster to be worth it.
No, the performance is too low. It must be 100x faster to be worth it.
No, I don't play games (Lier :) ).

---

### Post by doark on 2019-02-15
> **TheFu said:**
> I just bought a new GPU - first discrete GPU since spending $30 in 2010.  Only reason was because none of the older GPUs were working at 1200p resolutions.  

I don't game much, but did look at features and wanted h.265 encoding support in the hardware for the new GPU. THAT was important to me.  I had to fight to get the GPU to work with my KVM and 1920x1200 monitor because they dropped support for VGA.  Never intended to buy a new KVM or monitor just because last years lower end GPU only had DVI-D and HDMI output.  Ended up getting an active DVI-D converter after trying to force HDMI through a VGA converter that was limited to 1080p (I suppose).  I use HDMI for specific purposes here.  Anyway, using the current proprietary driver for the card, in debug mode helped me figure out that the DVI-D converter EDID wasn't putting out 1200p resolutions.  Had to disabled the driver from trusting any hardware, then manually load the EDID data using another machine (which was going though the KVM already using VGA), and eventually, I got 1920x1200 resolutions offered.

It shouldn't be this hard.
Ouch.
VGA has been the defacto standard for GPU-to-monitor connection for some time. Both Nvidia and AMD decided to get rid of them, but it appears that you can still find a very few cards that support it.
For example (I'm using Newegg because of there customer support vs. ebay where you can get scammed really easily. These ship from the USA, not china):
[https://www.newegg.com/Product/Product.aspx?Item=9SIA5758SP5171](https://www.newegg.com/Product/Product.aspx?Item=9SIA5758SP5171)
[https://www.newegg.com/Product/Product.aspx?Item=9SIA5758PB6681](https://www.newegg.com/Product/Product.aspx?Item=9SIA5758PB6681)

There are definitely MBs that have it: [https://www.newegg.com/Product/Product.aspx?Item=N82E16813144192](https://www.newegg.com/Product/Product.aspx?Item=N82E16813144192)
If I might ask, what driver and what card? I personally also have an active HDMI to VGA adapter and a passive DVI to VGA and they work well. I've never tried 1200p though. Here's my active one, it is currently out of stock: [https://www.newegg.com/Product/Product.aspx?Item=9SIA6706CZ4918](https://www.newegg.com/Product/Product.aspx?Item=9SIA6706CZ4918)

I hope it helps!

---

### Post by lisati on 2019-02-16
> **doark said:**
> It appears that there is a bug or something in the server. I keep getting 403 forbidden. I have tried different web browsers and ip addresses just in case. No go.

Not necessarily. Sometimes there's a glitch (e.g. when the forum is busy), and sometimes it's the contents of the post. Take a look at the Forum Feedback and Help section of the forum, and search for the keyword "Forbidden"

For example: [https://ubuntuforums.org/showthread.php?t=2405322](https://ubuntuforums.org/showthread.php?t=2405322) (take a look at the 6th post in the thread)

---

### Post by doark on 2019-02-17
It was brought to my attention that other (FLOSS) implementations appear to have better performance [http://brechpunkt.de/q2vkpt/](http://brechpunkt.de/q2vkpt/) than Shadow of the Tomb Raider!

---

### Post by doark on 2019-02-18
> **lisati said:**
> Not necessarily. Sometimes there's a glitch (e.g. when the forum is busy), and sometimes it's the contents of the post. Take a look at the Forum Feedback and Help section of the forum, and search for the keyword "Forbidden"

For example: [https://ubuntuforums.org/showthread.php?t=2405322](https://ubuntuforums.org/showthread.php?t=2405322) (take a look at the 6th post in the thread)

Thank you lisati, but I fail to see how that helps me now.

---

### Post by MartyBuntu on 2019-02-18
> **doark said:**
> Ouch.
VGA has been the defacto standard for GPU-to-monitor connection for some time. Both Nvidia and AMD decided to get rid of them, but it appears that you can still find a very few cards that support it.
For example (I'm using Newegg because of there customer support vs. ebay where you can get scammed really easily. These ship from the USA, not china):
[https://www.newegg.com/Product/Product.aspx?Item=9SIA5758SP5171](https://www.newegg.com/Product/Product.aspx?Item=9SIA5758SP5171)
[https://www.newegg.com/Product/Product.aspx?Item=9SIA5758PB6681](https://www.newegg.com/Product/Product.aspx?Item=9SIA5758PB6681)




I wasn't aware that 10XX series cards had VGA connectors...NVIDIA dropped analog support for this generation.

These look like fake, BIOS modified graphics cards.

---

### Post by doark on 2019-02-18
That is possible, which is why I used newegg.
But even so, you can still use passive DVI to VGA, unless all DVI ports are digital. I've not checked, but I've been meaning to.

---

### Post by TheFu on 2019-02-19
> **doark said:**
> That is possible, which is why I used newegg.
But even so, you can still use passive DVI to VGA, unless all DVI ports are digital. I've not checked, but I've been meaning to.

First, I solved my issue before posting anything to this thread. It was a rant. If I needed help, a fresh thread is how we do that here. 
 There are many fake GPUs out there, with modified firmware on older, off-lease, variants. I've seen GT 740 GPUs modified this way to report as 1050 and 1060 GPUs.  Just google "nvidia fakes". Best to check the official specs from the vendor site.  Newegg has a marketplace where 3rd parties can sell stuff. The only way that I know to get a non-fake GPU is to walk into a physical store with a good reputation and pull it off the shelf.  Online retailers with market-place setups like Newegg, amazon, ebay all have fake merchandise issues.

---

### Post by MartyBuntu on 2019-02-19
> **TheFu said:**
> Online retailers with market-place setups like Newegg, amazon, ebay all have fake merchandise issues.


Unfortunately, this is very true. The best thing would be to purchase from somewhere with a good return policy.

---

### Post by doark on 2019-02-27
The poll should end tonight (in about 6 and 1/2 hours).
If you did not vote you still have a chance.

---

