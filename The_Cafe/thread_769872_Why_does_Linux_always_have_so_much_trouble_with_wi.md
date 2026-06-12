---
title: "Why does Linux always have so much trouble with wireless?"
date: 2008-04-26
forum: The Cafe
---

### Post by ShadowGray on 2008-04-26
What is it with linux and not being able to use wireless correctly?  Almost everything else is plug and play, but when it comes to wireless connections I have to go through ndiswrapper and all these little problems.

And even if I do, it's not guaranteed to work.. my usb adapter can't connected to any encrypted routers, only open ones... and I don't want to be on an unsecured network.

What about wireless is so complicated?? :mad:

---

### Post by LaRoza on 2008-04-26
Works fine out the box for me. (Intel)

The reason why so many wireless issues exist is not a lack of Linux development, but a lack of hardware manufacturers cooperation.

---

### Post by SunnyRabbiera on 2008-04-26
wireless is still sketchy, its not our fault.
remember that most wireless devices have only windows in mind, heck you would have just as much trouble if you owned a Mac, perhaps even more trouble...

---

### Post by LaRoza on 2008-04-26
> **SunnyRabbiera said:**
> wireless is still sketchy, its not our fault.
remember that most wireless devices have only windows in mind, heck you would have just as much trouble if you owned a Mac, perhaps even more trouble...

Apple hardware would work I believe.

---

### Post by SunnyRabbiera on 2008-04-26
yeh, but if you got apple maintained stuff, but if you got a third party wireless card/usb receiver then things would be different.

---

### Post by LaRoza on 2008-04-26
> **SunnyRabbiera said:**
> yeh, but if you got apple maintained stuff, but if you got a third party wireless card/usb receiver then things would be different.

Yes it would.

---

### Post by Jackisback321 on 2008-04-26
Yeah it's worked fine for me from 7.04 through 8.04.  I'm no programmer so I won't complain; I'm sure it's harder than it sounds to have full wireless support right out of the box.

---

### Post by SunnyRabbiera on 2008-04-26
Yeh, there are so many variables to deal with here.
But look at the progress we have made so far, we just need more help from those big companies like linksys and such

---

### Post by ShadowGray on 2008-04-26
I suppose, and it's nice that intel wireless seems to be working out of the box.  Sadly, I've never had a single good experience with Linux wireless.

More importantly, it seems like no one has a clue on how to fix anything.  Does anyone know of a how-to guide for the WG111v2 on Hardy Heron?  I tried to do it using the same method I used to configure my Dell 1390, but the WG111v2 doesn't want to work right... I can't even get it to connect to my router when it has WPA on.

---

### Post by SZF2001 on 2008-04-26
It seems like ndiswrapper is the savior of wireless networking. People would have to actually write drivers without it. [/meanjoke]

But seriously, you should consider wicd as a wireless and LAN manager - the default gnome stuff doesn't seem to cut it much and for some reason wicd is always dependable... In my case anyway.

And if you haven't tried ndiswrapper you should seriously consider it. I know the idea of using a Windows driver for your hardware on a Linux machine is the ultimate open source sin, or whatever, but I'm actually using it over the rt* drivers that would constantly drop my connections and just be awful.

It seems like Linux has a way to go with wireless, but things can only get better, right?

---

### Post by SunnyRabbiera on 2008-04-26
well thats a bit more advanced and not as common, me i rely on a hardwire connection and never rely on wireless.
you can try to find a generic linux guide for your card though, even a guide for gutsy might help you out...
we will do the best we can, remember we are all volunteers here

---

### Post by ShadowGray on 2008-04-26
That's what I've been doing... I've been using the generic guide for ndiswrapper... but it still doesn't work for the USB adapter.  It works fine for integrated wireless on the laptop, but that's not the problem here.

---

### Post by phrostbyte on 2008-04-27
**Purchase Intel chipsets.** Intel wifi works OUT OF THE BOX, no config needed, with WPA and everything. This has been true since AT LEAST Ubuntu 6.06 Dapper. Intel produces open source wifi drivers.

**Boycott Broadcom chipsets.** Anytime you want to buy a computer or a friend buying a computer tell them to AVOID Broadcom chipsets. Broadcom = wireless hell on Linux. Broadcom doesn't even produce a proprietary Linux driver, and makes life hell for Linux developers with their firmware licenses! Unfortuneatly Broadcom is one of the most (if not the most common wifi).

---

### Post by Anduu on 2008-04-27
Wireless is getting there...slowly.

I am using the MadWifi driver for the Atheros card in my laptop.Unfortunately I am stuck using 32bit Ubuntu for now as there is no support as of yet for 64bit systems.

The MadWifi devs are trying to get a little help from the hardware manufacturers but as we all know this is like pulling teeth :(

---

### Post by init1 on 2008-04-27
Yeah, wireless can be a pain if you don't have a supported card. The reason why this is so is because many manufacturers don't release Linux drivers.

---

### Post by akiratheoni on 2008-04-27
Yeah my friend had a Broadcom card on his laptop. But it did work without too much trouble, thankfully... I guess it's because it's an older model. Luckily I don't have any new laptops so I don't need to deal with wireless connections... they're all wired right now.

---

### Post by Jammin80503 on 2008-04-27
> **SunnyRabbiera said:**
> wireless is still sketchy, its not our fault.
remember that most wireless devices have only windows in mind, heck you would have just as much trouble if you owned a Mac, perhaps even more trouble...

Thats not exactly true - most macs come with integrated airport cards, which makes it pretty easy to configure.

---

### Post by Seti on 2008-04-27
It's just proof that all the big companies that manufacture wireless gear are cornered pwnd by some illuminati-type group, and they're holding off until linux is ready take over the world desktop market (from u know who). Once this happens you will see a revolution in personal computing like there has never been before. Don't you think if they were able to make software to control soundcards and video, that they couldn't make the wireless work??? Something's fishy here. Something big is coming.

---

### Post by ShodanjoDM on 2008-04-27
So far I've installed Ubuntu (7.04 & 7.10) on:

HP/Compaq nc6000
ASUS W5
Acer Aspire 4520
Toshiba Satellite M200
+ a few of local brand laptops

The wireless works out of the box. Ofcourse, maybe I'm just lucky since none of those laptops have any "troubled" chips built in.

---

### Post by popch on 2008-04-27
> **ShadowGray said:**
> **Why does Linux always have so much trouble with wireless?**

It does not. So far, I have used Linux on something like six or ten different laptops at home (over the course of time), and ever since WLAN was supported at all, it worked perfectly all right. Well, most of the time.

As others have pointed out, it's the other way 'round: there are some WLAN cards which are less or not at all usable with Linux. The fault lies with the manufacturers because they withhold the information about their hardware needed to write a proper driver. They give that information to others who write Windows drivers or they write the Windows drivers by themselves, and with varying success, at that.

It does pay, however, to make sure that Linux runs with the hardware before buying that hardware. I have made it a point to run the live CD on any prospective PC of mine, and I have met with considerable success and cooperation in the shops I wanted to do so. Salespeople often are curious and want to see Linux run on their ware.

---

### Post by SirThom on 2008-04-27
Putting ndiswrapper on Heron it Hijacked my USB ports and I couldn't plug in my external mouse or keyboard even after I deleted it.  I had to redo my installation to get them back (which was new so no big deal).
Thankfully, I was able to find other instructions for using wireless on my machine that did not require ndiswrapper.

P.S. I am running a Pavilion tx1115nr with an AMD 64 dual core and built in broadcom.

---

### Post by gunbladeiv on 2008-04-27
honestly,
i've been using broadcom for about 2 years, not much problem from the beginning.  If firmware didnt work out of the box in previous version due to power problem, just use ndiswrapper.
But as far as I know, b43 firmware didnt have any problem.  So I should say that b43 is good and ready to go for those whose having trouble with bcm43xx driver before.   
And nice work from the dev team.  Really appreciate it.  Broadcom isnt that bad actually, the 'dev team' make it easier for end user to have wireless connection.  I shouldnt put complain on the drivers. :)

---

### Post by tashmooclam on 2008-04-27
For what it's worth. Changing to an Intel card cost me $25 on ebay. This instantly solved my wireless "issues" with Ubuntu. I had a Broadcom and did all of the "wrapper" stuff, and even changed programs for the network manager to WICD,forget it. Swap your wireless card, and enjoy your life. Think of it as a "Linux tax" or something.

---

### Post by madjr on 2008-04-27
> **tashmooclam said:**
> For what it's worth. Changing to an Intel card cost me $25 on ebay. This instantly solved my wireless "issues" with Ubuntu. I had a Broadcom and did all of the "wrapper" stuff, and even changed programs for the network manager to WICD,forget it. Swap your wireless card, and enjoy your life. Think of it as a "Linux tax" or something.

exactly go with Intel and avoid the headaches.

Just remember to get linux supported stuff in the future.

ask first then buy.

am sure no one buys something for an Apple pc unless they know is going to work 100%

---

### Post by ugm6hr on 2008-04-27
I second the "buy a card that works" option.

Easy enough for PCI or mini-PCI options (Atheros or Intel) - ebay has options between £12-£25 for these.

Unfortunately, few of the USB chipsets have support in Linux, which is probably the main problem (other than Broadcom).

Good thing I use mini-PCI in my laptop :)

---

### Post by FuturePilot on 2008-04-27
> **ugm6hr said:**
> I second the "buy a card that works" option.

Easy enough for PCI or mini-PCI options (Atheros or Intel) - ebay has options between £12-£25 for these.

Unfortunately, few of the USB chipsets have support in Linux, which is probably the main problem (other than Broadcom).

Good thing I use mini-PCI in my laptop :)

I'll third that. :)
When I bought wireless cards, I made sure they would work with Linux.
I have an Intel card and two Atheros based cards and all of them work out of the box.

Best bet is to go with an Intel or Atheros based card.

---

### Post by tylerspaska on 2008-04-27
From what I understand; the FCC has a lot of restrictions on radio signals and the code that goes into making them work. For some reason, the restrictions make it hard to learn about wireless driver creation which in turn makes it hard for those who want to write Linux drivers for wireless cards. At least this is what a friend of mine told me (he writes Linux drivers as a side-profession).

I'm lucky that my Broadcom wireless card is supported out of the box.

---

### Post by kevdog on 2008-04-27
What was the rumor a long time ago, that ndiswrapper was going to be dropped by Linus b/c it was considered proprietary software?  What a mistake that would have been?

---

### Post by Kernel Sanders on 2008-04-27
Mine worked great in Gutsy, then the new intel driver was added to the kernel, and now nothing but problems ever since :(

---

### Post by ssam on 2008-04-27
> **phrostbyte said:**
> Broadcom doesn't even produce a proprietary Linux driver, and makes life hell for Linux developers with their firmware licenses!

Thats not quite true. broadcom to make a proprietary linux driver. it is used in may wireless routers, eg linksys. however it is only for 2.4 kernels, and it not for x86 sysems.

this binary driver has been reverse engineered, and the result in now in the kernel.

the firmware bit it right. no one is allowed to distribute the firmware, which means it must be downloaded from the web, andextracted with the bcm43xx-fwcutter tool.

also broadcom are one of the biggest contibuters to the linux kernel, for their high end hardware. nothing is simple.

---

### Post by eye208 on 2008-04-27
> **ShadowGray said:**
> Why does Linux always have so much trouble with wireless?
Linux has zero trouble with Intel wireless. There is no Linux wireless problem, but a Broadcom wireless problem.

Every time people discuss the Broadcom wireless problem, comparisons with Apple come up. But Mac OS never had to deal with Broadcom wireless. Apple is 100% Intel.

There is a lesson to learn from Apple: Trouble-free user experience requires quality hardware. Once people learn this lesson and choose their hardware with Linux in mind, the problems will be gone.

Boycott Broadcom until they cooperate.

---

### Post by ssam on 2008-04-27
> **eye208 said:**
> Every time people discuss the Broadcom wireless problem, comparisons with Apple come up. But Mac OS never had to deal with Broadcom wireless. Apple is 100% Intel.

apple have only ever had drivers for 3 chipsets.
airport - orinoco
airport extreme - broadcom
whatever the new one on the intel macs is.

but as a hardware seller they can contact the chipset maker and say, 'if you write a driver for us we'll buy a million cards'

ubuntu (with out downlaoading anything, or making an modifications) works great with intel, orinoco, cisco aironet, many ralink, most atheros, prism, and probable a few more.

---

### Post by ShadowGray on 2008-04-27
Thing is, I don't believe Intel makes a USB wireless adapter, or does it?  Plus, I got this adapter for free anyway, and it's worked fine under windows for at least a year or 2 now.

---

### Post by ugm6hr on 2008-04-28
> **ShadowGray said:**
> Thing is, I don't believe Intel makes a USB wireless adapter, or does it?  Plus, I got this adapter for free anyway, and it's worked fine under windows for at least a year or 2 now.

As I mentioned, USB wifi is much more of a lottery than PCI or mini-PCI.

---

### Post by Naguz on 2008-04-29
> **ShodanjoDM said:**
> So far I've installed Ubuntu (7.04 & 7.10) on:

HP/Compaq nc6000
ASUS W5
**Acer Aspire 4520**
Toshiba Satellite M200
+ a few of local brand laptops

The wireless works out of the box. Ofcourse, maybe I'm just lucky since none of those laptops have any "troubled" chips built in.Then you hae been lucky. My 4520 has the Atheros AR2425-chip (R5007EG), and is not working at all in 8.04 64bit,  no matter wjhat you do. 32bit 7.10+ndiswrapper worked fine, but not out of the box.

---

### Post by aaaantoine on 2008-04-29
There was some improvement for my Broadcom 4318 in Hardy.  While the network performance isn't noticably better, my wifi light no longer defaults to on, and the signal bars are more often closer to 100% than to 50% as it was before.  I still have to download the firmware, but Gutsy and Hardy both made this a trivial process.

---

### Post by quinnten83 on 2008-04-29
> **phrostbyte said:**
> **Purchase Intel chipsets.** Intel wifi works OUT OF THE BOX, no config needed, with WPA and everything. This has been true since AT LEAST Ubuntu 6.06 Dapper. Intel produces open source wifi drivers.

**Boycott Broadcom chipsets.** Anytime you want to buy a computer or a friend buying a computer tell them to AVOID Broadcom chipsets. Broadcom = wireless hell on Linux. Broadcom doesn't even produce a proprietary Linux driver, and makes life hell for Linux developers with their firmware licenses! Unfortuneatly Broadcom is one of the most (if not the most common wifi).

crazy thing is that they're one of the companies working on the kernel with Linus.

---

### Post by jerrylamos on 2008-04-29
I've done a little wireless.  From what I can see:

1.  Each and every wireless manufacturer is bound and determined to make their wireless adapters "different".  Standard be d#$%^d. Specificaions deep dark secret.

2.  Each and every wireless manufacturer wants their code to be secret, locked, untamperable, and undecipherable.  Maybe even unusable except on the laptop they tried it on, and the Windows release they were using at the time.

3.  Profit margins being slim to none, the manufacturer won't develop drivers for any setup that they perceive is not "90%" of the market.

4.  There is a strong core of Linux developers that resist doing anything that is not "open code, open market, open adapter" however they define that.

5.  It's not at all evident to us users which wireless card(s) or which TV adapters ubuntu prefers.

So us users might luck out and we might not.

Jerry

---

### Post by drascus on 2008-04-29
Many Hardware manufacturers have been very uncooperative with us in general. And we are barely asking for anything at all. We don't need them to release a Free or Open Driver. We don't need them to port to linux. The only thing we have asked for is the specs on the hardware so we can write our own drivers. This whole thing could be solved with an e-mail of the stuff they already have on shelf. But they refuse to do it even after letters and petitions. I would suggest writing a letter to the manufacturer of your card and complaining. Then I would suggest getting a card that is supported. I have heard good things about Ralink. Here is a link to a database that might help you pick:[http://www.fsf.org/resources/hw/net/wireless/cards.html](http://www.fsf.org/resources/hw/net/wireless/cards.html) probably the easiest solution would be a usb type wireless adapter that way you don't even have to open up your computer. Good luck hope that helps.

---

### Post by quinnten83 on 2008-04-29
> **gunbladeiv said:**
> honestly,
i've been using broadcom for about 2 years, not much problem from the beginning.  If firmware didnt work out of the box in previous version due to power problem, just use ndiswrapper.
But as far as I know, b43 firmware didnt have any problem.  So I should say that b43 is good and ready to go for those whose having trouble with bcm43xx driver before.   
And nice work from the dev team.  Really appreciate it.  Broadcom isnt that bad actually, the 'dev team' make it easier for end user to have wireless connection.  I shouldnt put complain on the drivers. :)
my bcm4306 pcmcia card doesn't work and completely borks the system when i shove it in. Sooo nope... thye last time I got it working I had to use an instruction that isn't applicable for 8.04

---

### Post by Quillz on 2008-04-29
Since 6.06, I've actually had zero issues with wireless on my Dell Inspiron E1405. The Intel drivers were loaded right out of the box.

I did have some issues on my desktop due to it using an Atheros USB wireless adapter. But I solved it by replacing the ancient thing with a physical wireless card, and Ubuntu recognized it immediately.

---

### Post by sefs on 2008-04-29
Ralink seems to co-corporate pretty well, yet every release ubuntu breaks rt73 serialmonkey setup.

---

