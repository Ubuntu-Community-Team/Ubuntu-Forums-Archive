---
title: "ARM and Ubuntu is way to go?"
date: 2010-01-06
forum: The Cafe
---

### Post by 1337 on 2010-01-06
There gonna be new devices on the market called smartbooks, basically a netbook running non x86 (ARM) processor running Linux. Just perfect little machines running our favourite OS and capable of playing HD videos with awesome baterry life like 8-10 hours. On this years CES 2010 (starting 5 january) some companies are showing such devices. Cannonical is working closely atleast with two ARM processor/devices makers Marvell and Freescale. Look at [this]("http://www.youtube.com/watch?v=3uWsg2pDNKI") slick design running Ubuntu :) what do you all think? I think it can be great oportunity for Ubuntu and Linux itself. This machine is a reference design running newest Marvell Armada 510 ARM based CPU but I personally would like see this in the shops.

---

### Post by windowless on 2010-01-07
I have to agree I have been watching these for some time and thing they would be great for my kids for internet use.The freescale tables also looks good but 7 inch screen is a bit small maybe 10 o 11 and use it as an ebook reader as well

---

### Post by Sef on 2010-01-07
Moved to Community Cafe.

---

### Post by Warpnow on 2010-01-07
If the Cortex a9 ever comes out we'll know for sure.

All of the other ARM chips are far too slow for most realistic applications. If the a9 doesn't represent the promised leap forward, ARM will not succeed in the desktop/netbook market.

---

### Post by Chronon on 2010-01-07
Do you have some info about that?  ARM processors are not powerful enough to do what exactly?  The hardware in the link the OP provided seemed to be doing an admirable job at full-screen video.

What makes you say that they are too "slow" for realistic applications?  (I hope you aren't referring to clock speed as that's not a meaningful measure of comparison between two different architectures.)

---

### Post by Warpnow on 2010-01-07
The A8, which is A9's predecessor is clocked at 500mhz and is what's in cell phones and MIDs. Its a nice chip. I don't have access to a testing board, but I doubt it would handle most of the default linux distributions without serious slowdowns.

The A9, on the other hand, is dual core and clocked at 2ghz, and outstrips the atom on benchmarks, or so we're told...I don't actually know anyone whose seen one.

---

### Post by iponeverything on 2010-01-07
If history is anything to go by, moving away form the x86 architecture is going to tie your hands.  I have ran linux on sparc, mips, and alpha and in every case it was a pain waiting for package ports and bug fixes to come through the pipe. And once the outfit maintaining the architecture specific version of your favourite distro drops it, you are out in the cold. 

Power requirements for x86 architecture chips is droping very quickly as companies see $$ from small devices with long battery life.

I just ordered a lenovo x200s with a su9400, it is a very capable c2d 45nm processor with a 10w TPD. The thing only weighs 2.7 pounds and should get 6 hours with the 6 cell battery. The price was within the range of the pricier Atom Netbooks..

---

### Post by Chronon on 2010-01-07
> **iponeverything said:**
> If history is anything to go by, moving away form the x86 architecture is going to tie your hands.  I have ran linux on sparc, mips, and alpha and in every case it was a pain waiting for package ports and bug fixes to come through the pipe. And once the outfit maintaining the architecture specific version of your favourite distro drops it, you are out in the cold. 

Power requirements for x86 architecture chips is droping very quickly as companies see $$ from small devices with long battery life.

I just ordered a lenovo x200s with a su9400, it is a very capable c2d 45nm processor with a 10w TPD. The thing only weighs 2.7 pounds and should get 6 hours with the 6 cell battery. The price was within the range of the pricier Atom Netbooks..

Good point.  One might hope that with the near ubiquity of ARM in modern smartphones that decent support for this architecture might be maintained in the future.  I suppose the question is whether x86 dominance in the desktop market can be extended to dominance in the ultra-portable market.  Alternatively, can ARM dominance in smartphone, GPS, PMP, etc. markets be extended to the ultra-portable (i.e. netbook) market?

ARM clearly dominates on lower end devices, else we would be using x86 in our phones and mp3 players.  It's not clear to me which will hold the edge in the ultra-portable market in the future.

---

### Post by iponeverything on 2010-01-07
> **Chronon said:**
> 
ARM clearly dominates on lower end devices, else we would be using x86 in our phones and mp3 players.  It's not clear to me which will hold the edge in the ultra-portable market in the future.

They are only as good as the applications that they will run. Netbooks had an unexpectedly strong resonance with people because:

1 - they ran about everything (though slower)
2 - they were small and light enough that carry all the time

With ARM 1) becomes "they will run what has been ported" or what has been deemed useful by someone willing to do the port..

Are people going to be willing to forgo the flexibility of an x86 device for the fixed set of functions of a smartbook? Some will be, but will it enough people to create a parallel ARM universe..

The ubiquity of x86 has enormous mass. Like it or not, it is going to be the centre of the software universe for a while. Even apple couldn't escape its pull ;)

---

### Post by hessiess on 2010-01-07
The X86 architecture is an extreme mess of extensions which is practically designed to be as power inefficient as physically possible, without requiring impractical cooling devices. As it stands, the whole `desktop' computing industry is based on outdated hardware designs.

You cannot compare a RISC architecture like ARM to a CISC architecture like X86 based only on clock speed, RISC processors run simpler instructions which do less, but complete every instruction in a single cycle. In CISC architectures individual instructions take a variable number of cycles to execute.

I doubt that the desktop computing industry can improve much feather while dragging along the enormous amount of legacy garbage that it is currently.

---

### Post by blueturtl on 2010-01-07
What packages would an ARM user be missing? AFAIK Debian supports ARM and they have a very extensive software repository. Then again going with a smaller distro you might run into porting related issues like mentioned above.

---

### Post by iponeverything on 2010-01-07
> **hessiess said:**
> The X86 architecture is an extreme mess of extensions which is practically designed to be as power inefficient as physically possible, without requiring impractical cooling devices. As it stands, the whole `desktop' computing industry is based on outdated hardware designs.

You cannot compare a RISC architecture like ARM to a CISC architecture like X86 based only on clock speed, RISC processors run simpler instructions which do less, but complete every instruction in a single cycle. In CISC architectures individual instructions take a variable number of cycles to execute.

I doubt that the desktop computing industry can improve much feather while dragging along the enormous amount of legacy garbage that it is currently.

Agreed, but while RISC is far more elegant than CISC - CISC is currently stomping on RISC's head. It seem that the mess that is CISC, is forcing innovations in silicon to compensate for its extreme stupidity. Multiple cores, huge caches and extreme clock and bus speeds.. You have to admit if the same amount energy was being spent on RISC, skynet might already be here.. So maybe we have CISC to thank for saving the human race ;)

---

### Post by iponeverything on 2010-01-07
> **blueturtl said:**
> What packages would an ARM user be missing? AFAIK Debian supports ARM and they have a very extensive software repository. Then again going with a smaller distro you might run into porting related issues like mentioned above.

The main thing that comes to mind is support for devices. System utilities can often be ported with a simple recompile. Hardware drivers are slightly more problematic.. And, of course, it takes a small army of people to maintain the kernel port!

---

### Post by Swagman on 2010-01-07
Modern CISCS CPU's actually have a Risc core <--- I kid you not. They saw the writing on the wall and incorporated it into x86 architecture.. I'm pretty sure AMD did it first and licenced the tech to intel

[edit]

Actually "core" is probably the wrong term. Extension is probably closer to what I mean.

---

### Post by hessiess on 2010-01-07
> **Swagman said:**
> Modern CISCS CPU's actually have a Risc core <--- I kid you not. They saw the writing on the wall and incorporated it into x86 architecture.. I'm pretty sure AMD did it first and licenced the tech to intel

[edit]

Actually "core" is probably the wrong term. Extension is probably closer to what I mean.

CISC prosessors are basically implemented by running a emulator, implemented in microcode on top of a micro architecture which is basically a RISC-ish CPU, its the emulator, not the hardware which is actually executing the X86 instructions and dynamically recompiling them into instructions for the actual underlying processor. CISC processors will always use more power than an equiv RISC design, because of the need for microcode, which wastes CPU cycles. This is especially true with an ancient instruction set like X86, which has a stupid number of extensions.

---

### Post by 3rdalbum on 2010-01-07
> **iponeverything said:**
> The main thing that comes to mind is support for devices. System utilities can often be ported with a simple recompile. Hardware drivers are slightly more problematic.. And, of course, it takes a small army of people to maintain the kernel port!

I thought Linux kernel modules (in source code form) were portable across architectures?

---

### Post by Johnsie on 2010-01-07
Most users don't want Linux on their computer. We had this before with the netbooks. The return to base rate for Linux netbooks went through the roof.

I installed Ubuntu on a few peoples netbooks and they couldn't use the applications or hardware they wanted to use so they got frustrated. I eventually installed Windows XP for them because that's what they're used to and it works with just about everything.

---

### Post by xir_ on 2010-01-07
> **Johnsie said:**
> Most users don't want Linux on their computer. We had this before with the netbooks. The return to base rate for Linux netbooks went through the roof.

I installed Ubuntu on a few peoples netbooks and they couldn't use the applications or hardware they wanted to use so they got frustrated. I eventually installed Windows XP for them because that's what they're used to and it works with just about everything.

over 30% of netbooks are sold with linux, the whole return thing was some made up by some guy at microsoft to spread FUD. Even dell has said that microsft was mistaken and that their retutrn rate wasn't really any higher.

---

### Post by cascade9 on 2010-01-07
> **Swagman said:**
> Modern CISCS CPU's actually have a Risc core <--- I kid you not. They saw the writing on the wall and incorporated it into x86 architecture.. I'm pretty sure AMD did it first and licenced the tech to intel

[edit]

Actually "core" is probably the wrong term. Extension is probably closer to what I mean.

Nope, it was Intel- Pentium Pro. AMD did a RISC core for the original k6s a little bit later.

---

### Post by iponeverything on 2010-01-07
> **3rdalbum said:**
> I thought Linux kernel modules (in source code form) were portable across architectures?

The kernel is the shim between hardware and software. If the kernel module is for say squashfs, I imagine it pretty portable. If the module is for a piece of hardware - video, network, pci etc, the code is going to have to be specific to the architecture. 

Maintaining a kernel across architectures is a lot of work. Back in the day, Jon "maddog" Hall was working at DEC. He gave a cool alpha machine to Linus. Maddog wanted linux to ported to the alpha.. it worked ;)

---

### Post by iponeverything on 2010-01-07
> **Johnsie said:**
> Most users don't want Linux on their computer. We had this before with the netbooks. The return to base rate for Linux netbooks went through the roof.


I thought it was kind of odd hear this repeated. As xir_ stated that information had been refuted by Dell and others.

---

### Post by 1337 on 2010-01-07
> **Warpnow said:**
> The A8, which is A9's predecessor is clocked at 500mhz and is what's in cell phones and MIDs. Its a nice chip. I don't have access to a testing board, but I doubt it would handle most of the default linux distributions without serious slowdowns.


You are wrong, Cortex A8 is pretty powerful processor dunno if you know what you are talking about there's ARM8 and ARM Cortex A8 which is different and aimed for such nettops/netbooks it can fight easily with Intel ATOM. A8 can be clocked greater than 1GHz. There are also new Dual Core ARM processors and Quad Core in making by Marvell atleast probably by Qualcomm and Freescale too. [Here]("http://www.youtube.com/watch?v=W4W6lVQl3QA") is interesting comparision video of ATOM based netbook and Dual Core ARM Cortex A9 clocked only on 500Mhz (netbook is @ 1600Mhz).

---

### Post by BuffaloX on 2010-01-07
Have a look at this Lenovo Smartbook:

[http://www.youtube.com/watch?v=q9ziIOvRVgs]("http://www.youtube.com/watch?v=q9ziIOvRVgs")

I'm really excited by these new smartbooks.

_Arm based computers has a lot to offer:_
1. Very slim design Nearly as slim as a smart phone
2. Light weight of less than 2 pounds for a 10" system.
3. Long battery life, 8-10 hours of normal use, on a tiny 3 cell battery!
4. Low price, due to competitive licensed production.
5. Powerful processor based on true RISC technology.

When the ARM came out originally, it ran circles around anything Intel had at the time.
This is not a weak low end CPU by design.
The only reason it's not as powerful as it's potential, is that it has only had success on small devices like smartphones.

The Arm community has shown that both clock speeds and the number of cores can be increased reasonably easy. If there is a market for it, they have shown they can relatively quickly make a CPU that is about 6-8 times faster than what they have now.

I bet the ARM will run circles around Intels Atom, while using only a fraction of the power.
Even without a fan or other special cooling, the ARM doesn't get hot.
They have an enormous headroom for increased speed, the ARM was born fast, with fast IRQ and IO operations, memory optimization, efficient instruction set. All this is contrary to Intel x86 CPUs.

The RISC architecture doesn't necessarily mean that less work is done per instruction, it simply means that there are fewer instructions.
For example the ARM has compare built in to virtually every instruction, which actually means MORE is done per instruction, while still executing in fewer clocks. This is part of the design which both optimize instruction set and memory usage.

It will be extremely interesting to see how this goes. [-o<

---

### Post by Jarmen_Deffs on 2010-03-11
> **Warpnow said:**
> The A8, which is A9's predecessor is clocked at 500mhz and is what's in cell phones and MIDs. Its a nice chip. I don't have access to a testing board, but I doubt it would handle most of the default linux distributions without serious slowdowns.

The A9, on the other hand, is dual core and clocked at 2ghz, and outstrips the atom on benchmarks, or so we're told...I don't actually know anyone whose seen one.

The Snapdragon QSD 8672 is dual-core A8 tech, at 1.5 Ghz...

The LG U8500 is powered by Cortex A9: [http://www.lge.com/products/model/detail/u8500.jhtml](http://www.lge.com/products/model/detail/u8500.jhtml)

TI OMAP 4430 and 4440 are A9, so is Tegra2.

I'm putting off buying a computer until a decent ARM netbook comes out, I'm hoping it happens soon...

I am literally checking tech sites daily hoping I will see a good one go retail ;)

---

### Post by 1337 on 2010-03-12
> **Jarmen_Deffs said:**
> I'm putting off buying a computer until a decent ARM netbook comes out, I'm hoping it happens soon...

I am literally checking tech sites daily hoping I will see a good one go retail ;)

That is exactly what I'm doing too, I'm glad to see that other people thinking the same thing.

---

### Post by MooPi on 2010-03-12
Personally I would consider a tablet or netbook with the right interface for on the move computing. I guess you could say a mix between a computer and a large cell phone. Using it for maps and yellow page searches, minimal email and text. I wouldn't want to pay and Arm and a leg for it (sorry for the pun).

---

### Post by JDShu on 2010-03-12
Yeah I only recently learned about ARM. Is it realistic to expect ~$200 ARM netbooks with >9 inch screens that are based on Linux in the near future?

---

### Post by undecim on 2010-03-12
If I could get a 12.1 or bigger screen on a laptop running one of the new arm processors (with speed measured in GHz) I would buy it.

---

### Post by andras artois on 2010-03-12
I want one.

---

### Post by chris200x9 on 2010-03-12
personally I don't care how powerful they are, within reason, because I just want it to be a highly portable front end to my quad core desktop :P

---

### Post by Roasted on 2010-03-12
As long as it doesn't have video tearing like my last two desktops have had, I'd be all about one for watching movies on the go.

---

### Post by Jarmen_Deffs on 2010-03-13
> **JDShu said:**
> Yeah I only recently learned about ARM. Is it realistic to expect ~$200 ARM netbooks with >9 inch screens that are based on Linux in the near future?

Yes, have a look at the links in the OP here: [http://ubuntuforums.org/showthread.php?t=1377293](http://ubuntuforums.org/showthread.php?t=1377293)

You may be interested in this too: [http://news.cnet.com/8301-13924_3-10423606-64.html](http://news.cnet.com/8301-13924_3-10423606-64.html)

---

### Post by blueshiftoverwatch on 2010-03-13
> **iponeverything said:**
> The ubiquity of x86 has enormous mass. Like it or not, it is going to be the centre of the software universe for a while. Even apple couldn't escape its pull ;)
I was just thinking that probably the only way we're ever going to move away from x86 based chips is for Linux to gain a significant marketshare on the desktop market. Because many open source applications as well as the kernal have been ported from IA-32 over to other non-x86 based architectures. Microsoft only designs their OS for three architectures: IA-32, X64, and IA-64.

Currently, the only reason not as much development is going into non-x86 based Linux technology is because not many people run it on non-x86. But if that started to change, companies could create desktop/laptop computers for the home market that ran on ARM or maybe even MIPS and more people would adopt the technology because Linux and Linux applications could be more easily ported to them.

Besides that scenario, can anyone come up with another way that x86-based processors will ever go away? It seems like the longer the technology stays with us, the harder it will be to push away. Maybe (if the Human race is still alive) people will still be using x86 based chips several hundred years in the future when the Moon and Mars are being colonized. That would be kind of weird.
> **BuffaloX said:**
> When the ARM came out originally, it ran circles around anything Intel had at the time.
This is not a weak low end CPU by design.
The only reason it's not as powerful as it's potential, is that it has only had success on small devices like smartphones.
In addition to small low powered devices there are also supercomputers that run on ARM. So, if ARM can power the lowest of the low and the highest of the high, why not a desktop or laptop computer which are between the two extremes? Assuming that application architecture support was not an issue.

---

### Post by Jarmen_Deffs on 2010-03-13
> **blueshiftoverwatch said:**
> I was just thinking that probably the only way we're ever going to move away from x86 based chips is for Linux to gain a significant marketshare on the desktop market. Because many open source applications as well as the kernal have been ported from IA-32 over to other non-x86 based architectures. Microsoft only designs their OS for three architectures: IA-32, X64, and IA-64.

Currently, the only reason not as much development is going into non-x86 based Linux technology is because not many people run it on non-x86. But if that started to change, companies could create desktop/laptop computers for the home market that ran on ARM or maybe even MIPS and more people would adopt the technology because Linux and Linux applications could be more easily ported to them.

Besides that scenario, can anyone come up with another way that x86-based processors will ever go away? It seems like the longer the technology stays with us, the harder it will be to push away. Maybe (if the Human race is still alive) people will still be using x86 based chips several hundred years in the future when the Moon and Mars are being colonized. That would be kind of weird.

[ARM are predicting ]("http://blogs.zdnet.com/gadgetreviews/?p=13100")more [than 50 tablets based on their architecture]("http://www.computerworld.com/s/article/9168418/ARM_sees_over_50_new_iPad_like_devices_out_this_year") will be released this year, and as there's no windows for ARM, they'll all be running something based on Linux (unless MS can push wm7 onto some, but that's going to mean a price increase, still break compatibility with desktop windows, and even the "windows" in the name won't stop people noticing it's a completely different OS)

If that happens I think that this could be the toehold Linux needs to become a household name, and acceptable to most people, even if not preferred over windows.

We didn't see this happen with netbooks because people equate "computer" with "windows", and for some reason we are still waiting for decent ARM netbooks to be released to retail, but it looks like tablets might be a different story;  manufacturers seem to be on the ARM bandwagon already, and a different physical form factor may help break the consumer's mental barrier against computers without windows.

Apple running the iPhone OS instead of OSX on the iPad certainly won't hurt either; consumers will more readily accept tablets without their desktop OS because of this.

---

### Post by markbuntu on 2010-03-13
All the ARMs will be running linux. Archos and Nokia have already done a lot of the work porting apps to the ARM platform and the kernel is already there. Nokias Mameo is aimed at the ARM
There is a serious convergence going on here and these ARM tablets are bringing in the cutthroat cell phone makers. It will be their revenge for the iPhone.

My early adopter friends have moved on from iPhones to the ARM based Nokia 900 somethings already.

---

### Post by JDShu on 2010-03-14
> **Jarmen_Deffs said:**
> You may be interested in this too: [http://news.cnet.com/8301-13924_3-10423606-64.html](http://news.cnet.com/8301-13924_3-10423606-64.html)

Looks promising, everything I want if only the screen was bigger. They all seem to be prototypes, I wonder how many will actually start selling?

---

### Post by Austin25 on 2010-03-14
[http://www.open-pandora.org/](http://www.open-pandora.org/)

---

### Post by Jarmen_Deffs on 2010-03-15
> **JDShu said:**
> Looks promising, everything I want if only the screen was bigger. They all seem to be prototypes, I wonder how many will actually start selling?

Yeah, who knows?  They keep talking about it, but not many have gone beyond prototype yet (as far as we know).  There was a decent one released in partnership with a Spanish telco a couple of weeks ago, but I don't live in Spain, and apart from that I've heard nothing...:(

---

### Post by ssam on 2010-03-15
beagleboard runs linux well.

---

### Post by Khakilang on 2010-03-15
Is there a comparison between ARM and Intel Atom processor? Like performance for one?

---

### Post by 1337 on 2010-03-15
I only have something like [this]("http://www.youtube.com/watch?v=W4W6lVQl3QA"), I know this is not too much representative but it shows some stuff.

---

### Post by Jarmen_Deffs on 2010-03-15
> **Koh Kook Loon said:**
> Is there a comparison between ARM and Intel Atom processor? Like performance for one?

ARM demonstrated a chip [outperforming an Atom N270]("http://www.pcworld.com/article/172069/arm_flaunts_performance_by_boosting_processor_speed.html") last year, but the N270 was released in 2008, so it's not particularly exciting. :P

ARM performance can't really compete with the Atom, but has a much better power consumption to performance ratio, and it's cheaper and smaller.

---

### Post by Jarmen_Deffs on 2010-03-19
A tablet doesn't suit my needs (a netbook is what I want) but for people interested in tablets, here's a 10" one with the price ($99), processing power(1Ghz CPU capable of 1080p video) and battery life(20-30 hr) that would make a perfect netbook, IMHO:

[http://armdevices.net/2010/03/18/marvell-announces-99-moby-tablet-to-revolutionize-education/](http://armdevices.net/2010/03/18/marvell-announces-99-moby-tablet-to-revolutionize-education/)


If it had a keyboard I'd probably buy 3 or 4 ;)

But it's just a prototype, still not for sale (surprise, surprise...)

---

### Post by Gr8-Ideas on 2010-03-24
Hi,

Is it true Ubuntu have dropped support for the ARM processor??

Found in another post [http://ubuntuforums.org/showpost.php?p=8872009&postcount=194](http://ubuntuforums.org/showpost.php?p=8872009&postcount=194)

Just eager to know if this is true.

Poor show if this a reality.

---

### Post by 1337 on 2010-03-25
I doubt this info is true, look here: [http://www.ubuntu.com/products/whatisubuntu/arm](http://www.ubuntu.com/products/whatisubuntu/arm)

---

