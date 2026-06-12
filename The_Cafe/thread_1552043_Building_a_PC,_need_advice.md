---
title: "Building a PC, need advice"
date: 2010-08-13
forum: The Cafe
---

### Post by theraje on 2010-08-13
Hey folks!

I used to build computers as part of my work, but I haven't had the privilege to build a computer in years... since the days the Pentium 4 was just coming to market. Since then, I've bought my computers pre-fabricated and cheap. In fact, most of the computers I currently own and use are Atom-based.

Now I want to build myself a decent system that will serve me for a few years, but won't break the bank (too much :) ). I was thinking of starting with a hexcore processor. The Intel hexcores are really, really expensive, but the AMD models are a fraction of the price.

I like the AMD Phenom II X6 1055T (2.8GHz, AM3) for $200. Problem is, I'm confused as to what motherboards will support this processor. Things have changed a bit, so I assume the CPU FSB speed (4000MHz) has to be matched with the motherboard FSB... but all the motherboards I found on Newegg with AM3 sockets only have 2600MHz FSBs. (I've never build an AMD system, even when I was working - my boss insisted on Intel processors.)

Is there something I'm missing somewhere? Should I look somewhere besides Newegg? Or am I misinterpreting the specs?

I'm basically looking for a motherboard with SATA III 6Gb/s and USB 3.0 support, and preferably two PCI-e x16 slots. If something like this that supports the AMD Phenom II X6 processors is out there, or if you can lead me in the right direction on the FSB issue, please let me know.

Thanks guys!

---

### Post by Paqman on 2010-08-13
> **theraje said:**
> Things have changed a bit, so I assume the CPU FSB speed (4000MHz) has to be matched with the motherboard FSB... but all the motherboards I found on Newegg with AM3 sockets only have 2600MHz FSBs.

It doesn't have to be matched, but the mobo will limit the throughput, so you're not getting the most out of the chip.

---

### Post by Elaztic on 2010-08-13
Just keep in mind that there will always be bottlenecks in your setup but they will be different depending on your use case.

Most games will use GPU and RAM so make sure your RAM bandwidth matches your FSB and you have a solid graphics card.
For other types of applications you would make a lot of IO to the harddrive so investing in a fast drive (SSD or hybrid SATA/SSD) should be your focus here.

It used to be so that Intel based CPUs were better supported but I don't know if that's true any more - perhaps some else can contribute some knowledge here. I do know that Intel are very active in the Linux community and are contributing to the Moblin/MeeGo distros.

Hope this will help in your hardware choices.

---

### Post by cascade9 on 2010-08-13
Ohh dear. The old "FSB/Hypertransport" problem again, compouned by the 'marketing' droids. 

When newegg says "FSB" on on newer AMX motherboards, they are wrong....at least in part. What they actually mean is "HyperTransport". Well, HyperTransport technically is FSB (the connection between the CPU and the northbridge) but that is not what most people think of as FSB in my expereience. 4000MHz is just wrong, it runs at 2000MHz (each way). It should be MT/s (MegaTransfers per second) as well from what I know. 

Anyway, to cut through the marketing, the newer ATI and nVidia chipsets do 5200MT/sec, or 2600MHz HyperTransport. The AM3 CPUs with 2000MHz/4000MT/s get full bandwidth, with a nice amount left over in case you want to overclock, etc.. 

As for specific motherboards that support the Phenom II X6 CPUs, there are tons of them. Almost all the AM3 motherboards should, the main reason why they wouldnt is because the X6 CPUs are 125watts TDP, and some motherboards are limited to 95watts TDP CPUs. 

To get SATAIII, you really want a new the ATI 870, 890FX, 890GX or 880G chipset. Since you have said you would perfer 2 PCIe x16 slots, I am guessing you plan on running a video card, so throw out the 890GX/880G (both onboard video chipsets, pointless if you are running a video card). 

So that leaves the 870 and 890FX. The 870 can have 2 x PCIe x16 slots, but one of those slots is limited to PCIe x4. If that is not an issue for you, the 870s are a lot cheaper. 890FX is the 'top of the line' ATI chipset, commonly with more PCIe x16 slots than any sane person would ever want. Typically its at least 2 x PCIe x16 slots at full speed, with at least 1 PCIe x16 slot at x4 connection speed. Some boards come with up to 6 PCIe x16 slots! 

Most of the 870/890FX chipset boards I've seen support USB 3.0 as well. AFAIK, the only motherboard to have USB 3.0 ports motherboard ports that can be used hook up to front panel connectors is the Asrock 890FX Deluxe 3. Worth keeping in mind if you want to plug in/remove USB 3.0 devices without reaching round the back.....

---

### Post by Drenriza on 2010-08-13
What i found was the
Gigabyte GA-890FXA-UD5 (rev. 2.0) to satisfy the needs.

---

### Post by qualtch on 2010-08-13
> **cascade9 said:**
> Ohh dear. The old "FSB/Hypertransport" problem again, compouned by the 'marketing' droids. 

When newegg says "FSB" on on newer AMX motherboards, they are wrong....at least in part. What they actually mean is "HyperTransport". Well, HyperTransport technically is FSB (the connection between the CPU and the northbridge) but that is not what most people think of as FSB in my expereience. 4000MHz is just wrong, it runs at 2000MHz (each way). It should be MT/s (MegaTransfers per second) as well from what I know. 

Anyway, to cut through the marketing, the newer ATI and nVidia chipsets do 5200MT/sec, or 2600MHz HyperTransport. The AM3 CPUs with 2000MHz/4000MT/s get full bandwidth, with a nice amount left over in case you want to overclock, etc.. 

As for specific motherboards that support the Phenom II X6 CPUs, there are tons of them. Almost all the AM3 motherboards should, the main reason why they wouldnt is because the X6 CPUs are 125watts TDP, and some motherboards are limited to 95watts TDP CPUs. 

To get SATAIII, you really want a new the ATI 870, 890FX, 890GX or 880G chipset. Since you have said you would perfer 2 PCIe x16 slots, I am guessing you plan on running a video card, so throw out the 890GX/880G (both onboard video chipsets, pointless if you are running a video card). 

So that leaves the 870 and 890FX. The 870 can have 2 x PCIe x16 slots, but one of those slots is limited to PCIe x4. If that is not an issue for you, the 870s are a lot cheaper. 890FX is the 'top of the line' ATI chipset, commonly with more PCIe x16 slots than any sane person would ever want. Typically its at least 2 x PCIe x16 slots at full speed, with at least 1 PCIe x16 slot at x4 connection speed. Some boards come with up to 6 PCIe x16 slots! 

Most of the 870/890FX chipset boards I've seen support USB 3.0 as well. AFAIK, the only motherboard to have USB 3.0 ports motherboard ports that can be used hook up to front panel connectors is the Asrock 890FX Deluxe 3. Worth keeping in mind if you want to plug in/remove USB 3.0 devices without reaching round the back.....

This answer collects together few days I spent time searching and reading various articles and benchmarks in the web. This is the best answer to your question I'd say, since according to your topic title message you're looking for high-end motherboard with expandability. :)

To add some few questions:

Are you planning to CF your graphics? Do you want and need high-end performance with no limits? Are you going to use USB 3.0 peripherals and need a front-panel connection for them?

Then go for 890FX.

Do you want to save money e.g. for better RAM or GFX?

CF @ x8 and CF @ x16 performance differences aren't that huge (5-15% at maximum, also depends on game), so if you don't need the absolute max performance the 890GX suits you well. On-board USB 3.0 connection isn't necessary if you aren't going to use them at front panel e.g. I was planning to buy one without the support and probably buy PCI-E USB 3.0 -card later on as I'm not sure if I'm going to *need *front panel connectors. 890GX also provides SATA 6Mbit/s connectors.

---

### Post by theraje on 2010-08-13
Wow, lots of good info in this thread - thanks a load, guys!

I'll look around for a board with this information in mind, and post back what I find.

By the way, I'm mainly building this machine so I can have something that will handle what my current machines can't (which would primarily be gaming and VM), and will last me a few years (with or without upgrades). My problem is I have a bunch of "secondary" PCs, and no real "main workhorse." I'd rather spend a bit more now than to keep buying whole machines that are already outdated, or will be outdated in a month. :)

---

### Post by sidzen on 2010-08-13
[http://www.msi.com/index.php?func=proddesc&maincat_no=1&prod_no=2104](http://www.msi.com/index.php?func=proddesc&maincat_no=1&prod_no=2104) may be a place to start, esp for gaming, 3D, inter-operability, OCing  Intel, however.

---

### Post by Dustin2128 on 2010-08-13
[here's]("http://ubuntuforums.org/showthread.php?t=1536204") my list of components for the 450$ computer I'm building (once I finish saving my money...). The main things that aren't on there are things I'm salvaging from my old one, like a monitor, keyboard, optical drives etc.

---

### Post by xDeja on 2011-03-22
Thank you so much for this info cascade9. Thats a huge mistake on Neweggs part to confuse Mhz with Mt/s. 

hours of researching is now complete!

---

