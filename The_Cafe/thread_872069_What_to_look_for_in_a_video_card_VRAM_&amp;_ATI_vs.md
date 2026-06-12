---
title: "What to look for in a video card?? VRAM &amp; ATI vs Nvidia"
date: 2008-07-27
forum: The Cafe
---

### Post by jbrown96 on 2008-07-27
I'm trying to play video on my TV from a Kubuntu box, but it's turning into quite a mess. The box came with a Nvidia 6150 Go or something equally horrible. It had 64MB of memory on the card. The processor was a P4 2.8GHz with 1GB of RAM. It plays standard videos fine but completely chokes on anything hi-def. I then purchased a used computer with a pci-e slot because I have a Nvidia Quadro FX 540 (128MB) from work that was no longer used. I hooked that up to the new box: P4 3.0GHz, 1GB RAm. It works fine when there isn't much motion, but it freezes and pixelates under load. 
On a related note, I have a Nvidia Quadro FX 570m (256MB, I think) in my laptop, which plays the same hi-def videos fine. 
What makes a video card good? Should I be looking for a specific amount of VRAM or clock speed? If so, what? Any idea what the bottleneck is? I'm looking for something cheap that can play, at most, 1080p video. From Newegg, I've found some that are surprisingly cheap. $35-50. [http://www.newegg.com/Product/Product.aspx?Item=N82E16814141071]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814141071")
[URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16814102080"]
[/URL] [http://www.newegg.com/Product/Product.aspx?Item=N82E16814127342]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814127342")
I have always thought that Nvidia was the way to go because their drivers, in Linux, have been far better. Is this still true?

---

### Post by geekygirl on 2008-07-27
Nvidia 6150 graphics is actually just intergrated graphics, therefore using up 64mb of shared system memory. Depending on the rest of that system as to how well it handles graphic loads, but 64mb isnt much.

Another thing could be that the motherboard doesn't support HDTV in its BIOS, or you don't have enough system memory (1G). You can always try increasing to 2G and see what happens there, but I am leaning towards a lack of BIOS support for HDTV, and your newer graphics card is able to handle to load and output an image but your motherboard cannot decode the HD signal properly.

The Quadro card you have installed will be good for that purpose but your motherboard will need a BIOS update. The Quadro card isnt a gaming card though, its a desktop card.

A good graphics card which has build in HD support in the Nvidia 8500GT, and yes Nvidia are still good cards for Linux, although ATI are fast catching up again hardware performance wise.

Another thing to consider is when you are running a 32bit operating environment (no matter if it is Linux or Windows) you are limited by the amount of memory the system can reference. Example is that a 32bit system can only reference up to 4G of system memory. Install a 512MB video card and this now leaves you with only 3.5G of system memory out your 4G install that the OS can actually use as the 512MB VRAM is also included in the 4G total memory.

Probably the best upgrade for any system when it comes to graphics performance is an increase in the system RAM, usually works wonders too!

---

### Post by gn2 on 2008-07-27
For HD video you'll probably need a much higher spec CPU.

---

### Post by smartboyathome on 2008-07-27
Now, I would say go with ATI for Linux. Their drivers are improving rapidly now, and may soon surpass Nvidia in quality on Linux.

---

### Post by stmiller on 2008-07-27
Nvidia cards under Linux do not have the HD playback stuff that the Windows driver has ("purevideo"). Nvidia has not written this feature into the Linux kernel, and this has been a big gripe.

So ANY video playback in Linux with an Nvidia card is entirely on the CPU.

I think ATI may eventually (or currently?) have better GPU support for video playback in Linux.

---

### Post by geekygirl on 2008-07-28
Wow, never realised that, but I have only ever used Nvidia cards with decent CPU's.

Thanks!

---

### Post by jbrown96 on 2008-07-28
> **stmiller said:**
> Nvidia cards under Linux do not have the HD playback stuff that the Windows driver has ("purevideo"). Nvidia has not written this feature into the Linux kernel, and this has been a big gripe.

So ANY video playback in Linux with an Nvidia card is entirely on the CPU.

I think ATI may eventually (or currently?) have better GPU support for video playback in Linux.

I never would have thought that, but it seems entirely right. My CPU usage (P4 3GHz) is between 80-100% when playing videos. In comparison, my laptop (C2D 2GHz) is less than 15%. Do you have any more info on the ATI driver support?

---

### Post by manojiitan12 on 2008-07-28
What to look for in a video card.VRAM & ATI vs Nvidia are usually are good product for video cards in mobile phones. You can look the comparison at notebook vga guide section. But from my experience, X1300 outperforms 7300 in 3DMark03/05 but not significant. For light gaming both cards is same, you hardly notice the diff.between them.



mack


[Epson T048]("http://www.concordsupplies.com/epson-t048-ink-cartridges-6-pack/43479.html")

---

